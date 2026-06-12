---
title: "Software RAID HELP"
date: 2010-11-03
forum: Server Platforms
---

### Post by djanie78 on 2010-11-03
I have setup software RAID 5 but everytime my system restarts i have to do the setup again. My data is all there. Is there something am missing? :confused:

---

### Post by rubylaser on 2010-11-03
Have you created an mdadm.conf file, and added the array to your /etc/fstab?

Here's how to generate an mdadm.conf
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

And your /etc/fstab line should look something like this...
/dev/md0	/storage	    ext4	defaults	0	0

That should do it for you.

---

### Post by djanie78 on 2010-11-03
looks like these files are all there just like you said but i still have the same issue. Mind you ther files where generated when i setup the raid

---

### Post by djanie78 on 2010-11-03
> **djanie78 said:**
> looks like these files are all there just like you said but i still have the same issue. Mind you ther files where generated when i setup the raid

Hang on a minute. I apologise rubylaser. I followed your instructions on creating a mdadm file and that looks to have sorted the problem.

Thanks

---

### Post by rubylaser on 2010-11-03
Good glad to hear it.  Now, you'll want to setup smartmontools to monitor the disks in your array to automatically alert you if one fails a SMART test.

---

### Post by djanie78 on 2010-11-03
> **rubylaser said:**
> Good glad to hear it.  Now, you'll want to setup smartmontools to monitor the disks in your array to automatically alert you if one fails a SMART test.

Thanks
Will get on this later today. Big help. Thanks

---

