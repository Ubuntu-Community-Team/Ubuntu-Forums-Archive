---
title: "apt-get dist-upgrade chooses wrong kernel to upgrade"
date: 2010-12-08
forum: Server Platforms
---

### Post by greenmuh on 2010-12-08
Hello all, 

I have a question about upgrading the kernel and howto do it 
with apt-get dist-upgrade.
The virtual server im testing now had a linux-image-2.6.35-22-virtual kernel.

Now i installed the server kernel like this:

```
# apt-get -y install linux-headers-2.6.35-22-server linux-image-2.6.35-22-server
```

I now have:

```
# uname -r
2.6.35-22-server

```
When i do this:

```
# apt-get dist-upgrade
```

I get this:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-image-2.6.35-23-virtual
```

But i would expect linux-image-2.6.35-23-server to be picked.
How can i fix this to pick the right one with apt-get dist-upgrade?

tnx.

---

### Post by SlugSlug on 2010-12-08
I had a simlar prob moving ubuntu over to ubuntu server 

I installed -server and removed -generic after reboot

you could try removing -virtual  --  if its not in use!/

---

### Post by greenmuh on 2010-12-08
I rather keep the original for fallback, isnt it possible to force the dist-upgrade or something?

---

### Post by SlugSlug on 2010-12-08
well, it's only going to update it..  

try update and see what is default at grub, if virtual is default edit your grub

---

### Post by greenmuh on 2010-12-08
Yes i know, that is what i've been doing but that will mean if i forget it, it will reboot into the wrong kernel which i absolutely do not want. except for fallback off course :D

But thanks for your suggestion i will try to remove the virtual one if i get my 2nd test vps but i still think there might be other sollutions.

---

