---
title: "Ubuntu 8.10 Install Feedback"
date: 2008-12-01
forum: Testimonials &amp; Experiences
---

### Post by NilsJeppe on 2008-12-01
Decided to give Ubuntu another go. Not exactly a smooth experience. I finally got it to install, but forgot to change the boot drive in BIOS and ended up back in Windows, so all feedback after the install-reboot must wait until a later date (it's 1am and this has cost me WAY too much time already).

1) General impression: "Copying files" takes... a long time. I am not sure what exactly you are copying, and from where, but it's only one CD. Shouldn't that only take a few moments even on a fairly old drive?

2) X11 crashes after some time when a wacom tablet (Volito 2) is connected. The X-server then restarts a few times, unsuccessfully, and gets throttled, and the installation is stuck on an ncurses warning screen about flapping X-server. The crash also happened when I did not use the live-cd system, and did not start any terminals etc.

3) The first time #2 happened was during HD format (I was installing via the Live system desktop, and tried to start a terminal, which then seems to have resulted in the crash). Let's just say that the beast does NOT handle unreadable partitions gracefully; the partitioner froze up at 50%. I ended up deleting them manually on the CLI. Any kind of "Joe the User" (to use a Palinism, or is that a McCainism?) would've been utterly lost. really, if partitions are not readable, just give up at some point.

4) One of my USB drives seems to have large FAT blocks. This resulted in a very ugly error message, and I at first thought this was the cause for the 50% freeze in #3.

5) Disabling ACPI via boot option completely breaks the installation process. It results in the live filesystem being unmountable due to i/o errors on /dev/sr0, whatever /dev/sr0 is. (Considering how much trouble ACPI can be, disabling it should really be in the menu where you can set a safe display mode etc.)

6) More general feedback: The timezone selection thing is terribly ugly. And does it really need a huge drop down of cities? Just list the time zones with some examples. If people can't figure out what time zone they are in, then the drop down will be too hard for them to navigate as well. (The map is fine, but ugly.)

7) I can haz package selection plz? - Seriously, I like to have more control over an installation than to "copy everything". A base system would have been fine. I have no problem installing needed packages after the fact. The perfect place would be in the "advanced..." button in the last step. (If package selection is hidden somewhere, it is hidden well.)

8 ) The installation has a screen saver. I guess it makes sense, considering how long it takes, but I really must wonder if that isn't a waste of space. Besides I thought the system had crashed again when it first went on.

9) Positive: The display is clean and crisp, text feels much more legible than on my Windoze workstation. The background a bit grungy but it looks fine; I always liked the brownish color scheme of Ubuntu.

10) Partitioning suggestion: I had /dev/sda completely empty (no partition), at 180GB. The partitioner still suggested me to resize /dev/sbd and install Ubuntu on there. That may somehow be related to my boot order (I boot off of /dev/sdb) though I am not sure how the partitioner would know that, except checking for the active bit. Either way, if I have a completely empty HD, I think it makes a lot of sense to suggest using that instead of resizing something existing.

That's it for now. Hope these issues can be corrected for the next version.


Best wishes
- Nils

---

### Post by 3rdalbum on 2008-12-01
> **NilsJeppe said:**
> 1) General impression: "Copying files" takes... a long time. I am not sure what exactly you are copying, and from where, but it's only one CD. Shouldn't that only take a few moments even on a fairly old drive?

On desktops, the speed is fine IMHO. On laptops, I think the general speed of the components is the bottleneck.

> 2) X11 crashes after some time when a wacom tablet (Volito 2) is connected. The X-server then restarts a few times, unsuccessfully, and gets throttled, and the installation is stuck on an ncurses warning screen about flapping X-server. The crash also happened when I did not use the live-cd system, and did not start any terminals etc.

If you haven't already, please file a bug report so hopefully this can be fixed.

> 3) The first time #2 happened was during HD format (I was installing via the Live system desktop, and tried to start a terminal, which then seems to have resulted in the crash). Let's just say that the beast does NOT handle unreadable partitions gracefully; the partitioner froze up at 50%. I ended up deleting them manually on the CLI. Any kind of "Joe the User" (to use a Palinism, or is that a McCainism?) would've been utterly lost. really, if partitions are not readable, just give up at some point.

As someone who might possibly be affected by this bug at some point in time, please file a bug report. I have a feeling this problem might be inherited from Gparted.

> 7) I can haz package selection plz? - Seriously, I like to have more control over an installation than to "copy everything". A base system would have been fine. I have no problem installing needed packages after the fact. The perfect place would be in the "advanced..." button in the last step. (If package selection is hidden somewhere, it is hidden well.)

Fedora could be a good choice for you, or you could do an installation from the Server CD. I don't think this is necessarily something we really  need; it's a bit of a corner case as most Ubuntu users install the base system and then add to it. The way Ubuntu uses Apt (by installing the ubuntu-desktop package) might also be a reason why they're not offering package selection out-of-the-box.

> 8 ) The installation has a screen saver. I guess it makes sense, considering how long it takes, but I really must wonder if that isn't a waste of space.

You'd be surprised how many people with CRTs and plasmas would complain if you took the screensaver out of the standard install, or even disabled it from the live CD. No plasma TV will get burn-in from displaying the same image during the install, but you'd get plasma owners complaining.

But yeah, thanks for your testimonial and experience. I hope you enjoy your Ubuntu system.

---

