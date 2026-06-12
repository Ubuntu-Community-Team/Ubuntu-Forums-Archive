---
title: "Linux on HP Stream 7 x86 Tablet"
date: 2016-06-10
forum: Ubuntu/Debian BASED
---

### Post by coen.human on 2016-06-10
[Date Posted : 2016-06-10]
These are notes I compiled to get Linux (Ubuntu Mate 16.04) running on the HP Stream 7, feel free to use for your own projects and devices. I will keep it updated as I work on this project of mine.

I'm new to the forum, so I hope this thread is fine and where it was posted. Seemed like the Ubuntu Phone and Tablet was mostly for Ubuntu Touch. 
 
**Websites - Sources** 

[LIST]
[*][http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188](http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188) 
[*][http://ubuntuforums.org/showthread.php?t=2253934](http://ubuntuforums.org/showthread.php?t=2253934) 
[*][https://www.normalesup.org/~george/comp/linux_lenovo_miix3/]("https://www.normalesup.org/%7Egeorge/comp/linux_lenovo_miix3/") 
[*][https://sturmflut.github.io/linux/ubuntu/2015/01/21/installing-ubuntu-15.04-on-baytrail-tablets/](https://sturmflut.github.io/linux/ubuntu/2015/01/21/installing-ubuntu-15.04-on-baytrail-tablets/) 
[*][http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/](http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/) 
[*][http://www.amazon.com/gp/aw/review/B00NSHLUFQ/R21XA8UO4RTHR2?cursor=7&sort=rd](http://www.amazon.com/gp/aw/review/B00NSHLUFQ/R21XA8UO4RTHR2?cursor=7&sort=rd) 
[/LIST]
[B]
Creating Live Bootable USB[/B]
Requirements:

[LIST=1]
[*]Ubuntu Mate 16.04 64bit Image (Should with any Ubuntu 16.04 ISO, I've only tested this one). 
[*]Micro-USB OTG Cable Keyboard 
[*]Rufus (I found using Rufus to be the easiest). 
[*]Flash Disk 
[/LIST]

Steps:

[LIST=1]
[*]Using Rufus create a GPT UEFI based ISOHybrid bootable flash drive. 
[*]Copy 32Bit EFI Grub boot-loader to appropriate directory ([https://drive.google.com/file/d/0B2i4h73IqE3wa0RCNDBXVHZSVTA/view?usp=sharing]("http://https://drive.google.com/file/d/0B2i4h73IqE3wa0RCNDBXVHZSVTA/view?usp=sharing")). 
[*]Boot from disk. 
[/LIST]
[B]
Installing OS[/B]

[LIST]
[*]Ensure that you have an Internet connection, since GRUB automatically installs a 32bit based boot-loader which is convenient. 
[*]During  installation I noted that were a couple of error messages relating to  &#8216;Atomic&#8217; although these did not impact the installation or anything of  the sorts. It would seem that they are working to incorporate Atomic  support in the Linux DRM Drivers ([http://phoronix.com/scan.php?page=n...]("http://l.facebook.com/l.php?u=http%3A%2F%2Fphoronix.com%2Fscan.php%3Fpage%3Dnews_item%26px%3DAtomic-DRM-2016-Update&h=KAQGF8hZg&s=1")). 
[/LIST]
[B]
[Update : 2016-06-10] Installing the RTL8723BS WIFI device [/B]
* The following is from [kyle_b]("http://h30434.www3.hp.com/t5/user/viewprofilepage/user-id/2356427") post on his notes of installing Linux on the HP Stream 7 (see sources for link to post).*

[LIST]
[*]sudo apt-get install build-essential linux-headers-generic git clone [https://github.com/codeTom/rtl8723bs.git]("https://www.facebook.com/l.php?u=https%3A%2F%2Fgithub.com%2FcodeTom%2Frtl8723bs.git&h=mAQGubhC-&s=1") 
[*] cd rtl8723bs 
[*] make 
[*] sudo make install 
[*]sudo depmod -a 
[*]sudo modprobe r8723bs 
[/LIST]
 The above module for the WIFI did not work for me, though [https://github.com/hadess/rtl8723bs](https://github.com/hadess/rtl8723bs) is installed and working fine so far.
[B]
[Update : 2016-06-10 ] Manually adjusting screen brightness + Script [/B]
* The following is from [kyle_b]("http://h30434.www3.hp.com/t5/user/viewprofilepage/user-id/2356427") post on his notes of installing Linux on the HP Stream 7 (see sources for link to post).*

[LIST]
[*]xrandr --output DSI1 --brightness .7 (3 is still readable I would not go lower than that) 
[/LIST]
I made a simple script that can be run in the terminal ([https://drive.google.com/file/d/0B2i4h73IqE3wa1Z5RHZIWU1PM2M/view?usp=sharing)]("https://drive.google.com/file/d/0B2i4h73IqE3wa1Z5RHZIWU1PM2M/view?usp=sharing")[B]

[Update : 2016-06-10] Rotating the Screen + Script[/B]
* The following is from [kyle_b]("http://h30434.www3.hp.com/t5/user/viewprofilepage/user-id/2356427") post on his notes of installing Linux on the HP Stream 7 (see sources for link to post).*

[LIST]
[*]xrandr -o right 
[*]xinput set-prop 'Goodix Capacitive TouchScreen' 'Coordinate Transformation Matrix' 0 1 0 -1 0 1 0 0 1 
[/LIST]
 

[LIST]
[*]xrandr -o left 
[*]xinput set-prop 'Goodix Capacitive TouchScreen' 'Coordinate Transformation Matrix' 0 -1 1 1 0 0 0 0 1 
[/LIST]
 I made a simple script that can be run in the terminal ([https://drive.google.com/file/d/0B2i4h73IqE3waG5UNTZvdEhITVE/view?usp=sharing](https://drive.google.com/file/d/0B2i4h73IqE3waG5UNTZvdEhITVE/view?usp=sharing))[B]

[Update : 2016-06-10] Current issues I&#8217;m experiencing[/B]

[LIST=1]
[*]Buttons aren&#8217;t working in Linux environment. 
[*]Don't press power button, it continuously brings up the shutdown prompt and can't exit it. 
[*]Looking into Blue-tooth support for chip as well. 
[*]Battery is draining extremely fast. 
[*]Sound not working as well. 
[/LIST]

---

