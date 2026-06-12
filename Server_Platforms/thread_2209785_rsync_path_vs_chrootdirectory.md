---
title: "rsync path vs chrootdirectory"
date: 2014-03-07
forum: Server Platforms
---

### Post by lowrider2025 on 2014-03-07
Hi,

I am struggling a bit with specifying the right path when pulling some files from a remote server.
Scenario:
Ubuntu 10.04
_OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k (25 Mar 2009)_

remote server
/etc/ssh/sshd_config
Match User backup
   ChrootDirectory /backups (what I want it to be, now using: /)

rsync command on local server in script:
#!/bin/sh
rsync -e "ssh -p 2222" [email]backup@ipaddress:/backups/*.gz[/email] /backup (this works with / as ChrootDirectory)

What confuses me, is this:
what do I need to specify as path or filename to get to my files.

remote server:
backup user has home directory /backups
backup user is(I want it to be) chrooted to /backups

When the local backup user connects to the remote server, am I wrong in assuming that the directory when connecting to the remote server is /backups ? So the following would work: rsync -e "ssh -p 2222" [email]backup@ipaddress:*.gz[/email] /backup

Or is the ChrootDirectory always relative to user's home directory ? 
So if home directory is /backups and chrootdirectory is / then resulting directory would be: /backups
and if ChrootDirectory is /backups then resulting directory would be: /backups/backups

Thank you to who makes this clear to me

---

### Post by nerdtron on 2014-03-07
Always use the complete path when you copy or copying to in using rsync. That means you need to specify the home folder (or specific folder) for the user you created.
For example I have the user nerdtron at IP address 192.168.1.1, when I try to pull files which are located in my home directory, I still need to specify the whole path like:
rsync -e "ssh 222" [email]nerdtron@192.168.1.1:/home/nerdtron/*.gz[/email] /backup

I think rsync doesn't automatically treat a user@IP combination as a remote location unless you specify a path on it.

---

### Post by lowrider2025 on 2014-03-07
@nerdtron thx for the reply
When I use ChrootDirectory /backups and specify it in command: rsync -e "ssh -p 2222" backup@ipaddress:/backups/*.gz /backup , I get following error:
/bin/sh: No such file or directory.
rsync: connection unexpectedly closed

Could this have something to do with the fact /bin/sh not being available in the chrooted environment, like in the example here: [http://positon.org/sftp-chroot-rsync]("http://positon.org/sftp-chroot-rsync")

*edit: tested this with changing the shell for backup user in /etc/passwd and the error message changes accordingly. Will try the solution like in the url I mentioned and report back after the weekend.*

---

### Post by lukeiamyourfather on 2014-03-07
Are you running rsync as a daemon on the remote machine? See the manual for info on configuring rsync as a daemon if you haven't already, there's info on using chroot.

```
man rsyncd.conf
```

---

### Post by lowrider2025 on 2014-03-11
it worked by copying the necessary files for rsync and the user shell with the ldd command.\\:D/

---

