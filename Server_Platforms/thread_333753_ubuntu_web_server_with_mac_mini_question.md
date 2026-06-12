---
title: "ubuntu web server with mac mini question"
date: 2007-01-07
forum: Server Platforms
---

### Post by zany on 2007-01-07
i have a web server running Ubuntu 6.10.  When configuring the webserver (apache, etc) i want to host the website files on my mac mini G4 running MacOS X.  How do I point to the mac mini in the config file when i want to server to retreive the web files from the mac mini?

any ideas, books, documents, please let me know.  Thanks!

---

### Post by simonn on 2007-01-07
Why not host the whole thing on the mac mini?

To answer your question though, you will need to use some kind of network file system. 

Samba, a.k.a windows file sharing, is probably the easiest to set up. Alternatively you could use NFS (Network File System).

---

### Post by zany on 2007-01-08
yeah, hosting it all on mac mini wouldn't be a bad idea.  you mean basically installing ppc linux on the mac then?

---

### Post by simonn on 2007-01-08
> **zany said:**
> yeah, hosting it all on mac mini wouldn't be a bad idea.  you mean basically installing ppc linux on the mac then?

Nope. 

I am pretty sure OSX has built in web serving, so use that (sorry can't check at the mo as I am at work and my mac is at home). If this is not the case, I am sure you can install apache on OSX (google it).

---

