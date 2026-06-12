---
title: "[SOLVED] Suggestions for a Live Ubuntu Web Server Firewall?"
date: 2008-07-25
forum: Server Platforms
---

### Post by CrusaderAD on 2008-07-25
We're planning on launching a php website on a Ubuntu server we put together. What would be a good firewall to apply in front of the server? Are there any suggestions for a Ubuntu Server?

---

### Post by Endwin on 2008-07-25
I have always been a fan of shorewall. Simple config files, lots of potential power, and their website goes through a lot of the common stuff people want. Also it is in the repositories.

[http://www.shorewall.net/]("http://www.shorewall.net/")

---

### Post by CrusaderAD on 2008-07-25
Thanks but we're thinking of something along the lines of "hardware" such as a Sonicwall or Barracuda.

---

### Post by Uluen on 2008-07-25
Check out [m0n0wall]("http://m0n0.ch/wall/") on [hardware]("http://linitx.com/viewproduct.php?prodid=11954") from pc-engines, great stuff.

---

### Post by TommyJernberg on 2008-07-26
Or try PFSense which is a forkproject of m0n0wall.

[www.pfsense.com](www.pfsense.com)

---

### Post by songshu on 2008-07-26
i have an old machine without harddisk 600mhz celeron 128MB RAM and i guess it was purchased somewhere in the year 2000.
it has been running monowall for 4 years straight now (no reboot), so if the feature set is OK to you i can definitely recommend it.

---

### Post by moep on 2008-07-26
> **TommyJernberg said:**
> Or try PFSense which is a forkproject of m0n0wall.

[www.pfsense.com](www.pfsense.com)

I second this. pfsense is absolutely amazing.

---

### Post by antilog on 2008-07-26
I used Smoothwall for a while on an old machine, and it has a great feature set, and super simple to install and administer, lots of addons.  I needed the machine for something more important, and now use a WRT54GL running DD-WRTv24, which is a great gateway itself.  The only consideration I can see at this point would be if I needed extreme number of connections and routing work, I would rather have a PC CPU+heatsink than the WRT54GL.

[http://smoothwall.org](http://smoothwall.org)

Also, these solutions are free, except for hardware costs.  I think I paid $70 for the WRT54GL hardware, and like I said Smoothwall was on an old PC that was lying around.

---

### Post by CrusaderAD on 2008-07-26
Thanks for all the great replies... PFsense looks good. I've tried smoothwall in the past. Great Stuff!

---

