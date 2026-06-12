---
title: "Graphical connection to FTP on ubuntu server"
date: 2010-08-31
forum: Server Platforms
---

### Post by group256 on 2010-08-31
Hello,

I'm looking for a software in Windows which connects to FTP server on an ubuntu server. I understand there are softwares such as FileZilla, but there is one problem with them. I wanna watch my movies on FLY. Meaning I want to stream instead of COPYING them first and watching them.

In simpler words, just like what we have in Ubuntu--> CONNECT TO SERVER. As soon as you get connected Nautilus pops and you can do whatever you want same way as your own hard disk.

Thanks a lot.

Sam

---

### Post by BkkBonanza on 2010-08-31
I think you can just use your web browser for that. Most of them support ftp but whether they will auto-play a given movie I'm not sure. VLC can play an ftp stream but doesn't have anything much for browsing.

---

### Post by snek on 2010-08-31
Hmm in your usual file explorer just type in the adress like so:

[ftp://username:password@ip](ftp://username:password@ip)

FTP is not really meant for this though. 
I've tried what you mention, but never got it to work properly either. 

Right now I am running Ubuntu at work as well and use sshfs to mount my mp3 directory as a drive. That works perfectly, but I don't know if there are any sshfs clients for Windows.

If you want you can read the tutorial I wrote about this here:
[http://www.robotsystematic.com/2010/linux/nevermind-streaming-mount-your-mp3-dir-over-ssh-and-listen-to-your-music-at-work](http://www.robotsystematic.com/2010/linux/nevermind-streaming-mount-your-mp3-dir-over-ssh-and-listen-to-your-music-at-work)

---

### Post by snek on 2010-09-01
I just stubmled across this, a Hamachi gui for Ubuntu.
[http://www.haguichi.net/](http://www.haguichi.net/)

Using Hamachi you can easily setup a VPN network, which even goes through firewalls without having to do much configuring.

This would be your best and easiest solution I think, since there's a great hamachi client for windows.

[https://secure.logmein.com/products/hamachi2/](https://secure.logmein.com/products/hamachi2/)

---

### Post by group256 on 2010-09-01
Thanks a lot everyone, but honestly, it seems that there is no real easy way to use my file server in Windows the same way I can use it in Ubuntu. No discrimination but, Long Live Linux.

Thanks a lot for all the offers, I will definitely will give them a try.

Sam

---

