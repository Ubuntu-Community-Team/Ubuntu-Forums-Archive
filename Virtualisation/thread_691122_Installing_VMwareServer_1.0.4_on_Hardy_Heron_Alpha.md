---
title: "Installing VMwareServer 1.0.4 on Hardy Heron Alpha4"
date: 2008-02-08
forum: Virtualisation
---

### Post by supidupi on 2008-02-08
This small script/HOWTO installs VMwareServer 1.0.4 on Hardy Heron Alpha4
You can simply copy the following lines of into a file and execute it using:
$> sudo bash <script_name>


sudo apt-get -y install xinetd g++
cd ~/Desktop
wget [http://download3.vmware.com/software/vmserver/VMware-server-1.0.4-56528.tar.gz](http://download3.vmware.com/software/vmserver/VMware-server-1.0.4-56528.tar.gz)
wget [http://rtr.ca/vmware-2.6.24/vmware-any-any-update115a.tgz](http://rtr.ca/vmware-2.6.24/vmware-any-any-update115a.tgz)
tar xzf VMware-server-1.0.4-56528.tar.gz
tar xzf vmware-any-any-update115a.tgz
cd vmware-server-distrib/
sudo ./vmware-install.pl
# Always use the default answer and press enter
# Installation finishes with errors
cd ../vmware-any-any-update115a
sudo ./runme.pl
# Always use the default answer and press enter and use a valid passphrase
# Compilation finishes with warnings
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/

---

### Post by heikos on 2008-02-09
Does not work for AMD64. Starting vmware stopps with:
*vmware: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.*

Any ideas?

---

### Post by supidupi on 2008-02-14
Sorry forgot to mention that it is only for i386!:)

---

### Post by fjgaude on 2008-02-14
Wonder why the script wouldn't work for 64-bit Hardy? Would it work for 64-bit Gutsy?

---

