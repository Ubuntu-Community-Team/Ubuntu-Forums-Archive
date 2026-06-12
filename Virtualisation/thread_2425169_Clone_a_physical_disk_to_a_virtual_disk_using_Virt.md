---
title: "Clone a physical disk to a virtual disk using Virtualbox and a live CD"
date: 2019-08-21
forum: Virtualisation
---

### Post by vcrpcant on 2019-08-21
=============================================
clone a physical disk to a virtual disk
using Virtualbox and a live CD

see my similar tutorial from 2017 here:
[https://ubuntuforums.org/showthread.php?t=2360974](https://ubuntuforums.org/showthread.php?t=2360974)

context
someone has an encrypted linux operative system in a physical hard drive
and wants to convert that to a virtual machine with a virtual hard drive (VDI)

you must have Virtualbox installed

=============================================
the new disk (VDI) must have the same number of partitions:
boot (not encrypted)
swap (luks encrypted)
root (luks encrypted)

this I am not sure
the partitions must be formatted the same (ext2, ext4, etc)
if the original partitions are encrypted, the cloned partitions must also be encrypted
use a live CD with the same architecture (32 bit or 64 bit)

=============================================
create the virtual disk

VBoxManage createhd --filename /home/user1/my-new-clone-disk.vdi --size 30000 --format VDI
note:
--size 30000 means 30GB

chmod 777 /home/user1/my-new-clone-disk.vdi

chown user1:user1 /home/user1/my-new-clone-disk.vdi

=============================================
partition the virtual disk

create a new virtual machine in Virtualbox with:
- the new virtual disk (VDI)
- the live CD (or a linux guest with the same architecture (32 bit or 64 bit))

start the virtual machine

=============================================
guest

if fedora, centoOS or similar
    system-config-keyboard
    dnf install openssh-server
    dnf install cryptsetup
    nano /etc/ssh/sshd_config
        make appropriate changes
    service sshd restart
    passwd root
    passwd "user" (to see the user name open the terminal and see after $)
    ip a

if debian, ubuntu or similar
    apt update
    install openssh-server
    cryptsetup: nao é preciso instalar, ja está
    mousepad /etc/ssh/sshd_config
        make appropriate changes
    service sshd restart
    passwd root
    passwd "user" (to see the user name open the terminal and see after $)
    ip a
    in debian buster 10 if I change display resolution I won't be able to mount the encrypted mapped devices after, I don't know why
        if you don't believe, change it, then run "ls /dev/mapper" and see only "control" appear and nothing else

=============================================
host, login via ssh to guest
ssh root@"guest-ip-address"
if the key already exists, remove it and enter ssh again with these two commands
ssh-keygen -f "/user1/.ssh/known_hosts" -R "guest-ip-address" && ssh root@"guest-ip-address"

=============================================
guest

list disks
fdisk -l

now we must format the virtual disk with the 3 partitions, just like the original disk
1 - boot
2 - swap
3 - root

but first, in the host, check where these 3 partitions start and end
host
parted /dev/sdx
(parted) u s [unit sectors]
(parted) p [print, the partition table: shows each partition start and end sectors]
(parted) q [quit]

guest
parted /dev/sdx
(parted) mklabel msdos ou mklabel gpt [same as the original disk in the host]
(parted) u s
(parted) mkpart
fill the same details (and start and end sectors, as in the host original disk)

do the same for swap and root partitions
when asking about ext2, etc, just choose ext4 for example, they will be luks formatted below anyway

set boot flag on partition boot (partition 1)
(parted) set 1 boot on

print the partition table
and check if it is the same as the partition table of the original disk (start and end sectors)
(parted) p

quit
(parted) q

=============================================
create filesystems

boot
mkfs.ext4 /dev/sdx1
if your original disk has boot in ext2, also do ext2 here, or ext3

swap
cryptsetup luksFormat --cipher aes-cbc-essiv:sha256 --verify-passphrase --key-size 256 /dev/sdx2
cryptsetup luksOpen /dev/sdx2 SWAP_crypt
mkswap /dev/mapper/SWAP_crypt

root
cryptsetup luksFormat --cipher aes-cbc-essiv:sha256 --verify-passphrase --key-size 256 /dev/sdx3
cryptsetup luksOpen /dev/sdx3 ROOT_crypt
mkfs.ext4 /dev/mapper/ROOT_crypt

see the mapped devices
ls /dev/mapper

mount
mount /dev/mapper/ROOT_crypt /mnt

observe that the directory /boot is excluded here:
rsync -aAXv -e "ssh -p 55555" root@"host-ip-address":/* /mnt/ --exclude={"/boot/*","/dev/*","home/user1/.cache/*","home/user1/.thumbnails/*","/lost+found","/media/*","/mnt/*","/proc/*","root/.cache/*","root/.thumbnails/*","/run/*","/sys/*","/tmp/*","/var/tmp/*"}

mount /dev/sdx1 /mnt/boot
rsync -aAXv -e "ssh -p 55555" root@"host-ip-address":/boot/* /mnt/boot/

=============================================
in fstab and crypttab, change:
sda2_crypt and sda3_crypt
to
SWAP_crypt and ROOT_crypt

nano /mnt/etc/fstab
nano /mnt/etc/crypttab

and update the partitions' UUID's
to know them just run
blkid

in fstab and crypttab, comment all eventual partitions that you wont mount on this cloned disk
this will prevent you from waiting when you boot onto the cloned system later

=============================================
nano /mnt/etc/initramfs-tools/conf.d/resume
change
RESUME=sda2_crypt
to
RESUME=SWAP_crypt

=============================================
chroot:

mount --bind /dev /mnt/dev
mount --bind /dev/pts /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys

chroot /mnt

=============================================
update initramfs:

update-initramfs -u -k all

if these errors appears, just ignore them:
update-initramfs: Generating /boot/initrd.img-4.19.0-5-amd64
W: mkconf: MD subsystem is not loaded, thus I cannot scan for arrays.
W: mdadm: failed to auto-generate temporary mdadm.conf file.

=============================================
install grub:

grub-install /dev/sdx

update-grub

if errors like these appear, just ignore them:
WARNING: Device /dev/loop0 not initialized in udev database even after waiting 10000000 microseconds.

google showed:
these appear to be benign warning messages
though can burn up several minutes until the process terminates after the reported devices are probed repeatedly

=============================================
exit chroot:

exit
umount /mnt/dev/pts
umount /mnt/dev
umount /mnt/proc
umount /mnt/sys
umount /mnt/boot
umount /mnt

or
umount /mnt/dev/pts && sleep 1 && umount /mnt/dev && sleep 1 && umount /mnt/proc && sleep 1 && umount /mnt/sys && sleep 1 && umount /mnt/boot && sleep 1 && umount /mnt

shutdown -h now

remove live CD from the virtual machine settings

start the virtual machine

enjoy!

=============================================
notes

the new virtual machine with the cloned disk should boot properly in the first time

but, if on the second time it hangs while booting, in this message:
"a start job is running for /dev/mapper/cryptswap"

is because maybe you missed this step:
nano /mnt/etc/initramfs-tools/conf.d/resume
change
RESUME=sda2_crypt
to
RESUME=SWAP_crypt

in this case, shutdown the virtual machine
and try to start it several times until it starts well
it will after a few tries or even the next one

then, just disable swap by commenting it's line in fstab and crypttab
if this virtual machine will not be used often and is just to archive or system backup, etc
and then run
update-initramfs -u -k all

or recreate swap, if you prefer or you are going to use it often:
cryptsetup luksFormat --cipher aes-cbc-essiv:sha256 --verify-passphrase --key-size 256 /dev/sdx2
cryptsetup luksOpen /dev/sdx2 SWAP_crypt
mkswap /dev/mapper/SWAP_crypt

=============================================
thanks to Debian Forum members, especially p.H., who helped me on these two posts:
[http://forums.debian.net/viewtopic.php?f=10&t=143279](http://forums.debian.net/viewtopic.php?f=10&t=143279)
[http://forums.debian.net/viewtopic.php?f=10&t=143295&sid=f65bd7a1f48e761d2d51ecc4f5365c67](http://forums.debian.net/viewtopic.php?f=10&t=143295&sid=f65bd7a1f48e761d2d51ecc4f5365c67)

=============================================

improvements or suggestions are welcome!

=============================================

---

