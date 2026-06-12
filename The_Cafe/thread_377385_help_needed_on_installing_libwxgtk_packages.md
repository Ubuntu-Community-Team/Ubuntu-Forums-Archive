---
title: "help needed on installing libwxgtk packages"
date: 2007-03-06
forum: The Cafe
---

### Post by xrin on 2007-03-06
Hi,

I have manually downloaded libwxgtk2.6.0_2.6.3.2.1.5_i386.deb.

question:
where do i place this file in ubuntu???
and
how to i install it???

Help needed. thanks in advance.

---

### Post by aysiu on 2007-03-06
Did you manually download it because you don't have an internet connection on your Ubuntu computer?

Try double-clicking it. More details here:
[http://monkeyblog.org/ubuntu/installing/#deb](http://monkeyblog.org/ubuntu/installing/#deb)

---

### Post by joselin on 2007-03-06
You can install it by typing the following:
```
sudo dpkg -i libwxgtk2.6.0_2.6.3.2.1.5_i386.deb
```

But is better if you take it from the repositories:
```
sudo apt-get install libwxgtk2.6-0
```

---

### Post by takitez on 2008-06-08
do an 

```
apt-cache search libwx
```

to determine the latest version.

---

