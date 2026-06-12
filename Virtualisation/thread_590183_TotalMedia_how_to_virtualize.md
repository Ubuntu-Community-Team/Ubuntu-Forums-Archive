---
title: "TotalMedia: how to virtualize?"
date: 2007-10-24
forum: Virtualisation
---

### Post by bliffle on 2007-10-24
"TotalMedia" is an XP product from Arcsoft that will play the USB HDTV signal from the Diamond HDTV100 stick tuner. It runs fine under XP, but this is about the last thing I have to convert to Ubuntu in order to be done with Windows.

I tried finagling the native ubuntu software for a couple of weeks before I gave up and switched to trying to get the XP program running on ubuntu.

I tried "wine", using the XP Firefox as a test case (which worked), but TotalMedia didn't work, presumably because TotalMedia includes a driver and wine doesn't handle drivers, so I was told.

Haven't tried VirtualBox yet, but perhaps I should. I started looking at VMWare but I was bowled over by the magnitude of all the stuff they gave me, and then I fell asleep trying to find my way through all the documentation. Anyway, it seems to me that VMWare solves a lot of problems but not the one that I have.

Anyone tried this before?

Anyone know enough about VirtualBox or VMWare to say whether I should pursue one of those?

---

### Post by dresnu on 2008-10-04
Hey, reviving a zombie thread :-)

Anyway, I tried installing Arcsoft Totalmedia today in Virtualbox. It installs fine, my usb stick decoder gets recognized and I can search and add channels. But when trying to play one I can only hear sound somehow disturbed too and no video at all.

So I guess virtualbox is no solution for now (as you have probably already found out after one year from starting this thread :-D).

---

### Post by howefield on 2008-10-04
Does your USB tv tuner work in Ubuntu ?

I think if it does it should work in Virtualbox, but if it doesn't work natively in Ubuntu it won't in Virtualbox.

---

### Post by dresnu on 2008-10-04
It doesn't, at least out of the box if that's what you mean. It's a trident tm6000 chip based stick and today I tried following these instructions [http://nexthing.wordpress.com/2007/10/31/freecom-dvb-t-analog-tv-usb-stick-on-ubuntu-710-kaffeine/]("http://nexthing.wordpress.com/2007/10/31/freecom-dvb-t-analog-tv-usb-stick-on-ubuntu-710-kaffeine/") with no luck though.

But then again an old hp printer I had was not working properly in ubuntu and I had it up and running nicely in Virtualbox with its windows driver.

Sending print data to a printer is easier to handle than streaming video I guess then.

---

