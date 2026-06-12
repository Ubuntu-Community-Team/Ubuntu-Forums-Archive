---
title: "Uninstall Graphics Card After Server Install"
date: 2007-09-27
forum: Server Platforms
---

### Post by Soarer on 2007-09-27
I installed Gutsy server on an old P4 box, as Feisty refused to install at all (after 2 CD burns). Gutsy installed and is running just fine.

The system is from 2002 or so, and has no on-board graphics at all - nowhere to plug in a screen. It came with an nVidia PCI graphics card, which I used to view the terminal as it installed. Now I am using Webmin & ssh for administration, so I don't need the card, and would like to remove it as it has a noisy fan and uses juice unnecessarily.

However, if  just take it out, the system won't boot. I can't tell why as I don't, at that point, have a terminal of course.

So I guess I have to uninstall it before I remove it. Can anyone please tell me how to do this using the command line and/or Webmin?

Thanks.

---

### Post by /etc/init.d/ on 2007-09-27
I think it may not be Linux that isn't booting, but the BIOS.  A lot of BIOSes won't boot if they don't find a video device or a keyboard.  Some won't even boot if you have a video card but no monitor attached.

That said, I would have assumed it would have given an error beep.

If Linux is definitely trying to boot, then perhaps there is something specific with Ubuntu.  I definitely know Linux is capable of booting without a video card though.

You don't specify, but I assume you've removed X or didn't have it to begin with?

Another thing to think about is the kernel can be configured to send kernel messages out over a serial line, so you could see what's going on when it boots.

---

### Post by Soarer on 2007-09-27
Thanks for the reply. You might be right about the BIOS - like I say the system is old. The BIOS is up-to-date, but still dates from 2003 IIRC.

I just did the server install, no X installed.

I'll do a search for the serial line thing.

---

### Post by threeten on 2007-09-30
I had this problem when I installed Clark Connect and then removed the video card - it would refuse to boot.  I was unable to solve it, but switched to Ubuntu which is working fine without video.

Make sure your BIOS is set for:

Halt on errors - none

You might check your log files and see if there are any clues there.  I did a minimal install of Ubuntu and then installed everything via SSH after I removed the video card.

---

### Post by Soarer on 2007-09-30
Thanks threeten I'll check the BIOS and the logs. :)

---

