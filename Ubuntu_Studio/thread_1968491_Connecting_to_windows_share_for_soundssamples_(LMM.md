---
title: "Connecting to windows share for sounds/samples (LMMS)"
date: 2012-04-29
forum: Ubuntu Studio
---

### Post by BCMusic on 2012-04-29
I've got a windows machine with 51GB of samples and was wondering if, instead of transferring all of them to Ubuntu, I could just connect LMMS (or any of the other software) to my sample folder in Windows?
```
smb://192.168.1.3/path/to/samples/
```

---

### Post by BCMusic on 2012-05-03
Anybody?

---

### Post by sgx on 2012-05-04
I use symbolic links from a mounted windows partition,
or browse  to a mounted location. Thats on a dual boot. You could
try a wubi install of ubuntu inside the windows partition, so no
partitions or extra drives were needed.
Cheers

---

### Post by BCMusic on 2012-05-04
I probably should have explained a little better in the OP. I'm running Ubuntu Studio on a laptop. The Windows desktop is where all of my sounds/samples are located. I'm able to connect both the laptop and the desktop together over WiFi with no problems using nautilus-connect-server, but that seems to be the only way. How would I mount a HDD over WiFi?

---

