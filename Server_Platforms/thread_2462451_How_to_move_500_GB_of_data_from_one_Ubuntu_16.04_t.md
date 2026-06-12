---
title: "How to move 500 GB of data from one Ubuntu 16.04 to another Ubuntu 16.04 efficently?"
date: 2021-05-21
forum: Server Platforms
---

### Post by abcuser on 2021-05-21
Hi,
I have two Ubuntu 16.04 virtual machines running on the same physical vmware server. I need to move data as efficiently as possible between this two computers.

I tried SFTP, scp and rsync and all of them it looks to me bottleneck is encryption. I see CPU 40% on "ssh" process on source computer. I see 30% of network consumption and using vmstat command I see block output on target machine not storing on data for 5 seconds and then saving huge amount of data. Network should not be a problem it is 1 Gbit network and disks are totally new super fast flash disks.

I suspect there is encryption that is the culprit for slow data movement.

What is recommended tool to transfer data between two Ubuntu 16.04 virtual machines that as I have written are run on the same physical vmware machine? Encryption is not important in my case and I would like to avoid it, so searching for a tool and installation/configuration instructions. Any recommendations?

Any idea?
Thanks

---

### Post by LHammonds on 2021-05-21
Can you shutdown the source machine and detach the vmware disks from it and add it to the other VM?

I think setting up an NFS mount would be the fastest xfer method between them but way does it "have to" be fast?  Why not just rsync between both to get the vast majority of all the files.  It will get out of sync while the initial sync is running but then you run a 2nd sync after the 1st finishes which should only need to copy what has changed which should be must faster the 2nd time.  Keep doing this until it is fast enough for you to switch your application to use the new destination and then purge the original location.

LHammonds

---

### Post by scorp123 on 2021-05-21
> **abcuser said:**
> Hi,
I have two Ubuntu 16.04 virtual machines running on the same physical vmware server. I need to move data as efficiently as possible between this two computers.

Why not create a 3rd disk? Attach it to the 1st VM and copy your data onto it. Then detach it and attach this new disk to the 2nd machine and copy from there. When you're done detach + destroy the unneeded disk again.

I used this method once because I needed to copy several x-TB of data between 2 x VMs and using "scp" or "rsync" would have clogged up the network (... it was an old bad design that had lots of other problems too ...)

---

### Post by abcuser on 2021-05-25
Hi,
I created NFS mount following [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-18-04) article and using "cp" command to copy file from one machine to another.

Using top command on both Linux machines now I see around 45% of CPU consumption on target Linux and on source Linux see 37% CPU consumption for "kworker" process and 23% for "cp" process.

Time has not reduced. It looks like encryption using SFTP is not the main problem.
Regards

---

### Post by LHammonds on 2021-05-26
Do you understand what I mean when I am talking about using rsync multiple times?  Or about disconnecting a .vmdk file from one VM and re-attaching to another?

I would never use "cp" to copy large amounts of data.  Did you use nohup to ensure it could continue even if your SSH session got disconnected or use & at the end to send it into the background so you could monitor the copy or send output to a log file so you could review it once done to see if anything failed or got skipped because of a locked file or permission issue?  Do you have a method for ensuring that everything you have at the source matches what is at the target?

LHammonds

---

### Post by TheFu on 2021-05-26
Lots of good advice above.

If using NFS, be certain that the network card is using **virtio** drivers. I see 25Gbps connections with virtio between systems on the same physical host.

But I'd use **rsync** if there wasn't any specific reason to use NFS for other stuff. rsync can restart in the middle of a transfer and can be over and over and over again.  rsync adds data that is in the source to the target. If you want it to mirror the same files, then you'll need to also delete files on the target that do not exist on the source anymore.  There is an option in rsync for that.  rsync also has an option to use no encryption/ssh tunnels.

I would find shutting down and connecting storage files (I don't use storage files anymore) to a single VM just to make faster copies too much hassle. uptime for my VMs is measured in weeks, not hours.

Anyways, some iperf3 stats:
```
$ iperf3 -s
warning: this system does not seem to support IPv6 - trying IPv4
-----------------------------------------------------------
Server listening on 5201
-----------------------------------------------------------
Accepted connection from 172.22.22.3, port 36216
[  5] local 172.22.22.6 port 5201 connected to 172.22.22.3 port 36218
[ ID] Interval           Transfer     Bandwidth
[  5]   0.00-1.00   sec  2.96 GBytes  **25.5 Gbits/sec**                  
[  5]   1.00-2.00   sec  3.03 GBytes  **26.1 Gbits/sec**                  
[  5]   2.00-3.00   sec  3.03 GBytes  26.0 Gbits/sec
...
[  5]   0.00-8.00   sec  26.1 GBytes  **28.0 Gbits/sec**                  receiver

```
Network performance far exceeds storage performance, unless both sides are using x4 NVMe storage, unlikely.

BTW, I'm using KVM/qemu for the hypervisor.  Virtio for storage and networking is trivial. No clue which VMware tool you are using - there were 6 different tools made by VMware last time I counted.

---

