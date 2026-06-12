---
title: "Virtualization?"
date: 2006-08-29
forum: System76 Support
---

### Post by mecrider on 2006-08-29
I notice that several of the laptop models have the Core Duo processor, which has virtualization technology. Has anybody tried running Windows in Xen on one of these?
P.S. I'll definitely be looking your way when my laptop warrenty runs out next year. Looks like you've got good stuff.

---

### Post by crichell on 2006-08-29
We haven't ran Windows virtualized via Xen but we have virtualized Windows using the Vmware Player.  We have a How To [here.]("http://knowledge76.com/index.php/VMWare_for_Windows_and_Other_Appliances")

---

### Post by helmet on 2006-08-29
I did it!

I have a Dell 6400 w/ Core Duo t2500 and 1 gig ram. i installed xvncviewer and some sdl stuff from apt and install Xen from....i think the src package. i followed some howto to finish things up, moving /lib/tls to /lib/tls.disabled, making sure to set dom0_mem to something in the kernel config in the grub menu, and used a very basic xen config, which i can post if interested, and it cranked right up

---

### Post by mecrider on 2006-08-29
I've been running Win2k in VMware Player on my Ubuntu-powered Toshiba since player was first released. I just knew that last year Xen was saying you would need VT to run Windows, which was supposed to be out the first of the year, but I hadn't really looked at it since then because I had no need to replace existing hardware. I was just wondering if anybody had experience with setting this up and what performance was like. Win2K in Player seems a little slow to me at times (on a Mobile Celeron 2.6G with 512MB) but I'm not interested in buying a copy of XP if that is a solution - I'd rather reuse the license I already had, that is not in use anywhere else, and I can live with the speed I have for the little I am in it (which for me does not include any gaming).

---

