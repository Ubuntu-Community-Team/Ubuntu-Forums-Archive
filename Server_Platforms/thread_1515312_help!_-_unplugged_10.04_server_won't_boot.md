---
title: "help! - unplugged 10.04 server won't boot"
date: 2010-06-22
forum: Server Platforms
---

### Post by aidanewen on 2010-06-22
Someone unplugged our 10.04 server last night and now it won't boot. It was running a samba fileserver and a zimbra mailserver on a virtual machine. I'd only just set it up and don't have a backup yet. Linux is pretty new to me so I'm in a bit of a panic. 

So far I've tried booting from the CD and seem to be able to mount my md0 drive whilst running in rescue mode. I've tried "apt-get update" and "apt-get -f install" (I figure I should be naming package for "apt-get install" to do anything). I've also tried running "apt-get check" but that doesn't list any broken dependancies. 

I think I'm about to try using the re-install grub loader but I'm worried it will overwrite data on my md0 drive (that's a software raid drive that the system normally boots from). I'm not even sure I had grub running the first place.

Any pointers, suggestions or words of encouragement would be greatly appreciated.

Thanks in advance,

Aidan

---

### Post by Leppie on 2010-06-22
you most probably want to check the filesystem integrity of your raid unit.

---

### Post by aidanewen on 2010-06-22
Thanks, I'll have a look.

---

### Post by aidanewen on 2010-06-22
OK, I've tried checking /proc/mdstat and everything looks OK there:

md0 : active raid1 sda1[0] sdb1[1]
234259392 blocks [2/2]   [UU]

"mdadm --detail" seems to indicate everything is OK (active devices 2, working devices 2 - both devices state is listed as 'active sync'). There are numbers under 'major' in the table at the bottom, I'm not sure what this means.

fsck /dev/md0 gives me
/dev/md0: clean, 90671/14647296 files 26716582/58564848 blocks

So I can't seem to find any problems with either the raid setup or the filesystem of the boot drive.

Any other ideas?

---

### Post by aidanewen on 2010-06-22
I'm looking at the ROM-Based setup utility (hardware is HP Proliant), and there doesn't seem to be an appropriate boot device listed under the "Boot Device Priority" menu. The first boot device is listed as being the CD / DVD drive. The second is listed as "Not Installed", the third is usb and the 4th is network.

I'm not really sure where the ROM should be booting from (given that I've got software raid).

---

### Post by Leppie on 2010-06-22
have you checked the syslog of your install?
if you're using software raid, then don't mess around with the rom based fake raid...

---

### Post by aidanewen on 2010-06-22
I haven't had a look at syslog yet but have attached the output from my attempts to boot

```
    fsck from util-linux-ng 2.17.2
  /dev/md0: Superblock last mount time (Tue Jun 22  13:50:36 2010,
                  Now = Mon Jul 6 03:46:05 2009) is in the future.
   
  /dev/md0: UNEXPECTED INCONSISTENCY; RUN fsck  MANUALLY.
  mountall: fsck / [466] terminated with status 4
  mountall: Filesystem has errors: /
  
```

When I boot from a CD into rescue mode and run fsck I get the following

```

   #fsck
fsck from util-linux-ng 2.17.2
  e2fsck 1.41.11 (14-Mar-2010)
  /dev/md0 contains a file system with errors, check forced.
  Pass 1: Checking inodes, blocks, and sizes
  Pass 2: Checking directory structure
  Pass 3: Checking directory connectivity
  Pass 4: Checking reference counts
  Pass 5: Checking group summary information
  /dev/md0: 90707/14647296 files (0.1% non-contiguous), 2671662/58564848 blocks
   
  # fsck  fsck from util-linux-ng 2.17.2 
  e2fsck 1.41.11 (14-Mar-2010)
  /dev/md0: clean, 90707/14647296 files, 2671662/58564848 blocks
  
```

However I still can't boot from my hard disks (I get the same output as above)

---

### Post by aidanewen on 2010-06-22
To be honest I've no idea what I'm looking for in the syslog but I've attached it for info:

