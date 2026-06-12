---
title: "Is there any way to get 2D back"
date: 2012-08-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jerrylamos on 2012-08-16
> **philinux said:**
> [http://www.iloveubuntu.net/unity-2d-removed-ubuntu-1210-default](http://www.iloveubuntu.net/unity-2d-removed-ubuntu-1210-default)
Just did a install - I do tht periodically during Alpha's & beta's.  

Oops, no 2D.  Is there any way to get 2D back?  12.04 I guess. 

I'm downloading quantal lubuntu AMD64 now.

Jerry

---

### Post by Harry33 on 2012-08-17
> **jerrylamos said:**
> Just did a install - I do tht periodically during Alpha's & beta's.  

Oops, no 2D.  Is there any way to get 2D back?  12.04 I guess. 

I'm downloading quantal lubuntu AMD64 now.

Jerry

The only 2D you can get is gnome-panel (classic session).

---

### Post by philinux on 2012-08-17
Split to own thread.

---

### Post by ventrical on 2012-08-17
> **jerrylamos said:**
> Just did a install - I do tht periodically during Alpha's & beta's.  

Oops, no 2D.  Is there any way to get 2D back?  12.04 I guess. 

I'm downloading quantal lubuntu AMD64 now.

Jerry


 I tried another weird experiment. I copied the Oneric repos souces.list to the quantal sources.list and then updated and try to downgrade gnome-session but , as usual , there were some weird depends problems. :) But I had fun borking yet another install :)

---

### Post by jerrylamos on 2012-08-17
Choices.  I just installed Precise 2D and Lubuntu along with Quantal 3D, all amd64.  I prefer crisp clean sharp responsive while others (Ubuntu development) prefer Sponge Bob fuzzy foggy squirrely dizzy my eyes can hardly see what's going on when I do Alt-tab to switch windows.

I have a Quantal 3D partition (was 2D) for bug checking and use the other two for any regular applications I'm using, email, internet searching & shopping, news, videos, network file transfer, spreadsheets I forget what all..

If someone has a method for Quantal crisp clear sharp reasonable sized icons (I prefer size 32) and clear sharp stable Alt-tab I'd like to give it a try.

Now admittedly, Precise 2D and Lubuntu don't look like Smartphones if that is the Ubuntu goal.

So I have my choices.  I've been on Ubuntu development testing since Dapper Drake.

Jerry

---

### Post by cariboo on 2012-08-17
> **jerrylamos said:**
> Choices.  I just installed Precise 2D and Lubuntu along with Quantal 3D, all amd64.  I prefer crisp clean sharp responsive while others (Ubuntu development) prefer Sponge Bob fuzzy foggy squirrely dizzy my eyes can hardly see what's going on when I do Alt-tab to switch windows.

I have a Quantal 3D partition (was 2D) for bug checking and use the other two for any regular applications I'm using, email, internet searching & shopping, news, videos, network file transfer, spreadsheets I forget what all..

If someone has a method for Quantal crisp clear sharp reasonable sized icons (I prefer size 32) and clear sharp stable Alt-tab I'd like to give it a try.

Now admittedly, Precise 2D and Lubuntu don't look like Smartphones if that is the Ubuntu goal.

So I have my choices.  I've been on Ubuntu development testing since Dapper Drake.

Jerry

This is a development release, if you having problems, tell us your specs so that we can help solve your. Making repeated posts with the same content isn't helping any one.

---

### Post by xeizo on 2012-08-18
Strange noone mentioned Xubuntu? sudo apt-get install xubuntu-desktop and you have a clean crisp 2D desktop that also works great with compositing and launching 3D-apps. I guess Xubuntu will be the new Ubuntu for many ....

---

### Post by lucazade on 2012-08-18
> **xeizo said:**
> Strange noone mentioned Xubuntu? sudo apt-get install xubuntu-desktop and you have a clean crisp 2D desktop that also works great with compositing and launching 3D-apps. I guess Xubuntu will be the new Ubuntu for many ....

Well I'd say instead Kubuntu.. it works great on every kind of machine.
I personally use it on a netbook (Atom and Gma500), on a old Thinkpad T40 (Pentium M 1.5Ghz, mobility radeon 7500 32mb, 768mb ram) and on other powerful machines like i7.

It takes 200mb of ram like any other Linux desktop, it became really solid in the latest releases and it uses the best toolkit around: Qt4.

No lightweigth gtk-based Desktop env. can compete with it. Just IMHO ;)

---

### Post by critin on 2012-08-19
> **xeizo said:**
> Strange noone mentioned Xubuntu? sudo apt-get install xubuntu-desktop and you have a clean crisp 2D desktop that also works great with compositing and launching 3D-apps. I guess Xubuntu will be the new Ubuntu for many ....

