---
title: "Why Was Unity 2D Discontinued?"
date: 2015-07-03
forum: Ubuntu, Linux and OS Chat
---

### Post by eival on 2015-07-03
it makes no sense that Linux distros, and the one that is supposed to be the most user friendly would give a reason that "unless you have a powerful 3D graphics card then tough" the 2D version from 12.04 has the same exact layout and features, just without any additional flair (and then have to know to install a hidden app that actually lets you disable all those animations an stuff)

how bout instead of bothering with a "Gnome Classic" you instead put that work into simply porting Unity 2D over for those who wish.

---

### Post by ian-weisser on 2015-07-04
Unity 2D was discontinued because it had completed what it set out to do. 
The Unity codebase, including Unity 2d, is open-source.
You are free to form a group and continue development of Unity 2d, and to port it to any platform you wish.

The main goals of Unity-desktop do not include aggressive resource conservation. That is, however, a main goal of the Phone GUI, and cross-pollination is certainly possible.

Several other very good desktop environments do have a main goal of minimizing resource consumption.

---

### Post by grahammechanical on 2015-07-04
I have said it before and I will say it again. This is just a user forum. We try to give help based on our own experience and what we have learned to those who have problems. Sometimes we discuss different things related to computing. We have 2 sections for discussions on subjects like this subject.

It is no good telling us what we should or should not do. We are not the developers and we most certainly are not the decision makers in Ubuntu.

A decision was taken many months ago to use in Ubuntu some software called llvmpipe. It is an open source video driver and it can replicate Unity 3D on video cards that do not have the capabilities to run Unity 3D. So, llvmpipe was seen as an alternative to Unity 2D. Therefore, it did not make sense to employ software engineers to continue maintaining and developing Unity 2D. Especially as Unity 2D uses Metacity as the window compositor and not Compiz. More code to maintain than is necessary.

[http://www.mesa3d.org/llvmpipe.html](http://www.mesa3d.org/llvmpipe.html)

Since the release of Ubuntu 14.04 there have been three ways by which a user will find himself running Ubuntu on llvmpipe.

1) When we install Ubuntu on a machine that does not have a video card that can do hardware accelerated 3D rendering.
2) When we enter recovery mode and choose the Resume option.
3) When there is some kind of conflict with a proprietary video driver the system will often revert to using llvmpipe.

Compiz animations are not enabled by default. And Compiz Configuration Settings Manager (CCSM) has the power to break the system. That is why it is not installed by default. It is not correct to say it is hidden.

Gnome Classic is a Gnome project and not a Ubuntu project. The same is true of Gnome session flash back. Which is what we should install on Ubuntu if we want that "classic" look, as Gnome Classic is an extension to the Gnome 3 Shell. Installing Gnome Classic will bring in Gnome 3 Shell and that requires video adapters as powerful as those required for Unity 3D. The Gnome developers do not consider it a waste of time to work on those projects. 

[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)

Regards.

---

### Post by monkeybrain20122 on 2015-07-05
> **grahammechanical said:**
> 

A decision was taken many months ago to use in Ubuntu some software called llvmpipe. It is an open source video driver and it can replicate Unity 3D on video cards that do not have the capabilities to run Unity 3D. So, llvmpipe was seen as an alternative to Unity 2D. Therefore, it did not make sense to employ software engineers to continue maintaining and developing Unity 2D. 
.


Have you tried llvmpipe? Its performance is horrible. There have been threads on this forum and Ask Ubuntu complaining about super sluggish unity 3D desktop running on llvmpipe and the advise is usually to switch to something without compositing. I have to wonder whether Canonical has actually tested running unity 3D on llvmpipe on the kind of graphic cards that unity 2D was made for. It is one thing for Canonical to say sorry guys, we have other goals and limited resources so we cannot maintain Unity 2D just for hardware that should have retired or will retire before 12.04 eol, but it is quite another to tell you they have a replacement which doesn't work.

@OP  You should stick to 12.04 if you like Unity 2D. You probably will need to get a new machine before 12.04 eol in two years anyway.

---

### Post by vasa1 on 2015-07-05
> **eival said:**
> it makes no sense that ...
You can choose from several other Ubuntu flavors (if you wish to stay with Ubuntu). That's what I did.

As ian-weisser pointed out, the code is available and if someone wants to keep Unity 2D alive they can do so. The MATE story is pretty much about how a group of people got together to keep the GNOME 2 "metaphor" alive.

---

### Post by night_sky2 on 2015-07-05
Because it doesn't make much sense to use a DE like Unity if you have older hardware.
Trying to make Ubuntu-Unity fully compatible with those had become a waste of time for the devs.

I mean in such a case you're far better off using something like Xubuntu, Lubuntu or even Ubuntu MATE now.
These flavors receive funding from Canonical and users get to share the offical Ubuntu support forum. ;)

---

### Post by eival on 2015-07-06
> **monkeybrain20122 said:**
> Have you tried llvmpipe? Its performance is horrible. There have been threads on this forum and Ask Ubuntu complaining about super sluggish unity 3D desktop running on llvmpipe and the advise is usually to switch to something without compositing. I have to wonder whether Canonical has actually tested running unity 3D on llvmpipe on the kind of graphic cards that unity 2D was made for. It is one thing for Canonical to say sorry guys, we have other goals and limited resources so we cannot maintain Unity 2D just for hardware that should have retired or will retire before 12.04 eol, but it is quite another to tell you they have a replacement which doesn't work.

@OP  You should stick to 12.04 if you like Unity 2D. You probably will need to get a new machine before 12.04 eol in two years anyway.

12.04 has annoying issues like fullscreening moving to your launcher window in dual screen mode which were never fixed in the point updates which is why i had moved up to 14.04 earlier than intended in the first place, otherwise i had been waiting till the final year of the LTS in both 8.04 and 10.04 to make sure any bugs or issues were weeded out when i upgraded.

ive actually just installed Ubuntu-MATE last night (since i know from previous experience that just trying to install a DE on top of Ubuntu usually just results in it crashing and gong back to Unity) after wanting to originally like Lubuntu since its the objectionably lightest variant but its menu options and other stuff is just way too complicated than it needs to be and MATE seemed like the only one that has enough of a support backing and has the dark Ubuntu/Gnome style options built-in, vs say Mint

if Debian didnt treat you like a prisoner even with admin status i would happily stay with them, which is what i used back between 10 LTS an 12 LTS when Unity first came out and those same DE crashes occurred in 12.04 "classic" mode before finally learning Unity's layout because of Debian's issues

also its super great that every time i empty the trash bin it doesnt open file manager for no reason like 15.04 Ubuntu

i hate not having the side launcher, but i plan on trying to replicate it here in the coming days. and i agree with you with the GPU issues of Unity/Compiz, the fact that Haswell IGP's aren't even tested is ridiculous, nobody is going to have a high end graphics card on Linux, since Steam OS has yet to make any dent in game development and the IGP's of Haswell are more than sufficient to run multiple monitors and stream the highest HD content available, considering i was doing it just fine with the pitiful G45 chipset graphics prior to about a month ago.

and NO, animations arent turned off by default, which is why i have always had to install CCSM for the last 3 LTS' to turn all that crap off

---

