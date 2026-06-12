---
title: "Ubuntu Server Boot to RAM from a Flash Disk"
date: 2009-01-22
forum: Server Platforms
---

### Post by ComputerHQ-UK on 2009-01-22
Hi,

I am looking to have Ubuntu Server installed on a 4GB flash drive that I would like to then load in to ram on startup.

I am aware of the MTBF of flash drives, which is why I want it to load in to RAM (4GB 800Mhz), as this server will be running all the time, once loaded there should be no need to access the flash drive.

The system when complete will contain two 500GB RAID 0 drives for data storage, now I could install another disk to run the OS, but I want to lower the power requirements for this server.

I am also aware that I would need to make sure that the log file will have to be redirected either to a remote server or to the mirrored HDD.

Also another point would be to have any configuration files stored on the mirrored HDDs.

Is something like this possible?  Or am I wasting my time?

Thanks :)

---

### Post by cdenley on 2009-01-22
So you're trying to limit writes to your root filesystem by loading the entire filesystem into memory? A much more efficient solution would be to use the root filesystem read-only, then write only the changes to memory.
[http://ubuntuforums.org/showpost.php?p=5720661&postcount=5](http://ubuntuforums.org/showpost.php?p=5720661&postcount=5)

---

### Post by Terc on 2010-03-04
I'm also very interested in booting to ramdisk with the server flavor of ubuntu.  Very similar reasoning, but I'd like to be able to roll out updates by dd'ing over the boot partition and rebooting.

---

### Post by psusi on 2010-03-04
Or you could just install the server onto those two raid drives... you don't need another one.

---

