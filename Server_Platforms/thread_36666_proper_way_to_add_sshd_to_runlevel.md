---
title: "proper way to add sshd to runlevel"
date: 2005-05-24
forum: Server Platforms
---

### Post by blacksun on 2005-05-24
Hello; i've all the configuration tools like sysv-rc-config etc. But i can't add new services. I just want to run sshd at boot. 
I've read that i must use update-rc.d to add a new service; but first i should have a script in /etc/init.d/....?? confusing 
maybe there is a easier way..

---

### Post by ubuntu_demon on 2005-05-24
[QUOTE=blacksun]Hello; i've all the configuration tools like sysv-rc-config etc. But i can't add new services. I just want to run sshd at boot. 
I've read that i must use update-rc.d to add a new service; but first i should have a script in /etc/init.d/....?? confusing 
maybe there is a easier way..[/QUOTE]
 just install openssh by :

$ apt-get install openssh

It will run sshd at boot automaticaly. If you want to change this then you can use update-rc.d to turn it off

---

