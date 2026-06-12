---
title: "After I have set up a Ubuntu Virtual Machine using VMware, how do I increase the allo"
date: 2022-05-11
forum: Virtualisation
---

### Post by Complete on 2022-05-11
After I have set up a Ubuntu Virtual Machine using VMware, how do I increase the alloted desk size partition?  I have everything on a 2TB external drive.  So I am not going to run out of space.  But during the process of loading all the required software to do Android APP development, I have run out of space.  

I followed the steps from [https://kb.vmware.com/s/article/1004047](https://kb.vmware.com/s/article/1004047)  whick are also described [https://www.wikihow.com/Increase-Disk-Space-in-VMware](https://www.wikihow.com/Increase-Disk-Space-in-VMware)

I increased the disk size on the VMware side and this was condluced with 
[IMG]https://communities.vmware.com/t5/image/serverpage/image-id/95207iF5EF337769165257/is-moderation-mode/true/image-dimensions/2500?v=v2&px=-1[/IMG]

The next step is to use the command line on Ubuntu.  But when I started Ubuntu, I saw this after power-up:

[IMG]https://communities.vmware.com/t5/image/serverpage/image-id/95208iC8675288A8880B0A/is-moderation-mode/true/image-dimensions/2500?v=v2&px=-1[/IMG]

Please advise.

---

### Post by ActionParsnip on 2022-05-11
Is it an MBR disk in the VM? If so then the largest size is 2Tb. You need to use a GPT disk to use larger disks that 2Tb

---

### Post by QIII on 2022-05-11
Moved to Virtualisation as a more appropriate location.

---

