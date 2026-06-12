---
title: "I seem to have a System76 kernel on a non-System76 workstation"
date: 2022-01-14
forum: System76 Support
---

### Post by watchpocket on 2022-01-14
As the title suggests, I've discovered that the Linux kernel I'm using on my *(**non**-System76)* desktop workstation is a System76-built kernel:

$ *uname -sr*[I]
Linux **5.4.0-7642**-generic[/I]

The current version of the *(non-System76)* 5.4.0 kernel is ***5.4.0-92-generic***. 
(Though it looks like it will be upgrading to something newer soon, as kernel security updates are  apparently being rolled out right now.)

Kernel version *5.4.0-7642* doesn't exist anywhere in the Ubuntu kernels builds.  

The closest I can find about kernel *5.4.0-7642* is this: [https://launchpad.net/~system76/+arc...build/19851655]("https://launchpad.net/~system76/+archive/ubuntu/proposed/+build/19851655")
Which is a System76-built kernel.  (And also very old by the looks of it.)

I did recently have a System76 "Wild Dog" desktop computer dating from 2010.  I pulled this SSD from that computer not long ago and put it into a new computer.  This must be where this "leftover" kernel is from (even though I re-formatted the drive and fresh-installed 20.04 Linux-MATE.

[I][B]My questions: 
[/B][/I]
Does it make sense to keep the *5.4.0-7642* System76 kernel on a non-System76 machine?
 Could there be hazards to doing so?  
What kernel would it make sense for me to move to, or upgrade to?  

I'm running the Ubuntu-MATE 20.04.3 LTS OS.

---

### Post by &amp;KyT$0P# on 2022-01-14
> **watchpocket said:**
> my *(**non**-System76)* desktop workstation

What is your current desktop workstation?

> Does it make sense to keep the 5.4.0-7642 System76 kernel on a non-System76 machine?

No.  That kernel is old and maybe now insecure.  Better to use a current kernel version.

> Could there be hazards to doing so?

Security wise, I don't know.  Stability wise, if you don't notice any issue there probably isn't one.

I use System76 kernels in a VirtualBox VM and it works fine.

> What kernel would it make sense for me to move to, or upgrade to?

You have 3 options:

1) "Downgrade" to the stock 5.4.x kernel from the Ubuntu repositories.

2) Upgrade to the standard Ubuntu HWE kernel (currently 5.13.x I think).

3) Upgrade to the latest System76 kernel (currently 5.15.11).

If it were me, and if the 5.4.x kernels don't have issues on your current hardware, I'd probably go with (1) to maximize stability.  Some programs need to build kernel modules (for example VirtualBox, proprietary Nvidia drivers, v4l2loopback) and so can potentially break with newer kernel series.  If you don't have any programs like that, any of the kernel options would probably be fine.

---

### Post by guiverc on 2022-01-14
I'd check your sources as you may have added a Pop OS source into your system & thus introduced other non-Ubuntu packages beyond what you initially wanted.

I'd like see if you have a source for it with `apt-cache policy` and then `sudo apt update` and read the output looking for anything unusual added by user(s) with `sudo` rights (*or if it's only you, maybe it'll trigger your memory*). I may search *apt* logs looking for when it was installed (*it may also show what else was installed*), may consider using `ubuntu-security-status --thirdparty` to explore what else maybe non-Ubuntu etc... 

