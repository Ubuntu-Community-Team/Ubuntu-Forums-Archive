---
title: "&quot;Install Ubuntu&quot; absolutely busted"
date: 2012-11-06
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-11-06
Using SDC and then plugging one of my reliable units with the USB, all goes well right up to the point when Ubiquity goes on it's screen-roll. Does not detect hardware, does not even attempt to install anything. No dialog status bar on the bottom, underneath the carousel.

---

### Post by pal1965 on 2012-11-06
....I confirm the bug...

bye
Paolo

---

### Post by sparker256 on 2012-11-06
I have seen the same thing for the last 3 days trying to use USB to install. How do we file a bug against this?

Thanks Bill

---

### Post by mc4man on 2012-11-06
> **ventrical said:**
> Using SDC and then plugging one of my reliable units with the USB, all goes well right up to the point when Ubiquity goes on it's screen-roll. Does not detect hardware, does not even attempt to install anything. No dialog status bar on the bottom, underneath the carousel.

I gave the so-called amd (+mac) iso a try though did not click on the "Install now"
Mainly because I never got an "Installation Type" screen so wasn't going to risk losing my current installs

Did you get the "Installation Type" screen, either before or after 'Install now'? (it should be before 

2nd reason is because I don't see why I'd want the +mac image for an intel machine...

---

### Post by ventrical on 2012-11-06
> **mc4man said:**
> I gave the so-called amd (+mac) iso a try though did not click on the "Install now"
Mainly because I never got an "Installation Type" screen so wasn't going to risk losing my current installs

Did you get the "Installation Type" screen, either before or after 'Install now'? (it should be before 

2nd reason is because I don't see why I'd want the +mac image for an intel machine...


No .. I did not get "Installation Type". Tried  the live session also .. no go. It just walked me through up until username/password <continue> and then the Ubiquity carousssel.

---

### Post by mc4man on 2012-11-06
> **ventrical said:**
> No .. I did not get "Installation Type". Tried  the live session also .. no go. It jsut waled me through up until username/password <continue> and then the Ubiquity carousssel.
Well without the "Installation Type" & partitioner ect. the .iso is basically worthless, maybe tomorrow or so will be better..

---

### Post by ventrical on 2012-11-06
> **mc4man said:**
> Well without the "Installation Type" & partitioner ect. the .iso is basically worthless, maybe tomorrow or so will be better..


Yes .. agreed , I would assume so..

---

### Post by grahammechanical on 2012-11-07
7th November about 1900 GMT

Earlier today I noticed that there were now daily images on the qa site. I downloaded today's (20121107) desktop amd64 and I got the same thing that you guys are reporting.

The slideshow worked great but it did not give the Allocate Drive Space screen, So no option to Do Something Else or anything else. It took the location, the keyboard and my details but did not install.

See, what you get by complaining about Ubiquity! It is not being included in the image anymore. :)

It is a new style live session. It takes you through the install process without actually installing. It is for those of a nervous disposition.

Regards.

---

### Post by ventrical on 2012-11-07
> **grahammechanical said:**
> 7th November about 1900 GMT

Earlier today I noticed that there were now daily images on the qa site. I downloaded today's (20121107) desktop amd64 and I got the same thing that you guys are reporting.

The slideshow worked great but it did not give the Allocate Drive Space screen, So no option to Do Something Else or anything else. It took the location, the keyboard and my details but did not install.

See, what you get by complaining about Ubiquity! It is not being included in the image anymore. :)

It is a new style live session. It takes you through the install process without actually installing. It is for those of a nervous disposition.

Regards.


Perhaps I am going out on a limb here but I am of the mindset that perhaps they are trying a re-build of Ubiquity from the bottom up, hence , patience? But, if you are correct , then the whole testing process that we are accustomed to at U+1 has been effectively nuetered.

  That leads to my folow-up question .. what's the use of expending any further efforts at  constructing the testers-wiki ?

Regards...

---

