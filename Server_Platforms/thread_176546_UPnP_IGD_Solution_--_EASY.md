---
title: "UPnP IGD Solution -- EASY"
date: 2006-05-14
forum: Server Platforms
---

### Post by schweitzereffect on 2006-05-14
I have been unsuccessfully trying to get linux-igd to work for a long time, but stumbled across this today!  It is a testing debian package which works perfectly with ubuntu (dapper at least)!  Finally, I do not need to manually map ports for everything!  It works incredibly well and I assume its what all linux routers use as it is the only igd program i found for linux!
[http://packages.debian.org/testing/net/linux-igd](http://packages.debian.org/testing/net/linux-igd)
Just install all dependencies and dpkg -i it, edit /etc/default/upnpd to have your internal and external interfaces and done, it works great!

---

