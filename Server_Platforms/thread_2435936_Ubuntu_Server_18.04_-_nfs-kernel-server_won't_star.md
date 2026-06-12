---
title: "Ubuntu Server 18.04 - nfs-kernel-server won't start"
date: 2020-01-28
forum: Server Platforms
---

### Post by tailing on 2020-01-28
Hi, I have a file server using 18.04 server on an HP N40L, it started off as 14.04 but when updates stopped I upgraded it to 16.04, then 18.04, one after the other. It's generally headless but at some point when it was still 14.04 I installed Lubuntu to sometimes access it through the DE.

Till now it's been serving windows clients with samba but I'm setting up a Linux client and tried to install NFS but am having some problems with it.

This is the output after running 
sudo apt install nfs-kernel-server (note there were additional packages installed the first time but I removed nfs-kernel-server and reinstalled to show the output here)

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nfs-kernel-server
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 93.8 kB of archives.
After this operation, 345 kB of additional disk space will be used.
Get:1 http://au.archive.ubuntu.com/ubuntu bionic-updates/main amd64 nfs-kernel-server amd64 1:1.3.4-2.1ubuntu5.2 [93.8 kB]
Fetched 93.8 kB in 1s (147 kB/s)       
Selecting previously unselected package nfs-kernel-server.
(Reading database ... 225221 files and directories currently installed.)
Preparing to unpack .../nfs-kernel-server_1%3a1.3.4-2.1ubuntu5.2_amd64.deb ...
Unpacking nfs-kernel-server (1:1.3.4-2.1ubuntu5.2) ...
Setting up nfs-kernel-server (1:1.3.4-2.1ubuntu5.2) ...
A dependency job for nfs-server.service failed. See 'journalctl -xe' for details.
A dependency job for nfs-server.service failed. See 'journalctl -xe' for details.
invoke-rc.d: initscript nfs-kernel-server, action "restart" failed.
&#9679; nfs-server.service - NFS server and services
   Loaded: loaded (/lib/systemd/system/nfs-server.service; enabled; vendor preset: enabled)
   Active: inactive (dead)


Jan 28 13:43:07 proliant systemd[1]: Dependency failed for NFS server and services.
Jan 28 13:43:07 proliant systemd[1]: nfs-server.service: Job nfs-server.service/start failed with result 'dependency'.
Jan 28 13:52:36 proliant systemd[1]: Dependency failed for NFS server and services.
Jan 28 13:52:36 proliant systemd[1]: nfs-server.service: Job nfs-server.service/start failed with result 'dependency'.
Jan 28 13:59:40 proliant systemd[1]: Dependency failed for NFS server and services.
Jan 28 13:59:40 proliant systemd[1]: nfs-server.service: Job nfs-server.service/start failed with result 'dependency'.
Jan 29 09:10:51 proliant systemd[1]: Dependency failed for NFS server and services.
Jan 29 09:10:51 proliant systemd[1]: nfs-server.service: Job nfs-server.service/start failed with result 'dependency'.
Jan 29 09:10:53 proliant systemd[1]: Dependency failed for NFS server and services.
Jan 29 09:10:53 proliant systemd[1]: nfs-server.service: Job nfs-server.service/start failed with result 'dependency'.
Failed to restart nfs-kernel-server, ignoring.
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for ureadahead (0.100.0-21) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (237-3ubuntu10.33) ...