### Post by grahammechanical on 2012-11-07
What happened to the automated testing they were going on about at UDS? How can they put these images up for download when they do not work? Where is the hurry?

They want ISO testing in a two week pattern with the first week spent testing the image and it does not matter which of the daily images that week a person tests (this is my understanding of what I have read). So, why put images up for download before the testing schedule is in place?

Sometimes, I get disillusioned and I then find it very hard to overcome that feeling. I try to do things because I want to do it and then I try to do it for my own satisfaction. That's how I try to get through the day.

Regards.

---

### Post by ventrical on 2012-11-07
I got this far but forgot to make it a persitive USB drive :)

```

ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20121107.2) raring InRelease
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20121107.2) raring/main Translation-en_US
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20121107.2) raring/main Translation-en
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20121107.2) raring/restricted Translation-en_US
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Alpha i386 (20121107.2) raring/restricted Translation-en
Ign http://archive.ubuntu.com raring InRelease                            
Ign http://archive.ubuntu.com raring-updates InRelease                    
Get:1 http://archive.ubuntu.com raring Release.gpg [933 B]   
Get:2 http://archive.ubuntu.com raring-updates Release.gpg [933 B] 
Get:3 http://archive.ubuntu.com raring Release [49.6 kB]            
Get:4 http://archive.ubuntu.com raring-updates Release [49.6 kB] 
Get:5 http://archive.ubuntu.com raring/main i386 Packages [1,140 kB]  
Ign http://security.ubuntu.com raring-security InRelease                
Get:6 http://security.ubuntu.com raring-security Release.gpg [933 B]
Get:7 http://security.ubuntu.com raring-security Release [49.6 kB]
Get:8 http://security.ubuntu.com raring-security/main i386 Packages [14 B]     
Get:9 http://archive.ubuntu.com raring/restricted i386 Packages [8,257 B]      
Get:10 http://security.ubuntu.com raring-security/restricted i386 Packages [14 B]
Hit http://archive.ubuntu.com raring/main Translation-en                       
Get:11 http://security.ubuntu.com raring-security/main Translation-en [14 B]
Hit http://archive.ubuntu.com raring/restricted Translation-en         
Get:12 http://security.ubuntu.com raring-security/restricted Translation-en [14 B]
Get:13 http://archive.ubuntu.com raring-updates/main i386 Packages [14 B]
Get:14 http://archive.ubuntu.com raring-updates/restricted i386 Packages [14 B]
Get:15 http://archive.ubuntu.com raring-updates/main Translation-en [14 B]
Get:16 http://archive.ubuntu.com raring-updates/restricted Translation-en [14 B]
Ign http://security.ubuntu.com raring-security/main Translation-en_US  
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US    
Ign http://archive.ubuntu.com raring/main Translation-en_US                    
Ign http://archive.ubuntu.com raring/restricted Translation-en_US              
Ign http://archive.ubuntu.com raring-updates/main Translation-en_US            
Ign http://archive.ubuntu.com raring-updates/restricted Translation-en_US      
Fetched 1,300 kB in 11s (113 kB/s)                                             
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install ubiquity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  aptitude aptitude-common bogl-bterm libboost-iostreams1.49.0 libcwidget3
  libept1.4.12 ncurses-term tasksel tasksel-data ubiquity-frontend-debconf
  ubiquity-frontend-gtk ubiquity-ubuntu-artwork
Suggested packages:
  aptitude-doc-en aptitude-doc debtags libcwidget-dev
The following NEW packages will be installed:
  aptitude aptitude-common bogl-bterm libboost-iostreams1.49.0 libcwidget3
  libept1.4.12 ncurses-term tasksel tasksel-data ubiquity-frontend-debconf
The following packages will be upgraded:
  ubiquity ubiquity-frontend-gtk ubiquity-ubuntu-artwork
3 upgraded, 10 newly installed, 0 to remove and 38 not upgraded.
Need to get 9,020 kB of archives.
After this operation, 16.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ raring/main aptitude-common all 0.6.8.1-2ubuntu1 [669 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ raring/main libboost-iostreams1.49.0 i386 1.49.0-3.1ubuntu3 [39.0 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ raring/main libcwidget3 i386 0.5.16-3.4ubuntu1 [381 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ raring/main libept1.4.12 i386 1.0.9 [136 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ raring/main aptitude i386 0.6.8.1-2ubuntu1 [1,424 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ raring/main tasksel-data all 2.88ubuntu12 [6,806 B]
Get:7 http://archive.ubuntu.com/ubuntu/ raring/main tasksel all 2.88ubuntu12 [31.2 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ raring/main ncurses-term all 5.9-10ubuntu1 [424 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ raring/main bogl-bterm i386 0.1.18-8ubuntu1 [29.7 kB]
Get:10 http://archive.ubuntu.com/ubuntu/ raring/main ubiquity i386 2.13.0 [4,835 kB]
Get:11 http://archive.ubuntu.com/ubuntu/ raring/main ubiquity-frontend-gtk i386 2.13.0 [66.9 kB]
Get:12 http://archive.ubuntu.com/ubuntu/ raring/main ubiquity-frontend-debconf all 2.13.0 [452 kB]
Get:13 http://archive.ubuntu.com/ubuntu/ raring/main ubiquity-ubuntu-artwork all 2.13.0 [525 kB]
Fetched 9,020 kB in 37s (242 kB/s)                                             
Preconfiguring packages ...
Selecting previously unselected package aptitude-common.
(Reading database ... 161385 files and directories currently installed.)
Unpacking aptitude-common (from .../aptitude-common_0.6.8.1-2ubuntu1_all.deb) ...
Selecting previously unselected package libboost-iostreams1.49.0.
Unpacking libboost-iostreams1.49.0 (from .../libboost-iostreams1.49.0_1.49.0-3.1ubuntu3_i386.deb) ...
Selecting previously unselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3.4ubuntu1_i386.deb) ...
Selecting previously unselected package libept1.4.12.
Unpacking libept1.4.12 (from .../libept1.4.12_1.0.9_i386.deb) ...
Selecting previously unselected package aptitude.
Unpacking aptitude (from .../aptitude_0.6.8.1-2ubuntu1_i386.deb) ...
Selecting previously unselected package tasksel-data.
Unpacking tasksel-data (from .../tasksel-data_2.88ubuntu12_all.deb) ...
Selecting previously unselected package tasksel.
Unpacking tasksel (from .../tasksel_2.88ubuntu12_all.deb) ...
Selecting previously unselected package ncurses-term.
Unpacking ncurses-term (from .../ncurses-term_5.9-10ubuntu1_all.deb) ...
Selecting previously unselected package bogl-bterm.
Unpacking bogl-bterm (from .../bogl-bterm_0.1.18-8ubuntu1_i386.deb) ...
Preparing to replace ubiquity 2.12.14 (using .../ubiquity_2.13.0_i386.deb) ...
Unpacking replacement ubiquity ...
Preparing to replace ubiquity-frontend-gtk 2.12.14 (using .../ubiquity-frontend-gtk_2.13.0_i386.deb) ...
Unpacking replacement ubiquity-frontend-gtk ...
Selecting previously unselected package ubiquity-frontend-debconf.
Unpacking ubiquity-frontend-debconf (from .../ubiquity-frontend-debconf_2.13.0_all.deb) ...
Preparing to replace ubiquity-ubuntu-artwork 2.12.14 (using .../ubiquity-ubuntu-artwork_2.13.0_all.deb) ...
Unpacking replacement ubiquity-ubuntu-artwork ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
Setting up aptitude-common (0.6.8.1-2ubuntu1) ...
Setting up libboost-iostreams1.49.0 (1.49.0-3.1ubuntu3) ...
Setting up libcwidget3 (0.5.16-3.4ubuntu1) ...
Setting up libept1.4.12 (1.0.9) ...
Setting up aptitude (0.6.8.1-2ubuntu1) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode
Setting up ncurses-term (5.9-10ubuntu1) ...
Setting up bogl-bterm (0.1.18-8ubuntu1) ...
Setting up ubiquity-ubuntu-artwork (2.13.0) ...
Setting up tasksel-data (2.88ubuntu12) ...
Setting up tasksel (2.88ubuntu12) ...
Setting up ubiquity (2.13.0) ...
Setting up ubiquity-frontend-gtk (2.13.0) ...
Setting up ubiquity-frontend-debconf (2.13.0) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ubuntu@ubuntu:~$ ubiquity
ubuntu@ubuntu:~$ 

```

