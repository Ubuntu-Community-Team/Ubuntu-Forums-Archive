---
title: "What is the best choice for virtualization?"
date: 2010-02-11
forum: Virtualisation
---

### Post by TechDragon on 2010-02-11
I am wanting to install a virtual windows that is bootable from the grub menu and will load directly into windows.  What is my best option for this and is there a somewhat recent guide available?

Please and thank you

---

### Post by cariboo on 2010-02-11
You may get a better answer here

---

### Post by bronquel on 2010-02-12
not quite sure what you are asking, as to my knowledge having an OS be launched through grub would not be virtual... i would recommend virtual box for virtualization as it's free and performs wonderfully.  You can also do a wubi install, kinda a mix between virtualization and non virtualization, as it's not in it's own partition, it runs inside windows, but not while windows is running...  that's how i do ubuntu.  hope that helps

---

### Post by SirBismuth on 2010-02-12
You have two choices here:

1.  Dual-boot - which will present you with a choice to load either Ubuntu or Windows in your grub menu, but this is not ***virtualization***.  If you have already installed Ubuntu, with no Windows installation, things could get complicated, if it's even possible.  Search the forums and and ask the experts here, of which I am not one, sorry.

2.  VirtualBox - This is indeed ***virtualization***, with XP/Vista/7 (your choice) running inside your Ubuntu as a Virtual Machine.  But download the PUEL version from the VBox website, as it has USB support, which the OSE version doesn't have.  Not sure if the OSE version has network support, but the PUEL version does have this.

B

---

### Post by Letian on 2010-02-12
I think what you are asking is about dual booting as SirBismuth is referring to above. 
installing windows after already installing any linux distro always messes up the grub..but there are ways to fix it and have your grub having all your installed OS listed.

for virtualization my preference would be the latest virtualbox which is 3.1 i think but  3.0 upwards is good enough. Dont apt-get install it because you will probably get the OSE version that has a few features missing.
Go to the virtualbox site and download the Personal Use and Evaluation License(PUEL) version. very nice. 
sorts out sound and network issues i previously had with it. Plus its lighter on memory unlike vmware.

---

