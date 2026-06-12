---
title: "&quot;Disks&quot; application not opening"
date: 2014-12-23
forum: System76 Support
---

### Post by dimethyl on 2014-12-23
Hi all,
I was trying to open a cd rom on my system 76 gazelle pro, and after putting the disk in the tray and closing the tray , I could not find the disk.  I tried to open the "Disks" application and a window popped up telling me "Sorry, Ubuntu 14.04 has experienced an internal error."

the gnome-disk-utility 3.10.0-1ubuntu3 package crashed.

the title is " gnome-disks crashed with signal 5 in_start() "


i would like to post more information the "Report a problem..." application gave me but I cannot copy and paste directly from it.

I did send an error report of this problem.

Can anyone tell what the problem is from this information?

Thank You

---

### Post by Q-collective on 2014-12-23
If you open Files, does the cd-rom appear in there?
If not, is the optical disc station seen with the terminal commans lshw (which lists all your hardware)?
If not, you may have a broken optical disc station.

---

### Post by dimethyl on 2014-12-24
The cd is not in files, and there is no mention of anything disc or cd related with the terminal command lshw. 

Strangely, the system testing application does see it and tells me it is a "TSSTcorp CDDVDW SN-208AB"

I don't understand how the system testing application is the only way i can see the disc station is there at all.  Where do i go from here?

*Update*

I restarted the computer and now the disc drive is fully functional.  Very weird.

---

