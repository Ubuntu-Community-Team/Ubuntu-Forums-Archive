---
title: "[SOLVED] Can't change file's owner from root to me"
date: 2008-12-24
forum: Security
---

### Post by Milt15 on 2008-12-24
while i am in the directory of my storage I accidentally did the sudo su command
so now almost all my file's owner and group is root

 ```
milt15@DELL:~$ cd /media/DISK_VOL2/
milt15@DELL:/media/DISK_VOL2$ sudo chown milt15 ./Acadimic/
[sudo] password for milt15: 
Sorry, try again.
[sudo] password for milt15: 
chown: changing ownership of `./Acadimic/': Operation not permitted
milt15@DELL:/media/DISK_VOL2$ sudo chgrp milt15 ./Acadimic/
chgrp: changing group of `./Acadimic/': Operation not permitted
milt15@DELL:/media/DISK_VOL2$ sudo chown root ./Acadimic/
milt15@DELL:/media/DISK_VOL2$ sudo chgrp root ./Acadimic/
milt15@DELL:/media/DISK_VOL2$ 

```

As you see i can't change the dir Acadimic (and also the rest of my files and subdirectories ) owner to me but I can change it to root (which is no changing since the owner was root before chown root )

any ideas ?

---

### Post by ranch hand on 2008-12-24
Remember that changing ownership is generally a BAD thing.

Try sudo nautilus.

---

### Post by Sarmacid on 2008-12-24
Try doing it recursively with the -R flag, and don't use the ./ just the folder name.

---

### Post by Milt15 on 2008-12-24
```
milt15@DELL:/media/Milt15$ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:18302): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///root

(nautilus:18302): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:18302): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
Shutting down nautilus-share extension
seahorse nautilus module shutdown
milt15@DELL:/media/Milt15$ 


```

