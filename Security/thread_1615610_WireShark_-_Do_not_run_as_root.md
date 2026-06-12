---
title: "WireShark - Do not run as root"
date: 2010-11-07
forum: Security
---

### Post by mistypotato on 2010-11-07
The Wireshark website specifically warns against running WireShark as Root....

> **Administrator/root account not required!**

Many Wireshark users think that Wireshark requires a root/Administrator account to work with.

That's not a good idea, as using a root account makes any exploit far more dangerous: a successful exploit will have immediate control of the whole system, compromising it completely.

First of all, most Wireshark functions can always be used with a (probably very limited) user account. In particular, the protocol dissectors which have shown most of the security related bugs do not need a root account!

Only capturing (and gathering capture interface information) may require a root account, but even that can usually be "circumvented", see CaptureSetup/CapturePrivileges for details how to do so. 

Yet people here say they do it :confused:

Do you run Wireshark as Root?

---

### Post by CandidMan on 2010-11-07
Don't run it as root any more, when I do run it (once in a blue moon)

Check this link out [http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/)

---

### Post by Soul-Sing on 2010-11-07
: [http://ubuntuforums.org/showthread.php?t=1420930](http://ubuntuforums.org/showthread.php?t=1420930)

---

### Post by Rubi1200 on 2010-11-07
It is also possible to capture traffic by setting up Wireshark according to the following method:

Run each command separately:

```
sudo apt-get install libcap2-bin wireshark
sudo chgrp admin /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap
```(courtesy of forum member cdenley)

As others have stated, running Wireshark as root is both dangerous and unnecessary (see the links already provided above).

---

