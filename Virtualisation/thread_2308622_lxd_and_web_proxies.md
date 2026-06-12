---
title: "lxd and web proxies"
date: 2016-01-04
forum: Virtualisation
---

### Post by Christian_Tardif on 2016-01-04
Hi,

I'm new to LXD and trying to give it a try (!!!) in my lab environment. To go out on the internet, I need to get through a web proxy. It's working for standard stuff, as the environment has been patched through the web proxy. But when I try to launch an image (coming from remotely), I'm getting:

Creating ubuntu-32 error: Get [https://images.linuxcontainers.org:8443/1.0/images/c82fc7a8392a840848c494d79484169e3fd9f4f71ebfffbae5f55bc4de91ca5f:](https://images.linuxcontainers.org:8443/1.0/images/c82fc7a8392a840848c494d79484169e3fd9f4f71ebfffbae5f55bc4de91ca5f:) Unable to connect to: images.linuxcontainers.org:8443

If I'm checking with TCPDUMP at the same time, I can see that it's trying to access images.linuxcontainers.org directly on port 8443 instead of using the web proxy, configured from environment variables (http_proxy, https_proxy, HTTP_PROXY, and HTTPS_PROXY).

I can't find anything relevant on how to achieve that. Can someone help me?

Thanks.

---

### Post by Christian_Tardif on 2016-01-04
Oh! Forgot to mention....  if I try to get the link with wget, it works like a charm...

---

### Post by MAFoElffen on 2016-01-06
Just starting to play with LXD containers, but already had that host configured doing KVM (4 years) and Docker containers (2 years).

Usually, networking for a hypervisor is done 1 of 3 ways: internal (it own internal network between VM's but not to the outside world), External, it's own VM network (own NID) with access to the outside world, but not to the hot or host's netwrok, then a virtual switch/bridge (which just traditionally shares a host NIC and it on the same NID as the Host). Tha last has to be configured... (not usually a default)

I following the Ubuntu Wiki pages to configure a bridge (virtual switch) on my host. On that host, I have my bridge configured for it's 2d host NIC, so that they do their network on my main network through that card. My Vm's and container's network settings are the same as if they were a physical node on my network. In my VM's I set the VM to the bridge (virtual switch) to share the Host NIC. I also have another virtual switch going through my host's fiber channel, to share it on another segment that I use for just my servers.
RE:
[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)
[https://wiki.ubuntu.com/vlan](https://wiki.ubuntu.com/vlan)

Before that, with their default settings, I had to route between the two... as the VM network was a different NID than my main NID. I may go to back to a hybrid of this-- bridged to a host card, but subneted, to it's own NID and routed back to my main... to segment that section of my network.

There's supposed to be more options and possibilities for LXD contaners concerning networking. I honestly haven't tried them yet, but Dustin Kirkland mentions and does a walkthrough them in his blog here:
[http://blog.dustinkirkland.com/2015/06/the-bits-have-hit-fan.html](http://blog.dustinkirkland.com/2015/06/the-bits-have-hit-fan.html)
The Ubuntu wiki page on that:
[https://wiki.ubuntu.com/FanNetworking?_ga=1.69671888.1914232362.1442597649](https://wiki.ubuntu.com/FanNetworking?_ga=1.69671888.1914232362.1442597649)

---

