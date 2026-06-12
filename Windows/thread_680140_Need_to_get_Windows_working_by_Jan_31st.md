---
title: "Need to get Windows working by Jan 31st"
date: 2008-01-27
forum: Windows
---

### Post by Will Pittenger on 2008-01-27
I was having problems getting my Windows XP Pro SP1 install disk to boot.  (It would boot until it said "Starting Windows" and quit.)  I was told in an older thread here that I should have installed Windows and then installed Ubuntu.  So I cleaned off the drive with DiskPart and started over.

This time, I installed Windows and had it working.  I then proceeded to install Ubuntu.  Today I found that Windows no longer boots.  Instead, as soon as the Windows splash appears, my computer reboots itself.  I do NOT see a BSOD.  Windows knows it failed to boot and offers to come up in safe mode which I have yet to try.  What about the Linux install could cause this problem?  Both boot partitions are in the same drive with Grub controlling which partition gets booted.

It looks like DSL will be installed Thursday.  The installers (I don't know why they are needed but they are coming) need XP up and going.  Can anyone help?

---

### Post by lizadove on 2008-01-27
Just so you know, I'm no expert here, but I had a similar problem with my dual (actually tri-boot) system.  I would just get one problem fixed and then another would begin. I kept switching between the "good OS"  and the broken ones. Finally all three are working.  

First of all, are you sure you went through all the installation discs?  My problem ended up being that I needed to put the first installation disc back in after the second one was finished reading to fully install XP.  Otherwise, windows had some very strange problems.

Second, go ahead and try booting in safe mode.  You might be able to run a check disc from there and it could correct itself.  

Another thought I had is perhaps XP won't let you install it twice (did you already register the key??) even though it's on the same machine.  If that's the case, you'll probably need to call microsoft and explain the system after being on-hold for 45 minutes.

Lastly, if you haven't got any important files on your computer yet, and you've tried everyone's advice, try just using XP and not ubuntu until after the 31st.

good luck

---

### Post by stmiller on 2008-01-27
A DSL technician has a small device that can tell if the line is activated and working. A DSL modem makes the connection, and all you need is a web browser to configure a DSL modem.

The tech should have a laptop with him to verify anything if he needs to.

---

### Post by Will Pittenger on 2008-01-27
> **lizadove said:**
> First of all, are you sure you went through all the installation discs?  My problem ended up being that I needed to put the first installation disc back in after the second one was finished reading to fully install XP.  Otherwise, windows had some very strange problems.
My XP copy has only one disc.  What are you talking about being the second?

> **lizadove said:**
>  Second, go ahead and try booting in safe mode.  You might be able to run a check disc from there and it could correct itself.
Unfortunately, I don't know that safe mode is an option.  I don't think it gets that far.  The only options available are probably the ones available through Grub which doesn't list anything like safe mode.  Once XP takes control, there is only like 2 seconds from when the splash appears to when the reboot starts.

> **lizadove said:**
>  Another thought I had is perhaps XP won't let you install it twice (did you already register the key??) even though it's on the same machine.  If that's the case, you'll probably need to call microsoft and explain the system after being on-hold for 45 minutes.
Twice?  When was the first time?  I couldn't even boot the install CD when I installed Ubuntu first.

> **lizadove said:**
>  Lastly, if you haven't got any important files on your computer yet, and you've tried everyone's advice, try just using XP and not ubuntu until after the 31st.Which requires me to clean the hard drive and install Windows.

> **stmiller said:**
> A DSL technician has a small device that can tell if the line is activated and working. A DSL modem makes the connection, and all you need is a web browser to configure a DSL modem.

The tech should have a laptop with him to verify anything if he needs to.
I had used DSL before while in Oregon.  Verizon sent me a simple self-install kit that worked great.  In fact, it had me on the internet before my hardware firewall was connected. :(  So I am confused why it would matter to them what OS I use.

---

### Post by lizadove on 2008-01-27
Goodness!  Sorry for the confusion.  My XP Media Edition came with 2 discs, but during the installation it asked for a third, which of course I didn't have.  If your pack only came with one disc, then don't worry about that advice.

Okay, then in the 2 seconds or whatever you've got between selecting windows and failure, try pushing one of the Fn keys.  I can't remember which one.  :-kPerhaps F10 or F11 Try a bunch - it won't hurt anything.  If it makes it this far, you should be able to select the ability to start in Safe Mode (not a Grub option - a windows option)

And yes, to run windows by itself, it would require the icky reformat and reinstall process.  So, hopefully you won't have to do that - I'm just saying, as a last case scenario, you could do that if you absolutely had to.  

I agree that it's weird they require a particular OS at all.  When I had my DSL installed they didn't even need a computer to test it - just their tools.  Maybe the dude who told you you needed XP didn't know what he/she was talking about.

---

### Post by seventhc on 2008-01-27
It shouldn't matter what os you have, I once had a company where they insisted that a tech comes to do the install. My os was FreeBSD, the tech came, I was the one working the computer though as he had no idea what to do. ;) (consisted of opening a browser :P)But he still installed the broadband and it worked.

---

### Post by Will Pittenger on 2008-01-27
> **lizadove said:**
> Okay, then in the 2 seconds or whatever you've got between selecting windows and failure, try pushing one of the Fn keys.  I can't remember which one.  :-kPerhaps F10 or F11 Try a bunch - it won't hurt anything. 
I think it is F8 for the menu, but I could be wrong.

> **lizadove said:**
> If it makes it this far, you should be able to select the ability to start in Safe Mode (not a Grub option - a windows option)
Can Grub activate the options that XPs own boot menu would use?

> **lizadove said:**
> And yes, to run windows by itself, it would require the icky reformat and reinstall process.  So, hopefully you won't have to do that - I'm just saying, as a last case scenario, you could do that if you absolutely had to.If it comes to that, I will probably just chuck Linux.  It's not worth putting up with.  Some of the tools it comes with would help, but I think there are probably free versions of them for Windows if I can get the bandwidth to download them.

---

### Post by mc4man on 2008-01-27
If you can't get into safe mode what you may want to try is to use your xp disk to boot to the recovery console and run chkdsk /r . If that doesn't work running Fixmbr will restore xp's mbr. Another way is to download and burn a super grub boot disk which can be used to restore a window's mbr and later to give you back a dual boot once you fixed windows (if possible).  This could be a windows only issue - not related to your linux install

---

### Post by Will Pittenger on 2008-01-28
> **mc4man said:**
> This could be a windows only issue - not related to your linux install
I know that.  However, it was the installation of Linux that caused the problem.  I appear to have no way to fix it with out deleting the Linux partition.

---

### Post by Will Pittenger on 2008-01-29
At this point, I might as well delete the Linux partition.  I have another Linux partition (my first attempt) on my portable drive.  It won't boot there, but that is fine.

The problem I have now is how to restore a MBR that will work without Linux's EXT3 partition?

---

### Post by LaRoza on 2008-01-29
> **Will Pittenger said:**
> At this point, I might as well delete the Linux partition.  I have another Linux partition (my first attempt) on my portable drive.  It won't boot there, but that is fine.

The problem I have now is how to restore a MBR that will work without Linux's EXT3 partition?

Download the Super Grub Disk and burn it, it can restore the Windows MBR easily.

(It is under: Advanced->Windows(Advanced) and is the first option)

---

### Post by Will Pittenger on 2008-01-30
For those reading this thread and wanting to download the Grub Super Disk, go [here]("http://supergrub.forjamari.linex.org/").  Note: You need to burn a CD, deal with an IMG file (I don't know what opens that under Windows), or open a tar.gz (which you probably need something to open in Windows).

---

### Post by LaRoza on 2008-01-30
> **Will Pittenger said:**
> For those reading this thread and wanting to download the Grub Super Disk, go [here]("http://supergrub.forjamari.linex.org/").  Note: You need to burn a CD, deal with an IMG file (I don't know what opens that under Windows), or open a tar.gz (which you probably need something to open in Windows).

Use 7-Zip [http://www.7-zip.org/](http://www.7-zip.org/)

(Oh, the link for the Super Grub Disk was in the link in my sig, forgot to say that)

---

### Post by Battie on 2008-01-31
If you hit F8 before Windows gets to the splash screen, you will get the startup menu.  Unless you haven't installed any updates, there will be an option to let you disable the automatic restart on system failure.

This time, when you reboot, you will be able to see the BSOD.  Sometimes these codes are not helpful, but sometimes they can point right to the problem.

---

### Post by Will Pittenger on 2008-02-02
I just did a clean from DiskPart.  I ran it from a BartPE LiveCD.  However, now PartitionMagic insists that my 250 GB drive is only 131 GB.  What can I do to fix that?

---

