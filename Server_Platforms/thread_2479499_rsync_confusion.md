---
title: "rsync confusion"
date: 2022-09-26
forum: Server Platforms
---

### Post by aljames2 on 2022-09-26
When I run rsync like this..

```
rsync -rltDvz desk-box:/media/data/ /storage/data/
```

from my backup server, to pull data from a USB connected HDD connected to another machine, it gives permission errors because the destination folder on my backup server has root:root permissions.  I am running the rsync using a non-root user.  I suppose if I chown the folder on my backup server to this non-root user (user:user), which is the user that I do my work from on the backup server, then it would work.  user:user is a non-root user with sudo privileges.  I seem to need a refresher on permissions.

---

### Post by TheFu on 2022-09-26
So, 
to read root owned files that are x00 (400, 600,  700, etc), you have to be root on that system.
to retain the current owner, group, permissions, you have to be root (or root equivalent) on both systems.

I didn't look up your rsync options.  I use these when I want to perfectly mirror everything from 1 system directory tree to another.
```
$ sudo rsync -avz root@desk-box:/media/data/ /storage/data/
```
I'd have to lookup if this will translate the uid/gid to the correct local usernames and groupnames or not, since those usually don't exist on my target system.

I actually wouldn't use the 'root' account to pull the data. I have root-equivalent accounts used for backups on most systems which have root ssh credentials exchanged from the client system into the remote box root-equivalent ~/.ssh/ keys.

If you don't use sudo, then being root on the other system won't help retain files with correct owner, group, permissions, acls on the local storage.  Some times, that's fine, like when the source and target are wholly owned by the same human user. For for system files or for getting files with multiple human users, then the root/root-equiv is mandatory.

Also, if the target storage isn't a Unix file system, all bets are off. Don't even consider using NTFS or FAT-whatever. Those are useless.
Also, ensure that real mounts are used, not that funky gfvs crap.

I think I've answered most things without really showing any examples. Perhaps not from your standpoint?

---

### Post by aljames2 on 2022-09-27
My rdiff-backup scripts that do system pulls correctly backs up system and user files and retains all permissions.

I use rsync in 2 scenarios.  One is to maintain a second drive which is a duplicate of the first to drive.  In this case, both drives are physically attached to the same machine and a script performs this copy.  This keeps all the permissions the same.  

The second scenario is to pull, mostly static data, off of remote machines.  This is not done by a script, and is done whenever I run a manual rsync.  Not sure, in these cases, that I chose (rsync -rltDvz).  Strange, because those options I picked deliberately leave out the retention of permissions.  Perhaps it was my plan back in the day, for permissions to be ignored and to back up files so they are owned by root only when saved on the back up server.

@TheFu,  your explanation helps a lot!  I understand now that being root or root equivalent is necessary to retain user/group permissions.  My thinking was twisted, thinking that you only use root power when you want to store the files under root ownership only.

Now, I will adjust my rsync options and retry this using my root equivalent user.

---

### Post by SeijiSensei on 2022-09-27
Just run the job as root with sudo as TheFu suggests.

---

### Post by aljames2 on 2022-09-27
My sshd_config file on the remote machine has the following settings.  I think something here may be causing root@desk-box to not connect?
```

PermitRootLogin no
AuthenticationMethods publickey
PubkeyAuthentication yes
PermitEmptyPasswords no
PasswordAuthentication no
ChallengeResponseAuthentication no

```

---

### Post by TheFu on 2022-09-27
ssh -vvvvv ....
is the way to troubleshoot any ssh-based connection issues.

---

### Post by aljames2 on 2022-10-06
Sorting this out for me was a bit of a chore but I think it's right now.  Working at least.

My problem was getting rsync to work as root on both ends when pulling data off a remote desktop...while keeping SSH:  PermitRootLogin no

I first set up a user on the remote desktop.  A single purpose user to allow rsync command only.  An unprivileged user assigned to no-group & no GID.

I used visudo to grant this user rsync privileges only

Set up SSH keys on the backup server and sent the public key to the remote desktop user created above

Then created ~/.ssh/config to simplify the command

```

$ sudo rsync -avz -e "ssh" --rsync-path="sudo rsync" desk-box:/media/data/ /storage/data/

```

---

### Post by TheFu on 2022-10-07
There are lots of ways to solve problems. 

I haven't needed to specify an --ssh or --rsync-path options since around 2002, when ssh became the default for rsync.  But if it works, whatever.  

Perhaps you are doing something really special.  My "pulled" backups are working great and the remote rsync to another place (this is a push) is working using a root-equiv account, not root.

---

