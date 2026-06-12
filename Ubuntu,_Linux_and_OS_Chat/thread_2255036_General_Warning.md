---
title: "General Warning"
date: 2014-12-01
forum: Ubuntu, Linux and OS Chat
---

### Post by Tony_Fendall on 2014-12-01
Don't ever, EVER, install Ubuntu as single operating system; leave windows on the PC too.
My laptop is now scrap as I can't uninstall faulty Ubuntu or install any operating system on my laptop any more.
Tony

---

### Post by howefield on 2014-12-01
No semblance of a support thread here, so moved to "*Ubuntu, Linux and OS Chat*" forum.

---

### Post by d-cosner on 2014-12-01
Wow! You do not know what you are doing and it's Ubuntu's fault? Windows can be reinstalled, use it's partitioning tools and remove the partitions starting from the last to the first. After tha partitions are deleted the install will contiue as normal.

---

### Post by nicholi1977 on 2014-12-01
[quote=d-cosner] Windows can be reinstalled, use it's partitioning tools and remove the partitions starting from the last to the first.[/quote]

Agreed, d-cosner. Tony_Fendall, when you try to reinstall Windows, are you trying to delete/recreate the partitions? Windows and Ubuntu use very different file systems. Unless you remove the Extx file system Ubuntu sits on, you WON'T be able to install Windows. Any time you install any OS you should start with fresh partitions...

---

### Post by Hansiman on 2014-12-02
I've never had a problem reinstalling Windows after using Ubuntu, even after I managed to crash Ubuntu so bad that it refused to boot.

What happens when you try to install Windows now?

---

### Post by mastablasta on 2014-12-02
> **Tony_Fendall said:**
> Don't ever, EVER, install Ubuntu as single operating system; leave windows on the PC too.
My laptop is now scrap as I can't uninstall faulty Ubuntu or install any operating system on my laptop any more.
Tony

you can reinstall Ubuntu. procedure is same as for install (expert mode=something else) except you do not format the drive on install.

you can also install windows, if you have windows install disk.

---

### Post by coldraven on 2014-12-02
I think we need a forum section called /dev/null for people who join, not to ask advice but only to write negative comments.
If he had bothered to ask his problem could have been solved in 10 minutes.

---

### Post by howefield on 2014-12-02
> **coldraven said:**
> I think we need a forum section called /dev/null for people who join, not to ask advice but only to write negative comments.
If he had bothered to ask his problem could have been solved in 10 minutes.

S/he did... six months ago and didn't bother coming back then either. ETA for next post/comment around May 24th 2015. :)

---

### Post by sudodus on 2014-12-02
> **howefield said:**
> [QUOTE=coldraven;13178789]I think we need a forum section called  /dev/null for people who join, not to ask advice but only to write  negative comments.
If he had bothered to ask his problem could have been solved in 10 minutes.

S/he did... six months ago and didn't bother coming back then either. ETA for next post/comment around May 24th 2015. :smile:[/QUOTE]

:lolflag: I think you are right both of you. Anyway, no use to spend much time trying to help.

---

### Post by Tony_Fendall on 2014-12-02
I do thank you for your previous advice, but it was of no use, as the damage had already been done.
I no longer have access to my laptop systems, just a faulty Ubuntu and the laptop was not supplied with an install disk.
I wanted to point out to other novices, do not take the option of deleting Windows or you may end up with no PC/laptop.
My comments were not intended to be anti Ubuntu, I would love to try it out.
Tony

---

### Post by Hansiman on 2014-12-02
If you had access to any other computer, you could have most likely prepared a USB installer for Windows, and booted your computer from that.

Usually your OEM key is supplied on the bottom of the chassis on a sticker. Otherwise the maker of the computer can often supply you with your key by contacting their support line.

If you can get into BIOS, you can fix it. =)

---

### Post by /ADM on 2014-12-02
> **coldraven said:**
> I think we need a forum section called /dev/null for people who join, not to ask advice but only to write negative comments.
If he had bothered to ask his problem could have been solved in 10 minutes.

Just call it 'trolling'.

I've installed so many OS's on my Acer machine it's not even funny and everything is ok.  To the OP, this is what you get when non-techies try to install an OS.  If you can't even reinstall Windows, best not to mess with anything.

*grabs popcorn*

---

### Post by coffeecat on 2014-12-02
> **Tony_Fendall said:**
> just a faulty Ubuntu and the laptop was not supplied with an install disk.
I wanted to point out to other novices, do not take the option of deleting Windows or you may end up with no PC/laptop.

Then you gave wrong and misleading advice. Every Windows laptop I have used for the last 10 years or so has not come with an "install disk" as you put it. But every one has come with not only a recovery/restore partition but a utility for creating a set of recovery/restore DVDs or bootable recovery/restore USB. So my advice to novices would be:

Before installing Ubuntu:

