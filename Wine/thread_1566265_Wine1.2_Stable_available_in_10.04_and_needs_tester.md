---
title: "Wine1.2 Stable available in 10.04 and needs testers"
date: 2010-09-02
forum: Wine
---

### Post by jibel on 2010-09-02
Wine1.2 Stable has reached Lucid. It's waiting for testers before being released to lucid-updates

here's some of the big changes between 1.1.42 and 1.2:
more complete 64/32 bit wine sharing, better fonts on LCD's (fontconfig  taken from user settings), better support for .Net apps, long standing  opening urls in browser bug fixed, fixes for Microsoft Office 2007,  uTorrent, AutoCAD, Fallout 3, Starcraft 2.

You want  to help us and give it a try ? 
All you have to do is to go to the bug report [https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/606509](https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/606509), enable the -proposed repository and test it with your favourite games.

---

### Post by Perfect Storm on 2010-09-02
Thread moved to Ubuntu Forums Wine Forum.

And sticked for a couple of weeks.

---

### Post by dino99 on 2010-09-04
not tested with game(s) but with professional 32 bits apps with success, no need to add libs anymore: good job devs ):P

---

### Post by Nextgeneration on 2010-09-06
I can test it with wow I just need a little more info this is my first time testing anything.

---

### Post by jibel on 2010-09-07
Thank you for testing, your help is much appreciated. 

@Nextgeneration, in order to test that package, you need to enable the lucid-proposed repository (See [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed) for documentation how to enable and use -proposed) and install the latest version of wine from here.

Then use it as you usually do. We are interested to known if any application that didn't correctly work and mentioned in the release notes (I mentioned few of them in the original post) are now fixed and above all, if the applications that use to work are still working correctly with the newer version. You can post the results of your tests to the launchpad bug report ([https://bugs.launchpad.net/ubuntu/+s....2/+bug/606509]("https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/606509")) or here.

Thanks for your help.

---

### Post by NightwishFan on 2010-09-08
On Intel Drivers, most games run much better on 1.2 stable than with 1.1.42.

---

### Post by dino99 on 2010-09-09
the next step is to use 1.3.2 release: work like a charm (some fixme but lot of new things too)  :p

---

### Post by mike6086 on 2010-09-10
How do I download Wine1.2 in windows and then boot into Ubuntu 10.04 and install it.  I can't get my wireless adapter to work and don't have a cable long enough to reach my router - so wireless is all I got??

---

### Post by rostom_zer on 2010-09-22
E.M.Total.Video.Converter.HD.3.70.100621 installed sucessfuly but not working.

Need help please :(

thanX

---

### Post by Señor Banana on 2010-09-24
I'll have to look into this.
I'm new to Ubuntu, but I'd like to see if I can get Fallout 3 working on this.
I'm sure it'll look great if all works out.

---

### Post by nh7o_hi on 2010-09-26
After a system upgrade from Ubuntu 9.1 to 10.04, which took me from Wine 1.0 to Wine 1.2, I notice that the font rendering is now pixelated and rough. Previously it was better than now, using ttf or other fonts. Now I can't get good looking fonts using any of the relevant Wine config settings. This is with all apps, i.e. menu fonts.

I am using Windows fonts in my c:\windows\fonts directory. 

I seem to remember this from previous versions, but don't recall what was done to improve things.

---

### Post by jsebean on 2010-09-26
Wine seems to be working great here :D

---

### Post by PCTinker on 2010-10-02
Okay . . . I'd like to give Wine a try. I warn you, I'm new to Ubuntu, but I would like to test the following progs:

Jot Notes 3
Muzicman
SeaClear II

So how do I install Wine?

Done it!

First indications are that SeaClear II, and its associated MapCal program, are working fine and stable. More testing needed however to verify all options/conditions of use.

Jot Notes 3 has produce one system error message, once, the first time I ran it. Running Jot Notes seems to push my processor to its limits. 100% on System Monitor and fans flat out. Jot Notes works but I may have lost some functionality; or I may be getting fed-up waiting for response to a key stroke. More to follow.

---

### Post by jarviser on 2010-10-02
Tested the following boring Windows appps on a simple open file, tweak and close basis:
Notepad, 
Concise Oxford Dictionary 11th edition, 
FastStone photo resizer in batch mode, 
PhotoMe, 
Netmeter 1.3, 
Microsoft Office 2007 (Excel, Word, Powerpoint)

All worked either as well as on standard repository Wine 1.2, or as in the case of Office 2007 and Photome, **the fonts were massively improved** over the earlier 1.2 version
PhotoMe was unreadable before the upgrade to stable, now I only need strong glasses.

---

### Post by nh7o_hi on 2010-10-20
> **nh7o_hi said:**
> After a system upgrade from Ubuntu 9.1 to 10.04, which took me from Wine 1.0 to Wine 1.2, I notice that the font rendering is now pixelated and rough. Previously it was better than now, using ttf or other fonts. Now I can't get good looking fonts using any of the relevant Wine config settings. This is with all apps, i.e. menu fonts.

I am using Windows fonts in my c:\windows\fonts directory. 

I seem to remember this from previous versions, but don't recall what was done to improve things.

I read this post, and used his shell script to turn on font smoothing:

[http://ubuntuforums.org/showthread.php?t=1050920](http://ubuntuforums.org/showthread.php?t=1050920)

Now looks great.

---

### Post by jarviser on 2010-10-20
> **nh7o_hi said:**
> After a system upgrade from Ubuntu 9.1 to 10.04, which took me from Wine 1.0 to Wine 1.2, I notice that the font rendering is now pixelated and rough. Previously it was better than now, using ttf or other fonts. Now I can't get good looking fonts using any of the relevant Wine config settings. This is with all apps, i.e. menu fonts.

I am using Windows fonts in my c:\windows\fonts directory. 

I seem to remember this from previous versions, but don't recall what was done to improve things.


This thread is about testing the new version of 1.2 not the one that came as standard with 10.04.  The new version from the "proposed"  repository (which you have to add) has much better fonts when I tested it as per my previous thread.

---

### Post by bouncingwilf on 2010-10-20
Have been using wine 1.2 under 10.04 for several months now on three different machine (AMD_64, pentium duo & dm510 dual atom) all working fine with DrDepth with 1 minor issue.

Bouncingwilf

---

