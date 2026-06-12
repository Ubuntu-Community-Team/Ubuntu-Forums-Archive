---
title: "rdiff-backup remote permission issues"
date: 2020-06-06
forum: Server Platforms
---

### Post by aljames2 on 2020-06-06
I am running this command to pull remote Desktop data to my backup storage.  I got 49 errors, all permission errors accessing certain places at source including /root, and certain places under /etc.

```
rdiff-backup --remote-schema "ssh -C %s -p 34629 rdiff-backup --server" -v5 --print-statistics --exclude-special-files --include /etc --include /root --include /home --exclude '**' user@192.168.101.7::/ /backups/desktop
```

This "user" is the same primary user account on the desktop machine.

Is it best to set up a separate rdiff-backup user and if so how do I set it up so it has permissions it needs when running, considering my SSH configuration currently does not allow root-login?

EDIT:  I add that most data did back up with this method except data in the restricted locations did not with permission errors.

---

### Post by TheFu on 2020-06-07
System level backups must run as root (or root-equiv) on both sides.  /etc/ has some files that only root can access, for very good reasons. It is server crypto stuff that shouldn't be public.

Create a ~/.ssh/config file to simplify stuff.

```
host backup-client-7
  user root-equiv
  hostname 192.168.101.7
  port  34629
```

You can have as many of those stanzas as you like. Only the "host" must be unique. Tab completion for ssh/scp/sftp/rsync/rdiff-backup/sshfs/x2go ... all read this file and will fill in the host parts. It is a nice way to document where you have logins, userids, IPs, strange ports, but never actually need to know those details again. Especially great to have a host-alias for ugly VPS server names.
**ssh amz-www** is much easier to remember than **ssh xxx-yyy-zzz-sss-west-amz.amazon.com**

**ssh backup-client-7** and rdiff-backup will use the user and port to the IP. No need to have a complex rdiff-backup command or --server. The defaults work.  Of course, the **sshd_config** file on 192.168.101.7 needs to be modified to only allow access for that specific userid from the backup server and nowhere else.  Use the *Match User* and *Match Address* methods.

The ~root-equiv/.ssh/authorized_keys needs to limit the access to rdiff-backup.  Look at how github has their git (via ssh) access working. That shows how to allow 1 specific command to be run from a remote system safely as 1 specific userid (root or root-equiv).

Hopefully, that's enough.

---

### Post by LHammonds on 2020-06-07
Or have a script run (from root's crontab) on each local machine that which will collect the files you need into an archive ready for the backup server to collect.  Let's say that script dumps the archive to /bak/remote/yyyy-mm-dd-backup.tar.gz).  Then have your backup server collect any files sitting in the /bak/remote folder.  Your locally-run script runs in the root user space and as such, will not have permission issues access root-level files.  The same script will also have absolute control over the owner/file permission of the archive so that your backup server will be able to collect the archive.

Its a matter of where you want your backup logic to exist.  Each of my servers do different things and as such, will have different backup requirements.  As part of my setup process for the server, the individual logic to backup that server will be contained inside the local backup script.  The backup server only needs to be concerned with accessing each remote machine and collecting the archives that have already been prepared for backup...in a common location among all remote machines.

LHammonds

---

### Post by TheFu on 2020-06-07
Lots of different backup methods exist.   
There is a tipping point where the amount of data being backed up makes using a tgz solution impractical.  
There are also times when the tgz method is necessary.

---

### Post by aljames2 on 2020-07-07
Sorry for late reply.  I've been painting our house & getting it ready to sell/move.  Thanks for this help here..

I got remote rdiff-backup working without any "premission denied" issues and without allowing root login.  This was my process in case it's useful for others & in case I can make it better :D :

1) Made sure rdiff-backup was installed on both backup server & client/host & verified versions were the same:   rdiff-backup --version

2) Create an unpriviledged backup user "rdiff-bak" on client to be backed up.

3) On backup server created SSH keys at root@server
```
ssh-keygen -t ed25519
```
4) Copy the SSH .pub key to the remote client using
```
ssh-copy-id -i ~/.ssh/id_ed25519.pub rdiff-bak@192.168.101.7 -p 34629
```
5) Verified permissions at /home/rdiff-bak/.ssh/authorized_keys  (/.ssh = 700), (authorized_keys = 600)

6) Verified sshd_config entries on remote client:
```
Port 34629
AllowUsers otheruser rdiff-bak
PermitRootLogin no
ChallengeResponseAuthentication no
PasswordAuthentication no
AuthenticationMethods publickey
PubkeyAuthentication yes
PermitEmptyPasswords no
```
7) restarted sshd service:  sudo systemctl restart sshd.service

8) Tested SSH connection (good)

9) Provided more access for the rdiff-bak user by giving limited sudo priviledges by adding this at:  root@server:# visudo
```
rdiff-bak ALL = NOPASSWD: /usr/bin/rdiff-backup --server --restrict-read-only /
```

10) On backup server, added host information to ~/.ssh/config    to simplify the SSH command  (as shared earlier)

11) Used --remote-schema to get rdiff-backup to use sudo & tested a trial backup of /etc.  Perhaps I don't understand this part very much, but it worked.  I had read this may be necessary in order to use sudo at the remote host?
```
rdiff-backup --remote-schema 'ssh -C %s "sudo /usr/bin/rdiff-backup --server --restrict-read-only /"' -v5 --exclude-special-files --include /etc --exclude '**' backup-client-251::/ /backups/Desktops/temp/
```

12) Created a backup script to run the desired rdiff-backup.

13) Automated it with Cron

---

### Post by TheFu on 2020-07-08
Don't think the file ownership, groups, permissions, ACLs will be retained without root saving the data locally.  Have you checked that?

---

### Post by aljames2 on 2020-07-08
I did a side by side comparison (ls -al) of source & destination and they appear the same.  root:root and the permissions look the same.  Now this was done on /etc.  I should test this on the /Home user next to see if these are preserved, or if it saves as root:root.  Didn’t check that yet...

---

### Post by aljames2 on 2020-07-08
After testing a /home directory rdiff-backup, I saw that the file permissions were the same.  However, the user:group names on the backup server was not the same as the source user:group.

The reason the user:group for the data changed on the backup server is because the source UID:GID is 1000:1000, and since I already have a 1000:1000 user on my backup server already, the process gave the backup files the same UID & GID that already exists on my backup server.  However it does appear rdiff-backup did preserve the user & group IDs for the data.

---

### Post by TheFu on 2020-07-08
I&#8217;d be less concerned about end-user files than daemon account files. Anything in a HOME should be owned by the userid owning that HOME.  5 userids would take 15 seconds to fix post-restore.  What about the deep files under /etc with odd owners and groups?

The only reason i brought this up was because it appeared the backup server rdiff-backup process wasn't running as root. if that isn't true, sorry to have wasted your time.

---

