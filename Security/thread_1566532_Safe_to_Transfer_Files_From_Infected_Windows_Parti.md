---
title: "Safe to Transfer Files From Infected Windows Partition?"
date: 2010-09-02
forum: Security
---

### Post by Kixtosh on 2010-09-02
My Windows XP Pro laptop has been attacked! **[COLOR="Red"]Windows will no longer update and Microsoft Security Essentials will not update either. [/COLOR]**I've been trying to resolve the issue for over two weeks with Microsoft support, but it's just taking too long. I also tried some rescue CD options (all running some form of Linux, obviously):

- BitDefender Rescue CD (removed infections, now detects nothing),
- Kaspersky Rescue CD 10 (removed infections, now detects nothing), 
- Trinity Rescue CD (won't load AV Engine, so can't use it to do anything).

**[COLOR="Red"]Malwarebytes[/COLOR]** cleaned a bunch of stuff, but will not clean the final threat detected (it's supposed to get deleted on reboot, but never does). **[COLOR="Red"]Hijack.FolderOptions[/COLOR]** is stuck in the accursed registry, and it keeps causing Windows Explorer to crash. I cannot rename files or work with them or everything just crashes.

So I'm ready to reinstall XP from scratch, and add a dual boot with Xubuntu & LXDE, which I'm already running on a much older laptop.

Question: I want to rescue the files I need. My idea was:

1) Install Xubuntu with dual boot.
2) Copy over files from Windows XP partition using Xubuntu.
3) Back up files to an external drive using Xubuntu.
4) Reinstall XP Pro and format hard drive.
5) Reinstall Xubuntu with dual boot.
6) Use Xubuntu for daily use.
7) Only use XP for those tasks that require it (TomTom updates ...)

[B][COLOR="Red"]Should I be concerned about the security risk from copying files from the Windows partition to the Xubuntu partition, and from there onto an external hard drive?
[/COLOR][/B]
Is this the way to do it, or is there a better way? I just want my laptop back in working order. Right now I can't use it for anything.

---

### Post by howefield on 2010-09-02
> **Kixtosh said:**
> Should I be concerned about the security risk from copying files from the Windows partition to the Xubuntu partition, and from there onto an external hard drive?

If you have scanned them and you are happy that they are clean, there isn't much more that you can do, copy them over to the external and scan again.

> Is this the way to do it, or is there a better way?

I'd just boot with a live CD and copy your valuable files straight across to the external. (Well, to be more accurate, I'd use a bootable USB with Bitdefender on it). No real need to install xubuntu twice.

Then install windows, and finish with your xubuntu install.

---

### Post by Kixtosh on 2010-09-02
> **howefield said:**
> ... I'd just boot with a live CD and copy your valuable files straight across to the external. (Well, to be more accurate, I'd use a bootable USB with Bitdefender on it). No real need to install xubuntu twice. ...Ah, yes, of course ... that makes plenty of sense, especially since the Live CD seems to boot up fairly quickly on the infected machine.

What's the advantage (if any) of using the BitDefender CD or USB instead of a Xubuntu Live CD?

[COLOR="DarkRed"]*P.S. First 100 Beans for me Today!*[/COLOR]

---

### Post by OpSecShellshock on 2010-09-02
> **Kixtosh said:**
> Ah, yes, of course ... that makes plenty of sense, especially since the Live CD seems to boot up fairly quickly on the infected machine.

What's the advantage (if any) of using the BitDefender CD or USB instead of a Xubuntu Live CD?

[COLOR=DarkRed]*P.S. First 100 Beans for me Today!*[/COLOR]

I think the Bitdefender disk primarily would afford the luxury of scanning the files immediately once they've been moved. Eliminates a couple steps.

---

### Post by howefield on 2010-09-02
> **Kixtosh said:**
> What's the advantage (if any) of using the BitDefender CD or USB instead of a Xubuntu Live CD?

None, what I mean is I'd use an Ubuntu live USB stick that I'd installed BitDefender on. Boot from it, scan the windows disk, copy the files over and then format and create the partitions ready for the installs.

You are basically doing everything you need to do prior to the fresh installs with one Live stick.

Live CDs can't save settings ect, whereas a USB can save settings / applications ect, ect so when you boot from it, you have everything that you would have on a full desktop down to your favourite wallpaper ;-) 

> P.S. First 100 Beans for me Today!

Congrats :)

---

### Post by Kixtosh on 2010-09-02
All of that makes perfect sense, thank you!

And of course, now that I'm fed up, Microsoft have finally come through with free chat support (since it's a security issue), and seem to have fixed the issues using EasyAssist remote desktop control. It'll be a bit less frightening to copy files from this system now that it seems to be working just about normally ...

