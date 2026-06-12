---
title: "Finding a CDROM device (Python, if it matters)"
date: 2010-11-04
forum: Ubuntu Dev Link Forum
---

### Post by TJRC on 2010-11-04
I'm a casual programmer (i.e., I'm no longer a professional, I just program for fun or for my own projects), usually in Python (although I don't think this is a Python-specific question).

I'm writing a program that catalogs CDROMs, and need to go through the directory of the CDROM given the device.

On Windows, I use something like

```

startpoint="D:/"
for (root, dirs, files) in os.walk(startpoint):
  (stuff)

```Is there an equivalent starting point in Linux?

I've tried ```

startpoint="/dev/sr0"
and
startpoint="/dev/sr0/"

```but no luck.

What does work is 
```
startpoint="/media/VOLUMENAME"
```where VOLUMENAME is the name of the mounted CDROM volume; but I need to be able to do this without knowing the volume name.

Any ideas?

---

### Post by TJRC on 2010-11-07
After some experimentation, it seems like a working approach is to call the Linux "volname" command (hat-tip to Steven D'Aprano on the python-tutors list for identifying the command for me) to find out the volume, and then use the volume name to specify the directory in /media.  Here's what I'm doing now:

```

import subprocess, os
def getvolid(mountpoint):
     p = subprocess.Popen(["volname", mountpoint],
         stdout=subprocess.PIPE, stderr=subprocess.PIPE)
     (response, errmsg) = p.communicate()
     volid=response.rstrip()
     errmsg = errmsg.rstrip()
     if len(response)==0:
         volid=None
     return (volid, errmsg)
```I use it thus:

```
cdrom_dev="/dev/sr0"
(volid, errmsg) = getvolid(cdrom_dev)
if volid is not None:
    for (r, d, f) in os.walk("/media/"+volid):
        print (r, d, f)
else:
    print "Error retrieving volume id, '%s'" %(errmsg)
```

---

