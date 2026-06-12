---
title: "Mobile internet configuration."
date: 2015-05-06
forum: Ubuntu Phone and Tablet
---

### Post by jtappin on 2015-05-06
On the BQ Aquaris Ubuntu, I have been able to get an IP address over my carrier (lebara), by following (and adapting) the manual setup instructions on the Geek Squad website ([http://www.geeksquad.co.uk/articles/lebara-apn-settings](http://www.geeksquad.co.uk/articles/lebara-apn-settings)). However I can't access the web or even ping anything (it looks like there's no DNS everything ). 

ifconfig in a terminal gives:
```

ccmni0    Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr: 10.xxx.xxx.xxx  Mask:255.255.255.0
          UP RUNNING NOARP  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3947 (3.9 KB)  TX bytes:5804 (5.8 KB)

```
/etc/resolv.conf contains only the single nameserver 127.0.1.1 (which is clearly a loopback address),and the dns-nameserver command is not present on the system.

Is there anything else obviously wrong here? e.g. is the NOARP setting rather the BROADCAST & MULTICAST and a Broadcast address that I would expect to see on an ethernet connection an issue?
And is there a way to find/add nameservers?

---

### Post by lgd on 2015-05-08
> And is there a way to find/add nameservers?
I suggest a new line in /etc/resolv.conf as a first test. But you can install dns-nameserver (if in the sources) by making the system writable and using apt-get. But make backups before and learn how to use fastboot to reset your system with a backup. I don't see any information to Ubuntu Touch in the community wiki here but in a German construction wiki page or official at [developer.ubuntu.com]("https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/").

---

