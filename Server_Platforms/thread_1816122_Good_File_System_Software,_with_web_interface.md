---
title: "Good File System Software, with web interface?"
date: 2011-08-01
forum: Server Platforms
---

### Post by bryanfblareunion on 2011-08-01
I am in the process of setting up a Ubuntu server in my basement that I want to be able to store files on to access from within my home network. I have used SAMBA before, and it works good, but i would like something with a web interface for downloading/uploading files also. Any suggestions? 

Thanks in advance.

---

### Post by karlson on 2011-08-01
> **bryanfblareunion said:**
> I am in the process of setting up a Ubuntu server in my basement that I want to be able to store files on to access from within my home network. I have used SAMBA before, and it works good, but i would like something with a web interface for downloading/uploading files also. Any suggestions? 

Thanks in advance.

[http://www.coker.com.au/bonnie++/](http://www.coker.com.au/bonnie++/)
You will need to figure out what will you be doing in terms of read/write/delete requirements.  Then evaluate the filesystem you will create for that using bonnie++.

In the systems where read/write are predominant and filesystem is about 70-80% full at the most ReiserFS3 works great.

---

