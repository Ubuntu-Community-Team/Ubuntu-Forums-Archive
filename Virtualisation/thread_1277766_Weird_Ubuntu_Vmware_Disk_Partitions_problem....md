---
title: "Weird Ubuntu Vmware Disk Partitions problem..."
date: 2009-09-28
forum: Virtualisation
---

### Post by ssam1111 on 2009-09-28
I am having a very weird problem... in ubuntu...

I am running ubuntu on vmware workstation...
I extended vmdk file to 40GB which was earlier 20GB. Then I made a partition /dev/sda4 of 20GB on this extra space. 

Now somehow it is not letting me load anything more than 9.77GB. When I open gparted it shows me complete 20GB full. When I check disk information by right-clicking on the disk it shows the size of 20GB and shows 9.77GB/9.77GB Used and free space almost 0.

I am not able to determine where the problem could have been? gparted shows me some 41945719 total sectors allocated to this partition. When I run fsck it shows checked 2622611/ 2622611 blocks... I am not able to find relation between this 2. However this is just some extra information if someone finds helpful.

Please let me know even if you have just slightest of hint what could be wrong? I have been trying to figure this out since a long time...

Any help appreciated
Thanks
Sam

---

