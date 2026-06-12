---
title: "multiple vm images on single LUN"
date: 2014-09-11
forum: Virtualisation
---

### Post by scojopa on 2014-09-11
Newbie (linux and kvm)

been reading up on kvm, qemu, libvirt, virsh. I have successfully set up my first ubuntu server (going headless to learn the hard way). I have configured SSH, and setup an iscsi SAN. 

I tried creating my first storage pool. The lun was 100GB and I wanted to fit a few vm's on there. but when I create a vm it allocated the entire scsi target (100GB). 

How can I control this? 

Also - just ran into qcow2 information - should this be the format of my lun when I create the iscsi? Is that even how it works?

Thanks and apologies for ignorance. 

SJ

---

