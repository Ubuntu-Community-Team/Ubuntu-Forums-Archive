---
title: "why does mdadm refuse to name devices properly?"
date: 2011-11-18
forum: Server Platforms
---

### Post by MakOwner on 2011-11-18
I think I have gone through this the last 5 or 6 times I have built software raid arrays.

I build a raid device as /dev/md2, sync it, partition it and create the filesystem.

I do mdadm --detail --scan  and store the output in the mdadm.conf file.

I reboot and the array gets built as /dev/md127.

the mdadm.conf file looks like this right now:
```

ARRAY /dev/md/PE8502:2 metadata=1.2 name=PE8502:2 UUID=8f9addca:645ae425:c977187f:3f41817b

```

I have also tried it like this:
```

ARRAY /dev/md/2 metadata=1.2 name=PE8502:2 UUID=8f9addca:645ae425:c977187f:3f41817b

```

Will changing the name= parameter force the device name?


And the answer to that question is no, no matter what I do -- even completely destroying and rebuilding the array and after reboot the device comes back as /dev/md127.

I stopped the array, zeroed the superblocks of each component device, rebuilt everything.
Still no joy.


Did find this in syslog:
```

Nov 18 16:00:36 PE8502 mdadm[1031]: DeviceDisappeared event detected on md device /dev/md2
Nov 18 16:00:36 PE8502 mdadm[1031]: NewArray event detected on md device /dev/md127

```

---

### Post by MakOwner on 2011-11-18
47+ reads.  You guys enjoy watching someone flail, don't you? :/

The "device disappeared event" was the clue I needed.
Google turns up this, while the answer to this thread wasn't for me, the hint I needed was.


[http://fossplanet.com/f12/mdadm-device-reassignment-106141/](http://fossplanet.com/f12/mdadm-device-reassignment-106141/)

update-initramfs -u 

did the trick.

---

