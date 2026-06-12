---
title: "Red Hat? Drivers on Ubuntu server for Fujitsu Siemens Primergy tx150 s4"
date: 2012-08-19
forum: Server Platforms
---

### Post by Raiin on 2012-08-19
Heya, I'm a complete linux noob, who picked up this old company-server I want to use as a file-server and plex media server under ubuntu server. So far so good, all this I can get running myself.

I'm not seeing temperatures on it though, and the fans are running very high rpms (making lots of noise). 

I'm thinking this has to do with the drivers. (correct me if I'm wrong)
And I want to install drivers available here:
[http://www.fujitsu.com/global/services/computing/server/ia/driver/]("http://www.fujitsu.com/global/services/computing/server/ia/driver/")
But I can't make out which ones to install according to this sheet:
[http://www.fujitsu.com/downloads/PRMRGY/pg-linux-os-kernel-compatibility-list.pdf]("http://www.fujitsu.com/downloads/PRMRGY/pg-linux-os-kernel-compatibility-list.pdf")

Should I be using 64 or 32-bit. As the server only has 2gb ram are there any drawbacks to using 32-bit, and what drivers do I install, and how?

---

### Post by cariboo on 2012-08-19
The drivers designed for RedHat, may not work on a Debian based system, you'd have to convert from .rpm to .deb using alien. Alien is available in the repositories. The best bet may be to find the drivers source code and compile them yourself.

---

