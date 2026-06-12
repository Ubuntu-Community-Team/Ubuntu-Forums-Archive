---
title: "VMware"
date: 2008-09-09
forum: Virtualisation
---

### Post by stonecoldjha on 2008-09-09
i am a complete newbie to linux, using ubuntu 8.04.i want to install VMware and than windows xp on it.how do i do it?i do not understand any technical jargon.thanks in advance.

---

### Post by mevets on 2008-09-09
A guide to install vmware I usually follow is this one: [http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html)

If you want to try other vm software that would probably be easier to install try [virtualbox]("apt://virtualbox").

Another one I tend to use is qemu. To install it run:
```

sudo apt-get install qemu-launcher qemu

```

---

### Post by astabeno on 2008-09-09
To install VMWare Server on Ubuntu try this link [here]("http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/")

For desktop virtualization on Ubuntu I recommend using VirtualBox instead of VMWare.  It is another product that does the same thing.  To install VirtualBox type this at the command line.

```
sudo apt-get install virtualbox
```

Then go to System -> Administration -> Users and Groups, unlock the utility with your admin password click "Manage Groups."  Find the Vbox group and add your user to that group.  You can then create Virtuals with VirtualBox.

---

### Post by stonecoldjha on 2008-09-09
what do i do after installing virtualbox?imean i want to install windows xp on it.

---

