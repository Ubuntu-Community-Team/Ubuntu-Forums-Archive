---
title: "Mdadm issue, unable to re-mount array"
date: 2013-05-19
forum: Server Platforms
---

### Post by djh82uk on 2013-05-19
Hi All

I have a big issue im trying to solve.  I have an array (md0) that is currently resyncing, however I cannot mount md0 with the following command:

mount -t ext4 /dev/md0 /Data


It gives:
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



dmesg gives:


[  722.340720]  md0: unknown partition table
[  722.387711] md: could not open unknown-block(8,161).
[  722.387759] md: md_import_device returned -16
[  722.387769] md: could not open unknown-block(8,161).
[  722.387807] md: md_import_device returned -16
[  739.259850] EXT4-fs (md0): VFS: Can't find ext4 filesystem
[ 1141.465699] EXT4-fs (md0): VFS: Can't find ext4 filesystem




fsck.ext4 /dev/md0 says that there is no superblock


Trying to recover the backup blocks gives the same error.


Can anyone please help me?  I have 12tb of data on this array, the backup server has been down for a few days to an issue also with mdadm (two drives failed).

So now I have no backup due to very unfortunate timing.

Can anyone thing what else I can try?

Thanks

DJH

---

### Post by djh82uk on 2013-05-19
Hmm, managed to get the backup server up and running, but it is having the exact same issue, both are re-syncing but cannot mount  :(

---

### Post by darkod on 2013-05-19
First start by confirming the mdadm status:
```
cat /proc/mdstat
sudo mdadm --detail /dev/md0
```

---

### Post by djh82uk on 2013-05-19
Ok so  


Cat /proc/mdstat

```
 cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdk1[8] sdj1[6] sdi1[5] sdh1[4] sdf1[3] sdd1[2] sdc1[1] sdb1[0]
      13674590720 blocks super 1.2 level 5, 512k chunk, algorithm 2 [8/7] [UUUUUUU_]
      [============>........]  recovery = 62.1% (1214521984/1953512960) finish=161.6min speed=76201K/sec

md1 : active raid1 sdg1[2] sde1[0]
      976758841 blocks super 1.2 [2/2] [UU]

unused devices: <none>

```


sudo mdadm --detail /dev/md0

```
/dev/md0:
        Version : 1.2
  Creation Time : Sun May 19 21:15:42 2013
     Raid Level : raid5
     Array Size : 13674590720 (13041.11 GiB 14002.78 GB)
  Used Dev Size : 1953512960 (1863.02 GiB 2000.40 GB)
   Raid Devices : 8
  Total Devices : 8
    Persistence : Superblock is persistent

    Update Time : Mon May 20 01:48:55 2013
          State : clean, degraded, recovering
 Active Devices : 7
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

 Rebuild Status : 62% complete

           Name : fs01:0  (local to host fs01)
           UUID : 5046e2e3:c9d80bcd:87803c89:5d1ec772
         Events : 67

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       81        3      active sync   /dev/sdf1
       4       8      113        4      active sync   /dev/sdh1
       5       8      129        5      active sync   /dev/sdi1
       6       8      145        6      active sync   /dev/sdj1
       8       8      161        7      spare rebuilding   /dev/sdk1

```


Thanks

DJH

---

### Post by darkod on 2013-05-20
It looks fine, only it's in a process of rebuilding. raid5 array should still mount while rebuilding, but let it finish and see if the fsck does something, and if you can mount it. Try fsck without specifying the filesystem, it will detect any extN on its own.
```
sudo fsck /dev/md0
```

In general it looks good on the mdadm side. After it rebuilds you can start checking the filesystem side.

---

### Post by djh82uk on 2013-05-20
Hiya

Array has finished syncing, still won't mount due to the same issue:


FSCK

```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;

```

---

### Post by djh82uk on 2013-05-20
Trying to repair the superblock does not help either

```

djh@fs01:~$ sudo e2fsck -b 98304 /dev/md0
e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;

```

---

### Post by darkod on 2013-05-20
Are you sure the filesystem was ext2/ext3/ext4?

In any case this looks like filesystem repair now, not like mdadm repair. I don't have much experience with filesystem repairs except running the standard fsck.

---

### Post by djh82uk on 2013-05-20
Yeh it was definatley formated as ext4:


sudo fdisk -l gives

```

Disk /dev/md1: 1000.2 GB, 1000201053184 bytes
2 heads, 4 sectors/track, 244189710 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md0: 14002.8 GB, 14002780897280 bytes
2 heads, 4 sectors/track, -876319616 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 3670016 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```


It says md0 does not have a valid partition table, but it says the same for md1 which is ext4, has loads of data and is fine.

Thanks

---

### Post by djh82uk on 2013-05-20
Parted correctly identifies md1 as ext4

but for md0 it says :

```
Error: /dev/md0: unrecognised disk label

```

---

### Post by steeldriver on 2013-05-20
what does 'file' say? it can see things like LVM volumes as well

```
sudo file -sL /dev/md0
```

---

### Post by djh82uk on 2013-05-20
that comes back with:

```
djh@fs01:~$ sudo file -sL /dev/md0
/dev/md0: shared library

```

---

### Post by darkod on 2013-05-20
That message from fdisk is normal about md devices, it can't display them properly. But parted should display ext4 for md0. You might have a big problem.

While working with mdadm, you didn't use te --create option right? You might have created a new array over your old one. If it's still unformatted, it would say there is no ext4 on md0. But this is only an assumption.

---

### Post by djh82uk on 2013-05-20
Hiya

yes I did use the --create as --assemble would not work (missing superblock on every drive).

I have used --create a few times before and never had a problem, data has always been there.  Also a few guides stated it was ok to do.

I copy/pasted the same command I used last time that it worked.

Thanks

DJH

---

### Post by darkod on 2013-05-20
There have been cases where --create doesn't destroy data, but in general it is used to create new blank arrays. I think you might have blown away your data.

There are things to try if plain --assemble doesn't work, there are ways to force it and it can recreate the superblock.

You NEVER run --create on an array where you want to keep the data, regardless if it worked before or if some blog says it does. Did you use the --assume-clean option with --create? That might help keep the data.

---

### Post by djh82uk on 2013-05-20
Hi

Yes I used the --assume-clean, So you think everything is gone? :(

If I am to re-create the array, whats the best way to make sure it is all fresh & clean?

Also im thinking of going for more redundancy with 8 x 2Tb disks, is raid 10 best for this and will give me 8tb useable?

Thanks

DJH

---

### Post by darkod on 2013-05-20
With raid10 you lose 50% of the storage which is too much. But raid6 might be better option than raid5 since it allows two failed members.

If you used --assume-clean there might be hope, but I really don't know to troubleshoot these filesystem errors.

The --create always makes me nervous and I recommend to people to leave it as literary the last option, if nothing else works.

The problem is that I'm not sure we can search for the old superblock info since a --create was executed. But lets see the output of:
```
sudo mdadm --examine /dev/sd[bcdfhijk]1
```

That command will examine the superblock of each partition listed, even if currently not part of a working array. I assume right now it will show the superblocks of the newly created array, not the old one (you said most superblocks were missing anyway).

---

### Post by djh82uk on 2013-05-20
Hiya

output is below, im concerned with using 5/6 as my issue has not been drives failing, but just the array messing up, renaming itself to md127 etc.

I did like raidz, but don't like the need to use opensolaris.


```
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5046e2e3:c9d80bcd:87803c89:5d1ec772
           Name : fs01:0  (local to host fs01)
  Creation Time : Sun May 19 21:15:42 2013
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907027037 (1863.02 GiB 2000.40 GB)
     Array Size : 27349181440 (13041.11 GiB 14002.78 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 7a819fe6:baaa288b:2812feb4:4c5350e2

    Update Time : Mon May 20 19:54:41 2013
       Checksum : 4a2f048 - correct
         Events : 80

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAAAAAA ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5046e2e3:c9d80bcd:87803c89:5d1ec772
           Name : fs01:0  (local to host fs01)
  Creation Time : Sun May 19 21:15:42 2013
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907027037 (1863.02 GiB 2000.40 GB)
     Array Size : 27349181440 (13041.11 GiB 14002.78 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f90a9a5d:5074c7ab:c98cb7e9:94e32a59

    Update Time : Mon May 20 19:54:41 2013
       Checksum : 47d04e46 - correct
         Events : 80

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAAAAAAA ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5046e2e3:c9d80bcd:87803c89:5d1ec772
           Name : fs01:0  (local to host fs01)
  Creation Time : Sun May 19 21:15:42 2013
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907027037 (1863.02 GiB 2000.40 GB)
     Array Size : 27349181440 (13041.11 GiB 14002.78 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 7b755400:ac3242b3:1654e818:b2e6cc23

    Update Time : Mon May 20 19:54:41 2013
       Checksum : ebd8418e - correct
         Events : 80

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAAAAAA ('A' == active, '.' == missing)
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5046e2e3:c9d80bcd:87803c89:5d1ec772
           Name : fs01:0  (local to host fs01)
  Creation Time : Sun May 19 21:15:42 2013
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907027037 (1863.02 GiB 2000.40 GB)
     Array Size : 27349181440 (13041.11 GiB 14002.78 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ce758172:4e24a489:f1dc9aee:4c438381

    Update Time : Mon May 20 19:54:41 2013
       Checksum : 67d018fb - correct
         Events : 80

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAAAAAA ('A' == active, '.' == missing)
/dev/sdh1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5046e2e3:c9d80bcd:87803c89:5d1ec772
           Name : fs01:0  (local to host fs01)
  Creation Time : Sun May 19 21:15:42 2013
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907027037 (1863.02 GiB 2000.40 GB)
     Array Size : 27349181440 (13041.11 GiB 14002.78 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 6ffb83bc:cb4085dd:33096e68:ce4472b2

    Update Time : Mon May 20 19:54:41 2013
       Checksum : b075e8de - correct
         Events : 80

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 4
   Array State : AAAAAAAA ('A' == active, '.' == missing)
/dev/sdi1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5046e2e3:c9d80bcd:87803c89:5d1ec772
           Name : fs01:0  (local to host fs01)
  Creation Time : Sun May 19 21:15:42 2013
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907027037 (1863.02 GiB 2000.40 GB)
     Array Size : 27349181440 (13041.11 GiB 14002.78 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 515694fb:9be52fc6:6d3a93bb:4cccf591

    Update Time : Mon May 20 19:54:41 2013
       Checksum : ad9a14a - correct
         Events : 80

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 5
   Array State : AAAAAAAA ('A' == active, '.' == missing)
/dev/sdj1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5046e2e3:c9d80bcd:87803c89:5d1ec772
           Name : fs01:0  (local to host fs01)
  Creation Time : Sun May 19 21:15:42 2013
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907027037 (1863.02 GiB 2000.40 GB)
     Array Size : 27349181440 (13041.11 GiB 14002.78 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 80c85f0a:69a358b7:bc6eb9c7:889fb3b2

    Update Time : Mon May 20 19:54:41 2013
       Checksum : 37b1d8d2 - correct
         Events : 80

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 6
   Array State : AAAAAAAA ('A' == active, '.' == missing)
/dev/sdk1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5046e2e3:c9d80bcd:87803c89:5d1ec772
           Name : fs01:0  (local to host fs01)
  Creation Time : Sun May 19 21:15:42 2013
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907027037 (1863.02 GiB 2000.40 GB)
     Array Size : 27349181440 (13041.11 GiB 14002.78 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1b4d68be:39209205:40ef4808:abb808bc

    Update Time : Mon May 20 19:54:41 2013
       Checksum : 83d873e5 - correct
         Events : 80

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 7
   Array State : AAAAAAAA ('A' == active, '.' == missing)

```

---

### Post by darkod on 2013-05-20
Read this (only READ it, don't do anything right now!!!):
[http://serverfault.com/questions/347606/recover-raid-5-data-after-created-new-array-instead-of-re-using](http://serverfault.com/questions/347606/recover-raid-5-data-after-created-new-array-instead-of-re-using)

Very similar situation to yours. Read the main post quickly, then read the first reply (by Shane) very slowly and in detail.

The short summary is that Shane did few different tests in a VM and got the data successfully back. In one of those tests, where he recreated the new array with the wrong disk (member) order, he got the same fsck message you are getting. But as soon as he used the right disk order, the data was still there.

So, looks like there is a hope, but first read all of that carefully, try to understand what is happening in each of the different tests, and ask questions before you do anything if you have them.

With 8 disks you might need long time to get the order right, that's why it's beter to have a note of the disk order especially in big arrays. But with the right disk order the situation looks promising.

---

### Post by djh82uk on 2013-05-20
I had actually already read that, but how do I know what the right order is, or do I have to keep destroying the array, and re-creating it in different orders until I can possibly mount it?

Would the fact that i did a resync already have messed that up already?

Thanks

DJH

---

### Post by djh82uk on 2013-05-20
Does this not indicate the order?  or have I lost that info? (taken from that post)

It looks like this:

Number   Major   Minor   RaidDevice State
   0       8       33        0      active sync   /dev/sdc1
   1       8       49        1      active sync   /dev/sdd1
   3       8       17        2      active sync   /dev/sdb1

When it should look like this:

Number   Major   Minor   RaidDevice State
   0       8       17        0      active sync   /dev/sdb1
   1       8       33        1      active sync   /dev/sdc1
   3       8       49        2      active sync   /dev/sdd1

---

### Post by darkod on 2013-05-20
He was also doing resync, and it worked after he put the order correctly later.
The thing is that the current order is showing the current order, and it's irrelevant for the previous order. You can get the order with mdadm --detail /dev/md0 but when it was the original array. And then write it down so you have it for the future if something happens to the superblocks.

Right now I can't really be sure how to get the original disk order. If replacing some disks, they might have been inserted in the middle, not at the end. Let me send a PM to someone that has more mdadm knowledge, if he can join in.

---

### Post by rubylaser on 2013-05-20
Since, you've blown away the previous metadata by recreating the array, the only way to potentially recover at this point is to try every possible order combination to assemble your array and try to mount it each time to see if your data is available. Just so I understand, what you put it [post #4]("http://ubuntuforums.org/showthread.php?t=2146763&p=12655134#post12655134"), was after you ran mdadm --create --assume-clean, correct?

---

### Post by djh82uk on 2013-05-20
ok, so thats 40320 possible orders?

Is there a script around that can perhaps:

Create array variant 1

mount array

If output = 0 then success

If (len)output>=1 then

Delete array

Create array variant 2

Etc..

---

### Post by djh82uk on 2013-05-20
Ok, I have found a perl script, but I need some help:

```
#!/usr/bin/perl -w

# If you forgot how you built an array and need to try various
# permutations then this is for you...

# based on Mark-Jason Dominus' mjd_permute: permute each word of input

use strict;
use Getopt::Long;

sub usage {
 return "syntax: permute_array --md <md_device> --mount <mountpoint> [--opts <mdadm options>] [--for_real] <all devices>\n";
}

my $MD_DEVICE="/dev/md0";
my $MOUNTPOINT="/Data";
my $MDADM_OPTS="--assume-clean";
my $REAL;

################################################################
# This function is passed each permutation of component devices.
# This includes a 'missing' device.
# This is the place to hack command variations etc... 
sub try_array {
  # @_ looks like: ("/dev/sda1", "missing", "/dev/sdb1")
  my @device_list = @_["/dev/sdb1", "/dev/sdc1", "/dev/sdd1", "/dev/sdf1", "/dev/sdh1", "/dev/sdi1", "/dev/sdj1", "/dev/sdk1"];
  my $num_devices = scalar $_["8"];

  # This may need a --force... <gulp>
  my $create = "yes | mdadm --create $MD_DEVICE --raid-devices=$num_devices --level=5 $MDADM_OPTS @device_list 2>/dev/null\n";
  # Don't forget to mount read-only
  my $mount =  "mount -oro $MD_DEVICE $MOUNTPOINT 2>/dev/null";
  my $umount =  "umount $MOUNTPOINT 2>/dev/null";
  # and stop the array...
  my $stop = "mdadm --stop $MD_DEVICE 2>/dev/null";

  # REAL == --for_real option
  if ($REAL) {
    # we expect this to succeed
    system $create;
    if (my $err = $?>>8) {
      die "command : $create\n   exited with status $err\n\n";
    }
    # we expect this to fail and are happy if it succeeds
    system $mount;
    if (!(my $err = $?>>8)) {
      print "Success. possible command : \n  $create\n";
      system $umount;
    }
    # we expect this to succeed
    system $stop;
    if (my $err = $?>>8) {
      die "command : $stop\n   exited with status $err\n\n";
    }
  } else {
    # Just show the create/mount/stop commands
    # If you want more control you could use this to write a script
    print "$create\n$mount\n$stop\n";
  }
}


################################################################
# Execution starts here...
#
sub factorial($);

GetOptions ('md=s'      => \$MD_DEVICE,
	    "mount=s"   => \$MOUNTPOINT,
	    "opts=s"    => \$MDADM_OPTS,
	    "for_real"  => \$REAL);

if (!defined($MD_DEVICE) or !defined($MOUNTPOINT)) {
  die &usage;
}

print "using device $MD_DEVICE and mounting on $MOUNTPOINT\n";

# we *always* assume a 'missing' device - not doing so will destroy
# the array...
my @devices = @ARGV;
# how many devices?
my $num_devices = scalar @devices;
if ($num_devices < 2) {
  die "$0 needs at least two component devices\n";
}
# how many base permutations...
my $num_permutations = factorial(scalar @devices);
# try all permutations, substituting 'missing' for each device in
# turn...
for (my $d=0; $d < $num_devices; $d++) {
  my $skip_device = $devices[$d];
  $devices[$d] = "missing";
  print "skipping $skip_device\n\n";
  for (my $i=0; $i < $num_permutations; $i++) {
    my @permutation = @devices[n2perm($i, $#devices)];
    try_array(@permutation);
  }
  $devices[$d] = $skip_device;
}

################################################################
# permutation code

# n2pat($N, $len) : produce the $N-th pattern of length $len
sub n2pat {
    my $i   = 1;
    my $N   = shift;
    my $len = shift;
    my @pat;
    while ($i <= $len + 1) {   # Should really be just while ($N) { ...
        push @pat, $N % $i;
        $N = int($N/$i);
        $i++;
    }
    return @pat;
}

# pat2perm(@pat) : turn pattern returned by n2pat() into
# permutation of integers.  XXX: splice is already O(N)
sub pat2perm {
    my @pat    = @_;
    my @source = (0 .. $#pat);
    my @perm;
    push @perm, splice(@source, (pop @pat), 1) while @pat;
    return @perm;
}

# n2perm($N, $len) : generate the Nth permutation of $len objects
sub n2perm {
    pat2perm(n2pat(@_));
}

# Utility function: factorial with memoizing
BEGIN {
  my @fact = (1);
  sub factorial($) {
    my $n = shift;
    return $fact[$n] if defined $fact[$n];
    $fact[$n] = $n * factorial($n - 1);
  }
}
```



Running the code gives me the error:


```

djh@fs01:~$ sudo ./Permute_array.pl
using device /dev/md0 and mounting on /Data
./Permute_array.pl needs at least two component devices

```



Im guessing it's this part?    

my @device_list = @_["/dev/sdb1", "/dev/sdc1", "/dev/sdd1", "/dev/sdf1", "/dev/sdh1", "/dev/sdi1", "/dev/sdj1", "/dev/sdk1"];
my $num_devices = scalar $_["8"];


Thanks

DJH

---

### Post by djh82uk on 2013-05-20
Ok, well was worth a try, got the script running, it takes about 10 mins but comes back with the following command to run:

```
sudo mdadm --create --assume-clean /dev/md0 --raid-devices=8 --level=5  missing /dev/sdc1 /dev/sdd1 /dev/sdj1 /dev/sdk1 /dev/sdf1 /dev/sdi1 /dev/sdh1 2>/dev/null
```


It just sits there forever, what does "2>/dev/null" do?

Without it, it creates the array, but still cannot mount, so i guess the data really is gone. :(


Ran it again and it came back with a different sequence, so perhaps the script is not that good, or my array is totally messed up

Thanks

DJH

---

### Post by darkod on 2013-05-21
Before trying all different combinations, I would try remembering the flow of events, if you can. For example, if the disks were in order when first creating the array, and if they were 8 from the start, the most probable order would be: BCDEFGHI. Later if E failed for example, it can be replaced with J but the slot for J will still be number 3 (they count from 0). So, like BCDJFGHI.

I know this is not easy, but try considering what you did with this array and try those few combinations of disk order.

---

### Post by rubylaser on 2013-05-21
> **darkod said:**
> Before trying all different combinations, I would try remembering the flow of events, if you can. For example, if the disks were in order when first creating the array, and if they were 8 from the start, the most probable order would be: BCDEFGHI. Later if E failed for example, it can be replaced with J but the slot for J will still be number 3 (they count from 0). So, like BCDJFGHI.

I know this is not easy, but try considering what you did with this array and try those few combinations of disk order.

+1. Sorry, I wasn't clear.  This is exactly what you would want to do first.

---

