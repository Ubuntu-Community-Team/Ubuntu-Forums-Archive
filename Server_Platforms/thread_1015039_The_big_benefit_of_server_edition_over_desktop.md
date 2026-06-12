---
title: "The big benefit of server edition over desktop"
date: 2008-12-18
forum: Server Platforms
---

### Post by cl333r on 2008-12-18
Hi folks,
I'm planning to run GlassFish with MySQL 5.0 on Ubuntu and I'm wondering what's the big benefit (aside from saving like 100 MB of RAM by not running a desktop, which is no longer an issue nowadays) from installing a server edition rather than the desktop one?
Does the server edition do (much) faster disk read/writes?
Robustness - the desktop edition never crashed when using.
There are kernel tweaks, but again, in real world how much do I gain using a "server kernel", I would only use the server version if were talking about 20-30% speed increase or so.
I don't need the packages that come with the server edition since I use my own configuration of GlassFish.

---

### Post by Caduceus on 2008-12-18
Not sure whether you know, but the server edition (as far as I know) is just that, the server. Has no GUI and whatnot so it will run faster having to load the X window system. I should imagine the server version is faster and more robust, as I think big companies use it (though not as much as other Linux servers)

---

### Post by Bachstelze on 2008-12-18
From personal experience, the impact is minimal. I have a Debian Sid server with X installed (running Fluxbox as a Window Manager) and Xchat running in it permanently (plus some other programs every now and then); and my load average rarely goes above 0.1.

---

### Post by drubin on 2008-12-18
> **cl333r said:**
> Hi folks,
I'm planning to run GlassFish with MySQL 5.0 on Ubuntu and I'm wondering what's the big benefit (aside from saving like 100 MB of RAM by not running a desktop, which is no longer an issue nowadays) from installing a server edition rather than the desktop one?
Does the server edition do (much) faster disk read/writes?
Robustness - the desktop edition never crashed when using.
There are kernel tweaks, but again, in real world how much do I gain using a "server kernel", I would only use the server version if were talking about 20-30% speed increase or so.
I don't need the packages that come with the server edition since I use my own configuration of GlassFish.

Like you said the kernel is differnt. I would suggest installing the server edition and setting up your own DE

---

### Post by bapoumba on 2008-12-18
Moved to Server.

---

### Post by RealPSL on 2008-12-21
The link below details the differences between Desktop and Server. I think you will find that it really does matter what you choose.

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel")

---

