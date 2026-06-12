---
title: "simple mtime issue"
date: 2012-07-02
forum: Server Platforms
---

### Post by lolium on 2012-07-02
hey guys, having a weird issue using mtime with find

```
find . -name '*.*' -mtime -14 -exec ls -l {} \;
```

wanting to get everything thats 15 days old and less to current date, ive used this before and it works but im not sure if im just doing something wrong this time.

below is sample output
$ find . -name '*.*' -mtime -14 -exec ls -l {} \;
-rw-r--r-- 1 2001 sites  168106 2009-08-13 10:03 128847_1.jpg
-rw-r--r-- 1 2001 sites  181097 2009-08-13 10:03 128847_2.jpg
-rw-r--r-- 1 2001 sites  131183 2009-08-13 10:03 128847_3.jpg
-rw-r--r-- 1 2001 sites  188893 2009-08-13 10:03 128847_4.jpg
-rw-r--r-- 1 2001 sites  177707 2009-08-13 10:03 128848_1.jpg

Can anyone see what mistake im making as i dont want anything over 14 days old?

Regards

Sam

---

### Post by papibe on 2012-07-02
Hi lolium.

'find' by defualt searches for all entries: files and directories. It looks like some directories are being found, and the 'ls' is printing the whole directory.

Try restricting the search just for files:
```
find .  **[COLOR="Red"]-type f[/COLOR]**  -name '*.*' -mtime -14 -exec ls -l {} \;
```
Hope it helps, and tell us how it goes.
Regards.

---

### Post by hawkmage on 2012-07-02
That command should work.  What do you get if you use stat on one of those files instead of ls?  Stat will diplsy all of the time stamps on the file.

Also is this on ext3/ext4 formatted that is local or mounted via NFS?

---

### Post by lolium on 2012-07-02
That's perfect thank you! I just assumed that with the directory only containing files it wouldn't be an issue, guess i shouldn't have just assumed. 

Thank you

thank you for the reply hawk but papibe resolved my issue

---

### Post by papibe on 2012-07-02
:D Great!

Please mark the thread solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")), when you have the chance.

Regards.

---

