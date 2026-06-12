---
title: "Sharing lib and binary files in a remote samba directory?"
date: 2018-11-28
forum: Server Platforms
---

### Post by pandoragami on 2018-11-28
Hello all!

This is what I have in my server bashrc file
```
export PATH="$PATH:/path/to/bin"
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/path/to/lib64"
source ~/OpenFOAM/OpenFOAM-v1806/etc/bashrc 

```and what I want to do is to take this location above and access it using samba from a remote LAN computer, actually sharing it across other machines so that there is one copy of OpenFOAM on a computer and the other clients access this copy in the samba directory.
What I know already is that without cifs there is no way for bash to access this samba directory folder but I'm not sure how to go about making this work.

thanks ahead to anyone who tries to help with this one.

---

### Post by wildmanne39 on 2018-11-28
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by TheFu on 2018-11-29
~/ is relative to every userid based on their $HOME environment variable.  That is probably the issue.

---

### Post by pandoragami on 2018-11-29
> **TheFu said:**
> ~/ is relative to every userid based on their $HOME environment variable.  That is probably the issue.


Yes, the problem is that home directory being on a remote computer but it doesn't matter what the directory is because somehow bash on the local machine has to see 
the directory. 

What I found was to use this

```
mount -t cifs -o vers=1.0,username=user_name //server_name/share_name /mnt/
```

to mount the remote server directory to the local client machine and then use that directory to export and source the lib and bin folders, it's just I'm unsure if this would work? Any suggestions?

---

### Post by TheFu on 2018-11-29
Linux HOME directories cannot be on CIFS mounts.  You can use NFS, but control over the permissions in the normal way UGO+RWX is required.  You can mount CIFS for data, but using it for Unix programs or development just becomes too much hassle to deal with.

And don't get me started on NTFS problems.

---

### Post by pandoragami on 2018-11-29
> **TheFu said:**
> Linux HOME directories cannot be on CIFS mounts.  You can use NFS, but control over the permissions in the normal way UGO+RWX is required.  You can mount CIFS for data, but using it for Unix programs or development just becomes too much hassle to deal with.

And don't get me started on NTFS problems.


Okay, how about something like a scsi drive on the server? It has a directory 

```
/media/pandoragami/scsi
```

---

### Post by TheFu on 2018-11-29
iSCSI is presented to Linux as a block device, so you'd format it with a Linux file system like ext4 and use it like any other SAN device through an HBA or AoE.

iSCSI client initiators cannot be shared concurrently by multiple systems.
[https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html.en](https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html.en)

If you can clarify the storage, other server OS with the storage, there might be a workable, F/LOSS, answer.  If it is running Windows, then you have to pay and do lots of maintenance whenever a userid is added or removed.  Basically, you can use NFS for HOME directories and this is a well-known pattern in corporate setups.  The autofs tool has modes to make it easy.

---

### Post by pandoragami on 2018-11-29
> **TheFu said:**
> iSCSI is presented to Linux as a block device, so you'd format it with a Linux file system like ext4 and use it like any other SAN device through an HBA or AoE.

iSCSI client initiators cannot be shared concurrently by multiple systems.
[https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html.en](https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html.en)

If you can clarify the storage, other server OS with the storage, there might be a workable, F/LOSS, answer.  If it is running Windows, then you have to pay and do lots of maintenance whenever a userid is added or removed.  Basically, you can use NFS for HOME directories and this is a well-known pattern in corporate setups.  The autofs tool has modes to make it easy.

The scsi drive is ext4 on a lubuntu 16.04 lts system. Anything else you need ask!

---

### Post by pandoragami on 2018-11-29
I managed to mount the directory with 

```
sudo mount -t cifs -v //pandoragami_server.local/scsi/ /mnt/scsi -o username=pandoragami
```

It asks for password and mounts to the directory /mnt/scsi

Then to unmount use 

```
umount /mnt/scsi
```

---

### Post by TheFu on 2018-11-29
I'm so sorry - I saw "iSCSI", not scsi, and headed off into enterprise solutions. Sorry to waste your time.

I don't know anything about OpenFOAM ... isn't that a CFD tool?  Studied CFD in grad school, long ago. We wrote custom fortran at the time. No matter.

Are you certain that OpenFOAM doesn't need to be fully installed onto each system where it runs?  Is everything self-contained?  No files placed elsewhere?  If so, then you are golden.

If it were me, I'd setup the OpenFOAM install to appear exactly in the same location on both systems. The one it is physically on somewhere under /opt/ and then I'd NFS mount remote:/opt/ onto the other machine as /opt/  

