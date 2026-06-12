---
title: "error: src refspec master does not match any."
date: 2011-01-30
forum: Server Platforms
---

### Post by jiapei100 on 2011-01-30
Hi, all:

I'm trying to use git for version control.

I successfully committed my source to github already.
I'm trying to commit it to sourceforge now.

I strictly follow the description at [https://sourceforge.net/apps/trac/sourceforge/wiki/Git](https://sourceforge.net/apps/trac/sourceforge/wiki/Git) 
but finally with a failure notification like:

> 
jiapei@jiapei-laptop:~/cmake/sf/vosm$ git push origin master
[email]jiapei@vosm.git.sourceforge.net[/email]'s password: 
Counting objects: 205, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (200/200), done.
Writing objects: 100% (205/205), 282.70 KiB, done.
Total 205 (delta 103), reused 0 (delta 0)
fatal: Unable to create temporary file: Permission denied
error: unpack failed: index-pack abnormal exit
To ssh://jiapei@vosm.git.sourceforge.net/gitroot/vosm/vosm
! [remote rejected] master -> master (n/a (unpacker error))
error: failed to push some refs to 'ssh://jiapei@vosm.git.sourceforge.net/gitroot/vosm/vosm'


Can anybody give me a hint where I'm wrong?

Best Regards
JIA

---

