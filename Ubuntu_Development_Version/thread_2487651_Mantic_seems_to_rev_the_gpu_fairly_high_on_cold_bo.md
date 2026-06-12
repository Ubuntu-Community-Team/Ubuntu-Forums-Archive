---
title: "Mantic seems to rev the gpu fairly high on cold boot in '12 MacPro"
date: 2023-06-11
forum: Ubuntu Development Version
---

### Post by este.el.paz on 2023-06-11
The issue of Mantic seeming to "load" the gpu quite a bit on cold boot has recurred several times since moving to Mantic.  It seems to run it at higher "revs" for 4 or 5 mins before dropping itself down to "normal" speeds . . . this is before even launching FF . . . i.e., not asking the system to do anything except boot itself up, etc.

This was not an issue in the previous iteration of Lubuntu, but seems to be a "Mantic" thing??  The gpu is an upgraded Nvidia 780 I believe . . . running nouveau.

---

### Post by este.el.paz on 2023-08-27
> **este.el.paz said:**
> The issue of Mantic seeming to "load" the gpu quite a bit on cold boot has recurred several times since moving to Mantic.  It seems to run it at higher "revs" for 4 or 5 mins before dropping itself down to "normal" speeds . . . this is before even launching FF . . . i.e., not asking the system to do anything except boot itself up, etc.

This was not an issue in the previous iteration of Lubuntu, but seems to be a "Mantic" thing??  The gpu is an upgraded Nvidia 780 I believe . . . running nouveau.

et al:

Yes, this issue of the gpu spinning up to higher revs just to get itself going . . . this morning about 4 mins and now settled down to "normal" gpu speeds . . . continues.

---

### Post by guiverc on 2023-08-27
My suspicion is the issue maybe related to the kernel, I forget when *mantic* switched to 6.3, but I wonder if it's then.

(*lunar *used 6.2, as did *mantic* very early in the cycle).

I'll suggest grabbing a Ubuntu Desktop 23.04 *system* and write to thumb-drive, boot it and explore it there.  My suspicion is you won't have any problem there, but its giving you a *comparison* point.. so explore it awhile until you'd expect a problem & note what you do.  I'd then boot a Ubuntu Desktop *mantic* (23.10) system (ie. the current Ubuntu Desktop *daily*) and re-do what you did on 23.04 and see if it's the same there?  Are you experiencing what you are with Lubuntu *mantic* installed?  If you are, I'd file a bug report using the Ubuntu Desktop *daily*, record it on the [iso tracker]("http://iso.qa.ubuntu.com/") and outline it also occurs on your installed Lubuntu system.

