---
title: "Issues setting up a subversion server..."
date: 2010-03-24
forum: Server Platforms
---

### Post by colinhect on 2010-03-24
Following [this]("http://www.linuxpronews.com/linuxpronews-55-20090318HowToCreateAnUbuntuSubversionServer.html") tutorial I have attempted to set up a subversion server.  Here is what I did on the server:

```

colin@projhect:~$ cd /var
colin@projhect:/var$ sudo mkdir svn
colin@projhect:/var$ sudo svnadmin create svn
colin@projhect:/var$ sudo adduser --system --no-create-home --group svn 
Adding system user `svn' (UID 114) ...
Adding new group `svn' (GID 121) ...
Adding new user `svn' (UID 114) with group `svn' ...
Not creating home directory `/home/svn'.
colin@projhect:/var$ sudo chown -R svn.svn /var/svn/
colin@projhect:/var$ sudo adduser colin svn
Adding user `colin' to group `svn' ...
Adding user colin to group svn
Done.
colin@projhect:/var$ id colin
uid=1000(colin) gid=1000(colin) groups=1000(colin),4(adm),20(dialout),24(cdrom),46(plugdev),104(lpadmin),115(admin),120(sambashare),121(svn)

```

And then I attempt an initial commit from another box:

```

colin@hectop:~/projects$ svn import project/ svn+ssh://projhect.local/var/svn/project/head -m 'Initial import'
colin@projhect.local's password: 
colin@projhect.local's password: 
colin@projhect.local's password: 
Adding         project/todo
...
svn: Can't open file '/var/svn/db/txn-current-lock': Permission denied

```

I Googled this error and found that it is a permission issue (obviously).  I tried the various methods of fixing this but none of them worked.  

Anyone have any ideas?

---

### Post by vuetrip on 2010-08-13
try "sudo command" instead of just the command

and on the subject of subversion is anyone aware of a web interface that can edit and commit to svn?

---

### Post by Ryan Dwyer on 2010-08-13
You added colin to the svn group, but by default the group cannot write to that folder. You need to sudo chmod -R g+w /var/svn.

---

