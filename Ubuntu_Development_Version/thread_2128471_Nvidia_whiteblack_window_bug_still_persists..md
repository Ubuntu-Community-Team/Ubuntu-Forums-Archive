---
title: "Nvidia white/black window bug still persists."
date: 2013-03-23
forum: Ubuntu Development Version
---

### Post by monkeybrain2012 on 2013-03-23
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/729979](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/729979)

It says that fix has been released in compiz - 1:0.9.9~daily13.02.19-0ubuntu1 (post 162) But it is still the same here with Nvidia driver 313. 

(Upgrade Compiz with [https://launchpad.net/~smspillaz/+archive/compiz-experimental](https://launchpad.net/~smspillaz/+archive/compiz-experimental), it is still the same with regard to black windows, but fixes [http://ubuntuforums.org/showthread.php?t=2128354](http://ubuntuforums.org/showthread.php?t=2128354))

---

### Post by monkeybrain2012 on 2013-03-25
Two days and not a single comment. Does no one experiencing this problem any more or everyone has stopped buying Nvidia? :)

---

### Post by cjcj on 2013-03-25
Saw this a couple of days ago and was waiting to check wherether I still see this bug this too. I do still have this bug on a completely updated raring installarion with an nvidia GeForce GT630 graphics card. I am using the version 313 proprietary driver installed via the additional drviers tab of the software sources set up. 

Have you reported this as a bug?

---

### Post by dino99 on 2013-03-25
have you reset compiz ? or ran ccsm ?

> compiz --replace ccp &

---

### Post by cjcj on 2013-03-26
Yes have restarted compiz with compiz --replace ccp & . This surely happens anyway with every restart (?). The problem still persists as of newly updated on 26 March.

---

### Post by dino99 on 2013-03-26
i've reported that issue, possibly related with that problem:
[https://bugs.launchpad.net/ubuntu-gnome/+bug/1160197](https://bugs.launchpad.net/ubuntu-gnome/+bug/1160197)

---

### Post by monkeybrain2012 on 2013-03-26
> **cjcj said:**
> Saw this a couple of days ago and was waiting to check wherether I still see this bug this too. I do still have this bug on a completely updated raring installarion with an nvidia GeForce GT630 graphics card. I am using the version 313 proprietary driver installed via the additional drviers tab of the software sources set up. 

Have you reported this as a bug?

There is already a bug report, I have provided the link in my first post. Here it is again
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/729979](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/729979)

Problem is that it says a fix has been released and the raring daily build actually has a higher version of compiz. I have added another comment but so far no one has responded. I am also using the Nvidia 313 driver, I will try another one later and see if the problem still persists (but I am needing to reinstall because I have repartitioned my hard drive)

---

### Post by monkeybrain2012 on 2013-03-26
> **dino99 said:**
> i've reported that issue, possibly related with that problem:
[https://bugs.launchpad.net/ubuntu-gnome/+bug/1160197](https://bugs.launchpad.net/ubuntu-gnome/+bug/1160197)

Hmm... may be because I am dense, I  am not sure how your bug has to do with the bug in this thread.

---

### Post by fldc on 2013-03-27
yes, this sucks, the problem very much so still exist, I get a black window almost every time I restore a minimized window.

---

### Post by monkeybrain2012 on 2013-03-30
Odd that there are so few replies to this thread. Do other people using Nvidia and Unity experience this problem?? 

After repartitioning my hard drive I have done a reinstall using a newer image two days ago and so far I have not been able to install any Nvidia driver so I can't test it now. 

There is still no response on the launchpad thread regarding the status  of this bug (the bug was assigned to Sam Spilsbury but he is no longer  working for Canonical, I emailed him and only got an "I don't know".) May need to open a new bug if the issue persists.

---

### Post by monkeybrain2012 on 2013-04-01
Wow, this thread has been sitting here for a week and I get only one "me too". What happens to other people with Nvidia cards? Have you experienced no problem, solved the problem, or given up? If there is any workaround please share.I have installed emerald as someone advised but still no change. 

Now the Compiz version is 0.99~daily13.03.29 Ubuntu1 and the issue has not improved. This has been a problem since Precise's release and it says on the  lauchpad thread that I linked to in my first post that a fix has been released but still no luck. The launchpad thread  has not seen any activity for a while, so I am going to file a new bug later. 

Raring is fast and responsive except for this bug which is almost a show stopper for me.

---

### Post by dino99 on 2013-04-01
have you followed the "sticky" thread into "updates" subforum ?

---

### Post by monkeybrain2012 on 2013-04-01
> **dino99 said:**
> have you followed the "sticky" thread into "updates" subforum ?

Where is the updates subforum?

---

### Post by dino99 on 2013-04-01
> **monkeybrain2012 said:**
> Where is the updates subforum?

is that your April 1st joke ?  [http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

---

### Post by monkeybrain2012 on 2013-04-01
> **dino99 said:**
> is that your April 1st joke ?  [http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

I asked because I am not sure what my thread has to do with "installation and upgrade". It is a long standing bug, a bug has been filed on lauchpad, it says that a fix has been released but the fix doesn't work apparently. I would like to see if orher people with Nvidia are still experiencing the problem and if there is a known work around. It is not an upgrade by the way,

---

### Post by monkeybrain2012 on 2013-04-02
I have created a new bug report [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1162954](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1162954)

If this also affects you please go over there and add a "me too". Thanks,.

---

### Post by dino99 on 2013-04-02
> **monkeybrain2012 said:**
> I asked because I am not sure what my thread has to do with "installation and upgrade". 

that is where that sticky can be read (about your black/white windows issue)  ](*,)](*,)

---

### Post by monkeybrain2012 on 2013-04-02
> **dino99 said:**
> that is where that sticky can be read (about your black/white windows issue)  ](*,)](*,)

