---
title: "Backup Security Best Practices"
date: 2011-12-20
forum: Security
---

### Post by awells527 on 2011-12-20
I have read in the past about intruders breaking into hosting companies, wiping out their production servers, **and then their backups as well** because they left their backups available to their production servers.

I was thinking that they must have poor security practice to leave their backups vulnerable like that, but then I got to wondering...my backups function in the same way.  I have all of my servers backup to a common backup storage location.  In order to be automated, I use SSH key pairs with no passphrase. So...any compromised server would be able to wipe out the backup server with no problem.

So, the question is - what is the best way to secure a backup server from a compromised production server?

My thoughts so far:

*Pull from the backup server instead of pushing from the production server.*  This would protect against a compromised production server, but a compromised backup server puts **all** production servers at risk.

*Set the shell to /bin/false on the backup server's SSH account and disable root login.*  This would prevent someone from running malicious commands, but I could run rsync against an empty directory and would effectively wipe out the backup as well.

I found [this article]("http://library.linode.com/linux-tools/rdiff-backup"), but I don't like it because although the backup server mounts the production server filesystems as read only, there is nothing stopping a malicious user from changing the mount options if the server was compromised.

---

### Post by a2j on 2011-12-21
if we are talking about production environment, should you be backing up your back up server to a tape and keep it off-site?

---

### Post by agillator on 2011-12-21
Permissions, etc., etc. are certainly a step in the right direction. However, your concerns are certainly well founded. The solution, I believe, is really rather simple.  What is not connected cannot be compromised by intruders. What is not on site cannot be destroyed by accident. The question is how much money can/will you spend to solve your problem? In short, have multiple NASs, removable HDs, whatever available. Periodically remove the latest from your machine and replace it with your oldest backup (if it is no longer needed). You can go to the extent as some do of making a third level - the oldest backup is always off site so a fire or some such calamity cannot wipe you out completely. Personally I would not use tape, though. I found it inconvenient to work with when disks were available.

---

### Post by awells527 on 2011-12-22
I forgot to mention the backups are all off-site.  So, in terms of physical disasters these are safe.

So it sounds like there is no way to automate it while being totally secure?

---

### Post by haqking on 2011-12-22
> **awells527 said:**
> I forgot to mention the backups are all off-site.  So, in terms of physical disasters these are safe.

So it sounds like there is no way to automate it while being totally secure?

No such thing as totally secure (well unless it is never used,shared or turned on or connected to a network or given physical access), as for off-site the "safe" only applies if the offsite is not in close geographical proximity, if a natural disaster hits and your backup is 20 miles down the road, it is likely to be still be effected if its a hurricane or earthquake or similar and then you lose both on and off site.

Cheers

---

### Post by Lars Noodén on 2011-12-22
> **awells527 said:**
> I have read in the past about intruders breaking into hosting companies, wiping out their production servers, **and then their backups as well** because they left their backups available to their production servers.

I was thinking that they must have poor security practice to leave their backups vulnerable like that, but then I got to wondering...my backups function in the same way.  I have all of my servers backup to a common backup storage location.  In order to be automated, I use SSH key pairs with no passphrase. So...any compromised server would be able to wipe out the backup server with no problem.

So, the question is - what is the best way to secure a backup server from a compromised production server?

My thoughts so far:

*Pull from the backup server instead of pushing from the production server.*  This would protect against a compromised production server, but a compromised backup server puts **all** production servers at risk.

*Set the shell to /bin/false on the backup server's SSH account and disable root login.*  This would prevent someone from running malicious commands, but I could run rsync against an empty directory and would effectively wipe out the backup as well.

I found [this article]("http://library.linode.com/linux-tools/rdiff-backup"), but I don't like it because although the backup server mounts the production server filesystems as read only, there is nothing stopping a malicious user from changing the mount options if the server was compromised.

You could rotate the storage media to buy time.  Hopefully the problems are discovered and fixed before all the media are overwritten.  There are at least two ways to do that:

Rotate among two or three disks or have a different USB disk for each day of the week.

Or back up to different target directories on different days.

---

### Post by CharlesA on 2011-12-22
> **a2j said:**
> if we are talking about production environment, should you be backing up your back up server to a tape and keep it off-site?

+1 to tape being stored off-site. It's messy and nasty but it works.

> **haqking said:**
> No such thing as totally secure (well unless it is never used,shared or turned on or connected to a network or given physical access), as for off-site the "safe" only applies if the offsite is not in close geographical proximity, if a natural disaster hits and your backup is 20 miles down the road, it is likely to be still be effected if its a hurricane or earthquake or similar and then you lose both on and off site.

This is true too. I thought about storing backups in a safe deposit box at a bank but decided against it since if there was a major disaster, those backups would be wiped out.

Of course, that being said, I do daily and monthly backups and test to make sure they are good before something bad happens. ;)

---

