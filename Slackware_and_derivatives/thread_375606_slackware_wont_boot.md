---
title: "slackware wont boot"
date: 2007-03-03
forum: Slackware and derivatives
---

### Post by thegrimgod on 2007-03-03
I am not sure where to post this , nor if it is appropriate on the ubuntu forum, but this is my problem:
i am trying to install slackware as a second os, but it won't boot. I tried the dvd , skips it , i tried the cd , skips it , just gets to grub , then i go into ubuntu. The odd thing about it is that i am very able to boot it on other computers , which makes me want to break all of them...stressed. 
Also , i want to find out what my motherboard is---dont even ask how i got this pc , no manual, and since i am new , i have no clue , i think my bios is messing up with the slackware...but i have no clue what to do , if u can pls help
btw, its not the boot priorities, they are as follows , floppy , cdrom, harddrive
ty in advance

---

### Post by K.Mandla on 2007-03-03
This is probably a dumb question, but is your BIOS set to boot from CD? And this is probably a dumber question, but did you burn the ISO to the disc as a file? (I'm not trying to criticize; these things are sometimes the case.)

By the way, I'll shift this to the Other OS forum, where it's more likely to get attention from people who have experience with Slack. ;)

---

### Post by Kateikyoushi on 2007-03-03
With those settings it should boot to slackware installer, can you boot other disc on that machine ?

---

### Post by thegrimgod on 2007-03-04
yup, i can boot fedora , ubuntu dapper , (im on edgy now), bios is set to boot from cd : this is acctual order of booting floppy, cd, hd , and the cd does not contain an iso file, it has the files in the image , ty for reply in anycase , and for redirection :)

---

### Post by MethodOne on 2007-03-04
Try this:
[http://slackware.mirrors.tds.net/pub/slackware/slackware-current/rootdisks/sbootmgr.dsk](http://slackware.mirrors.tds.net/pub/slackware/slackware-current/rootdisks/sbootmgr.dsk)

Run the following command to make the boot floppy;
```
dd if=/path/to/sbootmgr.dsk of=/dev/fd0
```If you want to make it in Windows, download RAWRITEXP.EXE from the same page to write the image to a floppy.

Boot from the floppy and select CD-ROM from the menu to start the Slackware installation.

---

### Post by RAV TUX on 2007-03-04
> **thegrimgod said:**
> I am not sure where to post this , nor if it is appropriate on the ubuntu forum, but this is my problem:
i am trying to install slackware as a second os, but it won't boot. I tried the dvd , skips it , i tried the cd , skips it , just gets to grub , then i go into ubuntu. The odd thing about it is that i am very able to boot it on other computers , which makes me want to break all of them...stressed. 
Also , i want to find out what my motherboard is---dont even ask how i got this pc , no manual, and since i am new , i have no clue , i think my bios is messing up with the slackware...but i have no clue what to do , if u can pls help
btw, its not the boot priorities, they are as follows , floppy , cdrom, harddrive
ty in advance

You are not alone Slackware has never booted for me either, I suggest you try [**Wolvix Hunter** 1.0.5]("http://wolvix.org/node/379") which is Slackware based and a dream to use.

In fact I would say that Wolvix Hunter is "one-of-the" most advanced OS's in existence.

---

### Post by kazuya on 2007-03-05
For slack-based used the latest zenwalk 4.4.1. It is not a livecd install, it is text-based, but installs and works very fast. I recommend it because, it is very bleeding edge and yet stable.. Unlike slackware and most other derivatives, they use xorg 7.1 which allows for beryl/compr. The others use xorg 6.8 and xorg 6.9. 
Use this and you may be very amazed at the sheer performance.
They have a package manager in CLI and gui form that makes upgrading your system, and getting new apps very easy.

PS: Wolvix is perhaps one of the easiest slack-based distro to install for a total newbie. Zenwalk is pretty easy as well. But, I would give wolvix its props here. The admin on wolvix is also very very helpful from what I have read and seen. If wolvix used xorg 7, I would be there also primarily. I believe you can learn more as the admin or developer seems more patient than most to explain.

---

### Post by thegrimgod on 2007-03-05
first , ty all for reply , and ill try all of em , (already have wolvix down , but not givin up on slack11 yet)
methodone ,i did as u said , and most likely i made a mistake, from the menu i can boot from the floppy (on which i am already running guess it made sense) , and from my harddisks---gets me back to ubuntu :( , but i cant from the cdroms , gives me a disk error 0x01 i think i can check it back if it is relevent , from the removebale drives , it wont , no os there , makes sense 
now when this thing detects(may not have any importance , but ill ask) it see fd0 as floppy , hd0 as harddrive , and cd0 i beleieve as cdrom  , tho i have many more , shouldnt i get hdc for my cdrom , since there is where ubuntu mounts it ,or is it irelevant since ubuntu didnt even boot , im new , so im just covering anything i can :) , ty again

---

### Post by thegrimgod on 2007-03-26
:( no one has anymore answers or i didnt explain well...bad english...:( , anywhoo , it seems i wont get it to work this way , can anybody explain if i could boot from a network , and how would i do that , i really really want to try slack

---

### Post by mephisto786 on 2007-04-05
haave you tired booting lsacware from an iso burned on a slow speed, like 4x??

you may also want to look at boot prompts depending on your hardware, as you can chooose kernels etc at the boot prompt....porvided you have a correctly burned iso....

good luck

---

### Post by StarsAndBars14 on 2007-04-05
You should need three floppies at least for Slackware 11, two with the install.1 and install.2 images written to them and one with your default kernel (bare.i).  If that doesn't work then its possible that you have a bad ISO.
Put the disk that you wrote install.1 to in your floppy drive, restart your computer (with first boot set to A: of course) and follow the prompts.

Good luck.

---

