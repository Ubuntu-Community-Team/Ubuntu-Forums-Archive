---
title: "Installed &quot;Zenity&quot; by mistake on the server"
date: 2015-03-29
forum: Server Platforms
---

### Post by pirlea on 2015-03-29
Hi All,

I made a huge mistake and installed Zenity package on 14.04 server.
Could someone help me track changes and uninstall them?
Thank you.

---

### Post by kerry_s on 2015-03-29
sudo apt-get purge zenity
sudo apt-get autoremove
sudo apt-get clean

---

### Post by pirlea on 2015-03-30
Thank you!!!

---

