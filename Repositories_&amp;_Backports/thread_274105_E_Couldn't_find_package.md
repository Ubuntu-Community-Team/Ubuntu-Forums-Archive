---
title: "E: Couldn't find package"
date: 2006-10-09
forum: Repositories &amp; Backports
---

### Post by J0ris on 2006-10-09
hi,

I'm currently trying to set up a myth box using Ubuntu. I have installed Dapper Server and then tried installing the am64-k8 kernel so I ```
sudo apt-get install linux-image-am64-k8
``` which resulted in the message "Couldn't find package". My sources.list seems to be ok though. 
Does anybody have any idea how I get this to work?!

---

### Post by meng on 2006-10-09
Try installing:
linux-image-amd64-k8

Note that it needs to be amd64, not am64

---

