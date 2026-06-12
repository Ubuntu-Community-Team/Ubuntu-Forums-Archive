---
title: "Best OS for a Web Server? Your opinion Please.."
date: 2009-08-10
forum: Server Platforms
---

### Post by VipX1 on 2009-08-10
I'm reading my book on LAMP configuration. One of the points mentioned is for security you would want as few services as possible active on your web server. Instead of stripping an OS down for the task what would be a good OS to start with that would have only the bear essentials? 
This server's only job would be hosting websites!

---

### Post by wojox on 2009-08-10
Ubuntu Server Edition - comes with a nice optimized kernel and few features ( no GUI ).

---

### Post by cariboo on 2009-08-10
Using the Ubuntu server install, you only install the services you need.

---

### Post by piju on 2009-08-10
> **cariboo907 said:**
> Using the Ubuntu server install, you only install the services you need.

yes,
only install what service you need
and disable unneeded services

---

### Post by VipX1 on 2009-08-10
Is it true to say that Ubuntu Server has no service running until you add them? 
I ran my trail with Ubuntu server but I didn't know then what I know now and I installed Gnome.

---

### Post by amauk on 2009-08-10
to be honest, any distro

Debian based distros (like Ubuntu) can be configured to do various "tasks" using tasksel
```
sudo tasksel
```

Tick & untick the boxes to configure the various tasks you want

---

### Post by VipX1 on 2009-08-10
Fedora has a similar option at install.

---

### Post by Sef on 2009-08-10
List of common [Packages]("http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs/9.04") Installed by default for the server.

Now if you want everything shut off by default, then [openbsd]("http://openbsd.org") would be for you.

---

### Post by VipX1 on 2009-08-10
If I put Ubuntu server edition on the server, with no GUI and then use -X when connecting via ssh will it still give the GUI for the particular package on my ssh client?

---

### Post by amauk on 2009-08-10
> **VipX1 said:**
> If I put Ubuntu server edition on the server, with no GUI and then use -X when connecting via ssh will it still give the GUI for the particular package on my ssh client?
Yes,
You need to install xauth
```
sudo apt-get install xauth
```but you certainly don't need to install full-blown X to do simple x-forwarding

---

### Post by ibutho on 2009-08-10
Most Linux distros can do what you want. I tend to use netinstall versions to install a minimal system and then build up from there. If I use FreeBSD, I also do a minimal install and then build everything I need from ports (which also allows a lot of customisation).

---

### Post by VipX1 on 2009-08-10
My ssh client keeps timing out when I leave the terminal idle for 20+ minutes. The Server ssh_config is below but maybe the timeout is just something that happens when connected via the WAN.
```

Host 192.168.**.**
Port **
PasswordAuthentication no
ForwardX11Trusted yes
CheckHostIP yes
Protocol 2
ConnectTimeout 0

```

Has anybody else experienced this?

---

### Post by hessiess on 2009-08-11
Arch, Gentoo or any of the `build your own OS' distros, they are the only easey way to get rid of absolutly everything which you dont need.

---

### Post by VipX1 on 2009-08-11
> **hessiess said:**
> Arch, Gentoo or any of the `build your own OS' distros
I have to admit they are two new OS's to me but that's what I wanted from this post, great!

---

