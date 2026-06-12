---
title: "I'm going to do a Dual Boot with XP, and I have a question"
date: 2007-02-16
forum: The Cafe
---

### Post by steven8 on 2007-02-16
This not a technical question, as such, since I've done dual boots with multiple Linux distros, however: I am going to take the plunge and create a dual boot with my main HDD, which is running WinXP Pro.  

I am more than willing to let gparted be in control and divy up the available space by itself, and I am not worried about having a fat32 partition for file sharing, so none of that is a problem.  My question is, how long will this take?  

I have 125gbs available on my hdd, so it'll be half that for ubuntu.

My XP is NTFS, and has the whole drive to itself right now.

I have a 1.2 ghz amd athlon and 768 mbs of ram, with a 52x cdrom, and I am going to set up Dapper.  

I have approximately 2 hrs in the morning to do this.  Will that be enough time?  I don't mean all the tweaking afterwards, but to the point where I can reboot and check it out.

Thanks!

---

### Post by yabbadabbadont on 2007-02-16
I wouldn't count on 2 hours being enough time.  Just in case you didn't already know this, you will want to completely defragment your ntfs partition prior to it being resized.  It just works better (and more reliably) that way.

---

### Post by steven8 on 2007-02-16
> **yabbadabbadont said:**
> I wouldn't count on 2 hours being enough time.  Just in case you didn't already know this, you will want to completely defragment your ntfs partition prior to it being resized.  It just works better (and more reliably) that way.

I knew I forgot something in my post.  I did my defrag last night.  If two hours isn't enough, then I'll wait until Saturday night, after everyones in bed.  Then I'll have all night to tinker!!

Thanks!

---

### Post by Elim on 2007-02-16
Well, it's good that you've already defragged.  I've heard it suggested before that you might want to defrag twice.  *shrug*

Also, why not just partition it yourself rather than take gparted's defaults?  I'd do 15 (perhaps 20) GB Windows, 10 (perhaps 15) GB Ubuntu, 1 GB swap, remaing as fat32.  It's not at all hard to do, and you might be happier than with gparted defaults (I don't know what those are).  Just my $0.02.

I don't think it will take long, though, two hours should be enough. :)

---

### Post by yabbadabbadont on 2007-02-16
It just depends upon how full his ntfs partition is.  The fuller it is, the longer it will take to resize.  However, it has been a long time since I resized (or even had) a ntfs partition, so I don't know how long it will take.  Better safe than sorry though.

---

### Post by steven8 on 2007-02-16
> **Elim said:**
> Well, it's good that you've already defragged.  I've heard it suggested before that you might want to defrag twice.  *shrug*

Also, why not just partition it yourself rather than take gparted's defaults?  I'd do 15 (perhaps 20) GB Windows, 10 (perhaps 15) GB Ubuntu, 1 GB swap, remaing as fat32.  It's not at all hard to do, and you might be happier than with gparted defaults (I don't know what those are).  Just my $0.02.

I don't think it will take long, though, two hours should be enough. :)

I've already got 15 gbs used for windows, and my wife wants to use windows.  She likes msn gams and stuff liek that.  She likes to install demo games and whatnot.  Sometimes she remembers to uninstall, sometimes not.  I want to leave her plenty of room.  We don't have much to worry about saving.  I have a few things I'll upload to web storage just in case.  I have no worries about xp geting borked, as I'll just reinstall if it does.

I have another question.  My usb cable modem works in Dapper, but not in Edgy or Feisty (so far, I submitted a note to the dev mailing list).  I have tried the livecd's of edgy and feisty, but I wonder. . .If I have a working install of Dapper, the do a dist upgrade via the web, do yo uthing my modem would continue working. . .or break?

---

### Post by yabbadabbadont on 2007-02-16
I would put my money on it breaking.  You said it doesn't work in Edgy or Feisty.  It doesn't matter how your system gets there, (installed from scratch or upgraded), it will be the same versions of software running in the end...

---

### Post by steven8 on 2007-02-16
> **yabbadabbadont said:**
> I would put my money on it breaking.  You said it doesn't work in Edgy or Feisty.  It doesn't matter how your system gets there, (installed from scratch or upgraded), it will be the same versions of software running in the end...

That's okay.  Dapper it is until I get some word from the devs (my note is still awaiting approval) that they are taking steps to improve the situation.

---

### Post by steven8 on 2007-02-18
It is done!! :-)  Ubuntu and WinXP Pro living together in harmony on my HDD.  XP was angry at first.  It made me run a disc check to ensure integrity, etc., then it made me reboot.  Then it told me it discovered some new piece of hardware (it never said what), installed the software for it, and made me reboot.  I have no idea what it was talking about, but it starts just fine now and everything runs okay.

Ubuntu had 219 updates for me.  Installed them all with no problems.  I only use the open NV driver for my card, so an update has never bothered my system and probably never will.  

I showed my wife how GRUB works and she's cool with that.  Thanks folks for your suggestions.  It's great to have finally done it.  I was quite tired of swapping cables to my spare HDD evertime I wanted to use Linux!!

---

### Post by Steveire on 2007-02-18
Did it take less than 2 hours?

---

### Post by steven8 on 2007-02-18
The actual partitioning and installation itself took about a half hour.  Not bad in my opinion.  It was the 216 updates that stretched it out.  They took over an hour.  All in all it took about 2 hrs.  I think that's pretty dang good!!

---

### Post by steven8 on 2007-02-19
I had to make a small change.  my wife complained that she had to reboot 3 times today because she kept forgetting to wait for GRUB at boot, and it kept throwing her into Ubuntu.  I changed the start-up delay to five minutes!!  That ought to give her enough time to remember.
:)

---

### Post by yabbadabbadont on 2007-02-19
> **steven8 said:**
> I had to make a small change.  my wife complained that she had to reboot 3 times today because she kept forgetting to wait for GRUB at boot, and it kept throwing her into Ubuntu.  I changed the start-up delay to five minutes!!  That ought to give her enough time to remember.
:)

Just change the default in /boot/grub/menu.lst to be the windows entry.  That way your wife doesn't have to remember to do anything.  (and I'm sure you won't get upset if you forget ;))

---

### Post by steven8 on 2007-02-19
> **yabbadabbadont said:**
> Just change the default in /boot/grub/menu.lst to be the windows entry.  That way your wife doesn't have to remember to do anything.  (and I'm sure you won't get upset if you forget ;))

You know, I sat there and sat, pondering over whether or not to make XP the default, but the idea of doing it repulsed me so!  She can scroll down.  :popcorn:

---

### Post by steven8 on 2007-02-23
I work at night, so I sleep during the day.  I got up this evening for dinner, and found my son sitting at the computer playing samegnome.  I asked my wife if ubuntu had started by accident, and she said, "No, I started it.  I figured I'd go in and try figure some of that stuff out."

This is the first step, my friends!!  We may eventually have a windows-free house!!  :)

---

### Post by Polygon on 2007-02-23
just remember, that if you ever have to reinstall windows for some reason, your going to have to reinstall grub as the windows reinstallation is going to wipe out the grub entry in the MBR.

---

### Post by steven8 on 2007-02-23
Funny you should mention that.  I was just thinking about that today.  Do we do that from the livecd, eh?  How do we do that?

---