```
milt15@DELL:/media/DISK_VOL2$ sudo chown -R milt15  ./img/
chown: changing ownership of `./img/01197_tiles_2560x1600.jpg': Operation not permitted
chown: changing ownership of `./img/028JwS340271-02.jpg': Operation not permitted
chown: changing ownership of `./img/0a1.jpg': Operation not permitted
chown: changing ownership of `./img/1.jpg': Operation not permitted
chown: changing ownership of `./img/1666061064_29e7a2cb94_o.jpg': Operation not permitted
chown: changing ownership of `./img/1LSlqS651299-02.jpg': Operation not permitted
chown: changing ownership of `./img/2001869738701889745_rs.jpg': Operation not permitted
chown: changing ownership of `./img/2001872001897486861_rs.jpg': Operation not permitted
chown: changing ownership of `./img/2001874491140419479_rs.jpg': Operation not permitted
chown: changing ownership of `./img/2001887438742008512_rs.jpg': Operation not permitted
chown: changing ownership of `./img/2006002210041195037_rs.jpg': Operation not permitted
chown: changing ownership of `./img/2006005206140422677_rs.jpg': Operation not permitted
chown: changing ownership of `./img/2006022330916588636_rs.jpg': Operation not permitted
chown: changing ownership of `./img/2006041639786315215_rs.jpg': Operation not permitted
chown: changing ownership of `./img/2006074915607923683_rs.jpg': Operation not permitted
chown: changing ownership of `./img/2006076019463670806_rs.jpg': Operation not permitted
chown: changing ownership of `./img/2006083010266282206_rs.jpg': Operation not permitted
chown: changing ownership of `./img/2006091179798261071_rs.jpg': Operation not permitted
chown: changing ownership of `./img/2036297833_db8cd7cefc_o.jpg': Operation not permitted
chown: changing ownership of `./img/2279624506_2ee2115655_o.jpg': Operation not permitted
chown: changing ownership of `./img/23.jpg': Operation not permitted
chown: changing ownership of `./img/2478143660_7b496d4018_o.png': Operation not permitted
chown: changing ownership of `./img/2gED85rOzd.jpg': Operation not permitted
chown: changing ownership of `./img/3.jpg': Operation not permitted
chown: changing ownership of `./img/321.jpg': Operation not permitted
chown: changing ownership of `./img/3423.jpg': Operation not permitted
chown: changing ownership of `./img/432.jpg': Operation not permitted
chown: changing ownership of `./img/543.jpg': Operation not permitted
chown: changing ownership of `./img/56.jpg': Operation not permitted
chown: changing ownership of `./img/566.jpg': Operation not permitted
chown: changing ownership of `./img/654.jpg': Operation not permitted
chown: changing ownership of `./img/6aY3iz453856-02.gif': Operation not permitted
chown: changing ownership of `./img/770SPz781924-02.jpg': Operation not permitted
chown: changing ownership of `./img/90215210jvwgkoptbugfv2kic1.gif': Operation not permitted
chown: changing ownership of `./img/9lQJOk422301-02.jpg': Operation not permitted
chown: changing ownership of `./img/animals_wolves_003_3.jpg': Operation not permitted
chown: changing ownership of `./img/anime_71.jpg': Operation not permitted
chown: changing ownership of `./img/aviation_001_3.jpg': Operation not permitted
chown: changing ownership of `./img/aviation_002.jpg': Operation not permitted
chown: changing ownership of `./img/aviation_004_3.jpg': Operation not permitted
chown: changing ownership of `./img/aviation_005_3.jpg': Operation not permitted
chown: changing ownership of `./img/basketball_horse.swf': Operation not permitted
chown: changing ownership of `./img/beaches_004_2.jpg': Operation not permitted
chown: changing ownership of `./img/beaches_005_2.jpg': Operation not permitted
chown: changing ownership of `./img/beaches_007_3.jpg': Operation not permitted
chown: changing ownership of `./img/beaches_017_2.jpg': Operation not permitted
chown: changing ownership of `./img/bird_1_1.jpg': Operation not permitted
chown: changing ownership of `./img/boomboom.swf': Operation not permitted
chown: changing ownership of `./img/CaNJdr427220-02.bmp': Operation not permitted
chown: changing ownership of `./img/cars_audi_003_3.jpg': Operation not permitted
chown: changing ownership of `./img/cars_audi_009_3.jpg': Operation not permitted
chown: changing ownership of `./img/cars_audi_013_3.jpg': Operation not permitted
chown: changing ownership of `./img/cartoons_naruto_002_3.jpg': Operation not permitted
chown: changing ownership of `./img/cpvCpK677579-02.jpg': Operation not permitted
chown: changing ownership of `./img/crazy_flasher_4.swf': Operation not permitted
chown: changing ownership of `./img/d.jpg': Operation not permitted
chown: changing ownership of `./img/d47Cfy984653-02.jpg': Operation not permitted
chown: changing ownership of `./img/encountered_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/engrenagem_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/ExdpeF813071-02.jpg': Operation not permitted
chown: changing ownership of `./img/Exotic_Flower2a_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/EXSHIT_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/find_by_Test_4.jpg': Operation not permitted
chown: changing ownership of `./img/flight_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/floe_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/floral_escuro_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/flowers_001_3.jpg': Operation not permitted
chown: changing ownership of `./img/flowers_032_3.jpg': Operation not permitted
chown: changing ownership of `./img/fogo_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/game_129ff270109809e4b2b782bc65852085.swf': Operation not permitted
chown: changing ownership of `./img/game_502.swf': Operation not permitted
chown: changing ownership of `./img/garibaldi_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/Girl3_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/graphic1_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/gun1_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/holidays_christmas_001_3.jpg': Operation not permitted
chown: changing ownership of `./img/holidays_christmas_002.jpg': Operation not permitted
chown: changing ownership of `./img/holidays_christmas_003_2.jpg': Operation not permitted
chown: changing ownership of `./img/hotornotback.gif': Operation not permitted
chown: changing ownership of `./img/HwoUkX059609-02.jpg': Operation not permitted
chown: changing ownership of `./img/image002.jpg': Operation not permitted
chown: changing ownership of `./img/image022.jpg': Operation not permitted
chown: changing ownership of `./img/laminas_noturnas_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/lol_code_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/malted_lace_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/marx_by_Test.jpg': Operation not permitted
chown: changing ownership of `./img/matematica_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/meio_tom_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/metallic_pose_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/mickey_mouse_6.jpg': Operation not permitted
chown: changing ownership of `./img/m_c_escher_by_Test_2.jpg': Operation not permitted
chown: changing ownership of `./img/nature_001_3.jpg': Operation not permitted
chown: changing ownership of `./img/nature_008_2.jpg': Operation not permitted
chown: changing ownership of `./img/nature_014_2.jpg': Operation not permitted
chown: changing ownership of `./img/p959Aj870644-02.jpg': Operation not permitted
chown: changing ownership of `./img/portal_the_flash_version.swf': Operation not permitted
chown: changing ownership of `./img/prototype.js,scriptaculous.js,effects.js,custom.js,modalbox.js,menu.js,prototip.js': Operation not permitted
chown: changing ownership of `./img/rTZOZO248744-02.gif': Operation not permitted
chown: changing ownership of `./img/s.jpg': Operation not permitted
chown: changing ownership of `./img/sonny.swf': Operation not permitted
chown: changing ownership of `./img/Stick-gesamt_100x100.jpg': Operation not permitted
chown: changing ownership of `./img/strategy_defense_5.swf': Operation not permitted
chown: changing ownership of `./img/tacass.swf': Operation not permitted
chown: changing ownership of `./img/xLUd.h851562-02.jpg': Operation not permitted
chown: changing ownership of `./img/Year.bmp': Operation not permitted
chown: changing ownership of `./img/YoLinux_logo.png': Operation not permitted
chown: changing ownership of `./img/Wiki images/166px-Incandescence.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/171px-Early_flight_02561u_(4).jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/176px-Haeckel_Spumellaria.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/187px-Joan_of_Arc-Notre_Dame.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/188px-Washington_Monument_Dusk_Jan_2006.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/189px-Yellow-rattle_close_700.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/198px-Mahdist_in_the_Khalifa\'s_house,_Omdurman,_Sudan.png': Operation not permitted
chown: changing ownership of `./img/Wiki images/200px-Divers_-_Illustrated_London_News_Feb_6_1873-2.PNG': Operation not permitted
chown: changing ownership of `./img/Wiki images/200px-USA_10096-7-8_HDR_Antelope_Canyon_Luca_Galuzzi_2007.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/247px-Cuban_missiles.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/248px-Apollo_11_bootprint.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/250px-NASA-Apollo8-Dec24-Earthrise.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/290px-World_Map_1689.JPG': Operation not permitted
chown: changing ownership of `./img/Wiki images/333px-Lion_waiting_in_Nambia.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/333px-Mandel_zoom_07_satellite.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/333px-Mandel_zoom_10_satellite_seehorse_valley.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/354px-Moons_of_solar_system_v7.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/373px-Eyjafjallaj\366kull.jpeg': Operation not permitted
chown: changing ownership of `./img/Wiki images/373px-Seagull_on_sale_pier.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/375px-Anser_cygnoides.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/375px-Salad_platter.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/375px-Two_Gannets_edit_2.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/376px-St_Vitus_stained_glass.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/379px-STS-116_spacewalk_1.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/388px-Mark_48_Torpedo_testing.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/400px-Incandescence.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/417px-SeattleI5Skyline.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/424px-Grapevinesnail_01.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/438px-Coyote_portrait.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/451px-Washington_Monument_Dusk_Jan_2006.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/500px-Global_tropical_cyclone_tracks-edit2.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/655px-Yarra_Night_Panorama,_Melbourne_-_Feb_2005.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/800px-Anser_cygnoides.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/800px-Mandel_zoom_10_satellite_seehorse_valley.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/800px-Mark_48_Torpedo_testing.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/800px-Moons_of_solar_system_v7.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/Globe_panorama03.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/Incandescence.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/Indian_pigments.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/Romanian_hay.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/Round_hay_bale_at_dawn02.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/Static_jump.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images/Thistlegorm_train_parts_minus_red_edit.jpg': Operation not permitted
chown: changing ownership of `./img/Wiki images': Operation not permitted
chown: changing ownership of `./img/': Operation not permitted
milt15@DELL:/media/DISK_VOL2$ 


