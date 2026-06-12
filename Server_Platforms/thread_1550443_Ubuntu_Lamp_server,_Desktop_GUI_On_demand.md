---
title: "Ubuntu Lamp server, Desktop GUI On demand"
date: 2010-08-11
forum: Server Platforms
---

### Post by Sukhwinder.net on 2010-08-11
Hi
I have an working ubuntu server 6.10 with desktop. I want to upgrade my  server to Ubuntu 10.04 LTS now. I don't want the server to be booted to  GNOME desktop, but still i want GNOME desktop be there so that i can  start it when needed. By default ubutnu should boot in CLI. How cam i do  that? is this a good way for server installation? or any other  recommendation please.

PS My server is connected to local network and not to internet.

Thanx & regards

Sukhwinder Singh

---

### Post by linux18 on 2010-08-11
remove gdm
sudo apt-get remove gdm
after you install and it will automatically boot to a cli

---

### Post by Sukhwinder.net on 2010-08-11
> **linux18 said:**
> remove gdm
sudo apt-get remove gdm
after you install and it will automatically boot to a cli

Can i start Gnome later on when i require it? I don't want to remove GUI permanently, but want Ubuntu to not to go with Desktop by default, but i should be able to start desktop manually.

---

### Post by linux18 on 2010-08-11
yeah just type startx to start gnome

---

