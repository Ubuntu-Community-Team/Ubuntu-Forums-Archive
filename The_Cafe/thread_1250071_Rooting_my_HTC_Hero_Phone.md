---
title: "Rooting my HTC Hero Phone"
date: 2009-08-26
forum: The Cafe
---

### Post by Glenn Jones on 2009-08-26
Hi guys,

There appears to be a number of Google Android users here who have the HTC Hero/G2 phone. I was wondering if any of you had rooted your phones to gain greater access to the Android system? If so how did you do this under Linux as all the guides I find use windows to root their phones.

Also did you find much improvement in the phone by doing so

Thanks in advance

---

### Post by t0p on 2009-08-26
Let me get this straight... to gain root privileges *on your own phone* you have to get up to some nonsense involving a computer?  How can you say these phones "run on Linux" when the software is crippleware?

While we're on the subject of "Linux phones": I was listening to a *Security Now* podcast the other day and one of the presenters talked about a (hopefully now resolved) security issue with Android where apparently all a user's input was being echoed in a root shell.  Crazy.  Though I guess not much of a problem if no one can actually access the root shell...

These "smart" phones don't seem so smart after all.  I think I'll stick with my regular type cellphone.  At least I can install what I like on it.

---

### Post by Glenn Jones on 2009-08-26
After a day of rummaging around the internet I've found this link

