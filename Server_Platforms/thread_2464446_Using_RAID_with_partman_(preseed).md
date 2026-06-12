---
title: "Using RAID with partman (preseed)"
date: 2021-07-02
forum: Server Platforms
---

### Post by samad909 on 2021-07-02
I am trying to automate software RAID configuration and partitioning using partman during the OS install via a preseed config. I have followed the guide listed on the [Ubuntu website]("https://help.ubuntu.com/lts/installation-guide/example-preseed.txt"). I copied the part under "## Partitioning using RAID" as is and tried using it. However at the partitioning stage it keeps showing me [this screen]("https://i.imgur.com/KTrH4IX.png"). As you can see it doesnt setup the partitions as listed in the preseed, but just creates a single partition on both disks instead. Software RAID is not configured and it selects the first disk's partition for the OS install. This is what the preseed configuration looks like (almost an exact copy from the Ubuntu website, just changed the partition sizes and filesystem),

```
d-i partman-auto/method string raid
d-i partman-auto/disk string /dev/sda /dev/sdb

d-i partman-auto/expert_recipe string \
      multiraid ::                                         \
              2000 5000 4000 raid                          \
                      $primary{ } method{ raid }           \
              .                                            \
              2000 512 4000 raid                           \
                      method{ raid }                       \
              .                                            \
              500 10000 1000000000 raid                    \
                      method{ raid }                       \
              .

d-i partman-auto-raid/recipe string \
    1 2 0 ext4 /                    \
          /dev/sda1#/dev/sdb1       \
    .                               \
    1 2 0 swap -                    \
          /dev/sda5#/dev/sdb5       \
    .                               \
    0 2 0 ext4 /home                \
          /dev/sda6#/dev/sdb6       \
    .

d-i partman-md/confirm boolean true
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
```

I have also tried adding the $lvmignore{ } tag but that didn't help.
Any ideas?

---

### Post by MAFoElffen on 2021-07-04
What did your Intsallation Log say?

Are you preseeding with Ubuntu Server LTS 18.04 or 20.04? 18.04 still used the debian installer. 20.04 went to the subiquity server installer, with the process now called the Server Autoinstall. 

With the 20.04 installer- Since the whole installer is different, the debian installer preseed file does not work with the new installer. It is not backward compatible, because they are different animals. The reason's was because of SystemD and Yaml. I think you'll find the documention better than the debian installer was. There are 22 examples on GitHub: Canonical/subiquity examples, but I think only 2-3 of them relate to RAID storage 

RE: 
 - [Ubuntu Server AutoInstall Quickstart]("https://ubuntu.com/server/docs/install/autoinstall-quickstart")
 - [Understanding the Ubuntu 20.04 LTS Server Autoinstaller]("https://louwrentius.com/understanding-the-ubuntu-2004-lts-server-autoinstaller.html"): Look under his Storage Configuration, RAID Section
 - [Curtin Syntax Storage Configuration]("https://curtin.readthedocs.io/en/latest/topics/storage.html")
 - [Looking to create a Software RAID 1 setup for your 2-disk server on Ubuntu Server 20.04?]("https://gist.io/@fevangelou/2f7aa0d9b5cb42d783302727665bf80a")
 - [GitHub Subiquity Examples]("https://github.com/canonical/subiquity/tree/main/examples")

I hope that guides you in the right direction...

---

### Post by samad909 on 2021-07-05
Thanks for getting back to me. I am trying to install Ubuntu 18.04 LTS and this is what the [installation log]("https://i.imgur.com/qDxzUIf.png") looks like.

---

### Post by MAFoElffen on 2021-07-05
I see that it starts...It looked for existing mdadm members and found none... it started to make partitions... then didn't see what it did or where it failed.

I researched this a little. The preseed you are using is very close to the default example, which says:
```
 
- create 3 partitions each, on 2 disks
 - -  partitions sda1 and sdb1 as RAID1 members on two disks (mirrored), mounted as root, marked as bootable partitions. The size of the partition is fixed. Priority is as high as swap???
 - - partitions sda5 and sdb5 as RAID1 members on two disks (mirrored), mounted as Swap. The size of the partition is fixed. Priority is competing as high as root???
 - - partitions sda6 and sdb6 as RAID0, spanning across two disks, mounted as Home...The size of the partition is to query the the remaining space and use all unused. Priority is lower than Swap???

```
 - You get a mirrored system root, Swap is not "that" important to mirror, but if you have a disk failure, and you have mirrored disks, you just go on as usual, Right? Except that by not mirroring the Home, you end up having a big Home for data, but if one disk physically fails, you have no Home. Right? So as a strategy, the sys can be recreated quickly.  
 - On the swap, as in the example, is usually to query the system RAM and give a percentage... You definitely have the priority set to high on you swap partition. You say it's priority is higher than the Home, and it's maximum size is as large as the root partition. I think this is where it fails.
 - on the use of: use all unused, In mdadm, if the disks are not identical (different brand or models), this may sometimes fail in a preseed. Because it might see different unused space left to create the partitions.
```
# Specify the disks to be partitioned. They will all get the same layout, # so this will only work if the disks are the same size.
```
Not saying those are your problem, but not seeing the full log, that is what I might suspect. Play with the settings in your expert-recipe string (especially in defining your swap), and see if that makes a difference.

---

