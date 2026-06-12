---
title: "Moving To Server 2008"
date: 2010-04-21
forum: Server Platforms
---

### Post by imbty on 2010-04-21
Hey, guys. I managed to set up a home server for the obvious file sharing, auto backup of files and streaming to PS3 with Server 9.10.

I even managed to set up an FTP and web server for fun with my domain pointing to it, but I think I'm gonna move to Windows. My dad has a copy of Windows Server 2003 and 2008, and I think I might have an easier time with that.

Atm, I have Webmin, but I keep getting errors about /etc/webmin not having enough disk space even though it does. 

I really wanna stay with Linux coz it was fun, but holy crap, it's giving me a headache again.

---

### Post by cdenley on 2010-04-21
Is there a request for support, or are you just commenting on your experience with ubuntu and webmin? If you use ubuntu again, I suggest sticking with ubuntu software, not thirdy-party stuff like webmin.

---

### Post by imbty on 2010-04-21
It's more like my experience with Ubuntu. Atm, my server is running headless. I use to be able to reboot and be able to VNC into it, but now I can't. I wanted to transfer some files around so I could reinstall, but like I said, Linux is giving me a headache.

I installed Webmin because it would be easier for me to configure Samba.

---

### Post by cdenley on 2010-04-21
Well I would help you with your VNC misconfiguration, but I guess you're not going to use ubuntu so there is no point. This section is for server **support**. "Ubuntu Testimonials & Experiences" would probably be a more appropriate place to share your experiences.

---

### Post by imbty on 2010-04-21
Like I said, I really want to stay with Linux. I might do a fresh install of Ubuntu once I read more on file permission. I think most of my problems were due to file permission being wrong.

---

### Post by cdenley on 2010-04-21
Some links that might help:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by koenn on 2010-04-21
> **imbty said:**
> H it's giving me a headache again.

> **imbty said:**
>  but like I said, Linux is giving me a headache.

paracetamol might help.

for recurring headaches, you might wanna go see a doctor.

---

### Post by Iowan on 2010-04-21
I presume you've seen [this]("https://help.ubuntu.com/community/WebMin") help page and the section:> WebMin was in Ubuntu until 5.10 Breezy Badger, and was then dropped because it is not compatible with the way that Ubuntu packages handle configuration files, and caused unexpected issues with people's systems.[eBox]("https://help.ubuntu.com/community/eBox") is another option.

---

### Post by imbty on 2010-04-21
I really want to use Windows Server 2008 for ease, but I'm really stubborn (this is why I hate riddles) and have decided to stick with Ubuntu.

I plan to purchase a 1TB hard drive soon (I'm really afraid of losing my photos since I take pictures and stuff). Once I get that, I plan to reinstall Ubuntu Server 9.10 without the ubuntu-desktop GUI. 

This forum has been great and very helpful. Atm, I'm fully satisfied with Mediatomb and Deluge for my streaming and torrent needs.

Samba's the best for file sharing, right? 

Btw, how come when i "mv /media/sdb1/file_here /media/sdc1/file_here2" it doesn't really move it? It seems it just copies it. Is it because of ownership? Thanks.

---

### Post by senor_smile on 2010-04-22
> **imbty said:**
> I really want to use Windows Server 2008 for ease, but I'm really stubborn (this is why I hate riddles) and have decided to stick with Ubuntu.

I plan to purchase a 1TB hard drive soon (I'm really afraid of losing my photos since I take pictures and stuff). Once I get that, I plan to reinstall Ubuntu Server 9.10 without the ubuntu-desktop GUI. 

This forum has been great and very helpful. Atm, I'm fully satisfied with Mediatomb and Deluge for my streaming and torrent needs.

Samba's the best for file sharing, right? 

Btw, how come when i "mv /media/sdb1/file_here /media/sdc1/file_here2" it doesn't really move it? It seems it just copies it. Is it because of ownership? Thanks.

I would assume that it's defaulting the mv operation to a cp operation since they're on two different physical drives.

---

### Post by Iowan on 2010-04-22
> **imbty said:**
> Samba's the best for file sharing, right? With Windows systems... 
But there's NFS for *nix - and SSH, and FTP also.

---

### Post by cdenley on 2010-04-22
> **imbty said:**
> 
Btw, how come when i "mv /media/sdb1/file_here /media/sdc1/file_here2" it doesn't really move it? It seems it just copies it. Is it because of ownership? Thanks.

It shouldn't. Are you sure? If you don't have permission to delete it from the source drive, an attempt to move it would fail. Obviously, it can't be removed from the source drive until it is written to the destination drive.

---

### Post by cdenley on 2010-04-22
> **cdenley said:**
> It shouldn't. Are you sure? If you don't have permission to delete it from the source drive, an attempt to move it would fail. Obviously, it can't be removed from the source drive until it is written to the destination drive.

Actually, I just tested it, and it will copy if you're going from one filesystem to another, then give you an error if you don't have permission to remove the source file.

---

