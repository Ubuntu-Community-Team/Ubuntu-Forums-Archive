---
title: "SSH using putty on windows xp"
date: 2007-02-19
forum: Server Platforms
---

### Post by Mr $.$ on 2007-02-19
Hi Folks,

Im quit new to the linux/ubuntu environment, but im getting into it very quickly and its great fun :KS.

Iv got Ubuntu 6.10 Desktop version running on my PC. Iv got it running with Apache 2.0 server.

Everything is working perfectly on my local network, i.e i have putty access to the ubuntu desktop on my laptop which is running windows xp throughj my local ip.

The problem i am having is to access my ubuntu desktop thorught SSh putty from a windows  computer out of my local network i.e. through the web.

I can access my server from outside .. i.e if do [http://myipaddess](http://myipaddess) ... i can see my index page, but i cannot gain putty access using my ipaddress. 

any solutions? 

- Sandip

---

### Post by MJN on 2007-02-19
Have you forwarded port 22 (SSH) from your router to the server?
 
Matew

---

### Post by enriquecm on 2007-02-19
Firewall !!

DO U HAVE INSTALL A FIREWALL ???

if the answer is YES 
check ure firewall jejejejje
and check the 22 port

IF isnt NO 
U moved something of IPTABLES jejjejeje

:-\"

---

### Post by Mr $.$ on 2007-02-19
yup i have forwarded the port. i dnt think its a firewall issue, is there any way i can test or check for sure whether its my firewall? :S

---

### Post by Disstress on 2007-02-19
Iptables should be blocking that port by default. It is insecure to allow ssh from outside your network. if you don't know how to use iptables from the command line there is a gui frontend for it.

Search in synaptic.

---

### Post by MJN on 2007-02-19
> **Disstress said:**
> Iptables should be blocking that port by default. 
 
Are you sure?
 
I don't use iptables myself however I assumed at default it would leave all ports fully open by virtue of the fact that Ubuntu installs with only a minimum set of services - any others (including SSH server) being required to be explicitly installed by the user.
 
If it is the default, what other ports are closed?
 
(To the OP - use **iptables -L **to see what current rules, if any, you have in place)
 
Mathew

---

### Post by Royel on 2007-02-19
sounds to me like port 22 is not open in your firewall rules.

I use Shorewall to configure my firewall settings an for me adding this line to /etc/shorewall/rules is all I have to do. I'm not sure how you configure your firewall, but adding a rule similiar to this should allow you to connect via ssh to your computer outside of your local network.

```


ACCEPT  net     $FW     tcp     22

```


well, I edited to try an fix teh nasty formatting, but you get the idea I think anyhow

---

### Post by Mr $.$ on 2007-02-19
tnx for all the help :) 

i will try these suggestions out 2nite and let u guyz know how it goes... once agian tnx

---

### Post by Mr $.$ on 2007-02-19
i changed the accept rules on the firewall and now its made it worse.

i CAN NOT access my server from my internal ip address and i also CAN NOT access my server from my external ip address thorugh putty.

my firewall rule are as follows: 

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  'myipaddress'  anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  '192.168.x.x'          anywhere            tcp dpt:ssh 
DROP       tcp  --  anywhere             anywhere            tcp dpt:ssh 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

SOME PLEASE HELP ME, IM AT UNIVERSITY AND REALLY NEED THIS WORKING FOR MY FINAL YEAR PROJECT. ANY HELP WILL BE APPRECIATED. 

THANKS,

- Sandip

---

### Post by MJN on 2007-02-19
Out of interest, what were the firewall rules *before* you changed them? If there weren't any rules as I suspect then you can't possibly hope to solve your problem by adding some. If there were already rules in place, who put them in?

Mathew

---

### Post by Mr $.$ on 2007-02-19
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

That how it was. And iv just used the  'iptable -F' to change it back to that, and now my localip works with PUTTY (ssh) but i still cnt get MYIPADDRESS working on the internet,

Any ideas?  Thanks for the help :)

---

### Post by MJN on 2007-02-20
In which case it's **not** a firewall issue. Your rule tables are empty i.e. you haven't got a firewall (iptables is installed but is running its default configuration i.e. complete open) so no adding of rules is going to help.
 
As for where your problem truly lies I don't know. Have you ruled out problems at the client end? That is, can you SSH to another (remote) machine from the client? Or have you tried SSHing from another machine (at a different location preferably giving the problem could be on the network egress point).
 
Mathew

---

### Post by conjur3r on 2007-02-20
Do you know if your ISP is blocking port 22?  You can test by temporarily disabling your apache server and reconfiguring your SSHD to listen on port 80.  If you are thinking this, do the following:

Stop apache:
# sudo /etc/init.d/apache2 stop

Edit /etc/ssh/sshd_config and add Port 80 beneath Port 22.

Restart sshd:
# sudo /etc/init.d/ssh restart

---

