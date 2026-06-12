---
title: "intel graphics ubuntu 13.04"
date: 2012-12-13
forum: Ubuntu Development Version
---

### Post by nomenkultur on 2012-12-13
I can't really run ubuntu 12.10 on this laptop as the embed intel gfx for some reason doesn't load the proper driver in 12.10 or mint 14.

 I would like this to be rectified in 13.04 so I have looked and it does appear as it loaded the i915 driver and acceleration is achieved

 however when trying to use webgl in gmaps it saysmy system is not able to, while in 12.04, fedora 17, etc it enables webgl without problems.

 also in control panel -> details it shows my graphics as "unknown" and my driver as unrecognized.

---

### Post by dino99 on 2012-12-13
which intel graphic chip/card is it ?

---

### Post by grahammechanical on 2012-12-13
This

> also in control panel -> details it shows my graphics as "unknown" and my driver as unrecognized.

means nothing. It has been around since the details page was first introduced. There were times in the past when it would give me some information and then it would revert back to 'unknown.' I used to think that it was the difference between using the open source or closed source video driver. But I am wrong.

I put this bug under the heading of "It seemed like a good idea at the time," and I forget about it.

Regards.

---

### Post by nomenkultur on 2012-12-13
gm45

 in elementary os (12.04) it works perfectly

 intel mobile generation 4


 12.10 doesn't work at all (reverts to software driver)

 and in 13.04 it seems to load i915 kernel driver but no webgl and the dash is painfuuuuuuuuuly slow

