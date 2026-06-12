---
title: "How to restrict an FTP user to one directory?"
date: 2012-01-31
forum: Server Platforms
---

### Post by GOSSSAMER on 2012-01-31
HI all,
 
I have an Ubuntu server running vsftpd. 
I want to be able to create a limited user who will soley have access to one or two directories. 
I know by default they have access to their home directory but how can I direct their logon to the only directory I wish them to use?

---

### Post by Sab3r on 2012-01-31
How about creating a soft link to the directory in their home directory? Is that bad practice?

---

### Post by Return Privacy on 2012-07-02
Great question, I'm trying to do the same thing. Can't find an answer anywhere on here?

---

### Post by SlugSlug on 2012-07-02
jail them

quick google..
[https://www.google.co.uk/search?q=ftp+user+jail&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](https://www.google.co.uk/search?q=ftp+user+jail&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

