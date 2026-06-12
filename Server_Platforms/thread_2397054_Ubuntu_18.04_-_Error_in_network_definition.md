---
title: "Ubuntu 18.04 - Error in network definition"
date: 2018-07-24
forum: Server Platforms
---

### Post by JohnyBeGood on 2018-07-24
Hi,

I'm trying to set static IP for my server and I'm getting this error [https://prnt.sc/kalhj5](https://prnt.sc/kalhj5)
My other server (v16.04) is working [https://prnt.sc/kalkub](https://prnt.sc/kalkub) just fine with same setting (IP is different). 
Can someone point out what I'm doing wrong?

Thanks!

---

### Post by bizhat on 2018-07-25
The file is yaml format, that need some indentation for the lines.  That is you should add some space before via and link lines so it align same as "to" entty.

You can find more at 

[http://yaml.org](http://yaml.org)

---

### Post by JohnyBeGood on 2018-07-25
> **bizhat said:**
> The file is yaml format, that need some indentation for the lines.  That is you should add some space before via and link lines so it align same as "to" entty.

You can find more at 

[http://yaml.org](http://yaml.org)

Thank you!

Just in case someone runs into same issue here's the proper format:
```

# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
 version: 2
 renderer: networkd
 ethernets:
   ens33:
     dhcp4: no
     dhcp6: no
     addresses: [192.99.xxx.xxx/32]
     gateway4: 158.69.xxx.xxx
     nameservers:
       addresses: [8.8.8.8,8.8.4.4]
     routes:
     - to: 158.69.xxx.xxx/32
       via: 192.99.xxx.xxx
       scope: link



```

---

