---
title: "Feiste to Hardy Upgrade - Still Old Kernel."
date: 2008-07-09
forum: Server Platforms
---

### Post by TitanKing on 2008-07-09
Hi, thank you for looking at my thread!

I am having a serious problem on a live server. I have done the upgrade through the terminal on a Server. 

Using :

```
do-release-upgrade

```

All went well with the Upgrade, I kept all old config files.

After the Upgrade I am experiencing 2 big problems.

1. The old kernel still loads, namely 2.6.22-14-server
2. The websites cannot be accessed anymore. I think it is because of the old kernel.

The server is 15 000KM from me so I don't have direct access to it.

I tried looking at my grub file but I have no /boot/grub directory.

Please help me boot up the latest kernel so I can fix the web server.

Thanks again!

---

### Post by windependence on 2008-07-09
From what version to what version did you upgrade? The upgrade may have overwritten your Apache config files. You should always back up before doing anything as large as an upgrade.

-Tim

---

