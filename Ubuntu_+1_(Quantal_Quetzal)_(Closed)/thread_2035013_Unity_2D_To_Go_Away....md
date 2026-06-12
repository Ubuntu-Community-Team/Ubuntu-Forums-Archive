---
title: "Unity 2D To Go Away..."
date: 2012-07-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ergo-proxy on 2012-07-29
According to some rumours spread in April/May Unity2D is going to be dropped in Ubuntu 12.10, any news/plans to do that?

---

### Post by effenberg0x0 on 2012-07-29
I wonder if the time spent on that will be lost, all of its LOCs thrown away, or if it is somehow usable according to their plans.

Regards,
Effenberg

---

### Post by vasa1 on 2012-07-29
> **effenberg0x0 said:**
> I wonder if the time spent on that will be lost, all of its LOCs thrown away, or if it is somehow usable according to their plans.

Regards,
Effenberg
Hi,
[http://ubuntuforums.org/showpost.php?p=12107255&postcount=21](http://ubuntuforums.org/showpost.php?p=12107255&postcount=21)

---

### Post by forcecore on 2012-08-01
Unity 2D should really go away and keep Unity 3D as promised with llvmpipe.

---

### Post by jerrylamos on 2012-08-02
> **forcecore said:**
> Unity 2D should really go away and keep Unity 3D as promised with llvmpipe.

I'll be O.K. if they keep Lubuntu.  Using 2D here now.  No Compiz!  Yay!

Jerry

---

### Post by grahammechanical on 2012-08-02
Something in my dull brain is saying: "Unity 2D is the User Interface of Ubuntu TV." Now, where did I get that from? A session at Ubuntu Developer Week, I think. From the log of those sessions I got this link:

[https://wiki.ubuntu.com/UbuntuTV/Contributing#FAQ]("https://wiki.ubuntu.com/UbuntuTV/Contributing#FAQ")

Look at the FAQ What's the technology behind it?

I have a couple of questions. May I ask them?

1) What are the necessary requirements for Ubuntu to no longer need a fall-back mode (Also Know As Unity 2D)?

I guess that Ubuntu pre-installed on devices will not need a fall-back mode as the device will be set up by the OEM. I think that the OS on these devices will be tightly locked to prevent the user/idiot from breaking the OS.

2) Will people like us who test Ubuntu+1 be surplus to requirements in 12 to 18 months time because all or most testing will be done by machines and computer programs?

I think that a full back mode is necessary for running Ubuntu+1 for those occasions when the 3D desktop breaks. This happened to me just the other day after an update. I was glad I could log-in to Ubuntu 2D and carry on working until a further update fixed what was wrong. I do not mind if I have to install a fall-back mode through the command line or the software centre. I do think it is needed for folks like us. But will we be around in 2 years time.

Regards.

---

### Post by cariboo on 2012-08-02
> **grahammechanical said:**
> Something in my dull brain is saying: "Unity 2D is the User Interface of Ubuntu TV." Now, where did I get that from? A session at Ubuntu Developer Week, I think. From the log of those sessions I got this link:

[https://wiki.ubuntu.com/UbuntuTV/Contributing#FAQ]("https://wiki.ubuntu.com/UbuntuTV/Contributing#FAQ")

Look at the FAQ What's the technology behind it?

I have a couple of questions. May I ask them?

1) What are the necessary requirements for Ubuntu to no longer need a fall-back mode (Also Know As Unity 2D)?

According to this [page]("http://www.mesa3d.org/llvmpipe.html"), llvmpipe doesn't use the GPU

> I guess that Ubuntu pre-installed on devices will not need a fall-back mode as the device will be set up by the OEM. I think that the OS on these devices will be tightly locked to prevent the user/idiot from breaking the OS.

2) Will people like us who test Ubuntu+1 be surplus to requirements in 12 to 18 months time because all or most testing will be done by machines and computer programs?

According to guitara, there is still a need for human testers, as there is such a wide range of hardware being used, that it's impossible to create a test case for everyone.

> I think that a full back mode is necessary for running Ubuntu+1 for those occasions when the 3D desktop breaks. This happened to me just the other day after an update. I was glad I could log-in to Ubuntu 2D and carry on working until a further update fixed what was wrong. I do not mind if I have to install a fall-back mode through the command line or the software centre. I do think it is needed for folks like us. But will we be around in 2 years time.

Regards.

From the way it looks, instead of falling back to what is now called 2D mode, fallback just won't use compiz.

---

### Post by mc4man on 2012-08-02
> **cariboo907 said:**
> 
From the way it looks, instead of falling back to what is now called 2D mode, fallback just won't use compiz.

I took it the other way - when or if they can get this going that only unity/compiz will be available.
Support will be either thru capable video cards or the llvmpipe deal, in any event it will be unity/compiz.

