---
title: "usbmount by uuid (not vendor id)"
date: 2008-09-03
forum: Ubuntu Brainstorm
---

### Post by neerolyte on 2008-09-03
I assume I should probably put this up somewhere as a feature request but I didn't know where so I thought I would start here.

I want to mount certain usb drives in certain locations based on their uuid, eg I have a backup drive that isn't quite always on at boot or even always plugged in and I'd like it to always arrive at "/mnt/backup", but it doesn't get a useful vendor symlink so I have to use uuid. I couldn't see any obvious way of doing this with the current usbmount, so I've attempted to patch usbmount to provide this.

The attached patch file was generated using "diff -up" (I hope that's the normal format) and applies to "/usr/share/usbmount/usbmount".

To use the patch, first create a directory "/etc/usbmount/uuid_mappings". Then work out the uuid and the mount point you want and do something like: ```
# echo /path/to/mountpoint > /etc/usbmount/uuid_mappings/uuid-of-partition
```If anyone could tell me where exactly I should be posting this to try and get it introduced into the usbmount package that would be great.

---