```

Checking journalctl as suggested

```
Jan 29 09:26:01 proliant systemd[1]: Mounting RPC Pipe File System...Jan 29 09:26:01 proliant systemd[1]: Mounting NFSD configuration filesystem...
Jan 29 09:26:01 proliant mount[1249]: mount: /run/rpc_pipefs: unknown filesystem type 'rpc_pipefs'.
Jan 29 09:26:01 proliant systemd[1]: Starting Preprocess NFS configuration...
Jan 29 09:26:01 proliant systemd[1]: run-rpc_pipefs.mount: Mount process exited, code=exited status=32
Jan 29 09:26:01 proliant systemd[1]: run-rpc_pipefs.mount: Failed with result 'exit-code'.
Jan 29 09:26:01 proliant systemd[1]: Failed to mount RPC Pipe File System.
Jan 29 09:26:01 proliant systemd[1]: Dependency failed for NFSv4 ID-name mapping service.
Jan 29 09:26:01 proliant systemd[1]: nfs-idmapd.service: Job nfs-idmapd.service/start failed with result 'dependency'.
Jan 29 09:26:01 proliant systemd[1]: Dependency failed for RPC security service for NFS server.
Jan 29 09:26:01 proliant systemd[1]: rpc-svcgssd.service: Job rpc-svcgssd.service/start failed with result 'dependency
Jan 29 09:26:01 proliant systemd[1]: Dependency failed for RPC security service for NFS client and server.
Jan 29 09:26:01 proliant systemd[1]: rpc-gssd.service: Job rpc-gssd.service/start failed with result 'dependency'.
Jan 29 09:26:01 proliant mount[1250]: mount: /proc/fs/nfsd: unknown filesystem type 'nfsd'.
Jan 29 09:26:01 proliant systemd[1]: Started Preprocess NFS configuration.
Jan 29 09:26:01 proliant systemd[1]: proc-fs-nfsd.mount: Mount process exited, code=exited status=32
Jan 29 09:26:01 proliant systemd[1]: proc-fs-nfsd.mount: Failed with result 'exit-code'.
Jan 29 09:26:01 proliant systemd[1]: Failed to mount NFSD configuration filesystem.
Jan 29 09:26:01 proliant systemd[1]: Dependency failed for NFS Mount Daemon.
Jan 29 09:26:01 proliant systemd[1]: Dependency failed for NFS server and services.
Jan 29 09:26:01 proliant systemd[1]: nfs-server.service: Job nfs-server.service/start failed with result 'dependency'.
Jan 29 09:26:01 proliant systemd[1]: nfs-mountd.service: Job nfs-mountd.service/start failed with result 'dependency'.
```

I only have intermediate Linux knowledge, I can read and follow instructions and get things done but to try to diagnose this issue is a bit beyond me, I would appreciate any help.

---

### Post by darkod on 2020-01-29
In short, google search mentions cases where this error was fixed by reboot. Did you reboot the server recently?

If not, please do and then we can double check if all packages installed correctly after it boots again.

---

### Post by tailing on 2020-01-29
Yes I must have found the same info you did and tried to reboot which doesn't fix the issue. After rebooting and checking journalctl again I noticed these errors. I'm not sure if they're related but nfs runs as a kernel module right?

```
Jan 30 08:28:38 proliant systemd[1]: Starting Load Kernel Modules...Jan 30 08:28:38 proliant systemd-modules-load[503]: ctx=0x55f4c7007de0 path=/lib/modules/4.15.0-72-generic/kernel/drivers/parport/parport.ko error=No such file or directory
Jan 30 08:28:38 proliant systemd-modules-load[503]: ctx=0x55f4c7007de0 path=/lib/modules/4.15.0-72-generic/kernel/drivers/parport/parport.ko error=No such file or directory
Jan 30 08:28:38 proliant systemd-modules-load[503]: Failed to insert 'lp': No such file or directory
Jan 30 08:28:38 proliant systemd-modules-load[503]: ctx=0x55f4c7007de0 path=/lib/modules/4.15.0-72-generic/kernel/drivers/parport/parport.ko error=No such file or directory
Jan 30 08:28:38 proliant systemd-modules-load[503]: ctx=0x55f4c7007de0 path=/lib/modules/4.15.0-72-generic/kernel/drivers/parport/parport.ko error=No such file or directory
Jan 30 08:28:38 proliant systemd-modules-load[503]: Failed to insert 'ppdev': No such file or directory
Jan 30 08:28:38 proliant systemd-modules-load[503]: ctx=0x55f4c7007de0 path=/lib/modules/4.15.0-72-generic/kernel/drivers/parport/parport.ko error=No such file or directory
Jan 30 08:28:38 proliant systemd-modules-load[503]: ctx=0x55f4c7007de0 path=/lib/modules/4.15.0-72-generic/kernel/drivers/parport/parport.ko error=No such file or directory
Jan 30 08:28:38 proliant systemd-modules-load[503]: Failed to insert 'parport_pc': No such file or directory
Jan 30 08:28:38 proliant systemd-modules-load[503]: Module 'loop' is builtin
Jan 30 08:28:38 proliant systemd-modules-load[503]: ctx=0x55f4c7007de0 path=/lib/modules/4.15.0-72-generic/kernel/drivers/parport/parport.ko error=No such file or directory
Jan 30 08:28:38 proliant systemd-modules-load[503]: ctx=0x55f4c7007de0 path=/lib/modules/4.15.0-72-generic/kernel/drivers/parport/parport.ko error=No such file or directory
Jan 30 08:28:38 proliant systemd-modules-load[503]: Failed to insert 'lp': No such file or directory
Jan 30 08:28:38 proliant systemd[1]: systemd-modules-load.service: Main process exited, code=exited, status=1/FAILURE
Jan 30 08:28:38 proliant systemd[1]: systemd-modules-load.service: Failed with result 'exit-code'.
Jan 30 08:28:38 proliant systemd[1]: Failed to start Load Kernel Modules.

```

---

### Post by darkod on 2020-01-30
First check if there are any dependencies missing:
```
sudo apt-get install -f
```

If any packages are pending configuration you can use:
```
sudo dpkg --configure -a
```

Looks like some mess left over by the upgrade. Sometimes things don't work out 100% perfect when you upgrade the OS instead of clean install.

First see what the above commands say, then you can investigate if some kernel module is missing and how to create it. Honestly I've never done that yet.

---

### Post by tailing on 2020-01-30
No luck, no packages are required after the first command, the second command did not show any output.

---

### Post by darkod on 2020-01-31
According to this: [https://ubuntu.pkgs.org/18.04/ubuntu-updates-main-amd64/linux-modules-4.15.0-60-generic_4.15.0-60.67_amd64.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-updates-main-amd64/linux-modules-4.15.0-60-generic_4.15.0-60.67_amd64.deb.html)

The parport.ko module is included in linux-modules-... But note that the link is for kernel 4.15.0-60 and you have 4.15.0-72. Looks like the fix is to install that modules package.

What if you try:
```
sudo apt-get install linux-modules-4.15.0-72-generic
```

---

### Post by tailing on 2020-02-03
That did the trick, I feared a convoluted solution but that was quite simple, I installed the package, rebooted and nfs starts no problem. Thank you very much for your help!

I'll mark as solved.

---