---

### Post by effenberg0x0 on 2012-08-02
I don't know, it's starting to feel like 2006 and that scares me. I hope they rename llvmpipe to some user-friendly easily-explainable marketable name/concept. Like Lollipop-2D vs Lollipop-3D, whatever.

Remember when it was impossible to explain to normal users what was going on with the desktop? Everyone was trying to grasp GLX, AIGLX, XGL, DRI, MESAGL, MESA3D, OpenGL? And then there was Compiz, Beryl, Novell Compiz, CompizBeryl, Compiz-Quinn, Compiz Fusion, Compiz++ and Nomad, then the whole problem with Emerald and making Emerald not conflict with Metacity, etc. The good and the bad plugins. And also the sort of good plugins. Not to mention every talk was about the hunt for texture-from-pixmap support, sizing a buffer, then an offscreen buffer, and activating composition on xorg.conf, etc. 

Support to ordinary PC users was impossible. Everyone had a script to try to fix a kind-of-usable desktop in many different machines, I wrote some (you would try to detect if a GPU was present, which GPU, if it was usable, or if we would rely on CPU and software rendering, etc and remove/install dependencies, set xorg.conf according to the GPU capabilities or software-based composition, etc).  

Few people had real 3D support through a real GPU to allow for real hardware acceleration and run the beloved cube. Some had it, but didn't knew it. Other had it but could not make it work no matter what. Video (wasn't even high res yet) was dead - vmplayer had like 20 possible arguments, some people would restart X and change vmplayer args depending on the type of video to be played.  And it never worked right anyway. 

Making the damn cube show was just so amazing that people would tape it and post it on youtube. Think about that. Having a working desktop would classify people as skilled.

I hope I'm wrong. If we jump into that mess again I'll quit IT for good lol

Regards,
Effenberg

---

### Post by ronacc on 2012-08-02
to me it looks like just another step to prevent the USER from running HIS system the way HE wants . 

NOTE! in this case HE is non gender specific .

---

### Post by cariboo on 2012-08-02
This argument is getting old too. a user can use their system any way they want, you don't have to use the default installation, you just have to learn a bit more about a linux distribution, instead of using it like windows, to set it up the way you want.

We've been spoiled over the last few years, because Ubuntu has become so easy to use. If you remember back to Dapper Drake, there was no easy way to play multimedia, you had to use 3rd party scripts in order to get everything to work, and as effenberg0x0 said above, everyone had separate scripts to get the desktop to function properly.

As of right now, it seems that RedHat is pointing the way for Gnome, and their main aim is to produce an enterprise desktop, which is totally locked down, unlike a consumer desktop where it is up to the user to what he/she wants their system to do.

---

### Post by jerrylamos on 2012-08-02
> We've been spoiled over the last few years, because Ubuntu has become so easy to use.
Verily.  I tangle with Debian on occasion, lately on Raspberry Pi.  O.K. for me if someone else gets a package set running like Ubuntu or Raspberry Pi.

I'm expecting a fork as Ubuntu heads full speed toward a wannabe tablet/pod/phone, where the result has the limitations of all three.  Might be O.K. for the masses.  I'll have to look at my choices.  I've got a notebook on lubuntu precise because the 12.10 kernel checks for pae flag then refuses to boot.  For a while during Precise Alpha the check didn't work so precise went ahead and booted and ran anyway.

Jerry

---

### Post by ronacc on 2012-08-02
> **cariboo907 said:**
> This argument is getting old too. a user can use their system any way they want, you don't have to use the default installation, you just have to learn a bit more about a linux distribution, instead of using it like windows, to set it up the way you want.

We've been spoiled over the last few years, because Ubuntu has become so easy to use. If you remember back to Dapper Drake, there was no easy way to play multimedia, you had to use 3rd party scripts in order to get everything to work, and as effenberg0x0 said above, everyone had separate scripts to get the desktop to function properly.

As of right now, it seems that RedHat is pointing the way for Gnome, and their main aim is to produce an enterprise desktop, which is totally locked down, unlike a consumer desktop where it is up to the user to what he/she wants their system to do.

many of the easy configuration options have gone away or been hidden (in a different place each cycle ) that is getting old to me , my  "work" desktop is 10.04 and when I find it necessary to upgrade it ,the upgrade will not be to a "buntu" unless things change . That is not a threat just a statement of fact .

---

