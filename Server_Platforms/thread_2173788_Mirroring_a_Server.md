---
title: "Mirroring a Server"
date: 2013-09-11
forum: Server Platforms
---

### Post by athf-president on 2013-09-11
Hello,
 I am wanting to copy my remote server exactly how it exists currently to a local server for backup, and I was just looking for some clarification. I just am looking for an guidance to just make sure I am doing this correctly

My remote server is currently running Ubuntu Server 10.04 LTS. My local machine currently has Ubuntu Server 12.04 LTS. It is my understanding I will need to install 10.04 LTS on my local machine as to avoid any conflicts that could arise

When I do have that accomplished, I believe I will be running rsync as to share files between the 2 servers, from the "/" directory on the remote server to the "/" directory on my local machine

My question is, will I need to install modules such as mysql on the local machine, or will the transfer copy the necessary files?

If anyone has any comments, or a better solution, I would love to hear it

Thank you for your time

---

### Post by sandyd on 2013-09-11
Have you tried backing up the configuration and other files that you need instead of copying the whole root?

If you back them all up correctly, you should simply be able to restore the configuration, and there is no need to mirror the server.

For example:
```

#make dirs
mkdir -p /tmp/backup/root
mkdir /tmp/backup/root/etc
mkdir /tmp/backup/root/etc/apt

#Save packages installed
dpkg --get-selections > /tmp/backup/dpkg_packages

#Save nginx config
cp -R /etc/nginx/ /tmp/backup/root/etc/nginx

#Save installed repos
cp -R /etc/apt/sources.list.d /tmp/backup/root/etc/apt/sources.list.d

```
Restoring is just a matter of
a) Copying sources.list.d back over
b) Re-adding pgp keys from sources and updating package list (apt-get update)
c)
 doing
```
dpkg --set-selections < /path/to/dpkg_packages
apt-get -u dselect-upgrade
```
to reinstall all packages
d) Copying over the config

---

### Post by athf-president on 2013-09-11
Well it's not so much that I need to restore a file(s) as much as I need to create the backup of the server to a local machine. Currently I have no backup of the remote server

I am just unsure of exactly what to do as I made a change on the server a couple weeks ago that broke a small portion of it. I was able to fix it, but seeing as I couldn't restore the file that I broke, I am needing to create a backup to prevent that for future use

---

### Post by athf-president on 2013-09-11
My remote server is configured to accept ssh keys currently, as I have a microcontroller that uses rsync to access a specific directory located on the remote server. I eventually want to create a cron job so that it will back up on a weekly basis, but currently I am just looking to mirror the server exactly as it currently is on a local machine

---

### Post by sandyd on 2013-09-11
> **athf-president said:**
> Well it's not so much that I need to restore a file(s) as much as I need to create the backup of the server to a local machine. Currently I have no backup of the remote server

I am just unsure of exactly what to do as I made a change on the server a couple weeks ago that broke a small portion of it. I was able to fix it, but seeing as I couldn't restore the file that I broke, I am needing to create a backup to prevent that for future use

Exactly - if you use rdiff-backup (the above is just an example), you can send incremental backups of folders that you _need_ to backup to the local server with a cron-job or if you run it before editing things It supports rollback to date, .etc .etc.

Perhaps something like
```

rdiff-backup root@server-ip-address::/etc /home/yourname/etc
```
will make a incremental backup of the /etc directory on the remote server into /home/yourname/etc on your local computer.

To avoid remembering the command, I would add the below to a new line of ~/.bashrc
```

export PATH=$PATH:/root/bin
```
create /root/bin, and you can save it as a bash script that you can call by name before editing any configs. That being said, much of the main configuration is in /etc anyways, though you can easily add additional folders to backup.

Mirroring the entire root downloads a whole lot of stuff you really wont need, including all the binaries that will probably never need editing.

---

### Post by LHammonds on 2013-09-12
Sounds like you are not needing to "mirror" a server like an online fail-over replication but just a full backup.

I configure my servers to backup at various levels.

Once in a while (once a week), I backup all the partitions which can be restored on another server so you can bring the server back online just as it was.

But on a regular basis (hourly), I backup and archive just data files.

I configure my servers using LVM + Snapshots and use fsarchive to backup the partitions (while the servers remains online and operational).

I use rsync to copy data files to a backup folder and then archive the backup folder.

The data file archives and the partition archives are then copied to a remote server.

I have detailed step-by-step documentation on how I accomplish this in my signature links.

LHammonds

---

