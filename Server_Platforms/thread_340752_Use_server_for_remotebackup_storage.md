---
title: "Use server for remote/backup storage"
date: 2007-01-17
forum: Server Platforms
---

### Post by malder on 2007-01-17
I've searched on this for a while and have not been able to find anything that is very useful.

I have an Ubuntu Dapper LAMP server (which works great BTW). I'd like to use it for remote storage/backup as well, but I don't want to just use FTP or SSH to manually move files.

Here is how I see what I want to work:

create a user/home directory on server

Map a network drive on my XP PC that goes over the net to the afore mentioned folder.

then I'll have a place for my files that I can get to from anywhere. I can make off-site backups of local documents in one easy step. I can also give other people who need access to said files. etc.....

I found a program called sftpdrive ([http://www.sftpdrive.com/](http://www.sftpdrive.com/)) that appears to use SSH in conjunction with xp's drive mapping. It looks like it does what I want, but I'd prefer to stick with OSS if possible for obvious reasons.

I'm nearly certain there has to be an easy way to do this, but I've just not run across it yet.

Any suggestions?

Thanks

Matt

---

### Post by thornomad on 2007-01-17
Are you connecting to your LAMP server on your local network via SAMBA currently ?

I am not a WinXP user, but with Ubuntu I am able to remotely mount a folder on my desktop through SSH that is secure and acts in the ways that, I believe, you describe.  Once it is mounted, I just open it like a regular folder and the files on my server are accessible.

I would suggest using SSH because you can create a secure/encrypted connection; find a program that works in windows and allows you to mount an SSH connection as a folder ... not sure what would do that ... Ubuntu does it pretty easily using software called FUSE.  I wrote up a "remember how" document if want to look at it:

[http://www.damontimm.com/blog/how-to-mount-a-sftp-folder-ssh-ftp-on-ubuntu-linux-using-sshfs-fuse/](http://www.damontimm.com/blog/how-to-mount-a-sftp-folder-ssh-ftp-on-ubuntu-linux-using-sshfs-fuse/)

D

---

### Post by jtc on 2007-01-18
When it comes to the backups you could always use an automatic solution based on [cwRsync]("http://itefix.no/cwrsync/") (rsync, packeted with a minimal cygwin). Take a look at this [tutorial]("http://www.rsync.net/resources/howto/windows_rsync.html") to get the basic idea how to set things up.

When it comes to mapping a remote SFTP as a local drive in Windows I'm not sure if there really are any OSS-options. I have been looking myself for a while now. SftpDrive looks nice thought.

---

