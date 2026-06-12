---
title: "NFS server not presenting ACLs"
date: 2007-04-30
forum: Server Platforms
---

### Post by taenus on 2007-04-30
Upgraded a SLES 9 file server do Ubuntu (Dapper) 6.06.1. The server has two partitions (ext3) that contain the /home and /data directories. They are exported via NFS and mounted by various servers on the LAN. After installing Ubuntu, the server still recognizes the ACL permissions used on those directores, but the client machines do not.

Server is mcs02 and has a DNS alias of rafile.

Server /etc/fstab
/dev/sdd6 /home ext3 acl,user_xattr,usrquota 1 2
/dev/sdd5 /data ext3 acl,user_xattr,grpquota 1 2

Server /etc/exports
/data *(rw,acl,no_root_squash,sync)
/home *(rw,acl,no_root_squash,sync)

Server sample output
$ ls /data/agency -l
-rw-rw-r-- 1 root admins 284 2006-11-21 15:33 agency.lst
dr-xrwx--- 2 root BTHHQ 4096 2007-04-28 00:47 BTHHQ
drwxr-x--- 7 root Budgets 4096 2007-04-16 05:12 budget
drwxr-xr-x+ 5 root CRPHQ 4096 2007-04-30 01:00 CRPHQ
drwxr-x---+ 8 root DESIA 4096 2007-04-30 01:00 DESIA
drwxr-x--- 8 root HOLNE 4096 2007-04-28 00:57 HOLNE
drwxrwx---+ 7 root LITN 4096 2007-04-28 00:33 LITN
drwxr-x---+ 8 root LOGIA 4096 2007-04-30 01:00 LOGIA
drwxr-x---+ 8 root MLHIN 4096 2007-04-30 01:00 MLHIN
drwxr-x--- 8 root NORNE 4096 2007-04-28 00:57 NORNE
drwxr-x---+ 8 root OSCIA 4096 2007-04-30 01:00 OSCIA
drwxrwx---+ 8 root PEOIL 4096 2007-04-30 01:00 PEOIL
drwxr-x---+ 8 root PONIL 4096 2007-04-30 01:00 PONIL
drwxr-x---+ 8 root ROCIL 4096 2007-04-30 01:00 ROCIL
drwxr-x---+ 8 root 2013 4096 2007-04-28 00:52 SITEST
drwxr-x---+ 8 root TOAKS 4096 2007-04-30 01:00 TOAKS
drwxr-x---+ 8 root WAUIA 4096 2007-04-30 01:00 WAUIA
drwxr-x---+ 8 root WHOUS 4096 2007-04-28 00:33 WHOUS

$ getfacl /data/agency/ROCIL
# file: data/agency/ROCIL
# owner: root
# group: ROCIL
user::rwx
group::r-x
group:admins:r-x
group:SupportTeam:r-x
mask::r-x
other::---

Client /etc/fstab:
rafile.mosaicinfo.org:/home /home nfs defaults 0 0
rafile.mosaicinfo.org:/data /data nfs defaults 0 0

Client sample output:
$ ls /data/agency -l
-rw-rw-r-- 1 root admins 284 2006-11-21 15:33 agency.lst
dr-xrwx--- 2 root BTHHQ 4096 2007-04-28 00:47 BTHHQ
drwxr-x--- 7 root Budgets 4096 2007-04-16 05:12 budget
drwxr-xr-x 5 root CRPHQ 4096 2007-04-30 01:00 CRPHQ
drwxr-x--- 8 root DESIA 4096 2007-04-30 01:00 DESIA
drwxr-x--- 8 root HOLNE 4096 2007-04-28 00:57 HOLNE
drwxrwx--- 7 root LITN 4096 2007-04-28 00:33 LITN
drwxr-x--- 8 root LOGIA 4096 2007-04-30 01:00 LOGIA
drwxr-x--- 8 root MLHIN 4096 2007-04-30 01:00 MLHIN
drwxr-x--- 8 root NORNE 4096 2007-04-28 00:57 NORNE
drwxr-x--- 8 root OSCIA 4096 2007-04-30 01:00 OSCIA
drwxrwx--- 8 root PEOIL 4096 2007-04-30 01:00 PEOIL
drwxr-x--- 8 root PONIL 4096 2007-04-30 01:00 PONIL
drwxr-x--- 8 root ROCIL 4096 2007-04-30 01:00 ROCIL
drwxr-x--- 8 root 2013 4096 2007-04-28 00:52 SITEST
drwxr-x--- 8 root TOAKS 4096 2007-04-30 01:00 TOAKS
drwxr-x--- 8 root WAUIA 4096 2007-04-30 01:00 WAUIA
drwxr-x--- 8 root WHOUS 4096 2007-04-28 00:33 WHOUS
$ getfacl /data/agency/ROCIL
# file: data/agency/ROCIL
# owner: root
# group: ROCIL
user::rwx
group::r-x
other::---

