---
title: "Server Monitor Power Management"
date: 2008-10-05
forum: Server Platforms
---

### Post by IMSargon on 2008-10-05
I have Ubuntu Server installed on a laptop acting as a home server. The LCD, despite blanking, seems to be on all the time. I would like the LCD to shut off completely. X is not installed. My BIOS has no relevant options. setterm seems to have no effect. Anyone have a magic command for me?

---

### Post by gypsy84 on 2009-01-24
Bump.
I have the exact same problem.
Can someone please help?

---

### Post by KenSharp on 2012-06-22
Bump bump.

I've searched like mad for a solution but cannot find one. I tend to keep the monitor off (with it being a server system) but sometimes it can be left on for long periods of time.  I would prefer it go into a low power state.

The DPMS stuff seems to be linked to X. In fact, it all seems to be linked to X.
[http://packages.ubuntu.com/search?searchon=names&keywords=dpms](http://packages.ubuntu.com/search?searchon=names&keywords=dpms)

I cannot see a way to do this for a server machine without X.

I'm sure there must be a way to do this.

---

### Post by rubylaser on 2012-06-22
I just manage my headless servers via SSH, but Google turned these [solutions]("http://askubuntu.com/questions/62858/turn-off-monitor-using-command-line") up for me. 

They do seem to rely on X server though.  The easiest way would be to turn the monitor on when you're using it and off when you step away. Or, use an electronic timer to cut the monitor power at a certain time.  But these are certainly not as slick as automatic :)  It appears you'll need X to make this work.

---

### Post by CharlesA on 2012-06-22
Yep.

If you have furter questions please start a new thread instead of reviving one from 2008.

---

