---
title: "NFS behaviour with local IO saturation"
date: 2011-05-12
forum: Server Platforms
---

### Post by chrism0dwk on 2011-05-12
Hi All,

I have a problem with an NFS server connected to a small cluster (104 cores spread over 11 execution nodes).  The server exports 6 directories, with things like /home, /scratch, and /software partitions, etc.

I have a user who submits large task arrays to the cluster, with each instance of that task generating large amounts of disk writes.  This maxes out the IO bandwidth to the disk (sdb) in the NFS server containing the /scratch partition.  The result is that all the instances of the nfsd go into the 'D' state while they are waiting for the local IO (confirmed using top).  My output from iostat confirming this issue is:

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00    70.50    0.00    3.50     0.00  1188.50   339.57     0.00    0.00   0.00   0.00
sdb               0.00    82.00    0.00  109.00     0.00  2629.00    24.12     3.70   32.48   9.17 100.00
sdc               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00

Note the line for sdb.  The problem is that this condition appears to *also* hold up client access to directories on the two other disks, and the entire cluster grinds to a halt.  I have tested ethernet bandwidth (4 bonded GE lines), CPU (8 Xeon cores), and memory (8G) and there is plenty of headroom (esp CPU and memory). 

Is this expected behaviour for NFS, and is there anything I can do to alleviate the issue?

Thanks,

Chris

---

### Post by samosamo on 2011-05-12
What exactly is this user doing? It's great that you have CPU/RAM/Network to spare but why don't you make any mention of the types of disks and disk controller? This is most important when troubleshooting 100% IO problems. Have you tried mounting without atime?

---

### Post by chrism0dwk on 2011-05-13
Hi Samosamo,

My users is actually creating 2G core dumps, it turns out, and they are apparently being written to the same file.  Not ideal ;-)

My backend IO is a 2TB RAID10 using 4 7200rpm SAS drives through a Dell PERC6 controller.

No, I've not tried mounting without atime.  I have a feel that, while this may help, it won't cure the situation where saturating the bandwidth on one HDD snarls up the nfsd instances such that the other drives effectively become inaccessible.

Cheers,

Chris

---

### Post by samosamo on 2011-05-13
I don't think they make 7200 SAS drives but I could be wrong.

I have questions:
[LIST=1]
[*]Please post your /etc/exports from the NFS server, and relevant lines in /etc/fstab from the client so we may see the NFS options you are using
[*]Please state the speeds you get when read/writing to the /dev/sdb device locally. Perhaps use "dd" or "mkfile" tools
[*]Are you sure the PERC is functioning correctly? Is the battery attached and charged?
[/LIST]

---

### Post by chrism0dwk on 2011-05-17
Hi,

Answers to your questions:

1) /etc/exports:

/export/homes	192.168.0.0/24(rw,async,no_root_squash,no_subtree_check)
/export/scratch	192.168.0.0/24(rw,async,no_root_squash,no_subtree_check)
/export/storage/aston1 192.168.0.0/24(rw,async,no_root_squash,no_subtree_check)
/export/sge	192.168.1.0/24(rw,async,no_root_squash,no_subtree_check)
/srv/packages-x86_64-linux-gnu 192.168.1.0/24(async,rw,no_subtree_check,no_root_squash)

/etc/fstab:

192.168.0.2:/export/homes	/home	nfs	_netdev,defaults,rsize=8192,wsize=8192,intr	0	0
192.168.0.2:/export/scratch	/scratch	nfs	_netdev,defaults,rsize=8192,wsize=8192,intr	0	0
192.168.1.2:/export/sge	/usr/sge	nfs	_netdev,defaults,rsize=8192,wsize=8192,intr	0	0
192.168.1.2:/srv/packages-x86_64-linux-gnu	/usr/local	nfs	_netdev,defaults,rsize=8192,wsize=8192,intr	0	0
192.168.0.2:/export/storage/aston1 /storage/aston1 nfs _netdev,defaults,rsize=8192,wsize=8192,intr  0       0


2) I'm getting about 600M/s with $ dd if=/dev/zero of=bigFile.bin bs=2M count=1000, bearing in mind I have users writing to the disc at the same time.

3) Yes, I'm sure it's working correctly.

Chris

---

### Post by samosamo on 2011-05-17
Everything looks good to me. Sorry my friend, I hope someone else can chime in.

---

