---
title: "LTSP and Microsoft DHCP"
date: 2010-11-18
forum: Server Platforms
---

### Post by NathanBC on 2010-11-18
I am trying to test LTSP using Ubuntu 10.10 alternate CD.  If I install LTSP with the DHCP service running on the LTSP server everything works fine.  This however is not reasonable in our corporate network where Microsoft servers handle DHCP.  I have added the following options to the Microsoft DHCP server:


[LIST]
[*]017 Root Path:    /opt/ltsp/amd64
[*]066 Boot Server Host Name: 192.168.20.239
[*]067 Bootfile Name:    ltsp/amd64/pxelinux.0
[/LIST]
I have also tried:


[LIST]
[*]017 Root Path: 192.168.20.239:/opt/ltsp/amd64
[/LIST]
When I boot the thin client it comes up to the Ubuntu start up/loading screen (with the dots below the word Ubuntu) and just sits there and never completes loading.

I have edited /var/lib/tftpboot/ltsp/amd64/pxelinux.cfg/default and changed
append ro initrd=initrd.img quiet splash nbdport=2000
to
append ro initrd=initrd.img nbdport=2000
so that I can see what is going on.

The last message displayed during boot is "DHCP request for eth0"

All help would be greatly appreciated.

---

### Post by ilke42 on 2011-01-24
I am not shure if this will help you, but what we did is that we configured ip lease range to be complementry.
For example from x.x.x.0-x.x.x.150 for miscrosoft dhcp server (on windows server of course), and the rest for ubuntu (on ubuntu).

---

### Post by HugoSerrano on 2011-01-24
Is this correct?

[LIST]
[*]017 Root Path:    /opt/ltsp/amd64
[*]066 Boot Server Host Name: 192.168.20.239
[*]067 Bootfile Name:    ltsp/amd64/pxelinux.0
[/LIST]
maybe the clients are trying to get /opt/ltsp/amd64/ltsp/amd64/pxelinux.0

try with:
067 Bootfile Name: pxelinux.0

Regards!

---

### Post by ilke42 on 2011-01-24
And also check this thread:
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP](https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP)

---

