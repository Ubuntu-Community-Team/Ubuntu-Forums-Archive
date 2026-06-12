---
title: "VNC and SSH, noob needs some help..."
date: 2006-07-08
forum: Server Platforms
---

### Post by forsaken163 on 2006-07-08
Okay, I'm trying to set up a secure way to VNC into my box. Basically, what I want to do is to SSH into my box using my SSH key (public one, I believe) and then run VNC from the command line, so basically only allowing VNC connections from localhost. Is there anyway to do this in Ubuntu? I'm pretty sure there is, but help would be awesome.
Thanks!

---

### Post by scxtt on 2006-07-08
what box are you trying to connect from?  one on your LAN or one from the 'outside'?

---

### Post by Appolusionist on 2006-07-08
> **forsaken163 said:**
> Okay, I'm trying to set up a secure way to VNC into my box. Basically, what I want to do is to SSH into my box using my SSH key (public one, I believe) and then run VNC from the command line, so basically only allowing VNC connections from localhost. Is there anyway to do this in Ubuntu? I'm pretty sure there is, but help would be awesome.
Thanks!

Check out this link below:
[https://help.ubuntu.com/community/VNCOverSSH]("https://help.ubuntu.com/community/VNCOverSSH")

---

### Post by forsaken163 on 2006-07-18
Okay, got everthying working, cept for an interesting problem...using Putty from a Windows Box and tunneling port 5901, my vncniewer queries seem to disappear into nothingness (ie: I don't connect, but nor do I get an error message). In OS X, I just used 
```
ssh IPADDRESS -L 5901:localhost:5901
```
and then logged in using localhost:1 and it worked just fine, but doesn't work on my PC. This leads me to believe it is a problem with Putty...but I'm not sure. Any ideas?

---

### Post by Appolusionist on 2006-07-23
> **forsaken163 said:**
> Okay, got everthying working, cept for an interesting problem...using Putty from a Windows Box and tunneling port 5901, my vncniewer queries seem to disappear into nothingness (ie: I don't connect, but nor do I get an error message). 

I think I had the same problem with my old windows box. Have you doublechecked whatever firewall you have to see if port 22 is accessible?

---

