---
title: "All downloaded files get corrupted"
date: 2020-04-24
forum: Server Platforms
---

### Post by khedira on 2020-04-24
Hi! I recently installed Ubuntu server in a virtual machine on my Windows host. I am quite new to Ubuntu server so I don't know if I missed some configuration details but my issue is this: 

**Main issue:**
Every file I download seems to be corrupt. I have tried both curl and wget. I have tried using the "--compression=none" flag with wget but it didn't seem to help.

**Setup info:**
Windows 10 Pro:
Version 1909 (OS-version 18363.778)
VirtualBox:
Version 6.1.6 r137129 (Qt5.6.2)
Ubuntu server:
Version 18.04.4
curl 7.58.0
Wget 1.20.3

Thankful for any help I get!

---

### Post by TheFu on 2020-04-24
The only time I've seen file corruption was with a cracked motherboard and no virtualization.
Other things to check are the ethernet cable used or wifi.

Does the host show this issue too or not?

Last thing would be to check failing HDD or disk controller.

No OS has settings that corrupt or don't corrupt data.  Perhaps the hostOS has a virus that corrupts data?

---

### Post by khedira on 2020-04-25
Thank you for the reply!

The issue is only on the guest machine. I tried other versions of Virtualbox and and it suddenly worked with version 6.0.20.

---

### Post by noelmcloughlin on 2020-09-30
VirtualBox version 6.1.14 is a corrupt hypervisor release. Downgrading to 6.0.20 fixed for me also.

---

