---
title: "Ubuntu VMWare: Browser is fast/normal, PHP5 is extremely slow - http requests"
date: 2010-09-14
forum: Virtualisation
---

### Post by devknob on 2010-09-14
Im running a VMWare workstation 7.1.1 of Ubuntu 32bit desktop 10.04.1 Lucid Lynx on Windows Vista Home Premium 64

Thru the browsers everything seems to be running at the right speed. It seems like its just PHP5 - and maybe anything non-browser , goes really really way too slow

echo file_get_contents("http://google.com"); 

The above takes maybe aorund 6-7 seconds to load instead of fast as usual in php5, not the browser.

Anyone have any clue what the deal is?

---

### Post by devknob on 2010-09-14
i found this regarding apache2 and slow http requests
Regarding the network, are you having errors or CRCs? Check it with netstat:

netstat -i
Take a look the RX-ERR, RX-DRP, TX-ERR and TX-DRP columns. Ideally, these values should be 0.

Hope this helps.
--------------
so I ran netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1492 0      5176      0      0 0          2442      0      0      0 BMRU
lo        16436 0       450      0      0 0           450      0      0      0 LRU
------------
Problem is, im not a network guy and this might as well be japanese to me - anyone see the problem?
I checked a simple echo "rawr" and it responds in a snap as expected. The slowdown comes when im telling php to pull content from elsewhere.

---

