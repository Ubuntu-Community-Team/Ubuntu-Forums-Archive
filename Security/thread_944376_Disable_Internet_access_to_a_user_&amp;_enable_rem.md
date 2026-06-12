---
title: "Disable Internet access to a user &amp; enable remote access to the machine for the user"
date: 2008-10-11
forum: Security
---

### Post by santhoshsd on 2008-10-11
Hello,
I have a system in which I have installed NXServer.
I want the a user to access the system remotely, but the user should not be able to access/browse in the system.

I tried with 
httpd: [email]user@localhost.com[/email] in /etc/hosts.deny
and
sshd: [email]user@localhost.com[/email] in /etc/hosts.allow

but it did not work.

Then I tried with 
sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT		
sudo iptables -A OUTPUT -p tcp -m owner –uid-owner tuser01 -j DROP

which disables the internet for the user but disables the remote login ?

---

### Post by cdenley on 2008-10-13
```

sudo iptables -A OUTPUT -p tcp -m owner –uid-owner tuser01 -j DROP

```
This seems to work for me for ssh. Are you able to get a shell? Did you try removing the denyhosts configuration you made? Does it work if you remove the iptables rules?

---

### Post by kevdog on 2008-10-13
Sounds like you want to set the user up with limited access -- like jailing the user to a specific set of directories.

---

### Post by santhoshsd on 2008-10-13
Hello, 
I removed the hosts.deny and hosts.allow configuration.
and then flushed iptables 
sudo iptables -F 

ssh is working now

now I executed the command
sudo iptables -A OUTPUT -p tcp -m owner –uid-owner tuser01 -j DROP
this stops all tcp traffic for me
and turns ssh also down.

---

### Post by cdenley on 2008-10-13
> **santhoshsd said:**
> Hello, 
I removed the hosts.deny and hosts.allow configuration.
and then flushed iptables 
sudo iptables -F 

ssh is working now

now I executed the command
sudo iptables -A OUTPUT -p tcp -m owner &#8211;uid-owner tuser01 -j DROP
this stops all tcp traffic for me
and turns ssh also down.

I'm not sure why it works for me but not you, but you could try
```

sudo iptables -I OUTPUT -m state --state ESTABLISHED -j ACCEPT

```
I suspected that the ssh process would run as the user connecting, then the outgoing traffic from the ssh connection would be dropped, but when I tested it, this wasn't the case for me (even though the process is owned by the connecting user).

---

### Post by kevdog on 2008-10-13
The reason that your statement is blocking you is that any packet originating from ownerUID tuser01 is going to be blocked -- that is all ports.

You unfortunately can not block by application since application is not contained in the tcp/ip stack.  You could however fine tune your blocking parameter however to block specific ports and allow others.  For example if you added above your previous statement something like


sudo iptables -A OUTPUT -p tcp --dport 22 -m owner –uid-owner tuser01 -j ACCEPT
sudo iptables -A OUTPUT -p tcp -m owner –uid-owner tuser01 -j DROP


Or you could just do

sudo iptables -A OUTPUT -p tcp --dport !22 -m owner –uid-owner tuser01 -j DROP

which would drop all packet except those destined for remote port 22.

Am I way off base?

---

### Post by kevdog on 2008-10-13
I always applied state tracking rules like this:

sudo iptables -I OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

---

