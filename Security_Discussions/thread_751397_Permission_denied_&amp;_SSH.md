---
title: "Permission denied &amp; SSH"
date: 2008-04-10
forum: Security Discussions
---

### Post by amai on 2008-04-10
I have a laptop directly connected to UBUNTU Server Edition 7.10using cross-over cable.

I can ping my server(7.10) 
When I do ping the server I get 0% loss( which means i have connection to the server).
BUT i cant TELNET or SSH to it . I get connection failed.

What do i need to active or open/change so that i can have SSH working

Ta....

Here is my troubleshooting so far.


(All of the following was done whilst login in as SUDO besides number 10)

1)When i try to reinstall SSH
-get ssh is already the newest version

2)when i ran -A localhost
-Port 22 & 23 are OPEN

3)iptables -nl
- I get
chain INPUT (policy ACCEPT)
target     prot opt source destination

chain FORWARD (policy ACCEPT)
target     prot opt source destination

chain OUTPUT (policy ACCEPT)
target     prot opt source destination


4)nestat -ntulp | grep 22
i get
-tcp6 0  0 :::22      :::* LISTERN 4232/sshd

5)netstat -na | grep -i listen | grep 22
i get
tcp6  0  0 :::22      :::* LISTERN

5)/etc/hosts.allow
I get permission denied

6)/etc/hosts.deny
I get permission denied

7)/etc/ssh/sshd_config
I get permission denied

8)When I do /var/log/auth.log
-I get permission denied

9)/etc/services
I get permission denied

10)whereis sshd
/usr/sbin/sshd/usr/share/man/man8/sshd.8.gz

---

### Post by rajj on 2008-04-10
for steps 6 to 9, try sudo before the command.

now, can u do:  ssh 0
This would establish a ssh session with itself and confirm if sshd is working locally.
If yes, Then is your local firewall blocking you? can you ssh to other servers.

---

### Post by rickyjones on 2008-04-10
> **amai said:**
> I have a laptop directly connected to UBUNTU Server Edition 7.10using cross-over cable.

I can ping my server(7.10) 
When I do ping the server I get 0% loss( which means i have connection to the server).
BUT i cant TELNET or SSH to it . I get connection failed.

What do i need to active or open/change so that i can have SSH working

Ta....

Here is my troubleshooting so far.


(All of the following was done whilst login in as SUDO besides number 10)

1)When i try to reinstall SSH
-get ssh is already the newest version


Did you do **apt-get install ssh** or did you do **apt-get install openssh-server**?

You must do the latter, not the former.

-Richard

---

### Post by amai on 2008-04-11
1>>RAJJ
I am logged as SUDO

when I did SSH 0 its all working fine

2>>RICKYJONES
YES i used this command
apt-get install openssh-server?

---

### Post by rickyjones on 2008-04-11
Can you run NMAP on a different computer, targeting your server? Or run some sort of portscanner to see if the ports are open at all?

-Richard

---

### Post by stmurray on 2008-04-11
Your netstat is showing both ssh and telnet to be listening using IPV6 (tcp6).  I'm not sure why they are configured this way, but to use them your other machine must support IPV6 (and you must use the correct IPV6 address, which won't be x.x.x.x but something like xxxx: xxxx: xxxx: xxxx: xxxx: xxxx ) or you must change your ssh and telnet configs.  Changing ssh would be much easier.  For ssh, I believe all you need to do is edit /etc/ssh/sshd_config and change the line that reads:

```
ListenAddress ::
```


To 

```
ListenAddress 0.0.0.0
```

and restart ssh.  telnet may similar, but I have never used telnet 

I hope that helps.

---

### Post by The Cog on 2008-04-11
5, 6, 7, 8, 9):
To view those configuration files where you are getting permission denied, use
**cat /etc/hosts.allow**
rather than just
**/etc/hosts.allow**
which tries to launch the file as a program.

The listening address of :::22 is correct. It is in fact listening on both IPv4 and IPv6. No problems here.

Why does ssh connection fail?  Use a terminal command to make the connection and note the reason the connection fails.

Can the server conect to itself? (ssh 127.0.0.1)?

---

