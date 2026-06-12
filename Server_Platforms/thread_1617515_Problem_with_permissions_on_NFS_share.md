---
title: "Problem with permissions on NFS share"
date: 2010-11-09
forum: Server Platforms
---

### Post by jarthurs on 2010-11-09
I've recently been trying to mount shared folders hosted on an Acer Altos EasyStore four drive NAS. Having set up a Ubuntu 10.04 server I initally managed to mount the NFS share manually to /nfs, but couldn't even ls a folder without getting a Permission denied message. I initally tried to chmod 777 the whole /nfs tree, this didn't work but I then tried chmod -R go+rw and this seems to have allowed me rw access to the whole shared folder.

I've now installed Torrentflux and pointed the downloads folder to the NFS share. When I upload a torrent file to the Torrentflux the torrent file is uploaded OK, I can start the torrent but as soon as a peer is found (and downloading begins) the torrent stops and I get 'Torrent Failed'. I've tried to chmod -R 777 the /nfs/Torrents/ folder which contains all the files needs by Torrentflux and I appear to have rw access for all users and groups but I cannot get Torrentflux to work.

The NFS share is mounted in fstab as:

nas:/nas/NASDisk-00004/media  /nfs  nfs  rw

It automounts fine and I can create and copy files into any folder from the command line, but for some reason Torrentflux appears to not have access to *something* on the NFS share.

If I create a folder using the SMB share, the permissions show both the UID and GID as numbers. Items created Torrentflux appear with the UID/GID of www-data and if I manually create or copy files into the folders they appear with UID/GID of the login username.

I'm banging my head against a wall here, I cannot find the right permissions to allow Torrentflux to work.

Regards,
Jason.

---

### Post by koenn on 2010-11-10
the account that reads/writes to the nfs folders needs to exist on the NAS device and have the required permissions on the  folder (on the NAS) in order to use them - or something along those lines. eg you probably need either a www-data user account or a user account with the same UID on your NAS system. 
read up on NFS security, and check your NAS manual for which version of nfs its using, and instructions about users and permissions.

---

### Post by jarthurs on 2010-11-11
> **koenn said:**
> the account that reads/writes to the nfs folders needs to exist on the NAS device and have the required permissions on the  folder (on the NAS) in order to use them - or something along those lines. eg you probably need either a www-data user account or a user account with the same UID on your NAS system. 
read up on NFS security, and check your NAS manual for which version of nfs its using, and instructions about users and permissions.

Unfortunately the only NFS settings available on the NAS are for the IP address the share is exported to, there is no option for username, UID or GID. Just been through the manual and there is no reference to which version of NFS is being used.

Regards,
Jason.

---

