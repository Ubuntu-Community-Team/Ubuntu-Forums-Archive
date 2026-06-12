---
title: "Problems configuring vmware on ubuntu 8.04"
date: 2008-10-29
forum: Virtualisation
---

### Post by uroskriznar on 2008-10-29
[I]Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Workstation may crash if you'll continue. Please try to use exactly same
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no] 

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.[/I]

What do I have to do? Could someone please give me a very detailed explanation with all the necessary steps?

What will happen with VMware when I upgrade to Ubuntu 8.10?

---

### Post by colinlr on 2008-10-29
This worked for me
Setup server as normal, I chose lamp and ssh server options
apt-get update
apt-get upgrade
setup network for static
 Restart your network interface:
sudo /etc/init.d/networking restart
1. Prep ~. Install the needed tools. 

apt-get install build-essential linux-headers-`uname -r` xinetd

2. Download vmware server (be sure to obtain a serial number) Place it in a safe directory ( I use ~/src/VMWare) and extract. 

mkdir -p ~/src/VMWare #Download VMWare files here


*


VMWare server : [http://www.vmware.com/download/server/&#8734;](http://www.vmware.com/download/server/&#8734;)
*


VMWare serial number : [http://register.vmware.com/content/registration.html&#8734;](http://register.vmware.com/content/registration.html&#8734;)
* Extract and install VMWare Server. 

cd ~/src/VMWare
tar xzf VMware-server-1.0.6-91891.tar.gz

cd ~/src/VMWare/vmware-server-distrib
sudo ./vmware-install.pl


* Select defaults.
* Enter your serial # during the installation.
* Post-install configuration. Last, before running vmware : 

cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0

5.


In addition, for 64 bit users only, 

apt-get install ia32-libs
ln -s /usr/lib32 /usr/l32
sed -i -e 's:usr/lib/:usr/l32/:g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sed -i -e 's:usr/lib/:usr/l32/:g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9

server is available @ [http://ipaddress:8222&#8734;](http://ipaddress:8222&#8734;)

---

### Post by nithya.chandrakesan on 2008-10-29
Hi,
I configured VMWare in my machine. And i am trying to checkout code from CVS, from a guest OS instance. say redhat, freebsd etc.
In all of these, i get the error, 
cvs [login aborted] Cannot find working directory No such file or directory

Could someone help me find out what the issue is?

Thanks,
Nithya.


> **colinlr said:**
> This worked for me
Setup server as normal, I chose lamp and ssh server options
apt-get update
apt-get upgrade
setup network for static
 Restart your network interface:
sudo /etc/init.d/networking restart
1. Prep ~. Install the needed tools. 

apt-get install build-essential linux-headers-`uname -r` xinetd

2. Download vmware server (be sure to obtain a serial number) Place it in a safe directory ( I use ~/src/VMWare) and extract. 

mkdir -p ~/src/VMWare #Download VMWare files here


*


VMWare server : [http://www.vmware.com/download/server/&#8734;](http://www.vmware.com/download/server/&#8734;)
*


VMWare serial number : [http://register.vmware.com/content/registration.html&#8734;](http://register.vmware.com/content/registration.html&#8734;)
* Extract and install VMWare Server. 

cd ~/src/VMWare
tar xzf VMware-server-1.0.6-91891.tar.gz

cd ~/src/VMWare/vmware-server-distrib
sudo ./vmware-install.pl


* Select defaults.
* Enter your serial # during the installation.
* Post-install configuration. Last, before running vmware : 

cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0

5.


In addition, for 64 bit users only, 

apt-get install ia32-libs
ln -s /usr/lib32 /usr/l32
sed -i -e 's:usr/lib/:usr/l32/:g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sed -i -e 's:usr/lib/:usr/l32/:g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9

server is available @ [http://ipaddress:8222&#8734;](http://ipaddress:8222&#8734;)

---

