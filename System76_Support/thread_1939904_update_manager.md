---
title: "update manager"
date: 2012-03-12
forum: System76 Support
---

### Post by dimas869 on 2012-03-12
i am having this messege in the update manager but i dont know where to go to agrda that file so i will really appreciate any help

please see the picture so you understand what i meant

---

### Post by ubuntu27 on 2012-03-13
Did you add an PPA? 

It seems to me that it found an update but it can't update yet since it depends on another package that is not in the repository yet. If this is the case, then just waiting for a few days (or week? Depends on the maintainers of the PPA) will fix the problem.


---------

Just in case, could you post the content of your source.list ?

Just open the [terminal]("http://www.psychocats.net/ubuntu/terminal") and type (or copy&paste)
```

cat /etc/apt/sources.list 
```

---

### Post by isantop on 2012-03-13
Cat-ing sources.list may not include all repositories currently is use, such as those stored in the sources.list.d directory.

Go ahead and click on "Settings" at the bottom of that window. In the windows that opens, click on the "Other Software" tab, then press PrtSc (Print Screen) to take a screenshot. Post that here, and we can have a look.

---

### Post by dimas869 on 2012-03-13
hey guys thank you very much for your suggestions to help me out...yes i have a PPA for Xorg but i did to fix the porblem was delete the file in synaptic and update the system and now the messege from the update manager is gone...so i guess when i update again i got the newest file to be install

---

### Post by jerrrys on 2012-03-13
you should update sources whenever you edit it.

sudo apt-get update

---

### Post by HunkirDowne on 2012-03-17
command line junkie version of viewing multiple sources files:
```
find /etc/apt -depth -type f -name '*.list' -print|xargs cat|grep -v "#\|src"|tr -s '\n'|less
```
(so *that's* why they call it terminal)

---

