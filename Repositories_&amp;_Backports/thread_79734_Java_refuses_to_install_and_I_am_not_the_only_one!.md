---
title: "Java refuses to install and I am not the only one!"
date: 2005-10-20
forum: Repositories &amp; Backports
---

### Post by short4lif2 on 2005-10-20
Hi, I am trying to install j2re1.4 using synaptic.  When I select it for installation and hit apply, I get an error that says the following:

> j2re1.4:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed

However, when I checked, I discovered that i already have libc6 installed.  So I marked it for reinstallation, and I still got the same error message.  Does anyone know what is going on?  How do i get Java installed?

---

### Post by hillbillyray on 2005-10-20
[QUOTE=short4lif2]Hi, I am trying to install j2re1.4 using synaptic.  When I select it for installation and hit apply, I get an error that says the following:



However, when I checked, I discovered that i already have libc6 installed.  So I marked it for reinstallation, and I still got the same error message.  Does anyone know what is going on?  How do i get Java installed?[/QUOTE]

The repositories are not working correctly. I had to download it and manually install it. I found the packages to install using the built in search engine built into firefox. It has a list if dependancies you can check against in synaptic but you will have to install using dpkg from a command line. I have a 3200 64bit XP and had no problems other then the fact that the backports repositories would not update in synaptic. 

Goodluck; 

Hillbillyray

use 
sudo dpkg -i filename.deb 

after you make sure you have all required libs

---

### Post by short4lif2 on 2005-10-20
how do i get the .deb file? (i am a complete newbie)

---

### Post by jeffreyvergara.NET on 2005-10-21
you can find v1.5 [here]("http://www.java.com/en/download/linux_manual.jsp") the downloads, its not yet .deb but just follow the instruction and you'll be fine

---

### Post by short4lif2 on 2005-10-21
OK I reinstalled ubuntu and it worked.  Hope I do not have to do that agian.

---

