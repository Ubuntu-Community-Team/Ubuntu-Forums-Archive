---
title: "Constant Lockups"
date: 2009-07-04
forum: Server Platforms
---

### Post by Mizutsuki on 2009-07-04
I'm trying to get a working house file server, but I'm having a strange freezing problem.

This is some information about the computer.

Chipset:    VIA CLE266 + VT8235M Chipset
CPU:        VIA Eden 800MHz Processor
Audio:      [Disable at the BIOS]
Storage:    Compact flash

This first became a problem when I upgraded from ubuntu server 8.04 to 9.04.  After successfully completing both of the upgrades the computer restarted and I started noticing the symptoms.  I would boot up and within about 20 minutes the computer would lock up, sometimes as soon as 30 second after log-in.  When I say lock up, what I mean is that the system became 100% unresponsive, I couldn't ctrl-c or switch terminals or anything.  No error message was given.

Note that the server did not have any version of xorg or gnome installed.

After dispelling the idea that the problem was related to what I was doing (setting up samba, changing network setting and mounting an external HDD) my next thought was that this was a RAM problem.  I used memtest86+ for a little over 10 hours, and everything check out.

Next was the CF internal drive.  I don't fully understand how to test CF drives, but I used fsck on it with a number of different setting and it checked out.  I was able to do this with the help of a live distro, which told me something else: the problem isn't in the hardware.

So I thought, "eh, something's up, there's nothing on there worth saving", so wiped the HDD and booted up the 9.04 server installer, and it installed, but it couldn't boot because it said something about the processor not supporting some necessary feature.  I looked it up and apparently the server edition of the kernel doesn't work on Via processors, so I used a live distro, chrooted in and installed the normal version of the kernel.

Then it booted fine, but it still froze in exactly the same way.

So I tried installing the desktop version of 9.04, and at some point very near the end of the installation it crashed.  Unfortunately I wasn't near the monitor when it crashed so all I saw was a black screen.

When I rebooted it dropped me in run level 2 without any errors, and I began to track down some of the loose ends the installer wasn't able to complete.

This is the really interesting part to me, and I can't figure it out: it ran fine.  I worked on it for hours and rebooted many times and left it on over night, and it never froze.  That is, until I fixed the wrong thing...

I was getting an error when trying to do ifup that said, "Fake start-stop-daemon called, doing nothing" so I looked into it and I fixed it by replacing /sbin/start-stop-daemon with /sbin/start-stop-daemon.REAL, just as a guide I found suggested.  I restarted and it worked at fixing most of my problems.  It booted into GDM for the first time after that, and I logged in, but just as gnome was getting finished starting the system froze in exactly the same way as before.  I went in using the recovery mode and disabled gdm and xorg in the rc-default.  When I rebooted the server it went, as hoped into the terminal but soon after it froze, in exactly the same way as before.

So my best guess is that there is something in my hardware that is causing one of the daemons that was failing before I replaced the start-stop-daemon to freeze the system.  But I don't have any idea how to proceed from here, how to identify and fix the offending daemon.  Does anyone have any ideas?

That was long winded, I know.  Thank you for reading it all, and thanks so much for your support.

 - Stella

---

### Post by HermanAB on 2009-07-04
Hmm, divide and conquer!

You can use the BIOS to disable some mother board features for example the built-in ethernet (install a card from your scrap box instead).

Otherwise, try a different distribution - Knoppix, Debian, Fedora, whatever and see what they do.

---

### Post by Mizutsuki on 2009-07-04
> **HermanAB said:**
> You can use the BIOS to disable some mother board features for example the built-in ethernet (install a card from your scrap box instead).
Hehe.  I would but the system is about 5"x3", and wouldn't fit even the smallest PCI card. [http://e-itx.com/system-3855e.html]("http://e-itx.com/system-3855e.html")
I'll see what else I can disable, though.

> **HermanAB said:**
> Otherwise, try a different distribution - Knoppix, Debian, Fedora, whatever and see what they do.
I'll try installing DSL now.

---

### Post by Mizutsuki on 2009-07-05
I just tried debian.  The process went through just fine, but as soon as I tried to boot into it I get failures.  "mount: mounting /dev/disk/by-uuid/[UUID] on /root failed: Invalid argument" ([UUID] is the actual UUID of the disk, mind you."  It doesn't seem like this is related, but I don't really want to spend much time fooling around with it, so I'm actually installing DSL now.  I'll let you know how that goes.

---

### Post by Mizutsuki on 2009-07-05
Ok, I installed dsl without a problem, and I upgraded it to sarge and now I'm upgrading to etch.  I've been using it for about 2 hours, no problem, so it's definitely something in the software.  Any more ideas?

---

### Post by HermanAB on 2009-07-05
OK, I'm glad you proved that it is not hardware.  

The problem is clearly with a bad device driver, but figuring out what exactly would be really hard.  In the past I have found lockups due to bad ethernet drivers, bad display drivers, bad interrupt controller and bad ACPI drivers...  

You could try some kernel switches such as:
acpi=off
noapic
nolapic

and see how it goes.

---

### Post by Mizutsuki on 2009-07-07
> **HermanAB said:**
> OK, I'm glad you proved that it is not hardware.  

The problem is clearly with a bad device driver, but figuring out what exactly would be really hard.  In the past I have found lockups due to bad ethernet drivers, bad display drivers, bad interrupt controller and bad ACPI drivers...  

You could try some kernel switches such as:
acpi=off
noapic
nolapic

and see how it goes.

Ok, sorry for the wait.  I did as you asked and disabled those three things, and it still froze.  What's next?

-- EDIT --

Also, I used the bios to disable the onboard network card but it still froze.

---

### Post by Mizutsuki on 2009-07-08
Bump

---

### Post by cenwesi on 2009-07-09
Not only would mine lock up but it also will KILL the entire lan until i turn off the pc or unplug the network line off the pc. I really think it has something to do with Jaunty + network driver...

---

### Post by Mizutsuki on 2009-08-01
The problem with ubuntu remains unsolved, although I ended up installing debian lenny and being satisfied (fyi.)

---

