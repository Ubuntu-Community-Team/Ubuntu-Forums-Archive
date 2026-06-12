---
title: "Failed package on (K)Ubuntu install."
date: 2006-07-05
forum: Server Platforms
---

### Post by ExMachina on 2006-07-05
It get thought he whole install and then fails on one for the open office packets. 
how do i choose packets / how do i fix this?

runnign as root 

I ## out the crref in the sourcelist and uncommented all the others. 

```

apt-get update
apt-get upgrade
apt-get install xorg-xserver
apt-get install kubuntu-desktop

```

am i doing this right?

---

### Post by briguy on 2006-07-05
What error message(s) are you getting?

---

### Post by ExMachina on 2006-07-06
[QUOTE=briguy]What error message(s) are you getting?[/QUOTE]

its :confused: #-o 
```


Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice,org/openoffice.org-calc_2.0.2-2ubuntu12_
i368.deb
MD5Sum mismatch
E: unable to fetch some archves, maybe run apt-get update ( which i did before i installed this ) or try --fix-missing


```


<.<

---

### Post by Alpha_Cluster on 2006-07-06
MD5Sum mismatch

im pritty sure that means its just a corrupted download i would try again and do a update just to be safe.

---

### Post by ExMachina on 2006-07-06
[QUOTE=Alpha_Cluster]MD5Sum mismatch

im pritty sure that means its just a corrupted download i would try again and do a update just to be safe.[/QUOTE]


I just gave up i tried it 4 times. and just dled Xubuntu. it suppose to running leaner.

---

