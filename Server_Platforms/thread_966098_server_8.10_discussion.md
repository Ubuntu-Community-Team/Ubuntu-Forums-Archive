---
title: "server 8.10 discussion"
date: 2008-11-01
forum: Server Platforms
---

### Post by eppo on 2008-11-01
i have my main server running 8.04 LTS. I'm upgrading my backup server to test out 8.10. i was just wondering if anyone has been playing with 8.10 and any opinions you had on the upgrade. if anyone has any input on the virtualization upgrades to the OS i would like to hear that. i have VMware server running, only because i had problems getting KVM running when i set up the main server, VMware seemed easier.
the backup server is only a P4 1.8, would i be able to run KVM on that anyway even though the processor doesnt support virtualization?

---

### Post by Vegan on 2008-11-01
I use it and it cured some problems for me, so I strongly urge its adoption. I use it on my web-server and it works fine.

---

### Post by eppo on 2008-11-01
what problems did it solve specifically?

---

### Post by Vegan on 2008-11-01
I was trying to make Apache2 run PHP and ASPX files in a mixed platform. I.e. a catch ALL web server. That can speak 23 script languages etc.

My greed got the better of me with 8.04 LTS. So I was a very early adopter of 8.10 and therefor can stand up to help other adopters.

The problem specifically was with the Apache2 prefork and fork conflict. Now everybody is happy.

Unrelated, over at the Microsoft Server forum, people were SOL trying to install server 2008 by remote desktop. I upgraded by console remotely like I do with everything else.

The upgrade prompted for some config files, some needed to be saved. So there is some intervention required.

---

