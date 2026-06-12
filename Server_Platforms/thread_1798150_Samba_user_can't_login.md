---
title: "Samba user can't login"
date: 2011-07-05
forum: Server Platforms
---

### Post by luckyu on 2011-07-05
Hello,

I have a Samba server and it works except other users can't connect to it. The admin account can connect to the share fine but when I add other users they can't connect.

These are the commands I used to make and add users
```

useradd -s /bin/true
smbpasswd -a USER_NAME
smbpasswd -e USER_NAME

```
This is the smb.conf file
```

[other]
        path = /media/HDD1/Videos
        write list = lsjajj
        writeable = yes
        browseable = yes

```

---

### Post by donniezazen on 2011-07-06
I am having trouble with samba too. Is their any easy how to tutorial available out their? All i see is 06-07 blogs/forum post.

Thanks.

---

### Post by luvshines on 2011-07-06
@luckyu

For the other users which are trying to access, do they have read permissions on each of the directory for the shared path starting from /

---

### Post by capscrew on 2011-07-06
> **luvshines said:**
> @luckyu

For the other users which are trying to access, do they have read permissions on each of the directory for the shared path starting from /

In reality what the user needs is the ability to traverse the directories from / to the ultimate end.  This is the ***execute*** bit.  As directories can't be "executed" the bit is used to allow/deny traversal.  The mode 755 allows all users traversal and read rights.

---

### Post by kevinthecomputerguy on 2011-07-06
This guide may help, and they guy that wrote it rocks :- )
[http://woodel.com](http://woodel.com)
 
(you would be most interested in the bottom half of page 3, but i suggest taking a few days, and read pages 1 thru 4 without doing, then doing.
 
-Kev

---

### Post by donniezazen on 2011-07-06
[http://www.webmin.com/samba-howto.html](http://www.webmin.com/samba-howto.html) 

This was way too useful.

---

### Post by luckyu on 2011-07-06
@luvshines Thank You

I worked out perfect, I add that user to my group and chmod a bunch of folders and it worked out. 

Thank You All

---

