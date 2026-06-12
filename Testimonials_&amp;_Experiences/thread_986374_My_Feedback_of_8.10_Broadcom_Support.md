---
title: "My Feedback of 8.10 Broadcom Support"
date: 2008-11-18
forum: Testimonials &amp; Experiences
---

### Post by Titan8990 on 2008-11-18
I am not a Linux newb but I am a newb when it comes to wireless devices and networks.

When I used 8.04 on my laptop I was able to easily install my Broadcom drivers via ndiswrapper. Everything worked perfectly.

When I first upgraded to 8.10 I installed the new Broadcom drivers via the Restricted Drivers Manager. Then I find that my wireless interface's logical name was changed from wlan0 to eth2 and it lost its ability to scan using the iwlist command. Also, I had lost my gnome wireless applet. I uninstalled the new drivers and it turned out my ndiswrapper drivers were still there (even though my additional line to /etc/modules no longer included ndiswrapper).

Two drivers for the same interface did not work properly? That is understandable. After their removal, ndiswrapper worked just as it did before in 8.04.

So a week or so goes by and I get the urge to try some backup server software known as Restore-EE. The most recent package they had was for 7.10 (I tried to use the 7.10 packages in 8.10 with no luck). So I reformatted and installed 7.10. Restore-EE turned out to be crap for complete system backups, which is what I wanted.

I uninstalled Restore-EE and proceeded to upgrade all the way from 7.10 to 8.10. It worked without a hitch, and at this point, I had not touched ndiswrapper.

So I see two Broadcom drivers in the Restricted Drivers Manager when I get to 8.10. I installed them both. Once again, my wireless inteface is eth2, I have no Gnome wireless applet, and my wireless interface (eth2) does not support scanning.

I go back in to the Restricted Drivers Manager and to my surprise, there is only one entry for Broadcom. The other seemed to have disappeared after I installed it. So I uninstalled the other Broadcom driver and viola, eth2 is now wlan0.

Now here is the problem:

I still don't get a gnome applet

iwconfig doesn't support passphrases?


To me this new driver support was a step backwards. Yes, before with ndiswrapper installation it was more difficult, but it worked. If I was a new user to Linux this would be a major discouragement.

Just my 2 cents.

If anyone would like more information on my current set up:

Laptop: HP Pavilion tx1000
Wireless: Broadcom Corporation BCM4311 802.11b/g WLAN

Post on topic: [http://ubuntuforums.org/showthread.php?t=985223](http://ubuntuforums.org/showthread.php?t=985223)

---

### Post by waspbr on 2008-11-18
funny, my tx1320us  worked out of the box, but then my card is a bcm 4328...

unfortunately the drivers did not work in your case, but I reckon they are a step in the right direction,. though it is important that you come forward and point out glitches like this, hopefully future versions will include more cards and will work as they should.

---

### Post by armandh on 2008-11-18
never could get the bcm4311 to work B4 the restricted drivers.
the restricted drivers are just so much easier. 
best wishes to those who wish a custom wireless lan interface
for me, I just want it to work.
I note you upgraded to 8.10. 
in that case it could be anything.

---

### Post by Crafty Kisses on 2008-11-18
That's weird, Broadcom support should be better with Intrepid, I'd say file a bug report, if you haven't already.

---

### Post by Titan8990 on 2008-11-19
> That's weird, Broadcom support should be better with Intrepid, I'd say file a bug report, if you haven't already.

I have not yet. I was very surprised that A) I didn't see a bunch of others with similar issues B) Couldn't even get directed to a GUI program that will allow me to log on wireless networks via the forums (only been two days, I will remain patient).

---

### Post by stalkingwolf on 2008-11-20
I just installed 8.04 on an everex stepnote. Due to what I believe was
a DVDrom problem I had to put the HDD in my desktop. I used the DVD included
in The Complete Ubuntu book.

 When I reinstalled the drive and fired it up, Imagine my surprise to
find that the broadcom card was working.  Never been able to get it to work before.

---

### Post by quazi on 2008-11-20
My suggestion would be to make sure you deactivate the b43 driver and activate the Broadcome STA wireless driver.  Then, try a ```
sudo apt-get install network-manager-gnome
``` to see if it has somehow become uninstalled.  I know when I was originally mucking about with wireless I had installed wicd, which uninstalls network-manager-gnome (took me a few minutes to realize that).

---

### Post by Titan8990 on 2008-11-21
The STA drivers were the ones that turned my wireless interface into eth2. Those don't work for me.

I played with ndiswrapper last night and it looks like I have to have a reformat. Needed one anyways so I can replicate my server and do some testing.

---

### Post by tslawinski on 2008-11-22
It seems to me that I had a problem with the STA driver as well (Aspire 5110 series). I had both activated initially and also noticed that one of the drivers disappeared from the proprietary list (and I believe I lost my applet). I ended up de-activating one followed by a reboot and then deactivating the other. I finally activated the Broadcom B43 by itself. Everything works great now.

---

### Post by Titan8990 on 2008-11-24
I have yet to get to the everything working fine point. On friday I attempted to install ndiswrapper with no luck. Figuring that it is previous failed attempts that caused ndiswrapper not to work, I reformatted once again and am back to 7.10.

I will not upgrade to 8.10 until I am certain that my wireless drivers work properly.

---