---

### Post by mkenigson on 2007-05-08
I am having the same issue and would love to hear from anyone that has figured out how to deal with this.  I didn't have this problem when I was using debian -- it only presented itself when I moved to Ubuntu.

---

### Post by taenus on 2007-05-15
FYI - My company has a contract with Canonical on 2007-04-30, so I've generated a trouble ticket with them.  It was reproduced by them, (so it's not my total goof) and I should have an aswer soon.  I'll post the results when I get them, but I would still love it if the Ubuntu community could give me a quicker answer.  At over 1 week for results, I can't say I'm too thrilled.

---

### Post by seaq on 2007-05-23
Hi I'm linking this thread to the bug report bug#67175

---

### Post by taenus on 2007-05-24
Here is the reply that I got to my case with Canonical:

> 
15/05/2007 23:15 | Etienne Goyer
Mr XXX,

After much research, I am sorry to tell you that there is no way we can get you to have ACL support for NFS filesystems mounted from a Ubuntu server in a fashion that we can support. Here are the reasons why.

For NFSv3, the required kernel support is not enabled in Ubuntu. This is controlled by the CONFIG_NFS_V3_ACL and CONFIG_NFSD_V3_ACL directives in the kernel .config file. These .config files are available in Ubuntu as /boot/config-<full kernel version>. The kernel as shipped by Ubuntu has both of these directives undefined. Enabling these options would require to recompile the kernel, and this is something we do not recommend as we do not support machines running custom-compiled kernels.

For NFSv4, ACL support is built in the protocol. However, the userspace utilities required to manipulate NFSv4 ACL are not available in Ubuntu. Manipulating NFSv4 ACL would require either a special set of userland tools (the "nfs4-acl-tools" suite of utilities) that are not available from the Ubuntu software archive, or the getfacl and setfacl commands to be patched for NFSv4 ACL support which they are not in Ubuntu.

It is possible that you will be able to manipulate ACL on a NFSv4 filesystem mounted from a Ubuntu 6.06 server using a client that have proper client-side support for NFSv4 ACL. If you would like to investigate that possibility, I am willing to walk you through the configuration of NFSv4 on your Ubuntu 6.06 server. However, please be aware that I will not be able to help you from the client perspective, as it would be outside the scope of the support contract to configure non-Ubuntu client (or, in fact, any machine not covered by a support contract itself).


So, unlike every other major distro I have tried recently (Fedora, OpenSuSE, SLES), ACL over NFS must not be important.

The good news is my team has found sort of a work around.  Even though the ACLs are not being passed along by the NFS server, it's own system is still respecting them.  You can trick the client into thinking the file is accessable, then fine tune and even block access with ACL on the file server.

Example:  Lets say you have /home shared via NFS on box A and mounted on box B with your users synced between the two (very import that UIDs match).

I'll assume two users exist, Bob and Sue.  Bob is in groups users, while Sue is in users and managers.
On box A as Sue:
echo 'Hello' > ~/test
chmod 660 ~/test
chown sue:users ~/test

This create a file that any user can read.  The permissions from both A and B will be rw-rw---- so both users can access it.  Now for the interesting part.

Still on A:
setfacl -m g:users:--- ~/test
setfacl -m g:managers:rw ~/test

Now, if you look at permisions via ls you'll still get the same.  The ACL striped users, not the POSIX perms.  On A, a getfacl shows permissions you expect, Sue can read/write the file, but Bob can not.  If you look at the file from server B, ls will still report rw-rw---- on the file and pass read request to the server.  The server checks it's ACLs before processing and, as the group was removed, would block read requests from Bob, but allow Sue.

Of course, your milage may very.  This was done on a fully patch Dapper server and destop pair.

---

