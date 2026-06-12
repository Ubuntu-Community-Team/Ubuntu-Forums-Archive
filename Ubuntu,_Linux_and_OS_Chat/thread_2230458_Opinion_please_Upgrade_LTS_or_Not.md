---
title: "Opinion please: Upgrade LTS or Not?"
date: 2014-06-19
forum: Ubuntu, Linux and OS Chat
---

### Post by tecknomage on 2014-06-19
I am now running **Ubuntu 14.04 LTS** on my laptop.

In your opinion, should I apply upcoming **general UPGRADES** OR wait unitl the next **LTS UPGRADE** :-s

---

### Post by pfeiffep on 2014-06-19
I'm also running 14.04 LTS and find that there are multiple software upgrades weekly. Perhaps I didn't understand your question ;-)

---

### Post by LastDino on 2014-06-19
General daily upgrades consist of security patches and other bug fixes, so yeah, you should *always* do them irrespective of OS you're using, this is completely independent issue from your LTS upgrade. Distro upgrade (LTS) is optional as long as your existing OS is receiving the general daily updates.

And you said you're using 14.04 LTS right now, so that's the latest LTS version available for at least next 2 years. So, I don't know what you mean by waiting for next LTS upgrade?

---

### Post by MartyBuntu on 2014-06-19
> **tecknomage said:**
> I am now running **Ubuntu 14.04 LTS** on my laptop.

In your opinion, should I apply upcoming **general UPGRADES** OR wait unitl the next **LTS UPGRADE** :-s

Unless you need specific upgrades to apps that aren't serviced by either the repository or PPA's, stick with LTS versions.

I've stuck with LTS versions since 8.04.

---

### Post by monkeybrain20122 on 2014-06-19
Well whatever you do, disable the upgrade notification  in update-manager for your own protection. People shouldn't 'upgrade' just because of a popup on the zeroth-day of a new release based on impulse (or click the wrong button by accident if you have a bad day or a slip of the finger). If you want tp update the OS, wait a bit after release for the post release bug fixes, do some testings and research (read the forum, checking out bugs on launchpad etc) and then backup your data and do a fresh install, it is a lot faster and more reliable than 'upgrade'.

---

### Post by sudodus on 2014-06-19
> **tecknomage said:**
> I am now running **Ubuntu 14.04 LTS** on my laptop.

In your opinion, should I apply upcoming **general UPGRADES** OR wait unitl the next **LTS UPGRADE** :-s

I'm talking about production systems now, where you need stability.

If you are running **Ubuntu 1[COLOR=#ff0000]2[/COLOR].04 LTS**, continue with it (and do daily updates/upgrades within the version) at least until the first point release of 14.04 LTS, 14.04.1 is out in July or August. If you are running** Ubuntu 1[COLOR=#ff0000]4[/COLOR].04 LTS**, continue with it (and do daily updates/upgrades within the version) but do not upgrade to 14.10, 15.04, 15.10. Instead wait until the next LTS release, 16.04.1 LTS.

You can dual boot with a bleeding edge system, if you are interested, and maybe want to help testing the new versions of Ubuntu.

---

### Post by deadflowr on 2014-06-20
we're talking release upgrades, right?
simply set it to lts releases only, or never.
if on 14.04 now, even if you set it to the lts only flag, it'll be over two years until it pops up.

And contrary to some beliefs, even if you click on the upgrade to new release button, you still have two or three windows to go before the actual upgrade proceeds, as such you can cancel it at anytime before with no harm to the system. The upgrade starts when you click on install(maybe it says upgrade) at the page which lists how much will be upgraded, and how long it will take based on your network speed.
And even on that page there's a big fat cancel button right next to it.

---

### Post by tecknomage on 2014-06-24
> **pfeiffep said:**
> I'm also running 14.04 LTS and find that there are multiple software upgrades weekly. Perhaps I didn't understand your question ;-)

You are confusing **updates** with **upgrades**. What you refer to are updates.

**Upgrades** are like 13 to 14.

---

### Post by tecknomage on 2014-06-24
> **sudodus said:**
> I'm talking about production systems now, where you need stability.

