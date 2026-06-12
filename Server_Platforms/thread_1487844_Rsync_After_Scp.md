---
title: "Rsync After Scp"
date: 2010-05-19
forum: Server Platforms
---

### Post by mnauman on 2010-05-19
Hello There

I used  scp to copy data from one server to another. What happens if i now use rsync to sync data?

I guess my question would be is rsync smart enough to deal with data that is there from scp??:confused:

This question has been asked before:
[http://ubuntuforums.org/showthread.php?t=291264](http://ubuntuforums.org/showthread.php?t=291264)

Thanks.

---

### Post by arrrghhh on 2010-05-19
That's the whole point of rsync, it intelligently transfers files.  Even pieces of files.

---

### Post by mnauman on 2010-05-20
Thanks, 

It does, as long as the folder structure is same.

---

