---
title: "HOW TO: VMware Server 1.0.6 in Ubuntu 8.0.4 Hardy Heron 64-bit Editions"
date: 2008-06-12
forum: Virtualisation
---

### Post by gtdaqua on 2008-06-12
**ADDED: HOW TO: VMware Tools on a Linux VM. See the 2nd post.**

Applies only to 64-bit editions. Installing on a 32-bit edition is pretty straight forward.

**Build your Environment:**
Make sure you have the needed build environment and tools to compile the vmware modules for the kernel.

```

sudo apt-get install linux-headers-`uname -r` build-essential xinetd

```

These are required for 64-bit Servers:

```

sudo apt-get install libxtst6 libxt6 libxrender1
sudo apt-get install ia32-libs libc6-i386

```

**Install VMware Server:**

Untar the VMware Server package:
```

tar -xzf /Path/To/VMware-server-1.0.6-xxx.tar.gz

```

Change into the install directory and run the installer:
```

cd vmware-server-distrib
sudo vmware-install.pl

```

Choose defaults and installation will fail eventually when trying to build the drivers:

As of right now VMware Server 1.0.6  won't compile correctly on Hardy 64-bit without patching the vmmon file.
The patch can be downloaded here: 
```

wget http://uruz.org/files/vmware-any-any-update-116.tgz

```

Untar the patch and resume installation:
```

tar -xvzf vmware-any-any-update116.tgz
cd vmware-any-any-update116
sudo ./runme.pl

```

That will finish the vmware-server installation succesfully. 

**Installing the Management User Interface: **

Create symbolic links first for VMware-mui-1.0.6 to install and work properly:
```

sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

```

Untar the downloaded vmware-mui package and install:
```

tar xzvf Vmware-mui-1.0.6-xxx.tar.gz
sudo ./vmware-install.pl

```

If you receive a "starting httpd.vmware:-ne failed" error at the end of running vmware-config-mui.pl you will need to run the following command.

EXECUTE CAREFULLY!!
```

sudo ln -s -f /bin/bash /bin/sh
sudo vmware-config-mui.pl

```

Autostart VMware Management User Interface:

To enable vmware-mui automatically on each restart without requiring user intervention, add this to your "/etc/rc.local" file 
The line has to be added before "exit 0" line. "exit 0" is always the last command in the file.

```

vmware-mui-config.pl -d

```

The "-d" switch will automatically generate a SSL certificate with a default session time out of 60 minutes.

For 64 bit users there is one additional step in order to allow vmware console (on your desktops - not on the server) to launch:

```

sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9

```

That is all. You've now got all you want run VMware-server on your Hardy 64 bit server.

---

### Post by gtdaqua on 2008-06-18
**HOW TO: Install VMWare Tools on Linux VM under Hardy 64 bit Host running VMWare Server 1.0.6**

VMware tools does not work either on the Linux VM. You have to do this to get your vmxnet modules working under your Linux VMs.

Note: The following is taken from: 
[How to Install VMware Tools on Ubuntu Hardy 8.04 under VMware Fusion]("http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html")

```

sudo apt-get install build-essential libproc-dev libdumbnet-dev xorg-dev libgtk2.0-dev

wget http://mesh.dl.sourceforge.net/sourceforge/open-vm-tools/open-vm-tools-2008.04.14-87182.tar.gz


```

WARNING: Ignore "xorg-dev" and "libgtk2.0-dev" in line 1 incase of a Linux VM server. 

Extract the contents of VMware-tools and the open-vm-tools package.

```

tar xzvf VMware*.gz
tar xzvf open-vm-tools*.gz

```

Now build the open-vm tools:
```

cd open-vm-tools-2008.04.14-87182/
./configure && make
cd modules/linux/

```

In the modules/linux folder we have the vmblock, vmhgfs, vmmemctl, vmsync and vmxnet modules that we need to tar up and place into the official VMware tools tarball:

```

for i in *; do mv ${i} ${i}-only; tar -cf ${i}.tar ${i}-only; done
cd ../../..

mv -f open-vm-tools-2008.04.14-87182/modules/linux/*.tar vmware-tools-distrib/lib/modules/source/

```

Now run the regular VMware tools installer:

```

cd vmware-tools-distrib/
sudo ./vmware-install.pl

```

It will correctly compile and install. Modules will load perfectly into the  kernel. Restart to check if everything is ok.

---

### Post by TotallyC on 2008-09-13
Hi,

SuperFreaknNewbie here.  Have a question...

When I input the following command; sudo apt-get install linux-headers-`uname -r` build-essential xinetd, I receive:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-16-generic is already the newest version.
E: Couldn't find package build-essential

Will you please explain what is going on here?

---

