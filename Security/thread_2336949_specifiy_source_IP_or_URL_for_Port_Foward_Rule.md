---
title: "specifiy source IP or URL for Port Foward Rule"
date: 2016-09-12
forum: Security
---

### Post by jay116 on 2016-09-12
[COLOR=#333333][FONT=Helvetica]I need to open a port on OpenWrt router (Linksys WRT1200). I can see the setting in Luci but i need to specify an origination URL or IP so that only one specific remote address (source IP) can have its packets forwarded within my LAN. I don't see this option in the GUI but I thought I could run a specific command line code that ran a startup in the firewall with iptables to make this happen. Could someone give me an example of this or point me in the right direction. Still trying to put this together in my head.

Thanks.[/FONT][/COLOR]

---

### Post by CharlesA on 2016-09-12
You should only need to specify the destination IP you want that port forwarded to. There is not real "source" IP specified, at least from what I saw in the docs: [https://wiki.openwrt.org/doc/howto/port.forwarding](https://wiki.openwrt.org/doc/howto/port.forwarding)

You would need to handle access control on the box that has the ports forwarded to it with a firewall or other method.

---

### Post by jay116 on 2016-09-12
OpenWrt is just a small Linux distro which should use iptables. From this site ([https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)) there is a "--source" specfication. Any guidance on the final command is where I'm trying to head.

my application is this. I need to open port 9100 to a standalone printer on my internal network but I need to secure the router so that only specific traffic gets sent to it. Any suggestions?

---

