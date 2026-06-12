---
title: "Connection issues using Ubuntu on Virtualbox."
date: 2016-01-19
forum: Virtualisation
---

### Post by jacob95 on 2016-01-19
I recently installed Ubuntu 14.04 onto VirtualBox to try it out before using it as my main OS, Unfortunately I cannot get any internet connection through this OS. I have used two different routers so can confirm it is not a problem with that. I always get "Server not found" on firefox, despite the internet working fine on my host machine! Please help, this is stressing me out.
My host machine is Windows 10 by the way.

---

### Post by slickymaster on 2016-01-19
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by slickymaster on 2016-01-20
Check your Windows firewall settings. Has VirtualBox been allowed internet access?

---

### Post by MAFoElffen on 2016-01-20
If you go to the settings of your VM, what do you have your NIC pointed to? Easiest to just allow a connection to the internet, connection to other VM's (on the same NID), would be to choose "NAT".With NAT you are on a different NID as your host, so you would not be able to ping your host, but you would be able to ping your gateway. For internal, VM's with the same setting can talk with each other (they are on the same NID), but cannot get out anywhere. Bridged means you bridge to the same NID as your host. Host only means you can talk with your host and other VM's with that setting. That goes to host through it's local home ip (127.0.0.1, does not get out...).

So if that still have problems, next would be to post the results from your guest:
```

ifconfig -a
ping 127.0.0.1
ping 192.168.1.1   # change to your own specific gateway IP
ping 8.8.8.8

```

---

