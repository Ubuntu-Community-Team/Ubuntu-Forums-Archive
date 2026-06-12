---
title: "Connecting two laptops with a phone cord (one with Ubuntu, one with Linux)"
date: 2008-08-31
forum: The Cafe
---

### Post by Diana_Woods on 2008-08-31
Hi All;

I need to use a phone cord to get media files off of my friend's laptop w/ windows onto my laptop with Linux (Ubuntu)

His computer is totally messed up, and we want to get his media in a safe place before putting linux on it. We are out in the country, no wireless... trying to think of how to utilize whats available. 

I am new to linux and still unaware of what it can do for me. Is this possible?

thank you in advance!

---

### Post by fiddler616 on 2008-08-31
First of all, I'm sorry you mistyped your title, you're probably losing views because of it.
Second of all, that sounds iffy at best. I'm not sure using RJ11 to network two Windows computers together is possible, let alone easy, because the modems want someone to call. If you have Cat5, that'd be better, though they'd need to be crossover, and I'm guessing you don't because of the title.
Would it be easier to connect to the Internet with both of them (I guess you'd need separate phone lines...a friend's house?), and then just use a client like Hamachi to swap files? Or just email a bunch of attachments?
-------------
Oh. I'm an idiot. Disregard the first half unless this fails:
Get an Ubuntu Live CD (which you should already have, if you're installing Ubuntu), pop it in, boot off it, hit "Try Ubuntu with no changes to your computer" at the prompt, enter the CD-ified Ubuntu, make sure most of your hardware works (or else a different distro might be better), and then just copy all the important stuff onto a USB drive or something. Or burn CDs. Or whatever.

---

### Post by mrsteveman1 on 2008-08-31
Best bet is a crossover ethernet cable or 2 ethernet cables and a switch. Some ethernet cards will do the crossover for you though in which case it doesn't matter what you use.

You could also use an rs232 DB9 null modem cable but that gives you only about 13KB/s at best.

Most boxes don't have parallel ports anymore but they were fast when you could link stuff with them.

They do make USB transfer cables that will work for this purpose.

You could also burn stuff to a CD or DVD if you can do that.

You can also take the drive out and stick it in some portable drive case and connect it to the other machine.

---

### Post by Diana_Woods on 2008-08-31
I tried using an external hard drive with his files on it, but Ubuntu will not mount it. I am aware of this possibility but was hoping to use my situation as an opportunity to learn a thing or two about networking.  

The error is something to do with NTFS, that it is "already in use." I am kind of casting in the dark... so i wrote in "ps" and "top" in the terminal which didn't include NTFS.

---

### Post by toupeiro on 2008-08-31
A cut and paste of the actual error would be very helpful, but short of that try these steps.  This is all CLI based, so open a terminal window:

First, lets see what ubuntu sees as the NTFS disk:

type:>  sudo fdisk -l

It should give you all the information about the various hard drives and partitions on your system.  Find the one that is the same size as your external disk.  Tip:  USB2 drives will likely come up as SD* drives and not HD* drives.

now, lets do a little bit of staging.  Lets make a directory to mount to:

type:>  sudo mkdir /mnt/tmp_ntfs

Now lets just try a mount:

type: > sudo mount /dev/sd***# **/media/tmp_ntfs/ -t ntfs -o nls=utf8,umask=0222

*# is equal to the two characters that identify your NTFS partition.  e.g. sdb1 or sdd1)

If you get no errors, try to navigate to /mnt/tmp_ntfs and type:>  ls

do you see files?



option b: networking..

Unless you are comfortable with IP addressing, I would not recommend the crossover cable method, though it would work. My recommendation is to get a good router/switch, like a linksys, something with some on-board intelligence, and let it issue a DHCP address to your machines.  Chances are you will get more life out of the switch than the crossover cable.

We're assuming that his windows machine can still boot at all.  If it can, go to his drive in a windows explorer window, Share his drive and change the sharing properties to everyone-full control.  You should then be able to see it from your ubuntu machine if you have samba installed.

If his windows install is totally hosed, boot to an Ubuntu live CD.  

There are a million ways to do this, but I'm going to demonstrate the way I prefer.

**On your machine:**


Type:
> sudo apt-get install ssh-server
*if you already have ssh-server installed, you can bypass the step above.*

then type:
> ifconfig eth0  or eth1 if you have multiple network cards, depending on which you are using, and note your inet address

also, make sure you have an idea of where you want to (make a directory in your home.  for the sake of an example, try:

> mkdir ~/temp_drive
[B]
On the Live-CD machine:[/B]

from the terminal window, change directory to where the windows files are located (/media/###)

Now, if you want to copy everything in and below that directory, type the following command:> scp -r * youraccount@yourinetaddress:/home/youraccount/temp_drive

where youraccount equals your user name on your ubuntu machine, and yourinetaddress is the ipaddress you noted from the ifconfig command above.

You will be prompted for your password one time.

If you have individual files, use the above command without the -r, and instead of *, type the filenames or wildcards (*.whatever) of the files you want to copy.


Are there other ways to do this? yes..  But this way shows you some networking and brushes up on your CLI skills, which you seemed to have an interest in doing. :)  Also, ssh and scp are UNIX/Linux platform agnostic, meaning you can do this from ubuntu to ubuntu, redhat to slackware, solaris to HP/UX, and the ssh commands will work just as indicated above.

---

### Post by Slug71 on 2008-08-31
Id say burning everything to cd might be easiest if you dont come right with the externdal hd.

---