Sharing storage between Unix systems on the same LAN via NFS is pretty easy. The only trick is to make the userid and groupid (the numbers) match between the systems, assuming you aren't using centralized user management like LDAP already.  'id' on each system will provide the numbers - like 1001.  Only the userids that need access to the storage need to match. Same for the groupids.  Make those number match, but only for the groups that are important to the software working.  I wouldn't worry about any groups outside /opt/ if they don't matter.

There's an NFS-server how-to in the Ubuntu Server Guide. Google should find it.   [https://help.ubuntu.com/lts/serverguide/network-file-system.html.en](https://help.ubuntu.com/lts/serverguide/network-file-system.html.en) just make certain it is for the release you have.  18.04 changed things.

The client mount instructions might be a little different depending on the client-side ubuntu release. [https://help.ubuntu.com/lts/serverguide/network-file-system.html.en#nfs-client-configuration](https://help.ubuntu.com/lts/serverguide/network-file-system.html.en#nfs-client-configuration)  I don't have any 18.04 system here, so can't test it.

If you want to have a shared HOME on both systems, then using autofs makes more sense.

And it should go without saying - wired ethernet, no wifi.

---

### Post by pandoragami on 2018-11-29
> **TheFu said:**
> I'm so sorry - I saw "iSCSI", not scsi, and headed off into enterprise solutions. Sorry to waste your time.

I don't know anything about OpenFOAM ... isn't that a CFD tool?  Studied CFD in grad school, long ago. We wrote custom fortran at the time. No matter.

Are you certain that OpenFOAM doesn't need to be fully installed onto each system where it runs?  Is everything self-contained?  No files placed elsewhere?  If so, then you are golden.

If it were me, I'd setup the OpenFOAM install to appear exactly in the same location on both systems. The one it is physically on somewhere under /opt/ and then I'd NFS mount remote:/opt/ onto the other machine as /opt/  

Sharing storage between Unix systems on the same LAN via NFS is pretty easy. The only trick is to make the userid and groupid (the numbers) match between the systems, assuming you aren't using centralized user management like LDAP already.  'id' on each system will provide the numbers - like 1001.  Only the userids that need access to the storage need to match. Same for the groupids.  Make those number match, but only for the groups that are important to the software working.  I wouldn't worry about any groups outside /opt/ if they don't matter.

There's an NFS-server how-to in the Ubuntu Server Guide. Google should find it.   [https://help.ubuntu.com/lts/serverguide/network-file-system.html.en](https://help.ubuntu.com/lts/serverguide/network-file-system.html.en) just make certain it is for the release you have.  18.04 changed things.

The client mount instructions might be a little different depending on the client-side ubuntu release. [https://help.ubuntu.com/lts/serverguide/network-file-system.html.en#nfs-client-configuration](https://help.ubuntu.com/lts/serverguide/network-file-system.html.en#nfs-client-configuration)  I don't have any 18.04 system here, so can't test it.

If you want to have a shared HOME on both systems, then using autofs makes more sense.

And it should go without saying - wired ethernet, no wifi.

Definitely wired ethernet! Openfoam is self contained and I tried running it on one client machine and seems to work parallel with cifs, as for running a cluster from one cifs directory, that's something I need to setup. I'm afraid the mpi files may need to be also installed in the usr/local/bin and usr/local/lib client side folders but besides that I've had no problems. I even compiled openfoam and mpi on one machine and migrated them all to 2 others, both running same 16.04 LTS ubuntu variants (one xubuntu and another lubuntu), both machines work fine in parallel (this isn't related to cifs though, just another setup). 

What I've decided is to try using NFS now. I've managed to mirror a folder using the line in /etc/exports

```
/media/user/scsi ip-address( rw, sync, no_root_squash, no_subtree_check)
```

and this works for a small sized folder, but my openfoam directory is 4 gigs and that's without paraview which is installed with QT5 (All these are compiled from source) which adds 8 gigs for a total of 12 gigs in one directory. Obviously it would take a long time to boot the directory on the client machine for that so I wondered if the whole directory could be mirrored. It doesn't need to be writable, just readable? But overall I don't want to copy 12 gigs from the server to 2 client machines as I'm trying to save space. Do I just change something in the above command in the /etc/exports or is there something else that needs to be added? I'll check out the links too... thanks!

---

### Post by TheFu on 2018-11-30
I NFS mount 10+TB of storage around here. From my laptop: ```

$ df -h
Filesystem                         Size  Used Avail Use% Mounted on
romulus:/raid/media                1.8T  1.7T   51G  98% /R
istar:/DD                          3.5T  3.4T  139G  97% /DD
istar:/D                           3.5T  3.4T   71G  99% /D
istar:/misc/D5                     3.5T  3.3T  175G  96% /misc/D5
romulus:/Data/r2                   1.3T  1.1T  132G  89% /S
```

Also, you can share /usr/local/ if you like, assuming nothing down there (especially in /usr/local/etc/) is tied to anything specific on the main machine.  Just be certain that it is mounted to /usr/local on the client machine.  The Linux File System Hierarchy standards lay out what goes where and which can be shared, assuming the installers followed the rules.  Distros follow the rules.

I treat NFS storage like local storage on most systems, though for my Nextcloud server, I mount things read-only because of security risk mitigation strategies.

---

### Post by pandoragami on 2018-11-30
> **TheFu said:**
> I NFS mount 10+TB of storage around here. From my laptop: ```

$ df -h
Filesystem                         Size  Used Avail Use% Mounted on
romulus:/raid/media                1.8T  1.7T   51G  98% /R
istar:/DD                          3.5T  3.4T  139G  97% /DD
istar:/D                           3.5T  3.4T   71G  99% /D
istar:/misc/D5                     3.5T  3.3T  175G  96% /misc/D5
romulus:/Data/r2                   1.3T  1.1T  132G  89% /S
```

Also, you can share /usr/local/ if you like, assuming nothing down there (especially in /usr/local/etc/) is tied to anything specific on the main machine.  Just be certain that it is mounted to /usr/local on the client machine.  The Linux File System Hierarchy standards lay out what goes where and which can be shared, assuming the installers followed the rules.  Distros follow the rules.

I treat NFS storage like local storage on most systems, though for my Nextcloud server, I mount things read-only because of security risk mitigation strategies.

Basically mounting a directory will always take up space on your local drive? With cifs I mounted the location and the local machine only reads the files it needs when they are called. I have only 3 gigs of space left on my local machine and the openfoam on the server is 12 gigs so that's the reason why but I'm not sure how NFS would save me here. I did try running the cifs mount with openfoam and unfortunately after 3 cores running it, my computer froze on the 4th. I tried the same openfoam run with the local installation on the client hard drive and it worked fine with 6 cores. What could cause that to happen. cifs only seems to need to load once.

---

### Post by TheFu on 2018-11-30
What?  NFS and CIFS mounts only use an empty directory on the local storage.  The remote storage only **appears** like local storage.  It isn't using internal disk for anything beyond what the OS would use for disk buffers already regardless.

Plus NFS is about 20% faster than CIFS, includes better file locking and scales to thousands of clients.  I've used NFS with over 600 clients inside enterprises.

In short, CIFS is a worst case solution meant to accommodate Windows clients, not Unix clients. Unix has better solutions which have less overhead, faster, more secure.  NFS is one, but there are others for specialized needs.  NFS is a 95% solution - use it 95% of the time, unless some specialized need recommends some other solution like iSCSI, AoE, Gluster, Sheepdog, or some other remote storage solution.

Could you be mixing up storage amounts with RAM amounts?  12G is nothing for storage. Nothing for NFS.  I think you'll be happy with NFS.

Or am I completely missing the point?

---

### Post by pandoragami on 2018-11-30
> **TheFu said:**
> What?  NFS and CIFS mounts only use an empty directory on the local storage.  The remote storage only **appears** like local storage.  It isn't using internal disk for anything beyond what the OS would use for disk buffers already regardless.

Plus NFS is about 20% faster than CIFS, includes better file locking and scales to thousands of clients.  I've used NFS with over 600 clients inside enterprises.

In short, CIFS is a worst case solution meant to accommodate Windows clients, not Unix clients. Unix has better solutions which have less overhead, faster, more secure.  NFS is one, but there are others for specialized needs.  NFS is a 95% solution - use it 95% of the time, unless some specialized need recommends some other solution like iSCSI, AoE, Gluster, Sheepdog, or some other remote storage solution.

Could you be mixing up storage amounts with RAM amounts?  12G is nothing for storage. Nothing for NFS.  I think you'll be happy with NFS.

Or am I completely missing the point?


No, you're explaining everything fine, thanks so far. My ram is 32 gigs on the client machine. I just realized that when I mounted my NFS on the client that it was the server directory size on the bottom on the file manager, I use thunar on the client machine. So basically I have only 18 gigs on the server scsi and when I mounted that drive I mistook  as the client drive since the gigabytes of harddrive space look so similar. 

So besides NFS you mentioned those other solutions (" iSCSI, AoE, Gluster, Sheepdog, or some other remote storage solution"), which would be best for what I'm trying in your opinion, for openfoam?

---

### Post by TheFu on 2018-11-30
> **pandoragami said:**
> 
So besides NFS you mentioned those other solutions (" iSCSI, AoE, Gluster, Sheepdog, or some other remote storage solution"), which would be best for what I'm trying in your opinion, for openfoam?

NFS from what you've said.  The others are for SANs (block devices) or HA or virtualization.

---

