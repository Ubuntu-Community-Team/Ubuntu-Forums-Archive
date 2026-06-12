---
title: "vmware-install.pl file not running"
date: 2008-11-29
forum: Virtualisation
---

### Post by lamagy on 2008-11-29
hi all....

i need your help installing vmware workstation.

i already installed it on another pc but the link where it gave the clear instructions has changed.

i've tried all the commands sudo ./vmware-install.pl and nothing happens, i try some chmod command and same thing.

i can run things so its not a security or access issue...

all the links say to try the sudo ./vmware-install.pl command but this doesn't work...could someone pls explain why?????

thanks,

glenn.

---

### Post by bodhi.zazen on 2008-11-29
1. Do you need to cd into the directory with vmwar-install.pl ?

2. Where is the file located ? If it is not in home, or if home is on a separate partition, is the noexec set on the partition in /etc/fstab ?

---

### Post by lamagy on 2008-11-30
the file is in the desktop

under home/username/desktop/vmware-distrib

so i cd into vmware-distrib and then action the commands.

the same location that its on my other machine.

i managed to install it on the other machine but when i tried to run it again i get the same result as on the new machine so its just a matter of what i need to type in...

i had the instructions but lost them but i remember chmod command i think....

plsssss help or ima throw ubuntu out the window because this is 2008 and we shouldn't be going through this heartache when installing something, windows is not a perfect o/s but at least theres only one way to install things not 100.

---

### Post by bodhi.zazen on 2008-12-01
If you need a walk through, check the mega thread , the instructions for Server should work for Workstation.

You could also check the VMWare site as Workstation is a "Third party" application.

---

### Post by lamagy on 2008-12-01
i checked that...they all say the same command sudo ./vmware-install.pl

why is not happening, i know its a quick command just don't know what it is...

---

### Post by toddrom on 2011-09-05
This is an older thread but I will post here as I stumbled upon it while looking for the same answer trying to install it for vmware player. My vm was originally created with vmware server.

In order to be able to install the vmtools (to be able to run vmwar-install.pl) you need first to login as root.
To enable the root account in ubuntu:
sudo passwd root   and choose a password.

Once you are logged on as root you can open a terminal and run the installer:

sudo ./ (and drag the file here)

---

