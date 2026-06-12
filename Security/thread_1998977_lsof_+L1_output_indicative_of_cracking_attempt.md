---
title: "lsof +L1 output indicative of cracking attempt?"
date: 2012-06-07
forum: Security
---

### Post by SparTacux on 2012-06-07
I followed one of the security sticky links to [http://danielmiessler.com/study/lsof/](http://danielmiessler.com/study/lsof/) where I came across a tutorial on the use of lsof. In that tutorial was a mention of using lsof +L1 to find files that have a link count less than 1. It said you shouldn't get any results returned - if you do then it's often an indicative of a cracker trying to hide something. 

I ran the command and it produced about 11 lines of data with references to files being deleted. Is this normal or not?

---

### Post by unspawn on 2012-06-08
Some common services may delete files but what is normal or not depends on the process (path and executable, not argv[0]), who is running it and what files are opened slash deleted. (IMO it could have been more efficient if you would just have posted your list of deleted files.) If unsure just cat the file opened on the file descriptor number to a file somewhere else and examine its contents.

---

### Post by SparTacux on 2012-06-08
> **unspawn said:**
> Some common services may delete files but what is normal or not depends on the process (path and executable, not argv[0]), who is running it and what files are opened slash deleted. (IMO it could have been more efficient if you would just have posted your list of deleted files.) If unsure just cat the file opened on the file descriptor number to a file somewhere else and examine its contents.

I tried this on a live cd and got similar results except I couldn't reproduce the seamonkey output due to using Firefox on the live CD. 


COMMAND    PID    USER   FD   TYPE DEVICE SIZE/OFF NLINK    NODE NAME
nautilus  3487 browser   31r   REG    8,1       56     0 3803739 /home/browser/.local/share/gvfs-metadata/home (deleted)
nautilus  3487 browser   32r   REG    8,1    32768     0 3803761 /home/browser/.local/share/gvfs-metadata/home-5b304ed2.log (deleted)
seamonkey 3678 browser   50u   REG    8,1     1544     0 2235503 /var/tmp/etilqs_fbA6dKaQRNff5yU (deleted)
seamonkey 3678 browser   51u   REG    8,1     1024     0 2235533 /var/tmp/etilqs_P5Bv5jgccSA236o (deleted)
gnome-ter 3762 browser   23u   REG    8,1     1242     0 1835098 /tmp/vteX5Y3FW (deleted)
gnome-ter 3762 browser   24u   REG    8,1      264     0 1835099 /tmp/vteH793FW (deleted)

---

