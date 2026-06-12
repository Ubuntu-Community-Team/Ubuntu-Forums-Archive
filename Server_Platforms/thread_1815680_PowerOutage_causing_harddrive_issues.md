---
title: "PowerOutage causing harddrive issues"
date: 2011-07-31
forum: Server Platforms
---

### Post by rubicks on 2011-07-31
I'm running an atom based 10.04.3 server and we've had several electrical outages and i think that messed up my harddrives.

i can still ssh in, but I can't use AFP to connect to the server and when i use samba i can't move any data due to input/output errors.  and when i'm ssh'd in, i'll get this sometimes:
"ls: reading directory .: Input/output error"

[http://ubuntuforums.org/showthread.php?t=1815616](http://ubuntuforums.org/showthread.php?t=1815616)
[http://ubuntuforums.org/showthread.php?t=1815071](http://ubuntuforums.org/showthread.php?t=1815071)

those are 2 other posts i made before finding out about the harddrive issues.  but those were in the networking section, so hopefully this section will be able to help me figure out what to do.

please help :)

---

### Post by rubicks on 2011-07-31
i did a reboot, and some of the missing files showed up, but now Transmission is saying some files are missing but when i use the terminal to go to those locations the files are there.

---

### Post by Vegan on 2011-07-31
better backup and save you files onto a USB disk before you lose it all

---

### Post by Wim Sturkenboom on 2011-08-01
^ +1

And next run the HD manufacturer's analysis tools to check the state of the HDs.

If they come out without bad blocks, do a re-install; probably easier than trying to fix corrupted files.
If they come out with bad blocks, replace the HDs and do a re-install.

---

