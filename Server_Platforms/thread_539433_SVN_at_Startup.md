---
title: "SVN at Startup"
date: 2007-08-31
forum: Server Platforms
---

### Post by infinitezero on 2007-08-31
Is there a way to have SVN server start at boot? Currently I use this command, "svnserve -d --foreground -r /home/svn", to start my svn server after the system has started.

Thanks,
iz

---

### Post by trtech on 2007-10-18
This is interesting: 
[http://eightpence.com/a-subversion-initd-script-for-ubuntu-linux/](http://eightpence.com/a-subversion-initd-script-for-ubuntu-linux/)

There's a nice startup script there, *but* I prefer to not to run the svnserver process and access the repository via svn+ssh protocol, which is described at the beginning of that page.

Cheers,
Chris

---

