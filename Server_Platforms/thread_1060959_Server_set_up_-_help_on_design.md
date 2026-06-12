---
title: "Server set up - help on design"
date: 2009-02-05
forum: Server Platforms
---

### Post by Mr.Carramba on 2009-02-05
hi,

I will be soon setting up an 2xXeon Quad machine for scientific calculations and simulation.  

The users need to have be able use some kind of GUI, like KDE, Gnome or other.
My questions are:
should I install ubuntu 8.10_64 desktop directly? so that gnome can be run?
what is the preferred way to manage cores and cpu. I mean if there are 3 user logged in I would like to be able to give priorities on jobs. For example assign 4 cores for one job and and 1 to each of the rest, leaving one for the system. Is it possible to control it and administrate?
Should I go for another setup?

All suggestions and advice are welcome!

Thank you in advance!

C

---

### Post by cariboo on 2009-02-05
Before making assumptions about what your server needs, have a look at this [Server Guide]("http:///doc.ubuntu.com/ubuntu/serverguide/C/").

Jim

---

### Post by borahshadow on 2009-02-05
You could set it up with virtual machines. The host OS (base install) could be the high priority calculations and then you could make a virtual machine with a GUI and only assign it a certain amount of cores. That also has the benefit of keeping a GUI off of the server.

Just an idea.

---

### Post by Mr.Carramba on 2009-02-06
> **cariboo907 said:**
> Before making assumptions about what your server needs, have a look at this [Server Guide]("http:///doc.ubuntu.com/ubuntu/serverguide/C/").

Jim

thank you for tip. Never the less Im not making assumption about what I need. For example running matlab with gui will require kde or gnome. It maybe be enough with core packages, I don't know. this is the reson Im turning for answer to the community :)

---

### Post by Mr.Carramba on 2009-02-06
> **borahshadow said:**
> You could set it up with virtual machines. The host OS (base install) could be the high priority calculations and then you could make a virtual machine with a GUI and only assign it a certain amount of cores. That also has the benefit of keeping a GUI off of the server.

Just an idea.


sounds like a interesting solution. can virtual machine be configured in such way that /home/user/ folder in it is the same that it is on server? and that the user "auto-log-ins" to virtual machine, making it transparent to the user.
what happens then if there are several user wants to use the vm simultaneously?  can number of cores be extended then?

---

