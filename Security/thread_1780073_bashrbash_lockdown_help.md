---
title: "bash/rbash lockdown help"
date: 2011-06-11
forum: Security
---

### Post by ItsAsh on 2011-06-11
Hi Guys.

I have recently got my Ubuntu 11.04 Server installed.

I have the following users:

- root (disabled/locked)
- ash (groups: ash, admin)
- testdev (grouns: testdev, dev)

Every user will SSH into the server (for ssh tunelling & sftp). However ONLY the users in "admin" can "sudo".

All I would like to achieve now is...

1. Set the default bash to rbash using the "/etc/skel" directory.
2. Restrict new users to their own directories: **/home/<user>**.
3. Also allow restricted users access to: **/var/www/**.

--

If anyone is feeling generous or could assist me further, I would like to create a bash script called "promote.sh" which:

1. Prompts me for a username.
2. Appends the "admin" group to user; (usermod -aG admin <user>)
3. Removes the "dev" group from the user.
4. Updates the user profile to execute via /usr/bin/bash.

--

I would really appreciate any help i can get here!

Ash

---

