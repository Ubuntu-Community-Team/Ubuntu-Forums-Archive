---
title: "Quanta Plus : Spits the dummy when creating project files on NFS share"
date: 2007-01-28
forum: Server Platforms
---

### Post by Littleweseth on 2007-01-28
Hi;

I've decided that NFS is The Way Forwards for uploading files to my webserver. (FTP is a flaming mess, quanta wants my password every ten seconds, etc.) However, Quanta seems to be having some o' those ole permissions problems with NFS, too.

I have the following line in etc/exports of the remote computer (pellinore, 192.168.0.1);
```
/var/www/       192.168.0.2(rw)
```

And this line in my /etc/fstab
```
192.168.0.1:/var/www    /mnt/pellinore-www      nfs     soft,nosuid     0      0
```

Ownership of the nfs share;
```
lws@daedalus:~$ ls -l /mnt
drwxrwxrwx 12 www-data www-data 4096 2007-01-28 16:03 pellinore-www
```

My normal-user self, lws, belongs to the group www-data on both to local and remote computers.

I can touch files into existence, rm, mv, and all of the usual stuff when using a terminal. WHen using quanta, I can save html files and so forth with no difficulty. However, quanta's project management features seem to be having some issues. When I define a new project  using file protocol 'local' in /mnt/pellinore-www/orr/, i get the helpful dialogs;

Cannot open file /mnt/pellinore-www/orr/z.webprj for writing

followed by

Saving of project failed. Do you want to continue with closing (might cause data loss)?

This is very strange. Quanta is actually running as me (so it has all the right permissions), and in theory a mounted nfs share is indistinguishable from a mounted drive of any other kind.

Suggestions, or might this actually be a bug?

---

### Post by Littleweseth on 2007-01-28
Funnily enough, telling Quanta to create the project files in the webroot (/mnt/pellinore-www/ instead of /mnt/pellinore-www/orr/) fixed the issue. Quanta appears to be buggy in this regard - it's done the same thing with FTP as well.

---

