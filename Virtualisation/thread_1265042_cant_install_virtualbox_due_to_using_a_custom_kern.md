---
title: "cant install virtualbox due to using a custom kernel"
date: 2009-09-12
forum: Virtualisation
---

### Post by Meow27 on 2009-09-12
ive looked at this thread but nothing has worked so far.

[http://ubuntuforums.org/showthread.php?t=853374&highlight=virtualbox&page=2](http://ubuntuforums.org/showthread.php?t=853374&highlight=virtualbox&page=2)


virtualbox wont install its kernel module (3.0.6) and it says that it cant find linux headers

this hasnt happened with the previous versions.....

can someone help me?

im using linux2.6.30-custom

edit. im using jaunty 904

---

### Post by falconindy on 2009-09-13
Did you install custom headers when you compiled your new kernel? I run my own customized kernel (based on 2.6.28-15) and VirtualBox runs without a hitch.

---

### Post by PatrickVogeli on 2009-09-13
You can make a simlink from the headers to /usr/src/linux:

sudo ln -s /usr/src/your-custom-headers /usr/src/linux

Another to try:

sudo rm -rf /lib/modules/your-custom-kernel/build
sudo ln -s /usr/src/your-custom-headers /lib/modules/your-custom-kernel/build

Hope that helps

---

### Post by Meow27 on 2009-09-13
> **PatrickVogeli said:**
> sudo ln -s /usr/src/your-custom-headers /usr/src/linux


did the job for my laptop (2.6.31)
ill do it on my desktop a little later.

but thanks so far! i really appreciate it :3

---

