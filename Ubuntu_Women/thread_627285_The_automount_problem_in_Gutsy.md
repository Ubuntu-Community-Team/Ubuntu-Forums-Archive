---
title: "The automount problem in Gutsy"
date: 2007-11-29
forum: Ubuntu Women
---

### Post by NWAmama on 2007-11-29
I'm trying to get my iPod going on here.  I figured I needed to get the automount problem fixed first and then decide which route I'm going to go on software for the iPod.  I'm very new at this so any directions will need to be spelled out very clearly for me.  I'm open to c&p'ing code into the terminal or if you have a way for me to do it graphically that is fine too.  

I've already tried the WINE iTunes option, it was a bust.  I'm up for using Amarok, I also have GTKpod installed if I need to go that route. Feel free to make suggestions! 

Thanks, 

NWAmama.

---

### Post by Ek0nomik on 2007-11-29
I have a Creative, so I don't have any experience with iPods.

But, perhaps these will help:

[http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu](http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu)

[http://www.linuxjournal.com/article/9266](http://www.linuxjournal.com/article/9266)

[http://ubuntuforums.org/showthread.php?t=298530](http://ubuntuforums.org/showthread.php?t=298530)

---

### Post by NWAmama on 2007-11-30
Thanks for your response. 

I tried the suggestions provided in your first link.  I think my iPod is formatted incorrectly for Linux? 

Here's what my gedit says about the /dev

/dev/sda1 / ext3 rw,errors=remount-ro 0 0

Seems that it should be sdc1 or sdc2?  I didn't see a vfat file on there either.  That could be because I've tried several other things that I have seen in some different threads on the Ubuntu forums and some code that I pasted in could have deleted the vfat part of the code?  I'm not making any sense and I really don't know what I'm talking about.  I'm very confused :( 

The point is, I can't get it to mount at all.  How do I fix that?

I just want it to work!!

---

### Post by Ek0nomik on 2007-11-30
> **NWAmama said:**
> Thanks for your response. 

I tried the suggestions provided in your first link.  I think my iPod is formatted incorrectly for Linux? 

Here's what my gedit says about the /dev

/dev/sda1 / ext3 rw,errors=remount-ro 0 0

Seems that it should be sdc1 or sdc2?  I didn't see a vfat file on there either.  That could be because I've tried several other things that I have seen in some different threads on the Ubuntu forums and some code that I pasted in could have deleted the vfat part of the code?  I'm not making any sense and I really don't know what I'm talking about.  I'm very confused :( 

The point is, I can't get it to mount at all.  How do I fix that?

I just want it to work!!

What you showed me is /dev/sda1, and the mount point is /.  This means that this is your root filesystem, **not** your mounted iPod.

I have to take off, but I will try to take a look at this tomorrow for you.

---

### Post by NWAmama on 2007-12-02
Scratch this...it was a bad usb port in the front.  I plugged it into the back of my computer and it loaded up just fine...only I can't get sound.  I'm off to search how to convert my files so that GTKpod can read them.  Thanks for your help :)

---

