---
title: "just installed server"
date: 2007-01-30
forum: Server Platforms
---

### Post by jrock2004 on 2007-01-30
Ok I got the server edition running. I installed xorg and configured that. Due to this being a server would like fluxbox. when I do

sudo apt-get install fluxbox

E: Couldn't find package fluxbox

Now from that it sounds like it is looking on cd. How do I change that? Thanks

---

### Post by jkeyes0 on 2007-01-30
sudo nano /etc/apt/sources.list

---

### Post by jrock2004 on 2007-01-30
ok and am I suppose to comment out the cdrom one?

---

### Post by jrock2004 on 2007-01-30
now I just did apt-get update and it is going online to get packages. so I am not sure whats wrong here

---

### Post by jkeyes0 on 2007-01-30
comment out the CD-rom one (with a #), then remove the comments from pretty much every other line beginning with "deb". That should get you access to the main repositories, security patches, updates, and backports at the very least.

Edit: If you did an apt-get update and it's finding things online, you should be good to go. apt-get upgrade should get you the newest patches/packages based upon what you've got installed.

---

### Post by jrock2004 on 2007-01-30
still a no go

if not on the CD it wont install it

---

### Post by jkeyes0 on 2007-01-30
It could be your network settings are not configured properly. What do you get when you type "ifconfig" in a terminal? (Looking for something like "eth0" and a inet address)

---

### Post by jrock2004 on 2007-01-30
I am getting proper IP address. Like I said pings and the update went out to internet

---

### Post by jkeyes0 on 2007-01-30
In that case, can you post the contents of your /etc/apt/sources.list file?

---

### Post by jrock2004 on 2007-01-30
I figured it out. What I did after install was dones was do the apt-get update

after that I edit my sources file

I forgot that after that I have to do apt-get update again so it will go get packages

noob moment sorry

---

### Post by jkeyes0 on 2007-01-30
Very nice. So you're getting fluxbox now?

---

### Post by jrock2004 on 2007-01-30
yes it is installed but now I have to figure out how to start it. I will post a new topic for that

---

### Post by jkeyes0 on 2007-01-30
Installing fluxbox should have installed xorg and xserver-xorg, so to start it, you should only have to type "startx".

---

