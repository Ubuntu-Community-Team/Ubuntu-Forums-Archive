---
title: "Ubuntu 16.10 keep freezing in some minutes everytime I log in"
date: 2016-11-02
forum: Virtualisation
---

### Post by tech-gamer on 2016-11-02
I use VMware workstation 12 and ubuntu 16.10 and its keep freezing when I am doing something! Please help me there is no output I see or error message sometime all system get frozen or mouse is working but UI and that stuff isnt working!

---

### Post by ian-weisser on 2016-11-02
Check your /var/log/syslog for clues
Run 'top' on your desktop you you can see what is eating resources during a slowdown or freeze

---

### Post by tech-gamer on 2016-11-05
Found a solution I need to enable "Virtualize Intel VT-x/EPT or AMD-V/RVI" on VMWare

---

