---
title: "DIY home surveillance with a Webcam"
date: 2009-08-03
forum: The Cafe
---

### Post by Dragonbite on 2009-08-03
Ran across an article that goes over [_do-it-yourself home surveillance with a Webcam_]("http://news.cnet.com/8301-27076_3-10301349-248.html?part=rss&subj=news&tag=2547-1_3-0-20") and they focused on just PC and Macs and that made me think, "What's available for Linux?"  I'm sure there's some tools out there to turn your webcam into a home surveillance unit you can check over the web while away!

That is, so long as the bad guys can't view it and see when you are NOT home!

Any ideas?

---

### Post by Sublime Porte on 2009-08-03
Actually I used cheese today (set my webcam in a corner to see the whole room), running over an encrypted remote X session, to monitor my study whilst I had an inspection (by real estate agent) of my home. Just to make sure they didn't fool with any of my equipment or swipe anything. Worked quite well, certainly not a real surveillance situation, but worked good enough. So I sat in the other end of the house, and viewed my study as it was inspected.

A quick google brought up this, [Zoneminder](http://www.zoneminder.com/)

---

### Post by Dragonbite on 2009-08-03
> **Sublime Porte said:**
> Actually I used cheese today (set my webcam in a corner to see the whole room), running over an encrypted remote X session, to monitor my study whilst I had an inspection (by real estate agent) of my home. Just to make sure they didn't fool with any of my equipment or swipe anything. Worked quite well, certainly not a real surveillance situation, but worked good enough. So I sat in the other end of the house, and viewed my study as it was inspected.

A quick google brought up this, [Zoneminder](http://www.zoneminder.com/)

Did you have sound with that? And was it recording, or just playing real time?

---

### Post by lswb on 2009-08-03
Try these:

[http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)
[http://www.linux.com/archive/articles/114118](http://www.linux.com/archive/articles/114118)
[http://www.zoneminder.com/](http://www.zoneminder.com/)
[http://tech.shantanugoel.com/2008/05/14/keep-tab-on-home-security-with-a-webcam-and-twitter.html](http://tech.shantanugoel.com/2008/05/14/keep-tab-on-home-security-with-a-webcam-and-twitter.html)

BTW, a google search for "linux webcam motion detector" returned all these on the 1st page.

---

### Post by Dragonbite on 2009-08-03
> **lswb said:**
> Try these:

[http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)
[http://www.linux.com/archive/articles/114118](http://www.linux.com/archive/articles/114118)
[http://www.zoneminder.com/](http://www.zoneminder.com/)
[http://tech.shantanugoel.com/2008/05/14/keep-tab-on-home-security-with-a-webcam-and-twitter.html](http://tech.shantanugoel.com/2008/05/14/keep-tab-on-home-security-with-a-webcam-and-twitter.html)

BTW, a google search for "linux webcam motion detector" returned all these on the 1st page.

Used any of them?

---

### Post by richg on 2009-08-03
I have tried Cheese for this but it did not work for me and the USB webcam is seen by the OS with a command line check.

Rich

---

### Post by jackmetal on 2009-10-20
I've seen a lot about ZoneMinder in my recent searches on this..  I'm about to attempt to setup a multi-camera surveillance test, so I'll try to keep good notes and post back on it!  :-)

FYI: I stumbled across this:
[http://www.howtoforge.com/video_surveillance_zoneminder_ubuntu](http://www.howtoforge.com/video_surveillance_zoneminder_ubuntu)

---

### Post by Icehuck on 2009-10-20
I'm still a fan of X10 and it's reasonably priced as well. I will say their website does look like crap though.


[www.x10.com](www.x10.com)

---

### Post by jackmetal on 2009-11-01
Finally had a few minutes to look into this.  Tried out a number of them and settled on "motion".  It's extremely easy to configure:

1) Install:
   a) From repo: $ sudo apt-get install motion
   b) or download from site: [http://www.lavrsen.dk/foswiki/bin/view/Motion/DownloadFiles](http://www.lavrsen.dk/foswiki/bin/view/Motion/DownloadFiles)

2) Edit Config File:
  a) $ vi /etc/motion/motion.conf 
  Change target_dir to where you want the files (video on snapshots) stored.  
  There's a lot of other changes you can make within the config file, but for a quick start, just change the target_dir.

3) Run:
  a) $ motion &
-OR-
  b) You can copy the config file /etc/motion/motion.conf to any directory of your choice and run it via $ motion -c /dir_of_choice/motion.conf &

You can configure multiple cameras by creating a thread file for each one!

---

### Post by Pasdar on 2009-11-01
So leave on your PC (using as much energy as a fridge) to do surveillance while you can for 20 bux buy a surveillance system with a few cams, remote and even internet connection?

---

### Post by RandomJoe on 2009-11-01
Well, since the computer is already on anyway...  (Server that does other things.)

I have used Zoneminder and it is excellent.  Didn't try it with webcams, I used IP cameras - cheap D-Links.  They were limited in that they can't see in the dark (or even just low-light) at all, but otherwise do fine for daytime surveillance.  I keep contemplating some "real" cameras that will also do nighttime IR and set it all up again "for real".

I was so impressed with Zoneminder that it is one of the few programs I immediately went back and contributed to! :D

---

### Post by JillSwift on 2009-11-01
> **Pasdar said:**
> So leave on your PC (using as much energy as a fridge) to do surveillance while you can for 20 bux buy a surveillance system with a few cams, remote and even internet connection?
20 dollars? Where does one get such a fancy multi-cam Internet accessible surveillance camera system for such an amazing price?

Besides one's imagination?

---

### Post by Pasdar on 2009-11-01
> **JillSwift said:**
> 20 dollars? Where does one get such a fancy multi-cam Internet accessible surveillance camera system for such an amazing price?

Besides one's imagination?

They're cheap these days. Of course you shouldn't get them from a store specialized in such things. But here in Holland you'd get one from a large hardware store. It won't cost more than 30 euro's. It even had window sensors added in the package if I remember correctly.

---

### Post by steev182 on 2009-11-01
Links? Thats a crazy price...

---

### Post by JillSwift on 2009-11-01
> **Pasdar said:**
> They're cheap these days. Of course you shouldn't get them from a store specialized in such things. But here in Holland you'd get one from a large hardware store. It won't cost more than 30 euro's. It even had window sensors added in the package if I remember correctly.
I note the price is rising :p

Any links? Because the best I could find - from a clearance/deep discount - was 360 USD for a 4 cam web accessible system. And that lacks a DVR. I know the € is stronger than the $, but not by ***that*** much! ;)

---

### Post by kevdog on 2009-11-01
I also cry foul to the 20 "bux" statement.  Even if 30 Euros were true -- this is in no way equal to $20.  And yes I would like to see a link for 30 Euros.  I'm crying BS on this!

---

### Post by jackmetal on 2009-11-01
You noticed the price rising too..   LOL

Seeing as how the thread was on surveillance with a "Webcam", I'm not sure what help the 20 "bux" surveillance system is for them?  ;-)

I don't really use any of my computers for surveillance (although I do set it up on my laptop sometimes when I'm in a hotel and have to leave the room, etc..)  :-D

