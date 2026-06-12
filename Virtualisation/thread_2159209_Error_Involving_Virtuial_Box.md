---
title: "Error Involving Virtuial Box"
date: 2013-07-02
forum: Virtualisation
---

### Post by john halve on 2013-07-02
Wehn i installed virtuialbox 4.2 and went to the software canter for final download it downloaded.Then i went to upgrade my system and this allso happens wehn i try to install  things i get a error saying


sudo apt-get install perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: The package virtualbox-4.2 needs to be reinstalled, but I can't find an archive for it.**

then wehn i try to go to the software center to reinstall virtuialbox the  software center pops up but doesent ever load 

i am a new linux user and am dual booting with windows 7



Thank you

---

### Post by dargaud on 2013-07-02
Don't use the repository version as it is way outdated.
> wget [http://download.virtualbox.org/virtualbox/4.2.14/virtualbox-4.2_4.2.14-86644~Ubuntu~natty_amd64.deb](http://download.virtualbox.org/virtualbox/4.2.14/virtualbox-4.2_4.2.14-86644~Ubuntu~natty_amd64.deb) && sudo dpkg -i virtualbox-4.2_4.2.14-86644~Ubuntu~natty_amd64.deb

---

