---
title: "Clamfs on ubuntu 8.10 server"
date: 2009-01-30
forum: Server Platforms
---

### Post by dmitrysir on 2009-01-30
Hello.
I try to install clamfs to ubuntu 8.10 server, also install all suggested packages (clamav, ... ). After successful installation I copy clamfs config sammle to /etc/clamfs/config.xml and change only path to directories
 <filesystem root="/clamfs" mountpoint="/share" public="yes" nonempty="yes" />
(all directories is created and have permissions 0777). 
Then I started clamfs with new config (clamd started aumatically).
Mount was susccessfull, i can put any file to /share, but i can not open or copy any file from it (without viruses :) ). Only files with extensions from whitelist i can open. In log file I see:
(clamav.cxx:135) (file:5645) (root:0) /clamfs/Dzintari_1.jpg: Access denied. ERROR
(all permissions is, and I can scan directory /clamfs by clamscan)
What is the problem, or my error?
Thank you very much for help!

---

