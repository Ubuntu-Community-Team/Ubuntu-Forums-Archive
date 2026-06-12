---
title: "how to scp into ssh protected server"
date: 2009-07-12
forum: Server Platforms
---

### Post by goneskiing on 2009-07-12
I have a linode vps running ubuntu 9.04 - it is set up to allow me to ssh in from my laptop without password.  I ssh with no problem.  But now I want to scp web files onto the server but get Port 22 connection refused.  

Any suggestions ?

---

### Post by littlegreiger on 2009-07-12
If you're connecting without a password that probably means you're using key authentication, therefore you need to make your scp client aware of the key that you use. 'm not sure how to do this with a linux desktop but with windows you'll have to use a client like WinSCP that allows key-based authentication.

---

### Post by bernied on 2009-07-13
I have this in my /etc/ssh/sshd_config:
```
Subsystem sftp /usr/lib/openssh/sftp-server
```
Is scp the same as sftp? I always thought it was.

---

### Post by doas777 on 2009-07-13
just put 
```
ssh://user@<servername>
```in a nautilus address bar, and it should take you to / on the target ssh server. runs over sftp.

---

### Post by goneskiing on 2009-07-13
> **doas777 said:**
> just put 
```
ssh://user@<servername>
```in a nautilus address bar, and it should take you to / on the target ssh server. runs over sftp.

I'm confused by some of this - I can ssh into the server just fine but I want to copy a folder of files from my laptop to the server so I think I need scp - now it seems scp runs on ssh but my ssh is on port 5555 with most of the other ports closed by a firewall.  I tried scp -p 5555 .... but it keeps coming back with a port 22 refused - does scp automagically force it to port 22 ?  what to do ?

---

### Post by doas777 on 2009-07-13
> **goneskiing said:**
> I'm confused by some of this - I can ssh into the server just fine but I want to copy a folder of files from my laptop to the server so I think I need scp - now it seems scp runs on ssh but my ssh is on port 5555 with most of the other ports closed by a firewall.  I tried scp -p 5555 .... but it keeps coming back with a port 22 refused - does scp automagically force it to port 22 ?  what to do ?

if you are running on prt 5555 then you want to put in 
'ssh://username@servername:5555'

---

### Post by goneskiing on 2009-07-13
> **doas777 said:**
> ok, I've installed openssh-server on my ubuntu server 13of2. now from my ubuntu laptop, i want to copy some files up, so on the laptop, i open nautilus. then in the nautilus addressbar, I type 'ssh://myusername@13of2' and press enter. nautilus will pop up a window asking for my password, and it then connects. I can now see the root of my server in the nautilus window.

if you are running on prt 5555 then you want to put in 
'ssh://username@servername:5555'

it really is that simple. you only need a sepperate client for scp if you are using windows (winscp) as your client.


I don't use windows, I use linux on the client like everyone should :)

[SOLVED] "-p" with ssh  "-P" with scp  it was that simple

---

