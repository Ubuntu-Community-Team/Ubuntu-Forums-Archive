---
title: "Kernel Panic - Not Syncing: Attempted to Kill Init!"
date: 2007-11-03
forum: Server Platforms
---

### Post by thornomad on 2007-11-03
Hello -

I have a ubuntu server running 6.06.1.  Today I tried to mount an NFS share from another server.  when I ran the mount command on my machine, however, the system froze.  I couldn't get the mount to stop even using "ctrl-c".  So, I opened a new terminal window and logged back in and tried to restart the system ... however, that wouldn't work either (problem with enabling sudo).  So I fell back to doing an old fashion restart (power off power on) and now I am getting a kernal panic.  

The error when it hangs is:

```
run-init: /sbin/init: error 13
kernel panic - not syncing: attempted to kill init!
```

I have done some reading on the forum but most people seem to encounter this problem during an installation -- not after a system has been working for some time.  Also some suggestion that it is a hardware problem.  Reading on google indicates maybe the problem is that I can't mount the / directory at startup.  

However, I'm not really sure how to work to fix this.  I can't even get a command prompt (not in safe mode either) so I can't edit any configuration files.

I have my /home folders mounted separately, so as a fall-back I think I could reinstall the system, but want to try and avoid that.

Does anyone have any suggestions about where I can start to solve this ?

Thanks,
Damon

---

