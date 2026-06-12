---
title: "Thoughts on XEN failover iSCSI or DRDB?"
date: 2009-11-04
forum: Virtualisation
---

### Post by kameleon25 on 2009-11-04
I currently have an Ubuntu 8.04.3LTS machine installed with XEN and LVM. It is running fine, but I want to add another machine to do live migration and the such for failover. I have done some research and am looking for some input from fellow ubuntu/xen users.

I am debating on if I should do a dedicated iSCSI server to store all my data on or if I should just do DRDB between the 2 virtual servers. 

DRDB
Pro's:
only uses 2 machines (power savings)
seems to work well from research done

Con's:
"wastes" 50% of disk space. Say I have 2 TB per server, only 2TB is useable vs 4TB actual disk space

iSCSI
Pro's:
Can setup in a RAID5 array and only lose 1 disk (say there is 4 1TB drives, only lose 1TB leaving 3TB useable)

Con's:
adds another machine to power. 
If this machine goes down I would lose all disk space.

Any pointers or thoughts are welcome. If there are any other options out there that I have missed, please let me know. I am leaning toward the DRDB route just so I won't have to setup another machine and have fully redundancy. However I hate to think about the cost of "wasting" 2 drives. ;)

---

