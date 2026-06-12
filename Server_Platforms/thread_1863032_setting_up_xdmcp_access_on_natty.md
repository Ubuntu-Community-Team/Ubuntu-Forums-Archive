---
title: "setting up xdmcp access on natty"
date: 2011-10-17
forum: Server Platforms
---

### Post by np-hard on 2011-10-17
Hello,
 
I am a newbie to ubuntu linux, and want to setup xdmcp access, so i can access it from my windows box using xming. part of it is learning exersice also, since i know i could use vnc to directly connect to ubuntu.
i modified the gdm's custom.conf file like this
[xdmcp] Enable=true
but when i launch xlaunch, i see a blank screen, further diagnosing with wireshark, i got that the udp port 177 on the linux box is unreachable so i disabled the firewall on linux box, but still same result.
I checked with nmap and there is no service listening on UDP 177 port, the gdnsetup on natty is quite different from the older version, where setting up xdmcp was in UI
any help would be appreciated

---

