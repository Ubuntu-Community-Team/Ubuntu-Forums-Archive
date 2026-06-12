---
title: "Some Server help please before i give up"
date: 2014-07-09
forum: Server Platforms
---

### Post by do.marmor on 2014-07-09
Hi first excuse any grammar/ typing errors englich is not my native language 

i been sitting 2 weeks now trying to get this server to work as i want it to , i think i been reading every manual on the internet soon, and is about to give up but thought i write here first , i might be over explaining some

What im trying to do..
[I]simple file charring or NAS , but atm until i get new hard-drives whiteout RAID,(I want to set it up and try it before i buy hard drives that cost a fortune)

Simple put i want to be able to share at least one internal hard-drive in the workgroup and it should be accessible on all computers in the network windows and linux alike i also want all usb drives i plug in to be mounted and shared [/I]

atm i got a usb drive shared on my windows tower someting i wont need when server up and running

Im going whit a server instead of pure nas software because i also going to let it run a web server for testing designs im using xammp for windows for that atm besides a server can do more then a nas can

i plan to cross over to linux as much as possible, been running linux on my laptop for a year now however to my knowledge i do not need any help setting up the web server but file server seems impossible.

=======================
I assume i should use samba to set up the share. I can get windows to see the server and shares but never suceded to actually conect also looks like i only can share folders in samba not drives

playing around i broke my system so time to reinstall and start from beginning again, last try now

[I]can someone please direct me to a simple dummy guide for this, looks like i need one , I appreciate any good advice u might have to
[/I]
my skills on computers in general advanced but on linux total noob , im using ubuntu 14,04 server fully updated and xfce desktop installed to make some tasks easier.

---

### Post by Bucky Ball on 2014-07-09
*Thread moved to **Server Platforms**.*

You might have better luck here. Even though you're new on the forums you seem to be fairly across Ubuntu. There are many knowledgeable users here who I'm sure will be able to help with your support issue. 

Little confused with what your actual support request is. You are wanting to set up this server now or in the future and are researching? If you want to set something up now, what hardware are you intending to use for the server exactly? 

You mention RAID; is that in the future when you get other hard drives? What equipment are you using now that you have been struggling with for two weeks? ;)

---

### Post by CharlesA on 2014-07-09
I've used this for setting up Samba and it's worked fine for me.
[http://charlesauer.net/tutorials/ubuntu/samba3-ubuntu.php](http://charlesauer.net/tutorials/ubuntu/samba3-ubuntu.php)

What do you mean you can see the folders in Samba but not on the drives themselves?

---

### Post by lukeiamyourfather on 2014-07-09
If you haven't yet check this out.

[https://help.ubuntu.com/14.04/serverguide/](https://help.ubuntu.com/14.04/serverguide/)

Specifically this page.

[https://help.ubuntu.com/14.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/14.04/serverguide/samba-fileserver.html)

That should be exactly what you're looking for to share a directory (or drive) with all users on a network. Now getting it to share whatever USB drives get plugged in is another story. I wouldn't do that for many reasons, security for one. I also think automatic USB drive mounting is disabled on Ubuntu Server by default.

---

### Post by do.marmor on 2014-07-10
thanks for the reply , Charles page was new the other two i already been reading however reading them again made me see stuff i mist earlier, so ty both for the links ,

atm im working my ass of so might take me some time to try again if still problem i will ask here as for [COLOR=#000000]security [/COLOR]it wont be a issue the server can always be blockt from internet in the firewall and the files thats going to be stored is mostly movies music manuals so no problem if all in the home network can access it , if i need to store more private files i can always password protect that folder or drive i store it on when that day comes.

wishing Linux had a easier way to [COLOR=#000000]share [/COLOR]folders in the local network ,

---

### Post by CharlesA on 2014-07-10
Well, there are different methods of sharing files, I think nautilus-share is still around, but it conflicts with Samba and can cause issues down the line.

If you want to set up the firewall, check out this guide:
[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by do.marmor on 2014-07-15
its weird just as i was going to post my config file and ask for help i solved the problem, 
it was permissions problems  and to make tings easier i made the drive auto mount, seeing that drive is mostly sharing to windows computers its in fat32 idk if good or not but all is working now so ty guys for the advice and links much appreciated. :)

---

### Post by Bucky Ball on 2014-07-16
Thanks for sharing the fix. Please mark the thread as solved to help others by following the instructions in the second link of my signature. ;)

---

### Post by lukeiamyourfather on 2014-07-16
> **do.marmor said:**
> its weird just as i was going to post my config file and ask for help i solved the problem, 
it was permissions problems  and to make tings easier i made the drive auto mount, seeing that drive is mostly sharing to windows computers its in fat32 idk if good or not but all is working now so ty guys for the advice and links much appreciated. :)

The disk file system doesn't matter because the file sharing clients are talking through a protocol like SMB. I wouldn't use FAT32 for a disk in a Linux system because it's not native to Linux and it has a lot of limitations like max file size of 4GB. Ubuntu's default file system is ext4.

---