I am not sure if you read my posts. I didn't boot into a black screen. OK, in case you (or anyone else) haven't read my link to launchpad, let me clarify: when using the alt+tab switcher to focus applications the targeted window opens to be black and blank (in Precise it was white and blank). This bug only manifests when using the Nvidia blobs, it disappears if you use nouveau.

It is a Compiz + Nvidia bug that has been around for more than a year and finally a fix was released, but the fix apparently doesn't work. I am asking if anyone else is still experiencing this problem or perhaps the fix only doesn't work on my hardware, and if anyone knows what is the status of thisbug, as I have posted a comment on Launchpad and received no reply. I have now opened a new bug.

Thanks for bumping the thread though,

---

### Post by monkeybrain2012 on 2013-04-04
If this bug still affects you please add a "me too" [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1162954](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1162954)

I can't be the only one in the Ubuntu community still having this problem.

---

### Post by alphacrucis2 on 2013-04-04
I have nvidia card and using 313 updates driver. I've never seen the problem mentioned. Perhaps specific to certain cards.

```
*-display               
       description: VGA compatible controller
       product: GF119 [Quadro NVS 4200M]
       vendor: NVIDIA Corporation
```

---

### Post by monkeybrain2012 on 2013-04-04
> **alphacrucis2 said:**
> I have nvidia card and using 313 updates driver. I've never seen the problem mentioned. Perhaps specific to certain cards.

```
*-display               
       description: VGA compatible controller
       product: GF119 [Quadro NVS 4200M]
       vendor: NVIDIA Corporation
```

Interesting, never have access to a quadro card but this happens in several Geforce cards I have tested.

However, at least in Raring, this bug only manifests itself when several instances of the same applications are in use. For example, suppose you have Firefox, one instance of calc and two instances of evince in use (two pdf), if you use the alt-tab switcher to focus on either Firefox or Calc there is no black window, it only happens if you chosse to focus one of the instances of evince. If there is only one pdf document (one instance of evince), then it doesn't happen.

---

### Post by george83 on 2013-04-05
I have the same problems (EVGA GeForce GTX 460 1GB FPB) driver 313.30

---

### Post by monkeybrain2012 on 2013-04-06
I found out that if you disable "animation" from ccsm then this bug does not manifest, but as a result maximize, minimize, open and close windows appear abrupt. Those who are affected please add a "affect me too" at [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1162954](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1162954)

---

### Post by monkeybrain2012 on 2013-04-11
Bump!

---

### Post by somates on 2013-06-05
My experience is slightly different. I cannot get rid of this glitch under any circumstances, apart from installing the 173 nvidia drivers, which introduces so many other problems that it is not worth it. This was a well known nvidia driver bug (nvidia black window memory problem) back in the day, which the 173 was known to fix. But it seems nvidia then introduced the problem back in with later drivers. 

To recreate the problem, I can do the following (note I am on a dual head setup): keep opening windows. Lots of them, and big ones or busy ones. Eventually after say 20 windows, but may be more or less dependent on your resolution or your card, the whole screen will momentarily flash black. You have just hit memory limit. Now if you keep opening a few windows, and try swapping between them a bit, then some windows will end up with no content and be black (or white, depending on version etc.) windows. Note that each window change (e.g. opening a window) results in a brief screen flash. The screen flash is the indicator that you have a problem. The problem of the black screen manifests occasionally.

If you want you can find out when the exact memory limit is hit: once the screen flashes when you open a new window, reduce the size of some window a bit. You will find a window size where it will stop flashing if it is smaller and flash if it is bigger.

