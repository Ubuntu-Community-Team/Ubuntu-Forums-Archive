---
title: "Jaunty: Eucalyptus and Xen"
date: 2009-05-07
forum: Virtualisation
---

### Post by jinzishuai on 2009-05-07
Hi there,

I am so excited to know that 9.04 (Jaunty) has included Eucalyptus support. A few days ago, I gave it a try. Thanks to the documentation at [https://help.ubuntu.com/community/Eucalyptus](https://help.ubuntu.com/community/Eucalyptus), the installation process was quite smooth.

Only at the end, my virtual machiine quickly went from pending to terminated. 

After some research, I realized that Jaunty has no support for Xen. So does it mean KVM is the only choice to work with Eucalyptus on Jaunty without building my own xen kernel?
If this is true, I am curious how the documentation was able to run in the first place.

Thanks a lot.
Shi

---

### Post by bodhi.zazen on 2009-05-07
Jaunty does not support Dom0 , DomU is supported.

You can downgrade to 8.04 or try to compile a Xen kernel.

Alternate platforms exist including VirtualBox, KVM, and VMWare.

---

### Post by dendrobates on 2009-05-08
Does your hardware support KVM?  If it does not KVM will not work.  you can run the following command to see:
```
kvm-ok
```

--Rick

---

### Post by geppetto on 2009-06-26
A detailed and successful howto is

[http://www.infohit.net/blog/post/running-xen-on-ubuntu-intrepid-and-jaunty.html](http://www.infohit.net/blog/post/running-xen-on-ubuntu-intrepid-and-jaunty.html)

---

