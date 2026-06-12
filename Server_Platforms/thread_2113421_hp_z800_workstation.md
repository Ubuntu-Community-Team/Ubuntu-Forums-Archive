---
title: "hp z800 workstation"
date: 2013-02-07
forum: Server Platforms
---

### Post by kanjah on 2013-02-07
Hi guyz, just installed ubuntu server 12 amd64  on hp z800 workstation, to be used as a proxy server. I has 32 gb ddr3 ram, 2x3.0 xeon processor, tesla nvida media card, and 2tb space. At the login in page, it displays this error {drm} nouveau 0000:28:00.0: no native mode, forcing panel scaling.....
any advice

---

### Post by kanjah on 2013-02-10
I did edit the GRUB_CMDLINE_LINUX_DEFAULT add the line at the end="quiet drm_kms_helper.poll=0".since i could not edit the file due to the multiple error display, i copied the file to a flash disk and edited it on another computer, use google to check on how to mount and umount flash disk if you dont know how to, then i replaced the original grub with the edited one, then did an update of grub, i.e update-grub, then updated-system, it worked fine, dnt try to edit the file in recovery mode, since its in read-only mode, hope this helps someone else. Incase of query add a comment

---

