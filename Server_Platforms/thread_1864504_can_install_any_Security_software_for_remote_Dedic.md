---
title: "can install any Security software for remote Dedicated Linux servers like below"
date: 2011-10-19
forum: Server Platforms
---

### Post by lse123 on 2011-10-19
In an Ubuntu Server live OS run on a desktop (live dvd/cd or usb stick/hdd/ssd) can install any Security software for remote Dedicated Linux servers like below...?
Also may leave desktop always on to server web users - web server software...?

Security open source

[http://www.snort.org/](http://www.snort.org/)
Snort® is an open source network intrusion prevention and detection system (IDS/IPS) developed by Sourcefire.

[http://www.clamav.net/lang/en/](http://www.clamav.net/lang/en/)
ClamAV is an open source (GPL) antivirus engine designed for detecting Trojans, viruses, malware and other malicious threats.

[http://www.smoothwall.org/](http://www.smoothwall.org/)
SmoothWall Express - a Free firewall that includes its own security-hardened GNU/Linux operating system and an easy-to-use web interface.

---

### Post by vasile002 on 2011-10-19
yes you can install those but i am not sure why you need them since it's a desktop

---

### Post by jemate18 on 2011-10-19
I don't know if I got you right. 

But yes you can leave your desktop running live Ubuntu OS powered on to serve web requests using of course Apache Web Server.

And also, yes... you can install security software such as the ones you have mentioned.

Downside?
If your PC happens to shutdown or crash for some unknown reason, all your configurations and software installations will be gone because you are using a "live" Ubuntu OS.

Regards,

> **lse123 said:**
> In an Ubuntu Server live OS run on a desktop (live dvd/cd or usb stick/hdd/ssd) can install any Security software for remote Dedicated Linux servers like below...?
Also may leave desktop always on to server web users - web server software...?

Security open source

[http://www.snort.org/](http://www.snort.org/)
Snort® is an open source network intrusion prevention and detection system (IDS/IPS) developed by Sourcefire.

[http://www.clamav.net/lang/en/](http://www.clamav.net/lang/en/)
ClamAV is an open source (GPL) antivirus engine designed for detecting Trojans, viruses, malware and other malicious threats.

[http://www.smoothwall.org/](http://www.smoothwall.org/)
SmoothWall Express - a Free firewall that includes its own security-hardened GNU/Linux operating system and an easy-to-use web interface.

---

### Post by haqking on 2011-10-19
> **lse123 said:**
> In an Ubuntu Server live OS run on a desktop (live dvd/cd or usb stick/hdd/ssd) can install any Security software for remote Dedicated Linux servers like below...?
Also may leave desktop always on to server web users - web server software...?

Security open source

[http://www.snort.org/](http://www.snort.org/)
Snort® is an open source network intrusion prevention and detection system (IDS/IPS) developed by Sourcefire.

[http://www.clamav.net/lang/en/](http://www.clamav.net/lang/en/)
ClamAV is an open source (GPL) antivirus engine designed for detecting Trojans, viruses, malware and other malicious threats.

[http://www.smoothwall.org/](http://www.smoothwall.org/)
SmoothWall Express - a Free firewall that includes its own security-hardened GNU/Linux operating system and an easy-to-use web interface.

To install and save changes on a Live USB then you need perisistance.

As for the services, a firewall is built into Linux Kernel called netfilter and is controlled with IPTables which you can use from CLI or configure through an interface such as UFW/GUFW which are the most popular.

ClamAV is pretty poor as are most AV in linux, unless you are sharing files with windows users i wouldnt bother, iot throws a lot of false positives.

No system is 100% secure when on a network or sharing data, security is best in a layered approach and with ongoing vigilence and awareness, the main security flaw in any system is PEBKAP = Problem Exists Between Keyboard And Person

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

See here for Anti-Virus information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)

---

