---
title: "owner/user issue"
date: 2008-05-17
forum: Security
---

### Post by wcorey on 2008-05-17
Hi, I have a perplexing issue. I have a thunderbird profile on a NAS unit mounted as NFS. It shows the user/group as 1000 1000.  Since I reinstalled Linux my userid is 500 and I can not open the file with thunderbird. I tried going in as root to change the ownership of those files and directories but received permission denied. How do I change ownership of that directory tree?

Thanks,

Walt

---

### Post by HalPomeranz on 2008-05-17
You can't do operations as root on a file system that's mounted from a remote NFS server (unless the server admin explicitly allows you to do so), so your chown won't work.  If you have admin privileges on the file server, you can do the chown there.

However, it's probably easier for you to change your user/group on your Ubuntu system.  "sudo vi /etc/passwd" and change the third field of your password entry from 500 to 1000.  Then cd to your home directory and do "sudo chown -R 1000 ." to reset the ownerships on the files in your homedir (this is a dangerous operation, so make sure you're in the correct directory when you execute the chown command).  Then you'll need to log out and log back in again.

---

