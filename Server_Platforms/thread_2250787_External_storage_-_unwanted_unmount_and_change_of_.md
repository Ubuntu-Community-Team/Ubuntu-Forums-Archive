---
title: "External storage - unwanted unmount and change of dev file"
date: 2014-10-31
forum: Server Platforms
---

### Post by emilije on 2014-10-31
Hi to all, my first post here :))

I have ubuntu server installed, running LAMP (desknow) and Webmin. It's a bit out of date installation but works like a charm - Ubuntu 8.04 and Webmin 1.510.

For backup purposes i have USB disk 1TB connected to the server, formatted as ext3 and mounted as /mnt/BackupDrive/ - backup goes daily at 23:59.

Here's the trouble: from time to time (few days - week or two) usb drive just disconnects (mount is not available anymore) and ubuntu changes external drive device file (it's not /dev/sdb anymore but sdc instead for example) so i need to mount it again manually. Sometimes it's /dev/sdb then it's automatically changed to /dev/sdc then it's sdd and so on.
There's no other external storage connected to the server. 

Anyone know why this is happening? 

Thank you!

---

### Post by steeldriver on 2014-10-31
I don't know why it would disconnect (possibly a power management issue, or hardware fault on either the drive or the USB port?) but I'd suggest using the partition's UUID or label in fstab instead of the /dev/sdxx device path. You can obtain the UUID using

```

sudo blkid -c /dev/null

```

---

### Post by lukeiamyourfather on 2014-10-31
What steeldriver said, also you could use a script to make sure the drive is mounted properly before running the backup.

---

### Post by emilije on 2014-11-04
guys, thank you for your help.

I went on site yesterday to see it with my own eyes :) First, there were two USB drives connected, and one of them failed totally(maybe this one caused mysterious unmount of the other one). I have disconnected bad drive and connected only working one. Re-mounted it using uuid, so ill monitor situation and post you results.

---

