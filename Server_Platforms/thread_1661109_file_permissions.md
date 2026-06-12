---
title: "file permissions"
date: 2011-01-06
forum: Server Platforms
---

### Post by idny on 2011-01-06
Hi,
A simple question that i've been trying to find the answer to..

I have ubuntun server 10 running samba share. There is currently one folder that has a chmod 777 set with nobody nobody set for the owner and group. This means anyways can read, write and execute in this directory.

I want to allow users to write to this directory, but NOT remove.
Is this possible

Thanks :)

---

### Post by sisco311 on 2011-01-06
If the sticky bit is set on the directory, only the owner of a file or the owner of the directory (and root of course) will be able to delete that file.

See: [http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