```

---

### Post by sisco311 on 2008-12-24
what file system type is on the partition?

post the output of:
```
mount
```

---

### Post by Milt15 on 2008-12-24
the one with DISK_VOL2 is FAT32 and the other one is external ntfs
and when I do the mount command it tells me it is already mounted

---

### Post by ibutho on 2008-12-24
AFAIK changing file ownership on an an FAT32 partition or drive from within Linux does not work although changing permissions does.

---

### Post by Milt15 on 2008-12-24
well the problem to me is that to do anything i will have to do it from terminal as sudo ---- 
and with programs that i want to write to the file execution in root doesn't use my settings and files

so if I can solve this without changing the owner that would be also great

and when I was in sudo nautilus and opened GUI file browser when I go to file properties and change the file permission from read to read and write or from access only to create and delete it comes back fast to read only and access only

---

### Post by cariboo on 2008-12-24
You can just change the permissions on all the files in the directory by typing in a terminal:

```
sudo chmod -R 777 ./img
```

THis will recursivly change all the permissions to world read/write.

Jim

---

### Post by sisco311 on 2008-12-24
> **Milt15 said:**
> the one with DISK_VOL2 is FAT32 and the other one is external ntfs
and when I do the mount command it tells me it is already mounted

you can set the permissions and owner at mount time.
how did you mount the partitions?


please post:
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
```

in the fstab you need to add a new entry(or modify the old):
```
UUUID=<uuid of the partition> /media/mount-point type(vfat or ntfs) default,umask=002,gid=46 0 0
```

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by Milt15 on 2008-12-24
I did the 

```
milt15@DELL:~$ cd /media/DISK_VOL2/
milt15@DELL:/media/DISK_VOL2$ sudo chmod -R 777 ./
[sudo] password for milt15: 
milt15@DELL:/media/DISK_VOL2$ 

```

but permissions wasn't changed

and the I made the partition mount automatically (by changing noauto option to auto at the fstab )

```
milt15@DELL:/media/DISK_VOL2$ sudo fdisk -l
[sudo] password for milt15: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe095e095

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3649    29310561   83  Linux
/dev/sda2            3650       13799    81529875    f  W95 Ext'd (LBA)
/dev/sda5            3650        7298    29310561    b  W95 FAT32
/dev/sda6            7299       10947    29310561    b  W95 FAT32
/dev/sda7           10948       11194     1983996   82  Linux swap / Solaris
/dev/sda8   *       11195       12110     7357738+  83  Linux
/dev/sda9           12111       12749     5132736   83  Linux
/dev/sda10          12750       13397     5205028+  83  Linux
/dev/sda11          13398       13799     3229033+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c72f654

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS
milt15@DELL:/media/DISK_VOL2$ sudo blkid
/dev/sda1: LABEL="ST" UUID="e945adcf-5052-4d08-82ab-82125a67777e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: LABEL="DISK1_VOL2" UUID="71BF-EC69" TYPE="vfat" 
/dev/sda6: LABEL="DISK1_VOL3" UUID="753E-696B" TYPE="vfat" 
/dev/sda7: TYPE="swap" UUID="5dde72da-f7a4-4262-baf5-5284bd401891" 
/dev/sda8: UUID="a6bf3160-969c-43ac-bd22-27a81b66f9b0" TYPE="ext3" 
/dev/sda9: UUID="d3b84434-8d52-4693-b44e-653cb1294947" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: LABEL="Dreamlinux" UUID="f40b284f-055f-4d7e-b2fb-7f82888ee1a9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: UUID="019f0173-e0e6-4a68-8367-0c654e15d28b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="F64CA0F34CA0B033" LABEL="Milt15" TYPE="ntfs" 
/dev/sdc: UUID="CCDD-2A41" TYPE="vfat" 
milt15@DELL:/media/DISK_VOL2$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=a6bf3160-969c-43ac-bd22-27a81b66f9b0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=5dde72da-f7a4-4262-baf5-5284bd401891 none            swap    sw              0       0
# /dev/sda5, size=58621122, type=11: FAT32 (extended)
/dev/sda5 /media/DISK_VOL2 vfat user,exec,rw,auto
# /dev/sda6, size=58621122, type=11: FAT32 (extended)
/dev/sda6 /media/DISK_VOL3 vfat user,exec,rw,auto

milt15@DELL:/media/DISK_VOL2$ 


```

---

### Post by Vantrax on 2008-12-24
assuming its ntfs

sudo aptitude install ntfs-config


Press  Alt + F2, to get the ‘Run Application’ dialog box.
type in gksudo ntfs-config and click Run

Tick ‘Enable write support for external device

---

### Post by Milt15 on 2008-12-24
I have write support on ntfs but i don't have the permission to the files
I was on the dir and entered sudo su so all files and subdirectories owner changed to root and I can't change the owner nor permissions ( don't know why )

see this I have the read an execute premissions and after I did sudo chmod -R 777 ./ 
I still have the same permissions

