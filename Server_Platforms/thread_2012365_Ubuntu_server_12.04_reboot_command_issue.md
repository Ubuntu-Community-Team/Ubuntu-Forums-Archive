---
title: "Ubuntu server 12.04 reboot command issue"
date: 2012-06-29
forum: Server Platforms
---

### Post by shadowlinyf on 2012-06-29
I installed ubuntu 12.04 server on my new server(Mainboard is supermicro X9SCA-F).

Everything seems fine util I tried to execute 'reboot' command, the server was shutdown instead of reboot.
Does anyone have any idea why this happens?

PS:I tried to install ubuntu 11.10 server instead then the reboot worked fine.

---

### Post by anonymouschief on 2012-06-29
Try

```
sudo shutdown -r now
```

---

### Post by Gyokuro on 2012-06-29
Hi

with reboot an instant reboot get performed (you can check via man reboot and read the difference) whereas as anonymouschief posted already the standard 'reboot' command to reboot a system cleanly (unmounting drives,...) - HTH

---

### Post by shadowlinyf on 2012-06-30
> **anonymouschief said:**
> Try

```
sudo shutdown -r now
```

thanks
so the best way to reboot is to use shutdown -r instead of reboot?
and this way will be safer,right?

---

### Post by Gyokuro on 2012-06-30
Yes - correct, it's the safer.

---

