---
title: "Installation of Xymon(previously hobbit) in ubuntu"
date: 2011-08-17
forum: Server Platforms
---

### Post by rado3105 on 2011-08-17
Hi, has anybody installed xymon(hobbit) in ubuntu? I cant install it using apt-get install xymon it installs, but writing in webbrowser: localhost/xymon doesnt show nothing, also nothing for localhost/hobbit

---

### Post by MasterGamerJK on 2012-03-20
You can not "apt-get install" xymon. You have to compile it.

REF: [http://www.xymon.com/](http://www.xymon.com/)

---

### Post by raja.genupula on 2012-03-20
[http://sourceforge.net/projects/xymon/files/latest/download](http://sourceforge.net/projects/xymon/files/latest/download)

after downloading that extract with a right click option names extract here . 
open your terminal and cd to folder at where you have extracted 

then do as 

```
./configure
make
sudo make install
```
before going to next process make sure that first process done well . 

all the best ,

---

### Post by ebischoff on 2012-10-23
Uh ??? "apt-get install xymon" and "apt-get install xymon-client" work perfectly on (K)Ubuntu 12.04 and 12.10.

---

