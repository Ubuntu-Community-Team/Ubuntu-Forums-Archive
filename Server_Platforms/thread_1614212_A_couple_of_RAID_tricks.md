---
title: "A couple of RAID tricks"
date: 2010-11-05
forum: Server Platforms
---

### Post by Fafler on 2010-11-05
Hi. So i'm upgrading my RAID 5 array as we speak and thought i would give you all a few tricks for getting the most out of linux software RAID:

- Use serial numbers instead of devicenames. Look in /dev/disk/by-id/ and use those names instead. Now, you can re-arrange the drives any way you like, and still have everything work at startup

- Don't partition, just use raw devices. Atleast i can't find any reason to do so. It should also prevent issues with 4kb drives.

- If you do want partitions for some reason, use UIDs instead of devicenames or serial numbers.

- Make a cronjob that reads the entire array once in a while. This prevents silent read errors, that may break the array later on. Just had a RAID 5 array like that.
```

echo "cat /dev/md0 > /dev/null" | sudo tee /etc/cron.weekly/read-raid
sudo chmod +x /etc/cron.weekly/read-raid

```

- If you use encryption and have a multicore CPU, encrypt individual drives and put the mapped devices together in the array. This way, one instance of kcryptd is started for each device instead of one for the entire array, and the encryption is now scaled over as many cores as you have drives. Note, this also gives some overhead, because parity data is encrypted too. Still worth it on my C2D.

- Look at your /proc/mdstat once in a while. If you don't use local email (or haven't set it up correctly), you won't be warned if a drive fails. I missed a drive for a week without knowing, because a SATA cable fell out.

---

### Post by dtfinch on 2010-11-05
> - Make a cronjob that reads the entire array once in a while. This prevents silent read errors, that may break the array later on. Just had a RAID 5 array like that.
I believe this already happens, on the first Sunday of every month. /etc/cron.d/mdadm calls /usr/share/mdadm/checkarray, which writes "check" to /sys/block/md*/md/sync_action, causing the raid to do a full scan for inconsistencies. The results (number of mismatched blocks) is written to /sys/block/md*/md/mismatch_cnt. You can make it resync them by changing "check" to "repair".

As far as partitioning, I've been making them slightly smaller than the full drive, out of (maybe irrational) fear that if I buy a different model/brand replacement drive it might be slightly different smaller and thus unusable if I didn't, having noticed that my current drives are about 0.2% larger than their advertised size, 1000.2gb rather than 1000gb.

---

### Post by annoyingrob on 2010-11-05
I totally agree on using UUIDs rather than device names. I've had that problem before. In fact, I think any linux system should be using UUIDs rather than device names on ANY drive, not just raid drives.

---

### Post by Fafler on 2010-11-05
dtfinch: It might, but it didn't save my behind, so i'm still going for my own method.

You actually have a good point about different drives having different sizes. I use all WD15EARS drives in my setup.

---