Does this give you the 12.10 Xubuntu or 12.04?  I was going to do this after reading your post because I can't get the launcher icons to show on the unity bar (ubuntu).   I am concerned whether I'd actually be testing ubuntu 12.10  (2/ to3 D) fairly.    ;)    You don't have the dash/launcher bar do you?

I'm also testing Xubuntu and the desktop looks much different than ubuntu, so what does your desktop look like?    Xubuntu or 3D ubuntu?

---

### Post by cariboo on 2012-08-19
> **critin said:**
> Does this give you the 12.10 Xubuntu or 12.04?  I was going to do this after reading your post because I can't get the launcher icons to show on the unity bar (ubuntu).   I am concerned whether I'd actually be testing ubuntu 12.10  (2/ to3 D) fairly.    ;)    You don't have the dash/launcher bar do you?

I'm also testing Xubuntu and the desktop looks much different than ubuntu, so what does your desktop look like?    Xubuntu or 3D ubuntu?

Xubuntu uses the [Xfce]("http://www.xfce.org") desktop environment which is totally different from Unity, and it doesn't have a separate 2D or 3D version.

---

### Post by Starks on 2012-08-19
Is Unity now 3D on llvmpipe?

---

### Post by effenberg0x0 on 2012-08-19
> **Starks said:**
> Is Unity now 3D on llvmpipe?

It's not clear to me. I think:

- It will use software-based OpenGL via llvmpipe driver only if no proper driver is installed for the existing GPU (or if no adequate GPU - or no GPU at all - is available). But it doesn't work in my tests.

- The procedure to check for a GPU and get llvmpipe packages (and remove other conflicting VGA-specific packages, set symlinks, etc) would normally be handled by a python script inside jockey. But there's no jockey anymore (migrated to software-properties-gtk), which does not work for me. 

It would be really nice if anyone with more knowledge on these changes could write a post here, anywhere, a howto, Ubuntu wiki article, anything describing llvmpipe in details. 

**EDIT: ** People that say they have managed to use Gallium lvmpipe in Ubuntu local forums here mention that unity-support-test says it is OpenGL/Unity capable, but they can't use Unity (loop to lightdm with "missing GLX"). 

Regards,
Effenberg

---

### Post by fjgaude on 2012-08-19
> **Starks said:**
> Is Unity now 3D on llvmpipe?

No, definitely not. On my netbook Unity works, lots of bugs, but the display is more 2D than 3D. I can change the Launch ions size like you can in Unity that would be the old 3D, but because of the screen blemishes I'll wait a week or so before trying to use the netbook in real-world situations, like e-mail. <smile>

---

### Post by critin on 2012-08-20
> **cariboo907 said:**
> Xubuntu uses the [Xfce]("http://www.xfce.org") desktop environment which is totally different from Unity, and it doesn't have a separate 2D or 3D version.

Yes, I know the difference of Xubuntu, and I know it doesn't use unity.  I thought there may be a secret that only  experts knew about though since installing the Xfce DE was (or seemed to be as I read it) suggested in a Ubuntu discussion., an alternative way to get 2D and 3D. 

BTW, while you're here if you don't mind.
> =cariboo907
- It will use software-based OpenGL via llvmpipe driver only if no  proper driver is installed for the existing GPU (or if no adequate GPU -  or no GPU at all - is available).

I had assumed this driver would be available to use if necessary.  My driver sources show no drivers available at all, but obviously I don't have the correct ones installed, and I'm not the only one.   Is there word of when they will be available?

Thanks,

---

