---
title: "How is it that 18.04 is considered LTS..."
date: 2018-06-03
forum: Ubuntu, Linux and OS Chat
---

### Post by rnctx on 2018-06-03
...when there is no obvious way to install a desktop with the same functionality as 16.04?


[LIST]
[*]unity doesn't work because GDM3 broke it when you upgraded your 16.04 install in all likelihood
[*]GDM3 doesn't work if you need VNC
[*]can't log in to Gnome desktop using xorg because of [this bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1766137").
[*]purging everything desktop related and trying to reinstall unity and xorg won't work because GDM3 is a dependency to reconfigure lightdm
[*]if you can't reconfigure lightdm you can't ever see a greeter other than the gdm3 greeter
[/LIST]

It's like this OS decided to fall back to the early 2000s broken desktops just for grins one last time.  What could possibly be the motivation to break every default desktop configuration that you have and push it as a LTS release?

The bug reporting that unity was broken linked above is now a month + a week old. 
 
LTS...  
Default desktop on a desktop distro...  
Broken for 5 weeks.

Who in their right mind would buy into the IPO that this operation seems to want to get to?

---

### Post by wildmanne39 on 2018-06-03
*Thread moved to **Ubuntu, Linux and OS Chat for a more appropriate fit**.*

---

### Post by sudodus on 2018-06-03
General advice for all LTS releases:

If you want a smooth ride you are recommended to wait with upgrading until the first point release (late July or early August).

By that time several bugs will be squashed and 18.04.1 LTS is likely to work well, both as a fresh install and when upgraded from 16.04 LTS.

---

### Post by rnctx on 2018-06-03
> **sudodus said:**
> General advice for all LTS releases:

If you want a smooth ride you are recommended to wait with upgrading until the first point release (late July or early August).

That is the very opposite of what LTS means.

> **sudodus said:**
> 
By that time several bugs will be squashed and 18.04.1 LTS is likely to work well, both as a fresh install and when upgraded from 16.04 LTS.

From their own documentation...

```
[COLOR=#333333][FONT=&amp]Furthermore, we define the LTS to be:[/FONT][/COLOR]
[LIST]
[*]**Enterprise Focused:** We are targeting server and multiple desktop installations, where the average user is moderately risk averse.
[*]**Compatible with New Hardware:** We will make point releases throughout the development cycle to provide functional support for new server and desktop hardware.
[*]**More Tested:** We will shorten the development window and extend the Beta cycle to allow for more testing and bug fixing
[/LIST]

```

This release is a failure on all three of those points.

If anyone were using this as an 'average user' that dist-upgrade command from 16.04 just cost them a day of their life reinstalling their OS. **

There are driver related bugs with nVidia and AMD as well, so on the second claim the answer is no, not compatible.

Number three is laughable in this context. It's fairly obvious what happened here: they planned to ship wayland as the default, and then when it became obvious that doing so was impossible without an even bigger backlash, there was a rush to hack something together so that the two year deadline wouldn't blow by. And now the people who foolishly thought that they could keep unity running for remote desktop/VNC support are 5 weeks into waiting on a fix of this cobbled together garbage.

** On the bright side, I now see why everyone was so excited about ZFS in 16.04.  You need ZFS to run Ubuntu on any computer that you own, because if you make the mistake of dist upgrading it you'll need that snapshot to restore to, lest you wind up wasting a few hours dumping configs and reinstalling everything.

---

### Post by rnctx on 2018-06-03
I should point out that my reason for upgrading to 18.04 is that the official repository package of docker (docker-io) is broken on 16.04 (it will not complete 'hello world' after install).  So to add fuel to the fire of common, everyday things that Ubuntu is failing miserably at:  long term support in general.

