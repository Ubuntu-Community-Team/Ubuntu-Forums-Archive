---
title: "connection refused ?!!??!?"
date: 2010-07-29
forum: Server Platforms
---

### Post by noworldorder on 2010-07-29
I changed routers (I was testing a router) and then returned to my original router.  Now I cannot access my server.   
 
chris@chris-laptop:~$ sudo ssh 192.168.1.100 
[sudo] password for chris:  
ssh: connect to host 192.168.1.100 port 22: Connection refused 
 
But nothing has changed in my original router settings and they were working fine before. 
 
I have rebooted the server, power cycled modem and router, and rebooted my PC. 
 
any thoughts? ~ thanks

---

### Post by alex88 on 2010-07-29
You haven't other ways to access the server? To see if sshd is running? If you haven't a firewall closed ports are closed.

try to ssh on 

ssh.bshellz.net

to see if it's a server or router problem

---

### Post by rtllz on 2010-07-29
have you checked your router configurations to see if maybe its blocking that port?

---

### Post by noworldorder on 2010-07-29
> You haven't other ways to access the server? To see if sshd is running? If you haven't a firewall closed ports are closed.So I am 150% newbie...  yes I can access the server directly.  What is this sshd thingy and what should I do about it...  :redface:

---

### Post by alex88 on 2010-07-29
> **noworldorder said:**
> So I am 150% newbie...  yes I can access the server directly.  What is this sshd thingy and what should I do about it...  :redface:

as i said, try before to access to another ssh server so you can exclude connection problems, then you can start check why server refuses connections.

---

### Post by noworldorder on 2010-07-29
I do not have another server I can try to connect to; however, I am able to ping the server (if this tells us anything).  Also, I am not able to connect to the server in a different way: [http://192.168.1.100/agc/vicidial.php](http://192.168.1.100/agc/vicidial.php) in my browser is how I access a program from the server.

Not sure if this means we (if you will help me) can start looking at the serve as the cause or not.  

~c

---

### Post by noworldorder on 2010-07-29
> have you checked your router configurations to see if maybe its blocking that port?

As I said it was working perfectly - I replaced the router and then returned the router and that is when the trouble started.  None of the settings seem to have changed.

---

### Post by alex88 on 2010-07-29
Oh, so your server is in your local lan, if you have direct access as you said, do a

```
sudo netstat -tapn | grep sshd
```and post here the output

---

### Post by noworldorder on 2010-07-29
ccp6             0               0 :::22                 :::*               LISTEN
4598/sshd

---

### Post by alex88 on 2010-07-29
> **noworldorder said:**
> ccp6             0               0 :::22                 :::*               LISTEN
4598/sshd

well, it says it's listening on tcp6, are you using ipv6 on your network config? i don't think so.

do these things, open file /etc/ssh/sshd_config with nano, uncomment line
```
#ListenAddress 0.0.0.0
```the restart sshd with

```
sudo /etc/init.d/ssh restart
```then do again sudo netstat -tapn | grep sshd and see if something changed

---

### Post by noworldorder on 2010-07-29
I rebooted and power cycled several more times

And it healed itself

thanks for jumping in to help

I am grateful

---

