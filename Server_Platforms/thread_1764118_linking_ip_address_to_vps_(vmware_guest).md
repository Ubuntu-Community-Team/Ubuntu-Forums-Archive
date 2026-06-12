---
title: "linking ip address to vps (vmware guest)"
date: 2011-05-21
forum: Server Platforms
---

### Post by n0tiz on 2011-05-21
I have a dedicated server which is located in Germany under ip address xxx.xxx.xxx.xxx (i will refer to it as IP1). This server is running ubuntu server 10.04.

I have ordered and received an additional ip address xxx.xxx.xxx.xxx (refer to as IP2). This second ip address i have linked to my server with the following command:
```
sudo ip addr add xxx.xxx.xxx.xxx/xx dev eth0
```Surfing to IP2 gave me the default page of apache2.

And next I have installed VMware server 2.02. VMware is running a guest system with ubuntu server 10.04. The networking on this guest is done by vmnet8 NAT

And now come the problem... I want to link IP2 to the guest operating system, so that it works as a full server but in fact is a vps. I've googled and tried some things about iptables, but I don't understand a lot of it... And since this IP2 doesnt come out on my default page of apache2. So I think something is ****** up...

I hope someone will be able and willing to help me linking this second ip to the vps. If needed I still can change the networking on the guest to bridged...

---

