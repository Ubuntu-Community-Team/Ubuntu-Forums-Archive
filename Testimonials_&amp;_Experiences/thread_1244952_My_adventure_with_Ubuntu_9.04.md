---
title: "My adventure with Ubuntu 9.04"
date: 2009-08-20
forum: Testimonials &amp; Experiences
---

### Post by afmGM on 2009-08-20
Earlier experiences with Ubuntu on my old desktop always were always horrible.  I did not know how to use it right, and it normally didn't work out so well.  

About 6 months have passed, I'm learning C++, and I was interested in making a linux port to a game me, and my two online friends are making (I haven't even started programming it, I'm kinda thinking way too far ahead).  I started thinking about Wubi (I have used Wubi before on my laptop, with 8.10, but it didn'work out).  I just had a feeling in my gut, that I should (I have no comment).  So I following my gut, I installed 9.04 with Wubi.  I booted it up, it worked flawlessy this time.  But the only problem was the "Restricted Drivers" thing wasen't popping up at all.  After some work, the only way I got the drivers to install was using envy (can someone tell me what it is XD).  So everything was working there, and compiz was real smooth.

The next thing I had to do was get my headphones working as Ubuntu doesn't fully support my sound card right, so I had to do some more tweaking.  Next I themed it.  I ended up with this beauty :)

[[IMG]http://i818.photobucket.com/albums/zz103/afmGM/Screenshot-1-1.png[/IMG]]("http://i818.photobucket.com/albums/zz103/afmGM/Screenshot-1.png")

Then, I fell in love with Ubuntu.  Unlike hating it like last times (from what I discovered, the previous reasons it didn't work was the mobo in my laptop was not supported by the linux kernal causing lot's of issues).  So everything was good.  I installed stuff and pretty much mastered it (as I know understand terminal, repositories and all that from learning programming).

I've dealt with a few (OMG, HOW DO I GET THIS TO WORK) moments, especially in configuring conky and understanding what the hell I was doing with GCC.  But I've got both things figured out, and everything's good.  

But then, I found a package to allow a Sixaxis to work with Ubuntu.  I've installed the package bam, it screwed up Ubuntu really bad.  In any graphical application the arrow keys would go the opposite way or not work at all.  I remembered about the being able to uninstall packages with apt-get remove, so I pretty much uninstalled all the sixaxis driver packages and... YAY IT WORKED AGAIN :D

So now everything's working in Ubuntu, I'm thinking about moving Ubuntu to a real partition but not for a month as I have everything working and I would like to keep it that way for a while.

Some random other things I found was increased battery life with Ubuntu, which is going to be great for school as I need 3 hours of battery life instead of 1.8 hours with Vista.  I also found watching compiz that my CPU usage normally was always below 40% unless installing or running too many things at once.  Which was quite amazing, I have only heard my laptop's fan kicking into overdrive a few times, and my computer stayed much cooler then usual (It's so quite now :O).

I plan on helping out the open-source community (one day actually, when I get out of high school, I would like to start up an open source buisness like Conolical or however you spell it).  Although, I'm still learning the basics from a popular college C++ textbook from 1998 (that I got for $2 in a thirft shop).

So thank you Ubuntu developers for an outstanding OS and for fixing the issues with my laptop.

Edit: I forgot to say that it's really lame that Nvidia has a splash screen with Ubuntu finishes booting up for a few seconds.  Like what's the point >_>

---

### Post by oboedad55 on 2009-08-20
> **afmGM said:**
> Earlier experiences with Ubuntu on my old desktop always were always horrible.  I did not know how to use it right, and it normally didn't work out so well.  

About 6 months have passed, I'm learning C++, and I was interested in making a linux port to a game me, and my two online friends are making (I haven't even started programming it, I'm kinda thinking way too far ahead).  I started thinking about Wubi (I have used Wubi before on my laptop, with 8.10, but it didn'work out).  I just had a feeling in my gut, that I should (I have no comment).  So I following my gut, I installed 9.04 with Wubi.  I booted it up, it worked flawlessy this time.  But the only problem was the "Restricted Drivers" thing wasen't popping up at all.  After some work, the only way I got the drivers to install was using envy (can someone tell me what it is XD).  So everything was working there, and compiz was real smooth.

The next thing I had to do was get my headphones working as Ubuntu doesn't fully support my sound card right, so I had to do some more tweaking.  Next I themed it.  I ended up with this beauty :)

[[IMG]http://i818.photobucket.com/albums/zz103/afmGM/Screenshot-1-1.png[/IMG]]("http://i818.photobucket.com/albums/zz103/afmGM/Screenshot-1.png")

Then, I fell in love with Ubuntu.  Unlike hating it like last times (from what I discovered, the previous reasons it didn't work was the mobo in my laptop was not supported by the linux kernal causing lot's of issues).  So everything was good.  I installed stuff and pretty much mastered it (as I know understand terminal, repositories and all that from learning programming).

I've dealt with a few (OMG, HOW DO I GET THIS TO WORK) moments, especially in configuring conky and understanding what the hell I was doing with GCC.  But I've got both things figured out, and everything's good.  

But then, I found a package to allow a Sixaxis to work with Ubuntu.  I've installed the package bam, it screwed up Ubuntu really bad.  In any graphical application the arrow keys would go the opposite way or not work at all.  I remembered about the being able to uninstall packages with apt-get remove, so I pretty much uninstalled all the sixaxis driver packages and... YAY IT WORKED AGAIN :D

So now everything's working in Ubuntu, I'm thinking about moving Ubuntu to a real partition but not for a month as I have everything working and I would like to keep it that way for a while.

Some random other things I found was increased battery life with Ubuntu, which is going to be great for school as I need 3 hours of battery life instead of 1.8 hours with Vista.  I also found watching compiz that my CPU usage normally was always below 40% unless installing or running too many things at once.  Which was quite amazing, I have only heard my laptop's fan kicking into overdrive a few times, and my computer stayed much cooler then usual (It's so quite now :O).

I plan on helping out the open-source community (one day actually, when I get out of high school, I would like to start up an open source buisness like Conolical or however you spell it).  Although, I'm still learning the basics from a popular college C++ textbook from 1998 (that I got for $2 in a thirft shop).

So thank you Ubuntu developers for an outstanding OS and for fixing the issues with my laptop.

Edit: I forgot to say that it's really lame that Nvidia has a splash screen with Ubuntu finishes booting up for a few seconds.  Like what's the point >_>

That's quite an adventure. I've had the same experience with my laptop fan. It rarely kicks in with Ubuntu, was much more frequent with windslow xp. Have fun!

Jon

---

### Post by cariboo on 2009-08-20
You can disable the nvidia logo in /etc/X11/xorg.conf. Press Alt-F2 and type:

```
gksu gedit /etc/X11/xorg.conf
```

```
Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
Option "NoLogo" "True"
EndSection
```

You should see something like the above snippet just change the option line to match the above example.

---

### Post by afmGM on 2009-08-20
> **cariboo907 said:**
> You can disable the nvidia logo in /etc/X11/xorg.conf. Press Alt-F2 and type:

```
gksu gedit /etc/X11/xorg.conf
``````
Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
Option "NoLogo" "True"
EndSection
```You should see something like the above snippet just change the option line to match the above example.

Thanks, I really couldn't handle that logo :P

---

