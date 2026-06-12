---
title: "rsync lost some file."
date: 2005-05-07
forum: Repositories &amp; Backports
---

### Post by oneleaf on 2005-05-07
I‘m web master of [http://www.ubuntu.org.cn](http://www.ubuntu.org.cn).

I mirror cn.archive.ubuntu.com by rsync.

```
#!/bin/bash

HOST=cn.archive.ubuntu.com
#HOST=mirror.isp.net.au
#HOST=archive.ubuntulinux.org

MIRROR_ROOT='ubuntu'
LOCAL="/share/ubuntu"
OPTIONS="-vzrtopg --progress --delete --delete-excluded"
EXCLUDE="--exclude daily-installer-powerpc/ \
--exclude installer-powerpc/ \
--exclude binary-powerpc/ \
--exclude upgrade-powerpc/ \
--exclude disks-powerpc/ \
--exclude *_powerpc.udeb \
--exclude *_powerpc.deb"

if [ -f $LOCAL/Archive-Update-in-Progress-ubuntu ]
then
echo "Mirroring ubuntu Package"
echo "So exiting"
exit
fi
rsync $OPTIONS $EXCLUDE $HOST::$MIRROR_ROOT $LOCAL

echo "Processing standard using $HOST"
/bin/rm -f $LOCAL/Archive-Update-in-Progress-ubuntu 
```

has none error,

but some file has lost.

for this: 
[http://cn.archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/](http://cn.archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/)
[http://archive.ubuntu.org.cn/ubuntu/dists/hoary/main/installer-i386/current/](http://archive.ubuntu.org.cn/ubuntu/dists/hoary/main/installer-i386/current/)

[http://cn.archive.ubuntu.com/ubuntu/pool/universe/e/evince/](http://cn.archive.ubuntu.com/ubuntu/pool/universe/e/evince/)
[http://archive.ubuntu.org.cn/ubuntu/pool/universe/e/evince/](http://archive.ubuntu.org.cn/ubuntu/pool/universe/e/evince/)

I havn't ,but cn.archive.ubuntu.com has.

---

