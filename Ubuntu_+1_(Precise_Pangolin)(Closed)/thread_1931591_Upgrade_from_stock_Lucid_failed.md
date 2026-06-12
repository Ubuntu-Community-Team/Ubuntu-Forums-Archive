---
title: "Upgrade from stock Lucid failed"
date: 2012-02-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by NHclimber on 2012-02-25
On Pentium-M laptop (ie, non-pae), upgrading to Precise from just-installed, just-formatted, completely stock Lucid install -- upgrade completes but no kernel was installed.

As this is one of the dwindlingly few intended methods of installing Precise on non-pae machine, I thought it worthy of mention.

Note: I had not originally intended to test the upgrade from a completely fresh install of Lucid, as the machine had a Lucid install on it already that was somewhat customized but not terribly important. Unfortunately, I could not get the Precise upgrade to get past a dependency check on xserver-xorg-core (which wasn't custom) and I couldn't figure out what was pinning the wrong version.

---

### Post by ranch hand on 2012-02-25
No need to jump my butt about this not being the "supported" way of upgrading.

I had similar problems early in the cycle (for this upgrade this is early) of 10.04-testing getting 8.04 to upgrade.  I used apt-get and manually upgraded.  Worked.

You need to run;
```

sudo dpkg --configure -a

```
several times to get to the point where the remaining errors are identical a couple of times.

The boot to recovery and do the same command again.

Have no idea if it would work this cycle at all.  If you feel like playing with it just remember to have FUN.

---

### Post by NHclimber on 2012-02-25
> **ranch hand said:**
> You need to run;
```

sudo dpkg --configure -a

```several times to get to the point where the remaining errors are identical a couple of times.

The boot to recovery and do the same command again.

Have no idea if it would work this cycle at all.  If you feel like playing with it just remember to have FUN.

That's what I tried doing originally when the upgrade wouldn't budge past the weird dependency.

Of course, now that wouldn't work because there is no valid installation: the 2.6.32 Lucid kernel that didn't get replaced is not going to run all the new Precise packages that did get replaced.

Thanks anyway though. I'm about to see if installing fresh from Oneiric and upgrading from there will work... stay tuned :)

---

### Post by NHclimber on 2012-02-25
> **NHclimber said:**
> I'm about to see if installing fresh from Oneiric and upgrading from there will work... stay tuned :)

Well, I was able to upgrade Precise from Oneiric but it wasn't exactly a success.  Total install time was a little over 4 hours :(  That includes:
downloading oneiric iso = 10 min.
burning iso (at 8x speed because I have enough coasters already) = 10 min.
installing oneiric = just under an hour
updating oneiric = a while
upgrading to precise = painfully long (even after downloading, the install alone took more than 90 mins.)

---

### Post by prusswan on 2012-02-26
perhaps the hardware is just too old for a proper install experience. Also by stock lucid are you referring to 10.04.3 or really the very first 10.04?

---

### Post by NHclimber on 2012-02-26
> **prusswan said:**
> perhaps the hardware is just too old for a proper install experience.

What's with the enforced obsolescence?

The majority of the Linux kernel predates this laptop. It has no difficulty running what I need it to run, and it installed Lucid from CD in under 30 mins -- why should the Precise install take 8x longer?

This really stems from the decision to use the PAE kernel for the Live CD -- which in my opinion unnecessarily jettisons a substantial user base (well, at least, more substantial than those using the TI -omap flavour or even 32-bit PowerPC :)

> **prusswan said:**
> Also by stock lucid are you referring to 10.04.3 or really the very first 10.04?

By "stock Lucid", I mean currently available download iso - which is 10.04.4

---

### Post by sudodus on 2012-02-26
> **NHclimber said:**
> Well, I was able to upgrade Precise from Oneiric but it wasn't exactly a success.  Total install time was a little over 4 hours :(  That includes:
downloading oneiric iso = 10 min.
burning iso (at 8x speed because I have enough coasters already) = 10 min.
installing oneiric = just under an hour
updating oneiric = a while
upgrading to precise = painfully long (even after downloading, the install alone took more than 90 mins.)
I have a Pentium-M laptop, so this is interesting for me too.

- The update was slow, but does the computer work as it should afterwards?

- I guess you have also tried fresh install to Precise. How does that work on a Pentium-M laptop?

- Do you know if the same kernel is used also by Xubuntu and Lubuntu?

---

### Post by dino99 on 2012-02-26
Of course testing dist-upgrade is usefull to find buggy stuff. But doing a fresh install is surely the best decision to avoid such borked transitional config packages, broken symlinks left behind and all kind of crappy things. That way you can also format the partition with the latest gparted/partedmagic to get a clean partition (remember that parted/gparted is also a software and have bugs :()

And if your web link is fast (even if it is not anyway) , instead of burning cd/dvd, you can use either:
- usb stick with unetbootin and the full iso
- the mini.iso installation :  [http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/)

Remember to deactivate everything that can disturbate an installation before starting it, like screensaver, cronjob, suspend/hibernate, ...

---

### Post by NHclimber on 2012-02-26
> **sudodus said:**
> The update was slow, but does the computer work as it should afterwards?

About as well as it did before. I haven't checked the required checklist items though - suspend, hibernate, etc.  In my experience, the power management is the least stable kernel area. That and bluetooth :p

> **sudodus said:**
> I guess you have also tried fresh install to Precise. How does that work on a Pentium-M laptop?

Fresh install to Precise for Pentium-M laptops is **not possible** - that's the whole painful reason for having to upgrade (I'd much rather slap in a CD and be done in 30 mins, that's for sure).

It's been ruled out as 'Won't fix' -- see here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447)

Feel free to mark that bug as 'It affects me too" ;)

> **sudodus said:**
> Do you know if the same kernel is used also by Xubuntu and Lubuntu?

I have no idea about Xubuntu - sorry.  I read somewhere that Lubuntu is dropping the non-pae kernel altogether, but it seems that at least some have managed to get the Lubuntu pae kernel running on non-pae hardware (see comment #36 in above bug report).

---

### Post by sudodus on 2012-02-26
> **NHclimber said:**
> About as well as it did before. I haven't checked the required checklist items though - suspend, hibernate, etc.  In my experience, the power management is the least stable kernel area. That and bluetooth :p



Fresh install to Precise for Pentium-M laptops is **not possible** - that's the whole painful reason for having to upgrade (I'd much rather slap in a CD and be done in 30 mins, that's for sure).

It's been ruled out as 'Won't fix' -- see here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447)

Feel free to mark that bug as 'It affects me too" ;)



I have no idea about Xubuntu - sorry.  I read somewhere that Lubuntu is dropping the non-pae kernel altogether, but it seems that at least some have managed to get the Lubuntu pae kernel running on non-pae hardware (see comment #36 in above bug report).
Thank you. I read that launchpad thread, also about Jerry Lamos's tests with Lubuntu.

---

### Post by cariboo on 2012-02-26
Does anyone know if using the alternate install iso installs a non-pae kernel?

---

### Post by NHclimber on 2012-02-26
> **dino99 said:**
> Of course testing dist-upgrade is usefull to find buggy stuff. But doing a fresh install is surely the best decision to avoid such borked transitional config packages, broken symlinks left behind and all kind of crappy things. That way you can also format the partition with the latest gparted/partedmagic to get a clean partition (remember that parted/gparted is also a software and have bugs :()

Agreed. Upgrading is the least sound method of installing a distribution and a source of endless frustration with weird and unforeseen side-effects. Can't wait to file bugs against Precise when the follow-up will invariably be "Have you tried this with a fresh install?" and I get to reply "Can't"...

> **dino99 said:**
> And if your web link is fast (even if it is not anyway) , instead of burning cd/dvd, you can use either:
- usb stick with unetbootin and the full iso
- the mini.iso installation :  [http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/)


Have you actually tried this for non-pae hardware? It doesn't seem like others have had good luck there and may actually be giving up.  [http://ubuntuforums.org/showthread.php?t=1924455&page=7](http://ubuntuforums.org/showthread.php?t=1924455&page=7)

---

### Post by dino99 on 2012-02-26
to check if your kernel  is pae compatible:  cat /proc/cpuinfo | grep -i PAE

about installing mini.iso (non pae), several threads are around, latest is Lubuntu

---

### Post by NHclimber on 2012-02-26
> **cariboo907 said:**
> Does anyone know if using the alternate install iso installs a non-pae kernel?

I'm efforting that right now.

---

### Post by NHclimber on 2012-02-26
> **dino99 said:**
> to check if your kernel  is pae compatible:  cat /proc/cpuinfo | grep -i PAE

I already knew this laptop CPU wasn't pae-capable. But that brings up an interesting point: where exactly is a user supposed to input that command line if the Live CD won't boot because it uses a pae kernel?

Besides, users that have hardware that doesn't support pae are going to know that right away when they try to boot the Precise Live CD and they get this:
```
This kernel requires the following features not present on the CPU:
pae
Unable to boot - please use a kernel appropriate for your CPU.

```

I just thought of a conundrum: how can non-pae hardware be 'supported' in Precise if some earlier distribution level is required to fix it?  For example, what's the SOP methodology for rescuing a partition if grub rescue is insufficient? Boot using the Lucid Live CD?

---

### Post by NHclimber on 2012-02-26
> **cariboo907 said:**
> Does anyone know if using the alternate install iso installs a non-pae kernel?

The alternate iso [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/) uses the pae kernel to boot -- ie, after selectiing 'Install Ubuntu', non-pae hardware will halt with the same message above.

The irony is not lost on me. The alternate install CD page specifically states: "installs on systems with less than about 384MiB of RAM" - not really much use for pae on those systems :D  (I know it's really about NX but couldn't resist being just-a-little-bit-snide -- sorry)

---

### Post by prusswan on 2012-02-26
Lynx forever sounds good to me for a Pentium-M with 384 MB, even if the install works Precise will definitely be slower than Lynx

---

### Post by kansasnoob on 2012-02-26
> **cariboo907 said:**
> Does anyone know if using the alternate install iso installs a non-pae kernel?

DUH! Quick edit, not reading straight!

The alt image does install PAE!

---

### Post by kansasnoob on 2012-02-26
I posted a bit here at Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/42](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/42)

> @ Peter Hurley and all concerned,

I'm not sure what could have gone wrong. I have no hardware that actually requires a non-pae kernel but I performed upgrade tests from desktop versions of both Oneiric and Lucid today and both remained non-pae. I simply used the command "update-manager -d -c" in both instances.

The Lucid was a fresh install of 10.04.4 and naturally began with an insignificant number of updates to Lucid itself before proceeding with the dist-upgrade, but all went well afterward. I did however file a bug report about wording of one of the dialogue prompts ....... minor, but I'm a whiner.

The Oneiric install was naturally a different story, still a fresh install but it wanted 341 updates before proceeding with the upgrade, so I edited the software sources to require only "important security updates" and reloaded which brought the requirement down to only 81 updates. Then a restart was required, following that I once again ran "update-manager -d -c" and the dist-upgrade completed just fine.

Note: Once Precise Beta 1 is released, or actually after each milestone release, you'd then want to drop the "-c" and rather just use the command "update-manager -d", but right now that would only give me Alpha 2 which was quite buggy for me, and it would of course require a sled load of updates.

I've never done any server work so I'm not sure how the procedure for the server edition might vary.

Testing is still ongoing with the non-pae mini.iso as I've requested some changes to 'tasksel'. I may not get around to retesting the mini.iso for nearly a week though.

I hope this might be helpful to someone.


So, exactly what method did you use?

---

### Post by NHclimber on 2012-02-27
> **kansasnoob said:**
> So, exactly what method did you use?

Which time??  ](*,)

Beginning from somewhat custom Lucid distribution (which had been upgraded from Jaunty):

Attempt #1) Downloaded Precise i386 daily iso and burned to CD; wouldn't boot because pae kernel on Live CD won't boot on non-pae hardware. Spent several hours getting up to speed on the fubar situation re: Precise default kernel.

Attempt #2) Upgrade with 'update-manager -d -c'; failed while building dependency tree -- had selected lucid version of xserver-xorg-core; claimed that held package was likely; could not find any held packages and really couldn't remember what packages I might have customized/rebuilt/re-versioned.

Attempt #3) Manual upgrade method via dist-upgrade/dpkg --configure -a repeatedly. Initially same failure as #2. Eventually bunch of broken packages that I have no interest in unwinding.

Attempt #4) Download Lucid iso and burn to CD; burn speed too high; laptop LEDs just blinking on initial boot.

Attempt #5) Burn Lucid iso to CD; burn speed too high; failure to file read error while copying.

Attempt #6) Breathe deeply and slow down; realize that simple process has been made infinitely more complex by factors beyond my control; lowest burn speed; install Lucid 10.04.4 -- manual partitioning, select existing 28 gb ext4 partition as '/' mount and check format.  Install completes; at initial boot, upgrade via 'update-manager -d -c'. So tired; go eat dinner. Come back and realize that upgrade is not fully automated; babysit upgrade, selecting yes whenever services need to be restarted :roll:  Upgrade finishes; hit 'Restart now', reboots. Only available grub kernel selection is 'Ubuntu 2.6.32-38-generic' (ie., Lucid 10.04.4 kernel) and its recovery complement. Boot to that kernel anyway expecting to not get very far because Lucid kernel is not going to boot Precise packages; disappointed to see that I'm right again -- boot completely stalled on blank screen with flashing cursor.

Attempt #7 and success #1) Download Oneiric iso and burn to CD; lowest burn speed -- lesson learned; install Oneiric -- manual partitioning, select existing 28 gb ext4 partition as '/' mount and check format. Install completes; at initial boot, upgrade via 'update-manager -d -c'. 248MB of updates required :confused:  Sit through epic update cycle, knowing the moment I walk away it will want user response. Push through and am rewarded with grub 'Ubuntu 3.2.0-15-generic' kernel.  YES!!

Attempt #8 and success #2) Wondering if I did something wrong with clean install attempt from Lucid; install Lucid again from same CD -- manual partitioning, select existing 28gb .... Install completes; at initial boot, upgrade via 'update-manager -d -c'. Sit through trivial update cycle. Reboot and am rewarded with 'Ubuntu 3.2.0-15-generic' kernel. 1 for 2, or 50% success rate from Lucid.

Attempt #9) Asked if 'alternate install i386 iso' -- presumably because that install is designed to work with minimum memory systems. Same outcome as attempt #1 -- won't boot because it uses the pae kernel.

Having decided that 2 solid days is enough time invested in over-complicated-by-design install of Precise, quit testing of install process.

Login to Ubuntu Classic and immediately realize that absolutely no bugs have been fixed in Ambiance theme or unico engine, despite month-old patches already in Launchpad.

Get first follow-up email to bug #789352 reported in May, regarding Natty panel keyboard navigation broken with compiz; bug has been marked duplicate of #228343, but its been marked invalid due to age. Laugh; reply to email asking why, with detailed repro steps, has this bug been marked invalid? Response is 'Platform too old; have you tested with Precise?" =D>

Need to get back to what I was doing before -- finish tty & console driver over firewire so kernel debugging can evolve past printk and static analysis. Which, by the way, is exactly what old laptops are still good for since most have iLINK/S.400/Firewire ports and can easily run gdb inside emacs.

---

### Post by kansasnoob on 2012-02-28
> **NHclimber said:**
> Which time??  ](*,)

