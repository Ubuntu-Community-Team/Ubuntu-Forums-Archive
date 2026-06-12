---
title: "No Internet in server 14.04"
date: 2015-08-04
forum: Server Platforms
---

### Post by danny52 on 2015-08-04
Hey, I currently have a server running Ubuntu 14.04 it is not getting any internet access. DNS and Nameservers are set to 8.8.8.8, Static IP is set but can't ping any websites. I can ping internal devices. Any help on this would be great!

Thanks

---

### Post by jason_gibson2 on 2015-08-04
Is your gateway set in the /etc/network/interfaces file?

---

### Post by nerdtron on 2015-08-05
Better to provide the whole content of the /etc/network/interfaces file. 
And what is the current routing table?
```
sudo route -n 
```

---

### Post by TheFu on 2015-08-05
Definitely need to see the routing table.

---

