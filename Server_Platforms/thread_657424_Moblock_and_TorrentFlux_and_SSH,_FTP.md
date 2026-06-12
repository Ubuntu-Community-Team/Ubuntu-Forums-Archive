---
title: "Moblock and TorrentFlux and SSH, FTP"
date: 2008-01-03
forum: Server Platforms
---

### Post by Hawkeye05 on 2008-01-03
Can anyone help me with this im running a server with gusty and i want to use ssh (of course) and torrentflux, and i tried using moblock but it blocks the ssh, im on my home network so the ips would all be 192.168.x.x is there a way i can customize the list to allow SSH, and HTTP and FTP, but still have protection, maybe if i could just allow all on those ports maybe?

---

### Post by jre on 2008-01-04
> **Hawkeye05 said:**
> Can anyone help me with this im running a server with gusty and i want to use ssh (of course) and torrentflux, and i tried using moblock but it blocks the ssh, im on my home network so the ips would all be 192.168.x.x is there a way i can customize the list to allow SSH, and HTTP and FTP, but still have protection, maybe if i could just allow all on those ports maybe?

Yes, you can whitelist ports and IPs in /etc/moblock/moblock.conf.
Please also have a look at the HOWTO: [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)


greets
jre

---

### Post by Hawkeye05 on 2008-01-04
thanks a ton and sorry for the double post, i had assumed i had posted in the wrong area so i reposted.

---

### Post by jre on 2008-01-04
> **Hawkeye05 said:**
> thanks a ton and sorry for the double post, i had assumed i had posted in the wrong area so i reposted.
no problem, hope you could solve your problem now

---

