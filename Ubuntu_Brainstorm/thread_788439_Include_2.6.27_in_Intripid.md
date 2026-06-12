---
title: "Include 2.6.27 in Intripid"
date: 2008-05-09
forum: Ubuntu Brainstorm
---

### Post by smartboyathome on 2008-05-09
I think that Intripid should strive to include 2.6.27 in its release. It is generally more of a testing release than polishing (see: edgy), and this will be the first kernel with an important feature: modesetting. This would allow great enhancements to happen, for example Splashy to become a viable alternative.

---

### Post by Redrazor39 on 2008-05-10
agreed. +1 for you.

We should work on making it very stable so it doesn't have problems like .24 in hardy.

---

### Post by brandon30x on 2008-05-10
The thing about the kernel mode setting stuff though is that it also requires changes to X.org and the video drivers. Open source video drivers such as intel and radeon ([[COLOR="Blue"]and in the future, nouveau]("http://nouveau.freedesktop.org/wiki/ToDo")[/COLOR]) are already working on it. But I don't know about the closed source drivers that many people like me rely on. They may take longer to include changes.

I have been searching for information on this on kernel and X.org mailing lists, and the information is sparse. The slashdot article is the only source citing that the patches will be included in 2.6.27.

I am very interested in things like this which only improve the user experience. On the previously mentioned mailing lists I read, there is usually a strong backlash against putting video stuff in the kernel (too much like windows, etc..) and against having a "BSOD". However only the mode setting functionality is being added, not the whole video driver like windows. Additionally I welcome BSOD like functionality. I have had X crash on me too many times where I have no other option but a hard power off. On another box running gentoo, I was dismayed to find out that the kernel debugging of suspend involves saving a cryptic time to the system clock (which never worked for me anyways). The clock was the only way the information could survive a reboot. The kernel could not write the error to the screen. Hopefully the BSOD could fix that and make suspend debugging easier.

---

### Post by macaholic on 2008-05-10
I think that intrepid should, like smartboy said, strive to include the newer kernel, but during the development cycle, there should probably be testing on the latest 2.6.26 kernel aswell, since the bugs might not be able to be worked out in time for the release.

---

### Post by danbh on 2008-05-10
Has 2.6.27 even been released yet?   Im pretty sure that Intrepid will have 2.6.25, since that is what is currently released.  If you REALLY want the later and greater software, then you might want to try debian experimental?  I dunno.

---

### Post by smartboyathome on 2008-05-10
> **danbh said:**
> Has 2.6.27 even been released yet?   Im pretty sure that Intrepid will have 2.6.25, since that is what is currently released.  If you REALLY want the later and greater software, then you might want to try debian experimental?  I dunno.

It should be released before Intripid, but it will probably use 2.6.26.

---

### Post by quickshade on 2008-05-10
9.04 will have to use it. Freeze time will be in effect before 2.6.27 will be released (not 100% sure but from what I've seen). This may work better, as 6 months for developers to tweak the settings a video cards to fix the drivers will provide a more stable switch over. Currently some hardware doesn't take kindly to the settings, so time to sort that out would also be great.

I do agree though, Once this gets released and developers use it I think it will be great.

---

### Post by FrancoNero on 2008-07-29
I just read rc1 is out. I read it has lots of new things regarding ACPI suspendtoram/disk stuff in there, to me that's great news. I would really hope this kernel version will be the foundation for intrepid, especially with all the driver updates and stuff regarding networking etc, as well...

it's not an LTS so be on the edge!

---

### Post by smartboyathome on 2008-07-29
> **FrancoNero said:**
> I just read rc1 is out. I read it has lots of new things regarding ACPI suspendtoram/disk stuff in there, to me that's great news. I would really hope this kernel version will be the foundation for intrepid, especially with all the driver updates and stuff regarding networking etc, as well...

it's not an LTS so be on the edge!

Like Edgy? No, please! Make this optional? Yes! Also, since the ATI drivers are open source, then they would probably get this quickly after Intel. That leasves the demon that is Nvidia. :mad:

---

### Post by songshu on 2008-07-29
i think they should include openoffice.org 4.3 and thunderbird 3.5 as well....

come on...2.6.27 is not even released yet, and how important is splashy??? it will take some time before they will abandon usplash anyway.

sid is 2.6.25 at the moment so that will be likely to be included.

---

### Post by smartboyathome on 2008-07-29
> **songshu said:**
> i think they should include openoffice.org 4.3 and thunderbird 3.5 as well....

come on...2.6.27 is not even released yet, and how important is splashy??? it will take some time before they will abandon usplash anyway.

sid is 2.6.25 at the moment so that will be likely to be included.

It was slated to be released before Intrepid was, and this is older, but I digress. Intrepid will actually probably use 2.6.26, as it is definately going to be released before Intrepid is (I think it will be released soon).

---

### Post by songshu on 2008-07-29
> **smartboyathome said:**
> It was slated to be released before Intrepid was, and this is older, but I digress. Intrepid will actually probably use 2.6.26, as it is definately going to be released before Intrepid is (I think it will be released soon).

I'm not sure what the policy of the ubuntu kernel team is, do they follow debian unstable ??

---

### Post by Sciophobia on 2008-07-31
> **smartboyathome said:**
> It was slated to be released before Intrepid was, and this is older, but I digress. Intrepid will actually probably use 2.6.26, as it is definately going to be released before Intrepid is (I think it will be released soon).

Just a note:

[QUOTE=kernel.org]
The latest stable version of the Linux kernel is:  2.6.26 2008-07-13 22:44 UTC [...]
The latest prepatch for the stable Linux kernel tree is:  2.6.27-rc1 2008-07-29 03:12 UTC [...]
[/QUOTE]

2.6.26 has been out for a while and 2.6.27 is in RC status.

---

### Post by smartboyathome on 2008-07-31
Since 2.6.27 is in RC status, that is good news. If the 2.6.27 kernel gets released before August 28th (feature freeze for Intrepid), then it might be able to be included.

---

### Post by Slug71 on 2008-08-02
2.6.26 was released on July 13 2008 and 2.6.27 RC-1 was released July 28 2008. Hope Ubuntu makes the kernel update to 2.6.27 possible via the update manager if it is gonna be too late for Intrepid.

---

### Post by Slug71 on 2008-08-06
2.6.27-RC2 is out today!

---

### Post by AdamWood on 2008-08-06
> If the 2.6.27 kernel gets released before August 28th (feature freeze for Intrepid), then it might be able to be included

Crazy talk! That might actually give people time to test it! ;)

---

### Post by Slug71 on 2008-08-15
RC-3 is now out. Hopefully this will be able to be included.

---

### Post by b3n87 on 2008-08-23
I read on one of the mailists that they are thinking of including the newer kernel version which is excellent news

---

### Post by smartboyathome on 2008-08-23
> **b3n87 said:**
> I read on one of the mailists that they are thinking of including the newer kernel version which is excellent news

If that is so, and indeed modesetting is included, then that will be great! Those who have it supported can test it. :D

---

### Post by syko21 on 2008-08-23
[https://lists.ubuntu.com/archives/ubuntu-devel/2008-August/026142.html](https://lists.ubuntu.com/archives/ubuntu-devel/2008-August/026142.html)

We should have news by early next week then.

---

### Post by BCurtisWX on 2008-08-23
Launchpad has the builds for the 2.6.27 kernel up and already an hour into the build.  Maybe see them tonight?

---

### Post by syko21 on 2008-08-23
Hope that includes restricted and l-u-m, I tried rolling my own kernel and a lot of hardware didn't work properly because I didnt have those two.

---

