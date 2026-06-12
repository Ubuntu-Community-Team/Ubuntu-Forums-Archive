---
title: "New LAMP server build with SSD for OS and 2 mirrored RAID1 for data"
date: 2015-10-16
forum: Server Platforms
---

### Post by jonah1980 on 2015-10-16
Hi sorry if I'm posting in the wrong place...

I'm putting together a server rack which will hopefully have an SSD for the OS but a RAID1 for the data. So any websites served up are stored on the raid separate from the boot drive... This seems reasonably common when reading up on Windows Server setups but I've never done this with Linux, only configured RAID to use and include the OS!

I just wondered what the correct steps are using Ubuntu Server 14.04 LTS for this or if there are any guides out there for this setup?

Should I just make up the system with only the SSD in place, then install LAMP etc, then add the raid drives and try configure those or is there a way to set this all up off the bat?

Thanks very much for any help. :)

---

### Post by SeijiSensei on 2015-10-16
You can create a separate "mount point," actually just an empty directory, and mount the RAID on that.  
```

sudo mkdir /data
sudo mount /path/to/the/array /data

```

Now if this is a "fake RAID" system which requires a proprietary driver for Windows, you may find the RAID array is not supported.  Most people running RAID in Linux use the "software RAID" components that are part of the Linux kernel.  Some other widely-used [hardware RAID controllers]("https://wiki.debian.org/LinuxRaidForAdmins") like ones from Adaptec and LSI Logic are also well supported in Linux.  I suggest booting from the Ubuntu Server DVD, then seeing what it discovers in terms of the array.  You should also try CentOS, a free "respin" of RedHat Enterprise Linux, if Ubuntu doesn't see the array because RedHat may have better support.

---

