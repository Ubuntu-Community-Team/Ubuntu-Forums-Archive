---
title: "SSH Connection Refused - after upgrade?"
date: 2011-01-24
forum: Server Platforms
---

### Post by Tugi on 2011-01-24
Hi,

I've got a remote vServer for hosting a couple of files, also running apache on it, etc. (The point being that I can not physically access it ;) ). It's running Ubuntu Server 10.04.1 (64 bit).

Since installing a Teamspeak server yesterday (24/01/2011) and also doing 'apt-get update && apt-get upgrade' while I was on it, I can not access it via ssh after logging out.


I can remotely restart the server, which didn't help. 
I can however boot into rescue mode (where it boots in some kind of BSD I think) and then access the filesystem via ssh, but I cannot run any commands on the Ubuntu server (duh).

As far as I know, I updated ssh yesterday while running apt-get upgrade, but didn't really think twice about it.
I'm using the standard port (22), which is also noted correctly in /etc/ssh/sshd_config

Does anyone have any idea how I can "retrieve" ssh without reinstalling?

Cheers,
Tim

ps. yes, I know, next time before I upgrade, I'm using the backup feature in my web interface. 
Lesson learned. ;)

---

### Post by Tugi on 2011-01-25
Okay, so it turns out that openssh-server is only 'half-installed' and 'half-configured'.
Anyone have any idea how I can fix this w/o using ssh? Seems tricky, doesn't it? :D

---

### Post by James78 on 2011-01-25
I think one of these commands should help you out.
```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get purge openssh-server
sudo apt-get install openssh-server
```
If you have problems trying to remove it, you can force it to remove.
```
sudo dpkg -P --force-all openssh-server
```

---

### Post by Tugi on 2011-01-25
Thanks for your answer!

Is there a way that I can make the server execute these command lines w/o any SSH connection?
That's the main dilemma here ^^

---

### Post by James78 on 2011-01-25
Unless you have any other thing like a web interface (Webmin), some type of panel, or SSH (you don't have that one), you'll have to get at the server physically.. I hope you're able to do that.

---

### Post by sh1ny on 2011-01-25
That's why i always try to get servers with onboard IPMI or if not possible, by an addon card with ipmi. Saves lots of time and driving to the co-location center :D

---

### Post by papenpj on 2011-01-25
i am having a similar problem I just upgraded from 8.04 LTS to 10.04 LTS and now when I reboot I have no ssh access.

i ran all the commands james78 suggested and was able to get ssh access after rebooting.... However, to get ssh before then I had to physically go down and restart the ssh service.

I completely forgot about webmin being installed on mine as it just a home media server that I felt like putting random things on.

---

### Post by Really Bad Karma on 2011-01-31
@ James78 :

I had a similar issue where I could not get a 10.10 installation to ssh into another computer with a 10.10 upgrade. I kept getting that annoying "no route to host port 22" message.  

Using your advice here, I fixed my problems connecting as well.  

I am so glad for locating this posting, Thank you!

---

