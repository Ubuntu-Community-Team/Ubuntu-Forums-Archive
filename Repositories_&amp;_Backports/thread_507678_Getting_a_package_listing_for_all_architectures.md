---
title: "Getting a package listing for all architectures"
date: 2007-07-23
forum: Repositories &amp; Backports
---

### Post by Elpram on 2007-07-23
Hi,

I'm trying to find a way to download the package listing for all architectures.  I have a script that I have to run on the headers to pull out some info for a database.  I've looked into apt-get and dpkg....but haven't really made any headway (maybe wget?)

If someone could point me in the right direction, it would be much appreciated.

Thanks,
Elpram

---

### Post by tgm4883 on 2007-07-23
This may help.  You could parse the pages, going deep enough would yield the results your looking for

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Or perhaps here you could download the packages.gz file for each arch and parse that

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/)

Not sure how to do it your way though

---

### Post by Elpram on 2007-07-23
Perfect!

That second link was just what I needed.  Thanks a bunch for the help.

---

