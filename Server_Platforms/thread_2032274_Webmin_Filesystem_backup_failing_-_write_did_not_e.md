---
title: "Webmin Filesystem backup failing - write did not end on a block boundary"
date: 2012-07-23
forum: Server Platforms
---

### Post by antiartist on 2012-07-23
Using the Webmin Filesystem Backup module, my scheduled backups have been failing lately. Unsure of how to proceed.  The last few lines in the filesystem backup log are:

tar: /sys/devices/pci0000\:00/0000\:00\:0d.0/resource0: Read error at byte 0, while reading 9728 bytes: Input/output error
tar: /sys/devices/pci0000\:00/0000\:00\:0d.0/resource1: Read error at byte 0, while reading 5120 bytes: Input/output error
tar: /sys/devices/pci0000\:00/0000\:00\:0d.0/resource1_wc: Read error at byte 0, while reading 512 bytes: Input/output error
tar: write did not end on a block boundary
tar: /mediastorage2/systemdrivebackup: Wrote only 4095 of 10240 bytes
tar: Error is not recoverable: exiting now

Log can be found at [http://pastebin.com/yiAc1WaR](http://pastebin.com/yiAc1WaR)

Any help you can offer would be appreciated.  I'm not really sure what to start with troubleshooting this.

---

### Post by antiartist on 2012-08-07
<bump>

Please?  Anyone?  Throw me something

---

