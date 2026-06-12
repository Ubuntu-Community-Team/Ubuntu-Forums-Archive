---
title: "ssh proxy from china"
date: 2009-06-25
forum: Server Platforms
---

### Post by afbase on 2009-06-25
My friend is having some issues accessing google, etc. from China.  I guess the china firewall is blocking her from getting to the websites.  

I am trying to have her proxy through my ubuntu server in the USA to get complete internet access, but i'm thinking china blocked port 22 for ssh'ing.

here is what she did on her mac:
```

[SIZE=3]local-admins-computer:~ local_admin$ ssh -v -v -v -C -D 9999 [EMAIL="emily@coldowl.com"]Johnny5@coldowl.com[/EMAIL]
OpenSSH_5.1p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to coldowl.com [67.49.6.242] port 22.
debug1: connect to address 67.49.6.242 port 22: Operation timed out
ssh: connect to host coldowl.com port 22: Operation timed out[/SIZE]

```I can connect no problem using:
```

[SIZE=3]ssh -v -v -v -C -D 9999 [EMAIL="emily@coldowl.com"]Johnny5@coldowl.com[/EMAIL][/SIZE]

```
but then again, i'm in the US.  my server is behind a router with firewall disabled and the port forwarding all probperly configured.  
any ideas? my guess is china blocked port 22.

---

### Post by jimv on 2009-06-25
Use a different port.  For example, I forward port 54321 on my router to port 22 on my server to get around a port block at work.

EDIT

Also, I tried SSHing to your address, but it times out for me.  I'm in Oregon.

---

### Post by lmlypfan on 2009-06-25
Try changing the port.

---

### Post by afbase on 2009-06-25
Okay, I just upgraded my router's firmware to do port re-routing.  thanks guys.

[SOLVED]

---

### Post by fokmar on 2009-07-03
When i'm on a "strange" network I always use [http://webssh.strangled.net]("http://webssh.strangled.net/") in my webbrowser to connect with my ssh server. It's a ssh client on a website so when i use this i can create ssh connections but proxys or firewalls between me and and that site only see my connection with the website.

---

### Post by afbase on 2009-07-04
Thanks for the tip.  I just needed to reroute my ssh port.  I guess China has some ssh'ing issues on port 22

---

