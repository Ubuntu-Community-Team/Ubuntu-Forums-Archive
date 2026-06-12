---
title: "Ubuntu 11.04 Server - Samba share - right HDD, wrong stats (capacity etc.)"
date: 2011-08-09
forum: Server Platforms
---

### Post by ajc85 on 2011-08-09
Hi all,

Have purchased a HP Proliant Microserver to set up as a basic headless NAS device storing my media files.

Install of Ubuntu 11.04 Server on included 250GB HDD went ok, as did formatting new 2TB Hitachi HDD for media storage, install of Webmin, and adding 2TB drive as file share through Samba.

My problem though is this: the HDD stats (capacity etc.) are correct when check on server (250GB boot drive is sda and 2TB drive is sdb and mounted to \media\MEDIA), however when I map the 2TB drive (using directory \\[servername]\media\MEDIA where it's mounted) on Windows Vista laptop as a network drive so I can copy all my media across it seems to map successfully EXCEPT THAT the drive shows as having a capacity of only 224GB!!!

This sounds suspiciously like the formatted capacity of the 250GB boot drive of my server, but I can't figure out how the mix-up has occured or how I can fix it?!?!

I'm a complete linux newbie and have no idea what to do.  Please help :)

---

