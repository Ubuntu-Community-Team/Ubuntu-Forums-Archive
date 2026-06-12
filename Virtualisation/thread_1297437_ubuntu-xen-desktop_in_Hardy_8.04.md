---
title: "ubuntu-xen-desktop in Hardy 8.04"
date: 2009-10-21
forum: Virtualisation
---

### Post by LarryJ2 on 2009-10-21
If your attempt to install ubuntu-xen-desktop in Hardy 8.04 fails  
complaining that it needs "xenman" "which is not installable", read the wild dependency tale related below:

1. First synaptic doesn't list xenman! So how am I supposed to install it.  After gnashing my teeth and wringing my hands,  I read [https://answers.launchpad.net/ubuntu/+source/xenman/+question/31759](https://answers.launchpad.net/ubuntu/+source/xenman/+question/31759) 

2. That told me you can get an installable copy of xenman here:
[http://launchpadlibrarian.net/11041870/xenman_0.6-5ubuntu1_all.deb](http://launchpadlibrarian.net/11041870/xenman_0.6-5ubuntu1_all.deb)

3. But installation of xenman fails saying it needs  xen-utils-3.2

4. So  open up synaptic, install xen-utils-3.2, close synaptic.

5. Then you can double click on the launchpad link above and use the GDebi program to install xenman.

6. Then finally back to synaptic  to install "ubuntu-xen-desktop"

7. Then if you reboot,  you ***SHOULD*** be running the modified xen kernal as demonstrated below
lj@lian:~$ uname -r
2.6.24-24-xen

8. I think I finally might be closer to getting xen virtualization running as I now see Dom0 is up and running:
lj@lian:~$ sudo xm list
[sudo] password for lj: 
Name                                        ID   Mem VCPUs      State   Time(s)
Domain-0                                     0  3921     2     r-----     34.7

and you can try this also:
lj@lian:~$ sudo xm uptime
[sudo] password for lj: 
Name                                ID Uptime 
Domain-0                             0  0:42:13



And your /etc/network/interfaces should be (where
eth0 is the bridge and vethx are the taps) like this:
lj@lian:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto peth0
iface peth0 inet dhcp

auto eth0
iface eth0 inet dhcp


auto veth0
iface veth0 inet dhcp

auto veth1
iface veth1 inet dhcp

auto veth2
iface veth2 inet dhcp

auto veth3
iface veth3 inet dhcp

Finally  no use in trying to compile an nVidia driver (by downloading NVIDIA-Linux-x86-180.29-pkg1.run, for example) for the 2.6.24-24-xen kernel.  The nvidia .run package will finally announce you can't compile a package using their source code. Apparently the accelerated 3d version is incompatible with the xen kernel. So sadly, this means no dom0 twinview for us that have nvidia graphics boards.   So in the /etc/X11/xorg.conf,  I now have 
Section "Device"
    Identifier     "Device0"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"
EndSection
That driver shows up in Synaptic as "xserver-xorg-video-nv" 
I haven't tried the vga and the vesa drivers.

Couple more tips: remember you can stop and start the display (quicker than logging in and logging out)  with

sudo /etc/init.d/gdm   stop
sudo /etc/init.d/gdm  start

For fun, try out these xen utilities:
lj@lian:~$ sudo xentop

lj@lian:~$ sudo bash /etc/xen/scripts/network-bridge status

lj@lian:~$ sudo bash /etc/xen/scripts/network-nat  status

Hope this helps someone.  I'm putting xen aside while I give KVM a try.  Perhaps I'll move back to virtualbox which I found easy to install and administer.  XEN certainly is complicated.

---