(FYI:  I consider Ubuntu-MATE as Ubuntu; thus I'd not expect to find any System76 packages on my Ubuntu*/Xubuntu/Lubuntu/Ubuntu-MATE *system [my system is bloated with multiple DEs installed])

---

### Post by watchpocket on 2022-01-15
> **halogen2 said:**
> What is your current desktop workstation?

If you need any info about it beyond what's in my sig, let me know. 
 I built it myself a few months ago. (I had a long wait to be able to buy a graphics card, btw, and finally got one via NewEgg auction.)

>  . . . That kernel is old and maybe now insecure.  Better to use a current kernel version.

I'll either go with the stock 5.4 current version*** (5.4.0-92)**, *or*** 5.13 HWE***. 
(I was using 5.11 on another drive but USB audio didn't work in 5.11.)

I'm guessing 5.13 should be stable and beyond an experimental period.

> . . . Some programs need to build kernel modules (for example . . ***.proprietary Nvidia drivers*** [ my emphasis -watchpocket ]. . . ) and so can potentially break with newer kernel series.  If you don't have any programs like that, any of the kernel options would probably be fine.

I do have proprietary Nvidia drivers, and I recently tried to update a batch of nvidia libraries, etc.  
I allowed these updates to come in on my 5.4.0-7642 20.04 drive, and also on another drive running the 5.11 kernel with the same 20.04 UbuntuMATE OS.

After those updates came in, I couldn't get past the login screen on either OS.  (I used Timeshift to revert back to a previous state.) 

So I think I may be leaning toward using the ***5.4.0-92*** kernel for stability.
I'm guessing I can do that with this command:

*sudo apt install --install-recommends linux-generic*

(I am also still a bit curious about how 5.13 might work, and if it's stable enough. I may try 5.4 on one drive and 5.13 on the other.)

---

### Post by &amp;KyT$0P# on 2022-01-15
> **watchpocket said:**
> I'm guessing I can do that with this command:

*sudo apt install --install-recommends linux-generic*

It's unlikely to be that simple.  Please post the outputs from the following commands -
```
apt-cache policy
apt-cache policy linux-generic linux-image-generic linux-system76
```

---

### Post by watchpocket on 2022-01-15
> **guiverc said:**
> I'd check your sources as you may have added a Pop OS source into your system & thus introduced other non-Ubuntu packages beyond what you initially wanted.

I don't think you'll find a Pop OS source or anything else System76-related in my sources.  I try to keep a close eye on them.
(At the moment I'm using a fairly long list of PPAs -- 27 of them.)

Nevertheless, you can look at the output of  `*apt-cache policy*`;  `*sudo apt update*` and `*ubuntu-security-status --thirdparty*` [here]("https://paste.ubuntu.com/p/V2NQTnzRgC/").


> and read the output looking for anything unusual added by user(s) with `sudo` rights

I'm the only user.

> I may search *apt* logs looking for when it was installed (*it may also show what else was installed*) 

Interesting: */var/log/apt/term.log.5* indeed shows that the System76 *5.4.0-7642-generic* kernel was installed in October 2020.  
It may have presented itself as a routine kernel upgrade, except I didn't know it was a specialized System76 kernel.

---

### Post by watchpocket on 2022-01-15
> **halogen2 said:**
> It's unlikely to be that simple. 

Here, btw, is what ***sudo apt-get install --install-recommends linux-generic*** returned:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-generic is already the newest version (5.4.0.7642.46~1598628707~20.04~040157c~dev).
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

```


And here is what ***sudo apt-get install --install-recommends linux-generic-hwe-20.04*** returned:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  linux-headers-5.11.0-46-generic linux-headers-generic-hwe-20.04 linux-hwe-5.11-headers-5.11.0-46 linux-image-5.11.0-46-generic linux-image-generic-hwe-20.04
  linux-modules-5.11.0-46-generic linux-modules-extra-5.11.0-46-generic
Suggested packages:
  fdutils linux-doc | linux-hwe-5.11-source-5.11.0 linux-hwe-5.11-tools
The following NEW packages will be installed:
  linux-generic-hwe-20.04 linux-headers-5.11.0-46-generic linux-headers-generic-hwe-20.04 linux-hwe-5.11-headers-5.11.0-46 linux-image-5.11.0-46-generic linux-image-generic-hwe-20.04
  linux-modules-5.11.0-46-generic linux-modules-extra-5.11.0-46-generic
0 upgraded, 8 newly installed, 0 to remove and 19 not upgraded.
Need to get 93.0 MB of archives.
After this operation, 494 MB of additional disk space will be used.
Do you want to continue? [Y/n] n

```

> Please post the outputs from the following commands -
```
apt-cache policy
```
This can be found [here]("https://paste.ubuntu.com/p/V2NQTnzRgC/").

> ```
apt-cache policy linux-generic linux-image-generic linux-system76
```

```
--> apt-cache policy linux-generic linux-image-generic linux-system76                                            pts/2  Saturday  2022-01-15  18:33:00 
linux-generic:
  Installed: 5.4.0.7642.46~1598628707~20.04~040157c~dev
  Candidate: 5.4.0.7642.46~1598628707~20.04~040157c~dev
  Version table:
 *** 5.4.0.7642.46~1598628707~20.04~040157c~dev 100
        100 /var/lib/dpkg/status
     5.4.0.94.98 500
        500 http://mirror.us-ny2.kamatera.com/ubuntu focal-updates/main amd64 Packages
     5.4.0.92.96 500
        500 http://mirror.us-ny2.kamatera.com/ubuntu focal-security/main amd64 Packages
     5.4.0.26.32 500
        500 http://mirror.us-ny2.kamatera.com/ubuntu focal/main amd64 Packages
linux-image-generic:
  Installed: 5.4.0.7642.46~1598628707~20.04~040157c~dev
  Candidate: 5.4.0.7642.46~1598628707~20.04~040157c~dev
  Version table:
 *** 5.4.0.7642.46~1598628707~20.04~040157c~dev 100
        100 /var/lib/dpkg/status
     5.4.0.94.98 500
        500 http://mirror.us-ny2.kamatera.com/ubuntu focal-updates/main amd64 Packages
     5.4.0.92.96 500
        500 http://mirror.us-ny2.kamatera.com/ubuntu focal-security/main amd64 Packages
     5.4.0.26.32 500
        500 http://mirror.us-ny2.kamatera.com/ubuntu focal/main amd64 Packages
linux-system76:
  Installed: (none)
  Candidate: (none)
  Version table:

```

---

### Post by &amp;KyT$0P# on 2022-01-15
Thanks.  Try the following (note that you can replace [FONT=Courier New]sudo apt-get[/FONT] with [FONT=Courier New]apt-get -s[/FONT] to check what it *would* do before actually going ahead):

1) Make sure the 5.4.0-94-generic kernel is installed -
```
sudo apt-get install linux-{headers,modules-extra}-5.4.0-94-generic
```

2) Reboot, pulling up the GRUB menu and ensure you boot into the 5.4.0-94-generic kernel.

3) Downgrade the kernel meta-packages (and linux-libc-dev if you have it installed) -
```
sudo apt-get install linux-generic/focal linux-{headers,image}-generic/focal linux-libc-dev/focal
```

4) Mark kernel packages from (1) as automatically installed -
```
sudo apt-mark auto linux-{headers,modules-extra}-5.4.0-94-generic
```

