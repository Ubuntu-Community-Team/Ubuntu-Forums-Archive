---
title: "Ubuntu 10.04 desktop vs cloud server edition"
date: 2010-07-15
forum: Server Platforms
---

### Post by fred2028 on 2010-07-15
What's the difference in terms of scalability? We would be hosting videos and FOSS collaboration tools (wiki, forums, etc.) on 4 separate servers. If I install the cloud server, I will need to install the GUI anyways. The servers are all brand new

- 2x Intel Xeon quad cores 2.4 GHz
- 12 GB DDR3 RAM
- 4 Ethernet ports

What benefits would cloud server provide over desktop and vice versa?

---

### Post by gr4nf on 2010-07-15
Server edition won't install a lot of the extra software you will get with desktop edition (GIMP, Totem Movie Player, Rythmbox, etc...) and you would have to install the GUI with apt after the installation was complete, if you needed it. There isn't really that much difference once you get the GUI, besides some processes being automated that are notification/request based in desktop edition. Basically, if you want less maintenance, go with the server edition. If you want some universal functionalities, go with the desktop (although you should be able to just use apt or the package manager to get anything you might want on the server edition when you realize later that you need it).

---

### Post by fred2028 on 2010-07-15
> **gr4nf said:**
> Server edition won't install a lot of the extra software you will get with desktop edition (GIMP, Totem Movie Player, Rythmbox, etc...) and you would have to install the GUI with apt after the installation was complete, if you needed it. There isn't really that much difference once you get the GUI, besides some processes being automated that are notification/request based in desktop edition. Basically, if you want less maintenance, go with the server edition. If you want some universal functionalities, go with the desktop (although you should be able to just use apt or the package manager to get anything you might want on the server edition when you realize later that you need it).
 But my question is the difference between desktop and CLOUD ... I'm really eager to know what benefits CLOUD will have.

---

### Post by gr4nf on 2010-07-15
With cloud you'll get a well-designed GUI to do everything that you would have to do manually if you didn't have it. Cloud has a very specific purpose (managing local server services in a public or private environment). If that is exactly what you want to do, cloud would work great. In my personal opinion, if you CAN easily do the things 'manually' (meaning setting up your own web, sql, ftp, whatever server on the machines individually) then that is the better option. It's really up to your personal preference, though. If you like the cloud interface (and you really should at least try it) then it's great.

Cloud pros:

-easy to use, quick to learn
-allows you to manage multiple servers at once easily
-makes adding functionality painless.

Cloud cons:

-probably a loss in overall performance when compared to a well-configured 'normal' server
-difficult to deal with if you want to do something that isn't directly supported.

---