```
milt15@DELL:/media/DISK_VOL2$ ls -l
total 533728
drwxr-xr-x 11 root root     32768 2008-12-04 13:44 ?????
drwxr-xr-x  2 root root     16384 2008-08-22 22:33 ????????? ????????
-rwxr-xr-x  1 root root     25341 2008-04-08 00:31 111.pdf
-rwxr-xr-x  1 root root    110878 2008-07-31 00:18 140-00423-0-EM84510.pdf
-rwxr-xr-x  1 root root    152376 2008-10-24 16:24 2008-afd_plugin.zip.zip
drwxr-xr-x  2 root root     16384 2008-12-02 20:16 3gp
drwxr-xr-x  2 root root     16384 2008-11-04 19:04 680+ Math Books Collection
drwxr-xr-x 34 root root     16384 2008-12-19 16:58 Acadimic
-rwxr-xr-x  1 root root   2435072 2007-11-29 18:12 A_family_with_17_children_.ppt
drwxr-xr-x 13 root root     16384 2008-11-21 02:22 Age of Empires 3
-rwxr-xr-x  1 root root     12087 2007-06-05 22:03 Aget.docx
-rwxr-xr-x  1 root root     50688 2007-11-21 22:00 ali-hassan.doc
-rwxr-xr-x  1 root root    123546 2008-10-20 19:05 and.pdf.pdf
-rwxr-xr-x  1 root root     34371 2008-10-20 19:04 anrist.pdf.pdf
-rwxr-xr-x  1 root root    106952 2008-05-26 01:16 apr18_2008_slides.pdf
drwxr-xr-x  5 root root     16384 2008-06-25 21:55 Ara
drwxr-xr-x  2 root root     32768 2008-12-04 19:00 Ares
-rwxr-xr-x  1 root root    194016 2008-12-14 19:41 bestblacklist_s60_3_v_2_01.sisx
-rwxr-xr-x  1 root root    184518 2008-09-23 16:10 bestblacklist_s60_3_v_2_01.zip
drwxr-xr-x  2 root root     16384 2008-09-05 10:50 bios
drwxr-xr-x  2 root root     16384 2008-12-14 19:42 BlackList
-rwxr-xr-x  1 root root     11638 2008-09-23 16:09 Black List v114.zip
-rwxr-xr-x  1 root root        66 2008-10-20 19:26 books
-rwxr-xr-x  1 root root  11365936 2008-11-22 19:11 brainworkshop-4.3.zip
-rwxr-xr-x  1 root root   3118187 2008-10-18 19:22 BreakingTheLaw.mp3
drwxr-xr-x  7 root root     16384 2008-11-28 16:17 bt
-rwxr-xr-x  1 root root    118784 2008-06-04 15:44 BUE - Lecture.doc
drwxr-xr-x  2 root root     16384 2008-12-01 22:19 C# 2008 books
-rwxr-xr-x  1 root root   8087085 2008-06-04 23:31 C%2B%2B For Dummies.pdf
-rwxr-xr-x  1 root root    261632 2008-07-30 15:03 CALL FOR POSTERS.doc
drwxr-xr-x  8 root root     16384 2008-08-20 02:39 ccna
-rwxr-xr-x  1 root root   3305600 2008-09-25 20:00 cd080802.zip
-rwxr-xr-x  1 root root         0 2008-10-20 18:39 COMG_20081001_Oct_2008.PDF.PDF
drwxr-xr-x  2 root root     32768 2008-07-30 00:57 d
drwxr-xr-x  4 root root     16384 2008-06-18 18:46 DeepBurner
-rwxr-xr-x  1 root root     23552 2008-07-12 03:27 digikam3.db
-rwxr-xr-x  1 root root      5672 2008-07-12 03:28 digikam3.db-journal
drwxr-xr-x  2 root root     16384 2008-08-03 02:14 Documents
-rwxr-xr-x  1 root root  23510720 2006-11-22 07:21 dotnetfx.exe
-rwxr-xr-x  1 root root     19344 2008-06-23 02:30 encryption key.txt
drwxr-xr-x  3 root root     16384 2008-12-09 19:17 flash
-rwxr-xr-x  1 root root    734833 2008-04-04 15:32 Flash Memory Toolkit.rar
-rwxr-xr-x  1 root root    275968 2007-06-22 01:53 FrogLeap.xls
drwxr-xr-x  2 root root     16384 2008-01-26 14:06 funstuff
-rwxr-xr-x  1 root root    363520 2008-03-22 20:20 future job.pps
-rwxr-xr-x  1 root root        91 2008-04-06 17:48 Geeky!.url
-rwxr-xr-x  1 root root   1640570 2008-07-30 14:54 GOLDRush_July_2008_v2.1.pdf
drwxr-xr-x  3 root root     16384 2008-08-30 18:14 Google Desktop Data
-rwxr-xr-x  1 root root   8142712 2008-08-02 00:39 google-gadgets_0.10.0-0~getdeb1_amd64.deb
-rwxr-xr-x  1 root root      8403 2008-07-03 17:24 grub.txt
-rwxr-xr-x  1 root root         0 2008-07-01 15:40 grub.txt~
drwxr-xr-x  2 root root     16384 2008-07-11 20:25 GTA Vice City User Files
drwxr-xr-x 19 root root     16384 2008-08-08 18:07 HaCk3rZ
drwxr-xr-x  2 root root     16384 2008-03-30 10:55 homework
drwxr-xr-x  2 root root     16384 2008-11-05 20:29 home work
-rwxr-xr-x  1 root root      1630 2008-03-31 07:11 homework.rar
drwxr-xr-x  3 root root     16384 2008-11-11 00:31 How to burn and play ps2 games without modchip
-rwxr-xr-x  1 root root   1182981 2008-05-12 17:43 How to burn and play ps2 games without modchip.rar
-rwxr-xr-x  1 root root   5261118 2008-12-14 19:46 i am rock.mp3
-rwxr-xr-x  1 root root   2804974 2008-05-05 15:55 IEEEComSoc_2007.pdf
-rwxr-xr-x  1 root root   1041581 2008-05-18 11:17 Image039.jpg
drwxr-xr-x  3 root root     16384 2008-11-05 20:29 img
-rwxr-xr-x  1 root root    228765 2008-05-20 22:07 Incubation and Technology Parks for Economic Growth.pdf
drwxr-xr-x  2 root root     16384 2008-08-02 21:21 Internet
-rwxr-xr-x  1 root root       951 2008-03-31 22:47 iSpeak.zip
-rwxr-xr-x  1 root root      6217 2008-05-15 15:32 iWappy.swf
-rwxr-xr-x  1 root root   5851595 2008-07-31 00:17 JAP.jar
drwxr-xr-x  2 root root     16384 2008-04-09 20:19 Java
-rwxr-xr-x  1 root root    605264 2008-07-30 22:52 jUploadr-1.1.2-linuxGTK-i386.tar.gz
-rwxr-xr-x  1 root root   2222358 2008-11-05 22:03 KAUST-grad-programs.pdf
-rwxr-xr-x  1 root root    876612 2008-08-02 01:07 launchy_2.1.1-1~getdeb1_i386.deb
drwxr-xr-x  2 root root     16384 2008-12-02 20:31 lfs
-rwxr-xr-x  1 root root    584314 2008-11-13 19:14 lightsword.zip
-rwxr-xr-x  1 root root     33280 2008-03-26 23:35 Linux.doc
drwxr-xr-x  3 root root     16384 2008-11-25 10:43 mandriva-linux-free-2009-dvd-x86_64
-rwxr-xr-x  1 root root       278 2008-06-18 16:05 Masha blog.url
drwxr-xr-x 18 root root     16384 2008-07-09 02:20 matlab7
drwxr-xr-x 11 root root     16384 2008-07-11 03:02 Maxima-5.15.0
drwxr-xr-x  3 root root     16384 2008-08-22 22:30 mb
-rwxr-xr-x  1 root root      1544 2008-10-30 14:27 menu.lst
-rwxr-xr-x  1 root root  84502688 2008-07-11 05:21 Michael & Sara - Soulmates Never Die xvid.avi
-rwxr-xr-x  1 root root   1566203 2008-03-26 00:04 Mind Powers-How to Use and Control Your Mind.pdf
drwxr-xr-x  2 root root     16384 2008-11-03 06:17 M I T
drwxr-xr-x  3 root root     16384 2008-04-09 20:10 Mohammed's doc
drwxr-xr-x  3 root root     16384 2008-08-08 18:07 money
-rwxr-xr-x  1 root root        88 2008-04-06 17:48 More Downloads!.url
drwxr-xr-x  2 root root     16384 2008-11-05 18:47 Music
drwxr-xr-x 34 root root     16384 2008-12-18 19:47 My Pictures
-rwxr-xr-x  1 root root        15 2008-08-18 22:39 New Text Document (2).txt
-rwxr-xr-x  1 root root   5722240 2008-10-24 00:43 Nogomi.com_01.Jannat-Habibi_3la_Neyato.mp3.mp3
drwxr-xr-x  3 root root     16384 2008-11-13 20:15 openobex
drwxr-xr-x  3 root root     16384 2008-11-21 21:05 PaP3r
-rwxr-xr-x  1 root root     12089 2008-09-22 21:52 pclos-hardware-certified.png
-rwxr-xr-x  1 root root   1038776 2008-08-09 16:19 pcsx2_0.9.4-1~getdeb1_amd64.deb
-rwxr-xr-x  1 root root     15596 2008-08-01 16:54 peterarz.gif
-rwxr-xr-x  1 root root       617 2008-03-26 01:10 PHP-injection-Mahmood.zip
drwxr-xr-x  4 root root     16384 2008-12-02 20:09 Portable
drwxr-xr-x  2 root root     16384 2008-05-16 19:16 Practical Hacking Techniques & Countermeasures
drwxr-xr-x  3 root root     16384 2008-05-15 01:01 Projects
-rwxr-xr-x  1 root root     57406 2008-10-20 19:08 PS1.pdf.pdf
drwxr-xr-x  4 root root     16384 2008-06-25 01:49 ps2
-rwxr-xr-x  1 root root   1522483 2008-04-01 18:33 pssdk_dll_ver_3_0.zip
-rwxr-xr-x  1 root root    462848 2007-11-15 18:01 putty.exe
drwxr-xr-x  3 root root     16384 2008-11-22 19:16 Pyhthon
-rwxr-xr-x  1 root root    403213 2008-10-11 01:17 RAR Password Cracker 4.12.zip.zip
-rwxr-xr-x  1 root root    232893 2008-10-20 19:07 Ravi.pdf.pdf
-rwxr-xr-x  1 root root      1734 2002-10-14 11:26 readme.txt
-rwxr-xr-x  1 root root   5255188 2007-05-13 07:59 Red Hat Linux Fedora For Dummies.chm
drwxr-xr-x  5 root root     16384 2008-08-08 18:07 Resources
-rwxr-xr-x  1 root root    498288 2008-12-10 01:42 Riverbedthehandbookofapplicationdelivery.pdf
-rwxr-xr-x  1 root root     13708 2008-09-25 02:46 showpic.dml
drwxr-xr-x  4 root root     16384 2008-09-23 15:18 SmallNetBuilder - Small Network Help - How To Crack WPA _ WPA2_files
-rwxr-xr-x  1 root root  40347192 2008-11-02 20:20 Speak_English.rar
-rwxr-xr-x  1 root root     13153 2008-10-17 19:11 -=[SUMOTorrent.com]=-_USBExtreme_USBAdvance__USB_Loader_(FULL_NEW)_ST1817565.torrent.torrent
-rwxr-xr-x  1 root root     13113 2008-10-17 19:10 -=[SUMOTorrent.com]=-_USBExtreme_USBAdvance__USB_Loader.torrent.torrent
-rwxr-xr-x  1 root root    367593 2008-09-25 19:59 super_grub_disk_castellano_usb_0.9763.tar.gz
-rwxr-xr-x  1 root root   1635488 2008-12-10 01:43 the-public-domain.pdf
-rwxr-xr-x  1 root root     90785 2008-10-20 19:05 Toplak-disjunctive-JEdP02.pdf.pdf
-rwxr-xr-x  1 root root       124 2008-03-30 10:41 tp02b114.bat
drwxr-xr-x  2 root root     16384 2008-12-05 00:20 txt
drwxr-xr-x  2 root root     16384 2008-05-16 19:16 Ubuntu Hacks Tips and Tools for Exploring, Using, and Tuning Linux
drwxr-xr-x  4 root root     16384 2008-10-13 21:12 unebootin
-rwxr-xr-x  1 root root   3627996 2008-09-25 19:54 unetbootin-linux-282
-rwxr-xr-x  1 root root   1559706 2008-09-25 19:49 unetbootin-source-281.zip
-rwxr-xr-x  1 root root   9012303 2008-11-13 19:30 unetbootin-ubuntu710rev99-2.noarch.rpm
-rwxr-xr-x  1 root root   3859456 2008-07-18 17:11 unetbootin-windows-241.exe
-rwxr-xr-x  1 root root    661022 2008-05-20 20:48 untitled.bmp
-rwxr-xr-x  1 root root    100422 2008-10-17 19:16 USBeXtreme.zip.zip
-rwxr-xr-x  1 root root    982609 2008-11-13 19:21 Wa3D-ToolKit-1.0.0-VC++6.0.zip
-rwxr-xr-x  1 root root       611 2008-06-23 02:31 way.txt
-rwxr-xr-x  1 root root    235875 2008-10-24 02:12 WebsiteSecurityTests.pdf.pdf
-rwxr-xr-x  1 root root 295010304 2008-07-29 13:06 wiki.iso
-rwxr-xr-x  1 root root     35328 2008-07-30 19:01 winbox.exe
drwxr-xr-x  3 root root     16384 2008-12-15 18:22 wine
drwxr-xr-x  2 root root     16384 2008-06-25 02:03 Xbox
-rwxr-xr-x  1 root root    917777 2008-03-25 06:42 xx.pdf
milt15@DELL:/media/DISK_VOL2$ sudo chmod -R 777 ./
[sudo] password for milt15: 
milt15@DELL:/media/DISK_VOL2$ ls -l
total 533728
drwxr-xr-x 11 root root     32768 2008-12-04 13:44 ?????
drwxr-xr-x  2 root root     16384 2008-08-22 22:33 ????????? ????????
-rwxr-xr-x  1 root root     25341 2008-04-08 00:31 111.pdf
-rwxr-xr-x  1 root root    110878 2008-07-31 00:18 140-00423-0-EM84510.pdf
-rwxr-xr-x  1 root root    152376 2008-10-24 16:24 2008-afd_plugin.zip.zip
drwxr-xr-x  2 root root     16384 2008-12-02 20:16 3gp
drwxr-xr-x  2 root root     16384 2008-11-04 19:04 680+ Math Books Collection
drwxr-xr-x 34 root root     16384 2008-12-19 16:58 Acadimic
-rwxr-xr-x  1 root root   2435072 2007-11-29 18:12 A_family_with_17_children_.ppt
drwxr-xr-x 13 root root     16384 2008-11-21 02:22 Age of Empires 3
-rwxr-xr-x  1 root root     12087 2007-06-05 22:03 Aget.docx
-rwxr-xr-x  1 root root     50688 2007-11-21 22:00 ali-hassan.doc
-rwxr-xr-x  1 root root    123546 2008-10-20 19:05 and.pdf.pdf
-rwxr-xr-x  1 root root     34371 2008-10-20 19:04 anrist.pdf.pdf
-rwxr-xr-x  1 root root    106952 2008-05-26 01:16 apr18_2008_slides.pdf
drwxr-xr-x  5 root root     16384 2008-06-25 21:55 Ara
drwxr-xr-x  2 root root     32768 2008-12-04 19:00 Ares
-rwxr-xr-x  1 root root    194016 2008-12-14 19:41 bestblacklist_s60_3_v_2_01.sisx
-rwxr-xr-x  1 root root    184518 2008-09-23 16:10 bestblacklist_s60_3_v_2_01.zip
drwxr-xr-x  2 root root     16384 2008-09-05 10:50 bios
drwxr-xr-x  2 root root     16384 2008-12-14 19:42 BlackList
-rwxr-xr-x  1 root root     11638 2008-09-23 16:09 Black List v114.zip
-rwxr-xr-x  1 root root        66 2008-10-20 19:26 books
-rwxr-xr-x  1 root root  11365936 2008-11-22 19:11 brainworkshop-4.3.zip
-rwxr-xr-x  1 root root   3118187 2008-10-18 19:22 BreakingTheLaw.mp3
drwxr-xr-x  7 root root     16384 2008-11-28 16:17 bt
-rwxr-xr-x  1 root root    118784 2008-06-04 15:44 BUE - Lecture.doc
drwxr-xr-x  2 root root     16384 2008-12-01 22:19 C# 2008 books
-rwxr-xr-x  1 root root   8087085 2008-06-04 23:31 C%2B%2B For Dummies.pdf
-rwxr-xr-x  1 root root    261632 2008-07-30 15:03 CALL FOR POSTERS.doc
drwxr-xr-x  8 root root     16384 2008-08-20 02:39 ccna
-rwxr-xr-x  1 root root   3305600 2008-09-25 20:00 cd080802.zip
-rwxr-xr-x  1 root root         0 2008-10-20 18:39 COMG_20081001_Oct_2008.PDF.PDF
drwxr-xr-x  2 root root     32768 2008-07-30 00:57 d
drwxr-xr-x  4 root root     16384 2008-06-18 18:46 DeepBurner
-rwxr-xr-x  1 root root     23552 2008-07-12 03:27 digikam3.db
-rwxr-xr-x  1 root root      5672 2008-07-12 03:28 digikam3.db-journal
drwxr-xr-x  2 root root     16384 2008-08-03 02:14 Documents
-rwxr-xr-x  1 root root  23510720 2006-11-22 07:21 dotnetfx.exe
-rwxr-xr-x  1 root root     19344 2008-06-23 02:30 encryption key.txt
drwxr-xr-x  3 root root     16384 2008-12-09 19:17 flash
-rwxr-xr-x  1 root root    734833 2008-04-04 15:32 Flash Memory Toolkit.rar
-rwxr-xr-x  1 root root    275968 2007-06-22 01:53 FrogLeap.xls
drwxr-xr-x  2 root root     16384 2008-01-26 14:06 funstuff
-rwxr-xr-x  1 root root    363520 2008-03-22 20:20 future job.pps
-rwxr-xr-x  1 root root        91 2008-04-06 17:48 Geeky!.url
-rwxr-xr-x  1 root root   1640570 2008-07-30 14:54 GOLDRush_July_2008_v2.1.pdf
drwxr-xr-x  3 root root     16384 2008-08-30 18:14 Google Desktop Data
-rwxr-xr-x  1 root root   8142712 2008-08-02 00:39 google-gadgets_0.10.0-0~getdeb1_amd64.deb
-rwxr-xr-x  1 root root      8403 2008-07-03 17:24 grub.txt
-rwxr-xr-x  1 root root         0 2008-07-01 15:40 grub.txt~
drwxr-xr-x  2 root root     16384 2008-07-11 20:25 GTA Vice City User Files
drwxr-xr-x 19 root root     16384 2008-08-08 18:07 HaCk3rZ
drwxr-xr-x  2 root root     16384 2008-03-30 10:55 homework
drwxr-xr-x  2 root root     16384 2008-11-05 20:29 home work
-rwxr-xr-x  1 root root      1630 2008-03-31 07:11 homework.rar
drwxr-xr-x  3 root root     16384 2008-11-11 00:31 How to burn and play ps2 games without modchip
-rwxr-xr-x  1 root root   1182981 2008-05-12 17:43 How to burn and play ps2 games without modchip.rar
-rwxr-xr-x  1 root root   5261118 2008-12-14 19:46 i am rock.mp3
-rwxr-xr-x  1 root root   2804974 2008-05-05 15:55 IEEEComSoc_2007.pdf
-rwxr-xr-x  1 root root   1041581 2008-05-18 11:17 Image039.jpg
drwxr-xr-x  3 root root     16384 2008-11-05 20:29 img
-rwxr-xr-x  1 root root    228765 2008-05-20 22:07 Incubation and Technology Parks for Economic Growth.pdf
drwxr-xr-x  2 root root     16384 2008-08-02 21:21 Internet
-rwxr-xr-x  1 root root       951 2008-03-31 22:47 iSpeak.zip
-rwxr-xr-x  1 root root      6217 2008-05-15 15:32 iWappy.swf
-rwxr-xr-x  1 root root   5851595 2008-07-31 00:17 JAP.jar
drwxr-xr-x  2 root root     16384 2008-04-09 20:19 Java
-rwxr-xr-x  1 root root    605264 2008-07-30 22:52 jUploadr-1.1.2-linuxGTK-i386.tar.gz
-rwxr-xr-x  1 root root   2222358 2008-11-05 22:03 KAUST-grad-programs.pdf
-rwxr-xr-x  1 root root    876612 2008-08-02 01:07 launchy_2.1.1-1~getdeb1_i386.deb
drwxr-xr-x  2 root root     16384 2008-12-02 20:31 lfs
-rwxr-xr-x  1 root root    584314 2008-11-13 19:14 lightsword.zip
-rwxr-xr-x  1 root root     33280 2008-03-26 23:35 Linux.doc
drwxr-xr-x  3 root root     16384 2008-11-25 10:43 mandriva-linux-free-2009-dvd-x86_64
-rwxr-xr-x  1 root root       278 2008-06-18 16:05 Masha blog.url
drwxr-xr-x 18 root root     16384 2008-07-09 02:20 matlab7
drwxr-xr-x 11 root root     16384 2008-07-11 03:02 Maxima-5.15.0
drwxr-xr-x  3 root root     16384 2008-08-22 22:30 mb
-rwxr-xr-x  1 root root      1544 2008-10-30 14:27 menu.lst
-rwxr-xr-x  1 root root  84502688 2008-07-11 05:21 Michael & Sara - Soulmates Never Die xvid.avi
-rwxr-xr-x  1 root root   1566203 2008-03-26 00:04 Mind Powers-How to Use and Control Your Mind.pdf
drwxr-xr-x  2 root root     16384 2008-11-03 06:17 M I T
drwxr-xr-x  3 root root     16384 2008-04-09 20:10 Mohammed's doc
drwxr-xr-x  3 root root     16384 2008-08-08 18:07 money
-rwxr-xr-x  1 root root        88 2008-04-06 17:48 More Downloads!.url
drwxr-xr-x  2 root root     16384 2008-11-05 18:47 Music
drwxr-xr-x 34 root root     16384 2008-12-18 19:47 My Pictures
-rwxr-xr-x  1 root root        15 2008-08-18 22:39 New Text Document (2).txt
-rwxr-xr-x  1 root root   5722240 2008-10-24 00:43 Nogomi.com_01.Jannat-Habibi_3la_Neyato.mp3.mp3
drwxr-xr-x  3 root root     16384 2008-11-13 20:15 openobex
drwxr-xr-x  3 root root     16384 2008-11-21 21:05 PaP3r
-rwxr-xr-x  1 root root     12089 2008-09-22 21:52 pclos-hardware-certified.png
-rwxr-xr-x  1 root root   1038776 2008-08-09 16:19 pcsx2_0.9.4-1~getdeb1_amd64.deb
-rwxr-xr-x  1 root root     15596 2008-08-01 16:54 peterarz.gif
-rwxr-xr-x  1 root root       617 2008-03-26 01:10 PHP-injection-Mahmood.zip
drwxr-xr-x  4 root root     16384 2008-12-02 20:09 Portable
drwxr-xr-x  2 root root     16384 2008-05-16 19:16 Practical Hacking Techniques & Countermeasures
drwxr-xr-x  3 root root     16384 2008-05-15 01:01 Projects
-rwxr-xr-x  1 root root     57406 2008-10-20 19:08 PS1.pdf.pdf
drwxr-xr-x  4 root root     16384 2008-06-25 01:49 ps2
-rwxr-xr-x  1 root root   1522483 2008-04-01 18:33 pssdk_dll_ver_3_0.zip
-rwxr-xr-x  1 root root    462848 2007-11-15 18:01 putty.exe
drwxr-xr-x  3 root root     16384 2008-11-22 19:16 Pyhthon
-rwxr-xr-x  1 root root    403213 2008-10-11 01:17 RAR Password Cracker 4.12.zip.zip
-rwxr-xr-x  1 root root    232893 2008-10-20 19:07 Ravi.pdf.pdf
-rwxr-xr-x  1 root root      1734 2002-10-14 11:26 readme.txt
-rwxr-xr-x  1 root root   5255188 2007-05-13 07:59 Red Hat Linux Fedora For Dummies.chm
drwxr-xr-x  5 root root     16384 2008-08-08 18:07 Resources
-rwxr-xr-x  1 root root    498288 2008-12-10 01:42 Riverbedthehandbookofapplicationdelivery.pdf
-rwxr-xr-x  1 root root     13708 2008-09-25 02:46 showpic.dml
drwxr-xr-x  4 root root     16384 2008-09-23 15:18 SmallNetBuilder - Small Network Help - How To Crack WPA _ WPA2_files
-rwxr-xr-x  1 root root  40347192 2008-11-02 20:20 Speak_English.rar
-rwxr-xr-x  1 root root     13153 2008-10-17 19:11 -=[SUMOTorrent.com]=-_USBExtreme_USBAdvance__USB_Loader_(FULL_NEW)_ST1817565.torrent.torrent
-rwxr-xr-x  1 root root     13113 2008-10-17 19:10 -=[SUMOTorrent.com]=-_USBExtreme_USBAdvance__USB_Loader.torrent.torrent
-rwxr-xr-x  1 root root    367593 2008-09-25 19:59 super_grub_disk_castellano_usb_0.9763.tar.gz
-rwxr-xr-x  1 root root   1635488 2008-12-10 01:43 the-public-domain.pdf
-rwxr-xr-x  1 root root     90785 2008-10-20 19:05 Toplak-disjunctive-JEdP02.pdf.pdf
-rwxr-xr-x  1 root root       124 2008-03-30 10:41 tp02b114.bat
drwxr-xr-x  2 root root     16384 2008-12-05 00:20 txt
drwxr-xr-x  2 root root     16384 2008-05-16 19:16 Ubuntu Hacks Tips and Tools for Exploring, Using, and Tuning Linux
drwxr-xr-x  4 root root     16384 2008-10-13 21:12 unebootin
-rwxr-xr-x  1 root root   3627996 2008-09-25 19:54 unetbootin-linux-282
-rwxr-xr-x  1 root root   1559706 2008-09-25 19:49 unetbootin-source-281.zip
-rwxr-xr-x  1 root root   9012303 2008-11-13 19:30 unetbootin-ubuntu710rev99-2.noarch.rpm
-rwxr-xr-x  1 root root   3859456 2008-07-18 17:11 unetbootin-windows-241.exe
-rwxr-xr-x  1 root root    661022 2008-05-20 20:48 untitled.bmp
-rwxr-xr-x  1 root root    100422 2008-10-17 19:16 USBeXtreme.zip.zip
-rwxr-xr-x  1 root root    982609 2008-11-13 19:21 Wa3D-ToolKit-1.0.0-VC++6.0.zip
-rwxr-xr-x  1 root root       611 2008-06-23 02:31 way.txt
-rwxr-xr-x  1 root root    235875 2008-10-24 02:12 WebsiteSecurityTests.pdf.pdf
-rwxr-xr-x  1 root root 295010304 2008-07-29 13:06 wiki.iso
-rwxr-xr-x  1 root root     35328 2008-07-30 19:01 winbox.exe
drwxr-xr-x  3 root root     16384 2008-12-15 18:22 wine
drwxr-xr-x  2 root root     16384 2008-06-25 02:03 Xbox
-rwxr-xr-x  1 root root    917777 2008-03-25 06:42 xx.pdf
milt15@DELL:/media/DISK_VOL2$ 


```

