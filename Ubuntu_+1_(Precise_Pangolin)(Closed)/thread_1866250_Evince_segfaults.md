---
title: "Evince segfaults"
date: 2011-10-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2011-10-21
Am I the only one having trouble with Evince today?
OK, I've switched to epdfview for the time being, no great problem, but...

---

### Post by portis on 2011-10-21
> **zika said:**
> Am I the only one having trouble with Evince today?
OK, I've switched to epdfview for the time being, no great problem, but...

Same problem here. Seems to be utouch problem.

evince[29773]: segfault at 29 ip 00007f0f86027398 sp 00007fffeff0bdc0 error 4 in libutouch-geis.so.1.2.0[7f0f86020000+20000]

---

### Post by zika on 2011-10-21
> **portis said:**
> Same problem here. Seems to be utouch problem.

evince[29773]: segfault at 29 ip 00007f0f86027398 sp 00007fffeff0bdc0 error 4 in libutouch-geis.so.1.2.0[7f0f86020000+20000]
```
evince[15792]: segfault at 8001 ip 00007fdaff4ce3b5 sp 00007fff1c127aa0 error 4 in libutouch-geis.so.1.2.0[7fdaff4c6000+20000]
```

Bug reported: [https://bugs.launchpad.net/ubuntu/+source/evince/+bug/879348](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/879348)

---

### Post by Harry33 on 2011-10-21
> **zika said:**
> ```
evince[15792]: segfault at 8001 ip 00007fdaff4ce3b5 sp 00007fff1c127aa0 error 4 in libutouch-geis.so.1.2.0[7fdaff4c6000+20000]
```

Bug reported: [https://bugs.launchpad.net/ubuntu/+source/evince/+bug/879348](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/879348)

Do you have these newest updates installed (today)?
- libgrip (0.3.3-0ubuntu1)
- libutouch-geis (2.2.0-0ubuntu1)

If so, try to downgrade one of them and see what happens.
Evince depends on libgrip, which depends on libutouch-geis.

---

### Post by zika on 2011-10-21
> **Harry33 said:**
> Do you have these newest updates installed (today)?
- libgrip (0.3.3-0ubuntu1)
- libutouch-geis (2.2.0-0ubuntu1)

If so, try to downgrade one of them and see what happens.
Evince depends on libgrip, which depends on libutouch-geis.Yes, these are the versions I have at this moment...
I planned to do that, even had .deb files ready but no time at this moment. Maybe later in the afternoon. Epdfview works fine for now...

---

### Post by Harry33 on 2011-10-21
OK, I will test that later today also.

---

### Post by Harry33 on 2011-10-21
Right, I did some testing.
The problem is not Evince nor the package libgrip0.
The bug is in the package libutouch-geis1_2.2.0-0ubuntu1.
Workaround:
Downgrade to the earlier version 2.1.2-0ubuntu4.

---

### Post by zika on 2011-10-21
This little bug was a blessing in disguise for me. I'm glad I've tried Epdfview... ;)

---

### Post by Harry33 on 2011-10-21
> **zika said:**
> This little bug was a blessing in disguise for me. I'm glad I've tried Epdfview... ;)

Yes Epdfview is lightweight without gnome libraries, but it is a GTK+2 application.

---

### Post by zika on 2011-10-21
> **Harry33 said:**
> Yes Epdfview is lightweight without gnome libraries, but it is a GTK+2 application.There ain't no such thing as a free lunch.

---

### Post by Harry33 on 2011-10-22
There is a new update to the packgage libutouch-geis1 (2.2.1-0ubuntu1) available in Precise repos.
However, it is of no use for Evince. It does not fix this segfaulting.
So, do not update. The only working version is 2.1.2-0ubuntu4.

---

