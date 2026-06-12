---
title: "Problem blacklisting hash (-13)"
date: 2022-09-06
forum: Ubuntu Development Version
---

### Post by VMC on 2022-09-06
Note:This should be on development forum.
Ubuntu Kinetic Kudu (development branch)

I see this after current update. Google has limited help.
```
sudo dmesg|grep blacklist
[    0.414335] Key type blacklist registered
[    0.834401] blacklist: Loading compiled-in revocation X.509 certificates
[    0.838773] blacklist: Revoked X.509 cert 'Acer Database Forbidden: 9de028a2638669f109745d3e2a7ad5c9e64ed392'
[    0.838935] blacklist: Revoked X.509 cert 'Canonical Ltd. Secure Boot Signing: 61482aa2830d0ab2ad5af10b7250da9033ddcef0'
[    0.838945] blacklist: Revoked X.509 cert 'Debian Secure Boot Signer: 00a7468def'
[    0.839104] blacklist: Problem blacklisting hash (-13)
[    0.839182] blacklist: Problem blacklisting hash (-13)
[    0.839230] blacklist: Problem blacklisting hash (-13)
[    0.839264] blacklist: Problem blacklisting hash (-13)
```

---

### Post by nanook2 on 2022-09-29
blacklist: Problem blacklisting hash (-13) I am seeing the same thing with Ubuntu 22.10 mainline kernel 5.19.11, Mate desktop.

---

### Post by deadflowr on 2022-09-29
*Thread moved to **Ubuntu Development Version***

---

### Post by VMC on 2022-09-29
I have been seeing this for quite some time on any distro. Its just that now Ubuntu doesn't hide the output on boot.

---

### Post by VMC on 2022-10-14
I just wanted to hide that output, so a opted for loglevel=3 and grub linux line.

---

### Post by acarlton on 2022-10-21
I just performed the Kinetic distribution update today, hot off the presses, and I'm seeing this error in my dmesg and on-screen.

---

