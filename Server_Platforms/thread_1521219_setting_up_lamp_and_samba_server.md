---
title: "setting up lamp and samba server"
date: 2010-06-30
forum: Server Platforms
---

### Post by mistafeesh on 2010-06-30
Hi,

It's time for me to ask for help, because I'm getting nowhere by myself! I've been trying to set up an old 1ghz PC as a SMB file and php/mysql web server, which I thought was fairly simple! I currently run a similar setup on my mac, but it's 7 years old and I use it for other stuff too, so it was all getting too slow... Also, I wanted a working version of imagemagick(etc) and sendmail.

I downloaded the server 32bit installer CD and ran it. Unfortunately the first time I tried it, my CD was defective, but the second time the installation seemed to go OK apart from it had a problem setting up DCHP with my RAlink USB wifi adapter, which is [a known issue]("http://ubuntuforums.org/showpost.php?p=1310334") and I planned to fix it later. However, after what appeared to have been a successful install, I booted up and just got a flashing line at the bottom of the bios screen. I looked around and came across another similar case where someone had found that grub is not set up properly if it was already on the hard drive (now can't find the link), as it was from my first broken install (I think!) SO I boot into a liveCD, format the hard drive and try again. Now I just get a blank black screen!

I'm going to try installing standard ubuntu from the liveCD I downloaded to see if that works, but I wouldn't mind a bit of advice about what's going on!

---

### Post by arrrghhh on 2010-06-30
You may also try the alternate installer, but for what it's worth the server edition uses that as it's default installer - I believe they're the same.

Normally I would recommend you try that alternate CD, but perhaps that won't work.

Did you run a LiveCD to make sure all your hardware was compatible with Ubuntu?

---

### Post by mistafeesh on 2010-07-03
The live CD seems to sometimes work and sometimes not, which makes me concerned that there may be something odd going on with my system. Just now it booted fine, and it's installing as I type. 

My intention is to run it headless for most of the time... If this install is successful, then presumably I can install the server software and set it up to run without X unless I start it?

---

### Post by DJYoshaBYD on 2010-07-04
i think you are going to have more headache then its worth..

a newer, up to date motherboard would probably help.. same hardware, but the newer motherboard would also have a newer chipset that would probably have better support..

this is just a suggestion.. dont go out and buy anything till you research.. hahaha

but to me, i think that is the issue.. run an LTS version on a newer mobo, and you will probably be cool.. check the forums to see what is compatible for your price range.. 

again.. reeesssseeeaaaarrrccchhh before buy :D

---

### Post by mistafeesh on 2010-07-04
Hi,

I'd rather keep the mobo I've got if it's at all possible. Electronic waste and all that!
 I'm going to download UBCD and run some hardware tests - EDIT - I'm running the hardware test on the ubuntu CD.  I'll get a new bios batt too if everything else checks out OK. I think it's powerful enough to do what I need - once it's set up I don't need to run x windows, just apache, mysql and samba, with some remote admin software or other.

---

### Post by DJYoshaBYD on 2010-07-04
its not just having new stuff.. its having hardware that is compatible with the kernel :)

---

### Post by mistafeesh on 2010-07-04
OK. Would I be better off installing an older version of ubuntu (or, shudder,  another incarnation of linux) in that case?

It might be academic now as I found some problems with the PCI bus in PCIsniffer, which I've asked about on a hardware forum. Sounds like my mobo could be dying.... done a cmos wipe just in case, but still persists...

the liveCD now boots and runs fine, if slowly (which is to be expected on old hardware and running from CD) so presumably it's compatible with the kernel?

edit - Successfully installed ubuntu from the liveCD now, on the nth attempt! Will make a start on getting wifi working and then installing the stuff I want if/when I know mobo is OK....

---

