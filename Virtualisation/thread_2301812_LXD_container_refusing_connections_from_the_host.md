---
title: "LXD container refusing connections from the host"
date: 2015-11-05
forum: Virtualisation
---

### Post by drm-redmenace on 2015-11-05
I'm pretty new to LXD (and LXC) having recently discovered them.   I'm making progress with the basic interactions with images and  containers and now am trying to get my application running inside one.  This is my first try doing anything useful with LXD.


  Currently I am stuck on a problem connecting to a service running in  the container from the host.  I get a "connection refused" error.  More  details below:

The host is Ubuntu Server 14.04 on my laptop - it's a new install and  is pretty plain-vanila.  I let the system do all of the configuration  (including the lxcbr0 bridge) and haven't changed any of the  out-of-the-box defaults.

  I'm running a container based on a CentOSv6 image.  The container is  started and inside it I am running a web server.  From within the container  I can connect to the web server on port 80 just fine (by running "curl <hostname>" [edit: I initially recalled I had specified the IP, but in fact I had specified the hostname.  This was the key to figuring things out]).  I get a valid response from the local web server from  within the container.  Yay.

From the host, however, I am unable to connect to the web server.  If  I try the same "curl 10.0.3.49" from the host then I get a "connection  refused" error.

So, I'm trying to figure out what it will take to allow connections  from the host to the the web server running in the container.  I have  spent a few hours googling and have not found the answer (or been too  dense to recognize it).


The firewall is disabled ("ufw status" says so).  What am I missing?  Thanks in advance.

---

### Post by drm-redmenace on 2015-11-05
I solved my own problem.  The apache Listen directive specified the hostname, which I hadn't notice resolved to the loopback device and not the IP on the LXC bridge.  I changed the Listen directive to listen on the correct IP (10.0.3.4) and then things worked.

---

