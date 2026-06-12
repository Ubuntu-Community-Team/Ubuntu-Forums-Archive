---
title: "what is a good easy to use Video editing program?"
date: 2008-05-31
forum: Ubuntu Studio
---

### Post by Foxfire on 2008-05-31
any suggestions

---

### Post by tamoneya on 2008-05-31
if you want something simple you should use kino.  If you find that a bit lacking I would go to something like cinelerra instead.

---

### Post by cotcot on 2008-05-31
Kino, Kdenlive or Blender Video Sequence Editor. (I prefer the last one).

---

### Post by Qrikko on 2008-05-31
I would recommend having a look at lives too it seem pretty nice and the little I tried it (just tried it to put together rendered files from Maya (i.e. a group of .png pictures to a .avi and compress)

But it's nice interface and it was easy to grasp, but I think it is still young and maybe not as full featured :)

I checked a little it seem to have been around since 2002 and as I take it it is designed to be easy but still full featured.. or something like it.. for some light digested reading and so on check [http://lives.sourceforge.net/](http://lives.sourceforge.net/)

---

### Post by thomashome on 2008-05-31
[[LEFT][LEFT]How do you get kdenlive in ubuntu hardy it seems that all the good programs are for old ubuntu systems. I only had 2 goes with gusty then I left ubuntu and came back in 08 so I kinda have ubuntu as my only os one one of my computers because it is sooo good!
But I thought the sound & video stuff was lacking what I like to call maitivity (macintosh creativity) where you can have nothing and change it into a masterpiece.Where as ubuntu does not have that!][/LEFT][/LEFT]

---

### Post by hodenkat on 2008-06-02
Good luck.


Plugged my camcorder into the port running Hardy, nothing happened.

Launched Kino and got an error on the IEEE1394 control tab saying something about raw1394 not loaded or no read write access.

Rebooted into Windows, plugged camcorder in, dialog box came up asking if I wanted to capture video using Windows Movie Maker...
so I did!

It's been two months and I still can't use Kino to capture video.
I've been to dozens of links, tried everything I could find (believe me when I tell you I've tried EVERYTHING!) and nothing has worked for me yet. When it comes to video capture, stick with Windows kids...or be prepaired to sudo your brains out!

---

### Post by remeeraz on 2008-10-14
> **hodenkat said:**
> Good luck.


Plugged my camcorder into the port running Hardy, nothing happened.

Launched Kino and got an error on the IEEE1394 control tab saying something about raw1394 not loaded or no read write access.

Rebooted into Windows, plugged camcorder in, dialog box came up asking if I wanted to capture video using Windows Movie Maker...
so I did!

It's been two months and I still can't use Kino to capture video.
I've been to dozens of links, tried everything I could find (believe me when I tell you I've tried EVERYTHING!) and nothing has worked for me yet. When it comes to video capture, stick with Windows kids...or be prepaired to sudo your brains out!

That's because Kino is telling you that you need to configure your Firewire subsystem to allow full access.

[http://ubuntuforums.org/showthread.php?t=946708](http://ubuntuforums.org/showthread.php?t=946708)

---

### Post by cotcot on 2008-10-16
> **thomashome said:**
> [[LEFT][LEFT]How do you get kdenlive in ubuntu hardy it seems that all the good programs are for old ubuntu systems. I only had 2 goes with gusty then I left ubuntu and came back in 08 so I kinda have ubuntu as my only os one one of my computers because it is sooo good!
But I thought the sound & video stuff was lacking what I like to call maitivity (macintosh creativity) where you can have nothing and change it into a masterpiece.Where as ubuntu does not have that!][/LEFT][/LEFT]
Kdenlive is simple in the repositories (of hardy).

---

### Post by Bucky Ball on 2008-10-16
> **hodenkat said:**
> Good luck.


Plugged my camcorder into the port running Hardy, nothing happened.

Launched Kino and got an error on the IEEE1394 control tab saying something about raw1394 not loaded or no read write access.

Rebooted into Windows, plugged camcorder in, dialog box came up asking if I wanted to capture video using Windows Movie Maker...
so I did!

It's been two months and I still can't use Kino to capture video.
I've been to dozens of links, tried everything I could find (believe me when I tell you I've tried EVERYTHING!) and nothing has worked for me yet. When it comes to video capture, stick with Windows kids...or be prepaired to sudo your brains out!

Or be prepared to check the 'read me' file which is included with the documentation for raw1394 and shows you how to set up /dev/raw1394. It is a three step process with three sudos:

```
sudo modprobe raw1394
sudo adduser skulker disk
sudo chmod 666 /dev/raw1394

```You can find the read me by pasting this in a terminal:

```
nano /usr/share/doc/libraw1394-8/README.Debian
```Maybe check the read me in future before making rash statements or as you say, stick to Windoze. :)

---

### Post by nowardev on 2008-10-16
i used kdenlive...after i have solved some crash problems..

i have seen blender and if you select the video sequence editor it's the same of other video editor and it's very very powerfull 

so easy job, and avi files  = kdenlive 
complicated job and every formats = blender

---

### Post by marpola on 2008-10-16
This was just the info I was looking for. I was able to install /dev/raw1394 and
turn on Kino for capture from my Panasonic DV camera but it did not find the camera connected, just waiting for me to press play.

After 
grep IEEE1394 /boot/config-`uname -r`
CONFIG_IEEE1394_RAWIO=m is still m as well as the rest

What do I do now?
This is thje first time using this firewire card.
Ubuntu Studio.

---

### Post by wkulecz on 2008-10-17
> That's because Kino is telling you that you need to configure your Firewire subsystem to allow full access.


If the system detects a firewire subsystem, why can't it be automatically configured to actually be useful?  All this arcane knowledge needed to make basic tasks work is why Linux will never be mainstream.

For example, I have an pair of SAA7134 based capture cards,  I understand the problem as the driver complains about it and suggests the solution (if you know enough to read the messages with dmesg after booting).  But surprise, /etc/modules.conf no longer exists in 8.04.  I stumbled onto /etc/modules/options and put the "option saa1734 card =42,42" line in there and got it working, but this is ridiculus, same as changing from /etc/conf.modules to /etc/modules.conf was.

The arcane crap you have to know is bad enough, but when its a moving target like this, frustration and a return to Windows quickly beckons the non-dedicated geek.

--wally.

---

### Post by Bucky Ball on 2008-10-17
> **wkulecz said:**
> If the system detects a firewire subsystem, why can't it be automatically configured to actually be useful?  All this arcane knowledge needed to make basic tasks work is why Linux will never be mainstream.

For example, I have an pair of SAA7134 based capture cards,  I understand the problem as the driver complains about it and suggests the solution (if you know enough to read the messages with dmesg after booting).  But surprise, /etc/modules.conf no longer exists in 8.04.  I stumbled onto /etc/modules/options and put the "option saa1734 card =42,42" line in there and got it working, but this is ridiculus, same as changing from /etc/conf.modules to /etc/modules.conf was.

The arcane crap you have to know is bad enough, but when its a moving target like this, frustration and a return to Windows quickly beckons the non-dedicated geek.

--wally.

In an open source world this wouldn't be a problem so guess we can't really blame the Linux community ... :)

---

