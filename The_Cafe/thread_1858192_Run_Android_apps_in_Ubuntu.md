---
title: "Run Android apps in Ubuntu"
date: 2011-10-11
forum: The Cafe
---

### Post by 8jwong14 on 2011-10-11
I'd love to be able to run certain Android apps within Ubuntu so I don't always need to keep my phone besides me.

Are there any gui programs to do this?

Also, please support Linux support on BlueStacks which has an program to run Android apps in Windows and eventually OSX.  I wouldn't want Linux left out of the party =)
[http://community.bluestacks.com/bluestacks/topics/linux_support-uzu4d](http://community.bluestacks.com/bluestacks/topics/linux_support-uzu4d)

---

### Post by edemark on 2011-10-12
I have just found this with a search engine using similar words you have in the title of this post:
[http://news.softpedia.com/news/How-to-Run-Android-Applications-on-Ubuntu-115152.shtml](http://news.softpedia.com/news/How-to-Run-Android-Applications-on-Ubuntu-115152.shtml)
good luck and let me know if it works (i would be interested to know)

---

### Post by ottabaub on 2012-03-18
> **edemark said:**
> I have just found this with a search engine using similar words you have in the title of this post:
[http://news.softpedia.com/news/How-to-Run-Android-Applications-on-Ubuntu-115152.shtml](http://news.softpedia.com/news/How-to-Run-Android-Applications-on-Ubuntu-115152.shtml)
good luck and let me know if it works (i would be interested to know)

Yes, but this article was written 3 years ago. Ubuntu has been radically changed since then and so has Android OS. How valid is it now? I'd be afraid to screw up my Ubuntu installation.

---

### Post by Warpnow on 2012-03-18
The android sdk still works. Will prolly work for as long as android does. Hence it being the sdk...

Here's a more up to date guide for you though:

[http://pasindudps.blogspot.com/2011/11/android-emulator-for-ubuntu-1110.html](http://pasindudps.blogspot.com/2011/11/android-emulator-for-ubuntu-1110.html)

---

### Post by ottabaub on 2012-03-18
> **Warpnow said:**
> The android sdk still works. Will prolly work for as long as android does. Hence it being the sdk...

Here's a more up to date guide for you though:

[http://pasindudps.blogspot.com/2011/11/android-emulator-for-ubuntu-1110.html](http://pasindudps.blogspot.com/2011/11/android-emulator-for-ubuntu-1110.html)

Thanks. I'll give it a shot.

---

### Post by BrokenKingpin on 2012-03-18
What are the apps you need to run? There are no desktop Linux alternatives?

> **ottabaub said:**
> I'd be afraid to screw up my Ubuntu installation.
Use virtual box for this type of testing.

---

### Post by Warpnow on 2012-03-18
> **BrokenKingpin said:**
> What are the apps you need to run? There are no desktop Linux alternatives?


Use virtual box for this type of testing.

The SDK is already an emulator.

---

### Post by ojdon on 2012-03-19
> **Warpnow said:**
> The SDK is already an emulator.

Have you tried the SDK? It's performance is poor and pretty much unusable, but it was only there to test if you didn't have an actual device around to test on. 

I'd suggested using VirtualBox on one of these images avaiable from: [Android-x86 Project]("http://android-x86.org") No idea which image will be best to use in VirtualBox though, maybe try the eeepc build of Android-x86 4.0 RC1, that'll be your best bet and you'd have much better performance compared to using the SDK. 

Have you tried getting in contact with the developers of BlueStacks. When the project first started they sounded pretty in touch with the community. Although, I'm assuming they get a flood of messages these days. But it might be worthwhile asking to support Ubuntu if they are willing to eventually supporting other platforms than Windows, like as you mentioned, OSX.

---

### Post by Kodeine on 2012-03-19
I remember tring the Android SDK. It was very slow even on my new Lenovo H series PC (with i5 CPU). Would be good if you could install android apps on desktop Linux distributions such as Ubuntu without an emulator. Doubt that'll ever happen though?

---

### Post by ottabaub on 2012-03-19
> **Kodeine said:**
> I remember tring the Android SDK. It was very slow even on my new Lenovo H series PC (with i5 CPU). Would be good if you could install android apps on desktop Linux distributions such as Ubuntu without an emulator. Doubt that'll ever happen though?

I tried it last night. Shoot me!

---

### Post by ottabaub on 2012-03-19
> **BrokenKingpin said:**
> What are the apps you need to run? There are no desktop Linux alternatives?


Use virtual box for this type of testing.

I wanted to run Squeezebox Player and Squeeze Commander on my netbook. The latter is optional as I can use SqueezeCenter in Firefox. That works well for selecting music, etc. However, it requires a player. There's an app for Windows but when I tried it a couple of years ago it worked poorly. Perhaps it's been improved but I'd have to run it with Wine. I haven't been able to find a player for Linux. I find it odd that Logitech doesn't provide a suitable player to go with SqueezeCenter since it's available for Linux, Windows and Mac.

I've got SqueezeCenter running on my desktop and it feeds a couple of network music players. I would like the portability of my netbook as a player so I can just plug in a pair of headphones or speakers and listen to music anywhere in and out of my house.

---

### Post by pinguinhood on 2012-03-19
Canonical proposed it in [2009]("https://wiki.ubuntu.com/Specs/AndroidExecutionEnvironment"), but no progress since now...

---

### Post by Kodeine on 2012-03-19
> **pinguinhood said:**
> Canonical proposed it in [2009]("https://wiki.ubuntu.com/Specs/AndroidExecutionEnvironment"), but no progress since now...
How great would that be? Having the entire android library of applications ready to work on good 'ol ubuntu (the answer is 'very')?

---

### Post by zarthan on 2012-03-19
There is a Windows tool for running Android apps. Just going to beta. bluestacks.com 
I think I asked about a Linux version of the tool but ????

---

### Post by Kodeine on 2012-03-20
> **zarthan said:**
> There is a Windows tool for running Android apps. Just going to beta. bluestacks.com 
I think I asked about a Linux version of the tool but ????

I doubt they ever will make a version for Linux.

---

### Post by neu5eeCh on 2012-03-20
Unless I'm mistaken, the following could be a big change over the next year; and make possible much of what you'd like to see:

[http://www.zdnet.com/blog/open-source/android-and-linux-re-merge-into-one-operating-system/10625](http://www.zdnet.com/blog/open-source/android-and-linux-re-merge-into-one-operating-system/10625)

[http://www.slashgear.com/linux-3-3-eats-android-19218970/](http://www.slashgear.com/linux-3-3-eats-android-19218970/)

Sorry if this information has already been posted elsewhere on the forum...

---

### Post by b2zeldafreak on 2012-03-20
Linux Kernel 3.3 with Android upstream could help to make this much easier

---

### Post by perspectoff on 2012-03-22
I am running the Android-x86 OS in VirtualBox (I use the android-x86-4.0-RC1-eeepc.iso download -- works a treat).

Here are the instructions I used to make it work in Kubuntu (Ubuntu is similar):

[http://ubuntuguide.org/wiki/Install_Android_in_VirtualBox](http://ubuntuguide.org/wiki/Install_Android_in_VirtualBox)

The only thing I could (so far) not get to work is bridging the Internet connection in Android (which is only wireless-based) within the VirtualBox guest to a wired ethernet connection in (K)Ubuntu within the VirtualBox host. This is not a problem of VirtualBox, but in Android-x86, which doesn't have a native wired virtual adapter.

I am working on installing wired Ethernet drivers for the Android-x86 virtual OS so that I can get a successful bridge. If anyone has already done this, please post your solution here.

---

### Post by ojdon on 2012-03-22
> **b2zeldafreak said:**
> Linux Kernel 3.3 with Android upstream could help to make this much easier

How would it?

The merger is so that Android could simply run on vanilla Linux Kernels in the near future without the need of using a specifically compiled one for a Android device. :S 

If you are wanting to quickly test a app on a x86 platform then the recent update for the Android SDK has allowed code to be run "near-natively" apparently... Haven't tested it myself, personally, though but will do in the future when I update the SDK.

---

### Post by ToxicDoom83 on 2012-08-21
Well - until Ubuntu for Android comes along....Which looks very promising, yet, so far off :( - i do think i have something! Blame the total g33k in me LOL!

Back in my Windows days (Man, i say that like it was a few years ago, when, in actuality, i just came back to Ubuntu 3 days ago, and am NOT going back!

Anyway....

There was an app that i was DYING to find on here, that i was using for windows - that let me do just that - run Android apps through their program.

Now, here's the thing. I have tried the official Android SDK - SUCKS! I tried another App player - sucked even more. This one that i'm going to point out - ran smoothly, efficiently, and - updated no problem!

To call it an "Emulator"...is...Shady. To a point, i guess it could be...but, it runs better than any emulator could do (Yes, sorry, i'm even calling out VirtualBox on this one) - and, to top it off...it provides Android 3xx - i do remember updating in Windows, and not quite sure if it went to "Ice Cream Sandwich" (4.0)

And - even though i haven't attempted this yet (I just found it, and i am gonna toy with it by all means necessary! I need my Scramble and Words with Friends! LOL!)

See if this floats your boat :D

[http://www.androidpolice.com/2012/04/05/bluestacks-beta-rooted-allows-installation-of-the-play-store/](http://www.androidpolice.com/2012/04/05/bluestacks-beta-rooted-allows-installation-of-the-play-store/)

just look below the screens, and where it says "head here for requisite downloads and full root instructions." - Click that "Head Here" link. It'll guide you through a series of Terminal commands. (Which, some of us like, some hate - some don't mind on occasion. I spent the last 3 days in terminal....i hate it right now! LOL!)

As Mentioned - i have NOT "Tinkered with this yet. I will be. But, it's up to you to decide what you want to do with it.

---

### Post by mr john on 2012-08-21
My bus times app would be useful for some people. I don't have time to be compiling it for all different platforms. Having a one-size-fits-all installer type would save me and many other developers alot of time. Sadly there are too many power hungry people who think they should have their own installation mechanism and that is no fun for developers. I'd have to make an apk, deb, rpm, exe and whatever macs & blackberry use just to get into the mainstream operating systems. This is why I think cloud/web based applications are going to become more widely used than desktop applications. It's easier for developers if there's an open standard like html.

---

### Post by alexan on 2012-08-22
Android is build on Linux but it only uses the kernel for driver and other very basic service/modules . The "real" stuff that make application run is Davalik virtual machine, in which I do suppose (sorry if I am wrong), can potentially run on any OS (similar to Java).
It should be possible to port Davalik on other OS (especially a Linux one) but probably that require lot of work in which Google is not interested.


mmmh, just think if it will possible to run Davalik app after installing just few dependencies like with Java/icetea?
potentially every desktop PC Ubuntu compatible could install any Davalik application ever made. Free or for buy in Software center.

---

### Post by smartboyhw on 2012-08-22
My view: Wait till Ubuntu for Android is released:)

---