If you are running **Ubuntu 1[COLOR=#ff0000]2[/COLOR].04 LTS**, continue with it (and do daily updates/upgrades within the version) at least until the first point release of 14.04 LTS, 14.04.1 is out in July or August. If you are running** Ubuntu 1[COLOR=#ff0000]4[/COLOR].04 LTS**, continue with it (and do daily updates/upgrades within the version) but do not upgrade to 14.10, 15.04, 15.10. Instead wait until the next LTS release, 16.04.1 LTS.

You can dual boot with a bleeding edge system, if you are interested, and maybe want to help testing the new versions of Ubuntu.

Again, the confusion between updates and upgrades. **Ubuntu 14.04.01 is an update.** That leaves the question of 14.10 being an update or not, 15.04 would definitely be an upgrade.

---

### Post by QIII on 2014-06-24
Canonical has a 6 month release cycle.  So 14.10 will be a release upgrade, as will 15.04 from there.

The LTS versions also are issued "point releases", 14.04, 14.04.1, 14.04.2, etc.  Non-LTS releases do not get those.  You might just as well call point releases "version upgrades", as there my be significant technological changes as we saw between 12.04.1 and 12.04.2.

When 14.04.1 is released, you may choose to ***upgrade ***to it from 14.04 or stay with 14.04 and ***update ***it on your regular schedule until you upgrade to new version.

An "upgrade" goes from release to release.  An "update" updates within the release.  

Some confusion is generated by the fact that we use 

```
 sudo apt-get upgrade 
```

and

```
sudo apt-get dist-upgrade
```

to update packages *within* a release.  That is what Sudodus means by "daily updates/upgrades".

There is no confusion in Sudodus' terminology in his post.

---

### Post by craig10x on 2014-06-24
One thing i am a little confused about is, i am running 14.04...so when 14.04.1 arrives, do you do an actual upgrade into it or are you already in 14.04.1 by the fact that you have been letting the software updater do it's daily updates?

If you do an actual upgrade, does it pop up automatically in the software updater, or do you have to "trigger it" somehow? And does it include any kernel upgrade that might be part of the point release?

---

### Post by deadflowr on 2014-06-24
> **craig10x said:**
> One thing i am a little confused about is, i am running 14.04...so when 14.04.1 arrives, do you do an actual upgrade into it or are you already in 14.04.1 by the fact that you have been letting the software updater do it's daily updates?

If you do an actual upgrade, does it pop up automatically in the software updater, or do you have to "trigger it" somehow? And does it include any kernel upgrade that might be part of the point release?

Keep updating it and you'll be at 14.04.1 without needing to reinstall, or something like that.
14.04.1 won't be having any new kernel series, it should still have 3.13-whatever.
Now 14.04.2 will get the utopic kernel, however I believe you would either need to install yourself(the kernel, I mean), or do a fresh install of the latest iso.

---

### Post by craig10x on 2014-06-24
Thanks deadflowr...i thought that's the way it worked...although as far as getting the utopic kernel when 14.04.2 arrives...some have told me you have to install that manually (with some kind of "hardware stack" thingee) and others have told me me: no, you get it automatically along with your regular updates...so on that one i am still confused...

---

### Post by deadflowr on 2014-06-24
> **craig10x said:**
> Thanks deadflowr...i thought that's the way it worked...although as far as getting the utopic kernel when 14.04.2 arrives...some have told me you have to install that manually (with some kind of "hardware stack" thingee) and others have told me me: no, you get it automatically along with your regular updates...so on that one i am still confused...

Well. That always beats me.
I have precise installed from 12.04, before any point release version, and it only has 3.2-whatever kernel.
It has never asked or stated any other kernel version to be installed.

But I have seen threads of posters who originally installed 12.04.2, or .3 and have kept the system fully updated and they too, still have the kernel series they started with(either 3.5 or 3.8)
(I get this from the posters info which would have been requested to help overcome whatever problems they might have had)

Why some people somehow get a newer kernel is not something I'm familiar with.
But I do think you actually have to install the lts-release-version-name package.

---

### Post by LastDino on 2014-06-24
I was under the impression that kernel updates happen with your general updating process of either GUI (software and update manager - I could be wrong about this as I run mostly commands to update/upgrade) or command (**sudo apt-get dist-upgrade)**. I don't know what you mean by hardware stacking thingy but you can very much install latest by simply running something like this 
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

---

### Post by Gyokuro on 2014-06-24
I think LTSEnablementStack ([https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)) is meant here which is for people which want to stick with LTS but want to use newer Kernel+Xorg+Mesa for various reasons (hardware support) but I agree with deadflowr as soon your system runs with a Longterm supported kernel why you should upgrade? In my case testing needs so much time that I do not even care about LTSEnablementStack due to that all tests must be redone against the LTSEnableStack and therefore stick with 3.2.XX and it's Xorg/Mesa parts until the system is EOL whether I later upgrade to 14.04 is another question and at the moment I tend to skip 14.04 until a new LTS release which is similar to Debian Jessie but that's my/our requirement(s).

---

### Post by deadflowr on 2014-06-24
> **LastDino said:**
> I was under the impression that kernel updates happen with your general updating process of either GUI (software and update manager - I could be wrong about this as I run mostly commands to update/upgrade) or command (**sudo apt-get dist-upgrade)**. I don't know what you mean by hardware stacking thingy but you can very much install latest by simply running something like this 
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

This is a good explainer
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by LastDino on 2014-06-24
> **Gyokuro said:**
> I think LTSEnablementStack ([https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)) is meant here which is for people which want to stick with LTS but want to use newer Kernel+Xorg+Mesa for various reasons (hardware support) but I agree with deadflowr as soon your system runs with a Longterm supported kernel why you should upgrade? In my case testing needs so much time that I do not even care about LTSEnablementStack due to that all tests must be redone against the LTSEnableStack and therefore stick with 3.2.XX and it's Xorg/Mesa parts until the system is EOL whether I later upgrade to 14.04 is another question and at the moment I tend to skip 14.04 until a new LTS release which is similar to Debian Jessie but that's my/our requirement(s).

Thanks, looks like a good read. Pardon my ignorance, I've every little Linux experience.

---

### Post by monkeybrain20122 on 2014-06-24
You don't need to wait for lts point releases to update kernel and xorg/mesa. I have more updated kernels and xorg/mesa driver in 13.10 than 14.04 (need  newer kernel for something or others, minor things)

 Kernels can be installed from mainline and graphic driver from [https://launchpad.net/~oibaf/+archive/graphics-drivers](https://launchpad.net/~oibaf/+archive/graphics-drivers). The drivers are a lot better in performance than Ububtu's stock offer. For Intel and many AMD cards I would use it,--for some AMD cards the up to date open driver is as good as or even better than the fglrx driver for most purposes (other than gaming) and easy to maintain and upgrade.

There are of course always some risks in using bleeding edge graphic driver so I maintain an image of the latest working version (doesn't take too long to just clone the / partition) so in case an update goes busted I can revert to the most recent working OS without throwing away all the gains up to that point,--otherwise can always go all the way back to square one with ppa-purge. When I hit a sweet spot I would just disable the ppa.

---

### Post by craig10x on 2014-06-24
Interesting you should mention that, monkeybrain20122, because i installed 3.15 final from the mainline and it's really solid for me and took care of the multimedia instability problems i was having on my hardware with the "stock" 3.13 kernel (actually, originally it was ok but then some update they did to fix something else caused the regression for me in the form of the instability problem)...

Yeah, i think deadflowr is right...you wouldn't get the utopic kernel on 14.04 unless you manually upgrade to it yourself...

---

### Post by techcaptain on 2014-06-30
If you want the long support and stable version, go for Ubuntu 14.04 LTS definitetly. 
If you want the features, you can wait for Ubuntu 14.10 Utopic Unicorn.. or if you are desperate for a choice, get a daily build.
(Just a note; this is still ALPHA stage! This is very risky, and only really intended for devs.)

For me, I would just stick where you are and wait for Utopic Unicorn to come out. Upgrading to Ubuntu 14.04 and then to 14.10 will be a hassle.
If you don't want 14.10, I say just go to 14.04.

---

### Post by techcaptain on 2014-06-30
Oh also it might take some time to release a new LTS... you know, it hasn't been so much long since they released Ubuntu 14.04 LTS.

---

### Post by craig10x on 2014-06-30
> **techcaptain said:**
> Oh also it might take some time to release a new LTS... you know, it hasn't been so much long since they released Ubuntu 14.04 LTS.

New LTS releases are every two years...so after the current 14.04 LTS you won't see another LTS until 16.04 (April, 2016)...
All the other releases (such as the 14.10 which is coming in October) are the 6 month releases...

---

### Post by monkeybrain20122 on 2014-06-30
> **craig10x said:**
> 
All the other releases (such as the 14.10 which is coming in October) are the 6 month releases...

9 moth releases. :) I don't mind interim releases if I can use it for 7-8 months (I am using 13.10 still, it would be 7.5 months when I replace it with 14.04 in a couple of weeks) But I may stick to 14.04 a bit longer because of Mir. I don't want to have to downgrade when 15.10 comes out.

---

### Post by craig10x on 2014-06-30
Well, actually, they are 6 month releases with 9 months of updates ;)
From what i have been reading, Unity 8 and Mir won't be the default until 16.04 so if that is the case, you would have nothing to be concerned about if you want to upgrade to 14.10 and so forth...:D

---

### Post by monkeybrain20122 on 2014-06-30
I think Mir and Unity8 will be default in 15.10 because they want to get all the bugs out before the next LTS.

---

### Post by craig10x on 2014-06-30
I guess you may have missed this, then ;)
[http://news.softpedia.com/news/Mir-Displayer-Server-to-Be-Default-in-Ubuntu-16-04-LTS-431875.shtml](http://news.softpedia.com/news/Mir-Displayer-Server-to-Be-Default-in-Ubuntu-16-04-LTS-431875.shtml)

---

### Post by monkeybrain20122 on 2014-06-30
> **craig10x said:**
> I guess you may have missed this, then ;)
[http://news.softpedia.com/news/Mir-Displayer-Server-to-Be-Default-in-Ubuntu-16-04-LTS-431875.shtml](http://news.softpedia.com/news/Mir-Displayer-Server-to-Be-Default-in-Ubuntu-16-04-LTS-431875.shtml)

"By 16.04" means 'no later than 16.04", it can be before. ;) I doubt that they would start that with a LTS. I read somewhere in the +1 forum that 15.04 will still be Unity7 but 15.10 is going to be Unity8 + Mir. The person seemed to know what he/she was talking about.

---

### Post by craig10x on 2014-06-30
Ok...makes sense ;)
However, it should be very stable by 15.10 :D
You could continue to upgrade into each new 6 month version if you like and when 15.10 arrives, just run it live and if ok, then upgrade to that too...if not, skip until 16.04...
I'm probably going to do that, myself...

---

### Post by monkeybrain20122 on 2014-06-30
> **craig10x said:**
> 
You could continue to upgrade into each new 6 month version if you like and when 15.10 arrives, just run it live and if ok, then upgrade to that too...if not, skip until 16.04...
I'm probably going to do that, myself...

But 15.04 doesn't have one year support, not sure how you can 'skip' if 15.10 turns out to be buggy .. unless you plan to run 16.04 pre-beta (probably your choice) or stay with 15.04 for 3 months without support (or downgrade back to 14.04 for 3 months??!!)

---

### Post by craig10x on 2014-06-30
That is true of course...but many are testing the available images for mir and unity 8 so i have confidence that 15.10 will be fine...doubt that they would make it default on 15.10 unless the felt it was really ready for prime time...

---

### Post by mc4man on 2014-07-04
> **tecknomage said:**
> I am now running **Ubuntu 14.04 LTS** on my laptop.

In your opinion, should I apply upcoming **general UPGRADES** OR wait unitl the next **LTS UPGRADE** :-s
I'd stick with 14.04, certainly until you know you'll want what 16.04/unity8/mir/unity window compositor/ect., ect.  offers on desktop installs.
There's a solid possibility it won't please a number of current users..., yours truly included.

---

