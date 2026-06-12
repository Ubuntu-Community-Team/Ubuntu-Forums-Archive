---
title: "my ubuntu (macbuntu) installation is stuck at ubuntu splash screen"
date: 2016-04-08
forum: Ubuntu/Debian BASED
---

### Post by Ankit_Kumar on 2016-04-08
Hi all, i recently installed an old flavor of ubuntu (macbuntu) based on natty. 
I wanted to read my windows dynamic partition since i didn't wanted to loose that data. 
I crawled through hunderds of forums and came to a conclusion of installing ldmtool which mounts windows dynamic disks to linux fs. I had installed ldmtool successfully after adding a repository of vivid distro. Since this tool was not present in my existing repository. 
I installed this tool successfully, but after reboot am not able to get to my login screen in gui. My system is stuck at ubuntu splash screen where i see dots loading. 
Although am able to access my account from tty. But am not getting my login screen in gui. 

FYI: i have already performed below troubleshooting
Apt-get update
Apt-get -f install 
Apt-get autoremove 
Dpkg --reconfigure ubuntu-desktop
Dpkg -- reconfigure gdm
Restart gdm 

But still i am stuck to where i began. Looking ahead for any inputs and suggestions. 
PS : posting from my android phone

---

### Post by QIII on 2016-04-08
Moved to Ubuntu/Debian BASED.

macbuntu was/is not an official flavor of Ubuntu.

---

