---
title: "Ubuntu 14.10 no GUI or term login"
date: 2014-05-29
forum: Ubuntu Development Version
---

### Post by eusonlito on 2014-05-29
I have updated yesterday my Ubuntu 14.10 installation with apt-get dist-upgrade.

I was working all afternoon and after that I have rebooted computer. Once done it, lightdm doesn't starts (only gnome logo) and I can not view any of Ctrl + Shift + [1-6] terminals (cursor is blinking).

I have read a lot of posts with no success:

[LIST]
[*]nividia/intel conflicts (I have a laptop with an Intel graphic card)
[*]I have enabled nomodeset and tried all this options [My computer boots to a black screen, what options do I have to fix it?]("http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it") and some of [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535").
[*]I have repaired grub
[*]I can load recovery/livecd/windows and mount partitions and network without problem
[*]I have all packages and system updated
[/LIST]

Here my [logs]("http://pastebin.com/7jntD4Bm"). X11 not shows any error or problem, is loading all needed drivers without problem.

How can I raise the level of debug?

Best regards.
Lito.

---

### Post by coffeecat on 2014-05-29
Ubuntu 14.10.

*Thread moved to **Ubuntu Development Version**.*

@eusonlito, is this your main system or are you testing the development version? The development cycle is still at such an early stage for 14.10 that it would be unwise to use it for your main working system.

---

### Post by zika on 2014-05-29
Anything to do with [http://ubuntuforums.org/showthread.php?t=2226708](http://ubuntuforums.org/showthread.php?t=2226708) ...? (Even possible merge... ;))

---

### Post by eusonlito on 2014-05-29
> **zika said:**
> Anything to do with [http://ubuntuforums.org/showthread.php?t=2226708](http://ubuntuforums.org/showthread.php?t=2226708) ...? (Even possible merge... ;))

Ok, thanks!!! this post [http://ubuntuforums.org/showthread.php?t=2226708&p=13036073#post13036073](http://ubuntuforums.org/showthread.php?t=2226708&p=13036073#post13036073) solved my problem :)

Thanks again :)

---

### Post by eusonlito on 2014-05-29
> **coffeecat said:**
> Ubuntu 14.10.

*Thread moved to **Ubuntu Development Version**.*

@eusonlito, is this your main system or are you testing the development version? The development cycle is still at such an early stage for 14.10 that it would be unwise to use it for your main working system.

This is my main system in my laptop and main pc, I'm developer and I like to test and check bugs ASAP.

I have no problems to have down my computer some hours if I can learn as solve this problems :)

Best regards,
Lito.

---

### Post by zika on 2014-05-29
> **eusonlito said:**
> This is my main system in my laptop and main pc, I'm developer and I like to test and check bugs ASAP.

I have no problems to have down my computer some hours if I can learn as solve this problems :)

Best regards,
Lito.I also do find it as only way to test anything to use it as it should be used and be prepared... Nice to see I'm not alone... ;)
Almost everything I've learned (if I've learned anything at all) came just from knowledge/endurance/patience-testing situations in Testing... ;)

---

### Post by coffeecat on 2014-05-29
> **eusonlito said:**
> This is my main system in my laptop and main pc, I'm developer and I like to test and check bugs ASAP.

I have no problems to have down my computer some hours if I can learn as solve this problems :)

Best regards,
Lito.

Thanks for confirming. We occasionally get users who install the latest dev version even in the early stages and then wonder why it breaks. I just wanted to be sure because my advice to such people would be to re-install with a supported version. But it sounds as though you are enjoying yourself just fine. :) 

Good luck with that!

---

### Post by grahammechanical on 2014-05-29
I caught this bug yesterday on the 14.10 install I use most of the time. It tempted me to the point that I now have grub rescue "unknown file system" for that partition. It has also well and truly borked the daily images. I thought that I would re-install the latest daily without formatting the partition to see If I could recover the installation. It does not have any critical data.

The image of 28th would only get to the live session by enter x 2 + TRY but neither of the two install 14.10 icons would launch ubiquity. Nether would enter x 2 + Install.

The image of 29th does not even get that far. The purple splash screen with the dots comes up but at the point when we should get either a live session or a background with the install dialog (ubiquity) all we get is a blackscreen. The F6 nomodeset does not improve things. I have other installs but update-grub does not detect this partition. So, I cannot boot into to it with recovery mode.

Never say the development release has become boring. ;) I might try adding init=/lib/systemd/systemd to the live session boot parameters. Just for a laugh.

EDIT: Well that worked after a fashion. I changed

```
quiet splash --
```

for 

```
quiet splash -- init=/lib/systemd/systemd
```

and with either TRY or Install selected I got to a login screen. The username was Username and I pressed enter and got to a live session but the two "install Ubuntu 14.01" icons did not launch Ubiquity. The next time I tried this at the login screen after pressing Enter I was requested a password. User = ubuntu, password = ubuntu does not work. Nor does anything else that I can imagine. This is now starting to feel like hard work.

---

