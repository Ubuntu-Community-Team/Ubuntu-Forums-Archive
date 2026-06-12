---
title: "CIFS or SMB issues after upgrading 16.04 LTS to 18.04 LTS"
date: 2021-05-10
forum: Server Platforms
---

### Post by metainnova on 2021-05-10
Hi,

Thanks to everybody for your support. We have detected an important issue in different servers after updating Ubuntu Server 16.04 to 18.04 LTS. In two different servers, we have mounted two remote samba resources from a Synology Server. We have mounted through fstab, and we have make different test specifying different versions of the protocol (1.0, 2.0, 2.1 and 3.0). In all cases, the connection is correctly "apparently" stablished, but when we download in the server any package from that smb connection, (for example one ZIP), the file is downloaded but contains errors .

//(IP_of_the_erver)/Software       /media/Software cifs    vers=1.0,uid=www-data,gid=(group_name),iocharset=utf8,credentials=/root/.smbcredentials,dir_mode=0777,file_mode=0777

For example, in one server we have an apache2 that access to /media/Software using SMB in that folder. If we download through apache any Zip folder that is stored in /media/software, the file has CRC errors and is not possible to unzip it correctly.

In kernel and syslog, we have different errors:

```
/var/log/kern.log:May 10 16:01:03 renovatio kernel: [618506.636206] CIFS VFS: Server (IP_of_the_server) has not responded in 180 seconds. Reconnecting...
/var/log/kern.log:May 10 16:01:03 renovatio kernel: [618507.060558] CIFS VFS: Free previous auth_key.response = 898b8664
/var/log/kern.log:May 10 16:01:04 renovatio kernel: [618507.764218] CIFS VFS: No task to wake, unknown frame received! NumMids 10
/var/log/kern.log:May 10 16:01:04 renovatio kernel: [618507.938956] CIFS VFS: No task to wake, unknown frame received! NumMids 9
/var/log/kern.log:May 10 16:27:12 renovatio kernel: [    8.312195] CIFS VFS: Dialect not supported by server. Consider specifying vers=1.0 or vers=2.0 on mount for accessing older servers
/var/log/kern.log:May 10 16:27:12 renovatio kernel: [    8.312229] CIFS VFS: cifs_mount failed w/return code = -95
/var/log/kern.log:May 10 16:27:12 renovatio kernel: [    8.322020] CIFS VFS: Dialect not supported by server. Consider specifying vers=1.0 or vers=2.0 on mount for accessing older servers
/var/log/kern.log:May 10 16:27:12 renovatio kernel: [    8.322054] CIFS VFS: cifs_mount failed w/return code = -95
/var/log/kern.log.1:May  5 23:23:39 renovatio kernel: [213064.923845] CIFS VFS: No task to wake, unknown frame received! NumMids 2
/var/log/syslog:May 10 16:01:03 renovatio kernel: [618506.636206] CIFS VFS: Server 10.135.130.165 has not responded in 180 seconds. Reconnecting...
/var/log/syslog:May 10 16:01:03 renovatio kernel: [618507.060558] CIFS VFS: Free previous auth_key.response = 898b8664
/var/log/syslog:May 10 16:01:04 renovatio kernel: [618507.764218] CIFS VFS: No task to wake, unknown frame received! NumMids 10
/var/log/syslog:May 10 16:01:04 renovatio kernel: [618507.938956] CIFS VFS: No task to wake, unknown frame received! NumMids 9
/var/log/syslog:May 10 16:27:12 renovatio kernel: [    8.312195] CIFS VFS: Dialect not supported by server. Consider specifying vers=1.0 or vers=2.0 on mount for accessing older servers
/var/log/syslog:May 10 16:27:12 renovatio kernel: [    8.312229] CIFS VFS: cifs_mount failed w/return code = -95
/var/log/syslog:May 10 16:27:12 renovatio kernel: [    8.322020] CIFS VFS: Dialect not supported by server. Consider specifying vers=1.0 or vers=2.0 on mount for accessing older servers
/var/log/syslog:May 10 16:27:12 renovatio kernel: [    8.322054] CIFS VFS: cifs_mount failed w/return code = -95

```
After last error, we tried to specify versions 1.0, 2.0, 2.1 and 3.0 in /etc/fstab, and the connection is correctly stablished, but file downloaded through this are corrupted too. We don't know what more to do, instead rolling back to 16.04.

