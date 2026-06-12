---
title: "Apache Memory Leak"
date: 2008-04-08
forum: Server Platforms
---

### Post by Joeb454 on 2008-04-08
I've got reason to believe that Apache has some sort of memory leak :(

I'm running Ubuntu 7.10 server edition, and I noticed the RAM usage was high, so at the suggestion of a friend, I ran ```
:~# lsof | grep apache | wc -l
``` which told me that Apache had 843 files open.

I thought that was pretty high, so I refreshed the page, and that number jumped to 921! So anyway, I restarted Apache...and to my surprise, I found that RAM was 70Mb less, and the above command return 456 files open by Apache.

Does anybody know why this is? Or whether it is actually a memory leak in Apache?

---

### Post by cdenley on 2008-04-09
I tried on my gutsy server. It seems there are a lot of old, deleted access logs still open.
```

cdenley@www:~$ sudo lsof | grep apache |wc -l
4589
cdenley@www:~$ sudo lsof | grep apache |grep .log|wc -l
1000
cdenley@www:~$ sudo lsof | grep apache |grep \(deleted\)|wc -l
1075

```
My second server which doesn't use SSL doesn't have this problem.

I think it's related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/174805"). The apache logs are rotated daily, then a graceful restart of apache closes the old logs. However, since the graceful stop of apache is still broken in gutsy if you listen on multiple sockets, the logs are never closed until you restart apache completely. I hope they fix apache for gutsy, but it is already fixed for hardy.

---

### Post by Joeb454 on 2008-04-09
Thanks for that :)

I'm planning on Upgrading my server to Hardy anyway, so this is good news :)

---

