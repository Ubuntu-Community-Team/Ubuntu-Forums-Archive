---
title: "Windows Host VirtualBox + Ubuntu 20.04 guest. Increase HDD size"
date: 2021-04-22
forum: Virtualisation
---

### Post by nkat21 on 2021-04-22
Hello!
I have VirtualBox installed on Windows 2012 server and Ubuntu 20.04 as a guest OS
During installation .vdi was set to 10Gb
At the moment I decided to increase the size and already resized the .vdi up to 30Gb using VirtualBox
Then
1) run "disks"
[https://i.imgur.com/YMZAR77.png](https://i.imgur.com/YMZAR77.png)
2) resize partitions and it went similarly fine
3) restarted the host
and still the primary partition is 10Gb and 20Gb are unallocated
If I try another resize here is what gets displayed
[https://i.imgur.com/u6gBaBr.png](https://i.imgur.com/u6gBaBr.png)
Would someone please comment!?

---

### Post by CelticWarrior on 2021-04-22
Welcome.

Virtual Machine or normal installation the limitations are the same: You can't resize mounted partitions. 
You need to boot the VM from the installation ISO (live session) and use GParted to do exactly the same you would do in a normal installation.

---

### Post by TheFu on 2021-04-22
Did you resize the file system from inside the VM?  Resizing the partition is not enough.

**resize2fs** is the command.

Sorry, can't see the images.

---

### Post by ActionParsnip on 2021-04-22
Did you use LVM for the disks?

---

### Post by nkat21 on 2021-04-23
I'm sorry, what's LVM?

---

### Post by scorp123 on 2021-04-23
> **nkat21 said:**
> I'm sorry, what's LVM?

Logical Volume Manager

---

### Post by scorp123 on 2021-04-23
> **nkat21 said:**
>  and still the primary partition is 10Gb and 20Gb are unallocated 

You may have increased the partition/disk ... but you didn't increase the filesystem size inside.
To use an analogy: Just because you increased the size of your garage doesn't mean your car gets bigger...

Others here have already told you what you need to do, e.g. boot from a live CD and increase the filesystem on the disk while it is not mounted.

---

### Post by slickymaster on 2021-04-23
*Thread moved to **Virtualisation**.*

---

### Post by TheFu on 2021-04-23
> **scorp123 said:**
> You may have increased the partition/disk ... but you didn't increase the filesystem size inside.
To use an analogy: Just because you increased the size of your garage doesn't mean your car gets bigger...

Others here have already told you what you need to do, e.g. boot from a live CD and increase the filesystem on the disk while it is not mounted.

If you would please post the output from **sudo fdisk -l /dev/sda**, then we might see some other issues.  

For example, the physical placement on the storage may not allow the partition you want to be increased. The order of partitions and type of partition matters.  If you use GPT and not MSDOS partition tables, things are often easier, but there is still the physical layout if multiple partitions are immediately next to each other.  Shifting data around can get ugly, if that is needed.  Also, MSDOS partitions often are created with nested partitions, so resizing both is needed.  Do the Extended partition, then the logical partition inside.

And LVM ... LVM can allow all sorts of tricks that make changing things easier, but not always intuitively obvious.
Plus, by using a VM, you could just add a new vHDD, sized the way you want, create new partitions the size and in flexible locations inside the vHDD, and use partition cloning to migrate everything 1-for-1 in each partition to the new HDD. Update the /etc/fstab on the new vHDD storage and lastly, re-install and update grub on the new vHDD. Bob's your uncle.

For many people, the easiest answer would be to start over with a fresh install into larger vHDD storage. If you plan to get addicted to Ubuntu desktop, then 35G would be a minimal starting point.  For Ubuntu Server, it can be much smaller.  GUI code adds lots and lots of bloat.  

There are specialized Ubuntu releases just for use inside virtual machines or Linux containers. These can be tiny.  For example, I have an LXD container for DNS filtering. It is:
```
$ dft
Filesystem            Type  Size  Used Avail Use% Mounted on
lxd/containers/pihole zfs    13G  915M   12G   8% /

```less than 1GB in total storage. That's actually pretty bloated for what it really needs.  The 13G is shared across all my LXD containers, so it isn't like I'm wasting 12G. It doesn't have any swap, btw.

The "disks" tool is seldom used, BTW.  It follows the Gnome projects efforts to dumb down interfaces to where they are just a little too dumb.  **gparted** is the more capable solution, but it won't mount storage.

Anyways, storage possibilities are many on Unix systems. This isn't Windows.

---

### Post by nkat21 on 2021-04-28
Thank you! No, I did not use LVM
Currently, I have increased .vdi disk size up to 20Gb
In ubuntu I do see those 10Gb as free space
[ATTACH=CONFIG]288386[/ATTACH]
Right now I'm going to boot from CD and try resizing
If you could comment on LVM approach that would be great!
I believe smth like creating another partition should be done and then grouping those 2 partition into one logical entity of 20Gb
Please, elaborate

---

### Post by nkat21 on 2021-04-28
Thank you for your answer!
Here is the output of the fdisk -l /dev/sda command
[ATTACH=CONFIG]288387[/ATTACH]

---

### Post by slickymaster on 2021-04-28
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by TheFu on 2021-04-28
> **nkat21 said:**
> Thank you for your answer!
Here is the output of the fdisk -l /dev/sda command

Please copy/paste text here.  I can't quickly highlight stuff in images to point out issues, so I'm less likely to be clear in responses.

As I feared, you have partition complications.
There is 1 _logical_ (sda5) partition that takes up the entire _extended_ (sda2) partition. That logical partition is the one you'd like to make larger. Alas, it cannot cross outside the extended partition.  It has been many years, but I don't think extended partitions can be modified when there are any logical partitions inside. Then a _primary_ (sda3) partition was created after the extended partition and blocks any possibility of using gparted to simply extend the size of sda2.

Quite the pickle.

There are many, many, possible solutions. Since this is just a virtual machine, the easiest by far would be to just recreate the VM with the minimum recommended size (25G), move all your data/settings over to the new VM over the network, then using a generated list of installed programs, install all the programs you already have.  This is a 30 minute effort on modern systems.  35G in size would be better, BTW.  Ubuntu has become much more bloated in 18.04.  BTW, I was caught no allocation sufficient storage to a VM too.  It was with a 20.04 desktop last June. ;)

As for LVM, had you selected LVM during the installation of the OS, there would be trivial ways to add another virtual disk, add that vDisk into the VG and extend the LVs as needed. I've done it: [https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156](https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156)  outlines the steps.
LVM provides, options.

---

