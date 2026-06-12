---
title: "Hardware support (12.04) (Acer Revo RL100 network)"
date: 2012-05-09
forum: Testimonials &amp; Experiences
---

### Post by amalgamas on 2012-05-09
**Ubuntu 12.04 on the Acer Revo RL 100**
 

 I write this to show people what a hassle a linux install can be.  The reward when it succeeds, may be a wonderful working OS, but it can be a hard and thorny road.  Then, there is a question that has bothered me for a while.
 

 The Acer Revo RL 100 is a dedicated multimedia-PC and it has only HDMI video and audio output.  I bought it with the aim was to install XBMC and use it as network player and CD/DVD player in my home theater system.  It also has a flash-card slot and 3 USB slots.  It came with win7 which I never used.
 

 I tried openELEC, but could not get the network working.  It has the *Ralink* RT3090 for the wireless.  I ended up installing pinguy mini (a ubuntu derivate) because I used that on my laptop, and installed XBMC in pinguy.  This worked, but was not perfect, so when ubuntu 12.04 came about, I decided to reinstall.  I wanted to streamline, eliminate the grub splash, fix shutdown issue.
 

 First try was xbmcbuntu.  Almost impossible to install due to small and unreadable desktop font.  After some tinkering, i was able to install (with difficulties) only to see that the wireless did not work.  Googled and tried a lot of suggestions, but nothing worked.
 

 Next was ubuntu 12.04 mini (I like the new unity desktop).  It installed nicely, but no network.  Tried more suggestions, but could not get it working.
 

 Third try: full ubuntu 12.04 (ubuntu-12.04-desktop-amd64).  Same as the mini variant, no network.
 

 4.th try (after two weeks): reinstalled pinguy 11.04 mini with XBMC.  Now the network is working, but I am still trying to fix the shutdown issue, the age-old cifs shutdown bug.  Apart from that minor issue it seems to work perfectly: usb-slots, flash-cards, wireless touchpad/keyboard.   
 

 So my final question is: how is it possible that the latest ubuntu has a non-working network module, when an older ubuntu variant contains working network?  Has someone changed the working version for something that does not work?
 

 The Ralink adapter is rather common in a lot of laptops.  People who want to try ubuntu and experience such problems will be driven away from linux and won't get that pleasure of a great working OS.  The most important thing for newbies is that things work.  People at Canonical/ubuntu should take this seriously and fix this asap!

---

