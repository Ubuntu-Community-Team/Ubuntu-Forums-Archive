---
title: "Unable to install Ubuntu 14.04.x on NEW Dell M830 Server"
date: 2015-07-21
forum: Server Platforms
---

### Post by allezlesbleusno1 on 2015-07-21
Hi, 

I've been trying to install Ubuntu 14.04.2 Server on a brand new Dell M830 through iDrac by mounting the ISO, I can successfully partition the drives, install the OS and then right after selecting any packages to install, I receive the following error:[INDENT][I]
an installation step failed. you can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: select and install software[/I][/INDENT]

This happens whether I select a package or not.  I've tried to skip selecting any packages by attempting to select the next option (install grub) but everything fails at this point with the same message. 

I've tried different ISOs (Ubuntu 14.04 and 14.04.1) and the same error occurs. 

Any ideas as to what could be causing this and how to get past this ? 

FYI I was able to install CentOS 7 on this same server without an error so this definitely seems to only occur with Ubuntu.

---

### Post by allezlesbleusno1 on 2015-07-22
After looking inside of the /var/log/syslog, I found out that the disk where it was writing to was running out of space.  Upon closer inspection, it was revealed that when using the LVM guided partition it was attributing 1G of disk space to the root partition and 550G to the swap.   I had to manually create the partitions to fix this.

---

