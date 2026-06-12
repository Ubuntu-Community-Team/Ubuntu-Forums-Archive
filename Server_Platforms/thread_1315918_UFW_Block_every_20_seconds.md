---
title: "UFW Block every 20 seconds"
date: 2009-11-05
forum: Server Platforms
---

### Post by HuXu on 2009-11-05
I have set up UFW and I am seeing 

[UFW BLOCK] IN=eth0 OUT=(some mac address) SRC=169.254.1.76 DST=255.255.255.255

Now the SRC 169 is an invalid IP address but this is showing up every 20 seconds.  What is this?

---

### Post by gombadi on 2009-11-05
> 
[UFW BLOCK] IN=eth0 OUT=(some mac address) SRC=169.254.1.76 DST=255.255.255.255


There is some device on your network that has auto configured itself and given itself the ip address of 169.254.1.76 and it is sending out a broadcast packet every 20 seconds.

You will need to find what the device is and configure it.

---

