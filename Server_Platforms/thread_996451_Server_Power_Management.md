---
title: "Server Power Management"
date: 2008-11-28
forum: Server Platforms
---

### Post by lateralus01 on 2008-11-28
I've had a desktop in my room for a while and it's been just sitting there.  Well I thought a great use for it would be to use it as a server to manage some resources I had lying around but not using because I work mainly on a laptop and I don't carry around a printer or my external hard drive.  So after a few hours of configuring I made good use of the desktop and its now running Ubuntu Server 8.10 and it's configured as a print server, hosts windows shares with samba, a proxy server, a ssh server, and a proxy server for getting around that uncomprehensive blocker at my high school.  Anyway I really don't want to raise the power bill a ton running it all the time so does anyone know the best way to conserve power?  I've already used hdparm to set a spindown time on both hard drives for 5 mins but what else can I do?  It doesn't use a monitor so that's another plus but I still want to conserve more.

Any suggestions?

Thanks,
Lateralus01

---

### Post by Thirtysixway on 2008-11-28
I don't know how much it's worth doing, but if it's a server you can pull things out like soundcards and other things that you don't plan on using.

You could also ssh into it and shutdown at night, then press the power button in the morning but that may get annoying after a while.

---

### Post by Philio on 2008-11-29
> **Thirtysixway said:**
> I don't know how much it's worth doing, but if it's a server you can pull things out like soundcards and other things that you don't plan on using.

You could also ssh into it and shutdown at night, then press the power button in the morning but that may get annoying after a while.

Or you could probably automate that, setup a cron job to shut down the server and use the bios wake up feature (assuming it has it).

---

