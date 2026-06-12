---
title: "ubuntu_base and security updates"
date: 2005-01-20
forum: Server Platforms
---

### Post by MadsDK on 2005-01-20
My company is considering switching to Ubuntu on our servers and I thus have some questions about the security updates of a Ubuntu system:

My primary question is whether it is a problem (security-wise) that we remove the ubuntu_base metapackage? There are a lot of packages in the base system that we do not want on our servers (ppp, wireless etc.) and to remove them we also have to remove the ubuntu_base package since it depends on all packages in the base system.

Best regards, 
Mads Kristensen

---

### Post by jdong on 2005-01-20
no, a metapackage really is nothing but a set of dependencies. i.e. you can do apt-get install kde, and it pulls all the dependencies from KDE's metapackage. Or, you can do apt-get install kdelibs4 kdebase kdenetwork kdeartwork (you get the point)


You can feel free to remove whatever from your base system -- it may even be beneficial to your security.

---

### Post by MadsDK on 2005-01-20
Thanks for the quick reply. 

I did not think that it would be a problem... just wanted to be on the safe side.

I have a habit of removing everything I don't need from my linux systems just because it annoys me that its there when I'm not using it :-)

 - Mads

---

