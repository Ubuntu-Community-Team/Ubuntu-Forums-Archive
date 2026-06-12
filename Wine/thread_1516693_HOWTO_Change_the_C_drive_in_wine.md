---
title: "HOWTO: Change the C: drive in wine"
date: 2010-06-24
forum: Wine
---

### Post by Moyamo on 2010-06-24
This is a simple manual on how to change the c: drive in wine.  

1) Go to the ~/.wine directory
2) There is a directory called dosdevices. Go there
3) You should see a link c:(and sometimes c::).  Make sure this is a link
4) Delete the link c: (and c:: if present)
5) Make a link to the desired c: drive and paste it in the ~/.wine/dosdevices directory (if c: drive is a external device that is mounted make a link to the /dev/xxxx file e.g /dev/sda5)
6) Rename that link c: (and the link to the /dev/xxxx file c::)
7) type ```
winecfg
``` in the terminal
8) On the window that pops up click on the drives tab on the top corner.
9) If in the drive mappings the c: drive is the directory you wanted then you have successfully changed the c: drive!


Hope this helps

---

### Post by hikaricore on 2010-06-24
It should be mentioned (since you didn't) that one should NEVER link their wine "C" drive to an actual windows installation drive.
Unless of course they want to totally screw up their copy of windows in which case by all means go for it..

---

### Post by Moyamo on 2010-06-24
I didn't know that. :confused:

---

### Post by hikaricore on 2010-06-24
This is why we bother reading the documentation..

[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

Section 3.1

> WARNING: Do not try to configure Wine to point to your actual Windows C:\ drive. This will break Windows and require a reinstall. We have tried to make this hard to do so you probably cannot do it by accident. If you do manage this, Wine may or may not continue to operate, but your Windows install will be 100% dead due to critical parts of it being overwritten. The only way to fix Windows after this has happened is to reinstall it. 

---