### Post by ventrical on 2012-08-02
> **ronacc said:**
> many of the easy configuration options have gone away or been hidden (in a different place each cycle ) that is getting old to me , my  "work" desktop is 10.04 and when I find it necessary to upgrade it ,the upgrade will not be to a "buntu" unless things change . That is not a threat just a statement of fact .

 I have learned how to "lock-down" Maveric and Lucid for rainy days ahead.  There is no prerequisite where one has to update. For the most part, they are bullet-proof installs.

  I do  like  working and testing extreme edge developments. That's why I am here in these forums.  8 PCs, 1 Desktop Dell, 5 Towers and 3 laptops. Oh .. that's 9! :) Things always change with Ubuntu. I think the Canonical braintrust will not abandon older PCs. There is just too much interest . Ubuntu has a resilient way of resurrecting old PCs and laptops. Quantal so far hasn't presented any real departure with the exception of the boondoggle with Naultilus and the "me" permissions and a few other truncations. That may very well come back to haunt the devs - and I hope cooler heads will prevail before they put a feature freeze on that.

---

### Post by jbicha on 2012-08-02
> **ventrical said:**
> I have learned how to "lock-down" Maveric and Lucid for rainy days ahead.  There is no prerequisite where one has to update. For the most part, they are bullet-proof installs.

Except that Maverick has known security vulnerabilities and will not receive any additional updates. Even Lucid only has 9 more months of support.

---

### Post by ronacc on 2012-08-02
and how much more insecure is it today than in april 2010 ?

---

### Post by neodirtchief on 2012-08-02
I agree 100%. This is your system how WE designed it. Not looking real good.

---

### Post by jbicha on 2012-08-02
ronacc, because Ubuntu 10.10 isn't supported there isn't even a tracker of the security vulnerabilities. You can get a decent estimate by looking at all the fixes that have been released for Ubuntu 11.04 since April though.

[http://www.ubuntu.com/usn/natty/](http://www.ubuntu.com/usn/natty/)

The difference between now and when Maverick was first released is that these vulnerabilities are now known and widely published. It is relatively simple for someone to examine the code diff's and the associated bug reports to exploit those vulnerabilities.

---

### Post by ronacc on 2012-08-02
and in my case if they gain access they will be sorely disappointed no juicy porn , no creditcard #s and sure as heck not anything to do with banking , I'm one of those dinosaurs that still writes paper checks . my personal information is not stored on ANY computer I own , I only enter a short form  of my first name never an address or phone # so they will hack for little profit .

---

### Post by cariboo on 2012-08-02
> **jerrylamos said:**
> Verily.  I tangle with Debian on occasion, lately on Raspberry Pi.  O.K. for me if someone else gets a package set running like Ubuntu or Raspberry Pi.

I'm expecting a fork as Ubuntu heads full speed toward a wannabe tablet/pod/phone, where the result has the limitations of all three.  Might be O.K. for the masses.  I'll have to look at my choices.  I've got a notebook on lubuntu precise because the 12.10 kernel checks for pae flag then refuses to boot.  For a while during Precise Alpha the check didn't work so precise went ahead and booted and ran anyway.

Jerry

As far as your notebook goes, if you start with 10.04, you can directly update to the 12.04 LTS version, and get the non-pae kernel, it's only when you try to install 12.04 directly that it won't boot because of the older cpu.

There are plenty of debian based distributions that still use the non-pae kernel, so your notebook should still be usable for a couple more years before it needs to be retired.

---

### Post by ventrical on 2012-08-03
> **jbicha said:**
> ronacc, because Ubuntu 10.10 isn't supported there isn't even a tracker of the security vulnerabilities. You can get a decent estimate by looking at all the fixes that have been released for Ubuntu 11.04 since April though.

[http://www.ubuntu.com/usn/natty/](http://www.ubuntu.com/usn/natty/)

The difference between now and when Maverick was first released is that these vulnerabilities are now known and widely published. It is relatively simple for someone to examine the code diff's and the associated bug reports to exploit those vulnerabilities.

 I actually read that link. !! geesh!



Oy vey !

 One of those wake up and smell the coffee messages.  I guess Iv'e been in Oz just a bit too long and it's time to get back to Kansas - (no inference to Kansasnoob !:)lol

---

### Post by zombifier25 on 2012-08-03
> **ronacc said:**
> and in my case if they gain access they will be sorely disappointed no juicy porn , no creditcard #s and sure as heck not anything to do with banking , I'm one of those dinosaurs that still writes paper checks . my personal information is not stored on ANY computer I own , I only enter a short form  of my first name never an address or phone # so they will hack for little profit .

Current hackers don't hack people's computer to get banking information. It's so 5 years ago.

Hackers now hack computers to turn them into bots and engage in DDOS attacks.

---

### Post by ronacc on 2012-08-03
in that case they still lose , unless the sneak into my house ( not advisable ) and physically switch on the surge protector they will have no control over the availability of my box to be utilized as a bot so it would be a rather inefficient resource to them ( and mostly unavailable ) .

---

