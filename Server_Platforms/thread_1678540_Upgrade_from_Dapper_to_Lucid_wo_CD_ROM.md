---
title: "Upgrade from Dapper to Lucid w/o CD ROM"
date: 2011-01-30
forum: Server Platforms
---

### Post by murrellr on 2011-01-30
I have an IBM eServer xSeries 350 that has Dapper (6.06) server installed.  I have not been able to upgrade from Dapper because later versions will not properly recognize the CD-ROM.  Now I need to update, so I am trying to do that from apt-get.  The instructions I've found in the documentation say to change the contents of /etc/apt/sources.list to point to the desired repositories, but there were little examples to show how.  I tried to change the word 'dapper' to 'lucid' in the existing file, but there was an error trying to read a package list.  I then found an example of the file for loading 'hardy', but this produced several loading errors and now the system is unbootable.  Is there a way to update or install lucid without a CD-ROM drive?

---

### Post by koenn on 2011-01-30
can it boot from USB ?
PXE network boot ?
floppy disks ?

---

### Post by doogy2004 on 2011-01-30
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by Vegan on 2011-01-30
I would replace the DVD drive on the server first. Then you can install an update as needed.

---

### Post by murrellr on 2011-01-31
Thanks doogy2004, this is exactly the information I was looking for.  And thanks to the others that responded.  I have already replaced the CD-ROM drive and have confirmed that its an incompatibility between the driver that Ubuntu auto selects and the IBM hardware.  The server BIOS doesn't support USB boots and I don't have a way to create the floppys.

---

### Post by murrellr on 2011-02-02
The update from 6.06 to 8.04 went OK, but the update from 8.04 to 10.04 has left my machine unbootable.  All the kernel selections in the GRUB menu fail to load and end up in a maintenance prompt.  Based on my past experiences with Linux, I'm not surprised.  Can this be repaired?  Has anyone else tried to update from 6.06 to 10.04?

---

### Post by doogy2004 on 2011-02-03
> **murrellr said:**
> The update from 6.06 to 8.04 went OK, but the update from 8.04 to 10.04 has left my machine unbootable.  All the kernel selections in the GRUB menu fail to load and end up in a maintenance prompt.  Based on my past experiences with Linux, I'm not surprised.  Can this be repaired?  Has anyone else tried to update from 6.06 to 10.04?

I know it is late now but the instructions for 6.06 to 8.04 are here - [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

---

