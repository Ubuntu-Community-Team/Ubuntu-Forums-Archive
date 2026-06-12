---
title: "LTSP problem with 10.xx"
date: 2010-10-20
forum: Server Platforms
---

### Post by quesy on 2010-10-20
Hi all,

I have trying for days to get my LTSP-server + client work with no success at all.

The problem is that it says that it cant connect to NBD server when its trying to mount, ive been looking so much on the net about this problem with no success.

I can however mount NBD device in INITRAMFS mode witch seems to be the falback after NBD mount fails.

NDB server runs on port 2000 and in pxelinux.cfg/default i have port 2000. Is there something i need to do on the client image to get this to work, as it is now it doesent even try to mount it before it fails if i check LTSP server logs.

Lots of people tells me that 9.10 works flawless and 10.04 and 10.10 is not working at all. Is there anyone out there who solved this problem ? Seems that more and more stuff stops to work in every ubuntu server release.

---

