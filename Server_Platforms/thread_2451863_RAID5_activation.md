---
title: "RAID5 activation"
date: 2020-10-12
forum: Server Platforms
---

### Post by helen314 on 2020-10-12
I am having issues activating RAID5 
Looks as "standard"  /dev/mdx  changed from md0 to md123 ,
 hence I really do not know to address the array.

Also gparted  doe snot show it as mounted , hence "File" d o not see it. 

I do not have any data in the array but would prefer to fix this instead of recreating the whole mess.

If I recall correctly there is a step, generally not covered in tutorials,
 one has to do to make sure the array is auto-mounted on boot.
( I am asking Mrs Google to help me find it ) 


[HTML]
  	 	 	 	   RAID5 issues  
 
 
 Build as md0  
 named  a-SATA:00
 label NEW_MD_00
 gparted “label “ is md123  
 “File” does not see it  
 it does not appear to be “mounted “ in gparted  
 
 
 
 
 a@a-SATA:~$ sudo su
 [sudo] password for a:  
 root@a-SATA:/home/a#  mdadm --detail /dev/md/a-SATA:00
 /dev/md/a-SATA:00:
         Version : 1.2
   Creation Time : Sun Oct 11 20:48:25 2020
      Raid Level : raid5
      Array Size : 204668928 (195.19 GiB 209.58 GB)
   Used Dev Size : 102334464 (97.59 GiB 104.79 GB)
    Raid Devices : 3
   Total Devices : 3
     Persistence : Superblock is persistent
 
 
     Update Time : Mon Oct 12 08:54:25 2020
           State : clean  
  Active Devices : 3
 Working Devices : 3
  Failed Devices : 0
   Spare Devices : 0
 
 
          Layout : left-symmetric
      Chunk Size : 512K
 
 
            Name : a-SATA:00  (local to host a-SATA)
            UUID : 49f4606c:d78a0b52:2e1386f4:25a96772

          Events : 742

 
 
     Number   Major   Minor   RaidDevice State
        0       8       77        0      active sync   /dev/sde13
        1       8       26        1      active sync   /dev/sdb10

        3     259       11        2      active sync   /dev/sdf24
 root@a-SATA:/home/a# 
   		p { margin-bottom: 0.1in; line-height: 120% }
[/HTML]

---

### Post by slickymaster on 2020-10-12
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2020-10-12
Post the output of the following:
```
cat /proc/mdstat
sudo blkid
cat /etc/mdadm/mdadm.conf
```

---

