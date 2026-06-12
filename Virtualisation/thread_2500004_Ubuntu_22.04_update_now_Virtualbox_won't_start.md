---
title: "Ubuntu 22.04 update now Virtualbox won't start"
date: 2024-08-18
forum: Virtualisation
---

### Post by JimLS on 2024-08-18
I did a sudo apt update, sudo apt upgrade and now virtualbox won't start.  Software center was set to automatically install updates so should I have not done the update, upgrade?  Seemed like a safe thing to do but it appears that updated the kernel that software center did not update.  What's the details of that?

Anyway, I did a search and it said my gcc compiler needed to be updated from 11 to 12 so did that and then
sudo /sbin/vboxconfig

Still didn't work although I found a related bug tracker that said it had been fixed.
 it complained about some USB2.0 driver so I installed vitrualbox-ext-pack.  

Still won't start.  What now?

---

### Post by ajgreeny on 2024-08-18
You have not given us any useful information which might help us figure out the VBox problem and we need to know much more detail.

For a start please run command ```
inxi -Fzx
``` and show us the output.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

It will also be useful to know the exact version of VBox installed as there are some incompatibilities between kernel versions and VBox versions so again show the output again using code tags of command ```
apt policy virtualbox
``` again using code tags please.

---

### Post by makitso on 2024-08-19
[https://bugs.launchpad.net/bugs/2077214](https://bugs.launchpad.net/bugs/2077214)

---

