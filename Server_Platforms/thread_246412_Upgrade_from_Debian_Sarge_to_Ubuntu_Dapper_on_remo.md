---
title: "Upgrade from Debian Sarge to Ubuntu Dapper on remote server"
date: 2006-08-29
forum: Server Platforms
---

### Post by aleksabl on 2006-08-29
Hi,

I would like to upgrade my dedicated server (which I do not have physical access to) from Debian Sarge to Ubuntu Dapper. Does anyone have any clues on how to do this? Is it as easy as just updating the /etc/apt/sources.list file and do a sudo aptitude update + dist-upgrade + install ubuntu-server?

It is a clean install with no additinal packages installed.

I'd appreciate any response,

Aleksander

---

### Post by matthew on 2006-08-29
I haven't done it on a remote server, so you might want to wait until you get more responses. 

That said, I upgraded a computer from Debian Sarge (when it was still testing) to Ubuntu Breezy with no major problems. I seem to recall I had to force a couple of packages to upgrade, but really it wasn't much different from an upgrade within Debian or within Ubuntu from one release to another. That was with a desktop installation, which has a lot more packages than the general server (like X for example). For a server I would think it would be pretty simple.

---

### Post by aleksabl on 2006-08-30
Now it seems that the hosting guys was willing to install Ubuntu Dapper manually for me :) Anyway, thanks for your response!

---

