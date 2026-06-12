---
title: "Convert Current Server to UEC Image"
date: 2010-12-02
forum: Ubuntu Cloud and Juju
---

### Post by flickerfly on 2010-12-02
I have a windows server that I want to push to UEC. It is not currently virtualized. How do I convert it or do I need to build a new image just for this?

---

### Post by kim0 on 2010-12-03
You might wanna try with plain old dd like
[http://rwmj.wordpress.com/2009/10/13/poor-mans-p2v/](http://rwmj.wordpress.com/2009/10/13/poor-mans-p2v/)

Or another option might be to install a fresh Windows VM, then use a Windows tool to backup/restore the original server

Try googling for p2v Windows kvm

---

