---
title: "Installing Bugzilla without apt-get"
date: 2006-12-18
forum: Server Platforms
---

### Post by kpm on 2006-12-18
Hi,
I setup Bugzilla to work with our Active Directory on an Ubuntu LAMP server.  All worked well, but, as it turns out, I must now mimic a tweaked version that is running on a Windows server. It is using the latest stable version.  That tweaked version, I was told, should not care what the server is so It should run on a LAMP setup, but I can't seem to get it to work at all. So I tried the latest tar.gz and simply dumped and extracted it into the /var/www/ folder but I get nothing and can't even run the checksetup.pl script.  I have made all the param and config file changes, but my guess is I am missing some permissions or symlinks or Apache conf file settings.  If I use apt to install, then I can run the checksetup.pl script, but when I navigate to that same file dumped in the /var/www/ I am not able to, I get a 'command not found' error.
Can anyone offer any suggestions... want to try and avoid sticking Bugzilla on Windows, but will have to start formatting a Windows server soon if I can't get this sorted out so Bugzilla can work in one 'bugzilla' directory rather than all the other directories it ends up in with apt-get (etc, var, ...).
Thanks

---

### Post by elst on 2006-12-19
I would guess that you are missing something in either the Web server or database configuration. Without knowing more about the "tweaked version" it's difficult to be more specific. Web applications can be a pain to install and update if you don't use packaged versions.

---

