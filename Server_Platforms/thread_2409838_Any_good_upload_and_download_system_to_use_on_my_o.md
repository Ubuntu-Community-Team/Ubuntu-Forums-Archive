---
title: "Any good upload and download system to use on my own server?"
date: 2019-01-07
forum: Server Platforms
---

### Post by cazz on 2019-01-07
Hi
Was not so easy to write a title but I looking to create a system that I can myself upload files and my customers can download and when is download it delete from the server.
I know it is alot of free site that provide that kind of service but I like to have my own.
I working with alot of big files and not so easy when some mail host only can attached 10 Mb or somtime 20 Mb files.

Right now I use nextcloud but then I have to create a account and remember to delete the file and the account.

---

### Post by TheFu on 2019-01-07
Whenever I provide a file for a client, I tell them the file will be deleted in 7 days and use 'at' to schedule that deletion immediately at the time I send the notification.  Then I never think about it again.

```
$ echo "rm file"| at now + 7 days
```  In 20 yrs, only once did a client not get the file in time.

---

### Post by 1clue on 2019-01-07
@TheFu, that's a really good idea.

In 20 years, never once did I think of that.  :)

@cazz, I use sftp for any type of file storage with Internet access. If the system is not an isolated cloud server, I require them to also log into the VPN as I don't want an exposed ssh server on the net. For some reason that drives the script kiddies crazy and you'll get continual brute force attacks.

If you don't know what sftp is, it's an ftp-like command set built into openssh. It uses ssh protocol. When you have a normal openssh server, you can either use scp or sftp to transfer files. You can make a small change to your openssh server to limit some users so that they can only use sftp commands, and so that they can only reach their $HOME directory.

---

### Post by TheFu on 2019-01-08
I use multiple file access methods from the internet too.
Basically, access to internal web services is limited by the need to have either a full VPN or ssh-proxy setup.

* Nextcloud, but it requires a full VPN connection or ssh-tunnel-proxy
* Plex, but it requires a full VPN connection or ssh-tunnel-proxy; I don´t have a plex account.
* Calibre, but it requires a full VPN connection or ssh-tunnel-proxy
* sftp - useful for almost any Linux file manager (scp included)
* sshfs - convenient for scripting
* rsync - replication of backups
* NFS - only on the LAN and only via our storage network, not the public interfaces.

External web-services don´t need authentication and sit on a different subnet with firewalls.  If I were setting everything up again, I´d put these on a VPS hosted somewhere else to reduce the liability of network incursions.

All ssh connected services reject passwords for authentication from public networks and root remote access is only possible from the LAN backup server IP and only allowed to run backup-related commands.  We ¨pull¨ backups, never ¨push¨ and there´s no shared storage for the backups. Only the backup server can access that storage.

Because I´m paranoid about trusting php web-app security (we don´t trust it), most nextcloud file storage is provided via a read-only NFS mounts. Each user has a place where they can upload and download *_their_* personal stuff. We are small and nobody has abused the storage at this point, but quotas are possible, I think. But they still have to use a VPN or ssh-proxy for network access first.

I tested 2FA for nextcloud using U2F devices (yubikeys) a few months ago. It is really easy to setup, but only worked for desktops. Phones and tablets had to use the pre-printed, manually entered, codes.  That´s too bad. Our people use their phones to look things up about 40% of the time.

We also provided remote desktop access into our LAN for all our people using x2go.  I just checked the logs and I´m the only one using it still.

Probably more info than anyone wants to know. It is an imperfect world and there certainly are things I can do better to help our people. Priorities.

---

