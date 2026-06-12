---
title: "2 machines pull from same repo get different files"
date: 2012-08-06
forum: Server Platforms
---

### Post by rgeddes on 2012-08-06
Two amd64 machines pull from the same repo:

[http://ppa.launchpad.net/nginx/stable/ubuntu](http://ppa.launchpad.net/nginx/stable/ubuntu) precise main

installed files on machine A:
```
$0> dpkg -L nginx
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/nginx
/usr/share/doc/nginx/changelog.gz
/usr/share/doc/nginx/changelog.Debian.gz
/usr/share/doc/nginx/copyright
/usr/share/doc/nginx/README.Debian
/usr/share/doc/nginx/CHANGES.gz
```

installed files on machine B:
```
$0> dpkg -L nginx
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/nginx
/usr/share/doc/nginx/changelog.gz
/usr/share/doc/nginx/changelog.Debian.gz
/usr/share/doc/nginx/copyright
/usr/share/doc/nginx/README.Debian
/usr/share/doc/nginx/CHANGES.gz
/etc/nginx/conf.d/hide_server_tokens.conf
/etc/nginx/conf.d/gzip.conf
/etc/init/nginx.conf
```

notice the last three files on B are missing from A.

had nginx running OK on both machines
A is a fresh install, 
B has been updated since natty

updated both machines today.
- A complained about the /etc/init.d/nginx script and it would not do restart or stop correctly.
- B had no problems

purged A of nginx, re-installed... no change.

I noticed B has an upstart script... I copied this upstart file from B to A, and A is OK now.

I don't want to worry about this in the future.. is there a way to tell why A has those extra 3 files?

Thanks

---

