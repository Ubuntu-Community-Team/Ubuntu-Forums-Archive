---
title: "kernel log flodding klogd"
date: 2009-10-07
forum: Server Platforms
---

### Post by shizzy-t on 2009-10-07
I have an IBM server with Ubuntu 8.04 LTS installed.  Currently I'm having an issue with the IBM ServeRaid management software.  The software is running fine, there is however an issue where it floods syslog (/var/log/syslog) with an error message every 4 seconds.  This is a known bug and IBM claims it's a problem with the "new" linux kernel.  What ever that means.  The software does actually works fine but I would like to have it stop flooding the kernel logs.  

If I turn off klogd then the flooding stops but this is not a good setup. I've tried to create my own system map for klogd that has all of the scsi and sg entries removed but the flooding continues.  

So if anyone out there has any good ideas on how to stop kernel messages from the sg or scsi kernel modules I would very much appreciate it.  

The error message is...

sg_write: data in/out 404/404 bytes for SCSI command 0xd--guessing data in;
program java not setting count and/or reply_len properly

---