As of right this minute, the only combination of 18.04 + a working desktop + a working docker from official PPAs that  can be had is from the Unity7 fork @ [http://people.ubuntu.com/~twocamels/](http://people.ubuntu.com/~twocamels/)

No combination of current package fixes lightdm in official 18.04, its greeter cannot log in.   No combination of package fixes of GDM3 changes the fact that wayland has no screen sharing support, which is a regression in functionality from 16.04.

So I'm going to spend the next two hours installing a fork and locking the desktop packages to their versions as of that install.  It's so Linux, in a 1998 way....

---

### Post by rnctx on 2018-06-03
I take the above back, the Unity7 fork cannot enable any sort of sharing without a crash of the settings manager.

tl;dr: Ubuntu shipped a LTS version that is incapable of VNC. 

 So the 1998 jab above was not *entirely* accurate.  Google seems to think that VNC was invented by an Oracle lab in 1999.  So I was off by a year in terms of guesstimating major regressions in which a user would assume that pushing a desktop session over a network is some sort of wizardry not yet invented. We haven't gone back in time all the way to 1998, rather just 1999.

---

### Post by monkeybrain20122 on 2018-06-03
I don't know about the two camal iso, it was rather old and for beta testing.

But it is rather easy to install unity in standard 18.04

```
sudo apt install ubuntu-unity-desktop
```

make lightdm your default when prompted

reboot, that's it.

If need touchpad
```

sudo apt install xserver-xorg-input-synaptics
```

If it all works just remove gnome-shell and gdm3 (which will remove ubuntu-unity-desktop, but that is only a meta-package)

have been using this for a while and it works well, but I am not using vnc so I don't know about that.


BTW My work computer is still 16.04 and not planning to upgrade (will be fresh install) til next April. ;)

---

### Post by lostmoonofsaturn on 2018-06-03
Unity on 18,04 is supported only by the community and, as such, has been moved to the Universe repository. An impact of this is that if changes in Ubuntu going forward break something in Unity-on-18.04 the fixes for Unity depend on community effort, not Canonical's.

I.e., assessments of the LTS readiness of 18.04 shouldn't be based on how Unity performs on it.

I'm using Unity on 18.04 via a clean install and then adding ubuntu-unity-desktop. dpkg-reconfigure popped up during that install to offer a choice between GDM and LightDM.

Folks who prefer a Unity that's still supported by Canonical should stay with 16.04 as long as possible.

---

### Post by wildmanne39 on 2018-06-03
I will throw my 2 cents worth in, I have been running 18.04 since testing began and I have not really had any issues and while you think it is bad and full of bugs the issues that you are experiencing are not being experienced by most people out of the millions that use it the only users that post are the few that are having issues and can not resolve them other wise, true no operating system is perfect not even the ones you pay for but I will say that a clean install is better in most cases then an upgrade in my opinion and no Canonical never planned to have wayland as default in 18.04.

---

### Post by poorguy on 2018-06-03
Well I've installed ***Ubuntu 18.04 LTS (64 Bit) minimal install OOTB ***on many different desktop computers ranging from at least*** 10 years old to only 5 years old.***

I've not had an  issue that I recall and as for ***Gnome Desktop*** I have ***no complaints*** and it is ***100%*** better than ***Unity *** imo although others will disagree.

I didn't care for [COLOR=#0000cd]***Ubuntu 16.04 LTS***[/COLOR] as I had to many issues with it on my old ***Frankenstein Builds*** although ***Ubuntu 18.04 LTS*** works without problems on my old*** Frankenstein Builds*** which*** [COLOR=#0000cd]Ubuntu 16.04 LTS[/COLOR]*** only created problems on.

I never figured out why and don't care anymore.

[I][B]Bionic Beaver Rocks. :guitar:



[/B][/I]

---

### Post by TheFu on 2018-06-03
People who don't like change will always be disappointed.  Sometimes that includes me with some choices that Canonical makes.  I've come up with a solution.  Avoid their GUIs.  I'm not disappointed any since 12.04 when Unity was first made the default.  If you want a GUI that is unlikely to change much, check out i3.

Can't say anything about VNC. Haven't used that in at least 10 yrs.  NX stuff just works better for my needs - mainly it feels 2-3x faster than VNC ever did and it is based on ssh, so an extra tunnel isn't needed.  

LTS is about using less risky software versions that can be supported for 5 yrs, it isn't a guarantee of perfection.  That's why Wayland was introduced with 17.10 - to see if there were huge or small issues left to be resolved.  

I tested 18.04 before release for a few weeks.   Some things worked well and other things didn't work so well for me.  The new installer ensured I wouldn't be able to use the normal ISO files, since some of the important things left out are very important to my setups.  I provided feedback on a few elements about 2 months prior to the release which were heard and actions taken. It was nice to see that. The release team didn't do everything I wanted, but that is to be expected. I can be an extreme case.

Anyways, the 18.04 release isn't all bad, though it might seem less-great to you, for your needs.

---

### Post by mc4man on 2018-06-03
Your bullet points are only accurate in that they *may* occur for those that choose to  manually do a release upgrade from 16.04 to 18.04. 
Due to the extreme number of changes from 16.04 to 18.04 an official release upgrade won't be ready or offered until 18.04.1, around beginning of  July. 
This is clearly stated in the 18.04 release notes so any blame should be directed towards yourself..

---