[list][*]Read the manufacturer's manual. Make sure you know which keys are needed to access the BIOS or to access the recovery partition.
[*]Use the manufacturer&#8217;s installed utility to create a set of recovery/restore DVDs or a bootable recovery/restore USB.
[*]When you install Ubuntu, it is sensible not to delete the recovery partition in case you wish to restore the Windows operating system.  
[*]If you are really intent on deleting everything on the hard drive before installing Ubuntu, then ensure you have  created a set of recovery/restore DVDs or a bootable recovery/restore USB.
[/list]

---

### Post by bro2 on 2014-12-02
> **Tony_Fendall said:**
> I do thank you for your previous advice, but it was of no use, as the damage had already been done.
I no longer have access to my laptop systems, just a faulty Ubuntu and the laptop was not supplied with an install disk.
I wanted to point out to other novices, do not take the option of deleting Windows or you may end up with no PC/laptop.
My comments were not intended to be anti Ubuntu, I would love to try it out.
Tony

1. Use Gparted from a CD/USB
2. Create an MBR File system (will erase EVERYTHING!!!)
3. Install Windows. Your disk will now be recognized.


Windows does not have drivers to read EXT4 file systems that Ubuntu uses. It won't let you install Windows if your entire disk is taken up by Ubuntu (won't "see" any drives).

Also research dual booting.


Also to all new people: don't replace your current OS with Ubuntu if you've never tried it before.

---

### Post by /ADM on 2014-12-02
> **Tony_Fendall said:**
> I do thank you for your previous advice, but it was of no use, as the damage had already been done.
I no longer have access to my laptop systems, just a faulty Ubuntu and the laptop was not supplied with an install disk.
I wanted to point out to other novices, do not take the option of deleting Windows or you may end up with no PC/laptop.
My comments were not intended to be anti Ubuntu, I would love to try it out.
Tony

Then why not burn another DVD with 14.04 or use a USB (unetbootin) to boot another Ubuntu Live session and use the entire disk to put Ubuntu as the only OS?  Seriously, installing or messing it up won't destroy the laptop (only novices think this).  If you booted it once you can boot it again.

So what is the problem?  What is it that you cannot seemingly do again if you have done it once before?

---

### Post by buzzingrobot on 2014-12-02
> **Tony_Fendall said:**
> I... the laptop was not supplied with an install disk.


