---
title: "Won't boot up with a monitor plugged in."
date: 2012-09-03
forum: Server Platforms
---

### Post by mickey13 on 2012-09-03
I'm running Ubuntu Server 12.04 with no desktop installed.  When I don't have a monitor plugged in, it boots up fine.  I usually log into it via ssh.  I now would like to use a monitor with it, but when I power on the machine it won't boot:  nothing on the monitor, and I cannot ssh into it.

There's no xorg.conf file, but I don't think that's required any more.

Any ideas?  Thanks.

---

### Post by Bachstelze on 2012-09-03
Could be a dead graphics card, do you have a spare one to try?

---

### Post by mickey13 on 2012-09-03
Thanks for the suggestion.  It could be the video card, though I don't have one handy at the moment.  I tried reseating it just to check to see if it had become loose due being pushed back against the wall with the DVI cable attached to it.  I'm going to see if I can scrounge one up and test it out.

The last time I had the monitor plugged in, it had worked.  That was about a month ago when I did the OS install.

---

### Post by kennethconn on 2012-09-03
Are you getting any beeps at BIOS start-up? Sounds like it is not an OS issue.

---

### Post by Kalibur on 2012-09-04
> **mickey13 said:**
> I'm running Ubuntu Server 12.04 with no desktop installed.  When I don't have a monitor plugged in, it boots up fine.  I usually log into it via ssh.  I now would like to use a monitor with it, but when I power on the machine it won't boot:  nothing on the monitor, and I cannot ssh into it.

There's no xorg.conf file, but I don't think that's required any more.

Any ideas?  Thanks.

Firstly the fact that it boots without a monitor means your Operating system is happy that your graphics card works.  I am going to guess that your vga cable is an older type try another cable as a quick fix. To know what is really going on boot without a monitor ssh in as you normally do then view '/var/log/X.0.log that will tell you exactly what happened during the boot up process including any errors detected.  If you can pipe the contents to a file and bring it here that would be great.

At the end of the day will probably need to create you an xorg.conf.  For that I will need to know you monitor size model supported resolution and you graphics card details from 'lspci'.

---

### Post by mickey13 on 2012-09-06
Thanks for the replies.  The video card actually has a single output that requires a Y connector for DVI (you can't actually just put a DVI cable in the back of the machine without using the Y connector).  It worked at one point recently, as I installed the OS about a month ago using the same monitor and cabling.  I then intended the monitor to be used for something else, but have since decided to bring it back.  My first reaction was that some setting had been changed causing an issue with the display.

No beep codes, the internal speaker has been disabled or removed :/  I'll need to check on that.

---

