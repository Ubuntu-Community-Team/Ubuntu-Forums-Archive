---
title: "ClamAV and UFW question"
date: 2015-09-10
forum: Security
---

### Post by ra7411 on 2015-09-10
I'll be doing a new Ubuntu install on a new desktop computer - plenty of CPU (4 core, 3.8mhz), RAM (8g's) and HD (2tb) capacity. There won't be a Win install on this machine, Ubuntu only.

Does ClamAV and UFW tie up resources or slow things down, to a noticeable degree? I guess many Linux users don't bother w/ either, which makes sense if you're trying to stretch the usage of an old machine, but on a new machine, is there any downside to having these two installed and running?

Thanks

---

### Post by cariboo on 2015-09-10
If you are running a default installation, there is no need for a firewall, as there are no ports listening. This is the result of a port scan on my laptop running Wily (15.10) with no services running:

```
sudo nmap -Pn 192.168.0.106

Starting Nmap 6.47 ( http://nmap.org ) at 2015-09-10 16:48 PDT
Nmap scan report for 192.168.0.106
Host is up (0.013s latency).
All 1000 scanned ports on 192.168.0.106 are closed
MAC Address: XX:XX:XX:XX:XX:XX (Liteon Technology)

Nmap done: 1 IP address (1 host up) scanned in 2.39 seconds
```

MAc address obscured just in case. :)

As far as running a virus scanner, unless you are sharing windows files, there really is no need for it either.

---

### Post by ventrical on 2015-09-10
I have used ClamAv, AVG and Comodo AntiVirus  (for Linux/Ubuntu) all very successfully. Currently Comodo  will only work with Precise and it has 'on access' scanning  (meaning that anything known malware/virus) will pop up a window if it tries to get across the network or written  to the hdd. Also UFW GUI version. Absolutely  no affect on performance that I can notice.

 I am hoping that Comodo updates to trusty soon as I usally scan hdds that have had Windows OSes on them. It is perfect for cleaning malware but I can still use  12.04 as it is working just fine as of yesterday :)

regards..

---