### Post by Harry33 on 2011-10-22
The bug ( #879348 ) is marked as fixed, but is certainly is not.

[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/879348](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/879348)

---

### Post by zika on 2011-10-22
> **Harry33 said:**
> The bug ( #879348 ) is marked as fixed, but is certainly is not.

[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/879348](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/879348)It works here, as it was prior to the bug...

---

### Post by ranch hand on 2011-10-22
I will try it again in the morning.

I filed a bug and marked as a duplicate of yours when I found this thread.

---

### Post by portis on 2011-10-22
> **Harry33 said:**
> The bug ( #879348 ) is marked as fixed, but is certainly is not.

[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/879348](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/879348)

The fix works for me.

---

### Post by Harry33 on 2011-10-22
Does not work here. Evince does not start with this update installed and the whole system freezes when I try to reboot.

---

### Post by Harry33 on 2011-10-22
See the bug report ( #879348 )
[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/879348](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/879348)

Just like Rico Tzschichholz wrote, the bug is still there.
I am using xserver 1.11.1.901 and nvidia-current 290.03.

---

### Post by Harry33 on 2011-10-23
This bug has been reopened now.

---

### Post by VinDSL on 2011-10-23
> **Harry33 said:**
> This bug has been reopened now.
Glad you bumped this thread!  

I'm logged into GS right now.  Hold on...

Yep!  Evince is working fine, here.  Dittos for Unity, BTW.

[LIST]
[*]Linux 3.0.0-12 generic kernel (i686)
[*]nVidia 280.13
[*]GS official repo install
[/LIST]

Just saying...  ;)

---

### Post by ranch hand on 2011-10-24
Seems to work in my Xubuntu too today.  Much better.

---

### Post by Harry33 on 2011-10-24
> **VinDSL said:**
> Glad you bumped this thread!  

I'm logged into GS right now.  Hold on...

Yep!  Evince is working fine, here.  Dittos for Unity, BTW.

[LIST]
[*]Linux 3.0.0-12 generic kernel (i686)
[*]nVidia 280.13
[*]GS official repo install
[/LIST]

Just saying...  ;)

[QUOTE=ranch hand]
Seems to work in my Xubuntu too today. Much better.
[/QUOTE]

This bug may only affect setups with xserver 1.11 series. For example from Xorg-edgers.

---

### Post by VinDSL on 2011-10-24
> **Harry33 said:**
> This bug may only affect setups with xserver 1.11 series. For example from Xorg-edgers.
Huh?  Oh, okay...

I had this segfault problem on 21 October 2011, 3:06:55 AM  LoL!  :D

I confused this thread with one I replied to on Open Linux Forums.

This was part of my reply:

```
vindsl@Zuul:~$ evince
Segmentation fault
vindsl@Zuul:~$ 
```

Next day I checked, and Evince was working fine - and it's worked ever since.

Sorry, for the confusion, but it *was* affecting me initially.

Looks like the patch worked for some of us, but not others.  ;)

---

### Post by Harry33 on 2011-10-24
> **VinDSL said:**
> Huh?  Oh, okay...

I had this segfault problem on 21 October 2011, 3:06:55 AM  LoL!  :D

I confused this thread with one I replied to on Open Linux Forums.

This was part of my reply:

```
vindsl@Zuul:~$ evince
Segmentation fault
vindsl@Zuul:~$ 
```

Next day I checked, and Evince was working fine - and it's worked ever since.

Sorry, for the confusion, but it *was* affecting me initially.

Looks like the patch worked for some of us, but not others.  ;)

It seems the patch that has been applied to the latest version there is (libutouch-geis_2.2.1-0ubuntu1) works for xserver 1.10 series, but not for xserver 1.11 series.

---

### Post by zika on 2011-10-24
> **Harry33 said:**
> It seems the patch that has been applied to the latest version there is (libutouch-geis_2.2.1-0ubuntu1) works for xserver 1.10 series, but not for xserver 1.11 series.
I'm fully updated/upgraded (including xorg-edgers, only (mostly empty (cairo and pixman) PP branch) and I do not have 1.11 xserver... It is only in OO branch. So, You are mixing branches... aren't You?
Patch works fine here...

---

### Post by Harry33 on 2011-10-24
> **zika said:**
> I'm fully updated/upgraded (including xorg-edgers, only (mostly empty (cairo and pixman) PP branch) and I do not have 1.11 xserver... It is only in OO branch. So, You are mixing branches... aren't You?
Patch works fine here...

