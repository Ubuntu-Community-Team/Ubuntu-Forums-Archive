---
title: "Virtual Box Setup"
date: 2008-04-13
forum: Virtualisation
---

### Post by kursacl on 2008-04-13
l try to setup virtualbox by snaptic but don't complete 
however , this is very good

1. Now you need to update sources, run this command in your terminal:

sudo apt-get update

2. Install VirtualBox OSE:

sudo apt-get install virtualbox-ose virtualbox-ose-source

3. Install VirtualBox OSE kernel module:

sudo apt-get install module-assistant
sudo m-a prepare
sudo m-a a-i virtualbox-ose
sudo modprobe vboxdrv

4. Automatically load the kernel module:

sudo gedit /etc/modules

Then add:

vboxdrv

5. Add your username to “vboxusers” group:

sudo adduser [your username] vboxusers

Thanks

---

