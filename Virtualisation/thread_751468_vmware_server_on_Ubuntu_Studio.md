---
title: "vmware server on Ubuntu Studio"
date: 2008-04-10
forum: Virtualisation
---

### Post by SteinbergerNate on 2008-04-10
Hello, all.
I got vmware server installed ok on my computer today. However, I can't run any machines because I'm in ubuntu studio which has the RT kernel. The vmware kernel modules are for the normal kernel and don't work with the rt kernel.

Any thoughts on how to get it up and running? I really don't want to have to reboot to get into my vmware machines. 

Any ideas?

---

### Post by bradwilliamson on 2008-04-10
I have not tried VMWare on the RT kernel, and I would have some performance concerns if I did. 

Compiling VMWare can be a bit touchy.

HOWEVER, if you would like to try, you should be able to install the kernel headers for your specific kernel with:

sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4-base xinetd xserver-xorg libxt6 libxrender1 libxtst6 libxi6 libdb2 openssl libssl-dev

Note that everything after the `uname -r` is optional, but those packages are what VMWare is going to want to compile, even on a GUI-less machine. 

You will need to download the vmware .tar.gz package from VMWare directly, and register for some keys while you're there.

You will likely need the vmware-any-any kernel patch, [from here]("http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz").

tar -zxvf vmware-server.tar.gz
tar -zxvf vmware-any-any.tar.gz
look into the vmware-any-any directory and follow their instructions to apply the patch
cd into the vmware-server-distrib directory and run 
sudo ./vmware-install.pl
And follow the instructions.

Again, it can be touchy on some systems. I build my VMWare servers on Dapper 6.06.1 server, run the apt-get dist-upgrade shuffle, install VMWare, firewall them and then leave them alone.

For workstations, I've had much easier experiences with VMWare Player, but I create the machines on VMWare server or with [http://www.easyvmx.com/](http://www.easyvmx.com/)

Good luck!
Brad

---