Well I am not exactly mixing branches, because I had xserver 1.11.1 installed in OO.
And it staid that way now that I have upgraded to PP.
PP is very still much OO these days.

---

### Post by fiazseo on 2011-10-25
Right, I did some screening.
The issue is not Evince nor the program libgrip0.
The bug is in the program libutouch-geis1_2.2.0-0ubuntu1.
Workaround:
Downgrade to the previously edition 2.1.2-0ubuntu4.

---

### Post by zika on 2011-10-25
> **fiazseo said:**
> Right, I did some screening.
The issue is not Evince nor the program libgrip0.
The bug is in the program libutouch-geis1_2.2.0-0ubuntu1.
Workaround:
Downgrade to the previously edition 2.1.2-0ubuntu4.Copy and paste from [http://ubuntuforums.org/showpost.php?p=11375385&postcount=7](http://ubuntuforums.org/showpost.php?p=11375385&postcount=7) ...?

---

### Post by zika on 2011-10-25
> **Harry33 said:**
> Well I am not exactly mixing branches, because I had xserver 1.11.1 installed in OO.
And it staid that way now that I have upgraded to PP.
PP is very still much OO these days.I did not have xorg-edgers turned on in my last days on OO... ;)
I've done what is recommended: turned off xorg-edgers and ppa-purged before upgrade to PP...
So, it might be a conclusion: now we might say that using Xorg-Edgers from OO banch is a culprit, not a PP package...?
When we will see rise of full XE PP branch?

---

### Post by Harry33 on 2011-10-25
> **zika said:**
> 
...
When we will see rise of full XE PP branch?

Well it may very well be that xserver 1.11.x will not be in the Xorg-edgers (precise) PPA, because that very xserver is going to be the official Precise Pangolin xserver.
Perhaps we will one day see xserver 1.12 in XE PP branch.

---

### Post by zika on 2011-10-25
> **Harry33 said:**
> Well it may very well be that xserver 1.11.x will not be in the Xorg-edgers (precise) PPA, because that very xserver is going to be the official Precise Pangolin xserver.
Perhaps we will one day see xserver 1.12 in XE PP branch.[IMG]http://www.emotihost.com/thumbs/2.gif[/IMG]

---

### Post by Harry33 on 2011-10-25
Now, after all, this issue may already be fixed with the utouch-geis_2.2.1-0ubuntu1.
And that xserver 1.10.x is OK with it.
It appears that xserver 1.11.1 does not yet have the multitouch support and this may cause the problems with the new Eog and Evince, which offer that property.

---

### Post by paul_in_london on 2011-12-05
**evince**, **evince-common** and **libevince3-3** have just been upgraded from the main PP repos. Last time I tried running it from the terminal it segfaulted. Now it just hangs without producing any output. I'd already resorted to **epdfViewer** as an alternative in the meantime.

---

### Post by Harry33 on 2011-12-06
> **paul_in_london said:**
> **evince**, **evince-common** and **libevince3-3** have just been upgraded from the main PP repos. Last time I tried running it from the terminal it segfaulted. Now it just hangs without producing any output. I'd already resorted to **epdfViewer** as an alternative in the meantime.

Did you try to downgrade the package libutouch-geis1 to the earlier version 2.1.2-0ubuntu4?

---

### Post by paul_in_london on 2011-12-06
> **Harry33 said:**
> Did you try to downgrade the package libutouch-geis1 to the earlier version 2.1.2-0ubuntu4?

Hi Harry,

No - I know this was mentioned before and thanks for reminding me, but I haven't actually tried that. The version of **libutouch-geis1** that I currently have installed is **2.2.1-0ubuntu1**. I just made a point of trying evince again yesterday when it was updated. Slightly offf-topic, but I did revert to a stable version of Flash because 11.2 Beta 2 was crashing so much and I kept having to restore my FF profile from a backup!

---

### Post by zika on 2011-12-23
What is the current state of Xorg-Edgers with respect to Evince...?
Multitouch not in Xorg from XE, yet?

---

### Post by Harry33 on 2011-12-23
> **zika said:**
> What is the current state of Xorg-Edgers with respect to Evince...?
Multitouch not in Xorg from XE, yet?

