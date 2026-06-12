---
title: "How To DIsconnect Remote Sessions"
date: 2009-04-23
forum: Server Platforms
---

### Post by CarlosinFL on 2009-04-23
I am logged into a server and run the 'who' command. I notice that I have left open a ssh session from a workstation upstairs in my office to the server. I was wondering what is the command I can run in order to cleanly kill / disconnect that session?

```
[root@file_svr ~]# who
root     tty1         2009-04-02 14:48
carlwill pts/0        2009-04-22 16:02 (mako.omgwtf.com)
carlwill pts/1        2009-04-23 08:16 (bull.omgwtf.com)
```

I would like to know how to kill the session established from 'mako' on 4/22.

---

### Post by cdenley on 2009-04-23
You could just find the PID of the shell, then kill it.
```

sudo ps -ef|grep pts/0

```

---

### Post by CarlosinFL on 2009-04-24
Thank you!

---

