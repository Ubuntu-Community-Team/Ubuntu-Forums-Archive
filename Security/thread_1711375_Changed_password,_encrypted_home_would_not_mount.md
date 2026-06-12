---
title: "Changed password, encrypted home would not mount"
date: 2011-03-21
forum: Security
---

### Post by egandt on 2011-03-21
I just lost everything in my encrypted home directory after a password change and reboot, when it would no longer mount. I was forced to restore the entire directory from a backup (losing about a months changes in the process).

As far as I can tell searching for solutions there is no easy solution that works for everyone in this situation, and running short on time and needing a viable install a restore was all I could do.

Now I need to regain the lost files, how do I do this?, Why did this failure occur?

Thanks,
ERIC

---

### Post by BkkBonanza on 2011-03-21
At the cmd line the password for login and encrypted home are changed separately. On the desktop menu when you change password it will update the ecnrypted home as well, so that is the better way to change it.

From what I've read (and not tried) if you change the login password at the cmd line you have to manually update the ecryptfs password after to sync them. The following command will re-wrap the passphrase with your new password,

ecryptfs-rewrap-passphrase /home/.ecryptfs/$USER/.ecryptfs/wrapped-passphrase

For gui method see,
[http://bodhizazen.net/Tutorials/Ecryptfs/#Password](http://bodhizazen.net/Tutorials/Ecryptfs/#Password)

---

### Post by ThomasMcA on 2011-04-05
Change your password back to what it was before the problem, then restore from your most recent backup. Your "lost" data will still be there. Then find a way to update both the system password and the encryption password. The GUI change password tool is supposed to do both, but that didn't work for me with KDE and Kubuntu 10.10 - I had to change my password back using passwd, then I could log back into KDE.

---

