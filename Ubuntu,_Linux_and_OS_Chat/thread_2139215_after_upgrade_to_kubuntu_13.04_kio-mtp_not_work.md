---
title: "after upgrade to kubuntu 13.04 kio-mtp not work"
date: 2013-04-26
forum: Ubuntu, Linux and OS Chat
---

### Post by borisov87 on 2013-04-26
after upgrade to kubuntu 13.04 kio-mtp not work.
With 12.10 no problems, but after upgrade to 13.04 i have problem,  dolphin not display mtp icon, i remove kio-mtp with purge , and install  now,- problem continue.

---

### Post by schnelle on 2013-07-02
You need to update libmtp: 

sudo apt-add-repository ppa:aglasgall/libmtp
sudo apt-get update
sudo apt-get dist-upgrade

---

