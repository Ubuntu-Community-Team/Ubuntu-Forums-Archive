---
title: "partitioning ssd"
date: 2017-07-21
forum: Server Platforms
---

### Post by jhinson79 on 2017-07-21
Hi, I am trying to setup an Ubuntu Server 16.04 LTS. My server is a Dell PowerEdge R900 it's configuration is 4 x 6 core processors(X7XXX) and 128 GB of Ram, it has 2 240 GB SSD's that I want in a RAID 1 and an 1 TB SATA HDD for any Overflow data. Our R900 server has PERC 6i Bios and I have setup the RAID 1 through it. Now I need to partition the SSD, the guided partition sets my swap as 137 GB? Is this correct that seems extremely excessive considering its a 240 GB SSD. I googled a bit and the documentaion on Ubuntu site says twice the size of the RAM, some people are saying that's from the "old days, when computers had less than 8 GB." or "REDHAT says >64 GB use 4 GB" etc. What is the recommended SWAP size for a server with 128 GB of RAM. After I get a Accurate/Realistic number how do I then fix my SSD partition because it's still setup with 100 GB as OS and 137 GB as SWAP, I tried to undo changes but it doesn't do anything.

---

### Post by Michael_McKenney on 2017-07-21
What are you using Ubuntu for?   That seems like a huge waste of hardware for it.   I used standalone VMware 6 install to partition off my Ubuntu web server for 2 vCPUs, 6 GB.  / is 50 GB, /swap is 12 GB (2x RAM) and /var is 560 GB for my web sites.

---

### Post by oldfred on 2017-07-21
I do not know about servers.

But the old days were swap twice RAM size when RAM was 256MB.
Then swap was to be same as RAM but in MiB/GiB when up to 4GB of RAM only if you wanted to hibernate. 
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

On my desktop with 4GB of RAM, I almost never used swap and had 2GB of swap.

Some database apps or video rendering may need more RAM and then would use swap. But again more RAM is solution, not really swap.

Ubuntu 17.04 has changed to use a swapfile unless you already have a swap partition. So next LTS 18.04 will not have a swap partition.
 Starting from 17.04 Zesty Zapus release, instead of creating swap partitions, swapfiles will be used by default for non-lvm based installations.
no more than 5% of free disk space or 2GiB, whichever is lower.
[http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html](http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html)

---

### Post by jhinson79 on 2017-07-21
> **Michael_McKenney said:**
> What are you using Ubuntu for?   That seems like a huge waste of hardware for it.   I used standalone VMware 6 install to partition off my Ubuntu web server for 2 vCPUs, 6 GB.  / is 50 GB, /swap is 12 GB (2x RAM) and /var is 560 GB for my web sites.

We are using the Server to run our Chemical Processing system. The system is SQL and Java based, the recommended specs were 2 x 6 core processors with 32-64 GB of RAM, 2 x 200+ GB SSD's in RAID 1 and 1 x 1 TB SATA HHD optional for overflow. So I shot for a little bit of Overkill in case we needed it.

---

### Post by jhinson79 on 2017-07-21
> **oldfred said:**
> I do not know about servers.

But the old days were swap twice RAM size when RAM was 256MB.
Then swap was to be same as RAM but in MiB/GiB when up to 4GB of RAM only if you wanted to hibernate. 
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

On my desktop with 4GB of RAM, I almost never used swap and had 2GB of swap.

Some database apps or video rendering may need more RAM and then would use swap. But again more RAM is solution, not really swap.

Ubuntu 17.04 has changed to use a swapfile unless you already have a swap partition. So next LTS 18.04 will not have a swap partition.
 Starting from 17.04 Zesty Zapus release, instead of creating swap partitions, swapfiles will be used by default for non-lvm based installations.
no more than 5% of free disk space or 2GiB, whichever is lower.
[http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html](http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html)

I would love that to make our setup and install easier but however 18.04 is at least months from now and I need this setup before then. If I download the server 17.04 which isn't a LTS how do I upgrade when 18.04 is released without formatting and loosing data?

---

### Post by Michael_McKenney on 2017-07-21
I would see what the specs and licensing for your chemical process software needs.    128GB of RAM is amazing.   Does the program require /swap file space for its processes.  I had seen some engineering programs uses /swap space to move items in and out of RAM.   I would suggest getting a SATA or SAS drive for temp and paging files.   SSD drives can get eaten up by temp and paging/swap IOs.   Most recommend putting them on physical hard drives not SSDs.

---

