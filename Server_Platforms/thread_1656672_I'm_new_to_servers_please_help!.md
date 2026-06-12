---
title: "I'm new to servers please help!"
date: 2010-12-31
forum: Server Platforms
---

### Post by GeekGuy96 on 2010-12-31
So a few weeks ago I bought 2 old rackable systems phantom 4 v4.5.  Until a few days ago I had no time to install the os and when I install ubuntu 10.10 server on the first the install went fine but after it booted it sat there with a blinking _ and never did anything else.  So I reinstalled and the problem went away.  But now when it boots it list errors so fast I can read any of them.  The second problem happened on the second server too.  Can someone please help me.  I have used ubuntu before but I'm not very good at the terminal side of things (I plan to install a GUI on ubuntu server). 

Thanks so much,
  GeekGuy96

P.S. The servers have dual 2.8 ghz intel xeon's with 2 gigs of ram per processor.

---

### Post by rubylaser on 2011-01-01
You can view the boot errors by typing
```
dmesg
``` in a terminal.  I would guess what you where seeing is not errors, but the normal Ubuntu non-GUI boot process.

---

### Post by woodman231 on 2011-01-03
You may want to uninstall and re-install again.  After you re-install these should be the first commands you do once you have logged in to the OS:

```

sudo apt-get update
sudo apt-get install ubuntu-desktop
reboot

```

Thanks,
Sean W.

---

### Post by cariboo on 2011-01-03
If you install the ubuntu-desktop meta package you're going to get a full desktop installation with an office suite  and many programs that you don't need on a server. If you really need a gui on a server, I would suggest lxde, it's is a much lighter desktop, and you don't get a lot of what you don't need.

Instead of installing a desktop, I would suggest [webmin]("http://http://www.webmin.com/"),  once you have the servers up and running, you can unhook the monitors and keybaords and do all the administration remotely.

---