### Post by poorguy on 2018-06-03
> **TheFu said:**
> 
People who don't like change will always be disappointed.

I agree. ;)

> **TheFu said:**
> 
LTS is about using less risky software versions that can be supported for 5 yrs, it isn't a guarantee of perfection.
  
I read where certain software in ***Ubuntu 18.04*** is a few versions behind, hey as long as it works and bug free that's my idea of software perfection.

> **TheFu said:**
> 
Anyways, the 18.04 release isn't all bad

I ain't got no complaints with it. :)

I'll always be partial to*** Ubuntu 14.04*** as that was my very first*** Ubuntu*** distro.

---

### Post by PaulW2U on 2018-06-04
> **rnctx said:**
> 
LTS...  
Default desktop on a desktop distro...  
Broken for 5 weeks.

I'm writing this reply to you on something that started out as Ubuntu 17.10. I immediately installed the **vanilla-gnome-desktop** package as I wanted to use something that was closer to the former Ubuntu GNOME rather than Canonical's interpretation of what GNOME Shell should like. At some point I used the quick and dirty method to upgrade to Ubuntu 18.04 by changing the entries in **/etc/apt/sources.list** to point to the bionic repositories. For the entire development period of Ubuntu 18.04 I had very few problems. As my relatively new laptop has both a hard drive and SSD I created a second installation on the hard drive which has also been trouble free.

The installation on the SSD has now been upgraded to the current development release which will in due course become Ubuntu 18.10. That upgrade was also done by the quick and dirty method rather than any officially recognised upgrade procedure. I don't have any of the problems that many users come to the Ubuntu Forums with. In my opinion Ubuntu is far more robust than I think you have found. My installation of Xubuntu 18.04 is also working well on an old laptop that I use when not sat at my computer desk although admittedly a previously forced upgrade prior to being notified that an upgrade was available from Xubuntu 16.04 didn't go very well. 

Please don't take your experience of the latest Ubuntu LTS as being typical as many of us are quite happy with what we use on a daily basis. As mc4man has already pointed out many users are upgrading before the 18.04.1 release which won't be made available until late July. Upgrades from the previous LTS have not yet been fully tested. That will happen and any obvious issues rectified but **a lot** of testing will be required due to the change in desktop from Unity to GNOME Shell.

The [Release Notes]("https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes") are seldom read. :(

---

### Post by Geoffrey_Arndt on 2018-06-04
> **rnctx said:**
> ...Who in their right mind would buy into the IPO that this operation seems to want to get to?

Hmm, . . . an IPO has very little to nothing to do with Unity or Gnome3, lightDM, etc.    As previous posters have already stated, these minor functionality issues will get weeded out in Ubuntu 18.04.1 or 18.04.2.    

The IPO (for 2019 or possibly 2020) will be related to the capabilities Canonical will have implemented for IoT and Cloud mgmt (and very little with consumer desktops).

---

### Post by QIII on 2018-06-04
Just a point to put this in order:  LTS is an acronym for "Long Term Support" -- which it will receive.

It has nothing whatsoever to do with MEH (Make Everyone Happy), ANB (Absolutely No Bugs), EJW (Everything Just Works) or MYB (Makes Your Breakfast).

Why is 18.04 called an LTS?   Because that's what it is.

If you want help with any of its failings, by all means ask.  That is what we are here for.  We are under no illusions that Ubuntu is perfect.  We are under no misapprehension that Canonical gets everything right -- or is particularly wise in some of the questionable decisions that it makes.

But a running gripe session is of little value here because nobody here works for Canonical and none of us is in a position to affect change.  We are all equally able to contact Canonical, make bug reports through apport and create a launchpad account.

This very conversation is repeated with every release when someone comes along and declares the new release "the worst release evah!"

To avoid yet another Oroboros being hatched, please don't press this further.  If you have further issues, you may start individual support requests for each -- provided your request for support does not become a running editorial.

---

### Post by rnctx on 2018-06-04
I'll just keep updating this thread as I run across more ridiculous things that a LTS release should't do...

Today's contestant:

If you abandon the idea of upgrading from 16.04 and backup/reinstall everything on a fresh 18.04, thus getting a desktop environment to work with the same functionality you had in 16.04, it only works until you actually *do* anything.

Launching a QT based gui application, for example, spawns a Wayland process, killing the xorg process, thus immediately terminating whatever other things you had running that don't work on Wayland.

This is all a grand joke, honestly.

---

### Post by QIII on 2018-06-04
OK.  Thank you.  Running troll and gripe session terminated.

---

