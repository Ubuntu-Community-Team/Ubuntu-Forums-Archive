---
title: "apache not working with external ip"
date: 2008-11-16
forum: Server Platforms
---

### Post by kungfu71186 on 2008-11-16
I read some tutorials and tried to add it so that accessing a website using my external ip would work, but i cant seem to get it to work. It works using localhost and the internal ip.

Any ideas would be much appreciated. I also have this setup with vmware if that makes a difference. I tried to bridge the network connection instead to see if that made a difference.

---

### Post by cariboo on 2008-11-17
If you are using a router, you will have to port forward from your server to the router. The best way to do that is to set a static ip on the server, and then port forward to that ip address in your routers management console. There are so many different routers out there that it is pretty hard to tell you how to exactly do it, so it is best to consult the documents that came with your router, they are usualy located on the cd that came with your router.

After you have set up port forwarding go [here]("http://www.canyouseeme.org/") to see if your ISP is blocking any ports.

Jim

---

### Post by Dedoimedo on 2008-11-17
Hello,

Are you using any router / firewall in your setup? Maybe you need some advanced rules to allow traffic.

When you say the external ip, you do mean ip? Because if you're talking about names (fqdn), then you also need a dns to make it all work.

Dedoimedo

---

### Post by kungfu71186 on 2008-11-17
Heh, wow that sucks. Forgot to change the IP on port forwarding. Works now thanks.

---