Beginning from somewhat custom Lucid distribution (which had been upgraded from Jaunty):

Attempt #1) Downloaded Precise i386 daily iso and burned to CD; wouldn't boot because pae kernel on Live CD won't boot on non-pae hardware. Spent several hours getting up to speed on the fubar situation re: Precise default kernel.

Attempt #2) Upgrade with 'update-manager -d -c'; failed while building dependency tree -- had selected lucid version of xserver-xorg-core; claimed that held package was likely; could not find any held packages and really couldn't remember what packages I might have customized/rebuilt/re-versioned.

Attempt #3) Manual upgrade method via dist-upgrade/dpkg --configure -a repeatedly. Initially same failure as #2. Eventually bunch of broken packages that I have no interest in unwinding.

Attempt #4) Download Lucid iso and burn to CD; burn speed too high; laptop LEDs just blinking on initial boot.

Attempt #5) Burn Lucid iso to CD; burn speed too high; failure to file read error while copying.

Attempt #6) Breathe deeply and slow down; realize that simple process has been made infinitely more complex by factors beyond my control; lowest burn speed; install Lucid 10.04.4 -- manual partitioning, select existing 28 gb ext4 partition as '/' mount and check format.  Install completes; at initial boot, upgrade via 'update-manager -d -c'. So tired; go eat dinner. Come back and realize that upgrade is not fully automated; babysit upgrade, selecting yes whenever services need to be restarted :roll:  Upgrade finishes; hit 'Restart now', reboots. Only available grub kernel selection is 'Ubuntu 2.6.32-38-generic' (ie., Lucid 10.04.4 kernel) and its recovery complement. Boot to that kernel anyway expecting to not get very far because Lucid kernel is not going to boot Precise packages; disappointed to see that I'm right again -- boot completely stalled on blank screen with flashing cursor.

