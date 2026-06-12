---
title: "Another VSFTPD problem"
date: 2009-06-08
forum: Server Platforms
---

### Post by Jumpmasterrt on 2009-06-08
Ok, so I finally get the FTP server up and running but there are two issues.

1. When I connect (locally or via internet), it shows me my whole home folder. What I want is JUST the web server folder.

2. Even though it lets me into the server, I only have read access.
I looked all through the vsftpd.conf and can't seem to find any thing where that's set.

So, how do I change the folder and get write access?

**Update**
Ok so somehow I missed the line.```
#write_enable=YES
``` I uncommented that and now I have write access....
So how do I limit it to just the webroot folder.... for any/everyone all at once?
  ~Ok, limiting access with local_root=foldername is ok, but I can still see the other directories

---

### Post by Jumpmasterrt on 2009-06-10
Ok, well now I've got an interesting dilemma. I've connected to the FTP with both the DNS and IP from IE and Firefox and ONLY the folder I want shown is available. So that works.... unless I'm using FireFTP. FireFTP is showing the whole home folder but due to the restrictions in VSFTPD.conf will only let me in to the web folder. 

Soooooo long story short, it works but is kind of funny.

---

