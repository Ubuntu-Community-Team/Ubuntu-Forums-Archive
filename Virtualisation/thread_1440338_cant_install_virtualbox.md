---
title: "cant install virtualbox"
date: 2010-03-27
forum: Virtualisation
---

### Post by popshark86 on 2010-03-27
hi guys 

i get this message everytime i try to install virtualbox for linux ubuntu, i need it for my zunehd


dpkg: regarding .../virtualbox-3.1_3.1.6_59338_Ubuntu_karmic_i386.deb containing 
virtualbox-3.1:
virtualbox-ose-source conflicts with virtualbox
 virtualbox-3.1 provides virtualbox and is to be installed. 
dpkg: error processing /tmp/virtualbox-3.1_3.1.6-59338_Ubuntu_karmic_i386.deb (-
-install):
 conflicting packages - not installing virtualbox-3.1
Errors were encountered while processing:
 /tmp/virtualbox-3.1_3.1.6-59338_Ubuntu_karmic_i386.deb



any of u guys had the same issues and how did you fix it, thank u

---

### Post by jocko on 2010-03-27
> **popshark86 said:**
> 
virtualbox-ose-source conflicts with virtualbox
There's your problem. Uninstall all virtualbox-ose packages (search for virtualbox in synaptic and mark any installed packages for removal).

---

### Post by paddy.melon on 2010-03-27
Type this:
sudo apt-get remove virtualbox-ose-source

then,
sudo apt-get install virtualbox

both will need root capabilities (will ask you for password). You must have installed the OSE source earlier, be careful what you install!

---

### Post by Tamalin on 2010-03-27
Jocko is right.  Try removing the VirtualBox OSE packages.

```
sudo apt-get remove virtualbox-ose-source
```

or, if you still get errors involving OSE, and are sure you don't want anything to do with it, try entering Synaptic Package Manager,
searching for 'virtualbox-ose', and remove all related packages.

---

### Post by the yawner on 2010-03-27
I'd also want to add that the chaps at Virtualbox provide a repo.
```

deb http://download.virtualbox.org/virtualbox/debian karmic non-free

```

---

### Post by popshark86 on 2010-03-28
thanks alot 

it work

thank u again:guitar:

ps. virtual box ose came install when i installed ubuntu

---

### Post by popshark86 on 2010-03-28
i install vista in virtualbox

but i doesn't recognize my zunehd or storage drive?

---

