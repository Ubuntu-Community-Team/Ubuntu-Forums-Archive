---
title: "Need to copy files into MySQL Directory"
date: 2009-02-13
forum: Server Platforms
---

### Post by mistypotato on 2009-02-13
I need to restore some backed up MySQL data back into a MySQL folder but I may have to change folder & file permissions to do that.

My fear is that I won't be able to get the permission reset properly after I'm done and then MySQL will have problems.

Is thee a "Safe" way to backup the existing files then copy the previous backup into that directory (folder)

---

### Post by conjur3r on 2009-02-13
If you are working on that file level then you should be safe with changing ownership of all files and folders in the mysql storage (normally /var/lib/mysql) to the mysql user, eg:

# sudo chown -R mysql:mysql /var/lib/mysql

The issue with the above backup approach is that there may be compatibility issues importing to another version of mysql.  My personal preference is to export all databases to a SQL file.  You can then use it to import into the other servers if needed.  If interested, look at the mysqldump tool.

---

### Post by mistypotato on 2009-02-13
Good Point.

thx

I'm new at this and I know that setting the permissions wrong can really cause problems.

---

