---
title: "how to download &quot;xdg-open&quot; links; how to install tarballs"
date: 2019-12-12
forum: Ubuntu, Linux and OS Chat
---

### Post by amadness on 2019-12-12
Found this little cutie for opening those "xdg-open" links: [https://www.pling.com/p/1136805/](https://www.pling.com/p/1136805/)

And this YouTube video explains how to instal tarballs using a program called "alien": [https://www.youtube.com/watch?v=pt44bAP2rMg](https://www.youtube.com/watch?v=pt44bAP2rMg)

---

### Post by yetimon_64 on 2019-12-12
Are you aware that the command xdg-open is available in the package xdg-utils?
```
yetiman:~ $  apt-cache search **xdg-open**
**xdg-utils** - desktop integration utilities from freedesktop.org
snapd-xdg-open - Transitional package for snapd-xdg-open
```

To get the xdg-open command from the repositories...
```
sudo apt install xdg-utils
```

You can build your own xdg-open command from source but doing so could be risky particularly when it already exists in the repos but comes from the xdg-utils package.

Regards, yeti.

---

