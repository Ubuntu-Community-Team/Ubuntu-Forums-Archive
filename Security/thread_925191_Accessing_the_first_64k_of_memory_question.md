---
title: "Accessing the first 64k of memory question"
date: 2008-09-20
forum: Security
---

### Post by rifak on 2008-09-20
Hello,

I am using wine to run a couple of applications. When I tried installing and running, it gave me a message saying that "DOS memory range unavailable." I fixed this by running:

sudo sysctl -w vm.mmap_min_addr=0

and then made this change permanent by changing the /etc/sysctl.conf. I am wondering what kind of security risks this brings about and if it is unadvised to make it permanent, but rather run the line of code everytime before I use the wine programs. thanks for the input.

---