[http://youtu.be/qNxrP3BI_DE?t=5m49s](http://youtu.be/qNxrP3BI_DE?t=5m49s)

---

### Post by nomenkultur on 2012-12-13
> **grahammechanical said:**
> This



means nothing. It has been around since the details page was first introduced. There were times in the past when it would give me some information and then it would revert back to 'unknown.' I used to think that it was the difference between using the open source or closed source video driver. But I am wrong.

I put this bug under the heading of "It seemed like a good idea at the time," and I forget about it.

Regards.

 
 I also saw the same behavior on a compaq laptop from someone I know.

 it has a newer intel laptop card but ubuntu refuses to acknowledge it.


 there are only open source intel drivers and they should work by default.

 I find this strange because it works flawlessly in 12.04, fedora, mageia etc etc etc

 so it certainly is something canonical did

---

### Post by ventrical on 2012-12-13
There is no ubuntu 'alpha 1' 13.04.

---

### Post by sammiev on 2012-12-13
I had to install mesa-utils to see what video card I had in the details section.

---

### Post by serdotlinecho on 2012-12-13
Install mesa-utils and use this commands:

```
~$ sudo apt-get install mesa-utils
~$ glxinfo | grep OpenGL | head -n3
```

---

### Post by nomenkultur on 2012-12-14
> **serdotlinecho said:**
> Install mesa-utils and use this commands:

```
~$ sudo apt-get install mesa-utils
~$ glxinfo | grep OpenGL | head -n3
```


:KS:KS:KS:KS:KS

 5 star reply.

 graphic card showing
 correct driver showing
 
 dash is much faster...


 AND


MapsGL enabled

"
 Welcome to MapsGL! 
   We've rebuilt Google Maps from the ground up. Our enhanced Maps pr"

 
  
 someone forward this reply to canonical so 13.04 can have this as default.

 edit: ventrical I saw it at phoronix and another site, canonical even had a graph with a descending line saying " december 6 alpha 1"

---

### Post by deadflowr on 2012-12-14
> **nomenkultur said:**
> :

 edit: ventrical I saw it at phoronix and another site, Canonical even had a graph with a descending line saying " december 6 alpha 1"

This is actually a mislead. Ubuntu, itself will only have a late in development beta release, however the family of flavors such as edubuntu kubuntu and xubuntu have a choice as to whether or not they want to release alphas or not.

[https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule]("https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule")

---

### Post by rrnbtter on 2012-12-14
Greetings,
> sudo apt-get install mesa-utils 
glxinfo | grep OpenGL | head -n3
+1
Amazing results! And I was happy without it!
rrnbtter

---

### Post by thotz on 2012-12-17
I don't know why Ubuntu doesn't ship mesa-utils by default. There is always this question in every development cycle. 

Is there a bug filed about this? Or is it a problem to ship mesa-utils per default?

---

### Post by zika on 2012-12-17
> **thotz said:**
> I don't know why Ubuntu doesn't ship mesa-utils by default. There is always this question in every development cycle. 

Is there a bug filed about this? Or is it a problem to ship mesa-utils per default?
CD space is already used and there is overflow...

---

### Post by thotz on 2012-12-17
> **zika said:**
> CD space is already used and there is overflow...

It's not that big. And it's shipped I think in Fedora (already tested) and in openSUSE (also think it is).

But I understand you.

I have filed a bug here: [https://bugs.launchpad.net/ubuntu/+source/mesa-demos/+bug/1091214](https://bugs.launchpad.net/ubuntu/+source/mesa-demos/+bug/1091214)

---

### Post by zika on 2012-12-17
> **thotz said:**
> It's not that big. And it's shipped I think in Fedora (already tested) and in openSUSE (also think it is).

But I understand you.

I have filed a bug here: [https://bugs.launchpad.net/ubuntu/+source/mesa-demos/+bug/1091214](https://bugs.launchpad.net/ubuntu/+source/mesa-demos/+bug/1091214)It's not me that make any kind of decisions there. Just noticing...

---

### Post by thotz on 2012-12-19
> **zika said:**
> It's not me that make any kind of decisions there. Just noticing...

I know :)

So, if someone wants to check the status of this bug please do it here (my bug report was a duplicate).

[https://bugs.launchpad.net/ubuntu/+source/mesa-demos/+bug/914631](https://bugs.launchpad.net/ubuntu/+source/mesa-demos/+bug/914631)

---

### Post by rrnbtter on 2012-12-19
Greetings
 					Originally Posted by **zika** 					[[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12408858#post12408858") 				
 				[I]> CD space is already used and there is overflow...

Perhaps with Steam making it's debut and games being ported to Linux, the Linux community will discover that there are these things called DVD's and that they hold more data than CD's. Ultimately the residual Jaunty crowd will get over it. I'm thinking! 

rrnbtter
Life is good! Live it to the Ubuntu-ist! Until Friday!
[/I]

---

### Post by zika on 2012-12-19
> **rrnbtter said:**
> Greetings
                     [I]Perhaps with Steam making it's debut and games being ported to Linux, the Linux community will discover that there are these things called DVD's and that they hold more data than CD's. Ultimately the residual Jaunty crowd will get over it. I'm thinking! 

rrnbtter
Life is good! Live it to the Ubuntu-ist! Until Friday!
[/I]Too much resentment about the &#8222;problem&#8220; that could be solved with a single line in terminal...
Greetings from someone that do not feel any shame of being a member of &#8222;jaunty crowd&#8220;...

---

### Post by rrnbtter on 2012-12-19
Greetings,
Original by Zika
> Greetings from someone that do not feel any shame of being a member of „jaunty crowd“...

My apologies to the Jaunty crowd. Actually I didn't know there were any left. It was a tongue in cheek statement.
However we could learn something from Debian that is shipped on CD, DVD, USB image, Blue Ray, Net Install Image, etc.

rrnbtter
Life is good! Live it to the Ubuntu-ist! Until Friday!

---

### Post by jerrylamos on 2012-12-19
> Originally Posted by rrnbtter


Perhaps with Steam making it's debut and games being ported to Linux, the Linux community will discover that there are these things called DVD's and that they hold more data than CD's. Ultimately the residual Jaunty crowd will get over it. I'm thinking! 
There's also this thing called "internet" so I download .iso and boot them direct.  So Ubuntu could expand to many gigabytes.  I wouldn't want to run it.

To me the virtue of the CD was it tended to keep ubuntu down to size.  Now with 4G DVD's they can pile lots and lots of stuff in that I'll never ever ever use.  Launcher has stuff I never ever use.  etc.

On the other hand they've dropped things I use all the time like gparted, synaptic, flashplugin, zsync, and file sharing on my local network never works unless I do an apt-get install samba.  I have a setup exec to get software sources preferences, update preferences, and install a bunch of the stuff they've dropped out.

I've tried "mini" which was a bear.  At 1.5 MB internet it took forever and I was always forgetting some useful utilities,

BTW, sometimes I just want to do something with a live boot so I use linuxmint-14 which saves the bother of installing flashplugin plus is easier for me to setup dual monitors etc.  Booting from the mint .iso file is about like booting installed raring.

---

### Post by rrnbtter on 2012-12-19
Greetings,
Regarding the OP, at least the Intel and Mesa is still supported. My information says that Ubuntu is dropping ATI for lack of any kind of compatibility support or something like that. The 386 processer is being dropped.  I can see a deer in my headlights that has a CD-ROM on his forehead.  It just a matter of what hardware will use RR and that hardware will most likely have a DVD or BlueRay and most certainly a USB.  

rrnbtter
Life is good! Live it to the Ubuntu-ist! Until Friday!

---

### Post by zika on 2012-12-19
> **jerrylamos said:**
> There's also this thing called "internet" so I download .iso and boot them direct.  So Ubuntu could expand to many gigabytes.  I wouldn't want to run it.

To me the virtue of the CD was it tended to keep ubuntu down to size.  Now with 4G DVD's they can pile lots and lots of stuff in that I'll never ever ever use.  Launcher has stuff I never ever use.  etc.

On the other hand they've dropped things I use all the time like gparted, synaptic, flashplugin, zsync, and file sharing on my local network never works unless I do an apt-get install samba.  I have a setup exec to get software sources preferences, update preferences, and install a bunch of the stuff they've dropped out.

I've tried "mini" which was a bear.  At 1.5 MB internet it took forever and I was always forgetting some useful utilities,

BTW, sometimes I just want to do something with a live boot so I use linuxmint-14 which saves the bother of installing flashplugin plus is easier for me to setup dual monitors etc.  Booting from the mint .iso file is about like booting installed raring.
Due to improper quoting that @rrnbtter uses now his words are quoted as mine in Your post... **Please correct that... Thank You...**

---

### Post by zika on 2012-12-19
> **rrnbtter said:**
> Greetings,
Regarding the OP, at least the Intel and Mesa is still supported. My information says that Ubuntu is dropping ATI for lack of any kind of compatibility support or something like that. The 386 processer is being dropped.  I can see a deer in my headlights that has a CD-ROM on his forehead.  It just a matter of what hardware will use RR and that hardware will most likely have a DVD or BlueRay and most certainly a USB.  

rrnbtter
Life is good! Live it to the Ubuntu-ist! Until Friday!ATI is by no means dropped in Ubuntu... Open-source driver is getting better and better every day...
Please use quoting the way it is customary here on the Forum so other people would not have trouble answering on Your posts and Your writting would not be attributed to other memebres of Forum...

---

### Post by rrnbtter on 2012-12-19
Greetings,
> Due to improper quoting that @rrnbtter uses now his words are quoted as mine in Your post... Please correct that... Thank You...
Good grief! Whats the correct way to quote!  Just doing what I could figure out!

rrnbtter
Life is good! Live it to the Ubuntu-ist! Until Friday!

---

### Post by zika on 2012-12-19
> **rrnbtter said:**
> Greetings,

Good grief! Whats the correct way to quote!  Just doing what I could figure out!

rrnbtter
Life is good! Live it to the Ubuntu-ist! Until Friday!
Use &#8222;Quote&#8220; button...
You can see above why I'm complaining...
Your words are attributed to me...

---

### Post by rrnbtter on 2012-12-19
Greetings,
Thanks for the quote instructions. I will see if I can hunt down the ATI release.  Just ran across it yesterday on one of the technology sites.

rrnbtter
Life is good! Live it to the Ubuntu-ist! Until Friday!

---

### Post by zika on 2012-12-19
> **rrnbtter said:**
> Greetings,
Thanks for the quote instructions. I will see if I can hunt down the ATI release.  Just ran across it yesterday on one of the technology sites.

rrnbtter
Life is good! Live it to the Ubuntu-ist! Until Friday!I wrote about open-source driver... You do need to „hunt it down“...

---

### Post by Elfy on 2012-12-19
> **rrnbtter said:**
> Greetings,
Thanks for the quote instructions. I will see if I can hunt down the ATI release.  Just ran across it yesterday on one of the technology sites.

rrnbtter
Life is good! Live it to the Ubuntu-ist! Until Friday!

> **zika said:**
> Use „Quote“ button...
You can see above why I'm complaining...
Your words are attributed to me...
You can also use the multiquote button (to the right of quote) with the quote button to quote multiple posts, you can change the order as I have done here. 

Further you can quote posts from other threads, just a bit fiddlier.

Always best to quote properly if you can - not so much here - but elsewhere improperly quoting things can lead to trouble for people.

---

### Post by zika on 2012-12-19
> **Elfy said:**
> You can also use the multiquote button (to the right of quote) with the quote button to quote multiple posts, you can change the order as I have done here. 

Further you can quote posts from other threads, just a bit fiddlier.

Always best to quote properly if you can - not so much here - but elsewhere improperly quoting things can lead to trouble for people.Thank You...

---

### Post by rrnbtter on 2012-12-19
Greetings,
I think this goes away from the original OP but the ATI information I was referring to is here [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+question/213017](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+question/213017) however it appears to me after rereading that it is AMD that is dropping closed driver support for linux on some ATI card versions. The result is still a work-around however. There are also other links available on the same subject. I will leave it to you to do your own google-ing.

rrnbtter
Life is good! Live it to the Ubuntu-ist! Until Friday!

PS: I'm out of here!

---

### Post by zika on 2012-12-19
> **rrnbtter said:**
> Greetings,
I think this goes away from the original OP but the ATI information I was referring to is here [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+question/213017](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+question/213017) however it appears to me after rereading that it is AMD that is dropping closed driver support for linux on some ATI card versions. The result is still a work-around however. There are also other links available on the same subject. I will leave it to you to do your own google-ing.

rrnbtter
Life is good! Live it to the Ubuntu-ist! Until Friday!

PS: I'm out of here!First You wrote that Ubuntu is dropping ATI and now You write that ATI is dropping proprietary driver support for linux on some ATI card versions... These are two very different things...
I've done my Google-ing about that in Janty time and I've beeng doing that since then...

PS: I'm staying here...

---

### Post by thotz on 2012-12-20
According to the bug in launchpad it's fixed now.

[https://bugs.launchpad.net/ubuntu/+source/mesa-demos/+bug/914631](https://bugs.launchpad.net/ubuntu/+source/mesa-demos/+bug/914631)

---

### Post by kevpan815 on 2012-12-20
13.04 is working just fine with my Intel Processor and Intel Integrated Graphics Card on my Dell 1012 Mini Netbook with AMD64 13.04 installed. And that's even though I bought this system on a close out sale in 2010.

---

### Post by nomenkultur on 2012-12-22
if this was such a trivial matter like the correct display of the name of the graphics driver I wouldn't even have looked into it.

 Fact is without mesa and the codes that were posted I could not even activate WebGl.


 I would also ask canonical to look into performance in intel gfx cards:

 ubuntu 12.04 is smooth and fast and as you can see from the video I posted the dash experience in 13.04 is sluggish at best.

 ubuntu 12.10 for me is a no go simply because of intel gfx glitch that won't even start the driver.

 
 is anyone able to burn ubuntu on a cd? I'm using dvd's now

---

