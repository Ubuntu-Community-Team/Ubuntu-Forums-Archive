---
title: "Bacula quick start guide for server setup?"
date: 2013-02-27
forum: Server Platforms
---

### Post by MakOwner on 2013-02-27
Is there a concise, quick setup guide for Bacula on Ubuntu?

Googling sent me to this [http://www.bacula.org/manuals/en/install/install](http://www.bacula.org/manuals/en/install/install)
While this is great and all, trying to walk through the "quick start" of setting Bacula and I just seem to wander in circles following links that take me back to the same place...

I'm setting it up on a headless (thus no GUI) server with a SCSI attached Dell LT02 autochanger.

I'm thinking this isn't really that hard, but having never touched the software some - even the vaugest - hints at the correct direction would sure help.

---

### Post by Habitual on 2013-02-27
[https://help.ubuntu.com/community/Bacula](https://help.ubuntu.com/community/Bacula)

---

### Post by MakOwner on 2013-03-09
> **Habitual said:**
> [https://help.ubuntu.com/community/Bacula](https://help.ubuntu.com/community/Bacula)

If that worked, it would be great.
Any other guides that might work?

---

### Post by Habitual on 2013-03-12
the Official documentation doesn't work?
I'd retrace the steps...Is it installed?

---

### Post by MakOwner on 2013-03-14
It's installed - via apt-get at the command line. 
bacula-console just hangs.

I have a Dell PV122T changer with an LTO2 drive.  
Still haven't found a configuration for bacula-sd.conf that appears to do anything but cause bacula-console to get even weirder.


All I need is something to copy data  onto to LTO2 tapes that can span large files across multipl volumes.
This really doesn't have to be the rocket science torture that it's turning into.

---

### Post by hiflyer on 2013-03-29
try this tutorial. I got mine working using this as the basic. 
[http://webmodelling.com/webbits/miscellaneous/bacula.aspx#bacula-main-components](http://webmodelling.com/webbits/miscellaneous/bacula.aspx#bacula-main-components)

hope it helps:KS

---

