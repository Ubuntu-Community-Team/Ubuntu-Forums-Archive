---
title: "Connection between the Host and Guest"
date: 2010-04-02
forum: Virtualisation
---

### Post by praveensripati on 2010-04-02
I have created a Ubuntu 9.10 Guest on Ubuntu 9.10 Host using VirtualBox. When not connected to the network, IP is not allocated to the Host and so is not able to communicate with the Guest. Not able to Ping the Guest from the Host. How can the Host and the Guest communicate when the Host is not connected to the network? I am using a bridged adapter in the Network settings for the Guest.

Thanks,
Praveen

---

### Post by praveensripati on 2010-04-02
I choose host only adapter in VirtualBox and it helped.

[http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)

Praveen

---

