---
title: "Proper owner/permissions structure on /var/www for apache serv-/upload-/moving files"
date: 2008-01-27
forum: Server Platforms
---

### Post by isync on 2008-01-27
Could someone please give me a final note on how to setup a secure and proven permissions and owner structure for the /var/www directory tree?
According to [this thread]("http://ubuntuforums.org/showthread.php?t=146223") www-data of my apache2 should be an isolated user, member of no groups with only read access to the filepath.

But what when I let users upload files?? They are created with www-data:www-data so apache has no permission to create them in a read-only dir structure....
Should I make the www-data user part of a group with permission to write to /var/www and then chown the /var/www path to be writable by group??

Or even further make /var/www/uploaddir world writable so also www-data can write to it (in this case I don't have to make this user part of any group)

So:
www-data member of a write-allowed group or should I loosen write-restrictions on /var/www?
Or should I change the umask in /etc/profile for newly created files??

Update:
For example, hoster 1and1, uses myusername:ftpusers for all uploaded/created files. Does that mean, they let www-data be member of the group ftpusers?
[This]("http://www.soledadpenades.com/2006/12/15/how-to-set-up-the-web-server-for-working-in-a-team/") promotes putting all of /var/www into the group www-data.

---

