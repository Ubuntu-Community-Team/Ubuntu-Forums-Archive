---
title: "In need of cross-platform bandwidth monitor client"
date: 2006-11-11
forum: The Cafe
---

### Post by CSMatt on 2006-11-11
My university does not allow more than 650 MB of bandwidth to be used within a 24-hour period.  I have already exceeded this twice and got bused for it 2 months later (why the delay, I'm not sure).  In any case, I need something to monitor my daily bandwidth usage which can either cut me off or warn me when the 650 MB critical point is near.  The problem is that I want a cross-platform client, because I duel-boot Windows XP and Ubuntu.  Google searches mostly turn up "enforcer" software for servers and so far I have only found one client monitor (it is Windows-only, however).  I want to use the same client on both platforms so that they could possibly share data (such as time elapsed and bandwidth used) if I switch operating systems instead of reporting different bandwidths and times for each OS.  I would also prefer that the client be free software, but I'm willing to settle for proprietary freeware if need be.

Does anyone know where I could find such a program?

---

### Post by mips on 2006-11-12
I honestly do not know of a util that is available on both platforms.

What I would recommend though is a small fanless PC acting as a router/firewall etc which runs bandwidth usage software. Plonk it between your PC and the network and your done.

---

### Post by kewldude606 on 2006-11-12
Having it work the way you describe in both OSes would be mighty hard.  If you have another computer, you could route all of your traffic through it and have it total up the bandwidth.

---

### Post by CSMatt on 2006-11-12
Well, a hardware solution would be great, seeing as I use the same wall jack for other things as well, but I don't want another computer just so I can monitor my bandwidth.  Is there anything more simplistic?

---

### Post by mips on 2006-11-13
Another PC does not have to be big. It could be a mini-ATX board (dual ethernet) in a housing without monitor/keyboard/mouse.
[http://www.mini-itx.com/projects.asp](http://www.mini-itx.com/projects.asp)

Another option might be looking at something like RouterBoard 230, which offers a minimal 2 ethernet and wireless card slot. They also have smaller/bigger models available.
[http://www.routerboard.com/rb200.html](http://www.routerboard.com/rb200.html)

Both of the above could make for an interesting and fun project. I would love to get my hands on a routerboard.

The above options are small, fanless, headless and have options of what OS to use. You could always use them in the future or re-use them somewhere else. If you go the itx route the box could also serve as a nice server if you add a HD, assuming you are booting of flash currently.

---

### Post by adam.tropics on 2006-11-13
[http://netusage.mozdev.org/]("http://netusage.mozdev.org/") it's Australia oriented, but apparently adaptable.

---

### Post by CSMatt on 2006-12-07
Another potential problem with using another computer to monitor bandwidth is that the university might detect that two different devices are connected (although in a serial fashion as opposed to a parallel one) into the same jack.  This is evidentially considered to be "freeloading" on the university's bandwidth and is a policy violation unless the user pays a premium to use multiple devices in the same jack at the same time.  I really don't want to have to pay them more.

In the PC router setup, would any packet/MAC address monitors consider any traffic that goes through the bandwidth-monitoring PC to be coming directly from that PC, from the original device, or both?

---

### Post by mips on 2006-12-08
Just tell them it is a firewall to protect you from other student hackers...

I don't think they will pick it up that easily. The traffic will look like it is for/from the router pc unless they digg much deeper.

---

