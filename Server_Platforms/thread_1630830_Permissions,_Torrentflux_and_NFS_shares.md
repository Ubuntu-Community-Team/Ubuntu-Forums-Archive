---
title: "Permissions, Torrentflux and NFS shares"
date: 2010-11-25
forum: Server Platforms
---

### Post by jarthurs on 2010-11-25
I have a server set up running Torrentflux, now I had hoped to seed some of the torrents located on my NAS rather than storing lots of duplicate ISO files on the torrentflux box itself.

However I have come across a permissions problem. I have a folder on my Acer EasyStore NAS mounted as an NFS share to /nfs on my Torrentflux box. This appears to work fine, I can login as the user 'torrent' and create/copy/delete files and folders to my hearts content.

Torrentflux works fine when the source/destination directory is pointed at the default /var/cache/torrentflux but if I point it at /nfs/torrents (a folder on the NAS) any attempt to start a torrent is met with 'Download Failed'. I have chmod -R 777 /nfs/torrents to allow access to anyone as Torrentflux writes files using the user 'www-data'. 

Uploading a .torrent file to the Torrentflux box works fine and this appears to be stored on the NAS in the /.torrents folder, so something can write to the NAS. But starting a torrent, it goes from 'Queued' to 'connecting to peers' and then as soon as a download begins straight to 'Download Failed'.

I had assumed that with the folder chmod'ed to 777 there should no longer be any write issues for any user or group. But something cannot write to the NFS share and the torrents are failing as a result.

The NAS only allows the share to be allocated to a single IP, there are no user or group options available when setting up an NFS share.

Anyone shed some light on this issue?

Regards,
Jason.

---

### Post by jodue on 2010-12-08
i have the exact same situation/probleme here. i used tf for about 2 years now without any major problems but i have i running on a different machine now and want to write all downloads to a remote nfs storage. "download failed!" is all i get which makes no sense because it's writable by the www-data user ...

did you find any solution to this? i guess the easiest solution to circumvent this problem would be to move finished torrents to the nfs storage. yet this is no ideal solution for me as i run tf on a vm with minimal disk space, so running torrents with e.g. 10GB would not not work...

any ideas?

---

### Post by jodue on 2010-12-08
after some playing around i finally found the solution to this problem and i want to share it here because a google search did not bring up any useful hints.

it looks to me like bittornado wanted to lock the download-file but this resulted in an error. using the nfs mount option "-o lock" solved this problem. i guess using nfs4 would have also worked because it has a more advanced implementation for file-locking.

---

### Post by jarthurs on 2011-11-08
> **jodue said:**
> after some playing around i finally found the solution to this problem and i want to share it here because a google search did not bring up any useful hints.

it looks to me like bittornado wanted to lock the download-file but this resulted in an error. using the nfs mount option "-o lock" solved this problem. i guess using nfs4 would have also worked because it has a more advanced implementation for file-locking.

I also solved it in the end by mounting using CIFS and specifying nounix in /etc/fstab otherwise there were horrible permissions issues.

Regards,
Jason.

---

