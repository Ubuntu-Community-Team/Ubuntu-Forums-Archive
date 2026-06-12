---
title: "HBAnywhere on 6.06LTS"
date: 2007-07-15
forum: Server Platforms
---

### Post by olival.junior on 2007-07-15
Hi,

I'm running Ubuntu 6.06LTS Server on some Dell 2850 PowerEdge Servers. 
The storage people at my job installed Emulex LP9000 and LP11000 HBAs on these servers. So far, so good. Ubuntu has the lpfc module and recognized the HBAs (and the disks attached to them) just fine.

The problem is: neither Ubuntu nor Debian comes with an utility like Emulex HBAnywhere (lputil, etc) so we can manage the Emulex cards (install firmware, probe wwn, etc). I googled about the problem but was unnable to find a satisfactory solution so far.

One guy managed to install the HBAnywhere by Emulex (a tarball with rpm packages and an install script designed to run only on Red Hat and SUSE Enterprise), but he had to convert all the rpm packages to deb (using alien), to manually install them and recompile what was possible. He said that some things didn't work after all.

Switching Emulex to another HBA maker isn't an option.

So, I ask you if anyone knows about some utility to manage Emulex HBAs on Ubuntu (like HBAnywhere on rpm based systems).

TIA,

olival.junior

---

### Post by RichJacot on 2007-09-07
I'm very interested in this also!

How have you made out?

---

### Post by Brazen on 2007-09-07
IIRC, with qlogic cards anyway, you could actually install their SanSurfer software on a workstation and then remotely upgrade the firmware.  I don't think there was any install necessary on the server.  This sounds like a stretch though, I may be remembering it wrong.  Unfortunately, this is why I stick with RedHat on our servers at work :(  I hope someday Conanical can convince such vendors to supply deb packages along with their rpm packages.

---

### Post by fly3rman on 2007-10-05
Same Problem here, anyone any success?

---

### Post by Robstarusa on 2008-06-19
I'm also looking for a solution....

---