Attempt #7 and success #1) Download Oneiric iso and burn to CD; lowest burn speed -- lesson learned; install Oneiric -- manual partitioning, select existing 28 gb ext4 partition as '/' mount and check format. Install completes; at initial boot, upgrade via 'update-manager -d -c'. 248MB of updates required :confused:  Sit through epic update cycle, knowing the moment I walk away it will want user response. Push through and am rewarded with grub 'Ubuntu 3.2.0-15-generic' kernel.  YES!!

Attempt #8 and success #2) Wondering if I did something wrong with clean install attempt from Lucid; install Lucid again from same CD -- manual partitioning, select existing 28gb .... Install completes; at initial boot, upgrade via 'update-manager -d -c'. Sit through trivial update cycle. Reboot and am rewarded with 'Ubuntu 3.2.0-15-generic' kernel. 1 for 2, or 50% success rate from Lucid.

Attempt #9) Asked if 'alternate install i386 iso' -- presumably because that install is designed to work with minimum memory systems. Same outcome as attempt #1 -- won't boot because it uses the pae kernel.

Having decided that 2 solid days is enough time invested in over-complicated-by-design install of Precise, quit testing of install process.

Login to Ubuntu Classic and immediately realize that absolutely no bugs have been fixed in Ambiance theme or unico engine, despite month-old patches already in Launchpad.

