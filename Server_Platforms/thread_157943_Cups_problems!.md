---
title: "Cups problems!"
date: 2006-04-10
forum: Server Platforms
---

### Post by KevlarGurra on 2006-04-10
Hi!

I'm trying to set up a cups server on my ubuntu comp so the printer connected to it can be shared on the network. I've managed to get the hplip web-based frontend to work at myserver:631, but when I try to print a test page, nothing happens.

The printer is a hp photosmart 7150 and a ppd-file has been created that seems to be correct.

Below is what I believe the relevant part of error.log (using the most extensive debug level).

```

d [10/Apr/2006:00:08:53 +0200] send_ipp_error(0xb7955c3c[7], 404)
D [10/Apr/2006:00:08:53 +0200] Sending error: client-error-not-possible
D [10/Apr/2006:00:19:17 +0200] [Job 11] Process dying with "The renderer command line returned an unrecognized error code 127.", exit stat: 1
D [10/Apr/2006:00:19:17 +0200] [Job 11] error: No such file or directory (2)
D [10/Apr/2006:00:19:17 +0200] [Job 11] The renderer command line returned an unrecognized error code 127.
D [10/Apr/2006:00:19:17 +0200] [Job 11] error: Bad file descriptor (9)

```

I'd be happy to post more information if needed.

Any ideas of how I can get it to work?

---

### Post by KevlarGurra on 2006-04-15
No one?

---

### Post by LordHunter317 on 2006-04-15
Looks to me like whatever it's trying to run to render the job isn't installed.  How did you create this PPD?  Isn't there a packaged one for that printer already?

---

### Post by KevlarGurra on 2006-04-18
[QUOTE=LordHunter317]Looks to me like whatever it's trying to run to render the job isn't installed.  How did you create this PPD?  Isn't there a packaged one for that printer already?[/QUOTE]
Yes, there is a packaged one, I meant install, not create. That's the one I'm using.

---

### Post by KevlarGurra on 2006-04-18
By the way, commands like hp-clean and hp-align work fine, but hp-toolbox says "cannot connect to X server" (maybe because it's a GUI and I don't use Gnome or KDE).
The web frontend says "Print file was not accepted (client-error-bad-request)!" and printing doesn't work.

---

### Post by PaDV on 2006-04-23
Seems related to this bug: [https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/34971](https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/34971).
Please add your info if this is the case.

---

### Post by KevlarGurra on 2006-04-24
I figured out what the problem was: I didn't know that I had to install Ghostscript too... Now when I've installed it, it works perfectly! There's only one quite annoying thing: The printer always prints a page with the text "Product: GPL Ghostscript" or something before the other pages are printed. Any ideas of how to remove that page?

---

