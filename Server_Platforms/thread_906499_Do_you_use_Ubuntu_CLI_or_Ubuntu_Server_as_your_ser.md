---
title: "Do you use Ubuntu CLI or Ubuntu Server as your server platform?"
date: 2008-08-31
forum: Server Platforms
---

### Post by PryGuy on 2008-08-31
Good day! I wonder how many people here install Ubuntu Server for low end servers, say for home/small office use. I ask that because I personally do just fine with my Feisty CLI installation used as a server with DHCP/PPTP/SSH/PXE/Samba/Wi-Fi up and running. The best thing about that is that I use the same debs for server and desktop.

---

### Post by Silent Ninja on 2008-08-31
The CLI (command-line) will ALLWAYS be faster than the graphic styled, because it saves all the memory / cpu for printing and processing of graphics, and you can use it on anything else.

If you know enough of your system, you won't need a graphic interface. You can even browse on the web using lynx on text-mode.

---

### Post by promodus on 2008-08-31
Are you talking about who admins a server via command line
vs.
Those who may use GUI based utilities / web management?

---

### Post by cariboo on 2008-08-31
The OP was asking how we setup our servers. If you use the mini.iso to install you can install just to cli and use the desktop kernel, as opposed to installing the server version using the server kernel.

Jim

---

### Post by schettj on 2008-08-31
I don't remember. I think I installed 8.04 desktop, then the server kernel + desired services. I run a centos 5 text install in a vm as my "main" outward facing server (web/ssh). I know, weird.

---

### Post by Oldsoldier2003 on 2008-08-31
> **cariboo907 said:**
> The OP was asking how we setup our servers. If you use the mini.iso to install you can install just to cli and use the desktop kernel, as opposed to installing the server version using the server kernel.

Jim
Another plus about using the mini.iso is once you've installed you won't need to update right away as you would if you downloaded the alternate installeror live cd iso. This might be a decisive advantage for those that have limited bandwidth usage.

---

### Post by PryGuy on 2008-09-01
> **promodus said:**
> Are you talking about who admins a server via command line
vs.
Those who may use GUI based utilities / web management?Nope, I'm talking about text install with 'generic' kernel vs. 'server' kernel. Both without X server installed.

---