The good news is that I've had a chance to try all those Rescue CD's and a Live CD or two, so I'm pretty much sure that there are no major hardware conflict issues before installation (crosses fingers and toes).

---

### Post by Kixtosh on 2010-12-21
Just to tidy up, in case this thread ever comes up in a forum search, and mark this thread as solved:

This all worked like a charm. XP is now fully installed anew, and boots up in just under two minutes (well, it always takes a bit longer for the HDD activity light to stop blinking and the running processes to settle down). It works better than it has done in a long time, since it had been taking five whole minutes to start up. Shut down still takes about 30 seconds, but that's fairly normal, I think. There are no signs of any infection, but I've left most of the internet options on "paranoid" settings. I should have done this a long time ago!

I didn't need Xubuntu or Lubuntu in the end. Ubuntu was almost as fast, even though this ultra-light laptop only has a single core 1.2GHz CPU, and is limited by design to 1.28GB of RAM (I installed all of them, since it was so fast and easy to do, before making up my mind on which to use). Ubuntu now boots up in about 50 seconds and shuts down in about 5 seconds (mostly I just suspend it though, which is even faster). Just about everything needed works out of the box, including a slim PC card adding two extra USB ports so that I now have four in total (it actually fits completely flush with the laptop chassis). Wireless and bluetooth required no tweaking of any description either.

Naturally, I now use Ubuntu every day, and try to remind myself to boot up XP at least every other week so that it can update what it needs to.

Thanks everyone!

---

### Post by wcdrotar on 2010-12-21
> **Kixtosh said:**
> My Windows XP Pro laptop has been attacked! **[COLOR=Red]Windows will no longer update and Microsoft Security Essentials will not update either. [/COLOR]**I've been trying to resolve the issue for over two weeks with Microsoft support, but it's just taking too long. I also tried some rescue CD options (all running some form of Linux, obviously):

- BitDefender Rescue CD (removed infections, now detects nothing),
- Kaspersky Rescue CD 10 (removed infections, now detects nothing), 
- Trinity Rescue CD (won't load AV Engine, so can't use it to do anything).

**[COLOR=Red]Malwarebytes[/COLOR]** cleaned a bunch of stuff, but will not clean the final threat detected (it's supposed to get deleted on reboot, but never does). **[COLOR=Red]Hijack.FolderOptions[/COLOR]** is stuck in the accursed registry, and it keeps causing Windows Explorer to crash. I cannot rename files or work with them or everything just crashes.

So I'm ready to reinstall XP from scratch, and add a dual boot with Xubuntu & LXDE, which I'm already running on a much older laptop.

Question: I want to rescue the files I need. My idea was:

1) Install Xubuntu with dual boot.
2) Copy over files from Windows XP partition using Xubuntu.
3) Back up files to an external drive using Xubuntu.
4) Reinstall XP Pro and format hard drive.
5) Reinstall Xubuntu with dual boot.
6) Use Xubuntu for daily use.
7) Only use XP for those tasks that require it (TomTom updates ...)

[B][COLOR=Red]Should I be concerned about the security risk from copying files from the Windows partition to the Xubuntu partition, and from there onto an external hard drive?
[/COLOR][/B]
Is this the way to do it, or is there a better way? I just want my laptop back in working order. Right now I can't use it for anything.

To answer the real concern you have, I don't think there's any risk of Linux getting contaminated by Windows malware.  It can be a carrier however.  

I'm not seeing the value in transferring it to Xubuntu and then to an external.  Why not directly from Windows?  It won't clean the files if they're still infected by transferring them to Linux first.  It's also more difficult to backup and restore from Linux than Windows since it's not automated.  

You could do that, or just use only Linux with Windows in a VM when needed (iTunes, TomTom, or .exe files that won't work in Wine when it's necessary for stupid little reasons).  If it's an older computer a dual-boot might be a better option.  

What you suggested would work too.  Just trying to save you some time :p.

---

### Post by Kixtosh on 2010-12-22
> **wcdrotar said:**
> ... I'm not seeing the value in transferring it to Xubuntu and then to an external.  Why not directly from Windows?  ...I didn't want to use the Windows system at all, since it was no longer trustworthy. I used the Ubuntu LiveCD to copy the files to an external drive (as howefield suggested above) rather than follow my original plan as described in my first post. I didn't want to give whatever infection might have been present any chance to do any more damage, or leave me unable to even rename files or folders again. Perhaps it wasn't necessary though.

Anyway, it worked perfectly, including the XP install process (which took rather a long time ... after all the updates and service packs, M.S.E. security software to install and update and whatever else).

---

