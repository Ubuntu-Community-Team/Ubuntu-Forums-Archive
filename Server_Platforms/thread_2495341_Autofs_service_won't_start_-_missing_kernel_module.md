---
title: "Autofs service won't start - missing kernel module?"
date: 2024-02-15
forum: Server Platforms
---

### Post by ecrosby on 2024-02-15
Hello, all. I'm hoping someone can assist.
I am in a secure environment so I am limited to how much I can share on this forum during troubleshooting. I am currently running Ubuntu Server 18.04.6 with the 5.4.0-104 low latency kernel. The admin before me who is no longer around setup everything on the server but he may have missed a step. I'm currently having an issue with the autofs service not starting and I think it may be because of a missing kernel module from that particular low latency kernel version.
I would appreciate if someone could point me in the right direction as to what I need to download and/or install to get autofs service running.

EDIT: Just a follow up. It looks as if autofs modules are missing if I looking in /lib/modules/5.4.0-104-lowlatency/kernel/fs/

So, it is still a question of how do I get that module installed for that kernel?

---

### Post by TheFu on 2024-02-15
**autofs** is just the handler for mount programs.  I use it to mount some-times connected storage, all USB storage and all network storage.
 /lib/modules/5.15.0-94-generic/kernel/fs/autofs/autofs4.ko

Typically, I'd install autofs, nfs-common and nfs-kernel packages and that would be it.  APT dependencies would pull in any other required packages. Those dependencies are spelled out inside the .deb files. 
```
$ apt depends autofs
autofs
  PreDepends: init-system-helpers (>= 1.54~)
  Depends: libc6 (>= 2.28)
  Depends: libtirpc3 (>= 1.0.2)
  Depends: libxml2 (>= 2.7.4)
  Depends: ucf
  Breaks: <autofs5> (<< 5.0.6-1~)
  Recommends: nfs-common
 |Recommends: kmod
  Recommends: <module-init-tools>
  Recommends: e2fsprogs
  Replaces: <autofs5> (<< 5.0.6-1~)

```
I don't install the "recommended" package by default.

---

### Post by ecrosby on 2024-02-15
> **TheFu said:**
> **autofs** is just the handler for mount programs.  I use it to mount some-times connected storage, all USB storage and all network storage.
 /lib/modules/5.15.0-94-generic/kernel/fs/autofs/autofs4.ko

Typically, I'd install autofs, nfs-common and nfs-kernel packages and that would be it.  APT dependencies would pull in any other required packages. Those dependencies are spelled out inside the .deb files. 
```
$ apt depends autofs
autofs
  PreDepends: init-system-helpers (>= 1.54~)
  Depends: libc6 (>= 2.28)
  Depends: libtirpc3 (>= 1.0.2)
  Depends: libxml2 (>= 2.7.4)
  Depends: ucf
  Breaks: <autofs5> (<< 5.0.6-1~)
  Recommends: nfs-common
 |Recommends: kmod
  Recommends: <module-init-tools>
  Recommends: e2fsprogs
  Replaces: <autofs5> (<< 5.0.6-1~)

```
I don't install the "recommended" package by default.

So when I run apt list and grep for those packages, it looks as if everything is installed, even the recommended packages.

---

### Post by TheFu on 2024-02-15
What, exactly, is the error related to the autofs start? Any hints?

```
$ systemctl status autofs
```

---

### Post by ecrosby on 2024-02-15
Yeah. It's not an uncommon error. I have found it frequently in my searches.

> /usr/sbin/automount: test mount forbidden or incorrect kernel protocol version, kernel protocol version 5.00 or above required.
autofs.service: Control process exited, code=exited status=1
autofs.service: Failed with result 'exit-code':

---

### Post by TheFu on 2024-02-15
What file system?
What are the exports and what are the mount options?

Please, please, use forum code-tags for terminal output, as I did in post #2 above.

---

### Post by ecrosby on 2024-02-15
Unfortunately, the server is in a secured, segmented network not connected to the internet so I have no way of posting output. Everything that I can provide I am typing by hand.

The file system is ext4. This is a client that is supposed to mount NAS shares using autofs.'filename' with NAS server information in it. But the thing is it can't get that far because I can't even get the autofs service to start. And I believe it won't start because of those missing low latency kernel autofs modules.

---

### Post by TheFu on 2024-02-15
> **ecrosby said:**
> Unfortunately, the server is in a secured, segmented network not connected to the internet so I have no way of posting output. Everything that I can provide I am typing by hand.
I'd redirect the output to a file on a USB stick, assuming the USB ports aren't hot-glued. BTW, I've worked in air-gapped environments too - were we actually did hot-glue any external ports on workstations that weren't in locked cabinets. The building was a huge Faraday cage - no RF in or out.  When I needed to bring new software in, that was part of my job, it came through tape and had 2 middle-men involved who would copy the tape contents from an "introduction workstation", then run all the AV scans available on all files, then copy the contents over to a different network, in a more secured part of the building, in a more secure room, still outside the server floor area.  The following day, I'd go to that room and "find" the files, then move them to my servers.  Then I'd move to a different part of the building to a fast workstation and setup the new software version so it and the older versions wouldn't conflict, but were available for different managers to choose for specific missions.  Basically, they'd just have symbolic links pointing at the SW version they wanted.

> **ecrosby said:**
> The file system is ext4. This is a client that is supposed to mount NAS shares using autofs.'filename' with NAS server information in it. But the thing is it can't get that far because I can't even get the autofs service to start. And I believe it won't start because of those missing low latency kernel autofs modules.

