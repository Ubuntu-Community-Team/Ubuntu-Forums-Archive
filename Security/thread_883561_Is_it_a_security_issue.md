---
title: "Is it a security issue?"
date: 2008-08-08
forum: Security
---

### Post by rayj on 2008-08-08
Hello, everyone! I'm a relative newbie...

I'm having an issue with no resolution as of yet. Symptoms:
-numerous 'attacks' displayed by Firestarter
-firestarter locking up
-USB mouse flashing often, when mouse is untouched
-mouse occasionally shutting completely down
-interface lockups and seemingly random bugs/crashes
-keyboard 'hanging' on random keys

I was running with Ubuntu Studio 7.04, and the issues became severe. I reformatted both of my SATA drives, and installed 8.04, and the same behavior continued. I'm suspecting a hardware issue, but it certainly could be an intrusion...reformatting was difficult, and I hadn't originally formatted both disks, so a 'hop' between drives is possible, right?

I'm not even sure where to look, but I will gladly post any data that could point towards the issue. Any ideas? Thanks in advance...

---

### Post by The Cog on 2008-08-08
I'm pretty sure it's not a security issue. 
I would start by doing the memory test offered by the startup screen.
Then I would double-check the CD you installed from. This command should give you the right checksum:
**md5sum /dev/cdrom**

---

