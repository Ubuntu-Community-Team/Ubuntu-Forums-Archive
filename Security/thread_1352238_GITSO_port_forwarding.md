---
title: "GITSO port forwarding"
date: 2009-12-11
forum: Security
---

### Post by gewitty on 2009-12-11
I am attempting to use GITSO to support a couple of remote machines.

I have forwarded port 5500 on my router and also opened that port in Firestarter, but cannot get any connections.

I checked the port using the open port checking tool at [www.canyouseeme.org](www.canyouseeme.org). This returns an error, saying that port is not visible due to a timeout.

I tried temporarily switching off NAT on my router and also shut down Firestarter, but still got no connection.

The router is a Huawei EchoLife HG520b, which seems to have quite a lot more settings available than my previous Belkin and Linksys routers, so I'm wondering if either I'm missing something critical on the router or if my ISP (TalkTalk) is blocking the port.

---

### Post by cariboo on 2009-12-11
Have you also opened a port on the router to enable port forwarding? If not, that's why [canyouseeme]("http://canyouseeme.org") is telling you the port is closed.

---

### Post by gewitty on 2009-12-11
As far as I can see, the port is open. The attached screen-shot shows the current set-up.

---

### Post by cariboo on 2009-12-12
If you are using the firewall in your router, there isn't really any need for a firewall on the computer. purge the firewall rules and see if it makes a difference.

---

