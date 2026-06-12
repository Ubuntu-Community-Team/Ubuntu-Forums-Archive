---
title: "No boot unless monitor is plugged in..."
date: 2015-01-29
forum: Server Platforms
---

### Post by fizgig on 2015-01-29
I bought one of these computers the other day:  [http://www.aopen.com/us/de3250](http://www.aopen.com/us/de3250)

I installed 64-bit LTS 12.04 server on it and it works great.  The problem arises when I finally unplug the monitor from it and try to get it to start with no display plugged in.  It just wont.

I tried changing every relevant setting in the BIOS but no joy.  I finally ended up getting a [fake HDMI monitor plug]("http://www.amazon.com/CompuLab-fit-Headless-Display-Emulator/dp/B00FLZXGJ6/ref=sr_1_5?ie=UTF8&qid=1422551853&sr=8-5&keywords=hdmi+plug") and I can now boot.

The factory isn't being very helpful as they only test their BIOS against windows 8.  Does anyone have any settings I can modify in Ubuntu to try out as I'd like to get one more of these computers (price is right) but see if I can solve this problem without hardware first.

---

### Post by volkswagner on 2015-01-29
Have you tried any Grub modifications such as replace 'quiet splash' with 'nomodeset'?

Have you checked logs after failed boot for helpful info?

---

### Post by fizgig on 2015-01-29
> **volkswagner said:**
> Have you tried any Grub modifications such as replace 'quiet splash' with 'nomodeset'?

Have you checked logs after failed boot for helpful info?

I'll try that GRUB modification right now and post what it does.  Which log file should I be looking at?  /var/log/dmesg?

---

### Post by fizgig on 2015-01-29
> **volkswagner said:**
> Have you tried any Grub modifications such as replace 'quiet splash' with 'nomodeset'?

Have you checked logs after failed boot for helpful info?

I had nothing in the **GRUB_CMDLINE_LINUX_DEFAULT **variable to start with.  I added nomodeset, did the update-grub and rebooted.  No dice.  I then changed it to "quiet splash", updated, no dice.

What log can I look in?

---

### Post by volkswagner on 2015-01-30
I'm no grub expert. From my quick research, it seems grub doesn't have write permissions to the system. You may not find
any info in dmesg nor syslog.

You may also try uncommenting GRUB_GFXMODE=640x480

There's also a line to uncomment to allow beep GRUB_INIT_TUNE="480 440 1"

If you allow the beep, I'd be curious what happens if you hot plug the monitor five to 10 seconds after the beep.
Do you see the error on screen, or does it continue to boot?

---

### Post by MAFoElffen on 2015-01-30
No. Mine are all on a KMS switch to one console and boot fine. <-- means they share one monitor and keyboard for my 13 servers, so all but one boot, not ever seeing a monitor until needed. I do have to turn off kb and mouse error/continiue in the BIOS on a few of them...

So, yes... that sounds more like a BIOS/hardware issue, where theoi BIOS thinks that not having an attached monitor is an error. What system is it?

---

