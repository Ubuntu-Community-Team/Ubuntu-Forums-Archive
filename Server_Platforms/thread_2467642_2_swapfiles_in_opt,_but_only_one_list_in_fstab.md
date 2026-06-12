---
title: "2 swapfiles in /opt, but only one list in fstab?"
date: 2021-10-02
forum: Server Platforms
---

### Post by Heeter on 2021-10-02
Hi all,

Found 2 different sized swap files in the /opt folder:

```

root@serv:/home/adminpc# ls /opt
lost+found  swapfile15g  swapfile20g
root@serv:/home/adminpc#

```

In the fstab file, there is only one listed:

```

/opt/swapfile20g     none            swap    sw              0       0

```


Can I delete the other one?

Regards

---

### Post by darkod on 2021-10-03
Probably yes. It looks like it remained from earlier and wasn't deleted when it stopped being used.

In any case you can check active swap with the following command too, and that file will probably not be in the list of used ones:
```
swapon -s
```

---

### Post by LHammonds on 2021-10-03
> **Heeter said:**
> Can I delete the other one?
You (or the person setting up your server) was following [my tutorial](https://hammondslegacy.com/forum/viewtopic.php?p=814#p814) with their own customizations.  If you re-read the "Swap File Management" section, it shows how to add and remove swap files safely.

LHammonds

---

### Post by Heeter on 2021-10-03
Hey, Guys Thank you for your responses

It is the only one showing up on list

Lhammonds, I did use your tutorial to set up this server. I will use your tutorial to remove the extra swapfile.

Thank again Guys!!!!

---

### Post by TheFu on 2021-10-03
If you are using LVM, don't use swapfiles. Use a swap LV.

---

### Post by Heeter on 2021-10-03
Actually Thank you The FU

the swapfile is sitting in the /dev/LVG/opt folder, would that be considering swapLV?

---

### Post by TheFu on 2021-10-03
> **Heeter said:**
> Actually Thank you The FU

the swapfile is sitting in the /dev/LVG/opt folder, would that be considering swapLV?

No.  If you didn't run 
```
sudo mkswap /dev/{vgname}/{lvname}
```
then it isn't a swap partition/LV.

---

### Post by Heeter on 2021-10-03
> **TheFu said:**
> No.  If you didn't run 
```
sudo mkswap /dev/{vgname}/{lvname}
```
then it isn't a swap partition/LV.

Hi theFU! Thank you for responding!!!!.

If I understand your response correctly, the current swapfile sits in the /dev/LVG/opt folder and in the fstab file, with the command that you wrote, can the swap file stay in that folder? Or does it create a new swapfile in /dev/LVG/swap?

Just wondering if I should remove the current swapfile and remove the /dev/LVG/opt LVM?

Thank you again for being there for me.

---

### Post by TheFu on 2021-10-03
sudo mkswap /dev/{vgname}/{lvname}

Either you did that or you didn't.
If you use lsblk, does it show /dev/{vgname}/{lvname} as an LV, type swap?

Something like this?
```
  &#9500;&#9472;hadar--vg-[COLOR="#FF0000"]swap_1[/COLOR]              4.3G lvm  swap        [SWAP]
```

There is no "directory" called /dev/{vgname}/{lvname}.  It is a symlink to a /dev/dm-{some number}

```
$ ll /dev/hadar-vg/
total 0
drwxr-xr-x  2 root root  300 Oct  2 18:36 ./
drwxr-xr-x 21 root root 4960 Oct  3 22:21 ../
lrwxrwxrwx  1 root root    7 Oct  3 20:48 libvirt-lv -> ../dm-2
lrwxrwxrwx  1 root root    7 Oct  3 20:48 root -> ../dm-0
lrwxrwxrwx  1 root root    7 Oct  3 20:48 [COLOR="#FF0000"]swap_1[/COLOR] -> ../dm-1

```
I cleaned up that listing for clarity.  There are many other LVs there, each pointing at a different ../dm-{some number} device.

---

### Post by Heeter on 2021-10-03
Hi TheFU

Nope, it doesn't show up:

```

root@serv:/home/adminpc# lsblk
NAME              MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda                 8:0    0  1.8T  0 disk 
&#9492;&#9472;sda1              8:1    0  1.8T  0 part /mnt/2TExternal
sdc                 8:32   0  1.7T  0 disk 
&#9500;&#9472;sdc1              8:33   0  1.9G  0 part /boot
&#9500;&#9472;sdc2              8:34   0    1K  0 part 
&#9492;&#9472;sdc5              8:37   0  1.6T  0 part 
  &#9500;&#9472;LVG-root      253:0    0    4G  0 lvm  /
  &#9500;&#9472;LVG-usr       253:1    0   10G  0 lvm  /usr
  &#9500;&#9472;LVG-var       253:2    0    4G  0 lvm  /var
  &#9500;&#9472;LVG-tmp       253:3    0  3.5G  0 lvm  /tmp
  &#9500;&#9472;LVG-bak       253:4    0  7.5G  0 lvm  /bak
  &#9500;&#9472;LVG-srv       253:5    0  3.8G  0 lvm  /srv
  &#9500;&#9472;LVG-opt       253:6    0   52G  0 lvm  /opt
  &#9500;&#9472;LVG-home      253:7    0  1.8G  0 lvm  /home
  &#9492;&#9472;LVG-vmstorage 253:9    0  1.6T  0 lvm  /var/vmstorage
sr0                11:0    1 1024M  0 rom  
sr1                11:1    1 1024M  0 rom  
root@serv:/home/adminpc# 

```

```

root@serv:/home/adminpc# ll /dev/LVG
total 0
drwxr-xr-x  2 root root  220 Oct  3 12:56 ./
drwxr-xr-x 20 root root 4540 Oct  3 12:56 ../
lrwxrwxrwx  1 root root    7 Oct  2 17:16 bak -> ../dm-4
lrwxrwxrwx  1 root root    7 Oct  2 17:16 home -> ../dm-7
lrwxrwxrwx  1 root root    7 Oct  2 17:16 opt -> ../dm-6
lrwxrwxrwx  1 root root    7 Oct  2 17:16 root -> ../dm-0
lrwxrwxrwx  1 root root    7 Oct  2 17:16 srv -> ../dm-5
lrwxrwxrwx  1 root root    7 Oct  2 17:16 tmp -> ../dm-3
lrwxrwxrwx  1 root root    7 Oct  2 17:16 usr -> ../dm-1
lrwxrwxrwx  1 root root    7 Oct  2 17:16 var -> ../dm-2
lrwxrwxrwx  1 root root    7 Oct  2 17:16 vmstorage -> ../dm-9
root@serv:/home/adminpc#

```

```

root@serv:/home/adminpc# free -h
              total        used        free      shared  buff/cache   available
Mem:           94Gi         9Gi       452Mi       1.0Mi        83Gi        83Gi
Swap:          19Gi        24Mi        19Gi
root@serv:/home/adminpc# 

```

](*,)

