---
title: "Upgraded ubuntu server 21.03 won't mount and display data"
date: 2022-04-06
forum: Server Platforms
---

### Post by ccor58 on 2022-04-06
I recently had nfs-kernel-server v 20.04 problems not starting due to found cycles; then manually restarting it after doing mount -a only lasted a short time and server froze intermittently. Lost motherboard so rebuilt server on new box with vers 21.03. Managed to get server installed finally, ran into troubles with installer (RAID, LVM etc and cloud add ons in addition to UEFI). 

I managed to salvage all previous share data and contents and put it on a separate 2 TB hard drive with three partitions. When attached to a ubuntustudio desktop OS the mount points.
The three partitions showed up in the desktop's filesystem properly as /opt , /misc . /data and icons appeared on the desktop and would properly mount with a mount -a command through fstab file granting access to data files.

However where the problem arose is removing the ubuntustudio desktp OS drive and replacing it with the ubuntu server OS drive and attempting to add the mount points the same way automatically using mount -a through fstab in the server box, the icons appear on the desktop but will not mount and display data. I need to be able to successfully mount them all in order to use fstab to also auto set up the exports files for the NFS file system as well.

Here is what I am experiencing so far and any tips would be appreciated thanks :

[COLOR=#0000ff]# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/ubuntu-vg/ubuntu-lv during curtin installation
[/COLOR][COLOR=#ff0000]***/dev/disk/by-id/dm-uuid-LVM-***[/COLOR][COLOR=#0000ff]KR47Be3ndZ2FBZh0P4zne8Nf03fDzDTS66unFejw2Ise0ArBfClgbiwKcVUY7ktL / ext4 defaults 0 1

dev/disk/by-id/dm-uuid-a212b65a-8a8d-4ac3-af87-3694d7c0590c /opt ext4 defaults 0 1

dev/disk/by-id/dm-uuid-e5bc290c-568d-4963-8924-aa69333fe2e3 /misc ext4 defaults 0 1

dev/disk/by-id/dm-uuid-262a7060-0905-4eaf-bc3d-5df50b9bc66f /data ext4 defaults 0 1

dev/disk/by-id/dm-uuid-6D6A77DF36E4CDED /smbshare  NTFS/exFAT/HPFS defaults 0 1

dev/disk/by-id/dm-uuid-6b8c4274-33ce-4559-aad8-f595d80a3fcf /nsfDatatemp ext4 defaults 0 1


# /boot was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/c5126a6f-0ec3-4ce9-a807-f81efc2a7134 /boot ext4 defaults 0 1
/swap.img       none    swap    sw      0       0
#/dev/disk/by-uuid/6b8c4274-33ce-4559-aad8-f595d80a3fcf /mnt/6b8c4274-33ce-4559-aad8-f595d80a3fcf auto nosuid,nodev,nofail,x-gvfs-show 0 0
[/COLOR]
Error when mount -a input

root@woodchipper:userid# mount -a
mount: /opt: special device dev/disk/by-id/dm-uuid-a212b65a-8a8d-4ac3-af87-3694d7c0590c does not exist.
mount: /misc: mount point does not exist.
mount: /data: mount point does not exist.
mount: /smbshare: mount point does not exist.
mount: /nsfDatatemp: mount point does not exist.
root@woodchipper:userid# 

The partition UUID from gnome-disks output was used but how it relates to LVM or RAID I have not found a really good tutorial on such uses having always just dealt with standalone legacy drives with no UEFI either.

---

### Post by TheFu on 2022-04-06
21.03  Huh?  That isn't any ubuntu release.  BTW, 21.04 is beyond EOL and shouldn't be used.
If you can't migrate the OS every 6 months, stick with LTS releases - 20.04 and in a few weeks, 22.04 is next.

Details matter.  Starting with the release being used.

Those super-long device names are completely unnecessary.  LVM storage can be accessed using 
**[COLOR="#FF0000"]/[/COLOR]**dev/<vgname>/<lvname>  which is much shorter, but still provides very useful information. Use that in the fstab.

Other storage can use LABEL= or UUID= options instead of the super-long device links.  Which is used is your choice. **lsblk** or **blkid** commands can provide the mapping between the UUID and the other device names, if you like. blkid doesn't need any options.  lsblk does.

I'm assuming no ZFS or BTRFS.

The fstab doesn't care about uefi, except to mount the FAT32 partition to /boot/efi.  Nothing else.

---

### Post by ccor58 on 2022-04-06
Thanks for info I will look for 22.04 as soon as it is available then. but the current one is what it went to when I was given an option in 20.04 LTS to auto upgrade from 20.04. To add confusion the server installers changed twice since I did the first 20.04 install. The first newer one offers a RAID option and an LVM option then the second one offers the same options but will not allow one to proceed with install unless an LVM name label was given so not understanding anything about RAID or LVM or cloud options being only familiar with Legacy standalone hard drive installs I hesitated to select anything blindly.

I don't suppose you might know of somewhat plain english for newbies pdf tutorial that might explain these a bit more; the built in help on the install screen seemed lacking.
Thanks again

---

### Post by TheFu on 2022-04-07
_21.04 isn't current._ It was EOL in January.  Use 20.04, 18.04 or if you don't want LTS, 21.10 is current until June-July.
For production, I wouldn't suggest anyone use 22.04 until June, after the biggest bugs are fixed and released.  

As for LVM, RAID or LVM+RAID, a few weeks ago, I setup a disk using LVM-RAID (no mdadm commands at all).  Works perfect and provides all the extra enterprise volume management features that LVM provides.

If your goal is NOT to be a server admin, then stick with desktop releases and add on the server packages you want.

LVM maps to how all Unix LVM systems work - like those from Veritas, HP, AIX and others.  Solaris moved away from LVM around 2006 when they started pushing ZFS.  It is a completely different way of thinking about storage.

I'd be surprised if the any server installer _mandated_ using LVM or mdadm at all.  I've just never seen it that way.  About a year ago, I got tired of using the less-than-great disk setup options in any Canonical installers and just after the installer begins, I switch to a different console and setup the storage in the way I like using some scripts I wrote. These aren't general purpose and fit my needs only.  Plus, I **prefer** to use LVM on multi-disk systems, but I've been dealing with advanced storage setups since the 1990s.

There are lots of how-to guides for LVM.  Pick one.  Create a VM and work through it, following their LVM setup.  If you aren't using VMs already, then I'd think you aren't ready for LVM or RAID either.  The good news is that LVM doesn't have any GUI and all the same commands on any Linux work on all the others.  LVM == LVM, distro agnostic.  They all have PEs, PVs, VGs, LVs, and all use them the same way. No surprises.  The main concept to LVM that will save you is to never actually allocate all the storage to LVs. _***Always allocate only what is needed for 3 months at a time, no more.***_  Many of my systems are less than 50% for storage.  For example:
```
nvme0n1                    465.8G disk                     
&#9500;&#9472;nvme0n1p1                   50M part vfat     EFI        
&#9500;&#9472;nvme0n1p2                  600M part ext2     BOOT-A     
&#9492;&#9472;nvme0n1p3                  465G part LVM2_mem            
  &#9500;&#9472;vg00-swap                4.1G lvm  swap                
  &#9500;&#9472;vg00-root                 35G lvm  ext4     root       
  &#9500;&#9472;vg00-var                  35G lvm  ext4     var        
  &#9492;&#9472;vg00-home                 25G lvm  ext4     home
```
that's a media server system running a few VMs, containers and jellyfin with over 40TB connected.  But the base OS is as above.  If you count all the allocations, you'll see that LVM has 465G, but I've only allocated less than 100G. The rest will be used for expansion when needed and for new LVs to be mounted elsewhere, should those needs arise.  The empty storage gets used nightly for snapshots to ensure backup areas are quiesced completely.  /home, above, is about 2x larger than needed. It currently uses 13G.  

My storage layouts are about backup, recovery and disaster recovery. I want to minimize the OS stuff and keep those allocations away from any data.  Data is always stored somewhere else, never with the OS or in /home.

---

### Post by rsteinmetz70112 on 2022-04-07
It sounds like you system may not be set to upgrade to LTS only and you were offered an upgrade from 20.04 to something else. You will need to set your computer to upgrade only to LTS releases.  But first please open a terminal windows and run this command.
```
lsb_release -a
```
copy and paste the results in a reply using the ```
 tags.


Then in the same window run 
[CODE]$ lsblk
```
Copy and paste the results using code tags.

From the output above it appears some of your mountpoints are missing and you fstab has a problem.

I'm not sure but you may still be able to do a release upgrade to get to a current release until 22.04 comes out.

---

### Post by ccor58 on 2022-04-12
Apr 10 00:09:25 woodchipper snapd[1045]: daemon.go:246: started snapd/2.54.4 (series 16; classic) ubuntu/21
.10 (amd64) linux/5.13.0-39-generic.

Startup login screen shows ubuntu 21.04

root@woodchipper:/home/userID# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 21.10
Release:        21.10
Codename:       impish
root@woodchipper:/home/userID# 

# cat /etc/os-release
PRETTY_NAME="Ubuntu 21.10"
NAME="Ubuntu"
VERSION_ID="21.10"
VERSION="21.10 (Impish Indri)"
VERSION_CODENAME=impish
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=impish
root@woodchipper:/home/webbae# 
root@woodchipper:/home/webbae# lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0                       7:0    0  61.8M  1 loop /snap/core20/1169
loop1                       7:1    0  73.2M  1 loop /snap/lxd/21624
loop2                       7:2    0  79.9M  1 loop /snap/lxd/22826
loop3                       7:3    0  44.6M  1 loop /snap/snapd/15314
loop4                       7:4    0  61.9M  1 loop /snap/core20/1405
loop5                       7:5    0  43.6M  1 loop /snap/snapd/15177
sda                         8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1                      8:1    0     1M  0 part 
&#9500;&#9472;sda2                      8:2    0     1G  0 part /boot
&#9492;&#9472;sda3                      8:3    0 930.5G  0 part 
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0   200G  0 lvm  /
sdb                         8:16   0   1.8T  0 disk 
&#9500;&#9472;sdb1                      8:17   0 131.7G  0 part /exports/misc
&#9500;&#9472;sdb2                      8:18   0 468.5G  0 part /data
&#9492;&#9472;sdb3                      8:19   0   1.2T  0 part /opt
sdc                         8:32   0 931.5G  0 disk 
&#9500;&#9472;sdc1                      8:33   0 452.7G  0 part 
&#9492;&#9472;sdc2                      8:34   0 478.8G  0 part 
sr0                        11:0    1  1024M  0 rom  



[COLOR=#ff0000]fstab below is working half way for me:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/ubuntu-vg/ubuntu-lv during curtin installation
/dev/disk/by-id/dm-uuid-LVM-KR47Be3ndZ2FBZh0P4zne8Nf03fDzDTS66unFejw2Ise0ArBfClgbiwKcVUY7ktL / ext4 defaults 0 1

/dev/sdb1 /misc auto rw,noauto,user,exec 0 0

/dev/sdb2 /data auto rw,noauto,user,exec 0 0

/dev/sdb3 /opt auto rw,noauto,user,exec 0 0

/dev/sdc1 /nfsDatabackup auto rw,noauto,user,exec 0 0

/dev/sdc2 /smbshare auto rw,noauto,user,exec 0 0


# /boot was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/c5126a6f-0ec3-4ce9-a807-f81efc2a7134 /boot ext4 defaults 0 1
/swap.img       none    swap    sw      0       0

#CEDAR
#/srv/nfs/cedar          /exports/cedar                  nfs rw,bind 0 0
#/srv/nfs/videos         /exports/videos                 nfs rw,bind 0 0

#LILAC
#/srv/nfs/lilac          /exports/lilac                  nfs rw,bind 0 0
#/srv/nfs/videos         /exports/videos                 nfs rw,bind 0 0

#PINE
#/srv/nfs/pine           /exports/pine                   nfs rw,bind 0 0
#/srv/nfs/videos         /exports/videos                 nfs rw,bind 0 0

#VE4PER
#/srv/nfs/ve4per         /exports/ve4per                 nfs rw,bind 0 0
#/srv/nfs/videos         /exports/videos                 nfs rw,bind 0 0

#WILLOW
#/srv/nfs/willow         /exports/willow                 nfs rw,bind 0 0
#/srv/nfs/videos         /exports/videos                 nfs rw,bind 0 0

#WOODCHIPPER
/data/sharedata1        /exports/sharedata1                   nfs rw,bind 0 0
/data/sharedata2        /exports/sharedata2                   nfs rw,bind 0 0
/data/sharentfs1        /exports/sharentfs1                   nfs rw,bind 0 0

/misc                   /exports/misc                        nfs rw,bind 0 0

/opt/graphics           /exports/graphics                     nfs rw,bind 0 0
/opt/production         /exports/production                   nfs rw,bind 0 0
/opt/snd                /exports/snd                          nfs rw,bind 0 0
/opt/music              /exports/music                        nfs rw,bind 0 0

/opt/videos              /exports/videos                       nfs rw,bind 0 0
/var/www                /exports/websites                     nfs rw,bind 0 0
/srv/nfs/woodchipper    /exports/woodchipper                  nfs rw,bind 0 0
#####----------------------------------------------------------------------------------------------------------####
#This section mounts NFS shares to the media subfolder structure from this and other network
#NFS machines.

#cedar
#192.168.149.12:/exports/cedar                     /media/nfs-client/cedar/cedar             nfs defaults 0 0
#192.168.149.12:/exports/videos                   /media/nfs-client/cedar/videos                nfs defaults 0 0


#lilac
#192.168.149.3:/exports/lilac                      /media/nfs-client/lilac/lilac                   nfs defaults 0 0
#192.168.149.3:/exports/videos                     /media/nfs-client/lilac/videos                nfs defaults 0 0


#pine
#192.168.149.9:/exports/pine                      /media/nfs-client/pine/pine                nfs defaults 0 0
#192.168.149.9:/exports/videos                     /media/nfs-client/pine/videos                nfs defaults 0 0

#ve4per
#192.168.149.5:/exports/ve4per                   /media/nfs-client/ve4per/ve4per                   nfs defaults 0 0
#192.168.149.5:/exports/videos                   /media/nfs-client/ve4per/videos                   nfs defaults 0 0

#willow
#192.168.149.16:/exports/willow                   /media/nfs-client/willow/willow            nfs defaults 0 0
#192.168.149.16:/exports/videos                   /media/nfs-client/willow/videos                nfs defaults 0 0

#woodchipper
#192.168.149.2:/exports/graphics         /media/nfs-client/woodchipper/woodgraphics          nfs defaults 0 0
#192.168.149.2:/exports/production       /media/nfs-client/woodchipper/woodproduction        nfs defaults 0 0
#192.168.149.2:/exports/snd              /media/nfs-client/woodchipper/woodsnd               nfs defaults 0 0
#192.168.149.2:/exports/music            /media/nfs-client/woodchipper/woodsongs             nfs defaults 0 0
#192.168.149.2:/exports/sql              /media/nfs-client/woodchipper/woodsql               nfs defaults 0 0
#192.168.149.2:/exports/videos           /media/nfs-client/woodchipper/woodvideos            nfs defaults 0 0
#192.168.149.2:/exports/websites         /media/nfs-client/woodchipper/woodwebsites          nfs defaults 0 0
#192.168.149.2:/exports/woodchipper      /media/nfs-client/woodchipper/woodchipper           nfs defaults 0 0
#192.168.149.2:/exports/sharedata1       /media/nfs-client/woodchipper/sharedata1            nfs defaults 0 0
#192.168.149.2:/exports/sharedata2       /media/nfs-client/woodchipper/sharedata2            nfs defaults 0 0
#192.168.149.2:/exports/sharentfs1       /media/nfs-client/woodchipper/sharentfs1            nfs defaults 0 0
#192.168.149.2:/exports/misc             /media/nfs-client/woodchipper/misc                  nfs defaults 0 0[/COLOR]

[COLOR=#0000ff][I]/etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#       to NFS clients. See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes gss/krb5i(rw,sync,no_subtree_check)
#

# /etc/exports: the access control list for filesystems which may be exported
#       to NFS clients. See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes gss/krb5i(rw,sync,no_subtree_check)
#




#WOODCHIPPER
/exports/graphics                       192.168.149.0/24(rw,sync,no_subtree_check)
/exports/music                          192.168.149.0/24(rw,sync,no_subtree_check)
/exports/production                     192.168.149.0/24(rw,sync,no_subtree_check)
/exports/snd                            192.168.149.0/24(rw,sync,no_subtree_check)
#/exports/sql                            192.168.149.0/24(rw,sync,no_subtree_check)
/exports/videos                         192.168.149.0/24(rw,sync,no_subtree_check)
/exports/websites                       192.168.149.0/24(rw,sync,no_subtree_check)
/exports/woodchipper                    192.168.149.0/24(rw,sync,no_subtree_check)
/exports/sharedata1                     192.168.149.0/24(rw,sync,no_subtree_check)
/exports/sharedata2                     192.168.149.0/24(rw,sync,no_subtree_check)
/exports/sharentfs1                     192.168.149.0/24(rw,sync,no_subtree_check)
/exports/misc                           192.168.149.0/24(rw,sync,no_subtree_check)


# exportfs
/exports/graphics
                192.168.149.0/24
/exports/music  192.168.149.0/24
/exports/production
                192.168.149.0/24
/exports/snd    192.168.149.0/24
/exports/videos
                192.168.149.0/24
/exports/websites
                192.168.149.0/24
/exports/woodchipper
                192.168.149.0/24
/exports/sharedata1
                192.168.149.0/24
/exports/sharedata2
                192.168.149.0/24
/exports/sharentfs1
                192.168.149.0/24
/exports/misc   192.168.149.0/24

Remote W/S's do not mount these shares; the server here does not enable data to be available when mounted either using mount -a
[/I][/COLOR]

---

### Post by TheFu on 2022-04-12
Please wrap all text output seen in a terminal with forum 'code tags', so the columns line up correctly.  I did that in my post above. See how easy it is too read the lsblk output?  That's what we need from your post. 

Please.

Also, large numbers of lines with comments just get in the way. Please remove to prevent confusion.

Don't mount using direct device names like /dev/sdb1. Those are variable and change from boot to boot. They are not guaranteed to be the same order every time.  Use either the LABEL or UUID for those partition devices to avoid issues.
```
 /dev/disk/by-uuid/c5126a6f-0ec3-4ce9-a807-f81efc2a7134 /boot ext4 defaults 0 1
```
should be
```
UUID=c5126a6f-0ec3-4ce9-a807-f81efc2a7134    /boot    ext4    defaults   0    1
```
Longer lines are an opportunity for a mistake. If there isn't any useful, extra, information provided, then don't have longer lines that aren't necessary.  Avoiding mistakes in advance is good, proven, way to a more stable system.

What's the point of the different colors?  I'm just confused.

---

### Post by ccor58 on 2022-04-14
all of the fstab command lines are being properly handled. the original files being specified to share in the exports folders are showing and available using the file manager to view the exports folders directly. The folders data, opt, & misc are being shown correctly with files accessible using the file manager also. exportfs command shows that the exported folder contents are being made correctly available to clients at the correct 192.168.149.0/24 network addresses. However , when the mount -a command is issued the same exported data does not get made available in the predefined mount point folders associated with nfs-common clients. ufw status shows 2049 is open to all machines members at said network address yet no data is accessible. owners are root:root and chmod is 0777.  

Usually in the past when the fstab specified the exported shares to be mounted the icons showed up on the desktop greyed out until root did the mount -a command then the icons were visible and fully accessible to contained data files.  Now nothing occurs no icons appear and mount -a does not generate any evidence of any error messages.

Thank you for the head's up tip on using the /dev/sd? etc as being a future error source and I will endeavour to correct that once I get the actual mounting and file serving working like I had under previous nfs software versions. For now the use of those accomplishes what is needed for test purposes.

---

### Post by ccor58 on 2022-04-14
Currently following this tutorial guides setup instructions:   [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04)

---

### Post by ccor58 on 2022-04-14
Yes you are correct vers downloaded to install was 21.04 is what shows in lsb version command and in small print on login graphic. start up progress status screen refers to 21.10 either way it is something I will look into correcting for sure thanks.

---

### Post by ccor58 on 2022-05-03
> **ccor58 said:**
> all of the fstab command lines are being properly handled. the original files being specified to share in the exports folders are showing and available using the file manager to view the exports folders directly. The folders data, opt, & misc are being shown correctly with files accessible using the file manager also. exportfs command shows that the exported folder contents are being made correctly available to clients at the correct 192.168.149.0/24 network addresses. However , when the mount -a command is issued the same exported data does not get made available in the predefined mount point folders associated with nfs-common clients. ufw status shows 2049 is open to all machines members at said network address yet no data is accessible. owners are root:root and chmod is 0777.  

Usually in the past when the fstab specified the exported shares to be mounted the icons showed up on the desktop greyed out until root did the mount -a command then the icons were visible and fully accessible to contained data files.  Now nothing occurs no icons appear and mount -a does not generate any evidence of any error messages.

Thank you for the head's up tip on using the /dev/sd? etc as being a future error source and I will endeavour to correct that once I get the actual mounting and file serving working like I had under previous nfs software versions. For now the use of those accomplishes what is needed for test purposes.

complete new clean install of ubuntu server 22.04 LTS OS.  nfs client in server box and all workstations indicate all vers are supported 2, 3, & 4  nfs-client in server box mounts all exports properly; none of the workstations with ubuntustudio OS's get time out messages and do not mount exported shares. all workstations can succeed pinging server and server firewall is set for all NFS ports allowed.   ???????????

---

### Post by ccor58 on 2022-05-20
SOLVED  after much discussion and re installing ubuntu server OS and FINALLY the latest software UPDATE  the Problem solved itself.

---

