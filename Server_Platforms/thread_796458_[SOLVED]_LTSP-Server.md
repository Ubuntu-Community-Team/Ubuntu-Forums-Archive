---
title: "[SOLVED] LTSP-Server"
date: 2008-05-16
forum: Server Platforms
---

### Post by Lapp-Same on 2008-05-16
Hi, I wanna setup a LTSP-server (Thin-Client)

But shall i use Ubuntu 8.04 server Edition "Hardy Heron" and install it trough the terminal?

Or use the Ubuntu alternate CD and use "instal LTSP-Server" when i press F4 ?


What's best.. when it comes to performance?

-Christoffer-
Thanks for posts

---

### Post by songshu on 2008-05-16
there is no difference in performance, it will both do exactly the same.

i would say that the automatic way is fine if you just want to use it yourself in a non-production environment or just see what it does.

and the manual way will help you to understand the underlying process a little better so you actually know what it does so you can tweak the hell out of it and offer support if needed.


you choose.....

---

### Post by Lapp-Same on 2008-05-16
> **songshu said:**
> there is no difference in performance, it will both do exactly the same.


Soo i can still shange the ip-adress to the server... and make it my DHCP-Server?

---

### Post by songshu on 2008-05-16
> **Lapp-Same said:**
> Soo i can still shange the ip-adress to the server... and make it my DHCP-Server?

not sure what you mean, but you can either have a seperate dhcp server that directs your clients to the ltsp server (think its something like next-server ip_address)

or you have the dhcp server running on the ltsp server, which is the default setup

---

### Post by Lapp-Same on 2008-05-16
> **songshu said:**
> or you have the dhcp server running on the ltsp server, which is the default setup

This one... But i dont wanna use the 192.168.x.1 nettwork who is default... i can still change this in the auto-installer? 

Thanks for soo fast respons!!

---

### Post by songshu on 2008-05-17
its been a long time since i played with ltsp, not sure if you can do that during the ltsp build.

but it uses dcp3-server (from the top of my head) you can set that to anything you like

---

### Post by Lapp-Same on 2008-05-17
> **songshu said:**
> its been a long time since i played with ltsp, not sure if you can do that during the ltsp build.

but it uses dcp3-server (from the top of my head) you can set that to anything you like

Yeah, thanks for you're replays!

---

