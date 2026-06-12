---
title: "Windows is DANGEROUS"
date: 2007-02-24
forum: The Cafe
---

### Post by TheMono on 2007-02-24
I'm currently writing this from my laptop rather than my brand new desktop. Why, you say?

Simple - I tried to install windows. I got through to the point where you select a partition for it to go on. I'd carefully resized my feisty partitions (one for /home and one for /) to allow it space to install. Nothing complicated going in like LVM or multiple disks etc. 

In the Windows setup, I selected "Free Space" to install to. Naturally, windows decided to save me the time of installing by simply displaying a Blue Screen of Death preemptively.

How Kind, I though. But never fear, I can just reboot and all will be well. After all, it shouldn't have written anything to disk. And even if it has, I only told it to touch the free space.

Ah, not so. In fact, it saw fit to kill my partition table.... So I now have a blank HDD. No feisty, no feisty home partition. Nothing...

Is this something to do with maintaining a monopoly on my computer? I'm exceedingly angry about this. The Ubuntu installer would NEVER do something like kill partitions it was told not to touch. It's simply shocking code that XP could do that.

---

### Post by steven8 on 2007-02-24
I've read threads here on the forum about how it's bad to install windows after a linux distro.  How it can destroy things, because windows is designed to want to be the only OS on your computer.  I hadn't read of any scenarios where is ruined the whole drive, though.

---

### Post by TheMono on 2007-02-24
It hasn't ruined it per se... I just have to reinstall everything lol.

---

### Post by steven8 on 2007-02-24
> **TheMono said:**
> It hasn't ruined it per se... I just have to reinstall everything lol.

Perhaps, but I believe gparted would have respected your space.

---

### Post by Bigbluecat on 2007-02-24
You may be able to recover your partition table using a program called Testdisk. I found it on the GParted LiveCD and used it to recover my widnows drive after it trashed the partition table.

---

### Post by ComplexNumber on 2007-02-24
> **TheMono said:**
> I'm currently writing this from my laptop rather than my brand new desktop. Why, you say?

Simple - I tried to install windows. I got through to the point where you select a partition for it to go on. I'd carefully resized my feisty partitions (one for /home and one for /) to allow it space to install. Nothing complicated going in like LVM or multiple disks etc. 

In the Windows setup, I selected "Free Space" to install to. Naturally, windows decided to save me the time of installing by simply displaying a Blue Screen of Death preemptively.

How Kind, I though. But never fear, I can just reboot and all will be well. After all, it shouldn't have written anything to disk. And even if it has, I only told it to touch the free space.

Ah, not so. In fact, it saw fit to kill my partition table.... So I now have a blank HDD. No feisty, no feisty home partition. Nothing...

Is this something to do with maintaining a monopoly on my computer? I'm exceedingly angry about this. The Ubuntu installer would NEVER do something like kill partitions it was told not to touch. It's simply shocking code that XP could do that.
are you sure it merely didn't blank the MBR? its only likley that fiesty would have been killed if the BSOD occured in the middle of resizing. fiesty is probable still there and accessible.

---

### Post by floke on 2007-02-24
Yep, windows is imbued with the MS philosophy of greed, and wants to have the entire hard drive for itself. Its very difficult to get windows on a PC with another OS already on it.

Just another reason why it's a load of crap, really.

** EDIT ** you could try using a LiveCD to see if there's any data still on the disc

---

### Post by stoeptegel on 2007-02-24
This happened with vista, right?
Because /me has some dualboot to repair here too: the OS that came with my neighbours laptop, winxp, which felt it was needed to boot into BSOD's after one and a half week using it.

Thank you for supporting this crap, Dell.

(and then there is something with the Dell windows dvd which seems to make the laptop to vibe like an airplain)

---

### Post by karellen on 2007-02-24
that's why I always install linux **after** the stupid I-want-to-be-the-only-one-around-here-f***-the-rest Windows :mad:

---

### Post by Mathiasdm on 2007-02-24
> **TheMono said:**
> I'm currently writing this from my laptop rather than my brand new desktop. Why, you say?

Simple - I tried to install windows. I got through to the point where you select a partition for it to go on. I'd carefully resized my feisty partitions (one for /home and one for /) to allow it space to install. Nothing complicated going in like LVM or multiple disks etc. 

In the Windows setup, I selected "Free Space" to install to. Naturally, windows decided to save me the time of installing by simply displaying a Blue Screen of Death preemptively.

