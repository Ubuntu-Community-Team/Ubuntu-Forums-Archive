---
title: "All primary partitions are in use"
date: 2022-03-28
forum: Virtualisation
---

### Post by q-it-13 on 2022-03-28
Hi all, 
I have a problem on a ubuntu 16.04.3 when I try to add spaces to my disks.
I add 10 Gb to my Virtual Machine and when I do ```
cfdisk
``` I can see  ```
Free space 262144000 283115519 20971520 **10G**
```
But when I try to select New it says ```
All primary partitions are in use
```
Can you help me I know a little linux but that is out of my skills, how can I add that 10G ?

You can see

```
 lsblkNAME                                MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                                   8:0    0   135G  0 disk 
&#9500;&#9472;sda1                                8:1    0   487M  0 part /boot
&#9500;&#9472;sda3                                8:3    0   100G  0 part 
&#9474; &#9492;&#9472;template--ubuntu--16--vg-root   252:0    0 116,5G  0 lvm  /
&#9500;&#9472;sda4                                8:4    0     5G  0 part 
&#9474; &#9492;&#9472;template--ubuntu--16--vg-root   252:0    0 116,5G  0 lvm  /
&#9492;&#9472;sda5                                8:5    0  19,5G  0 part 
  &#9500;&#9472;template--ubuntu--16--vg-root   252:0    0 116,5G  0 lvm  /
  &#9492;&#9472;template--ubuntu--16--vg-swap_1 252:1    0     8G  0 lvm  [SWAP]
sr0                                  11:0    1  1024M  0 rom  

``` 

```
lvs  LV     VG                    Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   template-ubuntu-16-vg -wi-ao---- 116,52g                                                    
  swap_1 template-ubuntu-16-vg -wi-ao----   8,00g   

```

```
vgs  VG                    #PV #LV #SN Attr   VSize   VFree
  template-ubuntu-16-vg   3   2   0 wz--n- 124,52g    0 

```

```
 pvs  PV         VG                    Fmt  Attr PSize   PFree
  /dev/sda3  template-ubuntu-16-vg lvm2 a--  100,00g    0 
  /dev/sda4  template-ubuntu-16-vg lvm2 a--    5,00g    0 
  /dev/sda5  template-ubuntu-16-vg lvm2 a--   19,52g    0 

```

Thank you a lot if you can help me

---

### Post by TheFu on 2022-03-28
There are two types of partition tables used by MS-Windows and Linux.
[LIST]
[*]MBR/MSDOS
[*]GPT
[/LIST]

Each has limitations, but the MBR partition table has a limitation of 4 primary partitions. Your setup is already using all 4, so no more can be added.
GPT, the more modern type of partition table has been around decades and has been preferred for over 10 yrs.

For a long time, much longer than necessary, the Ubuntu installer would create an MBR partition table whenever LVM was selected, so how the system ended up this situation is easy to understand.

Because this is a virtual machine and using LVM2, there are hundreds of options to make a better situation.  You can do a quick fix or you can learn to setup a much nicer situation.
I posted exact steps for the quick fix in these forums about 18-24 months ago.  Let me try to find that post in my notes: 
[Https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156](Https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156)
Step by step. I did this and captured the actual commands as I did them. ZERO downtime for the VM.

If you have time, I'd recommend a better solution that uses LVM, not partitioning, for the final solution.  I'm actually a little shocked that adding more partitions was done. That seems like the hard way, but we all lack some knowledge before we gain new knowledge, so there's little point in going over it.

---

### Post by slickymaster on 2022-03-28
Thread moved to **Virtualisation** which is a better place for it

---

### Post by DuckHook on 2022-03-28
> **TheFu said:**
> …If you have time, I'd recommend a better solution that uses LVM, not partitioning, for the final solution.
+1

I've found that it's almost always better to set things up nicely rather than take the immediately more convenient way. Convenience often stores up trouble for later whereas taking the time to set up nicely brings all sorts of long term benefits. I.e. LVM snapshots are incredible. Being able to shrink and expand filesystems at will is also great.

---

### Post by guiverc on 2022-03-28
Don't forget Ubuntu 16.04 LTS has ended it's *standard* support life, and is in *extended support* which requires ESM to be *enabled* for security fixes to be seen, downloaded and installed.

[https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)

A fully upgraded machine should have reported itself as [16.04.7]("https://fridge.ubuntu.com/2020/08/14/ubuntu-16-04-7-lts-released/") even before reaching the end of it's *standard support* back in April 2021, so if your machine reports as 16.04.3 you are *years* behind on security fixes - I hope you use that system only offline.

---

### Post by DuckHook on 2022-03-28
> **guiverc said:**
> &#8230;A fully upgraded machine should have reported itself as [16.04.7]("https://fridge.ubuntu.com/2020/08/14/ubuntu-16-04-7-lts-released/") even before reaching the end of it's *standard support* back in April 2021, so if your machine reports as 16.04.3 you are *years* behind on security fixes - I hope you use that system only offline.
+1

Good catch. I did not even see that.

---

### Post by TheFu on 2022-03-29
> **DuckHook said:**
> +1

I've found that it's almost always better to set things up nicely rather than take the immediately more convenient way. Convenience often stores up trouble for later whereas taking the time to set up nicely brings all sorts of long term benefits. I.e. LVM snapshots are incredible. Being able to shrink and expand filesystems at will is also great.

Many file systems cannot be reduced and reducing even ext4 has risks.  ZFS and XFS are popular and cannot be reduced, for example, though it would be odd to have both LVM2 and ZFS (I do, but that's a long story due to LXD).
But increasing a file system, provided there is free space inside the VG is pretty trivial, especially with ext4 file systems. 1 command, 5 seconds, no downtime, or even a need to take the file system offline for work.

But the if the total space required + 10-20G for snapshots exists on the VM host, creating a new fake HDD, setting up LVM with correctly laid out LVs for root, home, stuff, var, and swap, would be recommended.  Using just a root (/) LV is like putting a toddler into a red wagon to be pulled by Dad.  With LVM, wouldn't you rather have a sports car driven by Mario?
LVM is meant to be used to allocate to LVs 
[LIST]
[*]what you need
[*]where you need it
[*]and increased as you need it, over time
[/LIST]
That's the power of LVM and it prevents poor guessing.

---