---

### Post by cdenley on 2008-12-26
fat16 and fat32 cannot store any unix permissions, so even if any chmod, chown, chgrp commands succeed, they will disappear as soon as the filesystem is unmounted. The entire filesystem is assigned permissions at mount time. You can use mount options such as uid, gid, umask, dmask, or fmask.

```

man mount

```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=a6bf3160-969c-43ac-bd22-27a81b66f9b0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=5dde72da-f7a4-4262-baf5-5284bd401891 none            swap    sw              0       0
# /dev/sda5, size=58621122, type=11: FAT32 (extended)
/dev/sda5 /media/DISK_VOL2 vfat **uid=1000,**user,exec,rw,auto
# /dev/sda6, size=58621122, type=11: FAT32 (extended)
/dev/sda6 /media/DISK_VOL3 vfat **uid=1000,**user,exec,rw,auto

```

---

### Post by albinootje on 2008-12-26
> **Milt15 said:**
> the one with DISK_VOL2 is FAT32 and the other one is external ntfs
and when I do the mount command it tells me it is already mounted

You cannot change ownership on a FAT-partition like your normally would.

FAT is a very primitive and old-fashioned file-system from the days when DOS was popular. (IBM-DOS,DR-DOS,Novell-DOS,MS-DOS etc.)
FAT has been a little improved through the years by Microsoft, but it continued not having proper file-permission support.
(NTFS does support file-permissions)

If you want to give your normal user full read/write permissions to a FAT partition, then use the umask mount option.
Read the mount manual page, the section about FAT : man mount
And see here :
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
You can also use the uid and gid options to only give access to your user.

---

### Post by Milt15 on 2008-12-26
thanks alot cdenly 
I have put the option uid=1000 in the fstab and it worked great

the user identifier idea is great and thnx for everyon who helped here

---

### Post by ben2talk on 2008-12-28
> **cariboo907 said:**
> You can just change the permissions on all the files in the directory by typing in a terminal:

```
sudo chmod -R 777 ./img
```

THis will recursivly change all the permissions to world read/write.

Jim

" this WILL"

but it DIDN:T !! I tried this on my NTFS partition, which I made and wrote the files to either as myself or as root.

---

