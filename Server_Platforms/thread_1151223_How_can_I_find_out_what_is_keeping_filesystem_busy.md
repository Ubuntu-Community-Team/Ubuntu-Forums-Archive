---
title: "How can I find out what is keeping filesystem busy?"
date: 2009-05-06
forum: Server Platforms
---

### Post by plonka2000 on 2009-05-06
Hi all,

I have a random question that has been bothering me for a while.

I have a home-built server (running Ubuntu x64, samba, webmin, vmware server 2.0 and an mdadm raid 5 array.

I have my samba shares on my mdadm array as its own **/raid** mount point and the rest of the system sits as normal under **/**

I also store my VMWare Server 2.0 VM's on my **/raid** filesystem even though all vmware binaries are installed on the main system **/**, and I always shutdown VMs before restarting or shutting down the system.

All works very well.

However, frequently, when I try to shutdown or restart this system, I find the system is unable to unmount the mdadm **/raid** volume.

Its come to the point before where I've forcefully unmounted it after waiting days and when it was next remounted, it was marked as corrupt causing mdadm to reconstruct it... Worrying, and I dont want to do that again.

My main question is, is there a way for me to find out what exactly is stopping me from unmounting my raid volume?
Is there a log that will tell me, or does anyone know if any of the applications I'm using may cause my filesystem to be marked as busy?

Thanks.

---

### Post by CrashTest71 on 2009-05-06
Maybe some process is holding a file open.

The "lsof" command might shed some light on that.  I'd try "lsof |grep raid".

---

### Post by fjgaude on 2009-05-07
Usually you can stop an array with the --stop command of **mdadm**:

```
sudo mdadm --stop /dev/md[nn]
```

That command is likely used in a script somewhere. Locate it.

---

### Post by plonka2000 on 2009-05-08
Thanks very much guys,

Im going to try these and report back.

Apologies for my late reply, I've just moved house and have intermittent internet access.

Thanks a bunch. :)

---

### Post by plonka2000 on 2009-05-08
> **CrashTest71 said:**
> Maybe some process is holding a file open.

The "lsof" command might shed some light on that.  I'd try "lsof |grep raid".

Tried this, I got:

```
root@soundwave:~# lsof |grep raid
md0_raid5 2821   root  cwd       DIR               8,97     4096          2 /
md0_raid5 2821   root  rtd       DIR               8,97     4096          2 /
md0_raid5 2821   root  txt   unknown                                        /proc/2821/exe
```

> **fjgaude said:**
> Usually you can stop an array with the --stop command of **mdadm**:

```
sudo mdadm --stop /dev/md[nn]
```

That command is likely used in a script somewhere. Locate it.

Also tried that and got:

```
root@soundwave:~# sudo mdadm --stop /dev/md0
mdadm: fail to stop array /dev/md0: Device or resource busy
```

Something is making my array busy, and unmountable even though I know nothing is accessing it.
I made sure all my VMs are down as well as that could be the only possible thing I would have thought. :(

Any ideas guys?

---

### Post by fjgaude on 2009-05-09
Okay, try unmounting the array and then stopping it:

```
sudo umount /dev/md0
```

```
sudo mdadm --stop /dev/md0
```

See what happens then.

---

### Post by minsik on 2009-05-10
try install iotop which is a file system monitor like top.

apt-get install iotop and then run it in a console or via ssh console.  O will reduce all items displayed back to what is reading and writing on a file system on your pc. 

I believe it can be put into a batch mode and grep the results to a file but i an such a beginner i dont know how to do that yet.

good luck.

---

