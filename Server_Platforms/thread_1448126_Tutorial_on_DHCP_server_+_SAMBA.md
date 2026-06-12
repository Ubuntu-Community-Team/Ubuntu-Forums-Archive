---
title: "Tutorial on DHCP server + SAMBA"
date: 2010-04-06
forum: Server Platforms
---

### Post by rmb938 on 2010-04-06
Hi, does anyone have a link to a tutorial on how to set up a DHCP server and SAMBA as a windows domain controller? I can't really find good detailed guides by searching google.

---

### Post by R.Bucky on 2010-04-07
Samba or DHCP are not designed for use as domain controllers. You might be looking for LDAP. However, DHCP assigns your internal network ip addresses, nameservers, and applies various other functions, while samba provides file and print services. Samba can be configured for password protected directories as well. It depends on your needs. Also, check out ClearOS. It is a Linux version of MS Server.

Check these out:
[https://help.ubuntu.com/community/dhcp3-server]("https://help.ubuntu.com/community/dhcp3-server")
[http://buckycomputing.net/blog/how-to-configure-dhcp3-server-in-ubuntu-server/]("http://buckycomputing.net/blog/how-to-configure-dhcp3-server-in-ubuntu-server/")
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by R.Bucky on 2010-04-07
Also...
[https://help.ubuntu.com/9.10/serverguide/C/network-authentication.html]("https://help.ubuntu.com/9.10/serverguide/C/network-authentication.html")

---