### Post by cariboo on 2012-05-09
It seems that you have a hardware problem that really has nothing to do with Ubuntu. Have a look at [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875659/comments/15") post on Launchpad.

Why not used an ethernet connection, as I've found that wireless doesn't do a good job of streaming media 100% of the time. I don't know if it's the phase of the moon, or how you hold your mouth, but I've had streaming working quite acceptably using a wireless device, when out of the blue it'll stop working, only to start working again the next day without a reboot, and no change to the source material or anything else.

---

### Post by amalgamas on 2012-05-10
> **cariboo907 said:**
> It seems that you have a hardware problem that really has nothing to do with Ubuntu. Have a look at [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875659/comments/15") post on Launchpad.

Why not used an ethernet connection, as I've found that wireless doesn't do a good job of streaming media 100% of the time. I don't know if it's the phase of the moon, or how you hold your mouth, but I've had streaming working quite acceptably using a wireless device, when out of the blue it'll stop working, only to start working again the next day without a reboot, and no change to the source material or anything else.


Not correct.  As the post states: "the network speed is horrible", this is no solution to the roblem.  But using the older ubuntu (pinguy 11.04) gives me a perfectly working network that does not change according to the phase of the moon.  And I have done that installation twice with the same result!

Conclusion: something has changed (to the worse) with the drivers in the ubuntu install ISO

---

### Post by mastablasta on 2012-05-10
> **amalgamas said:**
>  
Conclusion: something has changed (to the worse) with the drivers in the ubuntu install ISO
 
 
"problem" is that 12.04 uses new and fresh kernel. which seems to have chenged plenty of things. though the computer i installed it to works ok i have a hibernation/suspend problem (which seems to be a kernel bug). Ubuntu is not (directly) responsible for kernel. i you want something less bugy wait for 12.04.1 edition, use old stable (10.04.x) or use Debian (or one of it's derivatives).
 
addtionally Ubuntu now has certified hardware so that one should work nicely.
 
i hope this issue you have (and mine also) is fixed within next two months.
 
i guess no one tested it when it was in beta stage, saw this issue with Acer Revo RL and reported it...

---

### Post by amalgamas on 2012-05-11
> **mastablasta said:**
> "problem" is that 12.04 uses new and fresh kernel. which seems to have chenged plenty of things. though the computer i installed it to works ok i have a hibernation/suspend problem (which seems to be a kernel bug). Ubuntu is not (directly) responsible for kernel. i you want something less bugy wait for 12.04.1 edition, use old stable (10.04.x) or use Debian (or one of it's derivatives).
 
addtionally Ubuntu now has certified hardware so that one should work nicely.
 
i hope this issue you have (and mine also) is fixed within next two months.
 
i guess no one tested it when it was in beta stage, saw this issue with Acer Revo RL and reported it...


But it should not (ideally) change to the worse.  The network module or driver for the *Ralink* RT3090 works perfectly in the older version, so why do anything to it?  Mysterious.  Someone should explain how these things work to noobs like me

---

### Post by mastablasta on 2012-05-12
> **amalgamas said:**
> But it should not (ideally) change to the worse.  The network module or driver for the *Ralink* RT3090 works perfectly in the older version, so why do anything to it?  Mysterious.  Someone should explain how these things work to noobs like me

you are correct. it shouldn't.

it could be they did something not to it but to another driver that also changed (had an effect on this one) and since no one tested it and reported a bug there was no fix in time. i remember one week when all flash stopped working cause they "fixed" somethign on community graphics card driver. bug was reported that they messed up plenty of other card chips with that "fix". about 3 or 4 days later a fix was out for my card as well and all was working again as before. 

these things shouldn't happen in my opinion. 

on the other hand Ubuntu is based on debian testing. so to get a stable system where nothing lik this happens it is better to use RedHat or Debian. however that brings in other issues in desktop environments. in ubuntu to abvoid these kind of things one should use for example 12.04.1 editions to upgrade. staying on LTS for most of the time.

---

### Post by Tamlynmac on 2012-05-12
> mastablasta
you are correct. it shouldn't.
these things shouldn't happen in my opinion. 

Oh, be still. Are you suggesting backward compatibility - what's come over you mastablasta?
:lolflag:

---

### Post by mastablasta on 2012-05-13
it's not about backwards compatibility as it is about bugs that come with updates/upgrade. soemthign worked, but doesn't after update or upgrade. 

which is the reason why mint debian holds back the updates now. when they started at firts it was fun then new testing updates came and people started having problmes. something that works before shouldn't be broken in new version. or if it is (due to new features/imporvements it should be fixed before it gets to the users.

---

### Post by Tamlynmac on 2012-05-13
> mastablasta
it's not about backwards compatibility as it is about bugs that come  with updates/upgrade. soemthign worked, but doesn't after update or  upgrade. 

Regardless, of the bug or issue when a upgrade/update fails to  acknowledge the hardware of the previous release or performs poorly with  said hardware - I still see that as a failure to remain backward  compatible. Semantics. Deliberate or not, it still has the same impact. 

A new user wouldn't know the difference?  Only the user who upgraded/updated would see it as a backward  compatibility issue. It worked with the previous release or prior to updating and not with  the new release or after updating.

A bug or any other issue that interferes with upgrading/updating  shouldn't happen or at least rarely. It raises the question of why a  new version or update would be released if it had a known issue? Or, why at least a notification  didn't occur prior to the upgrade/update.

I do agree with you that patience might be a better solution.  Especially, if the upgrade/update is known to have an issue prior to  release. If it's unknown, then logic might suggest a commitment to  further testing before releasing any future upgrades/updates. Which, based on your feedback is what Mint does with updates.

Just my $0.02

---

