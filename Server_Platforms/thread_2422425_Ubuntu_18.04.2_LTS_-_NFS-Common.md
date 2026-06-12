---
title: "Ubuntu 18.04.2 LTS - NFS-Common"
date: 2019-07-07
forum: Server Platforms
---

### Post by juniperms on 2019-07-07
I'm running a fresh copy of Ubuntu 18.04.2 LTS and have nfs-common installed. I'm having an issue where nfs-common will not auto start and requires manual intervention. I'm not sure where the issue may be, but this happened after I changed the IP address on the server. I changed the IP address back, but the issue still persist. Has this happened to anyone else?

---

### Post by darkod on 2019-07-07
Are you sure nfs-common service should be running all the time at all?

I have nfs server and client on my LAN, and I just checked both and nfs-common is stopped (inactive). But nfs shares work just fine all the time.

---

### Post by juniperms on 2019-07-07
I thought it did, but looking at my Plex server, nfs-common is inactive and my shares are mounted.  I removed my share information from /etc/fstab and added it back, but no difference.  Below my fstab lines is the logs.  I'm thinking it's trying to mount the shares too fast and the network interface isn't up/up yet.

#
#
# Synology NFS File Shares
192.168.30.24:/volume1/Media   /mnt/nfs/tv nfs auto,noatime,nolock,bg,nfsvers=3,intr,tcp,actimeo=1800 0 0
192.168.30.24:/volume1/nzbget_dl   /mnt/nfs/nzbget_dl nfs auto,noatime,nolock,bg,nfsvers=3,intr,tcp,actimeo=1800 0 0
192.168.30.24:/volume1/Media   /mnt/nfs/movies nfs auto,noatime,nolock,bg,nfsvers=3,intr,tcp,actimeo=1800 0 0


Jul  7 14:14:14 downloader systemd[1]: Mounting /mnt/**nfs**/tv...
Jul  7 14:14:14 downloader systemd[1]: Mounting /mnt/**nfs**/nzbget_dl...
Jul  7 14:14:14 downloader mount[773]: mount.**nfs**: Network is unreachable
Jul  7 14:14:14 downloader systemd[1]: Mounting /mnt/**nfs**/movies...
Jul  7 14:14:14 downloader mount[777]: mount.**nfs**: Network is unreachable
Jul  7 14:14:14 downloader mount[780]: mount.**nfs**: Network is unreachable
Jul  7 14:14:14 downloader systemd[1]: mnt-**nfs**-tv.mount: Mount process exited, code=exited status=32
Jul  7 14:14:14 downloader systemd[1]: mnt-**nfs**-tv.mount: Failed with result 'exit-code'.
Jul  7 14:14:14 downloader systemd[1]: Failed to mount /mnt/**nfs**/tv.
Jul  7 14:14:14 downloader systemd[1]: mnt-**nfs**-nzbget_dl.mount: Mount process exited, code=exited status=32
Jul  7 14:14:14 downloader systemd[1]: mnt-**nfs**-nzbget_dl.mount: Failed with result 'exit-code'.
Jul  7 14:14:14 downloader systemd[1]: Failed to mount /mnt/**nfs**/nzbget_dl.
Jul  7 14:14:14 downloader systemd[1]: mnt-**nfs**-movies.mount: Mount process exited, code=exited status=32
Jul  7 14:14:14 downloader systemd[1]: mnt-**nfs**-movies.mount: Failed with result 'exit-code'.
Jul  7 14:14:14 downloader systemd[1]: Failed to mount /mnt/**nfs**/movies.
[B]
I'm able to resolve this by setting the server to dhcp and statically creating a dhcp reservation on my DHCP server.  I'd really don't like this idea.[/B]

---

### Post by darkod on 2019-07-07
Have you tried using autofs instead of entry in fstab? I do my nfs shares like that on the client side.

---

### Post by juniperms on 2019-07-07
I haven't considered using autofs.  I use nfs-common on three Linux Ubuntu servers with entires in fstab without an issue.  All three of those servers are configured for static IPs.  I'm not sure why this one is different.

---

