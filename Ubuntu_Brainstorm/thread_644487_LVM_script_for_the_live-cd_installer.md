---
title: "LVM script for the live-cd installer"
date: 2007-12-18
forum: Ubuntu Brainstorm
---

### Post by ihavenoname on 2007-12-18
The attached is a "proof-of-concept" script for setup of LVM on a hard drive. This is designed with the intention of later implementing it into the ubuntu live cd installer. You will need lvm2 installed on the live-cd (this can be done in the live-environment) and you will need to modprobe dm-mod after installing lvm2. The script should be run inside the live environment. I recommend using virtual box since this is pre-alpha software.

---