5) Confirm that things are normal: the following command should **not** try to autoremove the kernel you just installed -
```
apt-get -s --purge autoremove
```

6) If all is well at this point, it should be safe to purge the System76 kernel.

7) Check which kernel GRUB boots by default, it should now be the 5.4.0-94-generic.

---

### Post by watchpocket on 2022-01-16
> **halogen2 said:**
> Thanks.  Try the following (note that you can replace [FONT=Courier New]sudo apt-get[/FONT] with [FONT=Courier New]apt-get -s[/FONT] to check what it *would* do before actually going ahead):

1) Make sure the 5.4.0-94-generic kernel is installed -
```
sudo apt-get install linux-{headers,modules-extra}-5.4.0-94-generic
```


Having so far gone only this far, kernel 5.4.0-94 appearsto be installed. However, at the bottom of everything returned after entering the above command, this appeared:


```
DKMS: install completed.
   ...done.
Setting up linux-image-5.4.0-94-generic (5.4.0-94.106) ...
Failed to create symlink to vmlinuz-5.4.0-94-generic: Operation not permitted at /usr/bin/linux-update-symlinks line 64.
dpkg: error processing package linux-image-5.4.0-94-generic (--configure):
 installed linux-image-5.4.0-94-generic package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of linux-modules-extra-5.4.0-94-generic:
 linux-modules-extra-5.4.0-94-generic depends on linux-image-5.4.0-94-generic | linux-image-unsigned-5.4.0-94-generic; however:
  Package linux-image-5.4.0-94-generic is not configured yet.
  Package linux-image-unsigned-5.4.0-94-generic is not installed.

dpkg: error processing package linux-modules-extra-5.4.0-94-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-image-5.4.0-94-generic
 linux-modules-extra-5.4.0-94-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
sudo apt-get install linux-{headers,modules-extra}-5.4.0-94-generic  131.39s user 15.12s system 221% cpu 1:06.28 total

```

