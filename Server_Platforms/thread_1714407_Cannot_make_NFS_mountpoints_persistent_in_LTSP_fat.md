---
title: "Cannot make NFS mountpoints persistent in LTSP fat clients"
date: 2011-03-25
forum: Server Platforms
---

### Post by Alain Kansen on 2011-03-25
After having build a thin client  server based on Lucid, I'm trying with a fat one.
It works ok, except that I can't make NFS mount points persistent. Every time a user logs in, he has to manually run a 'sudo nfsmount.sh' script on the fat client  to mount the NFS shares from a dedicated NFS server.
The script first reloads portmap, then simply mounts external NFS shares and works perfectly.
However,

[LIST]
[*]I tried with RCFILE_nn in lts.conf
[*]directly in the fat chroot /etc/fstab image file
[*]calling the script from the rc.local client's script
[/LIST]
No way: the NFS mountpoints are unmounted at every logout.

Any idea :confused:

---

### Post by rootyourbrain on 2013-01-23
> **Alain Kansen said:**
> After having build a thin client  server based on Lucid, I'm trying with a fat one.
It works ok, except that I can't make NFS mount points persistent. Every time a user logs in, he has to manually run a 'sudo nfsmount.sh' script on the fat client  to mount the NFS shares from a dedicated NFS server.
The script first reloads portmap, then simply mounts external NFS shares and works perfectly.
However,

[LIST]
[*]I tried with RCFILE_nn in lts.conf
[*]directly in the fat chroot /etc/fstab image file
[*]calling the script from the rc.local client's script
[/LIST]
No way: the NFS mountpoints are unmounted at every logout.

Any idea :confused:

Hey Kansen.. I'm kind of working on a similar project as well. You might consider looking into autofs/automount 
```
sudo apt-get install autofs && sudo apt-get install nfs-common
```
My dilemma is very similar, but someone posted somewhere that when they did this as a 'per credentials' basis, they had to write a python script.... This is a bit over my head (right now) but I'm working on getting it done.

A point to remember is that before editing fstab with your NFS location information, you want the location mounted. THEN, edit fstab and test.

If you run into problems - like I did - and the Ubuntu splash tells you "unable to mount...." Hit M for recovery and comment out (# Your_fstab_entry), save and reboot. Just keep searching, friend. If you come up with a solution, please share it with the community.

Additionally, you make consider making the .sh file a part of the startup environment.. Just a thought. If anyone has a better suggestion, please share.

---

