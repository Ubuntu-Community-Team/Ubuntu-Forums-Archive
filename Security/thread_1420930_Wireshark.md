---
title: "Wireshark"
date: 2010-03-03
forum: Security
---

### Post by Silvertones on 2010-03-03
Based on the intrusion detection post I thought it would be interesting to install something to monitor network traffic.Wireshark seemed to be a good choice as it has a nice interface and seems fairly straight forward. I guess that's not the case. When I click on "list the avaiable capture devices" there aren't any. Mu connection to the internet is through a USR USB Dialup modem and my 2 computers are networked by a peer to peer wireless network.
Can anyone steer me in the right direction. I've read the manual.

---

### Post by Silvertones on 2010-03-03
If I start it this way: ```
sudo wireshark
``` it throws up a warning about running it as ROOT however it's the only way it'll run. That's sort of messed up isn't it?

---

### Post by cariboo on 2010-03-03
The last time I installed wireshark it created a menu item to run wireshark as root.

---

### Post by Soul-Sing on 2010-03-04
please do not use wirshark as root it is very unsafe, and their are alternatives: [http://wiki.wireshark.org/CaptureSetup/CapturePrivileges](http://wiki.wireshark.org/CaptureSetup/CapturePrivileges)
[http://wiki.wireshark.org/Security](http://wiki.wireshark.org/Security)

> Running Wireshark (or any other network capture/analyzer, for that matter) on Linux needs root privileges. Therefore, you have to have root privileges when starting Wireshark, else you can't capture data. Please note that you don't have to login as root when starting your computer, you can use su(1) or sudo(8) for that purpose. However, this remains unsecure as the dissectors, the parts of Wireshark which parse the captured data, run with root privileges as they did before. A much safer solution would be to su(1) to root, then use the bundled dumpcap to dump the data (for example, you can evoke dumpcap by using "dumpcap -w ./dumpfile", which will dump the packets to the file "dumpfile" in the current working directory. See "dumpcap -h" for details). You could also use tcpdump for this purpose. The advantage of this solution is, while dumpcap/tcpdump still run as root, you can run Wireshark as a ordinary user and load the data you captured previously, so effectively this is kinda "privilege separation by hand".

---

### Post by Silvertones on 2010-03-04
So what am  I supposed to do? do I run it as root or just not use it?

---

### Post by Soul-Sing on 2010-03-04
> **Silvertones said:**
> So what am  I supposed to do? do I run it as root or just not use it?
from the wiki

> Setting network privileges for dumpcap
1. Ensure your linux kernel and filesystem supports File Capabilities and also you have installed necessary tools.
2. "setcap 'CAP_NET_RAW+eip CAP_NET_ADMIN+eip' /usr/bin/dumpcap"
3. Start Wireshark as non-root and ensure you see the list of interfaces and can do live capture.
Limiting capture permission to only one group
1. Create user "wireshark" in group "wireshark".
2. "chgrp wireshark /usr/bin/dumpcap"
3. chmod 754 /usr/bin/dumpcap
4. "setcap 'CAP_NET_RAW+eip CAP_NET_ADMIN+eip' /usr/bin/dumpcap"
5. Ensure Wireshak works only from root and from "wireshark" user.

---

### Post by Soul-Sing on 2010-03-04
> **Silvertones said:**
> So what am  I supposed to do? do I run it as root or just not use it?

You could run tcpdump with an apparmor profile which comes with/from 9.04 and higher.

---

### Post by bodhi.zazen on 2010-03-04
> **leoquant said:**
> please do not use wirshark as root it is very unsafe, and their are alternatives: [http://wiki.wireshark.org/CaptureSetup/CapturePrivileges](http://wiki.wireshark.org/CaptureSetup/CapturePrivileges)
[http://wiki.wireshark.org/Security](http://wiki.wireshark.org/Security)

Nice link, thank you.

---

### Post by Silvertones on 2010-03-05
I did step 1-3 as posted by leoquant and it worked fine.
I then did step 1-5 and when I logged in as wireshark everything acted weird. Some of the icons were missing, real boggy etc. I deleted the wireshark user, reinstalled Wireshark program and did steps 1-3. I THINK I can leave it that way as I'm the only one who has access to this computer.

---

### Post by TurnOfTide on 2010-03-05
How is it harmful to run wireshark in root, other than the obligatory?

---

### Post by Soul-Sing on 2010-03-25
> **TurnOfTide said:**
> How is it harmful to run wireshark in root, other than the obligatory?

A Gentoo developer explained the "non-root choice" because of the complexity of Wireshark, the complexity of code. Wireshark contains
an enormous amount of code, with the possibility of exploits.
(The obligatory is not to run programs as root if not needed)

---

### Post by Rubi1200 on 2010-03-25
Ubuntu user cdenley suggested I use these commands:

sudo apt-get install libcap2-bin wireshark
sudo chgrp admin /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap
Worked like a charm :)

---

