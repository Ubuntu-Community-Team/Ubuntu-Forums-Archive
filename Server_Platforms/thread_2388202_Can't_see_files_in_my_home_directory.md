---
title: "Can't see files in my home directory"
date: 2018-03-30
forum: Server Platforms
---

### Post by jay116 on 2018-03-30
I'm sure the answer to this is simple but I'm hoping someone can explain. I have a couple scripts that are in my home directory on my server that I run to rsync some drives. Lately I've logged in and there are no files in my home directory. I can run a find and/or locate and it finds the files but I cannot see them in their directory (/home/user) "ls -la". I I've seen this before but I  thought it was a multiple SSH login issue. The home folder is encrypted. Last night I wanted to run a backup and I logged in once directly on the server then logged out. I then sat down at my main PC and opened an SSH with  the server as I only use the CLI and my home directory was empty. I rebooted with no change. I came home from work opened a shell and there they were. 

Any ideas?

---

### Post by wildmanne39 on 2018-03-30
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by darkod on 2018-03-30
Make sure the encryption/decryption and mounting works correctly. I assume it does otherwise if your home folder is not mounted it would not allow you to login at all... But better to check it out.

You can also try the backup destination to be outside of any home folder. I can't say that is the problem but in general I wouldn't use home folders for backups.

Also start checking out ownership and permissions of the folders created by the rsync. It might give you some info.

---

### Post by jay116 on 2018-03-31
Thanks for the advice. I'm logged in now and can see my home folder contents. I dont story anything there, just my scripts. They all point to external backup locations using rsync. I feel like there is some issue with me logging into the server directly then moving to another computer and logging in via putty.

---

### Post by darkod on 2018-03-31
Oh, I understood that rsync is syncing to inside your home folder.

So, when you say you can't see the files, you mean the scripts and other home files? But the rsync is working correctly and the backup copy is on the external destination without errors?

This is a strange issue. Which files you see should not matter whether you log in locally or over ssh.

Have you tried checking the volume status with cryptsetup when you are logged in locally and over ssh, to see if it displays any difference?

---

### Post by jay116 on 2018-04-03
it hasn't been a problem in the last few days. Maybe its an issue with running a script form my home directory then logging in again via SSH. I haven't figured out what situation is causing it. Thanks for all your input.

---

