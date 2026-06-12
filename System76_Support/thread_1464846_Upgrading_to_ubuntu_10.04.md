---
title: "Upgrading to ubuntu 10.04"
date: 2010-04-28
forum: System76 Support
---

### Post by thomasaaron on 2010-04-28
[CENTER][SIZE="6"]GOOD MORNING SYSTEM76-ers! 
It's Release Day![/SIZE][/CENTER]

System76 Customers are clear to upgrade as soon as the official release is put online.

**A couple of important notes:**

1. **In the past two releases, we saw large quantities of corrupted upgrades** due to Ubuntu's servers being overrun with early adopters. We would ***advise*** you to wait a week or so before doing the online upgrade. There are two advantages to waiting: First, you are less likely to experience a corrupted upgrade; and second, any bugs that were missed in initial testing most likely will be squashed in a week or two.

If you choose to go ahead and do the online upgrade, **please ensure you are well backed up**. If your upgrade is corrupted, we most likely will recommend a fresh installation.

2. **If you want to do a fresh install, there is no need to wait.** However, it is a good idea to double-check both your image and your burned CD to make sure there is no corruption.

3. **There are a few bugs you have reported to us, which we've not been able to isolate in the shop** -- particularly the inop bluetooth bug. We're still working on that one and a couple of other tricky ones pertaining to power management and hot keys. We consider all of those high priority and will be devoting full attention to them after the release.

Instructions for doing an online upgrade are [**here**]("http://knowledge76.com/index.php/LucidUpgrade").

Instructions for doing a fresh install are [**here**]("http://knowledge76.com/index.php/Restoring_Your_System") for laptops and desktops, and [**here**]("http://knowledge76.com/index.php/Restoring_Your_Netbook") for netbooks.

---

### Post by isaacullah on 2010-05-07
Hi all. This is my first post here, and I'm a proud new owner of a brand new Pangolin P7. I've had the Pan P7 since Monday. I've been a long-time user of Ubuntu on my lab computers at school, and I could not wait for 10.04 on my new "ubuntu laptop" any longer! So I took the plunge today, and did the "auto upgrade". I'm a PhD student, so I did the upgrade on campus with relatively fast broadband. It took about two hours to download and install the upgrade (from 9.10), and it went without a hitch. I was able to re-activate the System76 repository right away, and reinstalled the sytem76 driver (even though it said it was already installed). I tested wireless, webcam, microphone, keyboard, and hot keys. The Mute hot key seems to be non-functional, but the other two still work (mail key launches mail clinet, web key launches nautilus). Fingerprint reader doesn't work (but this is a known issue). I have not yet had opportunity to test the Bluetooth, but it prob does not work yet either, as this is a known issue. Overall, I like 10.04. It seems a lot like 9.10, though I imagine many of the changes are under the hood. The most obtrusive difference is that the window buttons were moved to the left side (a la Mac OS). I'm not down with that, so I had to move the window buttons back to the right side. I HATE the Mac-like left corner position of buttons! ;) But that was super easy. 

  I LOVE LOVE LOVE my Pan P7. It's BLAZING fast (I got the best i5 chip, 4 gigs of RAM, and the 7200rpm hard drive), and it's SO nice to know that it has NEVER been tainted by microsoft OR apple. It's a great deal, and I want to thank System76 for providing such a great service to those of us who value freedom in our computing. Three cheers for Sys76!!!

---

### Post by thomasaaron on 2010-05-07
Please go to System > Admin > Software Sources. Click the update tab. Enable "proposed" updates. Then reload, run all updates and reboot.

That should fix your hotkeys and bluetooth.

---

### Post by isaacullah on 2010-05-07
Hi Thomas,

   Thanks for the reply. Unfortunately, these steps do not fix those two issues. The mute hotkey still does not work, and Bluetooth is inop (the system does not find any bluetooth hardware). These things are not essential for me, so I'm happy to wait for future bugfixes! Please let me know if I can provide any sort of bug report/error logs, and I will be happy to do so.

Cheers,

Isaac

---

### Post by thomasaaron on 2010-05-07
Thanks. I just checked the Mute key and bluetooth on our shop Serval, and they both work fine. So I'm wondering if you installed the System76 Driver but didn't actually run it.

Please go to System > Admin > System76 Driver. Click the Install tab and the Install button. Once the driver finishes, reboot your system. Did that fix it?

---

### Post by isaacullah on 2010-05-07
Hi Thomas,

   Yes, I've done that twice now, with reboot, and no luck. All the correct repos are enabled, and the sys76 tool says it installs the drivers correctly, so I'm not sure what the issue is. Can you think of some kind of  command to attempt that will return output useful for diagnosing the issue?

Cheers,

Isaac

---

### Post by HegonBadde on 2010-05-07
I had the same problem on my new BP.

Turns out the Hotkey did work, and that I had turned off blue tooth before reinstalling, so it was never active to detect.

I just hit the hot key 1 time. and let gnome take care of it for me.
couple seconds later all was well.

---

### Post by isaacullah on 2010-05-07
Ahh... Yes, Bluetooth was disabled! I forgot that with this computer you turn off BT/WiFi/etc via Fn key combos! Duh! Bluetooth works just fine now. The Fn key combo for muting also works perfectly, but the dedicated "mute" hotkey in the upper left still does not work. The other two hot keys work just fine, and I was even able to reassign them to new tasks in the gnome "keyboard shortcuts" preference menu. The pressing the "mute" hotkey does not register any sort of kemapping info to gnome, whereas pressing the other two hotkeys does (eg. "XF86mail" for the "mail" hotkey).

---

