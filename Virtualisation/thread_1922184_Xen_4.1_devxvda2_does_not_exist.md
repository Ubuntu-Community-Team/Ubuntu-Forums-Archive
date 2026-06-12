---
title: "Xen 4.1: /dev/xvda2 does not exist"
date: 2012-02-08
forum: Virtualisation
---

### Post by sabi0050 on 2012-02-08
Hello everybody

I'm new to Xen, and playing around with it. I managed to set up Xen Hypervisor 4.1 on a Ubuntu 11.10, 
and I also managed to create a DomU with Ubuntu 10.04, using xen-create-image. 
We have other servers with an older version of Xen on Ubuntu 8.04, and I tried to "copy" one of the DomU guests from there onto my 
new Xen. 
I did this by creating logical volumes on the Xen 4.1 machine, rsync them with the logical volumes on the old server, and 
manually creating a config file for the new DomU guest.
I followed the procdure described here:
[http://www.virtuatopia.com/index.php/Building_a_Xen_Virtual_Guest_Filesystem_using_Logical_Volume_Management_%28LVM%29](http://www.virtuatopia.com/index.php/Building_a_Xen_Virtual_Guest_Filesystem_using_Logical_Volume_Management_%28LVM%29)
In the step: " Cloning the Host OS on the Guest root Partition", instead of the Host OS, I cloned the OS from a DomU guest on a different Xen Server.

The config of the DomU is:

kernel      = '/boot/vmlinuz-3.0.0-12-server'
ramdisk     = '/boot/initrd.img-3.0.0-12-server'
vcpus       = '1'
memory      = '8192'
root        = '/dev/xvda2 ro'
disk        = [
                  'phy:/dev/vg0/eco13-swap,xvda1,w',
                  'phy:/dev/vg0/eco13-root,xvda2,w',
                  'phy:/dev/vg0/eco13-var,xvda3,w',
              ]

name        = 'eco13'
vif         = [ 'ip=176.9.113.91' ]
on_poweroff = 'destroy'
on_reboot   = 'restart'
on_crash    = 'restart'

I can xm create eco13.cfg, but xm console eco13 fails with:
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/xvda2 does not exist.  Dropping to a shell!

cat /proc/cmdline gives:
placeholder root=/dev/mapper/vg0-root ro nomodeset

Is this the root device that I have to use instead? 

What confuses me is that in the configuration file of the domU guest that was created with xen-create-image, it also uses 
root        = '/dev/xvda2 ro'
as the root device. 

I googled this issue, but found no solution for me. Thanks for any help, Sabine

---

