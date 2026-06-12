---
title: "Error 21: Selected disk does not exist.  After 8.04 install."
date: 2009-07-22
forum: Server Platforms
---

### Post by blsmit on 2009-07-22
Hi all.  
   
  I’ve run into an Error 21: Selected disk does not exist after installing ubuntu 8.04 LTS server 32-bit.  
   
  I’m loading ubuntu on a MSI Nettop 100 with a 320GB WD HDD with NO cdrom.  I successful used unetbootin on a USB stick to install ubuntu 8.04 desktop.  However, when I put  ubuntu 8.04 LTS server 32-bit, the install went fine, but upon reboot I received Error 21.  I used the guided- use entire disk partition method.  
   
  Let it be known that I am using this system as a media/web/print server and 9.04 installed and worked but there was no streaming music from Jinzora, Ampache, or (even an install) from gnump3d.
   
  Also I am using the 32 bit version as recommended by [http://ubuntuforums.org/showthread.php?p=5178754](http://ubuntuforums.org/showthread.php?p=5178754).  

Can anyone help.  I have been doing research but most of the solutions are for systems with dual boot.  Mine is not.

Thanks in advance to anyone who helps.

blsmit

---

### Post by zipherx on 2009-07-22
I have had a similar problem with my system, but i have w7 as other os and it makes this (somehow invisible to unetbootin) partition that the installer cannot handle.

Try and check your fstab, if it is the right partition. I am not really sure what utility you can use to get a list of all partitions, hidden included. Would it be possible to boot to the live version and use gparted?

Another thing you can check, is if in the bios, that there is a way that another device is set as first boot device (like an on-board sata raid controller). I have seen cases where this would mess up the way the partitions listed.

---

### Post by blsmit on 2009-07-22
zipherx, 

I'm not at the computer right now but I will post the fstab in 30 mins or less.  

I don't know if booting into the live version would be possible, if there are directions (howto) some where I will gladly follow.

I went through the BIOS, everything in there says that the HDD is the first and only boot device.

Thanks for your help, and I will post (edit this post) in half an hour
blsmit

---

### Post by blsmit on 2009-07-22
I can't find how to display the fstab.  Can I get a link to directions?

Thanks

---

### Post by cariboo on 2009-07-22
If you can create a usb device with the Ubuntu Live CD you can use [this]("http://ubuntuforums.org/showthread.php?t=224351") howto to repair the problem.

---

### Post by blsmit on 2009-07-23
cariboo907 thanks for the post.

I've am currently struggling with getting a streaming music server working. (being able to listen to music from my server over the internet without itunes or vlc or windows media).  

I tried Sockso but it just plain didn't work.  Are there any suggestions for a good streaming media server.

Thanks 
blsmit

---

