---
title: "Creating a VM fails with partitioning or formatting of img file"
date: 2009-08-19
forum: Virtualisation
---

### Post by frippz on 2009-08-19
Got a server that runs several VM:s under 8.10. I just decided to create another one using vmbuilder. I have a bash script that I use for every machine I want to create, and I just change key options each.

```
sudo vmbuilder kvm ubuntu -v \
--suite=intrepid \
--flavour=virtual \
--arch=amd64 -o \
--libvirt=qemu:///system \
--tmpfs=- \
--ip=213.xxx.xxx.98 \
--mask=255.xxx.xxx.128 \
--net=213.xxx.xxx.0/25 \
--bcast=213.xxx.xxx.127 \
--gw=213.xxx.xxx.1 \
--dest=scm \
--part=vmbuilder.partition \
--templates=mytemplates \
--user=[username] \
--name=[name] \
--pass=[password] \
--addpkg=bash-completion \
--addpkg=aptitude \
--addpkg=nano \
--addpkg=wget \
--addpkg=unattended-upgrades \
--addpkg=acpid \
--firstboot=boot.sh \
--mem=1024 \
--hostname=[hostname]
```

This time around, though, vmbuilder throws an error.

```
2009-08-19 14:40:35,386 DEBUG    part: root, size: 50688
2009-08-19 14:40:35,386 DEBUG    part: swap, size: 512
2009-08-19 14:40:35,386 DEBUG    do_disk - size: 51200
2009-08-19 14:40:35,387 DEBUG    do_disk - part: root, size: 50688, offset: 0
2009-08-19 14:40:35,387 DEBUG    add_part - begin 0, length 50688, end 50687
2009-08-19 14:40:35,387 DEBUG    do_disk - part: swap, size: 512, offset: 50688
2009-08-19 14:40:35,387 DEBUG    add_part - begin 50688, length 512, end 51199
2009-08-19 14:40:35,387 DEBUG    ip: 213.xxx.xxx.98
2009-08-19 14:40:35,388 DEBUG    net: 213.xxx.xxx.0/25
2009-08-19 14:40:35,388 DEBUG    netmask: 255.255.255.128
2009-08-19 14:40:35,388 DEBUG    broadcast: 213.xxx.xxx.127
2009-08-19 14:40:35,388 DEBUG    gateway: 213.xxx.xxx.1
2009-08-19 14:40:35,388 DEBUG    dns: 213.xxx.xxx.1
2009-08-19 14:40:35,388 DEBUG    Checking if firstboot script boot.sh exists
2009-08-19 14:40:35,398 DEBUG    Temporary directory: /tmp/vmbuilderiox6Pt
2009-08-19 14:40:35,398 DEBUG    Creating the root mount directory: /tmp/vmbuilderiox6Pt/target
2009-08-19 14:40:35,398 DEBUG    Creating temporary root: /tmp/vmbuilderiox6Pt/root
2009-08-19 14:40:35,398 DEBUG    Creating destination directory: scm
2009-08-19 14:40:35,398 INFO     Creating disk image: /tmp/vmbuilderiox6Pt/disk0.img
2009-08-19 14:40:35,399 DEBUG    ['/usr/bin/kvm-img', 'create', '-f', 'raw', '/tmp/vmbuilderiox6Pt/disk0.img', '51201M']
2009-08-19 14:40:35,402 DEBUG    Formatting '/tmp/vmbuilderiox6Pt/disk0.img', fmt=raw, size=52429824 kB
2009-08-19 14:40:35,402 INFO     Adding partition table to disk image: /tmp/vmbuilderiox6Pt/disk0.img
2009-08-19 14:40:35,402 DEBUG    ['parted', '--script', '/tmp/vmbuilderiox6Pt/disk0.img', 'mklabel', 'msdos']
2009-08-19 14:40:35,408 INFO     Adding type 1 partition to disk image: /tmp/vmbuilderiox6Pt/disk0.img
2009-08-19 14:40:35,409 DEBUG    ['parted', '--script', '--', '/tmp/vmbuilderiox6Pt/disk0.img', 'mkpart', 'primary', 'ext2', '0', '50687']
2009-08-19 14:40:35,414 INFO     Adding type 3 partition to disk image: /tmp/vmbuilderiox6Pt/disk0.img
2009-08-19 14:40:35,414 DEBUG    ['parted', '--script', '--', '/tmp/vmbuilderiox6Pt/disk0.img', 'mkpart', 'primary', 'linux-swap', '50688', '51199']
2009-08-19 14:40:35,419 INFO     Creating loop devices corresponding to the created partitions
2009-08-19 14:40:35,419 DEBUG    ['kpartx', '-av', '/tmp/vmbuilderiox6Pt/disk0.img']
2009-08-19 14:40:35,428 DEBUG    gpt: 0 slices
2009-08-19 14:40:35,428 DEBUG    dos: 4 slices
2009-08-19 14:40:35,429 DEBUG    add map loop0p1 (254:0): 0 98997984 linear /dev/loop0 32
2009-08-19 14:40:35,429 DEBUG    add map loop0p2 (254:2): 0 998144 linear /dev/loop0 98999936
2009-08-19 14:40:35,429 INFO     Creating file systems
2009-08-19 14:40:35,430 DEBUG    intrepid: 256 bit inode
2009-08-19 14:40:35,430 DEBUG    ['mkfs.ext3', '-F', '/dev/mapper/loop0p1']
2009-08-19 14:40:35,433 INFO     mke2fs 1.41.3 (12-Oct-2008)
2009-08-19 14:40:36,222 INFO     
2009-08-19 14:40:36,224 INFO     Warning, had trouble writing out superblocks.
2009-08-19 14:40:36,224 DEBUG    Filesystem label=
2009-08-19 14:40:36,224 DEBUG    OS type: Linux
2009-08-19 14:40:36,225 DEBUG    Block size=4096 (log=2)
2009-08-19 14:40:36,225 DEBUG    Fragment size=4096 (log=2)
2009-08-19 14:40:36,225 DEBUG    3096576 inodes, 12374748 blocks
2009-08-19 14:40:36,226 DEBUG    618737 blocks (5.00%) reserved for the super user
2009-08-19 14:40:36,226 DEBUG    First data block=0
2009-08-19 14:40:36,226 DEBUG    Maximum filesystem blocks=4294967296
2009-08-19 14:40:36,226 DEBUG    378 block groups
2009-08-19 14:40:36,227 DEBUG    32768 blocks per group, 32768 fragments per group
2009-08-19 14:40:36,227 DEBUG    8192 inodes per group
2009-08-19 14:40:36,228 DEBUG    Superblock backups stored on blocks:
2009-08-19 14:40:36,228 DEBUG           32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
2009-08-19 14:40:36,228 DEBUG           4096000, 7962624, 11239424
2009-08-19 14:40:36,229 DEBUG    
2009-08-19 14:40:36,269 DEBUG    Writing inode tables: done378
2009-08-19 14:40:36,270 DEBUG    Creating journal (32768 blocks): done
2009-08-19 14:40:36,270 DEBUG    Writing superblocks and filesystem accounting information: done
2009-08-19 14:40:36,279 DEBUG    
2009-08-19 14:40:36,290 DEBUG    This filesystem will be automatically checked every 21 mounts or
2009-08-19 14:40:36,300 DEBUG    180 days, whichever comes first.  Use tune2fs -c or -i to override.
2009-08-19 14:40:36,860 DEBUG    Oh, dear, an exception occurred
2009-08-19 14:40:36,860 INFO     Cleaning up
2009-08-19 14:40:36,860 DEBUG    ['kpartx', '-d', '/tmp/vmbuilderiox6Pt/disk0.img']
2009-08-19 14:40:36,867 DEBUG    gpt: 0 slices
2009-08-19 14:40:36,868 DEBUG    dos: 4 slices
2009-08-19 14:40:36,868 DEBUG    loop deleted : /dev/loop0
2009-08-19 14:40:36,868 DEBUG    ['rmdir', 'scm']
2009-08-19 14:40:36,871 DEBUG    ['rm', '-rf', '/tmp/vmbuilderiox6Pt']
Traceback (most recent call last):
  File "/usr/bin/vmbuilder", line 29, in <module>
    VMBuilder.run()
  File "/usr/lib/python2.5/site-packages/VMBuilder/__init__.py", line 66, in run
    frontend.run()
  File "/usr/lib/python2.5/site-packages/VMBuilder/plugins/cli/__init__.py", line 67, in run
    vm.create()
  File "/usr/lib/python2.5/site-packages/VMBuilder/vm.py", line 453, in create
    raise e
VMBuilder.exception.VMBuilderException: Process (['mkfs.ext3', '-F', '/dev/mapper/loop0p1']) returned 1. stdout: Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
3096576 inodes, 12374748 blocks
618737 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
378 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 21 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
, stderr: mke2fs 1.41.3 (12-Oct-2008)

Warning, had trouble writing out superblocks.
```

So apparently, something fails when vmbuilder tries to either partition or format the image file prior to installation. I really have no idea why it behaves like this now. It used to work without a hitch before.

---

