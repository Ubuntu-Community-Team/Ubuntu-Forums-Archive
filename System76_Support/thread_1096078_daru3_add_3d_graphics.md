---
title: "daru3 add 3d graphics"
date: 2009-03-14
forum: System76 Support
---

### Post by catniko on 2009-03-14
Is it possible to add a 3d graphics card to my DARU3 so that I can play games that require one?  Or would this require alot of necessary changes?

Thanks.

---

### Post by thomasaaron on 2009-03-16
The graphics card in your DarU3 has 3D acceleration.
(But to answer your question more specifically: No. Unless you use some kind of external graphics card.

---

### Post by catniko on 2009-03-17
Thank you for the reply!  How do I get the 3d acceleration to work?  Is that suppose to be covered in upcoming drivers?

Thanks!

---

### Post by thomasaaron on 2009-03-17
It comes activated by default on your machine when you purchase it.
Go to System > Preferences > Appearance > Visual Effects and make sure it isn't set to "None."

Is there something in particular that you are trying to accomplish? The question is a bit abstract.

---

### Post by catniko on 2009-03-18
I am actually running Ubuntu, most of made a mistake and selected the other....any ways..

I am trying to run the World of Goo thru Steam (installed on Linux Crossover Games) and other demos without any luck.  The World of Goo does come up but it is dark and fuzzy.  

When I try to make sure the Visual Affects (within System/Preferences/Appearance/Visual Affects) are set to something other than None, I get this message: Desk top affects could not be enabled.  I get this message when either Normal or Extra is selected.

---

### Post by thomasaaron on 2009-03-18
> I am actually running Ubuntu, most of made a mistake and selected the other....

I don't understand. The other what?

> When I try to make sure the Visual Affects (within System/Preferences/Appearance/Visual Affects) are set to something other than None, I get this message: Desk top affects could not be enabled. I get this message when either Normal or Extra is selected.

OK, then 3-D acceleration is not activated. It comes activated by default on the machine, and Ubuntu supports it out of the box with no modifications by us.

So, you may have made some modification that broke 3-D acceleration.Have you made any configuration adjustments? Also, what software have you added or removed since getting the machine?

You might try re-installing the Intel drivers by running these commands in a terminal.
```

sudo apt-get --purge remove xserver-xorg-video-intel
sudo apt-get install xserver-xorg-video-intel
```

Then ***reboot*** your computer and see if you can activate desktop effects via my instructions in the previous thread.

---

### Post by catniko on 2009-03-19
Sorry it was early when I wrote that reply,  I meant that I put Kubuntu when I am actually using regular Ubuntu on the computer.

This is the software I have downloaded/installed outside of the Ubuntu repositories:

Crossover Professional
Crossover Games – Installed Steam and downloaded a few demo games
PlayonLinux have not tried it yet.
Cedega Gaming Service demo – decided not to try it, have not removed it yet.
SunVirtualbox installed XP within it and Itunes 8 in that  (got an Itouch for Xmas)
MediaMonkey within Wine

I had downloaded Google Earth and then removed because it did not look good.  This was back when I first got the computer.

I did what you suggested and reinstalled the Intel drivers per the script you provided,  appeared to do what it was suppose to do with out having any errors:

kristin@ubuntu:~$ sudo apt-get --purge remove xserver-xorg-video-intel
[sudo] password for kristin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xserver-xorg-video-intel*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1049kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 358536 files and directories currently installed.)
Removing xserver-xorg-video-intel ...
Purging configuration files for xserver-xorg-video-intel ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kristin@ubuntu:~$ sudo apt-get install xserver-xorg-video-intel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xserver-xorg-video-intel
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/438kB of archives.
After this operation, 1049kB of additional disk space will be used.
Selecting previously deselected package xserver-xorg-video-intel.
(Reading database ... 358515 files and directories currently installed.)
Unpacking xserver-xorg-video-intel (from .../xserver-xorg-video-intel_2%3a2.4.1-1ubuntu10.3_amd64.deb) ...
Processing triggers for man-db ...
Setting up xserver-xorg-video-intel (2:2.4.1-1ubuntu10.3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kristin@ubuntu:~$ 

After that,  I went back and tried to  activate the desktop effects and still get the same results:
“Desk top effects could not be enabled.”

Is there anything in the Preferences or Adminstration area that could effect it?  CompizConfig Settings Manager?  The only configuration I messed with was the resolution and then changed it back.

Thank you for your help!

---

### Post by thomasaaron on 2009-03-19
OK. Let's try reinstalling compiz.

```
sudo apt-get --purge remove compiz
sudo apt-get install compiz
```

---

### Post by catniko on 2009-03-22
Ok, I removed and reinstalled compiz and the desktop effects can not be enabled like before.

---

### Post by thomasaaron on 2009-03-23
OK. Are you using an external monitor? If so, desktop effects may not work. I think it depends somewhat on the resolution of your external monitor, particularly if you are in expanding your desktop.

Also, please post the output of this command...

> cat /etc/X11/xorg.conf

---

### Post by thomasaaron on 2009-07-07
That's because the DarU3's graphics card is blacklisted by compiz. Here is the work-around...

[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

---

