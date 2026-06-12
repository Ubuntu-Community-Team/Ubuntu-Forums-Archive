---
title: "Ubuntu Server In Virtual box"
date: 2013-04-12
forum: Server Platforms
---

### Post by serverMe on 2013-04-12
I installed ubuntu server in the virtual box. The installation was smooth. I installed all stuff I need such as apache, sql, php etc//

The virtual box works well. It says my IP is 10.0.2.15

I am not sure how I can connect with my mac via ssh?

so how do I connect to the ubuntu server via ssh when I am outside home network.. my computer IP (where the virtual box is install) is different.. its like 67.xx.xxx.xx ... please suggest me how to reach the ubuntu server via ssh so that I can work on it.. also Need to view a webpage since I installed apache in virtual box ubuntu server.

Please help. :)

---

### Post by CharlesA on 2013-04-12
Depends on how you have your network setup. I usually use bridged networking so the VM appears to be on the same network as the host, but I am also on a private network behind a router.

If you are directly connected to the internet, you might get away with using nat on the VM with port forwarding, but I don't know if that will work ok or not.

---

### Post by serverMe on 2013-04-12
port forwarding with bridged network did work to change the IP address. But I am still not able to ssh to the virtual machine even though I am in the same network. If its not vortual machine and its a standalone wired network then I dont have any issue ssh'ing to the system. Only in virtual box i am not able to ssh. :(

---

### Post by CharlesA on 2013-04-12
If you are trying to access the machine from outside your local network, you need to make sure port forwarding on the router is set up correctly.

---

