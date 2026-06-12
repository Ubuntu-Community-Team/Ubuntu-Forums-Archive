---
title: "Ububtu Core 22.04"
date: 2023-07-10
forum: Ubuntu, Linux and OS Chat
---

### Post by lammert-nijhof on 2023-07-10
I'm trying the Ubuntu Core desktop, the prototype of the planned immutable snap based Ubuntu Core 2024. I love, what I see! 

So  far I have changed the image format to vdi and it now runs in  Virtualbox on my 22.04 Host (Ryzen 3 2200G; 16GB).  On the host I  installed lxd and seemingly it is needed by Ubuntu Core for the  containers.  I can install the snaps using the new software manager.  With the Workshop App I can install e.g an Ubuntu 20.04 VM or an Ubuntu  22.04 LXC container, but both come up in the terminal. It has an option  to do a cloud install, but I have to investigate it somewhat more.  The  amount of parameters shown during creation is very limited, but there is  a very technical overview of say 30 other parameters, that could be  changed :)

I tried to install VBox Guest Additions, but that  failed. I could mount the CD, but the install had no access to the 2  roots folder needed, even allowing group access did not help yet.

Somewhat more info would be helpful.

---

