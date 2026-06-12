---
title: "Ubuntu 11.04 shows nothing after 1st shut down"
date: 2011-04-29
forum: Ubuntu Dev Link Forum
---

### Post by BlueJ91 on 2011-04-29
Upgraded to Ubuntu 11.04 frm 10.10...worked fine after the restart...but after i shut it down and started it again after sometime,it just draws blank...nothing on the screen except the wallpaper...no sidebar..no top bar with login,shut down options etc..i can access the home folder using open location through shortcut keys..right click options work as well,n i can change backgrownd,themes etc...please please help

---

### Post by w3rt on 2011-04-30
You should not be using 11.10 if you are a newbie

---

### Post by nomekop on 2011-05-06
the same thing happened to me and i think i have your solution 
(or at least this is what work for me)

boot up in **Ubuntu classic** and go to **system** -** administration** - **synaptic package manager**
remove anything that has to do with **compiz** (or anything that has compiz in the name)

now restart your computer and boot up in** Ubuntu **and press **ctrl alt t** and your terminal should come up type in this line **sudo apt-get install compiz** then press enter after that type in this line **sudo apt-get install unity** press enter then **sudo apt-get upgrade unity**

after its done restart your computer and boot in to **ubuntu** and bam everything is back

---

