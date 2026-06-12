---
title: "libdvd-pkg"
date: 2017-05-31
forum: Ubuntu Development Version
---

### Post by #&amp;thj^% on 2017-05-31
More nice suprises: :)
```
sudo apt install libdvdcss2
```
You now should see a dialog box shown as follows
```

This package automates the process of launching downloads of the source   &#9474; 
 &#9474; files for libdvdcss2 from videolan.org, compiling them, and installing    &#9474; 
 &#9474; the binary packages (libdvdcss2 libdvdcss-dev).                           &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Please run "sudo dpkg-reconfigure libdvd-pkg" to launch this process for  &#9474; 
 &#9474; the first time.                           

Configuring libdvd-pkg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
  &#9474;                                                                         &#9474; 
  &#9474; If activated, the APT post-invoke hook takes care of future automatic   &#9474; 
  &#9474; upgrades of libdvdcss2 (which may be triggered by new versions of       &#9474; 
  &#9474; libdvd-pkg). When updates are available, the hook will launch the       &#9474; 
  &#9474; process of downloading the source, recompiling it, and (if "apt-get     &#9474; 
  &#9474; check" reports no errors) using "dpkg -i" to install the new versions.  &#9474; 
  &#9474;                                                                         &#9474; 
  &#9474; Alternatively, the process can be launched manually by running "sudo    &#9474; 
  &#9474; dpkg-reconfigure libdvd-pkg".                                           &#9474; 
  &#9474;                                                                         &#9474; 
  &#9474; Enable automatic upgrades for libdvdcss2?                               &#9474; 
  &#9474;                                                                         &#9474; 
  &#9474;                    <Yes>                       <No>   

```
Followed with:
```

sudo dpkg-reconfigure libdvd-pkg
libdvd-pkg: Downloading orig source...
I: libdvdcss_1.4.0
/usr/bin/wget --tries=3 --timeout=40 --read-timeout=40 --continue -O libdvdcss_1.4.0.orig.tar.bz2 \
          http://download.videolan.org/pub/libdvdcss/1.4.0/libdvdcss-1.4.0.tar.bz2 \
        || /usr/bin/uscan --noconf --verbose --rename --destdir=/usr/src/libdvd-pkg --check-dirname-level=0 --force-download --download-current-version /usr/share/libdvd-pkg/debian
--2017-05-31 17:44:27--  http://download.videolan.org/pub/libdvdcss/1.4.0/libdvdcss-1.4.0.tar.bz2
Resolving download.videolan.org (download.videolan.org)... 2a01:e0d:1:3:58bf:fa02:c0de:5, 88.191.250.2
Connecting to download.videolan.org (download.videolan.org)|2a01:e0d:1:3:58bf:fa02:c0de:5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 364373 (356K) [application/octet-stream]
Saving to: ‘libdvdcss_1.4.0.orig.tar.bz2’

libdvdcss_1.4.0.ori 100%[===================>] 355.83K   554KB/s    in 0.6s    

2017-05-31 17:44:29 (554 KB/s) - ‘libdvdcss_1.4.0.orig.tar.bz2’ saved [364373/364373]

libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.0.orig.tar.bz2: OK
libdvd-pkg: Unpacking and configuring...
libdvd-pkg: Building the package... (it may take a while)
libdvd-pkg: Build log will be saved to /usr/src/libdvd-pkg/libdvdcss2_1.4.0-1~local_amd64.build
Current: = cap_chown,cap_dac_override,cap_dac_read_search,cap_fowner,cap_fsetid,cap_kill,cap_setgid,cap_setuid,cap_setpcap,cap_linux_immutable,cap_net_bind_service,cap_net_broadcast,cap_net_admin,cap_net_raw,cap_ipc_lock,cap_ipc_owner,cap_sys_module,cap_sys_rawio,cap_sys_chroot,cap_sys_ptrace,cap_sys_pacct,cap_sys_admin,cap_sys_boot,cap_sys_nice,cap_sys_resource,cap_sys_time,cap_sys_tty_config,cap_mknod,cap_lease,cap_audit_write,cap_audit_control,cap_setfcap,cap_mac_override,cap_mac_admin,cap_syslog,cap_wake_alarm,cap_block_suspend,cap_audit_read+ep
Bounding set =cap_chown,cap_dac_override,cap_fowner,cap_wake_alarm,cap_block_suspend,cap_audit_read
Securebits: 024/0x14/5'b10100
 secure-noroot: no (unlocked)
 secure-no-suid-fixup: yes (unlocked)
 secure-keep-caps: yes (unlocked)
uid=0(root)
gid=0(root)
groups=0(root)
libdvd-pkg: Installing...
Selecting previously unselected package libdvdcss-dev:amd64.
(Reading database ... 177658 files and directories currently installed.)
Preparing to unpack .../libdvdcss-dev_1.4.0-1~local_amd64.deb ...
Unpacking libdvdcss-dev:amd64 (1.4.0-1~local) ...
Selecting previously unselected package libdvdcss2:amd64.
Preparing to unpack .../libdvdcss2_1.4.0-1~local_amd64.deb ...
Unpacking libdvdcss2:amd64 (1.4.0-1~local) ...
Setting up libdvdcss2:amd64 (1.4.0-1~local) ...
Setting up libdvdcss-dev:amd64 (1.4.0-1~local) ...
Processing triggers for libc-bin (2.24-9ubuntu2) ...

```
```

$ apt policy libdvdcss2
libdvdcss2:
  Installed: 1.4.0-1~local
  Candidate: 1.4.0-1~local
  Version table:
 *** 1.4.0-1~local 100
        100 /var/lib/dpkg/status
     
```
Cheers

---

