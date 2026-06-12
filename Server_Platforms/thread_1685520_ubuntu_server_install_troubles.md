---
title: "ubuntu server install troubles"
date: 2011-02-10
forum: Server Platforms
---

### Post by paul1149 on 2011-02-10
Hi,
I'm attempting to install the latest version of unbuntu server x64, and not having a lot of fun doing so. I have minimal Linux experience.

I currently have it installed on a multi-boot box, but the boot hangs on: 

"Thank you for participating in the global usage survey"
"The server's response is:"

Zero idea what is going on. It might as well be telling me what kind of ice cream it likes best. There is no prompt, and I never signed up for a survey.

My first attempt at installation did not do this. I overwrote it for other reasons (and lost my mbr in the process), but at least it booted up.

p.

---

### Post by HermanAB on 2011-02-11
Howdy,

It meaans that there is a hardware driver problem, but figuring out what exactly is usually not quite worth the effort.  I'd suggest that you try different distributions, till you find one that works:
Regular Ubuntu, Fedora, CentOS, OpenSuse etc.

---

### Post by paul1149 on 2011-02-11
Thank you, Herman. I've decided to take it from the top once again. I rewrote the XP mbr, will install ubuntu server to a *Primary* partition this time, on drive b, and will place grub2 out on a usb stick so that the basic system is not affected by my experimenting.

If that doesn't work I certainly will bear your counsel in mind and look for a different solution.

p.

---