### Post by mc4man on 2012-08-20
Take this as you may from the devel mail today - (I think the questioner meant "3d", not "2d"

    > Is it correct that at the moment a machine that will not run [COLOR="Red"]2d[/COLOR] will
    not run at all after todays update?  This seems to be the case for me
    at the moment, I see no unity shell on screen and in .xsession-errors
    I see
    compiz (unityshell) - Error: OpenGL 1.4+ not supported

    When can I expect llvmpipe to start working so I know whether to log bugs?

(Jason Warner responds>
The rought ETA is sometime just after FF, so adding some time for testing and shakeout, it might be closer to beta1.
 


---

### Post by xeizo on 2012-08-20
> **critin said:**
> I thought there may be a secret that only  experts knew about though since installing the Xfce DE was (or seemed to be as I read it) suggested in a Ubuntu discussion., an alternative way to get 2D and 3D. 

It's no secret, xfce itself is 2D with compositing possible, and because of that it doesn't produce any bugs when trying to run real 3D-apps ie 3D-games. 

And it doesn't hog down any performance in them ie maximum fps possible.

Actually preferable to running a desktop which is runing in 3D, which steals performance from games and alike.

---

### Post by jerrylamos on 2012-08-20
Xfce?  Haven't run that for years.  

This is a full 12.10 Ubuntu with LXDE installed on top, choose LXDE at logoff/login time.  My opinion LXDE is a 2D type desktop.  Also some other login options with openbox etc. I haven't tried.

Let me do another full Ubuntu install on another partition and then see if XFCE will go on top of that O.K.

I've also got a Kubuntu up but at my level of non-Kubuntu expertise seems to take me more keystrokes to do the same thing as LXDE, for example turn laptop display off (ubuntu max bright hurts) and use the external monitor or start a terminal session. 

Jerry

---

### Post by critin on 2012-08-20
> **xeizo said:**
> It's no secret, xfce itself is 2D with compositing possible, and because of that it doesn't produce any bugs when trying to run real 3D-apps ie 3D-games. 

And it doesn't hog down any performance in them ie maximum fps possible.

Actually preferable to running a desktop which is runing in 3D, which steals performance from games and alike.

Thanks for this info.  My thoughts are from a new installer's point of view.  If I've  decided I liked the looks of ubuntu 12.10 desktop,  I would expect it to look like the pictures and of course work out of the box, so to speak.  If they wanted xfce they would've installed xubuntu in the first place--yes?  That's all I'm saying. ;)

I know things can be changed on my own install, but the test installs aren't really 'mine'.
[LEFT]I feel if I added something like xfce that won't be there in the final release, I'm not testing ubuntu.    I may be silly, but I'm a fairly new tester and haven't yet learned all the in and outs of it.   I am only thinking from the viewpoint of how a **ubuntu **12.10 user would feel.  I will be patient and wait for the official updates that will be in the final release.

I'm also working with xubuntu 12.10 and it works wonderfully for me.  No issues yet.  I did add backgrounds to make it more pleasant to work on.  lol


[/LEFT]

---

### Post by xeizo on 2012-08-20
> **critin said:**
> Thanks for this info.  My thoughts are from a new installer's point of view.  If I've  decided I liked the looks of ubuntu 12.10 desktop,  I would expect it to look like the pictures and of course work out of the box, so to speak.  If they wanted xfce they would've installed xubuntu in the first place--yes?  That's all I'm saying. ;)

I know things can be changed on my own install, but the test installs aren't really 'mine'.
[LEFT]I feel if I added something like xfce that won't be there in the final release, I'm not testing ubuntu.    I may be silly, but I'm a fairly new tester and haven't yet learned all the in and outs of it.   I am only thinking from the viewpoint of how a **ubuntu **12.10 user would feel.  I will be patient and wait for the official updates that will be in the final release.

I'm also working with xubuntu 12.10 and it works wonderfully for me.  No issues yet.  I did add backgrounds to make it more pleasant to work on.  lol


[/LEFT]

Yes, Xubuntu isn't exactly Ubuntu. It is Ubuntu with xfce and some tweaks. But I see your point, I changed to it myself as an alternative to downgrading Xorg during this Nvidia-debacle and then decided I mabe like it better than Unity.

Debian for instance have changed from Gnome to xfce as default, granted they say because of fitting an image below 700MB, but mabe the Debian-team like xfce too  ;)

---

### Post by cpatrick08 on 2012-08-20
unity-2d is still in the quantal repos [http://packages.ubuntu.com/search?keywords=unity-2d&searchon=names&suite=quantal§ion=all]("http://packages.ubuntu.com/search?keywords=unity-2d&searchon=names&suite=quantal&section=all")

---

### Post by xeizo on 2012-08-21
> **cpatrick08 said:**
> unity-2d is still in the quantal repos [http://packages.ubuntu.com/search?keywords=unity-2d&searchon=names&suite=quantal§ion=all]("http://packages.ubuntu.com/search?keywords=unity-2d&searchon=names&suite=quantal&section=all")

It's dummy packages afaik

---

### Post by jerrylamos on 2012-08-21
Currently running well with 12.10 Ubuntu installed LXDE-desktop from Synaptic.  I've got all the Ubuntu applications plus LXDE is crisp, sharp, fast, and supported somewhere in Debian land so it doesn't depend on Ubuntu development.

Yes I've got late architecture notebook amd64x2, netbook intelx2, 3.3 gHz tower running Precise 2D (I don't think Development has dropped that yet) and 12.10 LXDE to test Quantal.  Someone else can test Unity and Compiz.

I did try XFCE4 and Kubuntu however I myself am more productive with LXDE.

---

### Post by balloons on 2012-08-21
There's so many unity2d threads.. Anyways, spamming this link to all of them as I think it will help. If you want to try the new version of compiz (and help test it!) check this out. LLVMpipe is enabled, and working well for me so far. See how it fares for you. 

[http://ubuntuforums.org/showthread.php?t=2045579](http://ubuntuforums.org/showthread.php?t=2045579)

---

