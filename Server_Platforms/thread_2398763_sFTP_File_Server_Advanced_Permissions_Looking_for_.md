---
title: "sFTP File Server Advanced Permissions Looking for Advice"
date: 2018-08-16
forum: Server Platforms
---

### Post by ecaep2 on 2018-08-16
I've setup an Ubuntu 16.04.5 LTS server on the internet for my organization's use when sharing large files.  The only access to the server is ssh or sftp.

I've created chrooted directories based on group names for the departments that need to share files.  Each group has it's own directory, which acts as it's root directory under which they can create as many directories as needed to organize their files.  The configuration for this is in my /etc/ssh/sshd_config file, and the groups are working properly.  All permissions for the directories are handled by Linux standard permissions.  The pertinent part of my sshd config is:

Match Group sftp
         ChrootDirectory /sftp/Sales
         PermitTunnel no
         AllowAgentForwarding no
         AllowTCPForwarding no
         X11Forwarding no
         ForceCommand internal-sftp

This config is repeated for each chroot group.

My difficulty is trying to make the Linux permissions fit so that I can have some users in the same group that have read/write access and other users that have read-only access.  For example:

I have a groups called Sales.  I need 3 users in the Sales group to be able to both read and write in the Sales chroot directory tree.  I need 2 others members of Sales who have read permissions only.  Since all 5 users are members the Sales group in order to match the user to the Sales chroot directory, how do I specify per-user permissions?  I also want the read only users to be able to upload files in a special folder in the directory tree labeled dropbox.

Can this be accomplished using the sshd config and standard Linux permissions?

Thank you

---

### Post by TheFu on 2018-08-17
Welcome to the forums.

I haven't done this specific thing recently, but I think it will work ....

You can't with normal ugo permissions. You can add ACLs for the read-only users, however. In 25 yrs as a Unix admin, I've needed ACLs 2 times. I avoid using ACLs, because they can be disabled and are commonly forgotten, since there isn't any visual clue in Debian/Ubuntu that they are being used. CentOS/RHEL do provide a visual clue.

Or you can setup separate groups - rw_group and ro_group, doubling the number of Unix groups necessary, if you want to avoid ACLs.  The ro_group members would be "other" as far as Unix permissions are concerned.  2775 permissions for owner, rw_group, other.
I'd probably just move uploaded files from the ro_group upload directory to the rw_group upload directory every hour with a script.

Clear?

---

### Post by ecaep2 on 2018-08-17
Thank you TheFu!

I wasn't aware of the option in Linux for additional permissions that ACLs provide.  I can see why they should normally be avoided, but I think they will work perfectly for this situation, since the users aren't managing any permissions.  I'm reading about them now.

I really appreciate your advice!

---

### Post by TheFu on 2018-08-17
> **ecaep2 said:**
> Thank you TheFu!

I wasn't aware of the option in Linux for additional permissions that ACLs provide.  I can see why they should normally be avoided, but I think they will work perfectly for this situation, since the users aren't managing any permissions.  I'm reading about them now.

I really appreciate your advice!

I don't know how to automatically apply ACLs onto new files like the setgid bit does for normal groups. That's one of the bad parts.  So you'd need a script to apply ACLs every few minutes and hope that none of the read-only users learns this and takes advantage.   Using separate groups would be more secure, IMHO.

There are probably some other gotchas.

---

### Post by volkswagner on 2018-08-18
For setting ACLs on newly created files, you'll set "default acls" on parent directory.

---

