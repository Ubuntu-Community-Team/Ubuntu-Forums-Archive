---
title: "A question on remotely setup iptables"
date: 2008-07-07
forum: Server Platforms
---

### Post by satimis on 2008-07-07
Hi folks,


Ubuntu LAMP 6.06 amd64, Headless
Iptables
(no front-end firewall running)


Is there a simple and safe way to ssh setup/config iptables remotely without being blocked at time of setup/config.

ssl is running on the server.  The ssh connection port is 2222

TIA


B.R.
satimis

---

### Post by osjak on 2008-07-07
Here's a good tutorial on setting it up:
[https://help.ubuntu.com/community/IptablesHowTo#Allowing%20Incoming%20Traffic%20on%20Specific%20Ports](https://help.ubuntu.com/community/IptablesHowTo#Allowing%20Incoming%20Traffic%20on%20Specific%20Ports)

Just remember - the first rule you plase should be allowing your ssh sessions. Then you can safely add more rules.

---

### Post by satimis on 2008-07-07
> **osjak said:**
> Here's a good tutorial on setting it up:
[https://help.ubuntu.com/community/IptablesHowTo#Allowing%20Incoming%20Traffic%20on%20Specific%20Ports](https://help.ubuntu.com/community/IptablesHowTo#Allowing%20Incoming%20Traffic%20on%20Specific%20Ports)

Just remember - the first rule you plase should be allowing your ssh sessions. Then you can safely add more rules.
Hi osjak,


Thanks for your advice and URL


I have no problem to setup/config iptables on Intranet with following rule up;```

iptables -A INPUT -s 192.168.0.52 -p tcp --dport 22 -j ACCEPT
```
192.168.0.52 is the local IP of local machine.  Therefore the local machine won't be blocked disregarding changes made on other rules.  The local machine (the only machine) can still get connected.


But I haven't figured out how to setup/config iptables over Internet.  I can change the local IP of of the local machine to public IP, say 111.222.333.444.  Can I get the server connected on shell?  If YES, how to make it?  TIA


How to make use of following rules;```

ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www

```
It seems to me that if they are up the server can be connected worldwide.  Would iptables be touched worldwide?  TIA


B.R.
satimis

---

### Post by osjak on 2008-07-07
```

sudo iptables -F
sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -j DROP
```
1st command deletes all rules you have, to make sure you start clean;
2nd command opens up your SSH port;
3rd command opens up your HTTP port;
4th command closes allother ports.

Issue this to verify:
```
sudo iptables -L
```

---

### Post by osjak on 2008-07-07
> **satimis said:**
> 
It seems to me that if they are up the server can be connected worldwide.  
Yes, the rules above don't specify the source, so anyone can connect to your web server or SSH (if they know the login). Is that your intent?

---

### Post by satimis on 2008-07-08
> **osjak said:**
> ```

sudo iptables -F
sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -j DROP
```
1st command deletes all rules you have, to make sure you start clean;
2nd command opens up your SSH port;
3rd command opens up your HTTP port;
4th command closes allother ports.

Issue this to verify:
```
sudo iptables -L
```
Sorry I can't test them because I'm on the local machine.  The server is headless.  If running the 1st command the connection to the server on the local machine will be blocked.  I can't run the remaining 3 commands


satimis

---

### Post by satimis on 2008-07-08
> **osjak said:**
> Yes, the rules above don't specify the source, so anyone can connect to your web server or SSH (if they know the login). Is that your intent?
No, that is not my intent.


What I'm looking is a solution to connect the remote server on Internet?


For example;
Server domain - aaa.com
Its Public IP - 111.222.333.444

Local machine domain - bbb.com
Its Public IP - 666.777.888.999


Shall I run the command on Shell/Terminal OR on browser?

Thanks


B.R.
satimis

---

### Post by osjak on 2008-07-08
> **satimis said:**
> No, that is not my intent.


What I'm looking is a solution to connect the remote server on Internet?


For example;
Server domain - aaa.com
Its Public IP - 111.222.333.444

Local machine domain - bbb.com
Its Public IP - 666.777.888.999


Shall I run the command on Shell/Terminal OR on browser?

Thanks


B.R.
satimis

I am sorry, but I am not completely understanding what you are saying. You want to connect your local machine to your remote server. Connect for what? If you are talking about SSH connection to do your admin maintenance, then the iptables setup I gave above will allow you to do that. It will not block you out because (1) you wipe out any rues from iptables, therefore all ports are available and (2) you specifically tell your iptables to allow SSH connections to your server. And the rest follows. With that configuration you will end up with 2 ports open on your server - port for SSH and port 80 for HTTP.

If you don't need HTTP access, then skip the step #3, that's all. In that case you'll have just one port open for SSH. 

Actually, since your sshd is running on an unconventional port, you'd be better off specifying it by number, as I'm not sure if iptables is smart enough to pick it up on its own. So rule #2 would be:
```
sudo iptables -A INPUT -p tcp --dport 2222 -j ACCEPT
```

I hope I understood what you were asking.

---

### Post by satimis on 2008-07-08
> **osjak said:**
> I am sorry, but I am not completely understanding what you are saying. You want to connect your local machine to your remote server. Connect for what?

Sorry for not explaining clear on previous postings about my target to achieve.


What I'm looking for is;

The remote server already has working iptables rules running.  They are on /etc/rc.local.  I can connect the server on Intranet, LAN, with ssh without problem.  I'm finding how to connect the remote server over Internet if I put it colocated in DataCenter.  I can't run "ssh -p 2222 router_IP" to connect the server on local machine any more.

To run commands on shell/terminal or on browser?


> 
If you don't need HTTP access, then skip the step #3, that's all. In that case you'll have just one port open for SSH. 

I need HTTP access if the server colocated on DataCenter.  What device shall I use to run the commands?  On shell/terminal or on browser.  But it needs to assure that the connection won't be blocked on testing new rules.  Besides I expect only allow my local maching to connect the server, not other machine else.


> 
Actually, since your sshd is running on an unconventional port, you'd be better off specifying it by number, as I'm not sure if iptables is smart enough to pick it up on its own. So rule #2 would be:
```
sudo iptables -A INPUT -p tcp --dport 2222 -j ACCEPT
```

I have no problem connecting the remote server on Intranet on port 2222.  It has been working for >2 months.


B.R.
satimis

---

### Post by osjak on 2008-07-08
> **satimis said:**
> Sorry for not explaining clear on previous postings about my target to achieve.


What I'm looking for is;

The remote server already has working iptables rules running.  They are on /etc/rc.local.  I can connect the server on Intranet, LAN, with ssh without problem.  I'm finding how to connect the remote server over Internet if I put it colocated in DataCenter.  I can't run "ssh -p 2222 router_IP" to connect the server on local machine any more.

To run commands on shell/terminal or on browser?



I need HTTP access if the server colocated on DataCenter.  What device shall I use to run the commands?  On shell/terminal or on browser.  But it needs to assure that the connection won't be blocked on testing new rules.  Besides I expect only allow my local maching to connect the server, not other machine else.



I have no problem connecting the remote server on Intranet on port 2222.  It has been working for >2 months.


B.R.
satimis

You would connect to it from your terminal, the same way you connect to it now, but using its public IP for an address, that you will get form the collocation company:
```
ssh -p 2222 111.222.333.444
```

If you want to allow only your machine to connect via ssh, then you would specify it in your iptable rule:

```
sudo iptables -A INPUT -p tcp -s 666.777.888.999 --dport 2222 -j ACCEPT
```

---

### Post by satimis on 2008-07-08
> **osjak said:**
> You would connect to it from your terminal, the same way you connect to it now, but using its public IP for an address, that you will get form the collocation company:
```
ssh -p 2222 111.222.333.444
```

If you want to allow only your machine to connect via ssh, then you would specify it in your iptable rule:

```
sudo iptables -A INPUT -p tcp -s 666.777.888.999 --dport 2222 -j ACCEPT
```
Thanks, I'm clear now.


A further question;

1) 
Can I use Domain instead?

Remote Server
Domain - aaa.com

Local Machine
Public IP - 666.777.888.999


2)
Running dynamic IP

Remote Server
Domain - aaa.com

Local Machine
Public IP - dynamic IP

What can I do?  TIA



Edit:


A further thought:-

Can I create a subdomain on aaa.com, say admin.aaa.com?  Then;

Remote Server
Domain - aaa.com

Local Machine
Domain - admin.aaa.com


If YES, where shall I create the subdomain?  On Register's website?


satimis

---

