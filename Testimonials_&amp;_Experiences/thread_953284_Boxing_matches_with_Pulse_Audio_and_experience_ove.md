---
title: "Boxing matches with Pulse Audio and experience overall"
date: 2008-10-20
forum: Testimonials &amp; Experiences
---

### Post by jaklumen on 2008-10-20
I was a Windows XP user before I came to Ubuntu.

Story short, I'm a disabled dad living on a fixed income.  I found out quickly that software and hardware was going to need to be a Do-It-Yourself kind of thing.  When I was still running XP, I started using a lot of open source programs, because I honestly could not afford to buy commercial programs from Microsoft, Adobe, etc.

I got my first computer when XP was still relatively new.  My installation disc did not have any of the Service Packs at all.  When the first motherboard died (leaking capacitor) I found reinstallations were a real pain-- I had to ask a friend for a copy of SP2.  When I finally misplaced my XP installation disc, I knew I was screwed if that partition went under again.

So I decided to make the switch.  I couldn't get a LiveCD to work, so I used the alternate CD, for 8.04.  My intent was to do a dual-boot, but since I didn't understand how Linux labels hard drives, I accidentally installed it to my external hard drive (not really a bad thing in the end), but then skipped over the SATA I had XP installed to, and installed it to an IDE I had wiped, and wound up with a pure installation.

Wow.  Everything ran so smooth.  No defragmenting the hard drive, no registries to mess with, and I didn't really have to mess a lot with malware programs.  I wound up installing ClamAV and ufw + a GUI frontend, but otherwise I didn't have to bother with it a lot.

However, I found the adoption of the Pulse Audio sound server to be a real stumbling block.  To this day I cannot get a microphone to work, whatsoever.  After hours of tweaking I was able to get sound output from Flash, but I could not get sound mixing at all.  I eventually bought an SB! Live sound card specifically to address that problem.

I tried a few different solutions to Pulse Audio problems, but I found that I had to rip out the programs that installed the applet and specific GUIs for the Device Chooser every time.  Before, I had been able to get output through ALSA, but I had to drop down to OSS afterwards to get any sound to work.

One day after some particular upgrades, all sound stopped working.  I decided to upgrade to the 8.10 beta.  Suddenly, I had specific Sound Preferences for the SB! Live card.  However, I have not been able to get sound output through Flash since then.

Besides Pulse Audio, the only small downside in switching from XP to Ubuntu was I found gaming was no longer a lazy, guided process.  I was happy to find that Bioware provided Linux binaries for Neverwinter Nights, although I'm sure I stumbled through the installation-- I can't remember if I followed instructions here on the forums or the ones at the Bioware forums-- I think it was the latter.  I looked into gemrb, which is an Infinity Engine emulator, as I dearly love Planescape: Torment and was looking into trying out the other games such as Baldur's Gate, but... I have yet to figure out how to fully install gemrb.

I don't mind copying and pasting Terminal commands, but I am generally struggling with the learning curve.  If it's not specifically in a Debian package, I have a real hard time installing it, and you see, not everything I want is in the repositories.  I'm thinking of trying Linux Mint once Felicia (which corresponds to 8.10) is released, just because I don't want to duplicate my time tuning and tweaking things on a fresh install if I can help it-- and I probably will do a fresh install once 8.10 is fully released.

I'm trying really, really hard not to look back, to go back to Windows.  Overall, I much prefer Ubuntu as it performs very well on my older hardware-- my CPU is an old AMD Socket 754 type and I just can't afford to upgrade to the new multicore processors that are the must-haves for the young and gamer hardcore (although someday I might just overclock it a bit when time, patience, and money permits).  But I miss having sound that simply works, and popping in a CD and getting an Installation Wizard that glides me through the process.  (Yes, I have heard of the Loki installers and have looked into them a little bit.)  I'm using Wine (not yet ready to pony up money for Cedega) which is a mixed bag for the kinds of games I like.  EXTREMELY tempted to go to a dual boot so I can play certain games (KOTOR series, etc.) without so much hassle, but... I really don't want to.

I like Ubuntu, but I simply wish Pulse Audio problems could be solved once and for all, and that all commercial games were ported to Linux.  Extremely idealistic, I know, but pretty common to the wishes of users migrating over from Windows.

Glad to be here, though!

---

### Post by Comhra on 2008-10-20
It may be your lucky day.  The following excellent tutorial from Zimbio fixed Pulse Audio and Flash for me>

[http://www.zimbio.com/pilot?ZURL=%2FUbuntu%2BLinux%2Farticles%2F338%2FFlash%2BIs%2BFixed%2BIn%2BUbuntu&URL=http%3A%2F%2Fubuntuforums.org%2Fshowpost.php%3Fp%3D5587712%26postcount%3D472](http://www.zimbio.com/pilot?ZURL=%2FUbuntu%2BLinux%2Farticles%2F338%2FFlash%2BIs%2BFixed%2BIn%2BUbuntu&URL=http%3A%2F%2Fubuntuforums.org%2Fshowpost.php%3Fp%3D5587712%26postcount%3D472)

---

### Post by mikewhatever on 2008-10-20
In my case, the lucky day came two minutes after the installation. Having found out that two programs can't produce sound at once, I promptly disabled PA everywhere I could find. I am quite happy with alsa, so, problem solved. What's odd is why don't Ubuntu devs patch PA. Do you think they ever will?

---

### Post by jaklumen on 2008-10-20
> **Comhra said:**
> It may be your lucky day.  The following excellent tutorial from Zimbio fixed Pulse Audio and Flash for me>


Actually, I am corresponding with the author of that tutorial; it's featured right here on the forums.

> **mikewhatever said:**
> In my case, the lucky day came two minutes after the installation. Having found out that two programs can't produce sound at once, I promptly disabled PA everywhere I could find. I am quite happy with alsa, so, problem solved. What's odd is why don't Ubuntu devs patch PA. Do you think they ever will?

Well, I got the SB! Live card specifically to handle sound mixing at the hardware level, i.e. to allow multiple programs to produce sound at once.  It works very nicely, at least as far as I could see when I could get sound output from Flash.  I'm not sure if I specifically disabled PA or not but wouldn't mind if you could tell me how you did it, especially as I was reading that if I got that particular card, I could just roll back to ALSA.

---

### Post by wolfen69 on 2008-10-20
> **mikewhatever said:**
> In my case, the lucky day came two minutes after the installation. Having found out that two programs can't produce sound at once

for anyone reading this,
```
sudo apt-get install libflashsupport
```takes care of that issue.

---

### Post by mikewhatever on 2008-10-20
Hey wolfen, I've never had a problem with flash with or without PA. The problem was, that whenever I tried playing a song in Totem, a message in the logs said the device was busy. I think the problem is purely PA's, and I even remember seeing a bug report filed. Hope your suggestion helps someone though.

> **jaklumen said:**
> 
Well, I got the SB! Live card specifically to handle sound mixing at the hardware level, i.e. to allow multiple programs to produce sound at once.  It works very nicely, at least as far as I could see when I could get sound output from Flash.  I'm not sure if I specifically disabled PA or not but wouldn't mind if you could tell me how you did it, especially as I was reading that if I got that particular card, I could just roll back to ALSA.

I think the main place to start is in System->Preferences->Sounds. I just changed everything from PA to Alsa (see the screenshot).
There is also an autostart process you can disable under Sessions.

---