Does a manual mount command work for NFS?  
```
mount -t nfs -o nconnect=2,proto=tcp,rw,async      istar:/d/D1    /d/D1
```

Example autofs config: 
```
$ more /etc/auto.nfs 

/d/D1 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D1
/d/D2 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D2
/d/D3 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D3

```
Of course the auto.master refers to the auto.nfs file.
```
/-      /etc/auto.nfs --timeout=60 --ghost
```

That results in these mounts, after I perform some action to force the mount to happen:
```
Filesystem                               Type  Size  Used Avail Use% Mounted on
istar:/d/D1                              **nfs4**  3.5T  3.5T   13G 100% /d/D1
istar:/d/D2                              **nfs4**  3.6T  3.6T   24G 100% /d/D2
istar:/d/D3                              **nfs4**  3.6T  3.6T   20G 100% /d/D3

```

---

### Post by ecrosby on 2024-02-16
Yep. A manual mount of the NFS share works just fine.

---

### Post by TheFu on 2024-02-16
> **ecrosby said:**
> Yep. A manual mount of the NFS share works just fine.

Did you setup the **autofs** config files as I've shown and restart autofs.  Then try to **ls** somewhere inside the unmounted storage.
Before doing the ls, in a another terminal, run **dmesg -w**.  Anything in that?

I have to ask these things. You didn't report it.

---

### Post by ecrosby on 2024-02-16
Autofs files are already configured in our environment. However, with the validated config used successfully on other (RHEL/CentOS) servers, autofs service will not start on this problem server.

---

### Post by TheFu on 2024-02-16
> **ecrosby said:**
> Autofs files are already configured in our environment. However, with the validated config used successfully on other (RHEL/CentOS) servers, autofs service will not start on this problem server.

autofs is autofs on all Linux, so what's different about the working and non-working environments?  

Any other hints in the assorted log files?

The 5.4 kernel is pretty old. I moved to 5.15 when 18.04 standard support ended in 2023.

---

### Post by ecrosby on 2024-02-17
All the logs are displaying the same generic error: /usr/sbin/automount: test mount forbidden or incorrect kernel protocol version, kernel protocol version 5.00 or above required.

Unfortunately, due to the program, we can't move to a newer kernel at this time.
I think my options are limited. After communicating with the program leads on Friday, I think we are stuck where we are. We're either not going to use autofs and just setup a permanent NFS share for our purposes (since NFS works) or work with what we have until a much later date when we can move past 18.04.
I appreciate your time and responses @TheFu

---

### Post by TheFu on 2024-02-17
In googling the error ... there are a few things not mentioned.  running out of inodes in /tmp/ was one. [https://www.suse.com/support/kb/doc/?id=000020955](https://www.suse.com/support/kb/doc/?id=000020955)
Is this system on real hardware, inside a VM, inside a container, or a WSL thing?

Coming back to the kernel modules, 
**sudo apt -y install linux-modules-extra-$(uname -r)**

Just a few more things to check out, if you haven't already.  I've used NFS for 30 yrs and can't say I've seen this issue before.  Being in a secure environment makes it difficult.  I'd clone the server, take that clone to a different network and work on solutions there, assuming this is allowed.

---

### Post by ecrosby on 2024-02-18
> In googling the error ... there are a few things not mentioned.  running out of inodes in /tmp/ was one. [https://www.suse.com/support/kb/doc/?id=000020955](https://www.suse.com/support/kb/doc/?id=000020955)

Yep, saw that. It's not an issue.

> Is this system on real hardware, inside a VM, inside a container, or a WSL thing?

It is a VM.

> 
Coming back to the kernel modules, 
**sudo apt -y install linux-modules-extra-$(uname -r)**

Yep, tried that on a test machine that has a connection to the Ubuntu repository. It didn't work. I can't remember the output but it seemed there was no extra modules for that kernel being used.
What I did do in that testing is take that same VM that was on a outward facing network to the Ubuntu repository was install the next low latency kernel version up and autofs worked. So, again, I am leaning toward the kernel that we are required to use has missing autofs modules.
As mentioned, I'll like just have to skip the autofs option and just setup an NFS share for our purposes. Or, don't even setup the NFS share at all. I am letting the program leads make that decision.

---

### Post by TheFu on 2024-02-18
Well, crap.

There's only 1 other thing, and I hate suggesting it.  systemd-mount supports an automount option.  This is separate from autofs. 

[Https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156](Https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156)

It doesn't work quiet the same way - it delays mounts until requested, but it doesn't umount unused file systems later.  It uses the fstab (or a unit file).
> sudoedit /etc/fstab
# add a line to the fstab:
```
romulus:/Data/r2     /S      nfs        **x-systemd.automount**,x-systemd.idle-timeout=600s,proto=tcp,noauto    0     2
```

where:
* /S is the local mount point
* x-systemd.automount            appears to HAVE TO BE first in the options
* x-systemd.idle-timeout=600s    is optional AND doesn't work
* x-systemd.device-timeout=10s   is optional - stop trying after 10 sec
* proto=tcp                      is a best practice for NFS 
* noauto              is there to prevent mounting before a request was made

```
sudo systemctl daemon-reload
sudo systemctl start S.automount
```
    OR
```
sudo systemctl restart S.automount
```

For remote mounts:
```
sudo systemctl daemon-reload
sudo systemctl restart remote-fs.target
```

I tested this a few years ago and haven't touched it since.  My testing was on 18.04, I think.

---

