---
title: "The server is invaded and the /etc/ld.so.preload file cannot be modified"
date: 2021-11-01
forum: Security
---

### Post by leelee06 on 2021-11-01
During this period of time, the CPU load on the server is still very high without a process. I suspect that the server has been hijacked. I ```
cat /etc/ld.so.preload
```, Found the following line&#65306;
```
/usr/local/lib/libprocesshider.so

```According to the forum, I should modify the ld.so.preload file to delete this line, but I found that I did not have permission. I found that my lsattr and chattr commands all failed, even if I repeatedly installed e2fsprogs.I recompiled chattr using the forum method, and ```
sudo ./chattr -ia /etc/ld.so.preload
``` . And got the following:
```
leelee@ubuntu-PowerEdge-T440:~/tools$ sudo ./chattr -ia /etc/ld.so.preload
cur attrs: 0x00080030, mask: 0x00000030
new attrs: 0x00080000

```But I still cannot edit this file because ```
W10: Warning: Changing a readonly file
```. How can I solve this problem?

---

### Post by TheFu on 2021-11-02
If you suspect the system has been compromised, you need to backup data and logs then nuke it from orbit, that's the only way to be sure.  In those logs, you should figure out how someone hacked into the system and correct those issues on the new server.  If we have daily versioned backups, then we can compare new files added from period-to-period to notice when unexpected files "show up", their names and where they are located.  Stuff in /usr/local/ is stuff WE placed there. If we don't know what we put there, that's a problem.
&#8220;I say we take off and nuke the entire site from orbit. It's the only way to be sure.&#8221;

---

