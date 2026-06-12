---
title: "Empty desktop after installation"
date: 2014-02-13
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2014-02-13
I have this afternoon installed Lubuntu 14.04 daily version from live usb.
No problems with the installation which was faultless from start to finish but on reboot I had an empty desktop; no panel; no menu, of course; just the background colour (black).
Right clicking on the desktop gave me the option to open the menu, thank goodness, as I knew it should from previous use of lxde and lubuntu, and from there I could set the session preferences etc etc, so now all is great, with everything as I want and the system running incredibly speedily.

I use a separate /home partition and used that for the new install, having come from Xubuntu 12.04, which was also great, but I am wondering if some of the configuration folders and files in my home from that previous Xubuntu install may have caused my difficulty.
I have not yet had time to search out the configuration files in detail to see if some of those pointed to applications and autostart of apps that no longer are installed, but I just wonder if anyone else has had a similar problem when installing, particularly when using en existing /home from another DE.

Nevertheless very well done to the devs of Lubuntu 14.04; it is already incredibly polished and once set up has been running with no problems for several hours.

Gret job ! ! !

---

### Post by ajgreeny on 2014-02-14
Whoops; I spoke too soon, but that's all part of the fun of using a *ubuntu +1 OS.

This mornings updates have killed my attempts at opening of many applications with an error about missing **libgcc_s.so.1** shared file, though with a bit of detective work I found an older version of that lib file in a SuperTuxKart archive in my home, and got some things running again, though almost unusable.  I could not even run apt-get as that gave errors so I have no way of reinstalling any packages.

Perhaps I'm just not cut out for the bleeding-edge just yet, but I'll keep trying. However, I need to use this netbook soon so may have to bite the bullet and put Xubuntu 12.04.4 back on it, just for now, which I can do in about half an hour, so no great time wasted.

---

### Post by sudodus on 2014-02-14
I have not tried today's build, but I tried (live and installing)

the Lubuntu daily build of 2014-02-12, trusty-desktop-i386.iso, and
the Xubuntu daily build of 2014-02-13, trusty-desktop-i386.iso

I did not notice your problem with lack of menu, but I did not use an old /home partition, and I did not try to compile anything.

If you have time, please check if you have the same problems with a clean install, and if that is the case, report it as bugs :-)

---

### Post by ajgreeny on 2014-02-17
I see I was not the only one who had this probem, and it was sorted out again fairly quickly.  See [http://ubuntuforums.org/showthread.php?t=2205522](http://ubuntuforums.org/showthread.php?t=2205522)

A pity I didn't think of the sudo dpkg trick on the package in archives (clever one!) but nevermind. I may try Lubuntu 14.04 again when the need for the netbook to work 100% has disappeared, soon I hope as I was enjoying my try till that happened.

---

