---
title: "Cannot start the virtual machine (Xen on Ubuntu 8.04 64bit)"
date: 2008-10-18
forum: Virtualisation
---

### Post by louvros10 on 2008-10-18
I 'm trying to start the virtual machine and I get this message:

Using config file "/etc/xen/xen1.example.com.cfg".
Error: Unable to connect to xend: No such file or directory. Is xend running?

I used this tutorial: [http://howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories](http://howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories)

Does anybody knows what is the problem???

---

### Post by louvros10 on 2008-10-23
OK...I install Xen and create a VM. When I try to run this VM, I have the above message. Do I miss something???
Please help!!!:confused:

---

### Post by eternaluxe on 2008-10-23
Are you using a xen kernel?
```

uname -r
```

does the result end in '-xen'?

---

### Post by louvros10 on 2008-10-26
No...
```
2.6.24-19-generic
```
Should I change the /etc/xen-tools/xen-tools.conf???

---

