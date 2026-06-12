---
title: "how the fudge do you add keys for fedora rpmfusion non-free repo?"
date: 2009-05-17
forum: The Cafe
---

### Post by nolliecrooked on 2009-05-17
its driving me nutsssssssssssss

---

### Post by SunnyRabbiera on 2009-05-17
Uhh if you are using Ubuntu rpmfusion wont work anyhow, Ubuntu uses .deb

---

### Post by nolliecrooked on 2009-05-17
> **SunnyRabbiera said:**
> Uhh if you are using Ubuntu rpmfusion wont work anyhow, Ubuntu uses .deb

lmfao, Im not that ******* dumb bro, Im actually using Fedora xD

---

### Post by SunnyRabbiera on 2009-05-17
> **nolliecrooked said:**
> lmfao, Im not that ******* dumb bro, Im actually using Fedora xD

Ah, there i cannot help you as I dont use Fedora :D
I tried it out a few times but its not my cup of tea.

---

### Post by nolliecrooked on 2009-05-17
> **SunnyRabbiera said:**
> Ah, there i cannot help you as I dont use Fedora :D
I tried it out a few times but its not my cup of tea.

yea, it isnt mine either.....NEXT...

---

### Post by hansdown on 2009-05-17
Hi nolliecrooked.

Copy and paste this in the terminal.

su -c 'rpm -Uvh [http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm](http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm) [http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm](http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm)'

That will set up the free and nonfree repos.

---

### Post by nolliecrooked on 2009-05-17
> **hansdown said:**
> Hi nolliecrooked.

Copy and paste this in the terminal.

su -c 'rpm -Uvh [http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm](http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm) [http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm](http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm)'

That will set up the free and nonfree repos.

I already did that, but now its bitching about keys, and I cant find out how to add them.

---

### Post by gnomeuser on 2009-05-18
[http://rpmfusion.org/Configuration](http://rpmfusion.org/Configuration)

---

