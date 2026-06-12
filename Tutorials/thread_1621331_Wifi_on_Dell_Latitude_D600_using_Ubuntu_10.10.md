---
title: "Wifi on Dell Latitude D600 using Ubuntu 10.10"
date: 2010-11-14
forum: Tutorials
---

### Post by JBud on 2010-11-14
Okay, this is a tutorial for something I have had a hard time with, solved, and want to share the solution for everyone; how to install wifi firmware(drivers) on a Dell Latitude D600 (that has no internet connection otherwise) for use with Ubuntu 10.10 Desktop Edition.

What you will need:
[LIST]
[*]Another Internet Capable Computer (For downloading Drivers)
[*]A USB Flash Drive with at least 2MB free space
[*]A Dell D600 Laptop (Normally has broadcom wifi, for other wifi cards this will not work)
[/LIST]
Lets get started:
[LIST=1]
[*]Using your internet capable computer Download these packages to your flash drive:
[LIST]
[*][http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb)
[*][http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[*][http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
[/LIST]
[*]Plug your flash drive into the D600 and copy the above files into **your home folder**.
[*]Open b43-fwcutter_011-1_i386.deb **By right clicking and selecting 'Open with Archive Manager'**
[*]Extract *b43-fwcutter* from the /usr/bin folder of the *b43-fwcutter_011-1_i386.deb* archive into **your home folder**.
[*]Now open a terminal and type these commands one by one:
```
sudo ~/b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
```
```
tar xfvj ~/broadcom-wl-4.80.53.0.tar.bz2
```
```
sudo ~/b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
```
```
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
```
[*]That's It!!! Check your networks, your wifi card is already running, you may now delete the files from your home folder!
[/LIST]

---

### Post by Jaxilian on 2010-11-19
I have a D600 also,but I couldn't make the wifi to work even when following this exactly

When activating the driver from  System> Administration>Additional drivers I get error "SystemError:InstallArchives() failed"

---

### Post by JBud on 2010-11-21
This guide only applies to people who use the same broadcomm wifi card I use, (I will post exact model numbers shortly) If you do have the same card, then you do not have to do anything but follow the guide above... Doing it through the additional drivers application will fail, because it downloads driver dependencies from the internet, and since your wifi is your access to the internet, well you can see the issue.

Try the above guide, and if it does not work, then you will need to check what exactly the additional drivers required are, then similar to what I did above, install the driver manually. If you can figure out the driver you are missing, post it here and I will attempt to help you :)

---

### Post by marzshadow on 2010-12-15
This works on my Dell Latitude with a BCM4306 rev 02....until I reboot.
For some reason when I reboot the /lib/firmware/b43legacy directory disappears and I can no longer connect via wireless.

What causes this?
  :
Wait a minute...I repeated the above steps again...and now it didn't disappear.

Seems to work.

Thanks JBUD  "Where ever you are".

-m

---

### Post by JBud on 2010-12-25
No problem marzshadow, glad I could help! :)

---

### Post by tsvb on 2011-01-05
Just wanted to thank you for this.  Worked perfectly for me.  I had an old D600 from work that I just loaded up 10.10 onto.

---

### Post by JBud on 2011-01-06
No problem! I am glad to help. I looked for a forum post like this when I had the issue, and couldn't find one, so when I solved it, I thought I should post the solution. After all, The D600 is a fairly common model.

---

### Post by olepi on 2011-02-01
Thank you so much!!  Just spent the past four hours getting 10.10 up and running only to realize that wireless wasn't working.  Your tip did the trick.  For the record, I have a latitude D600 with a Broadcom BCM4306 rev2 card (Dell TrueMobile 1300) My connection speed is limited, but I can connect to WPA2 networks.

I thought I was going to have to go back to 10.04.

---

### Post by vixlow on 2011-02-03
Thaks, just followed the steps and worked perfectly!!!  (tried with Xubuntu 10. 10  distribution)

---

### Post by linux-king on 2011-04-04
Absolutely brilliant page and solution. Worked a treat first time after a few years of me wishing linux would work on this stable solid older hardware. Keep up the good work and Thank you once again for your excellent knowledge.

---

### Post by lawnberlin on 2011-05-04
High,  this works even fine for me on Dell Latitude D600 and Ubuntu 11.04!  Thank you!

---

### Post by lawnberlin on 2011-05-09
Also worked on Dell Latitude X300 with 11.04, thanx again.

---

### Post by dragwire on 2011-05-31
Thank you so much for your solution to get my Broadcomm TrueMobile 1400 wireless card working on a Dell Lattitude D600.  I had tried numerous other proposed solutions on the web, but none of them worked.  I followed your directions and the card started working right away.

Thank again for your posting!

---

### Post by Adam_NZ on 2011-07-01
Just like to add my vote of thanks. Followed the instructions to the letter ... worked a treat for my Dell D600! :):):)

You've now saved it from going to an early grave!!!

---

### Post by Swanie on 2011-10-10
This procedure worked a treat. Thank you for posting it.

---

### Post by Coliber on 2011-12-04
Is it also work on ubuntu 10.04?

---

### Post by sparktrician35 on 2011-12-04
good morning, im very new to ubuntu and this forum but I seriously need some help with my program. I have installed ubuntu and have been using it for several days. Im using ubuntu 11.10
my problem is i installed compiz and now all of my desktop icons are gone, i have a blank wallpaper and no tool bars, no icons, just a picture. but if I log out and log in as a guest, all of the normal icons and toolbars are there.
 
 
please help!!!

---

### Post by nunk2 on 2012-01-04
wow,..it's work on my linux mint 12,...thank's,..:) :cool::KS

---

### Post by vividexstance on 2012-02-08
Thank you so much, this worked for me on a Dell Latitude D600.

---

### Post by Island_Jon on 2012-04-02
Ditto - worked **so easily** on an old Dell Latitude D600 after fresh install of Ubuntu 11.10 on a wiped disk.

This D600 laptop was a Craig's List **$40 purchase** that had a hosed Windows.  I found it was _impossible_ to update drivers after the former owner's sloppy re-installation of Windoze!

Thanks VERY much. I've had time consuming difficulties with Dell Broadcom cards in the past -- probably my inexperience -- but I'm learning.:p

---

### Post by Redalien0304 on 2012-11-07
this worked for me also on Ubuntu 12.4. even though i have Ver 3 of the chip

---

