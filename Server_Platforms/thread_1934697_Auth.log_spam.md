---
title: "Auth.log spam"
date: 2012-03-02
forum: Server Platforms
---

### Post by HunterZ on 2012-03-02
I'm seeing this same spam in my auth.log about once per second. Turns out that an IP camera on my LAN was triggering the following corresponding samba log errors:
```
[2012/03/02 10:30:49.211394,  0] param/loadparm.c:8697(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/babycam failed. No such file or directory
```I've disabled that feature of the IP cam (since I don't use it anyways) and it stopped the log spam.

Edit: If anyone knows what that error means, I'd appreciate it. The IP cam can't connect to my Windows-based samba shares either. My Windows machines can connect to my Ubuntu samba shares just fine, so the IP cam is the screwy one.

---

### Post by redmk2 on 2012-03-02
> **HunterZ said:**
> I'm seeing this same spam in my auth.log about once per second. Turns out that an IP camera on my LAN was triggering the following corresponding samba log errors:
```
[2012/03/02 10:30:49.211394,  0] param/loadparm.c:8697(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/babycam failed. No such file or directory
```I've disabled that feature of the IP cam (since I don't use it anyways) and it stopped the log spam.

Edit: If anyone knows what that error means, I'd appreciate it. The IP cam can't connect to my Windows-based samba shares either. My Windows machines can connect to my Ubuntu samba shares just fine, so the IP cam is the screwy one.

The error says there is no usershare named babycam. Do you have Samba installed?  Do you have a share where the CAM is supposed to dump data?  How do you configure that?

---

### Post by cariboo on 2012-03-02
Moved to a thread of it's own as it had nothing to do with the thread it was in.

---