How Kind, I though. But never fear, I can just reboot and all will be well. After all, it shouldn't have written anything to disk. And even if it has, I only told it to touch the free space.

Ah, not so. In fact, it saw fit to kill my partition table.... So I now have a blank HDD. No feisty, no feisty home partition. Nothing...

Is this something to do with maintaining a monopoly on my computer? I'm exceedingly angry about this. The Ubuntu installer would NEVER do something like kill partitions it was told not to touch. It's simply shocking code that XP could do that.
It doubt it removed your partitions, it probably just replaced the MBR. Overwrite it with GRUB and you'll be fine.

---

### Post by Ek0nomik on 2007-02-24
I'm with karellen.  I had to make sure to install Ubuntu after Windows.

I am assuming your MBR just got borked.

---

### Post by TheMono on 2007-02-24
It was XP, not vista.

I doubt it was my MBR - I booted to a gparted live CD after which showed 250GB raw space... I don't know enough to say this is definitely not an MBR issue, but it sure didn't seem like one.

---

### Post by Zimmer on 2007-02-24
> **TheMono said:**
> It was XP, not vista.

I doubt it was my MBR - I booted to a gparted live CD after which showed 250GB raw space... I don't know enough to say this is definitely not an MBR issue, but it sure didn't seem like one.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Might help, but using a System Rescue disc could be easier to recover partition tables, MBR etc.
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by TheMono on 2007-02-24
It doesn't really matter that much, my feisty install was all of a few days old anyway, and I hadn't put any of my documents on there to start with, much less had need to back them up lol.

It's more the principle of it that annoys me - windows getting rid of everything. While I'm sure it probably was recoverable, I don't see Ubuntu doing that to windows partitions!

---

### Post by Trebuchet on 2007-02-24
> **TheMono said:**
> It's more the principle of it that annoys me - windows getting rid of everything. While I'm sure it probably was recoverable, I don't see Ubuntu doing that to windows partitions!While that's no doubt true, Ubuntu was designed to work with Windows. Windows wasn't designed to work with Ubuntu. Most of the time Windows can't even detect another OS. (And, yes, they should. Maybe their recent deal with Novell will finally lead Redmond to consider improving "Plays well with others" on its corporate report card. I'm not holding my breath.)

You're assuming a worst-case scenario and using that premise to attack Microsoft when people have pointed out, probably correctly, that XP probably just screwed up your MBR. It's highly unlikely it actually deleted an entire partition in the few seconds of a BSoD. Generally a BSoD means the system can't do *anything* at all, much less overwrite a multi-gigabyte partition.

I've never seen an XP BSoD; I was under the impression XP doesn't ever BSoD but instead reboots itself.

---

### Post by Gargamella on 2007-02-24
I can't really understand why it doesn't give you a decent possibility of dual boot by installing it...you have to do it only with linux. It is designed to reign and ruin everything.

They are not God and they can't think in this way ;D

---

### Post by UltimaDude on 2007-02-24
I have, the whole reason i'm getting Ubuntu is for a better experiance.
I'm just worried, will the Desktop CD mess up my computer?

---

### Post by steven8 on 2007-02-24
> **UltimaDude said:**
> I have, the whole reason i'm getting Ubuntu is for a better experiance.
I'm just worried, will the Desktop CD mess up my computer?

BY desktop CD, do you mean the liveCD?  No, the liveCD will make no changes to your computer.  It just allows you to see how compatible your hardware is, and to get a feel for the interface and programs.  When you select to shutdown the computer, or restart from the liveCD, it will shutdown services, etc., eject the disk for you, so you can remove it, then finish it's action after you hit 'enter'.

The liveCD is so user friendly you'll be amazed.  Have fun and convert like I've done.  You won't be disappointed!!

---

### Post by Raavea on 2007-02-24
> **steven8 said:**
> (...)
The liveCD is so user friendly you'll be amazed.  Have fun and convert like I've done.  You won't be disappointed!!
I have to mention here that if you have about 256MB RAM and a slow CD reader like the laptop I am using, the liveCD will be VERY slow. **However,** the OS once installed is VERY speedy, especially with lighter windows managers... I use GNOME though, 'cuz I like the pretty transparentness, and the stock programs, and because I'm patient enough to wait a whole second for the menu to open, as compared to ten or fiftenn when this laptop had XP on it... :3

---

