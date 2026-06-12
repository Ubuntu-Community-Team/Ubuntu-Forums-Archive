---
title: "Cant Install Xen Guest VM on Ubuntu 12:04"
date: 2013-02-07
forum: Virtualisation
---

### Post by esithole on 2013-02-07
**Hi all,**
 

 **I'm trying to set up a Xen PVM guest on Ubuntu 12:04 and I've followed the Ubuntu guidelines for Xen installations as provided on the link, [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)**
 

 **The internal configuration of the file for the Xen VM  is shown below:**
 ------------------------------------------------------------------------------------------------ 
   
 root@MYPC22:~# vi /etc/xen/Ubuntu.cfg  
 

 name = "Ubuntu-VM1" 
 memory = 256 
  
 disk = ['phy:/dev/Ubuntu-VG/Ubuntu-VM1,xvda,w'] 
   
 vif = [' '] 
  
 #bootloader = "pygrub" 
  
 kernel = "/var/lib/xen/images/ubuntu-netboot/vmlinuz" 
 ramdisk = "/var/lib/xen/images/ubuntu-netboot/initrd.gz" 
  
 

  extra = "debian-installer/exit/always_halt=true -- console = hvc0" 
 -------------------------------------------------------------------------------------------------
 **To start the VM and connect to the console I've executed the command below but nothing happens and the installation can't proceed (See output  response below):**

 

 root@MYPC22:~# sudo xm create /etc/xen/Ubuntu.cfg -c 



 Using config file "/etc/xen/Ubuntu.cfg". 
 Started domain Ubuntu-VM1 (id=1) 
                               root@MYPC22:~#  
 

 --------------------------------------------------------------------------------------------------
 **The physical volumes for the PVM Xen and HVM Windows  are shown as follows: ** 
 

 root@MYPC22:~# pvdisplay  
   --- Physical volume --- 
   PV Name               /dev/sda4 
   VG Name               Windows-VG 
   PV Size               15.23 GiB / not usable 3.00 MiB 
   Allocatable           yes  
   PE Size               4.00 MiB 
   Total PE              3899 
   Free PE               1339 
   Allocated PE          2560 
   PV UUID               WkRcPq-ex5S-QDiK-hx29-4V3s-BDMK-3VG902 
     
   --- Physical volume --- 
   PV Name               /dev/sda3 
   VG Name               Ubuntu-VG 
   PV Size               15.03 GiB / not usable 4.00 MiB 
   Allocatable           yes  
   PE Size               4.00 MiB 
   Total PE              3847 
   Free PE               2823 
   Allocated PE          1024 
    PV UUID               ku2eYL-raCo-TBQX-a7fS-OXqc-8hTy-3QJJWl 
 

 **The logical volumes for the PVM Xen and HVM Windows  are shown as follows: ** 
 

 root@MYPC22:~# lvdisplay  
   --- Logical volume --- 
   LV Name                /dev/Windows-VG/Windows-VM1 
   VG Name                Windows-VG 
   LV UUID                4jN2HZ-VdrC-masf-ezDO-7yjn-dceK-zF0RQc 
   LV Write Access        read/write 
   LV Status              available 
   # open                 0 
   LV Size                10.00 GiB 
   Current LE             2560 
   Segments               1 
   Allocation             inherit 
   Read ahead sectors     auto 
   - currently set to     256 
   Block device           252:0 
     
   --- Logical volume --- 
   LV Name                /dev/Ubuntu-VG/Ubuntu-VM1 
   VG Name                Ubuntu-VG 
   LV UUID                T3DxM7-UMaf-cwtN-r3Bv-js4J-UUng-ZcHd8Y 
   LV Write Access        read/write 
   LV Status              available 
   # open                 0 
   LV Size                4.00 GiB 
   Current LE             1024 
   Segments               1 
   Allocation             inherit 
   Read ahead sectors     auto 
   - currently set to     256 
   Block device           252:1 
     
 --------------------------------------------------------------------------------------------------
 **The only active domain when query the existing Vms is the Domain-0 as shown below. ** 
 

 root@MYPC22:~# sudo xm list 
 Name                                        ID   Mem VCPUs      State   Time(s) 
 Domain-0                                     0  7128     8     r-----  16554.4 
 root@MYPC22:~# 



  
 **Any ideas as to what's preventing the console from coming up and enabling the installation?**

 **Thanks in advance for your help.**

---

### Post by laars80 on 2013-06-20
I have exactly the same problem, anyone who can help? (In my case I manage to start a full virtualized guest, although without network access...)

---

### Post by heiko_s on 2013-06-20
I'm not an expert on PV guests. You need to use special Linux PV guest ISOs, which means that a regular Linux ISO won't do (unless you install as HVM guest). The config file doesn't specify any installation drive (ISO). See also link below (which is for HVM guests, but nevertheless you need to install a Linux PV system so there should be an installation ISO which needs to be mounted).

About network access of HVM guest, check your network bridge configuration. See [here]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013#p628768") for some hints.

---