```

Jun 21 16:44:54 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 16:47:42 Gandalf winbindd[1427]: [2010/06/21 16:47:42,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 16:47:42 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 16:47:42 Gandalf winbindd[1427]: [2010/06/21 16:47:42,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 16:47:42 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 16:47:42 Gandalf winbindd[1427]: [2010/06/21 16:47:42,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 16:47:42 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 16:47:42 Gandalf winbindd[1427]: [2010/06/21 16:47:42,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 16:47:42 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 16:59:59 Gandalf nmbd[1363]: [2010/06/21 16:59:59,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 16:59:59 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 16:59:59 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 16:59:59 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 16:59:59 Gandalf nmbd[1363]: [2010/06/21 16:59:59,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 16:59:59 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 16:59:59 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 16:59:59 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 17:15:12 Gandalf nmbd[1363]: [2010/06/21 17:15:12,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 17:15:12 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 17:15:12 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 17:15:12 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 17:15:12 Gandalf nmbd[1363]: [2010/06/21 17:15:12,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 17:15:12 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 17:15:12 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 17:15:12 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 17:17:01 Gandalf CRON[18967]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 21 17:22:24 Gandalf smbd[18227]: [2010/06/21 17:22:24,  0] lib/util_sock.c:539(read_fd_with_timeout)
Jun 21 17:22:24 Gandalf smbd[18227]: [2010/06/21 17:22:24,  0] lib/util_sock.c:1491(get_peer_addr_internal)
Jun 21 17:22:24 Gandalf smbd[18227]:   getpeername failed. Error was Transport endpoint is not connected
Jun 21 17:22:24 Gandalf smbd[18227]:   read_fd_with_timeout: client 0.0.0.0 read error = No route to host.
Jun 21 17:30:12 Gandalf nmbd[1363]: [2010/06/21 17:30:12,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 17:30:12 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 17:30:12 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 17:30:12 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 17:30:12 Gandalf nmbd[1363]: [2010/06/21 17:30:12,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 17:30:12 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 17:30:12 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 17:30:12 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 17:45:27 Gandalf nmbd[1363]: [2010/06/21 17:45:27,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 17:45:27 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 17:45:27 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 17:45:27 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 17:45:27 Gandalf nmbd[1363]: [2010/06/21 17:45:27,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 17:45:27 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 17:45:27 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 17:45:27 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 18:00:30 Gandalf nmbd[1363]: [2010/06/21 18:00:30,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 18:00:30 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 18:00:30 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 18:00:30 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 18:00:30 Gandalf nmbd[1363]: [2010/06/21 18:00:30,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 18:00:30 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 18:00:30 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 18:00:30 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 18:15:34 Gandalf nmbd[1363]: [2010/06/21 18:15:34,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 18:15:34 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 18:15:34 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 18:15:34 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 18:15:34 Gandalf nmbd[1363]: [2010/06/21 18:15:34,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 18:15:34 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 18:15:34 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 18:15:34 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 18:17:01 Gandalf CRON[19161]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 21 18:30:29 Gandalf nmbd[1363]: [2010/06/21 18:30:29,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 18:30:29 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 18:30:29 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 18:30:29 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 18:30:29 Gandalf nmbd[1363]: [2010/06/21 18:30:29,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 18:30:29 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 18:30:29 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 18:30:29 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 18:45:39 Gandalf nmbd[1363]: [2010/06/21 18:45:39,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 18:45:39 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 18:45:39 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 18:45:39 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 18:45:39 Gandalf nmbd[1363]: [2010/06/21 18:45:39,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 18:45:39 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 18:45:39 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 18:45:39 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 18:58:31 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 18:58:31 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 18:58:31 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 18:58:31 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 18:58:31 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 18:58:31 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 18:58:31 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 18:58:31 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 18:58:31 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 18:58:31 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 18:58:31 Gandalf winbindd[1427]: [2010/06/21 18:58:31,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 18:58:31 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:00:32 Gandalf nmbd[1363]: [2010/06/21 19:00:32,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 19:00:32 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 19:00:32 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 19:00:32 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 19:00:32 Gandalf nmbd[1363]: [2010/06/21 19:00:32,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 19:00:32 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 19:00:32 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 19:00:32 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:00:40 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:00:40 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:00:40 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:00:40 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:00:40 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:00:40 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:00:40 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:00:40 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:00:40 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:00:40 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:00:40 Gandalf winbindd[1427]: [2010/06/21 19:00:40,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:00:40 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:03:27 Gandalf kernel: [1747815.651974] ata2: EH in SWNCQ mode,QC:qc_active 0x7FC sactive 0x7FC
Jun 21 19:03:27 Gandalf kernel: [1747815.668449] ata2: SWNCQ:qc_active 0x4 defer_bits 0x7F8 last_issue_tag 0x2
Jun 21 19:03:27 Gandalf kernel: [1747815.668454]   dhfis 0x4 dmafis 0x0 sdbfis 0x0
Jun 21 19:03:27 Gandalf kernel: [1747815.701136] ata2: ATA_REG 0x41 ERR_REG 0x4
Jun 21 19:03:27 Gandalf kernel: [1747815.717001] ata2: tag : dhfis dmafis sdbfis sacitve
Jun 21 19:03:27 Gandalf kernel: [1747815.732620] ata2: tag 0x2: 1 0 0 1  
Jun 21 19:03:27 Gandalf kernel: [1747815.747910] ata2.00: exception Emask 0x1 SAct 0x7fc SErr 0x0 action 0x6 frozen
Jun 21 19:03:27 Gandalf kernel: [1747815.779562] ata2.00: Ata error. fis:0x41
Jun 21 19:03:28 Gandalf kernel: [1747815.795741] ata2.00: failed command: WRITE FPDMA QUEUED
Jun 21 19:03:28 Gandalf kernel: [1747815.795753] ata2.00: cmd 61/00:10:d0:8e:64/04:00:02:00:00/40 tag 2 ncq 524288 out
Jun 21 19:03:28 Gandalf kernel: [1747815.795755]          res 41/04:00:cf:8e:64/04:00:02:00:00/40 Emask 0x1 (device error)
Jun 21 19:03:28 Gandalf kernel: [1747815.795760] ata2.00: status: { DRDY ERR }
Jun 21 19:03:28 Gandalf kernel: [1747815.795763] ata2.00: error: { ABRT }
Jun 21 19:03:28 Gandalf kernel: [1747815.795766] ata2.00: failed command: WRITE FPDMA QUEUED
Jun 21 19:03:28 Gandalf kernel: [1747815.795775] ata2.00: cmd 61/c8:18:d0:92:64/03:00:02:00:00/40 tag 3 ncq 495616 out
Jun 21 19:03:28 Gandalf kernel: [1747815.795777]          res 41/04:00:cf:8e:64/04:00:02:00:00/40 Emask 0x1 (device error)
Jun 21 19:03:28 Gandalf kernel: [1747815.795781] ata2.00: status: { DRDY ERR }
Jun 21 19:03:28 Gandalf kernel: [1747815.795784] ata2.00: error: { ABRT }
Jun 21 19:03:28 Gandalf kernel: [1747815.795787] ata2.00: failed command: WRITE FPDMA QUEUED
Jun 21 19:03:28 Gandalf kernel: [1747815.795797] ata2.00: cmd 61/00:20:98:96:64/04:00:02:00:00/40 tag 4 ncq 524288 out
Jun 21 19:03:28 Gandalf kernel: [1747815.795799]          res 41/04:00:cf:8e:64/04:00:02:00:00/40 Emask 0x1 (device error)
Jun 21 19:03:28 Gandalf kernel: [1747815.795803] ata2.00: status: { DRDY ERR }
Jun 21 19:03:28 Gandalf kernel: [1747815.795805] ata2.00: error: { ABRT }
Jun 21 19:03:28 Gandalf kernel: [1747815.795809] ata2.00: failed command: WRITE FPDMA QUEUED
Jun 21 19:03:28 Gandalf kernel: [1747815.795817] ata2.00: cmd 61/00:28:98:9a:64/04:00:02:00:00/40 tag 5 ncq 524288 out
Jun 21 19:03:28 Gandalf kernel: [1747815.795819]          res 41/04:00:cf:8e:64/04:00:02:00:00/40 Emask 0x1 (device error)
Jun 21 19:03:28 Gandalf kernel: [1747815.795822] ata2.00: status: { DRDY ERR }
Jun 21 19:03:28 Gandalf kernel: [1747815.795825] ata2.00: error: { ABRT }
Jun 21 19:03:28 Gandalf kernel: [1747815.795828] ata2.00: failed command: WRITE FPDMA QUEUED
Jun 21 19:03:28 Gandalf kernel: [1747815.795837] ata2.00: cmd 61/00:30:98:9e:64/04:00:02:00:00/40 tag 6 ncq 524288 out
Jun 21 19:03:28 Gandalf kernel: [1747815.795839]          res 41/04:00:cf:8e:64/04:00:02:00:00/40 Emask 0x1 (device error)
Jun 21 19:03:28 Gandalf kernel: [1747815.795842] ata2.00: status: { DRDY ERR }
Jun 21 19:03:28 Gandalf kernel: [1747815.795845] ata2.00: error: { ABRT }
Jun 21 19:03:28 Gandalf kernel: [1747815.795848] ata2.00: failed command: WRITE FPDMA QUEUED
Jun 21 19:03:28 Gandalf kernel: [1747815.795857] ata2.00: cmd 61/08:38:98:a2:64/00:00:02:00:00/40 tag 7 ncq 4096 out
Jun 21 19:03:28 Gandalf kernel: [1747815.795859]          res 41/04:00:cf:8e:64/04:00:02:00:00/40 Emask 0x1 (device error)
Jun 21 19:03:28 Gandalf kernel: [1747815.795862] ata2.00: status: { DRDY ERR }
Jun 21 19:03:28 Gandalf kernel: [1747815.795865] ata2.00: error: { ABRT }
Jun 21 19:03:28 Gandalf kernel: [1747815.795868] ata2.00: failed command: WRITE FPDMA QUEUED
Jun 21 19:03:28 Gandalf kernel: [1747815.795876] ata2.00: cmd 61/00:40:a0:a2:64/04:00:02:00:00/40 tag 8 ncq 524288 out
Jun 21 19:03:28 Gandalf kernel: [1747815.795878]          res 41/04:00:cf:8e:64/04:00:02:00:00/40 Emask 0x1 (device error)
Jun 21 19:03:28 Gandalf kernel: [1747815.795882] ata2.00: status: { DRDY ERR }
Jun 21 19:03:28 Gandalf kernel: [1747815.795884] ata2.00: error: { ABRT }
Jun 21 19:03:28 Gandalf kernel: [1747815.795887] ata2.00: failed command: WRITE FPDMA QUEUED
Jun 21 19:03:28 Gandalf kernel: [1747815.795896] ata2.00: cmd 61/00:48:a0:a6:64/04:00:02:00:00/40 tag 9 ncq 524288 out
Jun 21 19:03:28 Gandalf kernel: [1747815.795898]          res 41/04:00:cf:8e:64/04:00:02:00:00/40 Emask 0x1 (device error)
Jun 21 19:03:28 Gandalf kernel: [1747815.795901] ata2.00: status: { DRDY ERR }
Jun 21 19:03:28 Gandalf kernel: [1747815.795904] ata2.00: error: { ABRT }
Jun 21 19:03:28 Gandalf kernel: [1747815.795907] ata2.00: failed command: WRITE FPDMA QUEUED
Jun 21 19:03:28 Gandalf kernel: [1747815.795916] ata2.00: cmd 61/28:50:a0:aa:64/00:00:02:00:00/40 tag 10 ncq 20480 out
Jun 21 19:03:28 Gandalf kernel: [1747815.795918]          res 41/04:00:cf:8e:64/04:00:02:00:00/40 Emask 0x1 (device error)
Jun 21 19:03:28 Gandalf kernel: [1747815.795921] ata2.00: status: { DRDY ERR }
Jun 21 19:03:28 Gandalf kernel: [1747815.795924] ata2.00: error: { ABRT }
Jun 21 19:03:28 Gandalf kernel: [1747815.795962] ata2: hard resetting link
Jun 21 19:03:28 Gandalf kernel: [1747815.795965] ata2: nv: skipping hardreset on occupied port
Jun 21 19:03:28 Gandalf kernel: [1747816.280098] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 21 19:03:28 Gandalf kernel: [1747816.340287] ata2.00: configured for UDMA/133
Jun 21 19:03:28 Gandalf kernel: [1747816.340448] ata2: EH complete
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:08:47 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:08:47 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:08:47 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:08:47 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:08:47 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:08:47 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:08:47 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Jun 21 19:08:47 Gandalf winbindd[1427]:   idmap_alloc module tdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module passdb already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap.c:149(smb_register_idmap)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Idmap module nss already registered!
Jun 21 19:08:47 Gandalf winbindd[1427]: [2010/06/21 19:08:47,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Jun 21 19:08:47 Gandalf winbindd[1427]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
Jun 21 19:15:46 Gandalf nmbd[1363]: [2010/06/21 19:15:46,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 19:15:46 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 19:15:46 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 19:15:46 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 19:15:46 Gandalf nmbd[1363]: [2010/06/21 19:15:46,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 19:15:46 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 19:15:46 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 19:15:46 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 19:17:01 Gandalf CRON[19358]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 21 19:30:42 Gandalf nmbd[1363]: [2010/06/21 19:30:42,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 19:30:42 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 19:30:42 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 19:30:42 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 19:30:42 Gandalf nmbd[1363]: [2010/06/21 19:30:42,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 19:30:42 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 19:30:42 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 19:30:42 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 19:45:52 Gandalf nmbd[1363]: [2010/06/21 19:45:52,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 19:45:52 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 19:45:52 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 19:45:52 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 19:45:52 Gandalf nmbd[1363]: [2010/06/21 19:45:52,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 19:45:52 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 19:45:52 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 19:45:52 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 20:00:57 Gandalf nmbd[1363]: [2010/06/21 20:00:57,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 20:00:57 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 20:00:57 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 20:00:57 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 20:00:57 Gandalf nmbd[1363]: [2010/06/21 20:00:57,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 20:00:57 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 20:00:57 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 20:00:57 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 20:15:50 Gandalf nmbd[1363]: [2010/06/21 20:15:50,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 20:15:50 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 20:15:50 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 20:15:50 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 20:15:50 Gandalf nmbd[1363]: [2010/06/21 20:15:50,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 20:15:50 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 20:15:50 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 20:15:50 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 20:17:01 Gandalf CRON[19546]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 21 20:31:03 Gandalf nmbd[1363]: [2010/06/21 20:31:03,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 20:31:03 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 20:31:03 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 20:31:03 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 20:31:03 Gandalf nmbd[1363]: [2010/06/21 20:31:03,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 20:31:03 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 20:31:03 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 20:31:03 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 20:46:04 Gandalf nmbd[1363]: [2010/06/21 20:46:04,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 20:46:04 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 20:46:04 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 20:46:04 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 20:46:04 Gandalf nmbd[1363]: [2010/06/21 20:46:04,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 20:46:04 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 20:46:04 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 20:46:04 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 21:01:02 Gandalf nmbd[1363]: [2010/06/21 21:01:02,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 21:01:02 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 21:01:02 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 21:01:02 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 21:01:02 Gandalf nmbd[1363]: [2010/06/21 21:01:02,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 21:01:02 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 21:01:02 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 21:01:02 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 21:16:12 Gandalf nmbd[1363]: [2010/06/21 21:16:12,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 21:16:12 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 21:16:12 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 21:16:12 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 21:16:12 Gandalf nmbd[1363]: [2010/06/21 21:16:12,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 21:16:12 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 21:16:12 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 21:16:12 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 21:17:01 Gandalf CRON[19734]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 21 21:31:15 Gandalf nmbd[1363]: [2010/06/21 21:31:15,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 21:31:15 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 21:31:15 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 21:31:15 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 21:31:15 Gandalf nmbd[1363]: [2010/06/21 21:31:15,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 21:31:15 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 21:31:15 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 21:31:15 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 21:46:07 Gandalf nmbd[1363]: [2010/06/21 21:46:07,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 21:46:07 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 21:46:07 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 21:46:07 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 21:46:07 Gandalf nmbd[1363]: [2010/06/21 21:46:07,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 21:46:07 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 21:46:07 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 21:46:07 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 22:01:08 Gandalf nmbd[1363]: [2010/06/21 22:01:08,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 22:01:08 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 22:01:08 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 22:01:08 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 22:01:08 Gandalf nmbd[1363]: [2010/06/21 22:01:08,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 22:01:08 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 22:01:08 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 22:01:08 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 22:16:24 Gandalf nmbd[1363]: [2010/06/21 22:16:24,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 22:16:24 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 22:16:24 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 22:16:24 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 22:16:24 Gandalf nmbd[1363]: [2010/06/21 22:16:24,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 22:16:24 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 22:16:24 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 22:16:24 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 22:17:01 Gandalf CRON[19924]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 21 22:31:26 Gandalf nmbd[1363]: [2010/06/21 22:31:26,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 22:31:26 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 22:31:26 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 22:31:26 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 22:31:26 Gandalf nmbd[1363]: [2010/06/21 22:31:26,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 22:31:26 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 22:31:26 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 22:31:26 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 22:46:29 Gandalf nmbd[1363]: [2010/06/21 22:46:29,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 22:46:29 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 22:46:29 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 22:46:29 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 22:46:29 Gandalf nmbd[1363]: [2010/06/21 22:46:29,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 22:46:29 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 22:46:29 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 22:46:29 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 23:01:37 Gandalf nmbd[1363]: [2010/06/21 23:01:37,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 23:01:37 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 23:01:37 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 23:01:37 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 23:01:37 Gandalf nmbd[1363]: [2010/06/21 23:01:37,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 23:01:37 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 23:01:37 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 23:01:37 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 23:16:46 Gandalf nmbd[1363]: [2010/06/21 23:16:46,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 23:16:46 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 23:16:46 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 23:16:46 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 23:16:46 Gandalf nmbd[1363]: [2010/06/21 23:16:46,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 23:16:46 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 23:16:46 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 23:16:46 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 23:17:01 Gandalf CRON[20135]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 21 23:31:39 Gandalf nmbd[1363]: [2010/06/21 23:31:39,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 23:31:39 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 23:31:39 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 23:31:39 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 23:31:39 Gandalf nmbd[1363]: [2010/06/21 23:31:39,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 23:31:39 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 23:31:39 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 23:31:39 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 23:46:51 Gandalf nmbd[1363]: [2010/06/21 23:46:51,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 23:46:51 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 23:46:51 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 23:46:51 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 21 23:46:51 Gandalf nmbd[1363]: [2010/06/21 23:46:51,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 21 23:46:51 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 21 23:46:51 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 21 23:46:51 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 00:01:47 Gandalf nmbd[1363]: [2010/06/22 00:01:47,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 00:01:47 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 00:01:47 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 00:01:47 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 00:01:47 Gandalf nmbd[1363]: [2010/06/22 00:01:47,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 00:01:47 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 00:01:47 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 00:01:47 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 00:16:58 Gandalf nmbd[1363]: [2010/06/22 00:16:58,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 00:16:58 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 00:16:58 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 00:16:58 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 00:16:58 Gandalf nmbd[1363]: [2010/06/22 00:16:58,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 00:16:58 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 00:16:58 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 00:16:58 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 00:17:01 Gandalf CRON[20325]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 22 00:31:52 Gandalf nmbd[1363]: [2010/06/22 00:31:52,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 00:31:52 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 00:31:52 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 00:31:52 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 00:31:52 Gandalf nmbd[1363]: [2010/06/22 00:31:52,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 00:31:52 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 00:31:52 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 00:31:52 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 00:47:03 Gandalf nmbd[1363]: [2010/06/22 00:47:03,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 00:47:03 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 00:47:03 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 00:47:03 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 00:47:03 Gandalf nmbd[1363]: [2010/06/22 00:47:03,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 00:47:03 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 00:47:03 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 00:47:03 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 01:01:58 Gandalf nmbd[1363]: [2010/06/22 01:01:58,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 01:01:58 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 01:01:58 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 01:01:58 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 01:01:58 Gandalf nmbd[1363]: [2010/06/22 01:01:58,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 01:01:58 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 01:01:58 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 01:01:58 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 01:17:01 Gandalf CRON[20522]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 22 01:17:10 Gandalf nmbd[1363]: [2010/06/22 01:17:10,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 01:17:10 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 01:17:10 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 01:17:10 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 01:17:10 Gandalf nmbd[1363]: [2010/06/22 01:17:10,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 01:17:10 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 01:17:10 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 01:17:10 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 01:32:04 Gandalf nmbd[1363]: [2010/06/22 01:32:04,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 01:32:04 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 01:32:04 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 01:32:04 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 01:32:04 Gandalf nmbd[1363]: [2010/06/22 01:32:04,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 01:32:04 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 01:32:04 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 01:32:04 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 01:47:16 Gandalf nmbd[1363]: [2010/06/22 01:47:16,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 01:47:16 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 01:47:16 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 01:47:16 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 01:47:16 Gandalf nmbd[1363]: [2010/06/22 01:47:16,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 01:47:16 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 01:47:16 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 01:47:16 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 02:02:11 Gandalf nmbd[1363]: [2010/06/22 02:02:11,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 02:02:11 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 02:02:11 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 02:02:11 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 02:02:11 Gandalf nmbd[1363]: [2010/06/22 02:02:11,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 02:02:11 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 02:02:11 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 02:02:11 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 02:17:01 Gandalf CRON[20718]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 22 02:17:23 Gandalf nmbd[1363]: [2010/06/22 02:17:23,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 02:17:23 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 02:17:23 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 02:17:23 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 02:17:23 Gandalf nmbd[1363]: [2010/06/22 02:17:23,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 02:17:23 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 02:17:23 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 02:17:23 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 02:32:16 Gandalf nmbd[1363]: [2010/06/22 02:32:16,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 02:32:16 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 02:32:16 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 02:32:16 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 02:32:16 Gandalf nmbd[1363]: [2010/06/22 02:32:16,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 02:32:16 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 02:32:16 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 02:32:16 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 02:47:28 Gandalf nmbd[1363]: [2010/06/22 02:47:28,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 02:47:28 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 02:47:28 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 02:47:28 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 02:47:28 Gandalf nmbd[1363]: [2010/06/22 02:47:28,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 02:47:28 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 02:47:28 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 02:47:28 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 03:02:24 Gandalf nmbd[1363]: [2010/06/22 03:02:24,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 03:02:24 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 03:02:24 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 03:02:24 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 03:02:24 Gandalf nmbd[1363]: [2010/06/22 03:02:24,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 03:02:24 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 03:02:24 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 03:02:24 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 03:17:01 Gandalf CRON[20920]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 22 03:17:35 Gandalf nmbd[1363]: [2010/06/22 03:17:35,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 03:17:35 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 03:17:35 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 03:17:35 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 03:17:35 Gandalf nmbd[1363]: [2010/06/22 03:17:35,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 03:17:35 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 03:17:35 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 03:17:35 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 03:32:29 Gandalf nmbd[1363]: [2010/06/22 03:32:29,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 03:32:29 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 03:32:29 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 03:32:29 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 03:32:29 Gandalf nmbd[1363]: [2010/06/22 03:32:29,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 03:32:29 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 03:32:29 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 03:32:29 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 03:47:40 Gandalf nmbd[1363]: [2010/06/22 03:47:40,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 03:47:40 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 03:47:40 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 03:47:40 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 03:47:40 Gandalf nmbd[1363]: [2010/06/22 03:47:40,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 03:47:40 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 03:47:40 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 03:47:40 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 04:02:35 Gandalf nmbd[1363]: [2010/06/22 04:02:35,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 04:02:35 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 04:02:35 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 04:02:35 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 04:02:35 Gandalf nmbd[1363]: [2010/06/22 04:02:35,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 04:02:35 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 04:02:35 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 04:02:35 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 04:17:01 Gandalf CRON[21121]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 22 04:17:47 Gandalf nmbd[1363]: [2010/06/22 04:17:47,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 04:17:47 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 04:17:47 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 04:17:47 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 04:17:47 Gandalf nmbd[1363]: [2010/06/22 04:17:47,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 04:17:47 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 04:17:47 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 04:17:47 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 04:32:50 Gandalf nmbd[1363]: [2010/06/22 04:32:50,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 04:32:50 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 04:32:50 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 04:32:50 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 04:32:50 Gandalf nmbd[1363]: [2010/06/22 04:32:50,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 04:32:50 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 04:32:50 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 04:32:50 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 04:47:43 Gandalf nmbd[1363]: [2010/06/22 04:47:43,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 04:47:43 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 04:47:43 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 04:47:43 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 04:47:43 Gandalf nmbd[1363]: [2010/06/22 04:47:43,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 04:47:43 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 04:47:43 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 04:47:43 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 05:02:57 Gandalf nmbd[1363]: [2010/06/22 05:02:57,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 05:02:57 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 05:02:57 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 05:02:57 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 05:02:57 Gandalf nmbd[1363]: [2010/06/22 05:02:57,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 05:02:57 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 05:02:57 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 05:02:57 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 05:17:01 Gandalf CRON[21309]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 22 05:17:50 Gandalf nmbd[1363]: [2010/06/22 05:17:50,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 05:17:50 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 05:17:50 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 05:17:50 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 05:17:50 Gandalf nmbd[1363]: [2010/06/22 05:17:50,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 05:17:50 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 05:17:50 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 05:17:50 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 05:32:53 Gandalf nmbd[1363]: [2010/06/22 05:32:53,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 05:32:53 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 05:32:53 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 05:32:53 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 05:32:53 Gandalf nmbd[1363]: [2010/06/22 05:32:53,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 05:32:53 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 05:32:53 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 05:32:53 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 05:48:05 Gandalf nmbd[1363]: [2010/06/22 05:48:05,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 05:48:05 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 05:48:05 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 05:48:05 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 05:48:05 Gandalf nmbd[1363]: [2010/06/22 05:48:05,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 05:48:05 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 05:48:05 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 05:48:05 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 06:03:00 Gandalf nmbd[1363]: [2010/06/22 06:03:00,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 06:03:00 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 06:03:00 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 06:03:00 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.
Jun 22 06:03:00 Gandalf nmbd[1363]: [2010/06/22 06:03:00,  0] nmbd/nmbd_browsesync.c:350(find_domain_master_name_query_fail)
Jun 22 06:03:00 Gandalf nmbd[1363]:   find_domain_master_name_query_fail:
Jun 22 06:03:00 Gandalf nmbd[1363]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Jun 22 06:03:00 Gandalf nmbd[1363]:   Unable to sync browse lists in this workgroup.

```

