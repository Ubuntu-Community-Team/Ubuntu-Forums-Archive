---
title: "Keyboard unconfigured"
date: 2011-12-01
forum: Server Platforms
---

### Post by barezi6 on 2011-12-01
Hi
when i installed my ubuntu server 8.04 LTS my keyboard was configured a little bad, some characters are exchange and now i can find this character ; to resolve the problem the only way is installing again the the server and config the keyboard again?

---

### Post by btindie on 2011-12-01
Depending on your version now you should be able to use

dpkg-reconfigure keyboard-configuration

The file where its set is /etc/default/keyboard

---

