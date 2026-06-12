---
title: "No KSM for KVM kernal module in Karmic install"
date: 2010-01-05
forum: Virtualisation
---

### Post by thelamer on 2010-01-05
I just did a fresh minimal install of karmic and installed ubuntu-virt-server. I have machines running on the node libvirtd is up and everything is working, but things seemed a little bit slower than my Centos install. 

After some research I found that the KSM kernal module is not enabled, does anyone know how I can build this in? It was supposed to be enabled since 9.04. 

IE

grep KSM /boot/config-2.6.31-16-generic

returns nothing. 

Look forward to your reply.

[http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs/whatsnew#9.04](http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs/whatsnew#9.04)

"KSM is a new technology within KVM which allows for memory aggregation. Identical memory blocks accross virtual machine are detected and aggregated allowing for a much higher density of guests on a given host when running similar virtual machines." 

Was this dropped in Karmic?

---

### Post by geekshlby on 2010-01-06
If i am not mistaken, the ksm patch was accepted into kernel 2.6.32.

Lucid has ksm enabled.

---

### Post by falstaff on 2010-01-07
Hello,

Yeah, KSM is a 2.6.32 feature. I tried the Mainline builds on Karmic too, but they don't provide KSM as well:
```

$ grep KSM /boot/config-2.6.32-020632-generic 
# CONFIG_KSM is not set

```
As far as I know there is a user space daemon needed as well, so just compile that module would not be enough :(. We have to wait for Lucid...

Bye
falstaff

---

### Post by thelamer on 2010-01-07
Hmm strange why would they have it in the Jaunty release notes for whats new? 

I appreciate the info people, looking forward to lucid. 

Looks like another centos server on our racks :(

---

