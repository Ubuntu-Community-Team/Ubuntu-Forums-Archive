---
title: "Disallow login before mounts"
date: 2012-01-05
forum: Server Platforms
---

### Post by Sun_Blood on 2012-01-05
Hi

I got an NAS with some encrypted mount points on. These will not mount automatically during a reboot(for example power loss) because they need a password to be entered before decrypting.
This is what I want, I don't want automatic decrypting :)

The problem I have is that I have a backup point mounted to /srv/backup and to this I have some automatic rsync script pushing backups with ssh.

Now if the server unexpected restarts the mount point /srv/backup will be empty so rsync will performe a full backup and fill up the wrong disk. 
So is there a way for me to disallow users to login if the mountpoint is not mounted?

---

### Post by Wayne_V on 2012-01-05
why not add a check (or wrapper) to your backup script to check that /srv/backup is mounted before kicking off rsync?

---

### Post by Sun_Blood on 2012-01-05
I want to keep the solution server side instead of client side.

I'm thinking about an ssh bash script. How about a script that is run on userlogin that check if the mount is present. If not disconnect the user?

Problem is that my bash scripting skills is zero.

---

