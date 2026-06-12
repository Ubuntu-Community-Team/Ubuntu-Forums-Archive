---
title: "MBs/CPUs that make sense"
date: 2008-12-17
forum: Server Platforms
---

### Post by stanleytberry on 2008-12-17
I have 5 mini-towers, all of which I assembled myself, 1 of which is running ipCop, 1 of which is running UBUNTU 8.04 server, 3 of which are running W2k Pro.  I'm wanting the UBUNTU server to be able to resize (and maybe rotate) images on the fly for www ... faster machine, more RAM.

I look at MBs and CPUs trying to figure out whether they would make a faster server.  Does UBUNTU actually exploit "DUO", "QUAD core", "Dual QUAD core" (I don't understand the internals)?  Does UBUNTU support 8GB RAM ... more?  Could I use one of these newer MBs that has NO IDE support (SATA only), only USB mouse support?

Thanks,
Stan

---

### Post by Sam Lars on 2008-12-17
I haven't personally tried this, but I don't see why it wouldn't work.  Ubuntu seems to be fairly serious about their server support.

---

### Post by tmillic on 2008-12-17
You'd be surprised at how little it takes for a well-configured server to work. If you're using one of your W2K as a desktop, then just install the Ubuntu server edition on your server and leave the gui desktop out. A LAMP configuration with the gd module will do what you want for image manipulation and without the GUI, you won't need much RAM or processing power at all. 
At home, I'm using a VIA C3 (1GHz) mini-itx for my server. It's much more than what the task demands, so it's folding at the same time and drawing a mere 40watts of power at peak. :) I bought it for less than $30 on ebay from a guy who couldn't figure out what to do with it.
If you check the mini-itx reviews on Newegg, you'll find that many others are using the low-power devices as servers, routers, etc. Unless its for a large business, anything more is just a waste of electricity and resources ($$$) that could go into your workstation or gaming pc.

---

### Post by tmillic on 2008-12-17
Heck. In my sermon, I neglected your last question. Ubuntu server will work with motherboards with just USB ports and SATA drives connections.

---

