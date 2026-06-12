---
title: "where is firewall script in ubuntu 5.10 ?"
date: 2006-01-16
forum: Server Platforms
---

### Post by stock99 on 2006-01-16
I have install ubuntu 5.10 but i can't find firewall script in /etc/init.d/ . In debian there is such script that allow me to do iptables start/stop/status/etc.

I do have iptable installed . But without such script is there anyway i can check if my firewall is running? Besides, can i use the script from lastest debian distro? Or is there any generic script i can download and use without much modification? I am newb at shell programming.



thx in advance

---

### Post by tcwitte on 2006-01-17
There's no firewall script (probably because there's no firewall by default). You can however put your script in /etc/network/if-pre-up.d (with +x set) and it will be executed before the connection is established.

---

