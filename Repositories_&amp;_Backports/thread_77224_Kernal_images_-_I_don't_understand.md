---
title: "Kernal images - I don't understand"
date: 2005-10-16
forum: Repositories &amp; Backports
---

### Post by speedsix on 2005-10-16
Ok in my synaptic I have..

**base**
linux-image-2.6.10-5-amd64-k8
linux-image-amd64-k8 [COLOR="Red"]**<<<what is this??**[/COLOR]

**restricted**
linux-amd64-k8 [COLOR="Red"]**<<<what is this??**[/COLOR]
linux-restricted-modules-amd64-k8

**universe**
linux-image-2.6.10-5-amd64-k8[COLOR="Red"]**<<<no restricted modules, nvidia etc.??**[/COLOR]


I'm confused with the naming conventions :confused:


Thanks

Dom

---

### Post by ecobuntu on 2005-10-16
[QUOTE=speedsix]Ok in my synaptic I have..

**base**
linux-image-2.6.10-5-amd64-k8
linux-image-amd64-k8 [COLOR="Red"]**<<<what is this??**[/COLOR]

**restricted**
linux-amd64-k8 [COLOR="Red"]**<<<what is this??**[/COLOR]
linux-restricted-modules-amd64-k8

**universe**
linux-image-2.6.10-5-amd64-k8[COLOR="Red"]**<<<no restricted modules, nvidia etc.??**[/COLOR]


I'm confused with the naming conventions :confused:


Thanks

Dom[/QUOTE]


Hi-
Install linux-image-2.6.10-5-amd64-k8 and I believe linux-image-amd64-k8 will install as well.  The first one is the kernel and I'm not sure what the latter is.  But if you install the former the latter should come along with the first

---

### Post by UbuWu on 2005-10-16
linux-amd64-k8 is just an empty package that makes sure a kernel is installed, even when the version numbers change.

---