You could do this with just Lubuntu installed system, but I suspect it'll carry more weight on Ubuntu Desktop, esp. given the research you can outline with what I've mentioned (*if what I'm suggesting makes sense*).  Lubuntu is a *generic* Ubuntu system, without any additional drivers.

This won't relate to where you are, but I've got one box I use in QA that really doesn't like Lubuntu *mantic*, and I've not worked out why yet. It's painfully slow, but I believe it's something in 6.3 that my old core2quad, or gpu or some other hardware component doesn't handle well (*but is fine with lunar, jammy or debian trixie*). I just need the time (*and patience*) to work out what my issue is (*my last attempt was a zsync of ubuntu desktop mantic for comparison; it was written to thumb-drive, but I ran out of  the time to do the actual testing of it on that box* *before the daily was stale*).

Also, IF IT SETTLES DOWN WITH USAGE, I'd likely not worry about it that much. Ubuntu *mantic* isn't expected to ship with 6.3

---

### Post by este.el.paz on 2023-08-27
@guiverc:

Thanks for the reply and the thoughts . . . might get to reporting it on the QA . . . that does take time, filing the bug report and so forth.  But, "the kernel" . . . might explain the problem or might not.  On the same machine I have 6 other linux distros installed, many of them cariations of openSUSE tumbleweed, which might be up to 6.4 kernel??? an none of the other distros have this issue, just mantic.

Lunar also did not have the problem . . . but in regards to "old hardware" that might relate, this is '12 Mac Pro . . . with the OEM Quad-core i7 of that era . . . the GPU is aftermarket, Nvidia 780 I believe.  So, possibly the nouveau driver might be not jiving with the older. but not OEM GPU???

It does settle down after a few minutes, but that is drawing juice to do that . . . for just booting and logging into the system and launching a browser . . . it's a "new" development in mantic.  I'll monitor it for awhile.

---

### Post by este.el.paz on 2023-09-02
@guiverc:

So I took the time to download the daily Ubuntu Desktop system and flash it to usb drive . . . booting from the usb drive I would say does not produce the speeding up of the GPU the way the Lubuntu installed system seems to still be doing.

Booting the Ubuntu live system seemed to generate a crash report, so I added my name to that other Bug report that seemed to be showing the same "timeout" problem, but from back in Jammy . . . ???

I looked at the ISO Tracker site . . . but, other stuff to do right now . . . .  Seems like I'd have to flip back over to Lubuntu Mantic and file the bug report and then go through steps to make the QA . . . time-consuming stuff, etc.

For now just posting here to let you know that the daily generic Ubuntu does not replicate the speeding up of the GPU as it does in Lubuntu Mantic.

---

### Post by jbicha on 2023-09-02
Ubuntu 23.10 is expected to include Linux 6.5 currently in mantic-proposed.

---

### Post by guiverc on 2023-09-02
> **este.el.paz said:**
> 
So I took the time to download the daily Ubuntu Desktop system and flash it to usb drive . . . booting from the usb drive I would say does not produce the speeding up of the GPU the way the Lubuntu installed system seems to still be doing.

Thank you for your testing.

Since there was no issue with Ubuntu Desktop, that may mean its a difference between the ISOs **OR** it's a Lubuntu configuration issue.

Ubuntu ISOs contain more kernel module choices than Lubuntu does (with Lubuntu you need to use the *generic* drivers/modules, then post-install use `ubuntu-drivers autoinstall` to add what Ubuntu Desktop ISOs **may** install with if you select to use them).  These extra features increase the size of Ubuntu Desktop ISOs (*inclusion of Nvidia kernel modules, alternate OEM kernel stacks etc*) when contrasted with Lubuntu's. These can mean Ubuntu Desktop *live* can use different setups in *live* mode too, options Lubuntu *live* doesn't have (eg. Lubuntu can only use `nouveau` where Ubuntu Desktop may not).

---

Using the *development* system can suffer breakage on installed systems. I'm back using my *primary* system using *mantic*, as I switched to using another box as I explored issues here that had 2 of my 5 screens unusable. My system is installed, but I could replicate the issue for more than week using Lubuntu *dailies,* and if I recall correctly only a couple of days with Ubuntu Desktop & then the issue was gone from Ubuntu Desktop ISOs, and a day or so later from Lubuntu dailies too. Alas the issue on the installed system continued.. My own fix was to *non-destructively *re-install, as I didn't the actual cause/fix.

Situations where an *unusual issue* or altered config creates a problem are very rare using *development* systems, but *mantic* is still in ***alpha*** having not reached *beta*, thus it's still from *stable* and problems like this can occur.

FYI:  I've still not found the cause on my *really slow* *secondary *box for *mantic* yet either.. as Ubuntu Desktop & Lubuntu ISOs seem **not** to have an issue, it exists only on my re-installed system.. but as I have my data on that system, I'm ~weekly non-destructively re-installing that (*instead of applying normal upgrades as a QA test*) and thus if it's a user config; it'll survive. I have not yet had the issue occur elsewhere though.

> **este.el.paz said:**
> 
For now just posting here to let you know that the daily generic Ubuntu  does not replicate the speeding up of the GPU as it does in Lubuntu  Mantic.

Thanks for testing, and letting us know.

---

