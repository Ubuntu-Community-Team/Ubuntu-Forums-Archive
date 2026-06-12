---
title: "Problems with webserver and VMWare"
date: 2008-10-28
forum: Server Platforms
---

### Post by zeitler on 2008-10-28
Hi,
I'm recently new on Linux world and I'm trying to configure a web server in a virtual machine (VMWare 2.0).
I've already tried with ubuntu server. I've changed /etc/nework/interfaces to static ip. In my local network apache webserver works fine and I'm able to view all of my webpages. When I try to access a web page using the Internet it just don't open the page, it goes timeout. I have a no-ip.com account and my router it's configured properly (I believe it does). 
I've tried using a dhcp ip (maybe it was static ip configuration with a bad configuration) and configure in router to that ip and it also doesn't work.
I've installed ubuntu desktop and I tried everthing again and it still doesn't work.

When I configure the router to my laptop it works fine over the Internet. It just doesn't work with vmware.

Any ideas?

Thanks
zeitler

---

### Post by windependence on 2008-10-28
Did you set up your install with bridged networking? It should work just like it was on the physical network.

-Tim

---

### Post by zeitler on 2008-10-28
yes.
I ping virtual machine and it works perfectly. Everything is configured as the laptop. 
The only thing different is the virtual machine.

thanks
zeitler

---