Get first follow-up email to bug #789352 reported in May, regarding Natty panel keyboard navigation broken with compiz; bug has been marked duplicate of #228343, but its been marked invalid due to age. Laugh; reply to email asking why, with detailed repro steps, has this bug been marked invalid? Response is 'Platform too old; have you tested with Precise?" =D>

Need to get back to what I was doing before -- finish tty & console driver over firewire so kernel debugging can evolve past printk and static analysis. Which, by the way, is exactly what old laptops are still good for since most have iLINK/S.400/Firewire ports and can easily run gdb inside emacs.

Clearly I was asking about the failed Lucid -> Precise upgrade since that was the OP topic.

But then you did have one Oneiric -> Precise & one Lucid -> Precise upgrade pass, eh :)

Why the other Lucid -> Precise upgrade failed I'm clueless. I realize it's a pain in the neck to file a bug report against a non-bootable system but w/o doing so no one can figure out what blew up :(

I'm only trying to be helpful ;)

---

### Post by NHclimber on 2012-02-29
> **kansasnoob said:**
> I'm only trying to be helpful :wink:

I'm sorry that you felt that any of my earlier frustration was directed at you. It wasn't, but I feel bad you felt that way. Truly sorry.

> **kansasnoob said:**
> But then you did have one Oneiric -> Precise & one Lucid -> Precise upgrade pass, eh :)