### Post by Eyore15 on 2010-05-26
I'm upgrading my starling in steps; from 9.04 to 9.10 then to 10.04.  Do I need to update the system76 driver at the end of the 9.10 upgrade or can I just wait until the 10.04 upgrade completed

---

### Post by thomasaaron on 2010-05-27
I think you can just wait until the end.

---

### Post by phyzome on 2010-06-02
> **thomasaaron said:**
> Please go to System > Admin > Software Sources. Click the update tab. Enable "proposed" updates. Then reload, run all updates and reboot.

That should fix your hotkeys and bluetooth.

Once you've installed Proposed updates, you can't really go back cleanly, right?

---

### Post by bix15 on 2010-06-02
I am the proud owner of a system76 Pangolin Performance. I've owned it since around November of 2009. It shipped with Ubuntu 9.10 installed.

Just today I decided to upgrade to 10.04 using the update manager. I was prompted through a few simple things. After everything was done and installed it asked me if I wanted to remove some out-of-date files and packages, so I just thought "Well if they are removed, naturally, up-to-date versions of those files and packages should be installed in place of them."..... I believe I was wrong because...

#1 These files I believe made up the kernel or Grub (with names such as 'Linux image       2.36-Generic')

#2 When I restarted my computer it ran a memory test and it kept repeating itself

#3 I get a screen that says "Operating system not found"

So here I am, a brand new Linux user, and I have no clue what to do next. I didn't make a backup of anything because I figured if I really screwed up bad enough I would just do a clean install of 10.04. 
Is there any way that I could possibly fix this without having to do a clean install myself and configure a bunch of drivers!! System 76 shipped it with drivers already installed which was REALLY nice!!! 

Any help would be greatly appreciated!

---

### Post by msrinath80 on 2010-06-03
Once again an upgrade goes awry. Anyways, no need to sweat. Just grab the 10.04 liveCD and reinstall from scratch. Install the system76 driver and you're good to go. If you need help with any of this (or prefer a less radical solution), hold on and wait for Tom (from System76) to respond.

---

### Post by thomasaaron on 2010-06-03
Well, msrinath80's idea is definitely a good one. I personally prefer fresh installs after hosed upgrades. I've found it often takes less time to install than to figure out all of the things that are hosed.

In your case, though, it sounds like you *might* just need to recover grub. As with msrinath80's suggestion, you will need a live CD or USB flash drive. From there, you can follow the instructions here...

To reinstall Grub2 from an Ubuntu Live CD go here...
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

And follow the instructions in this section...
"Recover Grub 2 via LiveCD"

---

### Post by VOLKOV9 on 2010-06-15
I have a roughly two-year-old Serval.

I just upgraded from Karmic to Lucid.  I followed the instructions at knowledge76 and things seemed to work fine.  I've never had problems with playing video files before, but now that I've upgraded to Lucid, I am, regardless of Compiz and other visual effects being on. What I know of my hardware specs are in my sig. I have "NVIDIA accelerated graphics driver (version current) [Recommended]" activated (and in fact, one of my reasons for upgrading was the supposedly improved NVIDIA drivers in Lucid). VLC, MPlayer, and Totem are all choppy playing .avi's: they play smoothly for several seconds, then start skipping (audio and visual, separately), though VLC does so less violently than the others. Similar problems, though slightly less severe, with watching flash movies in chromium.  Also, after a few minutes, it even happens to music played in Rhythmbox or embedded in websites.  During all of these activities (flash excepted), the processor use is < 10%.

Do you guys know what's going on or at least how to diagnose it?

---

### Post by VOLKOV9 on 2010-06-16
Actually, it doesn't seem to be media-related.  The screensaver hiccups, and even a simple game like Nibbles will run smoothly for several seconds, then stall for a split second, and repeat.  My computer seems to simply have the hiccups.

---

### Post by isantop on 2010-06-17
Try running Lucid from a LiveCD or USB Drive. Test out different types of media playback, and see if they also skip and stutter.

---

### Post by VOLKOV9 on 2010-06-18
Despite the fact that I couldn't activate my graphics card driver while running off the CD, video play of the "ubuntu is humanity" .ogv video was perfect.  In contrast, booting from my hard drive, the same video is choppy after a few seconds.

---

### Post by isantop on 2010-06-18
This is beginning to sound like an upgrade issue. Would it be possible to reinstall? I can walk you through the process if you'd like.

---

### Post by VOLKOV9 on 2010-06-21
Ah-hah, the culprit has been isolated!  I cleaned the computer off, and followed the "Restoring Your System" dealie on knowledge76.  When I first installed Lucid on the clean system, I watched the aforementioned video flawlessly.  Then I downloaded and installed the "NVIDIA accelerated graphics driver (version current) [Recommended]" rebooted and watched it again, and choppy choppy choppy.  Removing that, installing and activating "NVIDIA accelerated graphics driver (version 173)" and rebooting seems to have fixed it.  Is there anything I'm missing by using an out of date graphics driver?

---

### Post by jdb on 2010-06-22
> **VOLKOV9 said:**
> Ah-hah, the culprit has been isolated!  I cleaned the computer off, and followed the "Restoring Your System" dealie on knowledge76.  When I first installed Lucid on the clean system, I watched the aforementioned video flawlessly.  Then I downloaded and installed the "NVIDIA accelerated graphics driver (version current) [Recommended]" rebooted and watched it again, and choppy choppy choppy.  Removing that, installing and activating "NVIDIA accelerated graphics driver (version 173)" and rebooting seems to have fixed it.  Is there anything I'm missing by using an out of date graphics driver?

Yeh, choppy video :lolflag:

jdb

---

### Post by isantop on 2010-06-22
You guys should be okay, since that driver was tried and true for a while before the current one came out.If you notice anything, be sure and let us know so we can help you sort it out.

---

