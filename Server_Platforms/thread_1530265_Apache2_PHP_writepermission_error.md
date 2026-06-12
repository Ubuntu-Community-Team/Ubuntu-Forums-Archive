---
title: "Apache2 PHP write/permission error"
date: 2010-07-13
forum: Server Platforms
---

### Post by PyrexKidd on 2010-07-13
I have a PHP script the generates config files for my FTP server.  The Apache2 daemon and FTP daemon are both running on the same server.

The home directory of Apache2 is /var/www
The home directory of the FTP server is /tftpboot

When I set the directory permissions to 777 the script works great.
This is a huge security hole.

I need the permissions to be 740 (which is what I need it to be)
PHP returns a failed to write invalid stream error.

I have tried all iterations of the permissions and it will only write with permissions set to 777.  I have also tried changing owners and groups of that folder to no avail.

Is there something I am missing?

Thanks in advance.  I have been struggling with this Apache2 server for weeks.

---

### Post by zabuch on 2010-07-13
Where is that config file generated? I assume that in  /tftpboot.
You need to allow your apache user (www-data) to write to  /tftpboot this way or another.
One way of doing this is to set the group of  /tftpboot to www-data and set permission to 770.
Alternatively you can get much more flexibility with FACL (try to google it for examples).

I hope that helps!

---

### Post by cdenley on 2010-07-13
If the user "www-data" does not have write permissions for a directory, apache cannot create or delete files within the directory. If the user "www-data" does not have "x" (access) permissions for a directory and all parent directories, apache cannot access that directory.

---

