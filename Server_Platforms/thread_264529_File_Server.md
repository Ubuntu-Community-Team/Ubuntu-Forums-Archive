---
title: "File Server"
date: 2006-09-24
forum: Server Platforms
---

### Post by Fire on 2006-09-24
I have been using Linux for some time now but have never run a server.  I have been using Ubuntu for the last 4 months and have completely changed all my home systems to run Ubuntu.  Now I have gotten to a point where I really can use a centralized location for hosting files that I can get from any of my computers.  So I am looking to ubuntu server to set up a file server.  At the very least I would like to be able to access drives on the server from any of my other computers.  I just loaded the server software off of the alt installation disk.  I am not sure really where to head with this.  I am very new to setting up servers so any thought would be great..


Thanks

---

### Post by StormNet on 2006-09-24
What you want to do is set something up lin NFS so that you can have folders that are available on the network. There is a HOWTO in the Tips forum:

[http://www.ubuntuforums.org/showthread.php?t=249889](http://www.ubuntuforums.org/showthread.php?t=249889)

Hope that helps out.

---

### Post by MetalMusicAddict on 2006-09-24
I myself put Xubuntu-Desktop on my server and setup alot of SAMBA shares. I control it via VNC.

I have 4 (room for 8 wired + wireless) other computers that talk to it. 2 dual-boot windows. All shares work and all can print to the printer.

Hit me up if you need help/questions. Ill watch this thread also.

Some pics of my closet.

[[IMG]http://img167.imageshack.us/img167/2876/ssssdscf3426fh2.th.jpg[/IMG]](http://img167.imageshack.us/img167/2876/ssssdscf3426fh2.jpg) [[IMG]http://img167.imageshack.us/img167/1014/ssssdscf3429sr1.th.jpg[/IMG]](http://img167.imageshack.us/img167/1014/ssssdscf3429sr1.jpg)

---

### Post by Fire on 2006-09-24
hey everyone thanks for the quick response. I suppose I do like the idea of the xbuntu just because of the ease of use with the Gui for someone like me that is kinda new at it.. ofcourse the network file system sounds like it would work very well also..  If anyone else has any ideas on their favorite way of doing this I would be glad to hear it.

thanks

---

### Post by MetalMusicAddict on 2006-09-25
Its kinda up to you. What exactly are you trying to acomplish?

I have the server pictured just full of HD's for storage (little over 1 TB) and a printer hooked up to it. I have no keyboard, mouse or monitor hooked up to it and control it via VNC from other computers. I also have as many services turned off as I can. I could probally do better but everything runs fine. I share everything with SAMBA because I have windows machines connect to it also.

Can NFS (for linux boxes) and SAMBA (for windows boxes) run at the same time? Anyone?

I currently cant use CUPS to print because of some bug. I just use SMB and it works fine.

---

### Post by Fire on 2006-09-25
Well I am looking to run this on a low end 500Mhz system or maybe a 700Mhz system.  I figure the 500Mhz system would probably be sufficent as I don't believe I will need much in the way of resources.  Just HD's.  Now, I love the idea of running it through a VPN, though I have never set up anything like that in Linux.  Are there any Great How-To's for doing this out there???

---

### Post by nix4me on 2006-09-25
Yes, smb and nfs can run at the same time.

nix4me

---

### Post by MetalMusicAddict on 2006-09-25
> **nix4me said:**
> Yes, smb and nfs can run at the same time.

nix4me

Cool. I guess Ill look at using NFS for the linux boxes. Wait. what If I use SMB for printing? Guess it wouldnt matter. I just cant stop SAMBA from running.

---

### Post by jagosilver on 2006-10-03
I have a MacBook Pro and my wife will someday have a Macbook. I have a PC which will be surplus to requirements then but has about 760Gb over four hard drives (2x SATA, 2xIDE) that I would I like to use.

Having never used Linux before, I wondered how easy it would be to set this up as an Ubuntu file server for the Macs to access...?? :confused: 

Is it possible to do this and retain the data that's on these hard drives or would they have to be reformatted?

If anyone could point me to any tutorials or anything I'd appreciate it.

Cheers

Jago

---

