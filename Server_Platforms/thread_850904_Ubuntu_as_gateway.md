---
title: "Ubuntu as gateway"
date: 2008-07-06
forum: Server Platforms
---

### Post by benlakhoua on 2008-07-06
Dear all
i have ubuntu server edition.
i have setup squid3 as transparant .
i have enabled ipv4 forward in the kernel.

what i want to do is when i stop the squid i dont want eny one to have internet in my system.

now my ubuntu is working as a getaway which is bad for my setup.

any one can help to stop the ubuntu server as a getaway

---

### Post by Lapp-Same on 2008-07-06
> **benlakhoua said:**
> Dear all
i have ubuntu server edition.
i have setup squid3 as transparant .
i have enabled ipv4 forward in the kernel.

what i want to do is when i stop the squid i dont want eny one to have internet in my system.

now my ubuntu is working as a getaway which is bad for my setup.

any one can help to stop the ubuntu server as a getaway

```
sudo /etc/init.d/dhcp3-server stopp
```

then you can go to the administration and edit what are starting on startup and disable dhcp3-server

---

