---
title: "Thoroughly satisfied with 64bit 9.04"
date: 2009-04-26
forum: Testimonials &amp; Experiences
---

### Post by yetanothersteve on 2009-04-26
Everything that made me wonder why I was using 64bit instead of 32bit now appears to be working thanks to Ubuntu 9.04 and a few helpful third parties.

OS install went well, as it should have since I have been using Ubuntu since 2005 without any real issues and it became my primary and only installed to hardware OS with 6.06 64bit.

No longer a need for a 32bit browser for me: the **default 64bit Firefox** with the 64bit Adobe Flash, Java plugins, Totem, and VLC plugins take care of pretty much everything for me. The first time I hit a site with unknown movie formats, the search for the correct plugins required a few clicks and the movie played.

**Printing:** my Brother MFC-7820N was detected automatically without the need for downloading a driver.
**Scanning:** I did have to download the 64bit scanner driver and install it and run the Brother configuration program, but it worked first time.

**Camera:** My Canon Powershot S2 IS was detected automatically when I plugged it in via USB and F-Spot copied the images over no problem. 

Encrypted **DVD** playback worked after running install-css.sh which was already present thanks to livdvdread4 already being in the default desktop install.

**3D **acceleration required only a few clicks in using the Hardware Drivers System Administration applet to have very recent NVIDIA drivers installed.

My Soundblaster Live!5.1 was detected without issue and configured as well.

I am thoroughly satisfied with 9.04 64bit and do not see any need for a 32bit OS anymore - for me anyway. 

Next week my Ubuntu T-Shirts and mouse pad will finally arrive from the Ubuntu store after being back-ordered for a month.

---

### Post by mattlach on 2009-04-26
How did you get flash to work?

I had it working in 8.10, using some sort of windows wrapper, but after upgrading it appears to ahve stopped working...

I ahve flashplugin-nonfree and flashplugin-installer installed, and all I get is white boxes where the flash content would have been.

---

### Post by rileinc on 2009-04-26
> **mattlach said:**
> I ahve flashplugin-nonfree and flashplugin-installer installed, and all I get is white boxes where the flash content would have been.I've had those grey boxes too. Here's what I did to fix it:

1. Close firefox and remove flashplugin-nonfree and flashplugin-installer (or the restricted-extra package if that's where you originally installed flash).
2. Download this to your desktop: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)
3. Extract the file. It'll drop libflashplayer.so to your desktop.
4. Move libflashplayer.so to ~/.mozilla/plugins (create the folder if it wasn't there).
5. Start firefox and enjoy!

It has never given me any grey box.

---

### Post by yetanothersteve on 2009-04-26
rileinc did almost exactly what I did, downloaded the 64bit plugin from Adobe and put it somewhere where Firefox would find it.

In my case I copied it to 
/usr/lib/mozilla/plugins/libflashplayer.so

and then set up these symbolic links
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so

I had used the ndiswrapper with the 32bit version in 8.04, but that is no longer necessary with the release of the 64bit plugin. It is technically still a pre-release, but no problems I have noticed.

---

### Post by old_geekster on 2009-04-26
Like you, Steve, I too had a great experience with JJ using a clean install.  It recognized my ATI 4870 XXX, Canon MP610 (including the scanner) and my Samsung 226BW monitor.  I even have Compiz working correctly.  In fact, it was the easiest install of Ubuntu that I have done in years.  The only distro that I have skipped in recent years is Intrepid.  I was going to stick with 8.04. but got antsy to see what was new.  It just gets easier.  I did have to tweak flash a bit to get it working properly, but all is well that ends well.

---

### Post by Sef on 2009-04-27
Moved to Testimonials and Experiences since it is the former.

---

### Post by clhsharky on 2009-04-27
Me to

The easiest install Ive ever made, every thing works! Everything.
Clean install on ext4,and is very fast. 1.5 hours including apps, updates, flash & java,and KVM.

And did I say - everything works!

---

### Post by Martje_001 on 2009-04-27
By default, Ubuntu 9.04 already installs flashplayer 10 64-bit!

--> Shockwave Flash 10.0 r22 <--

---

### Post by wolfen69 on 2009-04-27
> **yetanothersteve said:**
> 
In my case I copied it to 
/usr/lib/mozilla/plugins/libflashplayer.so

and then set up these symbolic links
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so


for me, just dropping it into /usr/lib/mozilla/plugins worked great. no need for a symlink.

to the OP: great to hear you enjoy it.

---

### Post by stchman on 2009-04-27
> **mattlach said:**
> How did you get flash to work?

I had it working in 8.10, using some sort of windows wrapper, but after upgrading it appears to ahve stopped working...

I ahve flashplugin-nonfree and flashplugin-installer installed, and all I get is white boxes where the flash content would have been.

As far as 64 bit Flash 10 follow my procedure.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

I have Flash 10 64 bit running on 3 different machines.

---

### Post by ukripper on 2009-04-27
since Hardy 64bit i have never looked back. 64bit computing is the way forward and Jaunty is nice foundation for it!!

---

### Post by VoodooLoveDog on 2009-04-27
> **stchman said:**
> As far as 64 bit Flash 10 follow my procedure.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

I have Flash 10 64 bit running on 3 different machines.

Hmmm. I shyed away from 64-bit because of this very issue. I'm going to give it a go. Thanks for the post.

---

### Post by aniruddha on 2009-04-29
64bit seems to be running great for me as well. One question though, has anyone managed to get gfxboot running? I never could manage that on intrepid 64bit. Interesting to see if Jaunty has fixed this...

---

### Post by coskierken on 2009-05-04
Another satisfied customer of Jaunty 64 here!  I actually built this latest machine for 64bit (specs at bottom).  Flash works, w64codecs installed (can do dvd 2 mp4 in 16 minutes for 1.5 hr movie direct from dvd to mp4 in Handbrake 64! and it does not even support multi-cores at this time).  OH, DVDrip (latest) does not support multi cores, either (if someone know different, please let me know ASAP).  Just make sure you have the hardware to support it when you switch!  Flash works for me as does HDMI with sound!  You just have to know how to set the sound to which device you want it to go (via System >Pref > Sounds).  The only problem I have (and minor) is the ATI card (4650).  The drivers and catalyst are not near as good as in 32bit U.  So, the Nvidia GTS 250(1 gig DDR3) is on its way!  Hope more people jump on the 64bit wagon! 
________________________________________
Q9550 / MSI G45M Mb/ 8G 1066 Gskill / ATI 4650 (for 2 more days only)/ WD 500G boot/ Hitachi 1TB Storage/ 22" ACER monitor / Sharp 32" LCD. / AeroCool M40 case (great case.. look it up) Tunsiq 550W PSU  :lolflag:

---

### Post by beniwtv on 2009-05-04
Strange... all I ever had to do for flash on 64bit, is to install ubuntu-restricted-extras, or click on 'install plugin' when Firefox asked.

/me wonders why that many people have trouble. :confused:

---

