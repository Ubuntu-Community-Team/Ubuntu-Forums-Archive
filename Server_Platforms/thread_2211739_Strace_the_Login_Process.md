---
title: "Strace the Login Process"
date: 2014-03-17
forum: Server Platforms
---

### Post by IOutsmartedMyself on 2014-03-17
I have an Ubuntu 12.04.4 LTS server with no X Windows. Is there a way I can trace everything that is run from the moment a user logs in until they log out? Strace comes to mind, but something higher level that just shows each script executed would probably suffice.

The reason I'm looking to do this is because I made some change to disallow console logins, while still allowing SSH logins. I want to revert that change, but I don't remember how I did it. I [posted elsewhere]("http://www.linuxquestions.org/questions/linux-general-1/local-login-disabled%3B-how-do-i-allow-it-again-4175498318/") asking for help undoing the change with no luck. I'm thinking that tracing everything that runs after a user login will show me something I am overlooking. Perhaps there is a script that runs after login that I am not aware of. The issue affects all users, so it isn't just something in a home directory.

---

### Post by IOutsmartedMyself on 2014-03-21
I ended up just using strace (*sudo strace -f -p <pid> > st.log 2>&1*). I found what I was looking for near the end of the 59,000+ line log file:

```
[pid 10947] open("/etc/profile.d/nyan.sh", O_RDONLY) = 3
[pid 10947] fstat(3, {st_mode=S_IFREG|0744, st_size=4800, ...}) = 0
[pid 10947] read(3, "#!/bin/bash\n\n# If this isn't ssh"..., 4800) = 4800
[pid 10947] close(3)                    = 0
[pid 10947] rt_sigprocmask(SIG_BLOCK, NULL, [], 8) = 0
[pid 10947] rt_sigprocmask(SIG_BLOCK, NULL, [], 8) = 0
[pid 10947] rt_sigprocmask(SIG_BLOCK, NULL, [], 8) = 0
[pid 10947] rt_sigprocmask(SIG_BLOCK, NULL, [], 8) = 0
[pid 10947] rt_sigprocmask(SIG_BLOCK, NULL, [], 8) = 0
[pid 10947] rt_sigprocmask(SIG_BLOCK, NULL, [], 8) = 0
[pid 10947] rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
[pid 10947] open("/home/master/.bash_logout", O_RDONLY) = 3
```

The *nyan.sh* script was the last thing read before *.bash_logout*, so I looked closer and found the issue in that script. If you want more details, see the [LinuxQuestions.org thread]("http://www.linuxquestions.org/questions/showthread.php?t=4175498318").

---