The current state is that xserver 1.11.x does not have multitouch property, so it does not work.
Xorg-edgers PPA does contain the xserver 1.11.2 ATM.

Evince works OK, though, but you have to pin the version 2.1.2-0ubuntu4 (libutouch-geis).
By doing so edgers PPA works very well.

If you want to try the new pre-version of xserver 1.12, you will get it from Ricotz Unstable PPA.
There you will find the xserver 1.11.99.2.

---

### Post by zika on 2011-12-23
> **Harry33 said:**
> The current state is that xserver 1.11.x does not have multitouch property, so it does not work.
Xorg-edgers PPA does contain the xserver 1.11.2 ATM.

Evince works OK, though, but you have to pin the version 2.1.2-0ubuntu4 (libutouch-geis).
By doing so edgers PPA works very well.

If you want to try the new pre-version of xserver 1.12, you will get it from Ricotz Unstable PPA.
There you will find the xserver 1.11.99.2.
Yes, I know about the version 2.1.2-0ubuntu4... We've been talking about that at the very beginning of this thread.
What about xserver from Ricotz Unstable PPA, does it work with Evince, without pinning the version 2.1.2-0ubuntu4...?

One more question: how &#8222;unstable&#8220; it is? As You might know, I've used it at the beginning of this thread...

(Or, was it a thread: [http://ubuntuforums.org/showthread.php?p=11488688](http://ubuntuforums.org/showthread.php?p=11488688) ...? )

---

### Post by Harry33 on 2011-12-23
> **zika said:**
> Yes, I know about the version 2.1.2-0ubuntu4... We've been talking about that at the very beginning of this thread.
What about xserver from Ricotz Unstable PPA, does it work with Evince, without pinning the version 2.1.2-0ubuntu4...?

One more question: how &#8222;unstable&#8220; it is? As You might know, I've used it at the beginning of this thread...

(Or, was it a thread: [http://ubuntuforums.org/showthread.php?p=11488688](http://ubuntuforums.org/showthread.php?p=11488688) ...? )

Well, I haven't tested the Unstable PPA.
All I can see is that it gets updated quite often. Today again.
However, that pre-xserver 1.12 is not actually what it will be. If you install it now and use proprietary drivers (NVidia), I think there will a breakage at some point.
But if you use open source graphics drivers, it may work, more or less.

I do not see why Evince would not work. Multitouch issues are related to xserver 1.11.

The merge window for development of xserver 1.12 has not been fully closed yet, there may be some changes to come.
The multitouch code (X input 2.2) is in, but for example X RandR 1.4 is still out (likely staying out too).

---

### Post by zika on 2011-12-24
> **Harry33 said:**
> Well, I haven't tested the Unstable PPA.
All I can see is that it gets updated quite often. Today again.
However, that pre-xserver 1.12 is not actually what it will be. If you install it now and use proprietary drivers (NVidia), I think there will a breakage at some point.
But if you use open source graphics drivers, it may work, more or less.

I do not see why Evince would not work. Multitouch issues are related to xserver 1.11.

The merge window for development of xserver 1.12 has not been fully closed yet, there may be some changes to come.
The multitouch code (X input 2.2) is in, but for example X RandR 1.4 is still out (likely staying out too).Now that I jumped out of that train, several weeks ago, to get me on again, a question:
what benefit should I expect from getting this 1.12 xserver?

---

### Post by Harry33 on 2011-12-24
> **zika said:**
> Now that I jumped out of that train, several weeks ago, to get me on again, a question:
what benefit should I expect from getting this 1.12 xserver?

I do not think anything visual nor impressing at this time yet.

---

### Post by zika on 2011-12-24
> **Harry33 said:**
> I do not think anything visual nor impressing at this time yet.In Holyday's spirit, I've jumped on to the train again. And, it works... ;)

---

### Post by Harry33 on 2011-12-24
> **zika said:**
> In Holyday's spirit, I've jumped on to the train again. And, it works... ;)
OK, that is nice to know.
One of these days I'll do the same thing.

---