---

### Post by v1ad on 2010-06-22
try reconfiguring your bios for raid again. at times when it gets unplugged it resets the bios. and then on boot it tries to read it as ide instead of raid, and then the raid utility does not go up.

---

### Post by aidanewen on 2010-06-22
I'm running software raid, and I'm not sure how to point the bios at it. I'm using an HP Proliant server with 4 drives 2 x 250GB configured with RAID 1 (md0 for boot drive and md1 for swap) and 2 x 750GB with RAID1 (md2).

It looks like the BIOS is going to the CD/ DVD drive as it's primary boot device, followed by the first physical hard drive. The bios was certainly reset - I did it manually (as advised by HP Support).

I can't really see how the bios could be the problem given that I'm getting the following output when I try to boot:

```

   fsck from util-linux-ng 2.17.2
  /dev/md0: Superblock last mount time (Tue Jun 22 13:50:36 2010,
                  Now = Mon Jul 6 03:46:05 2009) is in the future.
   
  /dev/md0: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
  mountall: fsck / [466] terminated with status 4
  mountall: Filesystem has errors: /
  

```

Surely this output shows that it's trying to boot from my raid drive (md0)?

---

### Post by aidanewen on 2010-06-22
I've checked in the bios again and it's definitely listing the first SATA drive as the boot device. Is this this issue? - somehow it needs to boot from software raid (ie the combination of the 1st and 2nd SATA drives), rather than the first drive.