Any suggestion? The Synology SMB server is configured to support from 1.0 SMB to 3.0.

Thanks a lot.

---

### Post by slickymaster on 2021-05-10
*Thread moved to **Server Platforms**.*

---

### Post by LHammonds on 2021-05-10
Did you do an in-place upgrade and trying to use the exact same samba configuration files?  There might be changes in the configuration between samba version on Ubuntu 16 vs 18.

LHammonds

---

### Post by rsteinmetz70112 on 2021-05-10
I have a few Ubuntu Samba servers that have been migrated from earlier versions they are currently 18.04 or 20.04. I've never had a problem with using old smb.conf files. 

What do your fstab entries look like?

Have you loaded the full Samba Suite or just the minimal libraries  or something else?

Here is an fstab that works for me.:

//99.57.10.9/accounting /shylock2/accounting cifs credentials=/root/.cifs.credentials.shylock2.accounting 0 0

---

### Post by volkswagner on 2021-05-10
Since the OP is mounting other shares on Ubuntu, this would be
an smbclient issue no? I don't think smb.conf comes into play does it?

Perhaps it's not related to samba at all. Have you fully tested the network?
Try using iPerf to determine the network is not the issue.

Wireshark/tcpdump can be your friend here as well.

I've had minor issues with the few upgrades I did (16.04>18.04), but
I really haven't been using smbclient.

If the issue is related to cifs, perhaps [moving to NFS]("https://www.mjwebs.io/blog/configure-nfs-mount-with-synology-nas-on-ubuntu-18-04") will offer joy.

---

### Post by rsteinmetz70112 on 2021-05-11
It may not be related to SAMBA, but it could be. That's why I asked what was installed.

---

### Post by Morbius1 on 2021-05-11
> The Synology SMB server is configured to support from 1.0 SMB to 3.0.
> Dialect not supported by server. Consider specifying vers=1.0 or vers=2.0 on mount for accessing older servers

Something you might want to verify:

Install namp on the client to this server and run this command:
```
nmap --script smb-protocols IPofServer
```

Do you get something like this:
> Host script results:
| smb-protocols: 
|   dialects: 
|     NT LM 0.12 (SMBv1) [dangerous, but default]
|     2.02
|     2.10
|     3.00
|     3.02
|_    3.11


CIFS isn't controlled by samba on the client it's controlled by the Linux kernel. The kernel version in Ubuntu 16 defaults to vers=1.0. The version in Ubuntu 18 negotiates with the server to find the best dialect between 2.1 and  3.x.

---

### Post by TheFu on 2021-05-11
I'd push for using NFS from all Unix-like OSes if the Synology supports it. That provides native permissions, native file sharing.  Inside a company, centralized userid/groupid management should make this really easy.  Use CIFS only from Windows.

I vaguely recall there is 1 setting in the smb.conf that is for the client mount, but I don't know which CIFS/SMB clients use it.  Mounts using fstab or autofs probably do not, but mounts through a file manager using gvfs/gio probably do.

Morbius1 thanks for that nmap command!  Crazy useful to KNOW what version is supported on any device.
```
Host script results:
| smb-protocols: 
|   dialects: 
|     NT LM 0.12 (SMBv1) [dangerous, but default]
|     2.02
|_    2.10
```
So I shouldn't waste time trying anything newer than 2.1 to that system.
Attempted to setup an old $80 "NAS" to see which version of CIFS it supports.  I failed in the allotted time (15 min).

---

