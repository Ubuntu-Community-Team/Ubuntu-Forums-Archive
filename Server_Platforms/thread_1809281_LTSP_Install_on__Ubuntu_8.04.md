---
title: "LTSP Install on  Ubuntu 8.04"
date: 2011-07-21
forum: Server Platforms
---

### Post by adz13 on 2011-07-21
Hi there, 

I am very much a linux noob, only just started playing around with it. Anyway I want to install LTSP on 8.04 but the guides I follow, when I enter the commands I just get the error E: Couldn't find package ltsp-server-standalone.

I just wondered if anyone has LTSP working on 8.04 if so what did you do to get it working or is my build missing some major parts.

Thanks in advance, Adam :)

---

### Post by snowpine on 2011-07-21
The package can't be found because 8.04 has reached its "end of life" and is no longer supported. Give 10.04 or 11.04 a try. :)

---

### Post by adz13 on 2011-07-21
I tried it on 10.04 but couldn't get it working, the guides I have followed all seemed simple consisting of a few commands. I also configured all of the config files such as dhcpd.conf but I couldn't get the thin client to connect. I turned DHCP off on the router to allow the server to do it. I was a bit confused in regards to TFTP, does the server provide this too because there is no mention of it in any of the installation guides and I know it is required for PXE booting. I am only use one NIC in the server but I have read that it can work fine with only one NIC. Any help would be greatly appreciated. Thanks all

---

