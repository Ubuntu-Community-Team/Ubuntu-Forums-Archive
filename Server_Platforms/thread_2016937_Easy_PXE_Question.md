---
title: "Easy PXE Question"
date: 2012-07-04
forum: Server Platforms
---

### Post by robby0328 on 2012-07-04
My current config is:
default-lease-time 600;
max-lease-time 7200;

allow booting;
allow bootp;

subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.3 192.168.2.253;
  option broadcast-address 192.168.2.255;
  option routers 192.168.2.254;            
  option domain-name-servers 192.168.2.254;
}

group {
  next-server 192.168.2.50;                
  host tftpclient {
    hardware ethernet  90:2B:34:60:8C:E4; 
    filename "pxelinux.0"; 
  }
}
My question is can I wildcard the mac address to allow anything on the  network to boot to it? I know why for a business they wouldn't want that  but it's going to be on a home network and im not too worried about it.

---

### Post by HugoSerrano on 2012-07-05
Hello!

Think you just need to move "up" the 
>    next-server 192.168.2.50;                and
>      filename "pxelinux.0"; into your global network configuration.


something like this:

```

default-lease-time 600;
max-lease-time 7200;

allow booting;
allow bootp;

subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.3 192.168.2.253;
  option broadcast-address 192.168.2.255;
  option routers 192.168.2.254;            
  option domain-name-servers 192.168.2.254;
  next-server 192.168.2.50;                
    filename "pxelinux.0"; 
}
```

then all your network clients can boot via PXE.


Best Regards!

---

### Post by robby0328 on 2012-07-05
Hehehe I tried that and it didn't work. I realized what I did wrong. I was testing it on a virtual machine and didn't put the vm on the same network.. Doh. Thank you though this configuration worked out great.

---