### Post by helen314 on 2020-10-12
Well, here it is…
 
 
 At this point I  am ONLY interested in activating .

 ARRAY /dev/md/a-SATA:00 metadata=1.2 name=a-SATA:00 UUID=49f4606c:d78a0b52:2e1386f4:25a96772
 
 
 For unknown reasons – I build md0 and now the numbers keep changing.  
 
 
 I am about to try it again from scratch , but like to know why they keep changing.
 
 
 NO, I cannot delete anything just ADD NEW for now.  
 
 
 \
 ```
a@a-SATA:~$ cat /etc/mdadm.conf
 INACTIVE-ARRAY /dev/md127 metadata=1.2 name=jim-desktop:0 UUID=5afe531e:3c41ecd9:7057ae6e:98985049
 INACTIVE-ARRAY /dev/md126 metadata=1.2 name=z-desktop:1 UUID=2fcd6c3c:7536faa9:8eb26bcd:31243bf7
 ARRAY /dev/md/a-desktop:2 metadata=1.2 spares=2 name=a-desktop:2 UUID=3c054983:7f097201:ea7c71b7:63b6933d
 INACTIVE-ARRAY /dev/md124 metadata=1.2 name=a-desktop:4 UUID=de0c780d:10ebec5f:e4121455:e7280163
 **ARRAY /dev/md/a-SATA:00 metadata=1.2 name=a-SATA:00 UUID=49f4606c:d78a0b52:2e1386f4:25a96772**
 ARRAY /dev/md/a-desktop:3 metadata=1.2 name=a-desktop:3 UUID=92ea9b2e:5f6d6f5c:34b3efe6:42fb5617
 ARRAY /dev/md/b-backup:20 metadata=1.2 spares=1 name=b-backup:20 UUID=864cf55c:b312276f:fdf947c1:ed78a988
 a@a-SATA:~$  
```
 ```
 @a-SATA:~$ cat /etc/mdadm/mdadm.conf
 # mdadm.conf
 #
 # Please refer to mdadm.conf(5) for information about this file.
 #
 
 
 # by default (built-in), scan all partitions (/proc/partitions) and all
 # containers for MD superblocks. alternatively, specify devices to scan, using
 # wildcards if desired.
 #DEVICE partitions containers
 
 
 # auto-create devices with Debian standard permissions
 CREATE owner=root group=disk mode=0660 auto=yes
 
 
 # automatically tag new arrays as belonging to the local system
 HOMEHOST <system>
 
 
 # instruct the monitoring daemon where to send mail alerts
 MAILADDR root
 
 
 # definitions of existing MD arrays
 
 
 # This file was auto-generated on Sun, 11 Oct 2020 18:38:00 -0500
 # by mkconf $Id$
```
 ```
[sudo] password for a:  
 /dev/sda1: UUID="50D6-C4E8" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="4f929080-5b02-4d52-a717-efffff17ed13"
 /dev/sda2: UUID="0908c266-4230-47bd-8616-d4b449666681" TYPE="ext4" PARTUUID="e4a93374-c613-439e-b4ea-31bf0adb4a9a"
 /dev/sda3: UUID="90d3460f-451c-4bcb-af1f-c233953efaa1" TYPE="swap" PARTUUID="d204d8b6-727d-4d7b-b4d8-a2f6c8f06b94"
 /dev/sda4: UUID="5afe531e-3c41-ecd9-7057-ae6e98985049" UUID_SUB="f61c15f1-41fc-5354-02a9-08eec56ccd93" LABEL="jim-desktop:0" TYPE="linux_raid_member" PARTLABEL="RAID" PARTUUID="a363cefa-ff3c-4d73-bb44-033430eb76da"
 /dev/sda5: UUID="d472b935-9961-4621-b3df-346383dcd220" TYPE="ext4" PARTUUID="6d428254-682d-46a1-9ef7-dec88eb45c3b"
 /dev/sda6: UUID="5afe531e-3c41-ecd9-7057-ae6e98985049" UUID_SUB="e889dd68-1c89-188c-83b2-82e41ece5d63" LABEL="jim-desktop:0" TYPE="linux_raid_member" PARTLABEL="RAID_ADD" PARTUUID="f4edb7ba-b24f-4e3a-bb69-f3ac04ceecbf"
 /dev/sdb1: LABEL="Photo Album SATA" UUID="00FCC333FCC321B0" TYPE="ntfs" PARTUUID="c523b2bd-01"
 /dev/sdb5: LABEL="Programs SATA" UUID="EC2C214A2C21115E" TYPE="ntfs" PARTUUID="c523b2bd-05"
 /dev/sdb6: LABEL="OpenCameraB" UUID="EED447FDD447C695" TYPE="ntfs" PARTUUID="c523b2bd-06"
 /dev/sdb7: LABEL="Ex Drive Co" UUID="2600E4F800E4D03B" TYPE="ntfs" PARTUUID="c523b2bd-07"
 /dev/sdb8: UUID="08c450c1-580d-4a28-ab8a-5e7ee20c61bd" TYPE="swap" PARTUUID="c523b2bd-08"
 /dev/sdb9: UUID="2fcd6c3c-7536-faa9-8eb2-6bcd31243bf7" UUID_SUB="02061127-2ab6-d552-5d66-88e2f5f87a62" LABEL="z-desktop:1" TYPE="linux_raid_member" PARTUUID="c523b2bd-09"
 /dev/sdb10: UUID="49f4606c-d78a-0b52-2e13-86f425a96772" UUID_SUB="2de7905a-33a0-4d43-ac8d-5489dd12195d" LABEL="a-SATA:00" TYPE="linux_raid_member" PARTUUID="c523b2bd-0a"
 /dev/sdc1: UUID="87e75dcc-989b-45f5-9fbd-50f66871a275" TYPE="ext4" PARTUUID="76197791-01"
 /dev/sdc3: UUID="5afe531e-3c41-ecd9-7057-ae6e98985049" UUID_SUB="54ff9a0e-ee53-7f1d-5ce8-7f76e3524862" LABEL="jim-desktop:0" TYPE="linux_raid_member" PARTUUID="76197791-03"
 /dev/sdc4: UUID="d6105472-f275-44e1-8510-0b04aaa6c648" TYPE="ext4" PARTUUID="76197791-04"
 /dev/sdc5: UUID="ed875091-53e8-45e7-b90b-baed276ca7cc" TYPE="swap" PARTUUID="76197791-05"
 /dev/sdc6: LABEL="OS" UUID="d9001fae-357d-4b21-aa25-5f25cab3e673" TYPE="ext4" PARTUUID="76197791-06"
 /dev/sdd1: UUID="CDBE-1CA9" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="db6b86b5-a4cc-4395-a80a-f2a4e652586a"
 /dev/sdd2: UUID="D6E9-0180" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="44c98307-eb14-4cd8-ab7e-3138193729a1"
 /dev/sdd3: UUID="357de9dc-1696-40db-927a-6d258aa135d7" TYPE="swap" PARTUUID="20686abe-2a33-4ed0-8064-8a62b60ce537"
 /dev/sdd4: LABEL="OS" UUID="37a90d1a-aca6-4097-95e2-12265c43b05b" TYPE="ext4" PARTLABEL="OS" PARTUUID="3c5bf40c-0302-46d6-bb8d-4970ad250a40"
 /dev/sdd5: LABEL="Photo Album" UUID="00FCC333FCC321B0" TYPE="ntfs" PARTLABEL="PHOTO_COPY" PARTUUID="ea4383cf-e6ba-4f3a-a04d-2905e3a51550"
 /dev/sdd6: UUID="dae12eb3-dd41-4262-98c3-83b3f9f8501c" TYPE="ext4" PARTUUID="e6666bf9-9501-4785-80dd-5741cd1dedfa"
 /dev/md125p1: LABEL="NEW_MD_00" UUID="04893c76-3018-4414-90af-bbd15646e1e8" TYPE="ext4" PARTLABEL="NEW_MD_00" PARTUUID="2f38c6f7-0079-48aa-b40a-b91cd3e26a9a"
 /dev/sde1: UUID="DBC2-3097" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="7149cebc-a872-4fa7-bf45-e75ea1672895"
 /dev/sde2: UUID="36b009b5-8af9-4d2a-b1ff-fda9432bb4c6" TYPE="ext4" PARTLABEL="OS" PARTUUID="81e74e90-d97e-4e90-94a9-9202874a386b"
 /dev/sde3: UUID="ab1a8eeb-e052-4bb6-92b6-4a8177c64aa0" TYPE="swap" PARTUUID="27b694ac-fdcc-43c2-a5c0-4232c8b8c897"
 /dev/sde4: UUID="3c054983-7f09-7201-ea7c-71b763b6933d" UUID_SUB="c3c3a513-7d41-75ac-402e-7a034d812f7f" LABEL="a-desktop:2" TYPE="linux_raid_member" PARTLABEL="RAID_MD_2" PARTUUID="d056eb7a-907d-4116-9778-6350558ac2d6"
 /dev/sde5: UUID="3c054983-7f09-7201-ea7c-71b763b6933d" UUID_SUB="75b119d9-3834-72cb-76c0-6d67e06d1bce" LABEL="a-desktop:2" TYPE="linux_raid_member" PARTLABEL="RAID_MD_2" PARTUUID="1f14e175-8612-4502-81c0-ef18af3f3ae9"
 /dev/sde6: UUID="64ff8813-f1b8-45ce-9d26-5c0162276335" TYPE="ext4" PARTUUID="41f52b07-f271-4c46-9dad-d27fa652e3f4"
 /dev/sde7: UUID="dec1667d-ed37-47ba-9887-b2d645a2ba70" TYPE="ext4" PARTUUID="93f71a1c-51ce-4cc2-9bf8-7c6e44797537"
 /dev/sde8: LABEL="BOOT" UUID="4d9df079-5662-4b63-a428-ccae4ae36650" TYPE="ext4" PARTLABEL="BOOT" PARTUUID="1f7e3d4f-888f-4716-bad8-e3ee4e353ef7"
 /dev/sde9: UUID="2fcd6c3c-7536-faa9-8eb2-6bcd31243bf7" UUID_SUB="5df337cb-4b34-1fbe-de6c-5f773b1e48dc" LABEL="z-desktop:1" TYPE="linux_raid_member" PARTLABEL="TEST_RAID_3" PARTUUID="a1f05e6b-2bef-474a-b2b1-26d73100a600"
 /dev/sde10: LABEL="Photo Album" UUID="00FCC333FCC321B0" TYPE="ntfs" PARTLABEL="PHOTO_COPY" PARTUUID="66537b42-4255-4eef-886f-7f0d54024f1f"
 /dev/sde11: UUID="3c054983-7f09-7201-ea7c-71b763b6933d" UUID_SUB="3ba50675-b7cb-81a7-1a81-d2ff440ee54e" LABEL="a-desktop:2" TYPE="linux_raid_member" PARTLABEL="RAID_MD_2" PARTUUID="87f3c88a-97de-4dcb-b975-72867380a9be"
 /dev/sde12: LABEL="REsume" UUID="2808D1BB08D187E8" TYPE="ntfs" PARTLABEL="OLD_RESUME" PARTUUID="eaa6938b-2fda-41b8-a307-6eaa95e594e4"
 /dev/sde13: UUID="49f4606c-d78a-0b52-2e13-86f425a96772" UUID_SUB="d26f40dd-c068-2ad1-b308-4e0e320fcd6a" LABEL="a-SATA:00" TYPE="linux_raid_member" PARTLABEL="NEW_MD_00" PARTUUID="ca40555a-973a-4f61-ac06-649f8bd69904"
 /dev/sde16: UUID="de0c780d-10eb-ec5f-e412-1455e7280163" UUID_SUB="efda29fa-2eb0-4d7b-be6a-947cf10bfbe5" LABEL="a-desktop:4" TYPE="linux_raid_member" PARTLABEL="TEST" PARTUUID="f7137d60-56d5-4bcb-be0d-e924c10c5bb0"
 /dev/sde17: UUID="3c054983-7f09-7201-ea7c-71b763b6933d" UUID_SUB="5afd7295-65cd-865d-09d7-da7fcd2bc8e8" LABEL="a-desktop:2" TYPE="linux_raid_member" PARTUUID="cf0ab13e-f644-4e66-a68b-f171999d0fbc"
 /dev/sde18: UUID="3c054983-7f09-7201-ea7c-71b763b6933d" UUID_SUB="bacd05d8-a498-29ad-de73-8debc40eb260" LABEL="a-desktop:2" TYPE="linux_raid_member" PARTUUID="24346bb5-437b-48cb-8c68-9cb73279f8b4"
 /dev/sdf1: LABEL="Photo Album" UUID="00FCC333FCC321B0" TYPE="ntfs" PARTUUID="c523b2bd-01"
 /dev/sdf3: LABEL="ISO" UUID="9cc8ef26-d044-4b92-a66c-9da17e8da44f" TYPE="ext4" PARTUUID="c523b2bd-03"
 /dev/sdf5: LABEL="Programs" UUID="EC2C214A2C21115E" TYPE="ntfs" PARTUUID="c523b2bd-05"
 /dev/sdf6: LABEL="OpenCameraB" UUID="EED447FDD447C695" TYPE="ntfs" PARTUUID="c523b2bd-06"
 /dev/sdf7: LABEL="Ex Drive Co" UUID="2600E4F800E4D03B" TYPE="ntfs" PARTUUID="c523b2bd-07"
 /dev/sdf8: UUID="0822C8912019FFC8" TYPE="ntfs" PARTUUID="c523b2bd-08"
 /dev/sdf9: LABEL="WorkspaceRaspber" UUID="dbbd0cc9-1a8b-4844-a600-cbf501f7333c" TYPE="ext4" PARTUUID="c523b2bd-09"
 /dev/sdf10: LABEL="Eclipse" UUID="e90127fc-3eb5-48a9-863c-fe06f0fe4b0e" TYPE="ext4" PARTUUID="c523b2bd-0a"
 /dev/sdf11: LABEL="Alternate downlo" UUID="1bddecf0-83f9-4723-8f38-5bdf85141f61" TYPE="ext4" PARTUUID="c523b2bd-0b"
 /dev/sdf12: UUID="92ea9b2e-5f6d-6f5c-34b3-efe642fb5617" UUID_SUB="fb1ce9a4-47a7-b3aa-d56b-895274c52608" LABEL="a-desktop:3" TYPE="linux_raid_member" PARTUUID="c523b2bd-0c"
 /dev/sdf13: UUID="92ea9b2e-5f6d-6f5c-34b3-efe642fb5617" UUID_SUB="05b2de7b-8e5f-0c19-1482-62cca4ff2fc7" LABEL="a-desktop:3" TYPE="linux_raid_member" PARTUUID="c523b2bd-0d"
 /dev/sdf14: UUID="92ea9b2e-5f6d-6f5c-34b3-efe642fb5617" UUID_SUB="bb0c1fa9-e932-85d4-fa43-69c53e8a73c5" LABEL="a-desktop:3" TYPE="linux_raid_member" PARTUUID="c523b2bd-0e"
 /dev/sdf15: LABEL="QT" UUID="b8cd38cb-733a-446d-a6e1-dd3f45629c6d" TYPE="ext4" PARTUUID="c523b2bd-0f"
 /dev/sdf16: UUID="bdab9244-d5f1-4d5d-8ee6-c0e891a5ceb7" TYPE="ext4" PARTUUID="c523b2bd-10"
 /dev/sdf17: UUID="EB4A-7A61" TYPE="vfat" PARTUUID="c523b2bd-11"
 /dev/sdf18: UUID="6a707b8c-f7f4-4c89-b737-a99edf1d595a" TYPE="ext4" PTTYPE="dos" PARTUUID="c523b2bd-12"
 /dev/sdf19: UUID="fba73f1c-d67b-4f11-88e7-e966c7cddd9a" TYPE="swap" PARTUUID="c523b2bd-13"
 /dev/sdf20: UUID="864cf55c-b312-276f-fdf9-47c1ed78a988" UUID_SUB="9e306b67-e117-8292-9457-07a5e4065399" LABEL="b-backup:20" TYPE="linux_raid_member" PARTUUID="c523b2bd-14"
 /dev/sdf21: UUID="864cf55c-b312-276f-fdf9-47c1ed78a988" UUID_SUB="9ba5bcf0-7630-0d13-b366-86d9e7ca849b" LABEL="b-backup:20" TYPE="linux_raid_member" PARTUUID="c523b2bd-15"
 /dev/sdf22: UUID="864cf55c-b312-276f-fdf9-47c1ed78a988" UUID_SUB="08ca6938-5565-40c1-ac2a-d40f4149f75c" LABEL="b-backup:20" TYPE="linux_raid_member" PARTUUID="c523b2bd-16"
 /dev/sdf23: LABEL="NEW_RAID_MD5" UUID="8503c859-8c86-4513-b8ce-1fd38e78f1f0" TYPE="ext4" PARTUUID="c523b2bd-17"
 /dev/sdf24: UUID="49f4606c-d78a-0b52-2e13-86f425a96772" UUID_SUB="963e71cf-2773-7171-2039-62ae7bfe0cea" LABEL="a-SATA:00" TYPE="linux_raid_member" PARTUUID="c523b2bd-18"
 /dev/md124p1: LABEL="BACK_MD3" UUID="d2af4a0a-ecaa-48bc-a80c-5dae8b20e5af" TYPE="ext4" PARTLABEL="BACK_MD3" PARTUUID="aab196a9-b06c-4ecc-a5a6-69f0908a4954"
 /dev/md124p3: LABEL="DEV_MD3" UUID="506d7ca6-b09c-415b-a681-f7f71ec62513" TYPE="ext4" PARTLABEL="DEV_MD3" PARTUUID="d053ce77-69c3-49f0-b5b7-b33016a82793"
 /dev/md124p5: LABEL="DOC_MD3" UUID="92f91148-a6dd-4d06-9276-83ba2e39ec07" TYPE="ext4" PARTLABEL="DOC_MD3" PARTUUID="92fe3bcd-193a-493d-845f-32579b40aa85"
 /dev/md124p8: LABEL="MISC_COPY_MD3" UUID="922f42e6-6ab1-4cd0-bc82-2aee9868187f" TYPE="ext4" PARTLABEL="MISC_COPY_MD3" PARTUUID="123d8216-6aff-4c16-8c44-8222007d1809"
 /dev/md122p1: LABEL="ECLIPSE_BACKUP" UUID="92f91148-a6dd-4d06-9276-83ba2e39ec07" TYPE="ext4" PARTUUID="6a551d9f-01"
 /dev/md122p2: LABEL="DEV_MD2" UUID="506d7ca6-b09c-415b-a681-f7f71ec62513" TYPE="ext4" PARTUUID="6a551d9f-02"
 /dev/md122p3: LABEL="MISC_MD2" UUID="922f42e6-6ab1-4cd0-bc82-2aee9868187f" TYPE="ext4" PARTUUID="6a551d9f-03"
 /dev/md122p4: LABEL="BACK_TEMP_MD2" UUID="d2af4a0a-ecaa-48bc-a80c-5dae8b20e5af" TYPE="ext4" PARTUUID="6a551d9f-04"
 /dev/md125: PTUUID="3ffad94c-de65-4e98-a055-266fa622d366" PTTYPE="gpt"
 /dev/md124: PTUUID="14847c7f-025c-4ad2-9987-f3b55a4c3f04" PTTYPE="gpt"
 /dev/md122: PTUUID="6a551d9f" PTTYPE="dos"
 a@a-SATA:~$  
```
 ```
a@a-SATA:~$ cat /proc/mdstat
 Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
 md121 : active (auto-read-only) raid5 sdf21[1] sdf22[3] sdf20[0]
       204668928 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [UU_]
        
 md122 : active raid5 sde17[4](S) sde5[1] sde18[5](S) sde4[0] sde11[3]
       204668928 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
        
 md123 : inactive sde16[4](S)
       84130816 blocks super 1.2
         
 md124 : active (auto-read-only) raid5 sdf14[3] sdf13[1] sdf12[0]
       204668928 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
        
 [B]md125 : active raid5 sdf24[3] sde13[0] sdb10[1]
       204668928 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
        [/B]
 md126 : inactive sde9[3](S) sdb9[4](S)
       204668928 blocks super 1.2
         
 md127 : inactive sda6[3](S) sda4[1](S) sdc3[0](S)
       418872320 blocks super 1.2
         
 unused devices: <none>
 a@a-SATA:~$
```

---

### Post by darkod on 2020-10-12
In your /etc/mdadm/mdadm.conf add the following line in the section "definition of arrays":
```
ARRAY /dev/md0  metadata=1.2  UUID=49f4606c:d78a0b52:2e1386f4:25a96772
```

That should make it autoassemble on boot. In any case, when mounting try to use the UUID of the filesystem (NOT the array, they are not the same) instead of /dev/md0. That way you don't really care if it changes the mdX device name.

Another thing, I see many /dev/mdXpY in your blkid output. Arrays are not intended to be partitioned, yet it seems you are creating partitions on them. Each array should be made of partitions with the size you need, and you format and use the array as such. You don't partition it.

---