:D  Yep. 


> **kansasnoob said:**
> Why the other Lucid -> Precise upgrade failed I'm clueless. I realize it's a pain in the neck to file a bug report against a non-bootable system but w/o doing so no one can figure out what blew up :(

Filed the bug report anyway but logs are history, so it's basically impossible to find out what happened anyway.

---

### Post by ranch hand on 2012-02-29
The bug report gives your hardware, at least I hope you included that, and the fact that the upgrade failed.  This is important data for the devs working on the upgrade 10.04>12.04.

Could be caused by something in 10.04.   Or 12.04.  Or both.

That is not the job of the tester.  The devs can't even start to look for it if they do not know.  That is the testers job.  Let them know.

You did just what you needed to do,

---

### Post by bubbajunk on 2012-03-01
Hey there NHclimber, I gotta hand it to you. You have alot more patience and persistence that I have. I am the one who filed the bug report you referred to earlier: "It's been ruled out as 'Won't fix' -- see here: https://bugs.launchpad.net/ubuntu/+s...ux/+bug/930447". 

I too stumbled into this mess by chance after thinking I had a little free time on my hands and I wanted to play around with a 12.04 live usb. Like you, I found out that I have non-PAE hardware. I didn't even know what PAE was before this build came around. I too spent hours reading threads trying to figure out what the devs mean when they say they will not drop "support" for non-PAE until 12.10. Still scratching my head to figure out their interpretation of the word "support". 

I consider myself more technical than the average person and I can tell you, that if I'm confused, then the vast majority of the casual Ubuntu crowd will definitely be confused. 

I don't like the idea of the upgrade option at all. Even if you say it is working after 1-1/2 to 2 hours. I'd always be skeptical that something that wasn't working correctly was due to the upgrade vs. fresh install. I've done fresh installs since 10.04 on my Thinkpad T42 Pentium M laptop without issue until now. I guess I'm holding out hope that installing from the mini.iso (non-pae) will be the closest thing to a clean install, and that it will work. 

Not sure where I'm going with this, but just to say hats off to you for all of the testing you've done so far, and I'm 100% with you that a machine that runs 11.10 without issue is all of the sudden obsolete in 12.04.

---

### Post by ranch hand on 2012-03-02
I believe the alt install disk also will install either kernel.

---

### Post by NHclimber on 2012-03-02
> **ranch hand said:**
> I believe the alt install disk also will install either kernel.

Although it might *install* either kernel, the alternate install i386 iso will *not* boot on non-pae hardware.  This is because it boots the pae kernel itself. :(

---

### Post by kansasnoob on 2012-03-02
> **ranch hand said:**
> I believe the alt install disk also will install either kernel.

No, it won't!

---

### Post by kansasnoob on 2012-03-02
When everyone else complains I actually advocate for change:

[https://lists.launchpad.net/unity-design/msg08539.html](https://lists.launchpad.net/unity-design/msg08539.html)

> Sorry, I don't blog but I hang out a lot at Ubuntu forums, really a lot!

While I find the current Ubuntu/Unity quite pleasant I think we have one unrelated problem that needs some additional thought.

Around mid-December it was decided by the UTB that support will continue for the non-PAE kernel option until the Ubuntu 
12.10 release, so there would be support in Ubuntu 12.04 LTS. 

But the 
default i386 kernel in Ubuntu 12.04 LTS became the PAE-enabled 
kernel and the only options to keep those old Pentium M's running becomes installation from the non-pae mini.iso or upgrades from Lucid or Oneiric. Is that truly "support"? 

Regarding the aforementioned UTB meeting the minutes show that Colin said something to the effect that we could "revert if it causes too much fallout". I believe that "fallout" is apparent enough to require defaulting to the non-pae kernel.

I personally have no effected hardware, everything I have can run the PAE kernel just fine, but when no one else will speak up I try to be the guy that will.

Apologies in advance if I'm only being a nuisance. Since this doesn't directly effect me I truly questioned the value of even saying anything.


I hope you all realize I'm using up my karma!!!!!!!!!

---

### Post by kansasnoob on 2012-03-02
Just BTW I was perfectly happy until I saw this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/945053](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/945053)

And notice the:

> bot-stop-nagging 

tag!!!!!!!!!!!!!

Yeah, really, stop nagging?????????????

Ha, ha!!!!!!!!!!!!!!!

Explain your decisions to the boss!

---

### Post by cariboo on 2012-03-02
> **kansasnoob said:**
> Just BTW I was perfectly happy until I saw this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/945053](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/945053)

And notice the:



tag!!!!!!!!!!!!!

Yeah, really, stop nagging?????????????

Ha, ha!!!!!!!!!!!!!!!

Explain your decisions to the boss!

That wasn't aimed at you, when I had my atom+kernel problem, the bot would mark the bug unconfirmed every time a new kernel was about to be released, and suggest we try the new kernel and if it didn't solve the problem, to mark it confirmed again. This happened about 4 times before I got tired of the nagging, and solved the problem on my own. Even though the posts were signed by Brad Figg, it is a canned message, and I see the same post in the bug you linked to. I think all of use with kernel bugs are getting tired of the canned response.

---

### Post by kansasnoob on 2012-03-02
> **cariboo907 said:**
> That wasn't aimed at you, when I had my atom+kernel problem, the bot would mark the bug unconfirmed every time a new kernel was about to be released, and suggest we try the new kernel and if it didn't solve the problem, to mark it confirmed again. This happened about 4 times before I got tired of the nagging, and solved the problem on my own. Even though the posts were signed by Brad Figg, it is a canned message, and I see the same post in the bug you linked to. I think all of use with kernel bugs are getting tired of the canned response.

I know that. I didn't even file that bug report, but it's apparent that none of the devs are going to listen. So I pulled out all of the stops :D

Turn and burn until the motor blows :guitar:

Although I'd rather have saved the NOx for another day ;)

Old gear heads never die, their nuts just get twisted the wrong direction.

---

### Post by Irihapeti on 2012-03-03
If you are looking for an option that should work, and isn't an upgrade, there is [https://help.ubuntu.com/community/Installation/FromLinux#Without_CD](https://help.ubuntu.com/community/Installation/FromLinux#Without_CD)

I've done this a few times on my EeePC because I'm too lazy to write an ISO to a USB stick. :)

It involves installing from an existing system, which gets around the issue of not being able to boot an install CD. It describes partitioning using command-line tools but that's not necessary - graphical tools work fine.

The kernel is installed separately, after the basic minimal system has been installed. Then add ubuntu-desktop or whatever is wanted.

Of course, it's not for the beginner or the faint-hearted, and doesn't solve the original problem of having a non-pae install disk.

---

