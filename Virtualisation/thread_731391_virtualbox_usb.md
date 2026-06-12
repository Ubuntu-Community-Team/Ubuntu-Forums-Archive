---
title: "virtualbox usb"
date: 2008-03-21
forum: Virtualisation
---

### Post by chazn85 on 2008-03-21
so how do i get the tab that shows the OSE version of USB.  Ive looked at various guides nothing works.

Thanks

---

### Post by 89vision on 2008-03-21
I have tried all the guides and also cant get this tab.  Any help would be appreciated.

---

### Post by Bachstelze on 2008-03-21
Moved to Virtualization.

---

### Post by ruibernardo on 2008-03-21
> **chazn85 said:**
> so how do i get the tab that shows the OSE version of USB.  Ive looked at various guides nothing works.

All the guides you saw where for the closed version of VirtualBox. The OSE edition doesn't support USB.

---

### Post by chazn85 on 2008-03-21
so can i download the closed version or is that not possible?

---

### Post by ruibernardo on 2008-03-21
Yes you can. It's your choice.

First uninstall Virtualbox-ose in Synaptic. Search for all the packages that have "virtualbox" in the name. There is al least one package that is a kernel module). After you removed all the installed packages, go to the Virtualbox website and download it. The installation is a bit harder (no apt-get).

**[VirtualBox PUEL version (a.k.a. closed source edition)]("https://help.ubuntu.com/community/VirtualBox#head-fb6efb41e8620daf82ff89c75ca372bea487897e")**

---

### Post by chazn85 on 2008-03-21
i did originally try to install it via adding adding the address into the repos and that didnt work.  if i choose a debian format it saves as a java applet file (jnlp) which surely cannot be right!?

---

### Post by ruibernardo on 2008-03-21
There is a repository. Add the following in your sources.list file. Do it opening the Gnome menu > Administration > Software Sources or in Synaptic.

```
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free
```Update the repositories and a new package for Virtualbox should appear on your favorite package manager :)

You still have to uninstall all the OSE packages, and unload the  OSE module (reboot to be sure) and then install it as described on the wiki.ubuntu.com link.

---

### Post by ruibernardo on 2008-03-21
> **chazn85 said:**
> i did originally try to install it via adding adding the address into the repos and that didnt work. if i choose a debian format it saves as a java applet file (jnlp) which surely cannot be right!?

Oh, then you have to install it by clicking on the deb file or with "dpkg -i name_of_package.deb".

PS: don't forget to accept the damn license.

---

### Post by chazn85 on 2008-03-21
i cant install a jnlp with dpkg as it has to be a .deb im missing something really simple here i can tell.

I have removed all of the virtualbox-ose with apt-get remove blah blah rebooted etc.

---