What can I do to fix this? Have to add this to the growing list of fixes on this setup, LOLOL

---

### Post by LHammonds on 2021-10-05
Not convinced a swap file is that much worse than a partition.  Swap files should be fine.  The goal is not to utilize the swap file...only have it as an emergency overflow.   If you are constantly using the swap space, that's a sign you need more RAM.

LHammonds

---

### Post by TheFu on 2021-10-05
A swapfile is a new thing on Linux. 

Swap partitions/LVs have been around 25+ yrs.  

I'm not convinced change is good and if using LVM for the swap device, there is even less incentive to change because the main reason to have swapfiles is they can be easy to resize.  LVM makes resizing easy too. Anyway, that's my thought process.

As for the size of swap.  For a desktop, my answer is 4.1GB. This works for low-RAM systems and is sufficient for high-RAM systems so the end-users "feel" the RAM crunch and can take steps to close some programs. It is easy for any web browser to eat 4G of RAM these days.

On a server, the answer becomes more complex.  I strive to never need **any** swap on my servers, but that is based on workloads. To know how much RAM is needed for a workload requires monitoring for a few months to get the sizing correct.

If I was running a VPS and wanted to encourage my customers to move up to a higher-cost plan, I'd have 64G of swap so that most VPS instances would be swapped out.  I'd want to provide what they paid for, but make it slow until they got to a $20/month plan.  At $5/month, the hassles of dealing with customers are just too great for $60/yr. I wouldn't want to encourage that.

> What can I do to fix this? Have to add this to the growing list of fixes on this setup, LOLOL 
Create an LV and use it for swap?  Is this a trick question?

---

### Post by Heeter on 2021-10-05
Thanks Guys, Lhammonds and The FU

---

### Post by rsteinmetz70112 on 2021-10-06
> **TheFu said:**
> If you are using LVM, don't use swapfiles. Use a swap LV.

Could you please elaborate on why?

---

### Post by TheFu on 2021-10-06
> **rsteinmetz70112 said:**
> Could you please elaborate on why?

See post #12 above.

---

