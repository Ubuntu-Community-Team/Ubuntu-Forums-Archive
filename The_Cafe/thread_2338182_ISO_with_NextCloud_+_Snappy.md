---
title: "ISO with NextCloud + Snappy"
date: 2016-09-25
forum: The Cafe
---

### Post by MadsRH on 2016-09-25
Hi

This is almost without a doubt the wrong forum (feel free to move my thread). Anyway, I've been looking at the [NextCloud Box]("https://nextcloud.com/box/") and I'm loving it. Can anyone tell me if there's a ready-to-go ISO that I can download somewhere?

As I understand it, it's Ubuntu Core, Apatche and NextCloud, right?

I want to do something similar with my Pi3

Best regards
*MadsRH*

---

### Post by TheFu on 2016-09-25
Installed nextcloud on a minimal ubuntu server a few days ago following these instructions:
[https://www.linuxbabe.com/cloud-storage/setup-nextcloud-server-ubuntu-16-04-apache-mariadb-php7](https://www.linuxbabe.com/cloud-storage/setup-nextcloud-server-ubuntu-16-04-apache-mariadb-php7)
Took about 20 min. I made a mistake with the redis caching which broke it, but the instructions were correct.  I'm not willing to put it on the internet, but over a VPN it is working very well.  Also installed Wallabag on the same box - similar dependencies in both.  Together, they are using under 400MB of RAM, zero swap.

For a family, I think a r-pi v3 would have plenty of CPU.
The downside of the install instructions is that nextcloud is installed from source, not from a package.

If you don't have a kodi/OSMC media player, that is what I'd use my r-pi for.  Of course, just swap the SD card and you can easily have both options.

---

### Post by MadsRH on 2016-09-27
Thanks! Good tutorial.

Isn't there any ready-to-go images available for download, where everything is setup

---

