---
title: "ebox vs confs and .file"
date: 2009-08-12
forum: Server Platforms
---

### Post by tecrr on 2009-08-12
I removed a share via command line and when I went into ebox, I noticed that it hadn't detected my changes in smb.conf.

Also I added some printers via command line but they don't show up in ebox. Is there a way to refresh ebox so it sees the command line changes?

Also I want the .files to be hidden from windows users.

I added 
hide dot files = yes
 to the smb.conf where the Shared directories are but still those pesky .files are showing still. I did restart samba too.
I also tried 
hide files = /.*
and
hide files = /.*/

Am I doing this wrong?
I am using jaunty server

Thanks a bunch.

---

