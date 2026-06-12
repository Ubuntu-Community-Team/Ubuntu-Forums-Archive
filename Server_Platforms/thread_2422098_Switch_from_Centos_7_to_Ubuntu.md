---
title: "Switch from Centos 7 to Ubuntu"
date: 2019-07-02
forum: Server Platforms
---

### Post by wp.rauchholz on 2019-07-02
I am considering to switch my home server from CENTOS to Ubuntu to have the same Linux flavor on server and desktops/laptops at home.
Would you please point me to the best manuals/howtos.
My current setup includes a LAMP stack,  server acts as modem/router (dynamic IP, iptables) of LAN, DNS, media server

Thank you, Wolfgang

---

### Post by SeijiSensei on 2019-07-02
Start here: [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

Apache is organized rather differently in Debian/Ubuntu.  Most other things aren't that different. 

I use CentOS on all my servers, since I go back to the days of RedHat 3 and kernel 1.0.9.  Running a chrooted BIND is simple on those platforms; I'd probably have to read some documentation to reproduce that environment. Things like routing, iptables, DHCP via isc-dhcp-server, etc., work the same across all versions.

---