Here is line 64 (and surrounding lines) of /usr/bin/linux-update-symlinks:
```

 59  
 60     # Create a symlink with a temporary name
 61     my $rand;
 62     while (($rand = int(rand(1000000))) && !symlink($source, "$dest.$rand")) {
 63 *.......if ($! != POSIX::EEXIST) {
 64 *.......    die "Failed to create symlink to $source: $!";
 65 *.......}
 66     }
 67  
 68     # Move it into place atomically
 69     if (!rename("$dest.$rand", $dest)) { 
```

How significant are these error messages, and what might be done to remedy them?  Thanks.

---

### Post by &amp;KyT$0P# on 2022-01-16
> **watchpocket said:**
> ```
Failed to create symlink to vmlinuz-5.4.0-94-generic: Operation not permitted at /usr/bin/linux-update-symlinks line 64.
```

I'm not sure which symlink that is exactly, but check the output of
```
ls -la /
ls -la /boot
findmnt
```
make sure that user [FONT=Courier New]root[/FONT] can write to & create symlinks in both [FONT=Courier New]/[/FONT] and [FONT=Courier New]/boot[/FONT]

---

### Post by watchpocket on 2022-01-16
See below:

```

-> ls -la /                                                                                                       pts/3  Sunday  2022-01-16  16:57:28 
total 88
 4 drwxr-xr-x  21 root root  4096 Sep 30 12:00 ./
 4 drwxr-xr-x  21 root root  4096 Sep 30 12:00 ../
 0 lrwxrwxrwx   1 root root     7 Oct 13  2020 bin -> usr/bin/
 4 drwxr-xr-x   4 root root  4096 Dec 31  1969 boot/
 4 drwxr-xr-x   2 root root  4096 Oct 13  2020 cdrom/
 0 drwxr-xr-x  20 root root  4860 Jan 16 15:48 dev/
12 drwxr-xr-x 176 root root 12288 Jan 16 14:48 etc/
 4 drwxr-xr-x   3 root root  4096 Oct 13  2020 home/
 0 lrwxrwxrwx   1 root root     7 Oct 13  2020 lib -> usr/lib/
 0 lrwxrwxrwx   1 root root     9 Oct 13  2020 lib32 -> usr/lib32/
 0 lrwxrwxrwx   1 root root     9 Oct 13  2020 lib64 -> usr/lib64/
 0 lrwxrwxrwx   1 root root    10 Oct 13  2020 libx32 -> usr/libx32/
 4 drwx------   2 root root  4096 Jan 11 13:56 lost+found/
 4 drwxr-xr-x   4 root root  4096 Dec 15 18:00 media/
 4 drwxr-xr-x   4 root root  4096 Jan  2 17:01 mnt/
 4 drwxr-xr-x   8 root root  4096 Jan 16 14:48 opt/
 0 dr-xr-xr-x 408 root root     0 Jan 16 15:08 proc/
 4 drwxr-xr-x   8 root root  4096 Jan  2 15:30 root/
 0 drwxr-xr-x  43 root root  1300 Jan 16 16:04 run/
 0 lrwxrwxrwx   1 root root     8 Oct 13  2020 sbin -> usr/sbin/
 4 drwxrwxr-x  16 root root  4096 Dec 30 18:17 snap/
 4 drwxr-xr-x   2 root root  4096 Jul 31  2020 srv/
 0 dr-xr-xr-x  13 root root     0 Jan 16 15:36 sys/
 4 drwxr-xr-x   9 root root  4096 Jan 16 14:00 timeshift/
16 drwxrwxrwt  17 root root 16384 Jan 16 17:00 tmp/
 4 drwxr-xr-x  14 root root  4096 Jul 31  2020 usr/
 4 drwxr-xr-x  14 root root  4096 Jul 31  2020 var/
[rj@rjbox-2:~]  [zsh-5.8]  2004  -->                                                                                                                pts/3  Sunday  2022-01-16  17:02:00 
[rj@rjbox-2:~]  [zsh-5.8]  2004  -->                                                                                                                pts/3  Sunday  2022-01-16  17:02:03 
[rj@rjbox-2:~]  [zsh-5.8]  2004  --> ls -la /boot                                                                                                   pts/3  Sunday  2022-01-16  17:02:03 
total 18240
    4 drwxr-xr-x  4 root root     4096 Dec 31  1969 ./
    4 drwxr-xr-x 21 root root     4096 Sep 30 12:00 ../
    4 drwxr-xr-x  4 root root     4096 Dec 31  1969 EFI/
 4648 -rwxr-xr-x  1 root root  4756293 Jan  6 16:56 System.map-5.4.0-94-generic*
  236 -rwxr-xr-x  1 root root   237940 Jan  6 16:56 config-5.4.0-94-generic*
    4 drwxr-xr-x  4 root root     4096 Jan 11 14:43 grub/
13340 -rwxr-xr-x  1 root root 13656320 Jan  6 18:07 vmlinuz-5.4.0-94-generic*
[rj@rjbox-2:~]  [zsh-5.8]  2005  -->                                                                                                                pts/3  Sunday  2022-01-16  17:02:13 
[rj@rjbox-2:~]  [zsh-5.8]  2005  --> findmnt                                                                                                        pts/3  Sunday  2022-01-16  17:02:25 
TARGET                                     SOURCE                 FSTYPE          OPTIONS
/                                          /dev/sda2              ext4            rw,relatime,errors=remount-ro,stripe=8191
&#9500;&#9472;/sys                                     sysfs                  sysfs           rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/kernel/security                   securityfs             securityfs      rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/fs/cgroup                         tmpfs                  tmpfs           ro,nosuid,nodev,noexec,mode=755
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/unified               cgroup2                cgroup2         rw,nosuid,nodev,noexec,relatime,nsdelegate
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/systemd               cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,xattr,name=systemd
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/devices               cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,devices
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/pids                  cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,pids
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/cpuset                cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,cpuset
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/net_cls,net_prio      cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,net_cls,net_prio
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/cpu,cpuacct           cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,cpu,cpuacct
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/blkio                 cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,blkio
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/perf_event            cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,perf_event
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/hugetlb               cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,hugetlb
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/memory                cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,memory
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/rdma                  cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,rdma
&#9474; &#9474; &#9492;&#9472;/sys/fs/cgroup/freezer               cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,freezer
&#9474; &#9500;&#9472;/sys/fs/pstore                         pstore                 pstore          rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/firmware/efi/efivars              efivarfs               efivarfs        rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/fs/bpf                            none                   bpf             rw,nosuid,nodev,noexec,relatime,mode=700
&#9474; &#9500;&#9472;/sys/kernel/debug                      debugfs                debugfs         rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/kernel/tracing                    tracefs                tracefs         rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/fs/fuse/connections               fusectl                fusectl         rw,nosuid,nodev,noexec,relatime
&#9474; &#9492;&#9472;/sys/kernel/config                     configfs               configfs        rw,nosuid,nodev,noexec,relatime
&#9500;&#9472;/proc                                    proc                   proc            rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/proc/sys/fs/binfmt_misc               systemd-1              autofs          rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=29322
&#9474; &#9474; &#9492;&#9472;/proc/sys/fs/binfmt_misc             binfmt_misc            binfmt_misc     rw,nosuid,nodev,noexec,relatime
&#9474; &#9492;&#9472;/proc/fs/nfsd                          nfsd                   nfsd            rw,relatime
&#9500;&#9472;/dev                                     udev                   devtmpfs        rw,nosuid,noexec,relatime,size=65841208k,nr_inodes=16460302,mode=755
&#9474; &#9500;&#9472;/dev/pts                               devpts                 devpts          rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000
&#9474; &#9500;&#9472;/dev/shm                               tmpfs                  tmpfs           rw,nosuid,nodev
&#9474; &#9500;&#9472;/dev/mqueue                            mqueue                 mqueue          rw,nosuid,nodev,noexec,relatime
&#9474; &#9492;&#9472;/dev/hugepages                         hugetlbfs              hugetlbfs       rw,relatime,pagesize=2M
&#9500;&#9472;/run                                     tmpfs                  tmpfs           rw,nosuid,nodev,noexec,relatime,size=13189572k,mode=755
&#9474; &#9500;&#9472;/run/lock                              tmpfs                  tmpfs           rw,nosuid,nodev,noexec,relatime,size=5120k
&#9474; &#9500;&#9472;/run/rpc_pipefs                        sunrpc                 rpc_pipefs      rw,relatime
&#9474; &#9500;&#9472;/run/user/1000                         tmpfs                  tmpfs           rw,nosuid,nodev,relatime,size=13189568k,mode=700,uid=1000,gid=1000
&#9474; &#9474; &#9500;&#9472;/run/user/1000/gvfs                  gvfsd-fuse             fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=1000,group_id=1000
&#9474; &#9474; &#9492;&#9472;/run/user/1000/doc                   portal                 fuse.portal     rw,nosuid,nodev,relatime,user_id=1000,group_id=1000
&#9474; &#9500;&#9472;/run/timeshift/backup                  /dev/sdc2              ext4            rw,relatime,stripe=8191
&#9474; &#9492;&#9472;/run/snapd/ns                          tmpfs[/snapd/ns]       tmpfs           rw,nosuid,nodev,noexec,relatime,size=13189572k,mode=755
&#9474;   &#9492;&#9472;/run/snapd/ns/keepassxc.mnt          nsfs[mnt:[4026533361]] nsfs            rw
&#9500;&#9472;/snap/brave/140                          /dev/loop1             squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/core20/1270                        /dev/loop4             squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/bare/5                             /dev/loop0             squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/youtube-dl-pro/53                  /dev/loop6             squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/pyqt5-runtime/11                   /dev/loop7             squashfs        ro,nodev,relatime
&#9500;&#9472;/boot                                    /dev/sda1              vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
&#9474; &#9492;&#9472;/boot/efi                              /dev/sda1              vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
&#9500;&#9472;/snap/keepassxc/1522                     /dev/loop5             squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/youtube-dl-pro/52                  /dev/loop9             squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/pyqt5-runtime/12                   /dev/loop8             squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/ubuntu-mate-welcome/639            /dev/loop10            squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/gtk-common-themes/1519             /dev/loop11            squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/snapd/14295                        /dev/loop13            squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/lnav/2198                          /dev/loop12            squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/kde-frameworks-5-qt-5-15-core20/14 /dev/loop14            squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/ubuntu-mate-welcome/646            /dev/loop15            squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/brave/141                          /dev/loop16            squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/snapd/14066                        /dev/loop17            squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/core18/2253                        /dev/loop18            squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/software-boutique/54               /dev/loop19            squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/core18/2284                        /dev/loop2             squashfs        ro,nodev,relatime
&#9492;&#9472;/snap/core20/1242                        /dev/loop3             squashfs        ro,nodev,relatime


```

