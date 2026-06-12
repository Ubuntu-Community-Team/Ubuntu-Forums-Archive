---
title: "NTP ubuntu pools"
date: 2017-05-26
forum: Security
---

### Post by mindlr on 2017-05-26
Hi all,

I have the ntpd service with default configuration active. 
Yesterday my machine made ntp queries to an IP address that was one of the IOCs associated with wannacry namely the 146[.]0[.]32[.]144
It it supposed to make queries to this "dubious" IP?

ntp.conf file:
....
# Use servers from the NTP Pool Project. Approved by Ubuntu Technical Board
# on 2011-02-08 (LP: #104525). See [http://www.pool.ntp.org/join.html](http://www.pool.ntp.org/join.html) for
# more information.
pool 0.ubuntu.pool.ntp.org iburst
pool 1.ubuntu.pool.ntp.org iburst
pool 2.ubuntu.pool.ntp.org iburst
pool 3.ubuntu.pool.ntp.org iburst

# Use Ubuntu's ntp server as a fallback.
pool ntp.ubuntu.com
....

References of reported as malicious:
[https://www.virustotal.com/pt/ip-address/146.0.32.144/information/](https://www.virustotal.com/pt/ip-address/146.0.32.144/information/)
[https://www.shodan.io/host/146.0.32.144](https://www.shodan.io/host/146.0.32.144)
[https://cymon.io/146.0.32.144](https://cymon.io/146.0.32.144)

Wannacry IOC reference:
[http://blog.talosintelligence.com/2017/05/wannacry.html](http://blog.talosintelligence.com/2017/05/wannacry.html)

Best Regards

---

### Post by TheFu on 2017-05-26
WannaCry is a Windows issue. Not an NTP issue.  Don't think I'd worry, provided they are using Unix, not Windows, as the OS.  Linux had a huge UDP issue that was silently patched in February.  If you are running any unpatched linux-based servers, routers, wifi-APs, or IoT devices, I'd be more worried about that UDP issue than wannacry.

NTP servers are often run by volunteers. Some will be highly secure and others are part of some home network.  An IP is not necessarily a single server, right?  Each port can easily be forwarded to different hosts. In fact, different services on the same port can be forwarded to different hosts.

---