[http://larstobi.blogspot.com/2009/08/rooting-htc-hero.html](http://larstobi.blogspot.com/2009/08/rooting-htc-hero.html)

I hope this helps.

> Let me get this straight... to gain root privileges on your own phone you have to get up to some nonsense involving a computer? How can you say these phones "run on Linux" when the software is crippleware?

The phones do run linux and I believe that now allowing you root access is default is a smart idea. Your aren't event given root access in ubuntu by default and you must used su. Not everyone wants or needs root access to their phones. 

[QUOTE] While we're on the subject of "Linux phones": I was listening to a Security Now podcast the other day and one of the presenters talked about a (hopefully now resolved) security issue with Android where apparently all a user's input was being echoed in a root shell. Crazy. Though I guess not much of a problem if no one can actually access the root shell...[QUOTE]

I believe that this has been resolved.

---

### Post by HappinessNow on 2009-08-26
> **Glenn Jones said:**
> Hi guys,

There appears to be a number of Google Android users here who have the HTC Hero/G2 phone. I was wondering if any of you had rooted your phones to gain greater access to the Android system? If so how did you do this under Linux as all the guides I find use windows to root their phones.

Also did you find much improvement in the phone by doing so

Thanks in advanceThere is a link posted right here on Ubuntuforums:

> **aysiu said:**
> It's a bit too esoteric and specialized to be on the Ubuntu Tutorials part of my site (especially since it doesn't relate directly to Ubuntu), but you can read on my blog about my Android experiences:
[http://www.psychocats.net/ubuntucat/?s=android](http://www.psychocats.net/ubuntucat/?s=android)
[http://ubuntuforums.org/showpost.php?p=7842545&postcount=278](http://ubuntuforums.org/showpost.php?p=7842545&postcount=278)

Specifically:

**[Installing a rooted version of Android is easier than I thought it&#8217;d be]("http://www.psychocats.net/ubuntucat/installing-a-rooted-version-of-android-is-easier-than-i-thought-itd-be/")**

---

### Post by Sergio PC on 2009-09-30
[http://theunlockr.com/2009/08/27/how-to-root-your-htc-hero-in-one-click/#menu](http://theunlockr.com/2009/08/27/how-to-root-your-htc-hero-in-one-click/#menu)

---

### Post by freakalad on 2009-11-25
I'm looking at that [theunlockr.com video]("http://theunlockr.com/2009/08/29/how-to-root-the-htc-magic-in-one-click/") too, and I'm not too convinced yet.

The video seems to indicate the Cyanogen tool to facilitate the backup & load of the firmware (instructed in the next video), but that does not necessarily mean that I can log in as root on the actual device (127.0.0.1).

The other thing that's of concern to me is the backup of the apps & data on the device. I know that there was some hassles a while back with the CyanogenMod, and he/they where forced to remove the closed-source google apps from distribution. The way they worked around this was to "backup" the issued device's apps & data, instal the ROM & then restore the proprietary apps apps back onto the device (makes it all nice & legal).
Unfortunately I have no idea where this is or how to do that 

The 2 most popular/stable ROM's in circulation at present seems to be MoDaCo & CyanogenMod 

Has anyone gone through this whole sing & dance on the Hero, and able to assist me, please?
Also, will I be able to make use of the app store as usual, and get the new google apps & navigation (and any other nifty apps) when it comes out?

thanks in advance

- J

===

Some other guides & references I've found:
* [http://romeosidvicious.com/2009/11/09/rooting-the-htc-hero-with-ubuntu-karmic/](http://romeosidvicious.com/2009/11/09/rooting-the-htc-hero-with-ubuntu-karmic/)
* [http://forum.xda-developers.com/showpost.php?p=4084180&postcount=1](http://forum.xda-developers.com/showpost.php?p=4084180&postcount=1)

---

### Post by amitabhishek on 2009-11-25
> **&#20170 said:**
> 

Specifically:

**[Installing a rooted version of Android is easier than I thought it&#8217;d be]("http://www.psychocats.net/ubuntucat/installing-a-rooted-version-of-android-is-easier-than-i-thought-itd-be/")**

Thanks for that link. 

I am using HTC magic and TBH I have never felt the need to root it. The only time time I really wanted to flash the ROM was when I wanted a exchange server client & to take screen shots. Thankfully I got .apk(s) for both the requirements (though its convenient to take screeshots though Android SDK). I really don't want to brick magic so soon. Its not full proof yet.

---

### Post by t0p on 2009-11-25
> **Glenn Jones said:**
> 
I believe that not allowing you root access is default is a smart idea. Your aren't event given root access in ubuntu by default and you must used su. Not everyone wants or needs root access to their phones. 



Okay, I realize this post is a bit old now, but I only just saw it, and I have to reply.

The situation wrt root in Android and in Ubuntu are completely different.  In Ubuntu you are *not* denied root access by default.  You're just denied the ability to log inas root.  You can do stuff *as* root easily, with sudo.  Plus, it's easy to log in as root if you want to.  All you need is Google.  You don't need to "hack" the system.

But in Android you have to access your phone from a computer and do some esoteric stuff to get root access.  This is just wrong.  Sure, if someone doesn't want to get root access, all they have to do is not get it.  But if you do want to be able to get root privileges, it should be as simple as logging in as root, with apassword provided in the documentation - or if you prefer, by using sudo like in Ubuntu.

Incidentally, I find it funny that this procedure is called "rooting your phone".  In the world of evil h4x0rs, "rooting a computer" is illicitly getting root access on someone else's computer.  But in the world of Android phones, getting root access on your own device is made to seem somehow "wrong".  Bizarre.

---

### Post by freakalad on 2009-11-25
> **t0p said:**
> Incidentally, I find it funny that this procedure is called "rooting your phone".  In the world of evil h4x0rs, "rooting a computer" is illicitly getting root access on someone else's computer.

This is my take on it too; those videos/instructions seem to be a guide to loading a rootkit/bootloader, and not simply getting sudo on the device.

rooting the device is the first step to loading a custom ROM, which I'll do at a later stage

---

### Post by frisket on 2010-08-31
> **Sergio PC said:**
> [http://theunlockr.com/2009/08/27/how-to-root-your-htc-hero-in-one-click/#menu](http://theunlockr.com/2009/08/27/how-to-root-your-htc-hero-in-one-click/#menu)

Useless. It requires Windows binaries.

---

### Post by Dustin2128 on 2010-08-31
> **t0p said:**
>   How can you say these phones "run on Linux" when the software is crippleware?
One word. [Tivoization]("http://en.wikipedia.org/wiki/Tivoization"). But that brings up the whole classic GPLv2 VS GPLv3, Torvalds vs Stallman debate...
anyway, the transition to smartphone docked and tablet based computing, where most people accept these restrictions, could very well be how your average computer user loses true ownership over his hardware.

---

### Post by AllRadioisDead on 2010-08-31
Let me just say that my phone is noticeably faster and more responsive running froyo than the stock sense ui.

---

### Post by Dr. C on 2010-09-01
> **Dustin2128 said:**
> One word. [Tivoization]("http://en.wikipedia.org/wiki/Tivoization"). But that brings up the whole classic GPLv2 VS GPLv3, Torvalds vs Stallman debate...
anyway, the transition to smartphone docked and tablet based computing, where most people accept these restrictions, could very well be how your average computer user loses true ownership over his hardware.

This is the crux of the issue and devices without root access such as many mobile phones and the Kindle make GPL v3 all the more relevant. By the way Ubuntu does provide root access its called sudo and has plenty of GPL v3 code.

---