This occurs more in Unity than in gnome 3, but does occur in both. Turning the various compiz 3d settings consume more memory and so make the   problem more likely. But turning them off doesn't remove the problem. Just means you have to open more windows to get it.

As I work on a 3200x1200 desktop with usually 30 or more windows open, I encounter this problem all the time.

---

### Post by VinDSL on 2013-06-05
> **monkeybrain2012 said:**
> Does no one experiencing this problem any more or everyone has stopped buying Nvidia? :)
I recently "stopped buying Nvidia", because I couldn't find a version (or a patch) that allows me to operate my legacy nVidia card under Linux 3.10

I installed xedgers Nouveau and for the life_of_me, I haven't noticed any adverse affects.

Nouveau does cause my GPU to run about 10C hotter than nVidia drivers, but it hasn't caused a problem.

When/if they patch nVidia 304.x for Linux 3.10, I'll try it again, but I'm in no hurry...  ;)

---

### Post by monkeybrain2012 on 2013-06-06
> **VinDSL said:**
> I recently "stopped buying Nvidia", because I couldn't find a version (or a patch) that allows me to operate my legacy nVidia card under Linux 3.10

I installed xedgers Nouveau and for the life_of_me, I haven't noticed any adverse affects.

Nouveau does cause my GPU to run about 10C hotter than nVidia drivers, but it hasn't caused a problem.

When/if they patch nVidia 304.x for Linux 3.10, I'll try it again, but I'm in no hurry...  ;)

I know, nouveau is actually very good these days. I am using it in 12.04 and updated with oibaf's ppa (kind of like xorg-edgers but driver only) It is very smooth and fast and get OpenGL 3.  As long as you don't need GPU acceleration I find nouveau actually smoother than the Nvidia blob. 

Use Nvidia 319.23 (xorg-edgers) with the Compiz experimental ppa in 13.04. Very fast and smooth and cpu usage is very low. Only issue is the this black window bug. For any one who may still care here is the situation with my 13.04 setup right now:

I) If all windows are non minimized, then no black window switching either with alt-tab or the shift switcher.

2) if some windows are minimized but there is only one isntance for such applications (e.g no two instances of evince for two pdf documents), then no black windows switching with alt-tab 

3) if the minized windows (may have more than one instances of the same applications) restore to non maximized windows than no black windows using the alt-tab switcher.

4) Always get black windows with shift switcher if some applications are minimized (regardless of how many instances are in use)

5) Get black windows with alt-tab for applications with more than one instances in use  and minimized AND only for those instances that restore to maximized windows.

6) One way to avoid ALL black windows would be to enable the scale addon in ccsm and use a hot corner to pick windows (i.e using Unity like Gnome Shell) There is no black window under any scenario.

Sorry this has nothing to do with saucy, but hopefully it will help for someone testing their Nvidia cards.

---

### Post by P-I H on 2013-06-06
Nvidia 319.23 is available with Additional Drivers in Saucy. Installed it yesterday.

If I open 4 terminal windows and minimize all, I get this behaviour when I click the application in the Launcher
- At the 1:st click 1 terminal is shown opened on the screen
- At the 2:nd click, all 4 is shown and I can click on the one I want to use
When I close one window and click the application in the Launcher again I get a black window
When I close that window the other 3 behaves OK.
When I close 1 of the three and click the application in the Launcher I get a black window.
When I change focus to another window, the black window goes OK.

---

### Post by PJSingh5000 on 2013-08-13
I am having this problem using an Asus GeForce GTX 670 Direct CU Mini graphics card.
I just reinstalled Ubuntu 13.04 x64 with all of the updates, because I thought that would take care of this problem.

As soon as I selected the nvidia-313-updates proprietary driver and rebooted, the problem reappeared.

The Nvidia proprietary driver gives me 4 deg. lower temps but has this EXTREEMLY annoying bug.
I'll switch back to the nouveau driver, for now. :(

---

### Post by cariboo on 2013-08-14
Nvidia-319.32, is the latest driver in the repositories, have you tried that? Mind you, I'm using a 2 -3 year old GeForce 210 here, and everything works as it should.

---

### Post by monkeybrain20122 on 2013-08-14
> **cariboo907 said:**
> Nvidia-319.32, is the latest driver in the repositories, have you tried that? Mind you, I'm using a 2 -3 year old GeForce 210 here, and everything works as it should.

Are you talking about raring or saucy? I have tried all the drivers available in raring and it is as I described in the bug report (see post #27)

I am now on the latest version of Nvidia driver (325.15) and nothing has changed.

---

### Post by cariboo on 2013-08-14
This is the Saucy sub-forum, and I'm using the drivers available in the repositories, without the edgers ppa enabled.

---

