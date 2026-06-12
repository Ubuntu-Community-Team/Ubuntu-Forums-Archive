---
title: "apt-cacher-ng import over sshfs"
date: 2011-01-20
forum: Server Platforms
---

### Post by cong06 on 2011-01-20
I'm working on installing Ubuntu for several small labs. One of the things I install for these labs, is apt-cacher-ng. Apt-cacher-ng saves quite a bit of bandwidth for these labs.

In order to save more bandwidth, I like to import the debian files from another debian archive.
Now because of this, I need to mount the sshfs as read only:
```
sudo sshfs root@10.42.43.1:/var/cache/apt-cacher-ng/ /media/aptcache/ -o ro
```

Another factor is, the cache on 10.42.43.1 not only has 64 bit files, but also has lucid and maverick files. The cache for the labs only need lucid, and only need 32 bit. So it's silly to copy all the files over from the server.

Now, I could run:
```
sudo find /media/aptcache -name "*.deb" -type f -exec cp -v {} /var/cache/apt-cacher-ng/_import/ \;
``` and then run the import. This works well, but as I said above, I don't need all those files.
I'd rather do this:

```

lari@lari-desktop /var/cache/apt-cacher-ng/_import $ sudo ln -s /media/aptcache
lari@lari-desktop /var/cache/apt-cacher-ng/_import $ ls -l
total 0
lrwxrwxrwx 1 root apt-cacher-ng 15 2011-01-20 11:20 aptcache -> /media/aptcache

```

But this fails (with non-specific errors). I'd guess it has to do with the permissions, but I can't figure out what to do. I've tried almost anything.
Any ideas? I'd like any ideas, no matter how simple.

---

