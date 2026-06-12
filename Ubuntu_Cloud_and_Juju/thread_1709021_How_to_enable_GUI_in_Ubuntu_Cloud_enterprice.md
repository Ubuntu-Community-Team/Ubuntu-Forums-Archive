---
title: "How to enable GUI in Ubuntu Cloud enterprice"
date: 2011-03-17
forum: Ubuntu Cloud and Juju
---

### Post by Mohamed_khalil on 2011-03-17
Dear All, ):P
I just installed Ubuntu 10.10 cloud enterprise , after running it the command interrupter comes to the screen , I just wanted to go for GUI how ?

---

### Post by kim0 on 2011-03-18
Hi,
You shouldn't really start a GUI (Gnome) there. Since all resources should go into running UEC services and VMs. You're supposed to connect to it over the web interface from another machine, and control it using euca- commands or something like elasticfox

However if you do want to use it as a normal desktop, "sudo apt-get install ubuntu-desktop" should get the job done afaik :)

---

