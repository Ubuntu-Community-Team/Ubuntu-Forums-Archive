---
title: "Trusty Tahr ESM Support"
date: 2022-12-30
forum: Security
---

### Post by sceann on 2022-12-30
Hello,

I have enabled ESM support on my Trusty Tahr 64 Bit and is working fine . I am just confused that along with ESM repositories which of the Trusty Tahr repositories should be enabled and which ones should I remove?

Any guidance in this regard should be much appreciated.

Thanks

P,S : I have following repositories enabled 

"/etc/apt/sources.list"

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-proposed main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty partner 

###### Ubuntu Extras Repo
deb [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) trusty main 

"/etc/apt/sources.list.d/ubuntu-esm-infra-trusty.list"

deb [https://esm.ubuntu.com/ubuntu/](https://esm.ubuntu.com/ubuntu/) trusty-infra-security main 
# deb-src [https://esm.ubuntu.com/ubuntu/](https://esm.ubuntu.com/ubuntu/) trusty-infra-security main 
deb [https://esm.ubuntu.com/ubuntu/](https://esm.ubuntu.com/ubuntu/) trusty-infra-updates main 
# deb-src [https://esm.ubuntu.com/ubuntu/](https://esm.ubuntu.com/ubuntu/) trusty-infra-updates main

---

