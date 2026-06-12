---
title: "[SOLVED] Ubuntu Server on VMWare server error"
date: 2007-08-16
forum: Server Platforms
---

### Post by keymoo on 2007-08-16
Hi there,

I'm trying to install Ubuntu Server 7.04 on my Windows XP Pro machine (the host). I am user VMWare Server 1.0.3 as the VM software. I have tried twice to install Ubuntu on here but it always hangs at this screen:

[IMG]http://farm2.static.flickr.com/1398/1135613145_2389bea3db_o.png[/IMG]

Any ideas?

Thanks.

---

### Post by PilotJLR on 2007-08-16
Click inside the window and press Enter... see if the login prompt then appears.

---

### Post by keymoo on 2007-08-16
How embarrassing! Thanks, that worked fine. Oh man...

---

### Post by PilotJLR on 2007-08-16
No worries. When this first happened to me, I stared at the screen for a good minute or two before deciding to press some keys.  :-)

This doesn't normally happen, by the way. I've ONLY seen this with Ubuntu Server VM in a Windows host. This quirk doesn't occur on bare metal, or with a Linux host, or with an ESX host.

---

### Post by p_quarles on 2007-08-16
I actually *did *have that happen to me a couple times, when my server required personal attention. I normally use ssh, but have hooked up the monitor/keyboard a few times, and I've had this on an intermittent basis.

---

