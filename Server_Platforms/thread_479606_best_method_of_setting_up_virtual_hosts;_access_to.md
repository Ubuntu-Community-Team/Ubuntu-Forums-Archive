---
title: "best method of setting up virtual hosts; access to folders and users"
date: 2007-06-20
forum: Server Platforms
---

### Post by DoppyNL on 2007-06-20
Hi People,

I'm setting up an apache-server that will have several virtual hosts.
I'm planning on placing all those hosts in the dir /var/www/ as that seems to be the appropiate location.

The dir /var/www/ is owned by "www-data".

What would be the best way to handle this security-wise?

A - If I need to access files on that location or create a folder, I keep hitting the wall because I don't have access. I can use sudo to do stuff like that, but it doesn't make you happy. Also copying files is a hassle. Do I need to use a different location for my virtual hosts? do I need to use some sort of special access to some user to make this more easy?
B - How would I do this when I also install an FTP-server? several different users must be able to upload data to different virtual hosts, but aren't allowed to access other virtual hosts. How would I do this with users on my system? Will the FTP-server-configuration handle this?
C - Does uploading files via the ftp-server `solve` this problem? (because the FTP-server wil also run under www-data ??)
D - will there be a security-problem when all files in all virtual hosts are owned by www-root? When PHP-scripting is allowed. Or will the server-setting "DocumentRoot" prevent access to files outside the virtual host?

As you see; some question that are mostly security-related. I'm aiming for a system that is properly configured and not in an weird way.

I hope someone can point me to the correct method of configuring a server.
If this information can be found elsewhere, please direct me there.

Thanks for your help.

---

### Post by Frosty Cold Drink on 2007-06-20
> **DoppyNL said:**
> The dir /var/www/ is owned by "www-data".

What would be the best way to handle this security-wise?

A - If I need to access files on that location or create a folder, I keep hitting the wall because I don't have access. I can use sudo to do stuff like that, but it doesn't make you happy. Also copying files is a hassle. Do I need to use a different location for my virtual hosts? do I need to use some sort of special access to some user to make this more easy?
Change the directories to be writable by the www-user group, and add yourself to the group. (Although, since www-user is a default, you may want t ouse something else for the group so permissions clobbering doesn't happen.

> B - How would I do this when I also install an FTP-server? several different users must be able to upload data to different virtual hosts, but aren't allowed to access other virtual hosts. How would I do this with users on my system? Will the FTP-server-configuration handle this?
Same thing if you want to make your life miserable. Serve virtual hosts out of user directories if you want to keep your sanity.

> C - Does uploading files via the ftp-server `solve` this problem? (because the FTP-server wil also run under www-data ??)
No, although you could do it like that if you'd like... to suffer.

> D - will there be a security-problem when all files in all virtual hosts are owned by www-root? When PHP-scripting is allowed. Or will the server-setting "DocumentRoot" prevent access to files outside the virtual host?
DocumentRoot won't do jack security-wise. Yes, having everything owned by www-root would be a problem if you want to prevent users from clobbering each other's sites, or if you want to contain security breaches. People just seem to hate PHP safe mode...

> As you see; some question that are mostly security-related. I'm aiming for a system that is properly configured and not in an weird way.
Weird is good. Sloppy and insecure is bad.

---

