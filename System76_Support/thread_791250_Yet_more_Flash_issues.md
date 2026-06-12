---
title: "Yet more Flash issues"
date: 2008-05-12
forum: System76 Support
---

### Post by ctsdownloads on 2008-05-12
I think I must have been stupid enough to trust a 8.04 update from the recommended update repo recently because my flash support is quickly going backwards...

First [ustream.tv gives me errors]("http://ubuntuforums.org/showthread.php?t=776311") (only on 64bit Ubuntu mind you, my 32 bit notebook works fine with 8.04) and now Youtube and MySpace have a brand new error to frustrate me. :mad:

Both sites, YT and Myspace video will start a video, then reset it as if I have hit stop. I have *never* had this problem before and what is even stranger is the fact that I can view Flash ads, with sounds, seeing no issues at all.

With all seriousness, why is this still an issue with 64 bit Ubuntu? Honestly, is this just a regression or a sign of a bigger issue with nspluginwrapper?? ](*,)

Please understand, I have added, removed and reinstalled everything that has to do with Flash until the world looked level.

I have tested this with Firefox 2 and 3-beta with 8.04 64bit - really getting tired of 64bit Linux headaches here...

---

### Post by ctsdownloads on 2008-05-12
Update: Further tested Flash audio players with both with MySpace music players and pandora.com.

MySpace music plays fine, Pandora does EXACTLY the same start then stop thing as YouTube! This is freaking driving me nuts as it is impossible to diagnose.

My status bar clearly showing me that the page does stop loading when the music stops, so it may be a networking issue that relates to Flash at some level.

Seriously, I cannot believe for a second that I am the only one having this issue??

To be fair, I have only checked this out on multiple WPA and un-protected wifi networks. Will be removing the UFW and testing this on a LAN later. I am so ready to move back to 7.10 I could cry. And what is so maddening is that my only issue is indeed, with Flash...might just go 32bit as that is working fine.

---

### Post by ctsdownloads on 2008-05-12
n/m

---

### Post by ctsdownloads on 2008-05-12
Well, here is the latest: reverted both nspluginwrapper and flash-nonfree to previous versions - error remains. Next up, going to try reverting network manager...:(

---

### Post by ctsdownloads on 2008-05-12
Whoa, this is wild. I was alerted to a System76 update for their driver. I updated, then I rebooted. Then I reinstalled the System76 driver from Administration, system76 driver - reboot again....wait for it...I then reinstalled the Flash modules and boom - everything works again!

Not only is Youtube playing correctly again, so is Ustream.tv! You guys are amazing, I almost fell back into 32 bit...I was literally minutes away from switching back to 32 bit 8.04.

Whatever changes were made to the System76 driver apparently have solved the issue.

I will tell you this - I will be doing an "aptitude hold" on a series of packages from flashplugin-nonfree to nspluginwrapper. That will prevent any future surprises from my updates.

Thanks for being patient with my little break down. Flash is just too much a part of the web to be without, so I am thrilled I can still use 64 bit Ubuntu. :guitar:

---

