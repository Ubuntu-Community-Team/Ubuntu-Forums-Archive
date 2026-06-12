---
title: "Install Ubuntu desktop on 7.04 server"
date: 2007-05-09
forum: Server Platforms
---

### Post by NumberOne on 2007-05-09
When I try "sudo apt get install ubuntu-desktop" I get an error stating: sudo: apt: command not found.

Why am i getting this and how do I fix it.  I am running Server 7.04 setup as lamp server.

---

### Post by Kalifornia909 on 2007-05-09
the command needs a hyphon. it should be sudo apt**-**get install <package>

---

### Post by gashcr on 2007-05-09
I think it is sudo apt-get ... with the bar, isn't it??

---

### Post by NumberOne on 2007-05-09
Thanks guys,

 that was it.  I copied an example off of another post and must have missed the hyphen.

Thanks again.

---

