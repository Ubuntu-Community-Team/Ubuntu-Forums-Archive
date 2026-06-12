---
title: "Issue mounting a windows share"
date: 2013-10-19
forum: Server Platforms
---

### Post by Cole_M on 2013-10-19
Hi all.

I am trying to allow plex access to my windows shares. As per the instructions found at: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) I have created a [COLOR=#333333].smbcredentials file in root and my [/COLOR][COLOR=#333333][FONT=Ubuntu Beta] /etc/fstab file (lines 13 and 14) now look like 
[/FONT][/COLOR]```
//192.168.2.122/video /home/cole/Videos/Plex  cifs credentials=/home/cole/[COLOR=#333333].smbcredentials[/COLOR],uid=shareuser,gid=sharegroup 0 0
//192.168.2.122/public/Shared Videos /home/cole/Videos/Plex cifs credentials=/home/cole/[COLOR=#333333].smbcredentials[/COLOR],uid=shareuser,gid=sharegroup 0 0


```



Upon issuing a mount command I get: ```
[mntent]: line 13 in /etc/fstab is badmount: wrong fs type, bad option, bad superblock on //192.168.2.122/video,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Running a dmesg | tail gives me:
```
[   27.364720] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready[   27.366869] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.345545] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   30.345581] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1759.979620] FS-Cache: Loaded
[ 1760.035639] FS-Cache: Netfs 'cifs' registered for caching
[ 1760.035749] Key type cifs.spnego registered
[ 1760.035770] Key type cifs.idmap registered
[ 1760.036058] CIFS VFS: cifs_parse_mount_options: Invalid uid value
[ 1964.717624] CIFS VFS: cifs_parse_mount_options: Invalid uid value

```

I am unsure how to proceed and any help would be awesome!

---

