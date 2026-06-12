---
title: "Sudo apt-get update times out"
date: 2011-12-06
forum: Server Platforms
---

### Post by Daltonn0810 on 2011-12-06
so i was able to connect an old computer running Ubuntu 10.04 server to my windows 7 machine via Ethernet and was able to share a internet connection between them, i am able to ping Google.com and us.archive. Ubuntu.com from the server but when i run apt-get update it sits at 0% then it says could not connect to a bunch of URLS then sits at 21% and then stops. idk what to do, i dont have any proxy settings or anything, and im running in terminal mode.

:confused:

---

### Post by Bucky Ball on 2011-12-06
Do you perhaps need to open a port on the router or Win7 box? Are you running with exact same details on the Ubuntu box as Win7? Static IP or need to add DNS server?

---

### Post by lukeiamyourfather on 2011-12-06
Have you tried connecting the Ubuntu machine directly to the network connection instead of through the Windows machine? That's the first thing I would try to see if the issues are coming from sharing the connection on the Windows machine (or something external like the Ubuntu servers and repositories).

---

### Post by Daltonn0810 on 2011-12-06
> **Bucky Ball said:**
> Do you perhaps need to open a port on the router or Win7 box? Are you running with exact same details on the Ubuntu box as Win7? Static IP or need to add DNS server?

I doubt i need to open a port , the Ubuntu box can ping websites with the same speed as the windows box, so i imagine its a pretty smooth connection. i have checked the source lists as well and they are up to date. i have also tried to delete the cache too but i have had no luck

> Have you tried connecting the Ubuntu machine directly to the network connection instead of through the Windows machine? That's the first thing I would try to see if the issues are coming from sharing the connection on the Windows machine (or something external like the Ubuntu servers and repositories).

i will have to try that one tommorow, i have to physically move the box to another room XD

---

### Post by volkswagner on 2011-12-06
What is your network config?

```
cat /etc/network/interfaces
```

```
ifconfig
```

---

