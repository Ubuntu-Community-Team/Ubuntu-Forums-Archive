---
title: "installing windows xp 64bit on Virtual Box !"
date: 2008-10-25
forum: Virtualisation
---

### Post by medya on 2008-10-25
I installed virtualbox on my ubuntu hardy - by synaptic package manager.
and it works great with windows xp 32 bit
but when I tried to install XP 64bit , it doesnt support 64bit xp .

what should I do ?

is there any better virtual machine that supports 64bit stuff?

---

### Post by WRDN on 2008-10-25
VirtualBox does not support 64 bit Operating Systems. Instead, I recommend VMWare Server 2.0 (which I installed Vista 64 bit on).

---

### Post by Marshal0505 on 2008-10-25
I'm running 64 bit guests in Virtualbox.
You need to have 2.0.X and a 64bit host

---

### Post by Pom2122 on 2008-10-25
Agreed, virtualbox after 2.x supports 64 bit guests IF you have:
1) a 64 bit processor.
2) a 64 bit host OS.

---

### Post by medya on 2008-10-25
how I can install virtualbox 2.x ? it is not in synaptic package manager.

---

### Post by Marshal0505 on 2008-10-26
> **medya said:**
> how I can install virtualbox 2.x ? it is not in synaptic package manager.

Follow these instructions:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by medya on 2008-10-30
> **Marshal0505 said:**
> Follow these instructions:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

I had tried that but it told me that I am not allowed to download .
it seems they have blocked Iran's IPs .

I downloaded it with a proxy .

---

### Post by Marshal0505 on 2008-10-30
> **medya said:**
> I had tried that but it told me that I am not allowed to download .
it seems they have blocked Iran's IPs .

I downloaded it with a proxy .

Ok, let us know how it goes :)

---

### Post by medya on 2008-10-30
I installed "virtualbox-2.0_2.0.4-38406_Ubuntu_hardy_amd64" 
successfully and again when I  put the windows xp 64 bit in the cd-rom  it says :

> attempting to load an x64 operation system however this cpu is 32...blah blah

---

### Post by Marshal0505 on 2008-10-30
Make sure you install windows xp with extended features enabled.
You can find those in 'General Settings' ---> 'Advanced'.
Make sure you tick each one of them so they're all enabled.
I'm certain one or more of those disabled will also disable 64 bit support.

---

### Post by medya on 2008-10-31
yay it works now , thanks Marshal

---

### Post by Marshal0505 on 2008-10-31
np :)

---

