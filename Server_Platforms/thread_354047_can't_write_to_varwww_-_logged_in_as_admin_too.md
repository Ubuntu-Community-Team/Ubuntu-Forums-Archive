---
title: "can't write to /var/www - logged in as admin too"
date: 2007-02-05
forum: Server Platforms
---

### Post by nucklebone on 2007-02-05
As I see others have, I also have been having troubles putting files in my /var/www directory. I have Apache2 installed and running. I can see files in that directory and if I am physically at that machine I can put and get files to and from that directory.

The problem happens when I try to log in via a FTP/SFTP client using SSH. I can log in as the administrator and read files just fine, but when I try to upload files to that directory I get a permission denied error.

My user is part of the 'admin' group and I also made a new group called 'www-data' and added my user to that group also, as was reported to work in another thread, but still do not have the ability to upload files to that directory even though I am able to authenticate as the admin user.

In addition to being in the admin group for that computer, do I also have to define who the admin is in Apache2? This is very frustrating coming from the OS X world.

Any help would be appreciated. And please be explicit, I'm a Macintosh user. I only know how to get around and be dangerous in *nix, not be a <i>real</i> administrator.

--
nucklebone

---

### Post by elst on 2007-02-05
It's likely to be just a file permission setting on the directory - if you login with SFTP then the account that you specify on the remote system should have *execute* permissions for the directory in order to work with it.

This sets "www-data" as the owning group for /var/www and everything that it contains:

sudo chgrp -R www-data /var/www

And this grants the owning group read, write and execute on all files:

sudo chmod -R 775 /var/www

The fact that the directory happens to be used by Apache isn't really important in this case, as you aren't accessing it through the Apache service.

---

### Post by nucklebone on 2007-02-05
Perfect!

That worked great. Thanks for the response. I know how to use the chmod, chgrp and chown tools, but I never know when, where, why to use them. Your post made perfect sense.

Thanks again,
nucklebone

---

