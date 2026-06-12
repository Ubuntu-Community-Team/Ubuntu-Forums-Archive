---
title: "Strange DNS related(?) problem"
date: 2007-01-08
forum: Server Platforms
---

### Post by 8086ed on 2007-01-08
I'm in the process of setting up an Edgy server.  After I got SSH working, I moved the server to another location so it could be on all of the time.  I can connect to it via SSH, but when I try to update using sudo apt-get update, it can't resolve any hostnames.  I can ping google, but only using their ip.  Trying to ping google only gives 

```
ping: unknown host http://www.google.com/
```

Other computers on the same network function just fine.

Any ideas?

---

### Post by rth on 2007-01-08
What is in your /etc/resolv.conf? What should be there are DNS servers from your ISP, your router, or whatever way you access the Internet. However, you can also use something like OpenDNS and put in their DNS servers (208.67.222.222 and 208.67.220.220).

That is assuming that you have Internet access but are having resolution issues. I'm guessing that seeing as you can SSH to the box, that the network is working.

---

### Post by 8086ed on 2007-01-08
Great!  Changing my /etc/resolv.conf fixed it.  Thanks!

---

