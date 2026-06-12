---
title: "Server for home use"
date: 2010-09-01
forum: Server Platforms
---

### Post by jmore9 on 2010-09-01
Hello !

I am looking at installing a lamp server for my home use. 1 windows machine and 1 Ubuntu machine to be connected up to it.

Now once I get the server installed and the two machines talking to
to it, If I leave the Internet machine ( Ubuntu machine ) connected to it all the time, will that open up the lamp server to the internet ?

I do not want the lamp server on the internet only as a local server connected to both machines all the time.

Is that do able ?

Thanks in advance for any help.

---

### Post by arrrghhh on 2010-09-01
Do you have a router...?  Or do you have an Ubuntu computer that doubles as your router...?

---

### Post by thegaffney on 2010-09-02
Yeah its definitely possible,

Someone correct me if im wrong, but I dont think it would be viewable outside your home network, unless you specifically tell your router to forward port 80 connections to your server. Other wise even if someone typed in your external ip address coming from your ISP, they would just get your router, or (hopefully) a message saying that they dont have permission to access your router. ?

But also, we have a virtual host setup for our internal website that we dont want out to the public, but we also have a public website, so to prevent outside connections from being able to see it we added/changed the virtual host settings for it to deny all except 192.168 (our local network ip range)

So as far as i have messed with, those are the 2 ways I know to not let that happen

---

### Post by Iowan on 2010-09-02
Ordinarily, it's hard enough to *make* a machine visible from the internet. I'm also of the opinion that unless the (internet) machine is compromised (or badly mis-configured), it *shouldn't* make the server visible externally.

---

### Post by CharlesA on 2010-09-02
> **thegaffney said:**
> Yeah its definitely possible,

Someone correct me if im wrong, but I dont think it would be viewable outside your home network, unless you specifically tell your router to forward port 80 connections to your server. Other wise even if someone typed in your external ip address coming from your ISP, they would just get your router, or (hopefully) a message saying that they dont have permission to access your router. ?

On my router, it just gets an error message displayed that the connection timed out, since I don't have remote management enabled. Should be the same for almost all other routers as well.

> **Iowan said:**
> Ordinarily, it's hard enough to *make* a machine visible from the internet. I'm also of the opinion that unless the (internet) machine is compromised (or badly mis-configured), it *shouldn't* make the server visible externally.

Iowan is correct. The only way I can think of having a machine automatically visible to the internet is having UPNP enabled so that it opens up the correct ports, but (imho) UPNP is a bit pointless when you can just forward ports yourself.

---

