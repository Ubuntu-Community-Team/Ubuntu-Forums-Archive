---
title: "How to create an add on cd?"
date: 2009-07-30
forum: The Cafe
---

### Post by praveesh on 2009-07-30
Many of my friends don't have an internet connection. So I decide to download .deb package files  from internet and create an add on cd so that they could add the cd in the repository and  install softwares from it as we install softwares from an Ubuntu cd. Can anyone please tell me How to create such a cd ? . Where to keep the packages? What all folders are needed in the cd? Where to keep the package names? Thank in advance  .

---

### Post by Raffles10 on 2009-07-30
Is [APTonCD]("http://aptoncd.sourceforge.net/") what you're looking for ?

---

### Post by praveesh on 2009-07-30
> **Raffles10 said:**
> Is [APTonCD]("http://aptoncd.sourceforge.net/") what you're looking for ?

Thanks. Thats enough . But I wish to know the internal structure of the addon cd. What the folders and the files in it .

---

### Post by cariboo on 2009-07-30
If you check your live cd, you will see some add ons like ndiswrapper and build essentials. They are located in /pool/main/b and /pool/main/n. The open source packages are always in /pool/main and the closed source packages are in /pool/restricted, and then place in directories starting with the first letter of the package.

---

### Post by praveesh on 2009-08-01
> **cariboo907 said:**
> If you check your live cd, you will see some add ons like ndiswrapper and build essentials. They are located in /pool/main/b and /pool/main/n. The open source packages are always in /pool/main and the closed source packages are in /pool/restricted, and then place in directories starting with the first letter of the package.

Thanks. But I think there will be some file in which all the names of packages is written . But in KUbuntu , I didn't find any kde .deb files. Where are they.

---

