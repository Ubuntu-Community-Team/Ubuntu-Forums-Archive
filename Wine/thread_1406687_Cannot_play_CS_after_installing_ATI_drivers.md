---
title: "Cannot play CS after installing ATI drivers"
date: 2010-02-14
forum: Wine
---

### Post by bui89 on 2010-02-14
Hello, I own HP probook 4515s with ATI Radeon 4300 HD (512mb), When I installed Ubuntu 9.10 I firstly Installed Wine and then CS condition zero, and it worked. then i installed ati drivers from hardware drivers, now my game doesn't work, it starts but exits in few seconds. when i unintall ati drivers, CS works again :o

---

### Post by bui89 on 2010-02-14
Anybody???

---

### Post by asdfoo on 2010-03-12
replying to your own posts won't help.

which drivers did you install? 
which Wine version did you try?  If it was only 1.0.1 you should upgrade to 1.1.40

The fglrx drivers are provided by ATI and may work better if you get the latest release supported by your card, but ATI have dropped support for slightly old cards, so the free dri/mesa drivers are a becoming a better choice, but because they are updated so frequently you need to make sure you are using a recent version of them.

---

