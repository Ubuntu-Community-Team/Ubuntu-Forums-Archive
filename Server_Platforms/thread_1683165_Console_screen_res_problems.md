---
title: "Console screen res problems"
date: 2011-02-07
forum: Server Platforms
---

### Post by ubun2d00d on 2011-02-07
Hi everyone,
I have just installed Ubuntu 10.04 Server Eddition on a Dell PowerEdge 700. It is just going to be something I can use as a dumb terminal to ssh into my other servers and monitor their system usage etc. Unfortunatly the console screen resolution is stuck at 620x480@60hz. I have tried adding a 'vga=' kernal peramitor and also a 'video=' kernel parameter using various modes and combinations with both, but no success. In the first instance adding any VGA code above 620x480 takes the screen's refresh rate (normal 60hz) out of range and the monitor will not display the video. In the second instance (the video parameter) nothing happens and the parameter seems to be ignored. There is nothing unusual in my /var/log/boot.log file and extencive Googling hasn't got me very far. 

Will greatly appreciate any help and if anyone needs any more info I will be glad to provide it.

Thanks.

---

### Post by ubun2d00d on 2011-02-28
Anyone?

---

