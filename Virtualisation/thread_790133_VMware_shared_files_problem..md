---
title: "VMware shared files problem."
date: 2008-05-11
forum: Virtualisation
---

### Post by benc123 on 2008-05-11
Hello,I am virtualizing XP on my Ubuntu 7.10 desktop. I have VMware tools installed. But when i go to VM>Settings>Options i dont have the SHARED option visable.

I think i need to get  "Module vmhgfs" working, as it can't be found.

I am using VMware version 1.0.4.

Can anyone help me to share files between my desktop and VMWare?

Thanx Benc123

---

### Post by fjgaude on 2008-05-11
Please tell us what version of Ubuntu you are using.

Since you have vmware 1.0.4 installed we will use that.

Setting up file sharing is differenct between 7.10 and 8.04. It's easy once you understand principles. But until then, even the Sticky at the top of this Forum is overwhelming, eh? But consider, what we are doing is cutting edge. One of these days, in a year or so, it'll all be more automatic.

You might wish to read, study this forum post:

[http://ubuntuforums.org/showthread.php?t=776086](http://ubuntuforums.org/showthread.php?t=776086)

And get a feel at what we will be doing to get to where you wish to go.

---

### Post by Nampla on 2008-05-14
The file sharing feature of vmserver doesnt work (at least i never have been able to get it to) I think is is disabled by vmware.  I have had great sucess with just using Samba.  
Do: sudo apt-get install samba
then assign a user for samba 
sudo smbpasswd -a "system_username" (this needs to be both a win user and a linux user)
assign a folder to share on the linux box with win
on the windows side ensure that you have the user set up identically with password and name. (this is important)
then re-boot windows and look for the folder.
if that doesnt work there are other guides available on google.  Be careful and find your distro. cuz many of the work arounds they use are fixed by newer versions of ubuntu. I am using 8.04 and file share is a breeze with samba (no need to edit smb.conf)
good luck

---

