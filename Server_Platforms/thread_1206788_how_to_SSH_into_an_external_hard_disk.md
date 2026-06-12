---
title: "how to SSH into an external hard disk?"
date: 2009-07-07
forum: Server Platforms
---

### Post by jespes on 2009-07-07
Hello,

I'm a linux noob with a simple SSH server on an Ubuntu 9.04 machine. Here's my question:

I'd like to connect an external USB drive and access it by SSH. Is this possible? When I try simply plugging in a USB disk, I'm unable to access it via SSH .

many thanks and best ,
JP

---

### Post by Daimanta on 2009-07-07
So you are able to access the machine but you are not able to access the external device?

In that case, I think you need to mount the device first. The device has a name like /dev/sda1 but you can learn which devices are connection by using the command (sudo) fdisk -l.

---

### Post by TwiceOver on 2009-07-07
Did you mount the disk after you connected it?  If so is the disk usable directly from the terminal?

---

### Post by guilly on 2009-07-07
You don't really SSH into a specific disk, you SSH into the operating system. Once you have SSH into the box it's like you are physically at the computer. From there you will have to mount the disk using the mount command. 

So really the problem here is that your disk is probably not mounted. Do a man on mount it's pretty straight forward.

---

### Post by MystaMax on 2009-07-07
USB drives do not automount on Ubuntu server. You'll have to mount it manually. You'll most likely mount in your /media/ folder. Take a look at this web page:

[https://help.ubuntu.com/community/Mount/USB#Manually Mounting]("https://help.ubuntu.com/community/Mount/USB#Manually Mounting")

---

### Post by jespes on 2009-07-07
many thanks for the quick replies. 

some answers:

daimanta: i can ssh into the machine and see all my "home" folders perfectly. but i can't see the external drives. the external disk is mounted (it appears in the "places" list on the left-hand side of the file browser on the ubuntu machine itself) 

twiceover: apologies, here's where my nooby-ness shows: i don't know how to check to see if the disk is accessible from the terminal.  the external disk is, however, accessible from the ubuntu desktop...

gully: thanks, what command(s) should i use to mount the disk from terminal? 

many thanks again and best, .jp

---

### Post by jespes on 2009-07-07
mystamax: many thanks, i didn't see your note before sending my previous reply. i will read that how-to right now.

(fyi if it matters: i'm not using ubuntu server, but plain-vanilla ubuntu 9.04)

---

### Post by MystaMax on 2009-07-07
If you're using Ubuntu 9.04 desktop version, then the drive should automatically be mounted when plugged in. If its not automounting and is an NTFS formatted drive, its possible the drive was not properly unmounted.

A quick fix for this is to plug it into a Windows PC, and use the "Safely remove hardware" wizard. You can also forcefully mount the drive, but I can't remember the command for that right now.

If you can browse to the USB Drive using Nautilus, it'll tell you the path to your USB Drive. For example, when I mount my usb flash drive, its @ /media/DIESEL/. Check the media directory after plugging in your drive, and see if you see any new directories.

---

### Post by jespes on 2009-07-07
success! 

many thanks, i've got it working. here is explanation:

the external hdd does mount automatically, but doesn't show up in my "home" folder, which seems to be a prerequisite for me to access it remotely via ssh. so, i followed the directions suggested by mystamax and created a hdd mount point *within" my home folder. that enabled me to see the hdd when logged in via ssh.

once again, many thanks to all.
best, jp

---

### Post by dragos2 on 2009-07-07
Semantics.. you don't login into a disk! You mount a disk, then you can use a terminal
if you like and cd to it.

---

### Post by jespes on 2009-07-07
> **dragos2 said:**
> Semantics.. you don't login into a disk! You mount a disk.

dragos: nobody in this thread said "login" to a disk, did they?

---

### Post by ducksun43 on 2009-07-07
hmm ... well, first you mount the disk (just plug it) and then you can use ssh to access you computer [http://sunoano.name/ws/public_xhtml/ssh.html](http://sunoano.name/ws/public_xhtml/ssh.html)

---

### Post by jespes on 2009-07-13
ugh.

I thought I had this working, but I've run into a new problem: My Ubuntu server sometimes "forgets" that I should have write privileges on the external HDD when SSHing into it. 

In other words, sometimes I can write to the HDD via SSH from another machine. But then a few minutes later, it will tell me I don't have permission to modify this or that file on the same disk.

Any thoughts on what might be causing this, and how to overcome? My setup is described earlier in this thread.

Many thanks!

---