Not providing an install DVD is a Windows weakness.  Restorals are done via a "hidden" partition.  If the user deletes that partition, the only way to restore Windows is to boot from an actual Windows install DVD. (I believe Windows machines typically ship with an offer to purchase those install DVD's.) 

That "hidden" Windows partition is only hidden to Windows users.  It is not hidden to other operating systems. If you choose to install another operating system and to use all the disk(s), then the disk(s) will be repartitioned, and that includes removing *all* the Windows partitions.

If you do, in fact, boot from a Windows install DVD, you need to use it to delete any existing partitions before you proceed.  I'd recommend doing that and then rebooting to start the process from the beginning.

It's unfortunate you had this trouble, but it's rooted in the inadequacies of how Windows is provided these days and its assumption that it's the only OS that will ever be installed.

---

### Post by Tony_Fendall on 2014-12-02
I am a novice and I don't know how to recover the situation as all advice has failed to work. It won't boot from USB it won't boot from DVD drive, just goes straight into faulty Ubuntu 14.04 LTS.
I know the laptop is destined for the bin and just want to save other novices from falling into the same trap; don't ditch the existing Windows OS.

---

### Post by buzzingrobot on 2014-12-02
> **Tony_Fendall said:**
> I am a novice and I don't know how to recover the situation as all advice has failed to work. It won't boot from USB it won't boot from DVD drive, just goes straight into faulty Ubuntu 14.04 LTS.
I know the laptop is destined for the bin and just want to save other novices from falling into the same trap; don't ditch the existing Windows OS.

You need to alter a BIOS setting to boot from a USB. If you have done that correctly and still can't boot from the USB, then either the laptop is itself, in fact, faulty, or the image on the USB stick is damaged (which can happened if it is removed improperly).

An Ubuntu installation does not render hardware unusable.  Any perceived unusability is either coincidental with actual hardware failure, or, frankly, due to user errors.

Telling novices to be wary of removing the Windows restore partition if they want to preserve the option to restore Windows is good advice. Telling them Ubuntu will break their system is inaccurate and unwarranted advice.

---

### Post by Hansiman on 2014-12-02
But why are you unable to get into BIOS to change the boot settings? The BIOS access should appear before Ubuntu even starts to load.

---

### Post by PondPuppy on 2014-12-02
As others have suggested, the laptop is almost certainly salvageable.

But you need to access the BIOS in order to make the laptop boot from a DVD, CD, or USB. Right now it appears the BIOS boots from the hard drive first, and that puts it into the borked Ubuntu install. You need to tell it not to do that.

Often the BIOS can be accessed by pressing F1 or F2 as the computer boots. But different manufacturers use different keys or combinations of keys, and you really need to check for your specific make and model. 

A partial list of makes and models and the keys used for BIOS can be found here: [http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm](http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm)

Search online for your particular machine to be sure.

Once you get into the BIOS, set the machine to boot from DVD or USB as the first option. Post back if you have trouble with that step.

But you don't have to give up on the machine unless you want to.

---

### Post by Yougo on 2014-12-02
i smell a case of PICNIC.

Just wondering, do you scrap your entire car when it has a flat tyre after you went head first and poked at it yourselves?

From what i gather it does boot into ubuntu, but you call it 'faulty'. i've had my share of 'faulty' situations (99% caused by tinkering :P ) but as long as i have an internet connection and a command prompt or even some sort of desktop, i always got it back up. and i learned a lot in the process

are you going to ask for help, or are you going to just trash an -until proven otherwise- perfectly fixable computer. your money...

---

### Post by /ADM on 2014-12-02
Can I ask, if you cannot boot from dvd but you managed to install Ubuntu, then you must have set the bios to boot from dvd first.  You have not provided laptop details, what you did etc.  So help us to help you or I will take this as simply trolling.  Or do you not want to be helped and have your laptop saved?

---

### Post by sudodus on 2014-12-02
> **Tony_Fendall said:**
> I am a novice and I don't know how to recover the situation as all advice has failed to work. It won't boot from USB it won't boot from DVD drive, just goes straight into faulty Ubuntu 14.04 LTS.
I know the laptop is destined for the bin and just want to save other novices from falling into the same trap; don't ditch the existing Windows OS.

If you want to get Windows or Ubuntu or both back and a working computer, ***please tell us as much as possible about your computer***. Specify at least

- Brand name and model (very important since it will give us a chance to help you get into your BIOS/UEFI system)
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by Tony_Fendall on 2014-12-02
Of course it's due to user error somewhere along the line, but what has broken my system if not an attempt to install Ubuntu, it was not broken before the Ubuntu install.
Is there anyone in Basingstoke who would like to try to install Ubuntu 14.

---

### Post by /ADM on 2014-12-02
Why not ask for help?  You have not answered our questions or attempts to help you.

---

### Post by Tony_Fendall on 2014-12-02
Since hacking all day I have tried running the Vista recovery disk for my laptop, which failed.
However the laptop now boots and runs Ubuntu 14.02 without mains supply and responds to the Off Button.
So now if I can get wireless to work I would be able to use the laptop again. Wired works fine but the wireless switch does not switch on wireless and I don't know how to get it back. 
I realise I am a tremendous nuisance to you all, but if I could resolve wireless I would be happy again.

---

### Post by /ADM on 2014-12-02
If you answered our requests for laptop specs we can help you.  You're not being helpful by ignoring our requests.  I won't post again if you're going to play with us instead of letting us help you.

We are volunteers here, our time is our own.  So be helpful.

---

### Post by QIII on 2014-12-02
Tony_Fendall,

You may have put others off previously in this thread by not providing requested information and/or not responding to the suggested steps for resolution.   I you want help with your wireless, it might be in your best interest to answer questions (asked for diagnostic purposes) and to report back on the effect of suggested actions.

Please help people help you.

---

### Post by buzzingrobot on 2014-12-02
> **Tony_Fendall said:**
> Since hacking all day I have tried running the Vista recovery disk for my laptop, which failed.

How did it fail?  Were you able to boot into it? (Needing to adjust the BIOS to boot from a DVD or USB is independent of any OS. The BIOS always assumes control when a machine boots, every time, and then turns control over to the operating system it assumes is on the drive it has been told to boot from.)

> However the laptop now boots and runs Ubuntu 14.02 without mains supply and responds to the Off Button.

A typo?  There is no "14.02" version of Ubuntu.  There is the 12.04 release, and the 14.04 and the 14.10 releases. Systems Settings->Details will show you. (Access Systems Settings via the little cog icon on the far right of the top panel or, in a standard install, via its icon in the Launcher on the left.)

Does the laptop boot and run plugged into mains, or only on battery? 

>  ...wireless switch does not switch on wireless and I don't know how to get it back. 

That suggests wireless previously worked on Ubuntu. Correct?   If not, you may have wireless hardware that requires a specific proprietary vendor driver. We need to know your hardware specifications, first.
 
> I realise I am a tremendous nuisance to you all, but if I could resolve wireless I would be happy again.

No nuisance.  Telepathy doesn't work, though, so we just need more info about your machine and your setup.

---

### Post by QIII on 2014-12-02
On re-reading this thread and noting both it's title and location, the subject at hand is no longer in reasonable context.

Please start a new thread requesting help in the Networking & Wireless section where you will get more specific guidance.

Thread closed.

---

