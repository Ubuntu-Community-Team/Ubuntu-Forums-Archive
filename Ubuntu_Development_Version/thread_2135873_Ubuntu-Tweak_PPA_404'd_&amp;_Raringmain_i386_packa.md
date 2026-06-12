---
title: "Ubuntu-Tweak PPA 404'd &amp; Raring/main i386 packages: Updater failed"
date: 2013-04-15
forum: Ubuntu Development Version
---

### Post by bogan on 2013-04-15
Hi! All,

After successfully installing Raring 13.04 and twelve packages, as well as updating to 3.8.0-18 #28; following a reboot, everything was working OK except for ubuntu-tweak and Software Updater.

The later consistantly gave: "Failed to Download repository information" - check your internet connection. Though the Wi-Fi was working as before and Firefox downloaded as needed.

When I ran 'sudo apt-get update' it showed not only the Ubuntu tualatrix ppa as 404 not found, but also: "launchpad.net raring/main i386 packages 404 not found".

Eventually, after several tries and reboots, I unticked the tualatrix entry in Software Sources and then ''sudo apt-get update' and Software Updater both ran without errors.

Is ubuntu tweak not avilable yet for raring ? and is this behaviour of the raring/main ppa normal? do I need to worry about it?

Separate minor problem: 'gksudo' gave: 'not available - install gksu'. Installing and running it opened a strange Window asking for a Password but would not accept the normal user password.
However running 'gksudo' instead, functioned OK  asking for a password with the usual window and accepting the user password.

Strange, seeing there were a lot of Posts saying that 'gksu' was deprecated and to use 'gksudo' instead for graphigal usage.

Chao!,** bogan**.

---

### Post by mcellius on 2013-04-15
Yeah, I don't think Ubuntu Tweak has a completed version for Raring yet, but you can use the testing PPA for it (there is a Raring version there). It's: **ppa:ubuntu-tweak-testing/ppa**

This version, still in development I believe, has worked well for me.

By the way, there is another program called Unity Tweak, also still in development, but it works quite well in Raring, too.  I have both installed on 13.04.

---

### Post by mcellius on 2013-04-15
Oh, I came across the missing "gksudo" command as well.  In my case, I was trying to open gedit with gksudo, but after I got the error message I used sudo instead and it worked just fine, just as gksudo used to work.  Maybe they rolled gksudo's functions into sudo.

---

### Post by bogan on 2013-04-16
> **mcellius said:**
> Yeah, I don't think Ubuntu Tweak has a completed version for Raring yet, but you can use the testing PPA for it (there is a Raring version there). It's: **ppa:ubuntu-tweak-testing/ppa**

This version, still in development I believe, has worked well for me.

By the way, there is another program called Unity Tweak, also still in development, but it works quite well in Raring, too.  I have both installed on 13.04.**Hi!,**
Thanks for your response, I have added the ubuntu-tweak-testing PPA and loaded it.

I had already found the 'Unity-tweak', which at first glimpse seems very useful; it does the 'Windows Button -Left or -Right' which Ubuntu-tweak no longer offered in 12.10.

Chao!, **bogan**.

---

### Post by Frogs Hair on 2013-04-16
Open the Unity Tweak Tool and navigate to Themes > Window Controls > Default > Right  . I can't enable the right side with a custom button setting though.

---

### Post by bogan on 2013-05-03
Hi!,** All,**

With the latest update - 2nd May/13 - a raring version of Ubuntu-tweak is available and the 'ppa:tualatrix/ppa' works correctly.

So I am marking this as 'Solved'.

Chao!,** bogan**.

---

