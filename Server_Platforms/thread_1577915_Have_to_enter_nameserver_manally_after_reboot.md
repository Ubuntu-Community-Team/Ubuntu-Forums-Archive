---
title: "Have to enter nameserver manally after reboot"
date: 2010-09-19
forum: Server Platforms
---

### Post by sipickles on 2010-09-19
Hi,

I have a small webserver running ubuntu server 10.4. It runs fine except after every reboot, I get DNS errors.

I have to manually edit /etc/resolv.conf to add:
```

nameserver 192.168.1.1
```

the address of my internet gateway on my LAN. Obviously I am ignoring the warning in resolv.conf that this will be overwritten.

What is the correct way to fix this?

Thanks

Simon

---

### Post by Joe of loath on 2010-09-19
I think you have to adjust the DHCP settings to ignore the DNS suggested by the DHCP server. I'm not sure *how* to do this though.

---

### Post by windependence on 2010-09-19
Please post your /etc/network/interfaces file here so I can have a look.
 
-Tim

---

