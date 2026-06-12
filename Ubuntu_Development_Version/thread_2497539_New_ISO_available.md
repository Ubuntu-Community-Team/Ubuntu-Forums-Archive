---
title: "New ISO available"
date: 2024-05-09
forum: Ubuntu Development Version
---

### Post by corradoventu on 2024-05-09
Ubuntu 24.10 "Oracular Oriole" - Daily amd64 (20240509.1)
Installed, no problems: [https://iso.qa.ubuntu.com/qatracker/milestones/454/builds/300975/testcases/1761/results](https://iso.qa.ubuntu.com/qatracker/milestones/454/builds/300975/testcases/1761/results)

---

### Post by #&amp;thj^% on 2024-05-09
Thanks corradoventu, No Xubuntu 24.10 I could find so I'll wait till then.
I'm just not a Gnome Fan :)
I could rename sources but that defeats manual partitioning.

---

### Post by corradoventu on 2024-05-09
For Xubuntu check here: [https://launchpad.net/~ubuntu-cdimage/+livefs/ubuntu/oracular/xubuntu](https://launchpad.net/~ubuntu-cdimage/+livefs/ubuntu/oracular/xubuntu)

---

### Post by #&amp;thj^% on 2024-05-09
> **corradoventu said:**
> For Xubuntu check here: [https://launchpad.net/~ubuntu-cdimage/+livefs/ubuntu/oracular/xubuntu](https://launchpad.net/~ubuntu-cdimage/+livefs/ubuntu/oracular/xubuntu)
Thanks again corradoventu, I'll keep checking.
I trust Steve so when it gets the green Light I'm there. (Failed to build)

---

### Post by oldfred on 2024-05-09
From this web page I go to Kubuntu and then daily live, pending. Other versions similar but same file name.
 [https://cdimage.ubuntu.com/](https://cdimage.ubuntu.com/)

I copy noble final to oracular and zsync. only 9% different.

All my ISO are in an ISO data folder.
fred@z170-noble:~$ cd ISO
fred@z170-noble:~/ISO$ cp -a noble-desktop-amd64.iso    oracular-desktop-amd64.iso
fred@z170-noble:~/ISO$ zsync [http://cdimage.ubuntu.com/kubuntu/daily-live/pending/oracular-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/kubuntu/daily-live/pending/oracular-desktop-amd64.iso.zsync)
Read oracular-desktop-amd64.iso. Target 91.0% complete.      
verifying download...checksum matches OK

---

### Post by #&amp;thj^% on 2024-05-10
> **1fallen said:**
> Thanks again corradoventu, I'll keep checking.
I trust Steve so when it gets the green Light I'm there. (Failed to build)


I took the source name change just to investigate anything interesting, and nothing to speak on yet, but Xubuntu 24.10 was now ready so downloading now.
```
PRETTY_NAME="Ubuntu Oracular Oriole (development branch)"
NAME="Ubuntu"
VERSION_ID="24.10"
VERSION="24.10 (Oracular Oriole)"
VERSION_CODENAME=oracular

```
Fingers crossed on the installer, and manual partitioning.

---

### Post by #&amp;thj^% on 2024-05-10
Manual partitioning still broke, but LVM2 with encryption now works.
>  Add '+', Change 'Change', and Delete '-' buttons to create your desired scheme
    The screen updates showing your desired partitions and mount points
I'm using an older install script I might have to look at that, but for now,
For this setup testing I chose lvm/encrypted.

```
sudo dmsetup status
[sudo] password for me: 
dm_crypt-0: 0 493684736 crypt 
ubuntu--vg-ubuntu--lv: 0 493682688 linear 

```
```
 df -hT
Filesystem                        Type      Size  Used Avail Use% Mounted on
tmpfs                             tmpfs     1.4G  2.6M  1.4G   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv ext4      231G   12G  208G   6% /
tmpfs                             tmpfs     6.8G     0  6.8G   0% /dev/shm
tmpfs                             tmpfs     5.0M   16K  5.0M   1% /run/lock
efivarfs                          efivarfs  148K  127K   17K  89% /sys/firmware/efi/efivars
/dev/sdg2                         ext4      2.0G  101M  1.7G   6% /boot
/dev/sdg1                         vfat      1.1G  6.2M  1.1G   1% /boot/efi
tmpfs                             tmpfs     1.4G  128K  1.4G   1% /run/user/1000
```
Still on kernel:
```
Linux me-Legion-5-lvm2 6.8.0-31-generic #31-Ubuntu SMP PREEMPT_DYNAMIC Sat Apr 20 00:40:06 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

```
Some minor bugs appear to be fixed (So far)
And the rumored lack of nVidia support is bogus on this install:
```
nvidia-smi
Fri May 10 13:55:27 2024       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.171.04             Driver Version: 535.171.04   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce RTX 3050 ...    Off | 00000000:01:00.0  On |                  N/A |
| N/A   30C    P5               4W /  60W |     48MiB /  4096MiB |     23%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      2404      G   /usr/lib/xorg/Xorg                           45MiB |
+---------------------------------------------------------------------------------------+

```
So far not going to make it to a production system at the current stage now, and this may change...IJDK

And I may keep snaps around, at least until they **** me off....LOL
EDIT and a swap was created at install:
```
free -hg
               total        used        free      shared  buff/cache   available
Mem:            13Gi       2.0Gi        10Gi        17Mi       1.6Gi        11Gi
Swap:          4.0Gi          0B       4.0Gi

```

EDIT: XFCE4-panel fix some properties and Menu select
After reboot a filesystem check runs every time after unlocking encryption. (More to Come)

And Snaps did not last here...LOL :P

---

### Post by corradoventu on 2024-05-17
Very few news in the recent ISOs, according .manifest files just 4 package changed between May 10 and May 17.

---

