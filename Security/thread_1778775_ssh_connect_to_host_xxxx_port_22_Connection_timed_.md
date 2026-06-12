---
title: "ssh: connect to host xxxx port 22: Connection timed out"
date: 2011-06-09
forum: Security
---

### Post by mahi.aw on 2011-06-09
Hi everyone,

I am new to ssh..
I am trying to connect to the remote Ubuntu system but not able to do so::let me tell you what are the options i have set up and what's problem.

open-ssh is install on my laptop and also available on remote system.
firewall port 22 is on.
I can connect to local host
I can ping to the remote system.
I have wireless connection.

When i am trying to ssh  to remote system i get message like this::
ssh: connect to host xxxx port 22: Connection timed out

P.S I have check other related post but not able to figure out what's the problem..

Can any one help to solve the issue?
thanks in advance for help

---

### Post by linuxinstalledfromhdd on 2011-06-09
> **mahi.aw said:**
> Hi everyone,

I am new to ssh..
I am trying to connect to the remote Ubuntu system but not able to do so::let me tell you what are the options i have set up and what's problem.

open-ssh is install on my laptop and also available on remote system.
firewall port 22 is on.
I can connect to local host
I can ping to the remote system.
I have wireless connection.

When i am trying to ssh  to remote system i get message like this::
ssh: connect to host xxxx port 22: Connection timed out

P.S I have check other related post but not able to figure out what's the problem..

Can any one help to solve the issue?
thanks in advance for help

Have you ever been able to connect to the other computer with ssh before? Or do you think
you have configured the ssh server incorrectly?

---

### Post by mahi.aw on 2011-06-09
Hi thanks for your prompt reply.

No I have not tried from my  laptop before..this is the first time i am trying to connect from my laptop.
and i just run the command 
sudo apt-get install openssh-server for installing ssh..

---

### Post by linuxinstalledfromhdd on 2011-06-09
Have you been able to connect to that ssh server from any other system before either?

Double check your ssh server settings if not:

[http://cinderbox.net/2011/02/22/how-to-setup-ssh-on-ubuntu-10-10-maverick-meerkat-using-openssh-server/](http://cinderbox.net/2011/02/22/how-to-setup-ssh-on-ubuntu-10-10-maverick-meerkat-using-openssh-server/)

---

### Post by uRock on 2011-06-09
By default openssh-client is installed. Have you install openssh-server?

What syntax are you using to connect? It should look something like ```
ssh urock@192.168.254.253
```

Moved to ***Security Discussions***

---

### Post by mahi.aw on 2011-06-09
Actually i did not tried to connect to this ssh-server from some where else..
but just to confirm whether ssh server is working or not..i did the ssh to local host and it's working..

regarding the configuration i do not have much idea,,as what to setup but let's see i will follow your link..

---

### Post by mahi.aw on 2011-06-09
Hi uRock

i have install the openssh-server and using the command like ssh xyz@ipadressofremotesystem.

---

### Post by collisionystm on 2011-06-09
ssh is very easy.

What steps did you take to install? For me all I do is

```
sudo apt-get install ssh
```

And now I can ssh to the box from another machine.

Do you have a firewall enabled? That is probably the issue.

---

### Post by uRock on 2011-06-09
Are you on the local network when trying to connect? If not, then have you set up port forwarding on your router? Without port forwarding, your router will drop incoming packets that do not have a NAT/PAT entry in its IP table.

---

### Post by mahi.aw on 2011-06-09
[Hi collisionystm]("http://ubuntuforums.org/member.php?u=1249225")

yes i did exactly the same..and the firewall is also enabled...

---

### Post by collisionystm on 2011-06-09
> **mahi.aw said:**
> [Hi collisionystm]("http://ubuntuforums.org/member.php?u=1249225")

yes i did exactly the same..and the firewall is also enabled...


Did you make sure to allow inbound on port 22?

Are these computers both on your local network?

---

### Post by uRock on 2011-06-09
> **mahi.aw said:**
> yes i did exactly the same..and the firewall is also enabled...

If the firewall is enable, then you will have to add a rule allowing incoming packets for port 22.

---

### Post by mahi.aw on 2011-06-09
yes port 22 is open on my laptop..but do i need to do same thing..like port opening in remote system?

---

### Post by uRock on 2011-06-09
> **mahi.aw said:**
> yes port 22 is open on my laptop..but do i need to do same thing..like port opening in remote system?

Yes, the system you are connecting to has to have port 22 open.

---

### Post by mahi.aw on 2011-06-09
Both these computer are not on local network..
I am sorry but i did not understand what is inbound on port 22?

---

### Post by collisionystm on 2011-06-09
> **mahi.aw said:**
> Both these computer are not on local network..
I am sorry but i did not understand what is inbound on port 22?


Open your firewall program such as GUFW. Allow connections inbound on port 22.

Go to your router that the remote machine is accessing the internet through, enable port forwarding on port 22 to the local ip address of the computer.

Now on your computer, ssh to the public ip address of the router itself.

you can find this by going to a computer in that network and visiting [www.whatismyip.com](www.whatismyip.com)

---

### Post by cariboo on 2011-06-09
Could you paste your firewall rules in your next post? Use the following command:

```
sudo iptables -L
```

---

### Post by mahi.aw on 2011-06-09
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            state INVALID limit: avg 3/min burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination

---

### Post by krumpy on 2011-06-09
Is it possible to put both the computers on a local network while you're trying to get ssh up and running?  That way you can make sure ssh is working before doing the rest of the steps that collisionystm described (port fowarding, you may need to setup dyndns or similar service, etc.).

---

### Post by mahi.aw on 2011-06-09
I have enabled the port 22 already on my laptop which is using wireless connection.
My remote system is having LAN connection..Please note that both of these system are not part of same connection intrnet connection system.

I am bit confused here now..may be i ask some stupid questions herein now!!
which router should i access now(it's my laptop or remote system) and how should i accesss it?
local ip address of the which computer are you talking about?.

---

### Post by krumpy on 2011-06-09
For example my Home computer sits behind a router (which has a public IP address).  If I want to connect to my home computer from outside my home network I need to tell my router to forward port 22 requests to my home computer.  Maybe you could describe your network setup in a little more detail if it isn't something similar to this?

---

### Post by mahi.aw on 2011-06-09
Hi krumpy

OK..My case is like this:

I have laptop which is connected to internet wirlessly (this is my network)
My remote system is having wired connection (not a part home network)

Now from my laptop i am trying to access remote system (the ip address of this remote system i got from ifconfig command).
So now you mean i need to tell my router (at remote computer side:::not the laptop) to forward port 22 requests to remote computer,,right?
if am getting it right,,how can i forward port 22 requests to remote computer..

---

### Post by krumpy on 2011-06-09
So it sounds like your remote system does sit behind a router.  So yeah you have to setup some sort of port forwarding.  What brand router do you have?  This website explains how to set that up for many different types of routers ([http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm)).  

Usually it's pretty straight forward.  For my router there is a tab in the router's setup page that allows port forwarding.  So I set it to forward requests to port 22 to port 22 and my home computer's network IP address.

---

