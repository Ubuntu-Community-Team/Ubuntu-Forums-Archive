---
title: "Disk Performance with KVM: IDE vs. VIRTIO"
date: 2009-09-09
forum: Virtualisation
---

### Post by hiasl on 2009-09-09
Hi,

we just bought a new server: 2 Quadcore XEON, 6G RAM, 1T Soft-RAID1 HD on SATA, which I set up with Ubuntu 9.04 and KVM.

To find out the perfect setup for the KVM guests, I did some HD benchmarking with bonnie++. For that purpose I set up a minimum Ubuntu 9.04 guest with 2 additional LVM VGs as virtual drives: 1 IDE (sda), 1 VIRTIO (vda). The guest has 1 VCPU and only 100MB RAM.

Inside the guest I created an ext3 partition in each of the two additonal drives and mount them into 2 dirs: ~/ide and ~/virtio.

Now I run the bonnie++ drive test on the 2 dirs with 500MB files (so that it's much larger then the available RAM). Below are the results:

============ IDE ============ 
Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
virtiotest     500M 28462  66 29208   7 34808   9 56499  85 362458  59  3791  13
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
virtiotest,500M,28462,66,29208,7,34808,9,56499,85,362458,59,3790.7,13,16,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++



============ VIRTIO ============ 
Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
virtiotest     500M 27075  63 27448   7 50246  11 62734  79 243664  34  3124  57
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
virtiotest,500M,27075,63,27448,7,50246,11,62734,79,243664,34,3123.7,57,16,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++

============ HOST SYSTEM ============ 
Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
eve          11760M 65971  91 86969  24 42273   7 38865  71 91063   8 451.1   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
eve,11760M,65971,91,86969,24,42273,7,38865,71,91063,8,451.1,0,16,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++

There are 2 things I dislike / don't understand:
- the performance on the disk via IDE emulation is not much different from the VIRTIO drivers. documentation says it should be a lot different
- the performance on both drives is approximatly only 1/3 to 1/2 of the performance on the HOST System. according the the docs, it should be almost the same VIRTIO and the HOST System

Can anybody please tell about his experiences with VIRTIO / KVM and/or comment my results.

Thanks,
Matthias

---

### Post by CrustyRatFink on 2009-09-09
I'm interested in this topic as well.  Might I ask what the guest kernel is?  Specifically, is it linux-xx-virtual?

I saw reports of 3X increases in IO based on virtio, but I haven't experienced that on my amd64 host and 32-bit jaunty guest.

---

### Post by hiasl on 2009-09-10
it's the normal kernel that comes with ubuntu 9.04 server, when it's installed via vmbuilder. I don't think it's something special for virtualization (like with xen):
that's the exact version: 2.6.28-15-server

Matthias

---

### Post by samokk on 2009-10-28
Same problem here, using Ubuntu karmic (9.10) host with karmic guests.

I enabled disk virtIO in KVM/virt (and added the virtio_blk + virtio_pci to the init ram disks), and the performance is not that much different from IDE, according to stupid unscientific dd tests, as well as bonnie++ benchmarks...

dumpxml reports :
<disk type='file' device='disk'>
      <source file='/srv/ubuntu-kvm/disk0.qcow2'/>
      <target dev='vda' bus='virtio'/>
    </disk>

Any pointer or help is welcome,

thanks,
sami dalouche

---

### Post by mkutsevol on 2009-10-29
If you want perfomance - dont use file-based images. Use block-based devices.
And I usually don't mix virtio and ide, I use ide for install OS only purposes.
inside a VM do lspci - and look if your drivers are ok. If you use 9.04 then drivers are ok even if you use a standart server kernel.

PS. Nice sever :)

---

