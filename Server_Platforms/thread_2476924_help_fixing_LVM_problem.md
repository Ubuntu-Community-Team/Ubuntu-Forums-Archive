---
title: "help fixing LVM problem"
date: 2022-07-12
forum: Server Platforms
---

### Post by fst001 on 2022-07-12
i made a really big mess :(. thanks to a storage admin that told me all volumes i've told him are removed from zoning i wiped an old server with all disks. unfortunately one disk was still zoned to the server and got wiped as well ](*,)

so the other server that all the raw devices have been moved to has a broken LVM consisting of 10 instead of 11 disks. i know that the data is lost, but is there a way how to get the data out of the other 10 disks or somehow fix the vg and better the whole logical volumes?

i tried remove the missing volume but this removed the logical volume as well :(. and using vgcfgrestore can see the lvm backups/archive but i can't manage to get it back. i already tried remap the deleted volume again, but from what i see it looks like the lvm config uuid maps to a wrong disk.

```
description = "Created *before* executing 'vgreduce --removemissing FS00x_VG_DATA'"

creation_host = "xxx" # Linux FS001 5.4.0-121-generic #137-Ubuntu SMP Wed Jun 15 13:33:07 UTC 2022 x86_64
creation_time = 1657395786      # Sat Jul  9 21:43:06 2022


FS00x_VG_DATA {
        id = "h3SZvF-uiux-Uu0c-eyQS-rDEJ-O0Xe-5j2uCx"
        seqno = 17
        format = "lvm2"                 # informational
        status = ["RESIZEABLE", "READ", "WRITE"]
        flags = []
        extent_size = 8192              # 4 Megabytes
        max_lv = 0
        max_pv = 0
        metadata_copies = 0


        physical_volumes {


                pv0 {
                        id = "zGEC9n-Hbop-M0TU-3Rm5-cXgs-vl0N-GrTGWL"
                        device = "[unknown]"    # Hint only


                        status = ["ALLOCATABLE"]
                        flags = ["MISSING"]
                        dev_size = 21474832384  # 10 Terabytes
                        pe_start = 2048
                        pe_count = 2621439      # 10 Terabytes
                }


                pv1 {
                        id = "9Gv4nQ-r28B-OdqE-GWMT-BPC3-4Lgh-RfIXGi"
                        device = "/dev/mapper/sdi_crypt"        # Hint only


                        status = ["ALLOCATABLE"]
                        flags = []
                        dev_size = 21474832384  # 10 Terabytes
                        pe_start = 2048
                        pe_count = 2621439      # 10 Terabytes
                }


                pv2 {
                        id = "cltQGM-NKhS-YHFe-jEkd-NPVc-futc-PfoARI"
                        device = "/dev/mapper/sdj_crypt"        # Hint only


                        status = ["ALLOCATABLE"]
                        flags = []
                        dev_size = 21474832384  # 10 Terabytes
                        pe_start = 2048
                        pe_count = 2621439      # 10 Terabytes
                }


                pv3 {
                        id = "SL1lbL-0w2v-1vaf-yruZ-Gmjn-EvHj-Cjh1td"
                        device = "/dev/mapper/sdk_crypt"        # Hint only


                        status = ["ALLOCATABLE"]
                        flags = []
                        dev_size = 21474832384  # 10 Terabytes
                        pe_start = 2048
                        pe_count = 2621439      # 10 Terabytes
                }


                pv4 {
                        id = "7Cbr31-7kfg-Ye2g-UztT-hNuR-xTb1-P87KG0"
                        device = "/dev/mapper/sdl_crypt"        # Hint only


                        status = ["ALLOCATABLE"]
                        flags = []
                        dev_size = 21474832384  # 10 Terabytes
                        pe_start = 2048
                        pe_count = 2621439      # 10 Terabytes
                }


                pv5 {
                        id = "pKoyzI-Y0nf-DDeZ-K951-F3fs-bwX5-wAMzX3"
                        device = "/dev/mapper/sdb_crypt"        # Hint only


                        status = ["ALLOCATABLE"]
                        flags = []
                        dev_size = 21474832384  # 10 Terabytes
                        pe_start = 2048
                        pe_count = 2621439      # 10 Terabytes
                }


                pv6 {
                        id = "PsHsPr-WDx3-MyaX-AZZJ-o7GS-hV4M-WbLqac"
                        device = "/dev/mapper/sdc_crypt"        # Hint only


                        status = ["ALLOCATABLE"]
                        flags = []
                        dev_size = 21474832384  # 10 Terabytes
                        pe_start = 2048
                        pe_count = 2621439      # 10 Terabytes
                }


                pv7 {
                        id = "ZwoRye-1wji-sZVn-8TP6-xLe3-490Z-w8Y5EM"
                        device = "/dev/mapper/sdd_crypt"        # Hint only


                        status = ["ALLOCATABLE"]
                        flags = []
                        dev_size = 21474832384  # 10 Terabytes
                        pe_start = 2048
                        pe_count = 2621439      # 10 Terabytes
                }


                pv8 {
                        id = "aBrCme-GiBB-eZjm-uo1a-guxJ-4T83-Iedeyl"
                        device = "/dev/mapper/sde_crypt"        # Hint only


                        status = ["ALLOCATABLE"]
                        flags = []
                        dev_size = 21474832384  # 10 Terabytes
                        pe_start = 2048
                        pe_count = 2621439      # 10 Terabytes
                }


                pv9 {
                        id = "3BIP11-BgjI-Oo59-ggYq-7L5b-w0DO-uEr4Eb"
                        device = "/dev/mapper/sdf_crypt"        # Hint only


                        status = ["ALLOCATABLE"]
                        flags = []
                        dev_size = 21474803712  # 9.99998 Terabytes
                        pe_start = 2048
                        pe_count = 2621435      # 9.99998 Terabytes
                }


                pv10 {
                        id = "3GIcYu-MEF9-zf1s-OLi4-WfMZ-3dFc-bBVzlO"
                        device = "/dev/mapper/sdg_crypt"        # Hint only


                        status = ["ALLOCATABLE"]
                        flags = []
                        dev_size = 21474803712  # 9.99998 Terabytes
                        pe_start = 2048
                        pe_count = 2621435      # 9.99998 Terabytes
                }
        }
```

according to this, the missing disk should be uuid zGEC9n-Hbop-M0TU-3Rm5-cXgs-vl0N-GrTGWL, but the deleted disk is one of the last two pv's with a little less than 10TB, so it can't map it with the following command:

```
root@xxx:~# pvcreate --test --uuid "zGEC9n-Hbop-M0TU-3Rm5-cXgs-vl0N-GrTGWL" --restorefile /etc/lvm/archive/FS00x_VG_DATA_00007-57313386.vg /dev/mapper/sdh_crypt --force  TEST MODE: Metadata will NOT be updated and volumes will not be (de)activated.
  WARNING: Couldn't find device with uuid zGEC9n-Hbop-M0TU-3Rm5-cXgs-vl0N-GrTGWL.
  WARNING: Couldn't find device with uuid 9Gv4nQ-r28B-OdqE-GWMT-BPC3-4Lgh-RfIXGi.
  WARNING: Couldn't find device with uuid cltQGM-NKhS-YHFe-jEkd-NPVc-futc-PfoARI.
  WARNING: Couldn't find device with uuid SL1lbL-0w2v-1vaf-yruZ-Gmjn-EvHj-Cjh1td.
  WARNING: Couldn't find device with uuid 7Cbr31-7kfg-Ye2g-UztT-hNuR-xTb1-P87KG0.
  WARNING: Couldn't find device with uuid pKoyzI-Y0nf-DDeZ-K951-F3fs-bwX5-wAMzX3.
  WARNING: Couldn't find device with uuid PsHsPr-WDx3-MyaX-AZZJ-o7GS-hV4M-WbLqac.
  WARNING: Couldn't find device with uuid ZwoRye-1wji-sZVn-8TP6-xLe3-490Z-w8Y5EM.
  WARNING: Couldn't find device with uuid aBrCme-GiBB-eZjm-uo1a-guxJ-4T83-Iedeyl.
  WARNING: Couldn't find device with uuid 3BIP11-BgjI-Oo59-ggYq-7L5b-w0DO-uEr4Eb.
  WARNING: Couldn't find device with uuid 3GIcYu-MEF9-zf1s-OLi4-WfMZ-3dFc-bBVzlO.
  Physical extents end beyond end of device /dev/mapper/sdh_crypt.
  Format-specific initialisation of physical volume /dev/mapper/sdh_crypt failed.
  Failed to setup physical volume "/dev/mapper/sdh_crypt".
```

should i try to use testdisk to try to get data from the old disks or is there a way to fix this mess to get 100TB of data back instead of the full 110TB?

thanks

---

### Post by TheFu on 2022-07-12
This feels a bunch like work (and I'm not being paid), so I won't be digging deep into the LVM details.  My only real skill in this is from using LVM 20+ yrs and having 80% of my data lost due to my stupidity about 20 yrs ago.  I've worked with storage teams before.  They can be both brilliant and have tightly focused views, since they may be managing hundreds of frames with tens of thousands of client servers and hundreds of thousands of physical and virtual disks.  I've also had failures due to the storage vendor SE oversimplifying how some advanced tools in their frames worked which turned out not to be true.

I've never used vgcfg-anything.  My data loss a few decades ago taught me to keep LVM use simple.  Complex setups fail in bad ways and make having bonehead simple backups even more important.

Anyway ... 
If you connect the existing devices to a system running Ubuntu, I will propose some commands to begin gathering information. Facts are better than descriptions.  Facts come from running specific commands, with all relevant options shown and all output displayed. ZERO interpretation.  

Wrap all commands AND the output in forum 'code-tags', so things line up correctly. Otherwise it is just too hard to view, especially with all the columns these commands create.

Open any encryption container, if there is any first.
```
sudo vgchange -ay   # have the system scan for any LVM objects and make them seen.
sudo pvs
sudo vgs
sudo lvs
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

those commands should be enough to start.  However, if the encryption has been corrupted, get your backups ready. That's the only way to get any data back.
After seeing and digesting that output, I may have desire to see more details, but not yet.

You probably know much more about this than me, but perhaps bouncing some ideas will be helpful?

---

### Post by fst001 on 2022-07-12
> **TheFu said:**
> This feels a bunch like work (and I'm not being paid), so I won't be digging deep into the LVM details.  My only real skill in this is from using LVM 20+ yrs and having 80% of my data lost due to my stupidity about 20 yrs ago.  I've worked with storage teams before.  They can be both brilliant and have tightly focused views, since they may be managing hundreds of frames with tens of thousands of client servers and hundreds of thousands of physical and virtual disks.  I've also had failures due to the storage vendor SE oversimplifying how some advanced tools in their frames worked which turned out not to be true.


totally agree and yes i also know that i could have more carefull myself, but to be honest i didn't really thought about that they could have missed some volumes, but anyway i'd be grateful for each and every hint, because maybe someone else looks at this from a different angle. so let's try to find a way to recover it, because it's easier to get 10TB of data from tape instead of 110 :D.

there we go... all crypt disks are mounted
```
root@xxx:~# lsblk
NAME                    MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sda                       8:0    0   30G  0 disk
&#9500;&#9472;sda1                    8:1    0    1G  0 part
&#9474; &#9492;&#9472;LUKS_BOOT           253:3    0 1022M  0 crypt /boot
&#9500;&#9472;sda2                    8:2    0    2M  0 part
&#9500;&#9472;sda3                    8:3    0  128M  0 part
&#9492;&#9472;sda5                    8:5    0 28.9G  0 part
  &#9492;&#9472;sda5_crypt          253:0    0 28.9G  0 crypt
    &#9500;&#9472;ubuntu--vg-swap_1 253:1    0    4G  0 lvm   [SWAP]
    &#9492;&#9472;ubuntu--vg-root   253:2    0 19.9G  0 lvm   /
sdb                       8:16   0   10T  0 disk
&#9492;&#9472;sdb_crypt             253:5    0   10T  0 crypt
sdc                       8:32   0   10T  0 disk
&#9492;&#9472;sdc_crypt             253:6    0   10T  0 crypt
sdd                       8:48   0   10T  0 disk
&#9492;&#9472;sdd_crypt             253:7    0   10T  0 crypt
sde                       8:64   0   10T  0 disk
&#9492;&#9472;sde_crypt             253:8    0   10T  0 crypt
sdf                       8:80   0   10T  0 disk
&#9492;&#9472;sdf_crypt             253:9    0   10T  0 crypt
sdg                       8:96   0   10T  0 disk
&#9492;&#9472;sdg_crypt             253:10   0   10T  0 crypt
sdh                       8:112  0   10T  0 disk
&#9492;&#9472;sdh_crypt             253:4    0   10T  0 crypt
sdi                       8:128  0   10T  0 disk
&#9492;&#9472;sdi_crypt             253:11   0   10T  0 crypt
sdj                       8:144  0   10T  0 disk
&#9492;&#9472;sdj_crypt             253:12   0   10T  0 crypt
sdk                       8:160  0   10T  0 disk
&#9492;&#9472;sdk_crypt             253:14   0   10T  0 crypt
sdl                       8:176  0   10T  0 disk
&#9492;&#9472;sdl_crypt             253:13   0   10T  0 crypt
sr0                      11:0    1 1024M  0 rom
```

```
root@xxx:~# vgchange -ay
  0 logical volume(s) in volume group "FS00x_VG_DATA" now active
  2 logical volume(s) in volume group "ubuntu-vg" now active
```

```
root@xxx:~# pvs
  PV                     VG            Fmt  Attr PSize   PFree
  /dev/mapper/sda5_crypt ubuntu-vg     lvm2 a--   28.85g   4.97g
  /dev/mapper/sdb_crypt  FS00x_VG_DATA lvm2 a--  <10.00t <10.00t
  /dev/mapper/sdc_crypt  FS00x_VG_DATA lvm2 a--  <10.00t <10.00t
  /dev/mapper/sdd_crypt  FS00x_VG_DATA lvm2 a--  <10.00t <10.00t
  /dev/mapper/sde_crypt  FS00x_VG_DATA lvm2 a--  <10.00t <10.00t
  /dev/mapper/sdf_crypt  FS00x_VG_DATA lvm2 a--  <10.00t <10.00t
  /dev/mapper/sdg_crypt  FS00x_VG_DATA lvm2 a--  <10.00t <10.00t
  /dev/mapper/sdi_crypt  FS00x_VG_DATA lvm2 a--  <10.00t <10.00t
  /dev/mapper/sdj_crypt  FS00x_VG_DATA lvm2 a--  <10.00t <10.00t
  /dev/mapper/sdk_crypt  FS00x_VG_DATA lvm2 a--  <10.00t <10.00t
  /dev/mapper/sdl_crypt  FS00x_VG_DATA lvm2 a--  <10.00t <10.00t
```

```
root@xxx:~# vgs
  VG            #PV #LV #SN Attr   VSize    VFree
  FS00x_VG_DATA  10   0   0 wz--n- <100.00t <100.00t
  ubuntu-vg       1   2   0 wz--n-   28.85g    4.97g
```

lv does not show up since i tried to remove the missing disk with command: [COLOR=#000000][FONT=&amp]vgreduce --removemissing FS00x_VG_DATA[/FONT][/COLOR]

```
root@xxx:~# lvs
  LV     VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   ubuntu-vg -wi-ao---- <19.88g
  swap_1 ubuntu-vg -wi-ao----   4.00g
```

```
root@xxx:~# lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                     SIZE TYPE  FSTYPE      MOUNTPOINT
sda                       30G disk
&#9500;&#9472;sda1                     1G part  crypto_LUKS
&#9474; &#9492;&#9472;LUKS_BOOT           1022M crypt ext4        /boot
&#9500;&#9472;sda2                     2M part
&#9500;&#9472;sda3                   128M part  vfat
&#9492;&#9472;sda5                  28.9G part  crypto_LUKS
  &#9492;&#9472;sda5_crypt          28.9G crypt LVM2_member
    &#9500;&#9472;ubuntu--vg-swap_1    4G lvm   swap        [SWAP]
    &#9492;&#9472;ubuntu--vg-root   19.9G lvm   ext4        /
sdb                       10T disk  crypto_LUKS
&#9492;&#9472;sdb_crypt               10T crypt LVM2_member
sdc                       10T disk  crypto_LUKS
&#9492;&#9472;sdc_crypt               10T crypt LVM2_member
sdd                       10T disk  crypto_LUKS
&#9492;&#9472;sdd_crypt               10T crypt LVM2_member
sde                       10T disk  crypto_LUKS
&#9492;&#9472;sde_crypt               10T crypt LVM2_member
sdf                       10T disk  crypto_LUKS
&#9492;&#9472;sdf_crypt               10T crypt LVM2_member
sdg                       10T disk  crypto_LUKS
&#9492;&#9472;sdg_crypt               10T crypt LVM2_member
sdh                       10T disk  crypto_LUKS
&#9492;&#9472;sdh_crypt               10T crypt
sdi                       10T disk  crypto_LUKS
&#9492;&#9472;sdi_crypt               10T crypt LVM2_member
sdj                       10T disk  crypto_LUKS
&#9492;&#9472;sdj_crypt               10T crypt LVM2_member
sdk                       10T disk  crypto_LUKS
&#9492;&#9472;sdk_crypt               10T crypt LVM2_member
sdl                       10T disk  crypto_LUKS
&#9492;&#9472;sdl_crypt               10T crypt LVM2_member
sr0                     1024M rom
```

so sdh_crypt is the volume i tried to re-add to the vg but failed. in general i thought i had an easy lvm setup by simply adding 10TB raw devices and extending the volume by need, any way you would have done this a different way?

thanks so far for your assistence!

---

### Post by TheFu on 2022-07-12
You didn't use partitions on any of these devices?  For shame.  Some data recovery tools don't work if there aren't partitions.

Did you stripe the data (RAID0)  or just concatenate it?
If it was striped - it is gone, gone, gone.
For concatenated, let's just say that I did that and lost 80% of my data and never recovered any of it.  I could have wasted months with testdisk/photorec trying to recover stuff and I probably have those IDE disks on a shelf somewhere, waiting 20+ yrs later, but I obviously have lived without the data so far.

I did find this in an old RH LVM manual: [https://stuff.mit.edu/afs/athena/project/rhel-doc/5/RHEL-5-manual/en-US/Cluster_Logical_Volume_Manager.pdf](https://stuff.mit.edu/afs/athena/project/rhel-doc/5/RHEL-5-manual/en-US/Cluster_Logical_Volume_Manager.pdf)
> 4. Removing a Disk from a Logical Volume
 In order to remove a disk, you must first move the extents on the LVM physical volume to a different disk or set of disks.
In the troubleshooting section there are many commands for specific purposes.  Because LVM is LVM, I'm less concerned about RH vs Ubuntu and more concerned about 2005 vs 2022 versions of LVM.  Based on the first post, seems you may have already been following a similar troubleshooting guide.

If it was me, I'd start over clean and go with a slightly different setup. At this point time is better spent doing the restore, not seeking magic answers.  I don't allow any PV to be larger than 4TB and I don't span any LV across more than a single device.  That's what I learned from my lost data all those years ago.

Sorry, I'm not any help. I really wanted to have the commands say striped or concatenated.

---

### Post by fst001 on 2022-07-13
i only used LVM to get one big volume out of multiple "physical" disks, so no raid setup because the SAN backend is/was doing the raid. but ok then i'll start over. thanks anyway for your comments and help!

---

### Post by TheFu on 2022-07-13
> **fst001 said:**
> i only used LVM to get one big volume out of multiple "physical" disks, so no raid setup because the SAN backend is/was doing the raid. but ok then i'll start over. thanks anyway for your comments and help!

If the SAN is doing RAID for you, perhaps it can do BCVs too?  Then the restore would be nearly instantaneous while the BCV data is copied back to the primary SAN disks.  Of course, this assumes the SAN guys don't wipe the BCV data when the primaries are pulled.

---

### Post by fst001 on 2022-07-13
afaik it's an old storage that is/was just used for this kind of archive and can't do snapshots. so i'll simply restore and wait till it finishes :D

---

