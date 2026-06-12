---
title: "Problems with xubuntu in Ultra Sparc 5"
date: 2006-11-26
forum: Sun Sparc Users
---

### Post by edugonch on 2006-11-26
Hello, I have a problem with mi Ultra5, I instaled ubuntu 6 server, and I tried to install XUBUNTU (sudo apt-get xubuntu-desktop) but I can't make it work, I get this error "xf86MapPciMem: Could not mmap PCI memory
Inappropiate ioctl for device"
I look in several forums incluin this one, and I try all the possible answers to this issue, but I can't make this work, can some body help me with this problem please, I don't know what else to do, and I don't want to return to Solaris 10 :(.
THANKS1

---

### Post by netztier on 2006-11-27
> **edugonch said:**
> I look in several forums incluin this one, and I try all the possible answers to this issue, but I can't make this work, can some body help me with this problem please, I don't know what else to do, and I don't want to return to Solaris 10 :(.

I have also run into this problem on my Ultra5 with Ubuntu 6.10. I think it is X.org related - but I ran into other problems installing ubuntu-desktop on my U5, so I haven't yet been able to investigate further.

Debian Etch is said to run it's X.org on the U5, and **Ubuntu 6.06 LTS** did work ok on my U5, so by picking one of these, you don't have to return to Solaris.

best regards

Marc

---

### Post by edugonch on 2006-11-27
I found the answer, know my ubuntu works fine with Xfce

Look at this link

-----> [http://kristof.willen.be/?q=node/689](http://kristof.willen.be/?q=node/689)

It works for me and now I have X working :D.

---

### Post by netztier on 2006-11-27
> **edugonch said:**
> I found the answer, know my ubuntu works fine with Xfce

Look at this link

-----> [http://kristof.willen.be/?q=node/689](http://kristof.willen.be/?q=node/689)

It works for me and now I have X working :D.

Now that's cool!:D Thanks for the Info! I'll see tonight if I can work around it, too.

Here's more links related to this, found by following the ones in the document you referred to:

[Bug #8020 on freedesktop.org]("https://bugs.freedesktop.org/show_bug.cgi?id=8020")
[Bug #392312 on bugs.debian.org]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=392312")

regards

Marc

---

### Post by netztier on 2006-11-28
> **edugonch said:**
> I found the answer, know my ubuntu works fine with Xfce

Look at this link

-----> [http://kristof.willen.be/?q=node/689](http://kristof.willen.be/?q=node/689)

It works for me and now I have X working :D.


I have added this link and the others from my other posts to a bug report on launchpad.net:

[Bug #56427: Fatal crash on X startup on Ultra 10]("https://bugs.launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/56427")

regards

Marc

---

### Post by netztier on 2006-11-29
> **netztier said:**
> Now that's cool!:D Thanks for the Info! I'll see tonight if I can work around it, too.


YAY!

I tried as you suggested:

I got a new Xorg executable out of the xserver-xorg-core .deb from [packages.debian.org]("http://packages.debian.org/testing/x11/xserver-xorg-core"), from Debian testing.

I plainly copied it over the existing /usr/bin/Xorg, making sure that owner, group and mode matched the orginal and... 

Well, it works :-) Thanks a lot!

Marc

---

### Post by kingcharles1666 on 2007-03-08
Hi,

can you explain the commands you used to get and copy the files?
I have an ultra 10 with the same error but i am a bit of a noob so a step by step would be helpful
thanks

charles

---

### Post by kingcharles1666 on 2007-03-10
ok, so a little proud of myself as i managed to figure it out.
To help other noobs this how i did it:

I used my other pc running dapper for downloading the "xserver-xorg-core_1.1.1-19_sparc.deb" from the link above.
I then used the archive manager to open the .deb as an archive.
I then browsed to the "data.tar.gz/usr/bin" folder where i found Xorg.
I extracted Xorg to my desktop.
Now i had to get the file to my sparc machine running edgy server. I decided to use a floppy.
I used the archive manager again to tar the Xorg file because it was to big for a floppy.
I now had a Xorg.tar.gz file that I copied to a floppy
I put the floppy into the ultra 10.
From now on command line only :-)
sudo mount /dev/fd0 /media/floppy0 -t vfat
cp /media/floppy0/Xorg.tar.gz /home/sparkie (my home folder)
tar -xvf /home/sparkie/Xorg.tar.gz
sudo cp /home/sparkie/Xorg /usr/bin
startx

Job done!
next step: try to install Xubuntu desktop......

---

### Post by ve1uxe on 2007-03-13
All,

Thank you so much for finding the Xorg fix!!  I installed it on my ooooooooooold U10 w/384Mb of RAM and verified that X would start.  I finished installing the ubuntu-desktop and it fires up w/o any issues, woohoo!  

Now I've completed my task of getting Edgy to work on my Mac G3, Mac G4, Pentium 4, and Sparc systems (don't ask me why).  Thanks to the forums, all are working like champs :)

---

### Post by bryceharrington on 2007-06-14
Another suggested workaround is to unmount /sys before starting X.

---