---

### Post by loukingjr on 2012-11-07
Downloaded the Xubuntu 13.04 daily build a few ago. Like the others here, the installer isn't working. Runs fine off the .iso.

---

### Post by mc4man on 2012-11-08
Supossedly fixed as mentioned here
[http://ubuntuforums.org/showpost.php?p=12343764&postcount=8](http://ubuntuforums.org/showpost.php?p=12343764&postcount=8)

Bug report
[https://bugs.launchpad.net/ubuntu/+source/python3.3/+bug/1076305](https://bugs.launchpad.net/ubuntu/+source/python3.3/+bug/1076305)

---

### Post by sgage on 2012-11-08
I just used the existing iso, got into Live mode, updated ubiquity, and it works as always - allowing you to choose where to install, etc.

In fact, it's installing right now :KS

---

### Post by loukingjr on 2012-11-08
> **sgage said:**
> I just used the existing iso, got into Live mode, updated ubiquity, and it works as always - allowing you to choose where to install, etc.

In fact, it's installing right now :KS
I'm not sure how you updated Ubiquity. When I try I just get an error message.

---

### Post by sgage on 2012-11-08
> **loukingjr said:**
> I'm not sure how you updated Ubiquity. When I try I just get an error message.

Boot to the Live Desktop. Open a term. sudo apt-get update, sudo apt-get upgrade ubiquity. Start the installer. That's all there is to it.

BTW, I am coming to you from a nice fresh installation of the Raring Ringtail! So far (about 13 minutes) so good. I am in the process of "moving in" and getting set up to my prefs.

---

### Post by loukingjr on 2012-11-08
> **sgage said:**
> Boot to the Live Desktop. Open a term. sudo apt-get update, sudo apt-get upgrade ubiquity. Start the installer. That's all there is to it.

BTW, I am coming to you from a nice fresh installation of the Raring Ringtail! So far (about 13 minutes) so good. I am in the process of "moving in" and getting set up to my prefs.
thanks. I was just typing ...upgrade and wasn't enough space. mine's installing now :)

---

### Post by jerrylamos on 2012-11-08
Install amd64 O.K. after apt-get update, apt-get dist-upgrade.

At least 15 python upgrades.

Install O.K.

Update did the same 15+ python upgrades all over again.

BTW, got an Intel solid state drive from Tiger Direct bargain plus rebate, opened up the laptop, save the Windows 7 for when I pass the laptop off, install the solid state drive.

General impression, ZOOM.

p.s. installed i386 on USB drive on Acer Aspire1 netbook O.K.  Same whole pile of python updates, on live before install and then same ones plus some others after install.

Running about the same as the raring apt-sources update, which is to say O.K. but on this netbook wireless WPA security is a real bear.  Select network, try to enter anything in a drop down box, wait minutes for any keystrokes to appear.  Pangolin runs fine with this hidden wireless WPA.  Fastest thing on it so far is Android tablet....blows Ubuntu away for response.  BTW, processor speed on tablet 1 gHz vs. 1.6 gHz on intel netbook.  Yes, there's a launchpad bug written.

---

### Post by ventrical on 2012-11-13
UbiquityInstaller is working normally now from the daily so I will mark this thread solved.

---

