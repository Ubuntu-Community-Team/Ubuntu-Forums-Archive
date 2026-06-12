---
title: "My dual-boot experience has mixed results."
date: 2011-02-17
forum: Testimonials &amp; Experiences
---

### Post by LinuxFox on 2011-02-17
For the longest time, I've been using Ubuntu via Wubi and I loved it, and my mother's been using Wubi for Ubuntu as well.  Since I'm always reading that "Wubi is not for long-term use" (I still fail to see why it's not, when I've clearly used it since 2008 ), I decided to install Ubuntu as a real dual-boot on both of our computers.  The results are mixed, one computer did it with no issue, while the other failed.

My laptop was where I tried to install Ubuntu 10.04 as a dual-boot.  I'm glad it was very easy with Ubuntu 10.04, and the result was a successful install and still being able to access Windows Vista for my iPod, playing Need for Speed, and other Windows only stuff.  The only weird thing, the boot options for Vista recovery and Vista are reversed.  Choosing Vista loads recovery mode, and choosing Recovery mode loads Vista.  It's only a visual problem and Vista still loads, I don't want to mess with the GRUB file just to be on the safe side.

On my mother's computer, dual-booting broke it.  She used Wubi just fine, but when I went to install Ubuntu 10.04, it stopped at 48% and had an error about a faulty CD drive (which it's not since it's been working without issues).  So I removed the partitions the installer made and resized the Windows XP partition, keeping Windows XP intact.  I reboot, and got a "A disk error occurred" message and Vista wouldn't load.  A friend of mine is going to fix it for her, and hopefully she'll let me re-install Wubi as Windows runs slow on her computer.  Even with Wubi installed, Ubuntu ran a lot faster than Windows, which is a good thing.  My friend says all it is is a boot-loader problem, so he can fix it.  All her stuff is backed up to a broken MP3 player (it saves data, just won't playback music) so I can restore it easily.

Just wanted to share my experience about dual-booting, the results are mixed since one install was successful and the other messed up the boot-loader.  For my mother, I'm just going to stick with Wubi.  In my opinion, it can be used for long-term use, as long as you know its limits and risk (if Windows goes down, it takes Ubuntu via Wubi with it).  But she rarely uses Windows except to check her job's website (requires Internet Explorer), otherwise she mainly used Ubuntu for most things.

---

### Post by mikewhatever on 2011-02-17
Wubi installations are much more susceptible to file system corruption, but as long as you keep a regular backup, there is nothing to worry about.

---

### Post by LinuxFox on 2011-02-17
> **mikewhatever said:**
> Wubi installations are much more susceptible to file system corruption, but as long as you keep a regular backup, there is nothing to worry about.If that's the case, then I'll keep Wubi on her machine.  I do use that MP3 player to back up personal documents that belong to the both of us.  A broken mass storage MP3 player is just handy for back up. :)

Though this is just an experience I wanted to share.  Between the two of us, we enjoyed Ubuntu, whether it's dual boot on my laptop, or Wubi on mother's computer.

---

### Post by mikewhatever on 2011-02-17
Thanks for sharing.;)

---

### Post by Rubi1200 on 2011-02-17
Thanks for sharing your experiences LinuxFox.

For Wubi installs, see [here]("https://wiki.ubuntu.com/WubiGuide") and [here]("http://ubuntuforums.org/showthread.php?t=1639198").

The easiest way to backup is copy the root.disk to a safe location such as an external drive or USB stick.

Good luck and enjoy :-)

---

