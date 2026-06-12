---
title: "Ubuntu One won't connect"
date: 2009-11-05
forum: Ubuntu One (CLOSED)
---

### Post by Acoustyk on 2009-11-05
I've had Ubuntu NBR 9.10 installed since the release date and have had a relatively good experience except for ubuntu one.  I'd really like to explore how it functions but it won't stay connected.  It turns into the opaque cloud for a fw seconds then returns to the cloud with an exclamation mark in the center.  I used to have capability mismatch errors but now this.  Any ideas?

Much Thanks

---

### Post by gpaterson on 2009-11-06
I had this problem as well, but I managed to solve it by deleting the ubuntu one config files from my home directory.

First, stop the ubuntuone client if it is running.

Then look in the .config directory there will be a directory called ubuntu one, containing a couple of .conf files. Delete these then restart the ubuntuone client and it should start synchronising again.

Hope that helps.

---

### Post by Acoustyk on 2009-11-07
I tried deleting the files but now when I launch UbuntuOne it doesn't stay open.  I have the icon set to always show but it doesn't come up anymore.  I've never seen it actually work but I imagine UbuntuOne is a lot like dropbox is that correct?

---

### Post by jasonmh on 2009-11-15
Ubuntu One serves the same purpose as DropBox, but so far it doesn't seem as reliable.  I had the same disconnect issue until I deleted the configuation files.  That fixed the problem for about 2 minutes, and now I'm back to the disconnection problem.  I probably just need to reboot, which would be ridiculous if that's the case.

---

### Post by frogotronic on 2010-10-20
> **gpaterson said:**
> I had this problem as well, but I managed to solve it by deleting the ubuntu one config files from my home directory.

First, stop the ubuntuone client if it is running.

Then look in the .config directory there will be a directory called ubuntu one, containing a couple of .conf files. Delete these then restart the ubuntuone client and it should start synchronising again.

Hope that helps.

Awesome!  This completely worked.

- CH

---

### Post by cariboo on 2010-10-23
This is really an ubuntuone problem, has has nothing to do with UNE. Moved to the Ubuntuone sub-forum.

---

