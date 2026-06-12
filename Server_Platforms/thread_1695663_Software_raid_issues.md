---
title: "Software raid issues"
date: 2011-02-26
forum: Server Platforms
---

### Post by anifort on 2011-02-26
Hello there,
I Installed on a computer the ubuntu server 10.10 with software raid 1. The installation proceeded normally but on first reboot it gave me the following message
error: no such device: {a-huge-id-number}
grup rescue>

notice that during the software raid setup, on the question if i wanted to boot in degraded raid state, i choose No.

Thanks in advance

---

### Post by joshruehlig on 2011-02-26
check this site, make sure everything goes well. specifically check the forums where i troubleshooted a problem with my software raid settup. I was one of the config files that was being autowritten to, but what it wrote wasn't exactly correct.

[http://www.ainer.org/raid-5-6-install-setup-configuration-guide-for-ubuntu-10-04-lts-lucid-lynx](http://www.ainer.org/raid-5-6-install-setup-configuration-guide-for-ubuntu-10-04-lts-lucid-lynx)

Not sure if this is your problem but should help you troubleshoot a bit.

---