---

### Post by watchpocket on 2022-01-16
I am wondering if the "lib32" and "libx32"  lines should be there.  I don't think I've seen them there previously:

*0 lrwxrwxrwx   1 root root     9 Oct 13  2020 lib32 -> usr/lib32/*

---

### Post by &amp;KyT$0P# on 2022-01-16
The problem is that your EFI partition somehow got mounted at [FONT=Courier New]/boot[/FONT] as well as the normal location [FONT=Courier New]/boot/efi[/FONT] at the same time.  But [FONT=Courier New]/boot[/FONT] needs to be a Linux type filesystem.  Sorry I have no idea how to safely fix this :(

---

### Post by watchpocket on 2022-01-16
OK - Thanks loads for helping me get this far. 
 (It may be that my less-than-perfect use of Timeshift  had something to do with the misplacement of the EFI partition.)

```
--> lf /boot   
total 18232
    4 drwxr-xr-x 4 root root     4096 Dec 31  1969 EFI/
 4648 -rwxr-xr-x 1 root root  4756293 Jan  6 16:56 System.map-5.4.0-94-generic*
  236 -rwxr-xr-x 1 root root   237940 Jan  6 16:56 config-5.4.0-94-generic*
    4 drwxr-xr-x 4 root root     4096 Jan 11 14:43 grub/
13340 -rwxr-xr-x 1 root root 13656320 Jan  6 18:07 vmlinuz-5.4.0-94-generic*
[rj@rjbox-2:~]  [zsh-5.8]  2007  --> lf /boot/EFI    
total 18232
    4 drwxr-xr-x 4 root root     4096 Jan 11 14:43 EFI/
 4648 -rwxr-xr-x 1 root root  4756293 Jan  6 16:56 System.map-5.4.0-94-generic*
  236 -rwxr-xr-x 1 root root   237940 Jan  6 16:56 config-5.4.0-94-generic*
    4 drwxr-xr-x 4 root root     4096 Jan 11 14:43 grub/
13340 -rwxr-xr-x 1 root root 13656320 Jan  6 18:07 vmlinuz-5.4.0-94-generic*

--> lf /boot/EFI/EFI  
total 8
4 drwxr-xr-x 2 root root 4096 Jan 11 14:43 BOOT/
4 drwxr-xr-x 2 root root 4096 Jan 11 14:43 ubuntu/

--> lf /boot/EFI/EFI/BOOT   
total 1860
936 -rwxr-xr-x 1 root root 955656 Jan 11 14:43 BOOTX64.EFI*
 84 -rwxr-xr-x 1 root root  85672 Jan 11 14:43 fbx64.efi*
840 -rwxr-xr-x 1 root root 856232 Jan 11 14:43 mmx64.efi*


```

---

### Post by watchpocket on 2022-01-16
> **halogen2 said:**
> 1) Make sure the 5.4.0-94-generic kernel is installed -
```
sudo apt-get install linux-{headers,modules-extra}-5.4.0-94-generic
```
[etc] 

Just a note to say that all of this worked fine on my other (NVMe) drive, where I was also running the 5.4.0-7642 kernel.  
I'm now using 5.4.0-94-generic there and have removed the System76 kernel.  (There were no issues with the /boot and /boot/efi dirs there.)

Now all I need to do is get grub to have the sda drive as an entry on its menu, and of course, to fix my sda drive's /boot dir.

---

### Post by &amp;KyT$0P# on 2022-01-16
> **watchpocket said:**
> Just a note to say that all of this worked fine on my other (NVMe) drive, where I was also running the 5.4.0-7642 kernel.  
I'm now using 5.4.0-94-generic there and have removed the System76 kernel. 

Cool, you're welcome & thanks for reporting back :KS

---

### Post by watchpocket on 2022-01-17
I've now cleaned up my /boot and /boot/efi dirs on my sda drive, and I've installed kernel 5.4.0-94-generic there as well as on my NVMe drive.

I've completely rid myself of the 5.4.0-7642 System76 kernel on both of my drives. (For anyone new to this thread, I'm not using any System76 hardware.)

There are still a few nits to work out, but for purposes of this thread, I've marked it SOLVED.  Thanks again, Halogen2.

---

