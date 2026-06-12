---
title: "FTP users can access enitre disk?"
date: 2010-04-19
forum: Server Platforms
---

### Post by mfcallahan on 2010-04-19
Quick question - I would like to know how to prevent users from accessing directories above the directory used for ftp.  I'm running proftpd and I'm able to connect outside of my LAN, however all user accounts can click "Up to higher level directoy" and access everything, all the way up to the root directory.  How can I make this unaccessable/not visible to users connecting to my server, allowing access only to the directories and subdirectories I have specified?

---

### Post by dudumomo on 2010-04-19
Hi mfcallahan.
In /etc/proftpd/proftpd.conf, there is an option to restrict a user to his home directory or any other folder.
It's called the DefaultRoot.

---

### Post by mfcallahan on 2010-04-19
all works ok, thanks for the help!

---

