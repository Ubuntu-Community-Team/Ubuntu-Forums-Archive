---
title: "fs corrupting on 2 machines, one brand new"
date: 2009-07-21
forum: System76 Support
---

### Post by mike1212 on 2009-07-21
I've got a serval that's a couple years old.  Upgraded from 8.04 to 8.10 to 9.04 in one night.  Next 2 weeks began getting fsck checks on start, then the system wouldn't boot at all (booted to grub propt).  Ran live cd, copied all personal files from hard disk, reinstalled 9.04 from scratch.  Since then (1 week) no file system problems.  I did have a problem with Screem crashing every time I typed in text, seemed to have solved this by removing the nvdia graphics driver (not sure why this worked, but did have a problem with cursor not showing up when cursor moved over main screem window.

Anyway, just got my wife a new pangolin on july 10th.  It's now begining to show signs of same file system problems I had on mine.  It does the fsck check on startup and firefox freezes and I've had freezes when browsing folders with pictures in them (freezing meaning program turns grey and in not responsive to mouse clicks.

Now why would my new machine, only a couple weeks old, exhibit these simptoms?  Should I reinstall upbuntu?  My wife wanted something that "just works".  I had great luck with 8.04 and showed her the ubuntu website that claims the os "just works".

I've read the posts about a kernel bug.  Is fix I could attempt.

Thanks alot for any help/suggestions.

Mike

---

### Post by gila_monster on 2009-07-22
Hi, Mike.

Tom Aaron will probably have more intelligent things to say on this than I would. But we've been discussing this very problem in the S76 forum at [http://ubuntuforums.org/showthread.php?p=7656632](http://ubuntuforums.org/showthread.php?p=7656632). Are you able to get anything to boot long enough to find out what kernel you are using? Can you use grub to select an older kernel, or does it die before you get to that point?

---

### Post by mike1212 on 2009-07-22
Thanks, I'll ad a reply to that forum.

my older serval is now using 2.6.28-13, after the fresh install and has had no problems for a week (except for a problem with the nvdia driver).  I'm not sure what kernelversion I had when it crashed after the upgrade.

the new pangolin also is using 2.6.28-13 and it is showing signs of having problems (programs freezes/crashes and fsck's on startup).  I've disabled the nvdia driver because that solved a problem on my other machine.

what am I losing by diabling the nvdia driver?  everything seems to still work the same as it did when it was enabled.  I'm sure I won't be able to use any desktop effects, but for now I'd just like to know i can boot and run my programs.

thanks

---

### Post by gila_monster on 2009-07-22
> **mike1212 said:**
> what am I losing by diabling the nvdia driver?  everything seems to still work the same as it did when it was enabled.  I'm sure I won't be able to use any desktop effects, but for now I'd just like to know i can boot and run my programs.

thanks


Basically just the 3D special effects goodness. The system should be quite happy to run without the driver.

Using -13...the mystery deepens. Works for some, not for others. Gotta love those kinds of problems.

---

### Post by mike1212 on 2009-07-22
just to note, i've disabled the nvdia driver on both machines (they were using version 180) and haven't had any problems since.  It's only been 2 days, but so far, so good.  I'll report any changes.

---

### Post by mike1212 on 2009-07-24
yeah, so the pangolin was good for a few days after disabling the nvdia driver, but is having problems now.  I've got the fsck on 2 of the last 4 boots.  After fixing everything with fsck, the system boots fine.  I have a feeling I won't be booting soon.  

I'm thinking a fresh ubuntu install?  My serval has been good after the new install.  Any thoughts?

thanks

---

### Post by thomasaaron on 2009-07-27
Let me know if it messes up again. Fsck will automatically run every twenty-something boots.

I'm starting to see this problem happen on some of the older Servals and Pangolins. From what I can tell, heavy file transfers seem to exacerbate it, which may be why I'm not seeing a whole lot of the bug (most people don't do regurlar heavy file transfers). Hopefully this ridiculous bug isn't hitting the new pangolins too.

---

### Post by gila_monster on 2009-07-27
> **thomasaaron said:**
> Let me know if it messes up again. Fsck will automatically run every twenty-something boots.

I'm starting to see this problem happen on some of the older Servals and Pangolins. From what I can tell, heavy file transfers seem to exacerbate it, which may be why I'm not seeing a whole lot of the bug (most people don't do regurlar heavy file transfers). Hopefully this ridiculous bug isn't hitting the new pangolins too.

Tom, can you define "old" and "new" here? I have a panp4n that I purchase last September/October. Is that old or new?

I installed Kubuntu on Friday just to see if some of my issues were related to GNOME rather than Ubuntu. Seeing some of the same things (like the processor running at 20-30% all the time). Currently using the 2.6.29 kernel, so I'm not seeing any of the myriad issues reported with 2.6.28. Using the 180.44 nVidia driver, and not seeing the technicolor barf problem. But I do get occasional freezes, which thus far seem temporary.

I am actually considering a vanilla Debian installation as further exploration. It seems prudent to try that on the backup laptop (a Gateway, sadly with Intel graphics) rather than taking the immediate plunge with the Pangolin. I'll report back when I have more data.

Yeah, I know you guys don't support Kubuntu or XFCE or Debian or left-handed Rastafarian OSes. I'm going to see if I can learn something anyway.

---

### Post by thomasaaron on 2009-07-27
Yeah, when I say "old," I'm referring to the Pangolin version 3 and the Serval version 4. They were based on a different mobo. The PanP4 and PanP5 are also very similar. They are the newest iteration.

It's kind of hard to keep track of, and I need to remember that recent customers don't necessarily have the 50,000 foot view on the models we've produced. I'll try to do better at that.

---

### Post by jdb on 2009-07-27
> **gila_monster said:**
> Tom, can you define "old" and "new" here? I have a panp4n that I purchase last September/October. Is that old or new?

I installed Kubuntu on Friday just to see if some of my issues were related to GNOME rather than Ubuntu. Seeing some of the same things (like the processor running at 20-30% all the time). Currently using the 2.6.29 kernel, so I'm not seeing any of the myriad issues reported with 2.6.28. Using the 180.44 nVidia driver, and not seeing the technicolor barf problem. But I do get occasional freezes, which thus far seem temporary.

I am actually considering a vanilla Debian installation as further exploration. It seems prudent to try that on the backup laptop (a Gateway, sadly with Intel graphics) rather than taking the immediate plunge with the Pangolin. I'll report back when I have more data.

Yeah, I know you guys don't support Kubuntu or XFCE or Debian or left-handed Rastafarian OSes. I'm going to see if I can learn something anyway.

If you can make room on your disk for another partition, 10 gig should be plenty, you can install Debian on it & have a dual boot machine.

Most of my machines are quadrupal boot or more :)

jdb

---

### Post by gila_monster on 2009-07-27
> **jdb said:**
> If you can make room on your disk for another partition, 10 gig should be plenty, you can install Debian on it & have a dual boot machine.

Most of my machines are quadrupal boot or more :)

jdb

Understood. I've had dual-boot boxen in the past. I'm just not that fond of it in general.

I note you are using Xubuntu Jaunty. How is that working for you? I used Xubuntu on the smaller laptop for a number of years because it didn't have a lot of firepower.

---

### Post by jdb on 2009-07-27
> **gila_monster said:**
> Understood. I've had dual-boot boxen in the past. I'm just not that fond of it in general.

I note you are using Xubuntu Jaunty. How is that working for you? I used Xubuntu on the smaller laptop for a number of years because it didn't have a lot of firepower.

I like the xfce2 desktop Xubuntu uses, it has less overhead than gnome.
It just seems that xfce doesn't get in my way.
I don't use it much anymore though, I just like to keep track of whats going on in Ubuntu.

My working distro is Archlinux & my favorite desktop is fluxbox.
It takes a little while to learn how to configure Archlinux, when you first install it all you have is a root shell prompt, no other users and no desktop.
There are no gui configurations, all configuration is done by editing files.
That's the bad news.

The good news is there is plenty of online help and good wikis.
The application manager (pacman) is fantasitc.
There are packages for KDE, Gnome or about anything else a person might like.
Configurations are simple once you get the hang of it and you never find yourself wondering what some automatic gui configuration just did to your machine.
Another nicety is rolling updates.
There are no version upgrades of the Arch distro.
Applications & kernels are released continuously, the Archlinux packages lag the applications by about 2 weeks.
I do updates every couple weeks & the one I did today loaded kernel 2.6.30.2-1.

jdb

---

### Post by glacialfury on 2009-08-04
I've been dealing with the filesystem corruption for awhile now; initially I was directed at tracker as the probable cause, but I'm not so sure, since I thought tracker was not enabled by default in a clean install.  I saw the corruption problem on a brand new Kubuntu 9.04 64bit installation within a few days.  

I'm using a serp4.  

I had the same problem in Ubuntu.  If it's a kernel problem, maybe we can use an older kernel, but for now the *easiest* fix - annoying, but easy - might be installing 8.04 or 8.10, which didn't seem to suffer from it.

---

### Post by jdb on 2009-08-04
> **glacialfury said:**
> I've been dealing with the filesystem corruption for awhile now; initially I was directed at tracker as the probable cause, but I'm not so sure, since I thought tracker was not enabled by default in a clean install.  I saw the corruption problem on a brand new Kubuntu 9.04 64bit installation within a few days.  

I'm using a serp4.  

I had the same problem in Ubuntu.  If it's a kernel problem, maybe we can use an older kernel, but for now the *easiest* fix - annoying, but easy - might be installing 8.04 or 8.10, which didn't seem to suffer from it.

I think the bug is only in the 64 bit kernel so if you have less than 3 GB of ram a 32 bit version is another option.

jdb

---

### Post by glacialfury on 2009-08-05
Swapping to a different kernel, as outlined in the bug report, seems to have fixed the problem for me.

---

### Post by thomasaaron on 2009-08-05
glacialfury, what kernel did you switch to?

---

