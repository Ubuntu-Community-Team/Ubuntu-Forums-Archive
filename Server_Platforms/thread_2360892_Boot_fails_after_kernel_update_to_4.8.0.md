---
title: "Boot fails after kernel update to 4.8.0"
date: 2017-05-09
forum: Server Platforms
---

### Post by afrancescon on 2017-05-09
Dear all,

I have a problem with Ubuntu Server 16.04 installed on my PC. Ubuntu Server 16.04 came out with 4.4.0 kernel but, in order to make my wireless board working I need to update to 4.8.0.
I freshly installed Ubuntu Server on the 32GB eMMC of my PC (64 bit system). After the installation I ran an apt update/upgrade to upgrade my system and then used:

```
sudo apt-get install linux-virtual-hwe-16.04
```

to upgrade kernel to 4.8.0 and it work without errors.

Unfortunately, after reboot, I have following error:

```

Begin: Running /scripts/local-block ... mdadm: CREATE group disk not found
mdadm: No devices listed in conf file were found.

```

repeated some times: after that:

```

Gave up waiting for root device. Common problems:
...
ALERT! UUID=... does not exist. Dropping to a shell!

```

In the shell I tried:

```
blkid
```
```
cat /etc/fstab
```
```
cat /proc/partitions
```

but each one provide empty result!

Rebooting the previous kernel (4.4.0) works fine but I really need 4.8.0 version of the kernel. Any idea?

Thanks for support
Ale

---

### Post by howefield on 2017-05-09
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2017-05-09
1. Is there a specific reason you installed linux-virtual instead of linux-generic? I have always used linux-generic even on virtual servers.

2. Do you use mdadm arrays at all or not? A message that mdadm didn't find any arrays is normal on systems that don't have mdadm arrays. But mdadm still checks on that on boot.

3. UUID does not exist can sometimes be false message, if it can't detect the partition UUID on time, or simply fails detecting it for whatever reason. There was one procedure to avoid that check I think, but I would have to search to find it. And if the message is not false (if the partition can't be found really), then you have another type of problem and you will need to check why it can't be found. Maybe because it is on eMMC card...

---

