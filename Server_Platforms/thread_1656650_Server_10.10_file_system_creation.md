---
title: "Server 10.10 file system creation"
date: 2010-12-31
forum: Server Platforms
---

### Post by Melknix on 2010-12-31
Hi to everybody, what I have to do with an Ubuntu 10.10 server is build a home server. I buy a 2TB HD of WesternDigital. I create the partition as follow:
35 GB /
4 GB swap
2TB /dev/data

The installation create the first 2 partition, but for the 3rd is 24h that is creating filesystem ext4, and is still running... Is it normal or the hd is broken? I can't understand why all this time for this operation... Can anyone help me? 

Thanks.
Melknix

PS: happy new year to everybody...

---

### Post by ian dobson on 2010-12-31
Hi,

Could it be that you bought 4K sector drives? If the partitioning isn't on a 4K boundry then writes to the drive will be really slow.

The last time I formatted my 6Tb array it took about 30minutes to format.

Regards
Ian Dobson

---

### Post by Melknix on 2011-01-03
I don't know this. Have you any suggestion to format my HD with another tool? So I can format only the 
35 GB /
4 GB swap
partition and skip the other alredy format?

---