---

### Post by BobVila on 2010-06-22
From the output in your last post, your system clock is WAY off. Dunno if that's enough to make fsck freak out to the point that it is, but you should edit that anyway.

Have you followed its advice, booted a livecd and run fsck against the md?

---

### Post by v1ad on 2010-06-22
my bad, i should read better. if its a software raid, then just make sure it is booting to the right drive. set the first to the first and second to second boot device see what that does. it might be trying to boot of the wrong drive. 

on software raid the bios should be detecting both hard drives, but i could be wrong.

---

### Post by aidanewen on 2010-06-23
I have booted from a live CD and run fsck against the raid drive md0.

When I run fsck the first time after boot I get
```

     fsck from util-linux-ng 2.17.2 
  e2fsck 1.41.11 (14-Mar-2010)
  /dev/md0: clean, 90707/14647296 files, 2671662/58564848 blocks
    
```
Then the second (and subsequent) time I run it I get 
```

   fsck from util-linux-ng 2.17.2 
  e2fsck 1.41.11 (14-Mar-2010)
  /dev/md0: clean, 90707/14647296 files, 2671662/58564848 blocks
  
```
This seems to be repeated each time a boot up from the CD.

---

### Post by aidanewen on 2010-06-23
The bios doesn't show any signs that it's recognising the raid drive - it lists only the sata drive.

fsck seems to correct errors after every boot. Is it possible that the bios is trying to boot from one of the drives in the raid array, making a mess of that drive, and then fsck is fixing the mess when I run it on the raid drive? That could explain why the process I described in my last post is repeated.

---

### Post by aidanewen on 2010-06-23
OK, think it's time to call it a day and rebuild the server. Thanks everyone for your help.

---

### Post by Leppie on 2010-06-23
the log you posted only has entries about not being able to join some domain, and there's no sign of why the system is not booting properly.
check the other logs as well (like dmesg.*.*, syslog.*.*)

---

