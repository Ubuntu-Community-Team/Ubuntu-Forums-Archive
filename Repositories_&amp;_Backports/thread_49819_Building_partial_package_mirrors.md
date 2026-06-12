---
title: "Building partial package mirrors"
date: 2005-07-17
forum: Repositories &amp; Backports
---

### Post by Kinema on 2005-07-17
Is there a way to build a partial mirror?  I only need x68 from Hoary.  Main and Universe.  I don't want to waste bandwidth sucking down packages that I'm never going to use.  Is there a way to rsync just what I need?

In case you are wondering I'm interesed in a local mirror because I have quite a few boxes and a limited amount of bandwidth.

--adam

---

### Post by UbuWu on 2005-07-21
Yes, that is possible. Use debmirror. The command would look something like this:

debmirror -p --nosource --host=mirror.pacific.net.au
--root=linux/ubuntu --method=http --dist=hoary --arch=i386
--section=main,multiverse,restricted,universe /opt/ubuntu_pacific/

And then you can use this location as a repository.

See also:
[http://www.ubuntuforums.org/showthread.php?t=4117](http://www.ubuntuforums.org/showthread.php?t=4117)

---

