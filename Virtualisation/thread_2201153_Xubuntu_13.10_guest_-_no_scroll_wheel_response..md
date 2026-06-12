---
title: "Xubuntu 13.10 guest - no scroll wheel response."
date: 2014-01-22
forum: Virtualisation
---

### Post by sorceror171 on 2014-01-22
I'm running a Xubuntu 13.10 guest on a Xubuntu 13.10 host (as an isolated browsing environment). I'm using straight qemu via the command line, the command being:

  ```
qemu-system-x86_64 -localtime -m 2048 -soundhw all -vga vmware -enable-kvm -usbdevice tablet xubu1310.qcow
```

When I ran a 13.04 guest on a 13.04 host, it "just worked". Now it doesn't (though the scroll wheel works in the host environment). Is there an option I'm missing or did some default change?

---

### Post by sorceror171 on 2014-01-23
Well, it's worse than that. Just fired up my seldom-used XP guest, and the scroll wheel doesn't work there either. So now it appears that it's on the host side that the problem was introduced.

---

