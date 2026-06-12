---
title: "Basic Security Defaults?"
date: 2006-01-27
forum: Server Platforms
---

### Post by franklee on 2006-01-27
:confused: Just wondering how secure Ubuntu 5.10 is out of the box. If we dont modify anything at all...

oh and does anyone know if Lokkit is any good? My girlfriend asked me last night what the security for Ubuntu was like (as she has NEVER used Linux before) and I really want her to give it a go...all I could respond with was the usual "linux is different to windows" reply and directed her to repositories to find something to ease her mind...

Anyone suggest good apps to increase security within this distro?:-k

---

### Post by ardchoille on 2006-01-27
I am more paranoid than the average Linux user and I like the security in Ubuntu out-of-the-box. There are no "world-facing" servers, the root account is disabled, and users created after the inital user are not able to use sudo. I install rkhunter and chkrootkit (both check for different rootkits) and firestarter to tweak the firewall.

---

### Post by rfruth on 2006-01-27
Breezy security is good out-of-the-box, I have a linksys router (see link if you must )
[http://www.ubuntuforums.org/showthread.php?t=121997]("http://www.ubuntuforums.org/showthread.php?t=121997")
and that helps + I use firestarter to configure the firewall then there is clamAV [https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29]("https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29")
I'm as sug as a bug in a rug  ;)

---

