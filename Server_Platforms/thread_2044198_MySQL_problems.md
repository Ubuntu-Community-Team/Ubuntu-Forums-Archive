---
title: "MySQL problems"
date: 2012-08-18
forum: Server Platforms
---

### Post by jpcjr on 2012-08-18
Hi all,
 
I had a functional lamp, mail and samba server until the hdd croaked =(
 
I have replaced the drive and installed esxi host this time and installed the lamp server, gotten email functional. But after I installed the vmware tools inside the vm mysql has quit working. All attempts to bring it back up fail. Please help
 
I have a screenshot of the error

---

### Post by spjackson on 2012-08-19
It looks like you have no /tmp directory.
```

ls -l /
ls -l /tmp/

```

---

### Post by LHammonds on 2012-08-19
The only times I ran into problems running my server is when I have run out of space.  Make sure the important partitions are not full.

```
df -h
```

LHammonds

---

### Post by jpcjr on 2012-08-19
Thanks for the replies and sorry it has taken me so long to reply. I did delete the tmp directory when vmware tools had an install issue that I finally resolved. I guess I am still used to windows where the tmp directories get recreated. 

I have now made a new tmp directory and am rebooting the server.

What permissions does the /tmp/ directory need?

---

### Post by LHammonds on 2012-08-19
> **jpcjr said:**
> What permissions does the /tmp/ directory need?All of them including the sticky bit.

IIRC: chmod 1777

---

### Post by jpcjr on 2012-08-19
Thank you both so much! I had just finally found that command through my seemingly endless google search, lol. I am back in business.

You guys rock!  :guitar:

---

