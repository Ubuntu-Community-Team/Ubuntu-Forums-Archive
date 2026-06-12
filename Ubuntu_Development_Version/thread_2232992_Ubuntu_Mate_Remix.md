---
title: "Ubuntu Mate Remix"
date: 2014-07-05
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2014-07-05
I found this on discourse.ubuntu. It is said to be based upon 14.10 and it is very, very much under development, so I thought I would post it here for the interest of those who are concerned about Ubuntu and the classic look and older hardware.

[http://ubuntu-mate.org/blog/ubuntu-mate-remix-alpha1/](http://ubuntu-mate.org/blog/ubuntu-mate-remix-alpha1/)

[http://discourse.ubuntu.com/t/ubuntu-mate-remix-alpha-1/1770](http://discourse.ubuntu.com/t/ubuntu-mate-remix-alpha-1/1770)

[http://ubuntu-mate.org/about/](http://ubuntu-mate.org/about/)

The web page has screen shots.

Regards.

---

### Post by d-cosner on 2014-07-05
I installed Ubuntu Mate this morning, it is awesome! The old Ubuntu look and feel with a modern system under the hood. This is light on resources and runs great! People that miss the Ubuntu Gnome 2x days are really going to love this!

---

### Post by cariboo on 2014-07-05
I installed the Mate remix in a vm, it looks like 2006 all over again. I expected an updated version of the gnome interface, Don't these people have a design person on the team?

---

### Post by d-cosner on 2014-07-05
I kind of like the old school look. I like how Firefox is playing YouTube videos in HTML5 too, full screen with no hesitation and decent resource use. Nice! I really thought my days with Gnome 2x were done and over but this is sort of cool.

I read that the Mate developers had cleaned up the code quite a bit for the current release. I can't remember Gnome 2x 64 bit running this light and quick. I have been enjoying this all day!

---

### Post by Gyokuro on 2014-07-06
Should get a lot of testing and support and as soon Debian will spin an official MATE install disk we will get numbers how many people will use MATE. Good project and IMHO most interesting Ubuntu Remix.

---

### Post by buzzingrobot on 2014-07-06
I've been running MATE 1.8 installed on a 14.10 netinstall for a couple of weeks.  It's been fine. Did a quick install of MATE Remix, compared the package list and they were essentially identical.

The Remix has patched Ambiance and Radiance to work better in MATE and is hyping the retrospective look.  Theming is ephemeral, though, so any working MATE theme could be used. (MATE needs themes with both GTK2 GTK3 components; old Gnome 2 themes are GTK2 only and probably won't correctly handle GTK3 apps.)

Perhaps since MATE 1.8 is stable and much of the focus of 14.10 development is likely to be in packages not used in this remix, it will become quite usable sooner than later.  Should appeal to people who don't want to adopt Mint approach.

(Nitnoy:  If it's named after a South American plant, why does the project use all upper case -- MATE -- as if it were an acronym?)

---

### Post by d-cosner on 2014-07-06
The only real problem I have found is that if I install the ubuntu-restricted-extras nothing is getting installed. I can still watch YouTube videos in HTML5 with Firefox and I converted some music over to ogg files for now. Mp3,s, mp4's, flv's, etc will not play at all even after manually installing the gstreamer packages. Odd but still usable.

---

### Post by ventrical on 2014-07-08
Just randomly closed after 23MBs of download.

---

### Post by buzzingrobot on 2014-07-08
> **ventrical said:**
> Just randomly closed after 23MBs of download.

The updater is downloading iso's?

---

### Post by d-cosner on 2014-07-08
There was also a bug with the network icon not displaying in the panel. After experimenting with trying to build a Mate version of 14.04 I found that trying to remove the Ubuntu control center caused the Gnome control center to be installed. Both of these caused problems with various things not launching from the Mate control center.

I probably should have tried my experiment with a minimal install but I can see where the developers are going to have dependency issues they will have to resolve to make this work. In my attempt I had everything working except the network icon in the panel and user manager in the Mate control center. I could launch user manager from the terminal but I could tell that the other control center was interfering with it.

I had the improved theme installed and other than the bugs I mentioned it was running reasonably well. At any rate, I can see where the developers have more to do bfore the 14.10 release is ready for prime time. I did try the fixes for the network applet with no success. All in all it was fun tinkering around with this and it gave me some insight to the problems that the developers will have to resolve.

Edit: In my experiment I was removing all of Unity and various elements of Gnome trying to make a pure Mate remix of 14.04.

---

### Post by buzzingrobot on 2014-07-08
You'd tried the fix for the network manager applet icon that is here: [http://ubuntu-mate.org/blog/](http://ubuntu-mate.org/blog/)?  You need to reboot, as well.

I've installed Mate 1.8 on a 14.10 mini.iso install a couple of times without encountering any issues.  The Mate team still hasn't created an official repo for 1.8 on 14.04; it remains available in an archive they set up. 

Since 14.10 isn't due for a release for a few months, there really can't be a stable Mate Remix until then. But, 1.8 is stable, though, so I suspect things will settle down when the developers have time to work on it, and then they can deal with the 14.10 changes that come along.

---

### Post by grahammechanical on 2014-07-08
I have decided to get in on this act. Live session; install session and loading to the desktop are all as they should be. Definitely missing that Netwrok Manager icon. I am finding it difficult to set up a WiFi connection. Still it is eary days.

System monitor is showing a base memory useage of 22% out of 1GB RAM. But I noticed earlier on in the day that Utopic + Unity was showing a much lower base memory useage. So, how much of this low memory useage is down to the Mate UI or down to it being built on Utopic I cannot say.

I ran updates. Did I really see "installing KDE window manager?"

What I have found is that as an unbiased tester I am contaminated by my user prejudices.

Regards.

---

### Post by buzzingrobot on 2014-07-08
> **grahammechanical said:**
> 
System monitor is showing a base memory useage of 22% out of 1GB RAM.


Here, Mate by itself takes 350-400 megs. XFCE is marginally lighter. 

> 
I ran updates. Did I really see "installing KDE window manager?" 

Yeah, so did I.  That's *not* a Mate dependency. Odd. Also saw a preferences widget about "preparing for shipping to user" which I'm guessing is a leftover from the image building that should not be there. 

This is a tiny project at this point, with few participants and one guy who seems to have done most of the work so far. Putting Mate from the Utopic repos on a 14.10 install hasn't been problematic for me, so I expect things will be sorted out.

---

### Post by grahammechanical on 2014-07-11
I do not update Ubuntu Mate every day but I just now updated it and I now see a Network manager icon in the top panel. So, I think that bug has been fixed. I also noticed "preparing for shipping to user." I wonder what it does?

It will be interesting to see how this flavour progresses.

---

### Post by d-cosner on 2014-07-12
I just did a virtualbox install of the Mate Remix today. They have fixed the network icon issue. Ubiquity was not removed from the installed system but removing it after the install I saw how to remove the oem install. All in all this is shaping up nice.

---

### Post by VMC on 2014-08-25
I just today read on Misc News at Distrowatch about [Ubuntu Mate becoming the newest official offering]("http://distrowatch.com/weekly.php?issue=20140825#news"). I'll have to try it and compare it to Xubuntu. I had some problems with Gnome3 in the past

---

### Post by Cavsfan on 2014-08-25
Glad I found this thread. I just happen to have 10GB of space for it. It got an network error trying to download it directly.
So I used the torrent with Transmission and that went great. :)

Going to try to install it.

---

### Post by Cavsfan on 2014-08-25
This is pretty sweet! It had massive updates. The network icon was there and was connected to the internet but when I clicked on the icon and then on Wired Connection 1 it did something.
I'm not sure what but my modem indicated a lot of activity. I had already gotten all the updates just not the ones held back before this.

Thanks grahammechanical for finding this. There's still lots of tweaking to do. Haven't yet got compiz working just right and many other things but this is fun. :guitar:

---

### Post by Cavsfan on 2014-08-25
That was odd. I was installing chromium-browser and it was not downloading it until I once again clicked on the network icon and then Wired Connection 1 and off it went.
It gave the message "successfully connected". I wonder if this is going to be an on going thing?

---

### Post by buzzingrobot on 2014-08-25
Tried a fresh install on 14.04 minimal from the Trusty PPA. An earlier install worked fine, but the mouse was dead in this one. Touchpad was OK.  Odd.

---

### Post by Cavsfan on 2014-08-26
I see it has systemd too. :p Haven't gotten to try that yet. But, I already have a custom grub entry for it. ;)

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep systemd
ii  libpam-systemd:amd64                      208-8ubuntu1                             amd64        system and service manager - PAM module
ii  libsystemd-daemon0:amd64                  208-8ubuntu1                             amd64        systemd utility library
ii  libsystemd-journal0:amd64                 208-8ubuntu1                             amd64        systemd journal utility library
ii  libsystemd-login0:amd64                   208-8ubuntu1                             amd64        systemd login utility library
ii  systemd                                   208-8ubuntu1                             amd64        system and service manager
ii  systemd-shim                              7-1                                      amd64        shim for systemd

```

---

