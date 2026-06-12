---
title: "Write speed is fluctuating on USB disks"
date: 2017-08-18
forum: Server Platforms
---

### Post by jeuteuhais on 2017-08-18
Hello all, I up a one year old post, because à don't want to make a new one.

Have exactly the same problem, with a mini PC (XU4) and two HDD (connected in USB3), and this ARM powered PC deosn't have a bios. There is 2 weeks my samba shares were working properly, data transferts client to server, and server to client were fast as 80 MB/s. By mistake, I have disconnected the power of one of the HDD and probably switched the USB port between the two HDD :S, when I reconnected, the speed data transfert from client to server had down to 40 MB/s.

dd if=/dev/sda of=test.mkv bs=1024k count=180
180+0 enregistrements lus
180+0 enregistrements écrits
188743680 bytes (189 MB, 180 MiB) copied, 2,81117 s, 67,1 MB/s

dd if=/dev/sdb of=test.mkv bs=1024k count=180
180+0 enregistrements lus
180+0 enregistrements écrits
188743680 bytes (189 MB, 180 MiB) copied, 2,7983 s, 67,4 MB/s

Thank you for your help !

---

### Post by cariboo on 2017-08-18
Moved to a thread of it's own, and it isn't the same problem as the old thread it was in.

---

