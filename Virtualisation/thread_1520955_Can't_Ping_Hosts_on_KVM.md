---
title: "Can't Ping Hosts on KVM"
date: 2010-06-30
forum: Virtualisation
---

### Post by Addiction2Code on 2010-06-30
Hello, I setup a server to run on KVM/Qemu, however, I cannot ping the the server from a remote host. The server can be pinged from the computer that KVM is running on but it cannot be pinged from my Desktop in my office. In theory the devices are on different networks (eth0 and virbr0) but the KVM host can access the Internet so something must be working. How can I ping these hosts? Is there a way to put my hosts on the same network as eth0?

---

### Post by MystaMax on 2010-06-30
I'm by no means, an expert on this. But, I feel I can point you in the right direction. Have a look at the link below. Basically, you want to setup a network bridge.

[https://help.ubuntu.com/10.04/serverguide/C/libvirt.html#virtual-networking](https://help.ubuntu.com/10.04/serverguide/C/libvirt.html#virtual-networking)

Hope that helps.

---