---

### Post by Pasdar on 2009-11-01
No BSing from my side. I've seen them lots in the weekly adds they send us in mail from local hardware stores. I just did a quick search and could unfortunately only find a 70 euro wireless one... but again im not bsing.. In fact, I even told my sister I would install such a system in her house because its so cheap...

---

### Post by ice60 on 2009-11-01
someone asked me to make them one once, these are the bookmarks i have if you want them -
[http://devsec.sourceforge.net/](http://devsec.sourceforge.net/) i can't get there atm!!
>  Devolution Security is a video surveillance system for Linux based systems. It supports up to 16 cameras and features unicast and multicast broadcasting, a Web interface, an X11 interface, themes, motion detection, record on motion, eight different camera layouts, camera cycling, fullscreen mode, and more. Devolution Security uses its own toolkit (dtk).

[http://www.zoneminder.com/](http://www.zoneminder.com/)

[http://ledow.blogspot.com/2005_09_01_ledow_archive.html](http://ledow.blogspot.com/2005_09_01_ledow_archive.html)

[http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)

[http://sourceforge.net/projects/net-cam/](http://sourceforge.net/projects/net-cam/)

[http://embraceubuntu.com/2005/12/13/setting-up-a-physical-security-camera/](http://embraceubuntu.com/2005/12/13/setting-up-a-physical-security-camera/)

i remember the zoneminder guy was on this podcast too lol
[http://www.tllts.org/dl.php?episode=183](http://www.tllts.org/dl.php?episode=183)

---

### Post by alek66 on 2012-08-07
I am so going to test zoneminder!!!!

---

### Post by cariboo on 2012-08-07
Let's put this 3 year old thread back to sleep. Thread closed

---

