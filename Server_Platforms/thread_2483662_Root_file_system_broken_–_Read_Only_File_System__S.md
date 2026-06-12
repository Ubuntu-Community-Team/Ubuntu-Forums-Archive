---
title: "Root file system broken – Read Only File System / Structure needs cleaning"
date: 2023-02-06
forum: Server Platforms
---

### Post by maryberry on 2023-02-06
Hey all,

been reading a lot and often in the last 5 years, so first of all: Thank you all! Now I’m desperate enough for my first post.

I have a server running Ubuntu 16.04 and suddenly apache was not responding anymore, so I ssh’d into the machine and tried to restart the apache service which did not work: 

```
Job for apache2.service failed because a configured resource limit was exceeded. See "systemctl status apache2.service" and "journalctl -xe" for details.
```

I then found out I could not run any command not even a simple [FONT=courier new]ls -la[/FONT] or [FONT=courier new]df -h[/FONT] would work. Most commands would show *input/output error* or *command not found*.

After reading [this post]("https://askubuntu.com/questions/197459/how-to-fix-sudo-unable-to-open-read-only-file-system"), I found out that the [FONT=courier new]mount[/FONT] would still show me a list of mount points and I tried to remount with [FONT=courier new]sudo mount -o remount /[/FONT] which didn’t work out:

```
mount: cannot remount /dev/mapper/koloss--vg-root read-write, is write-protected
```

I then tried [FONT=courier new]sudo mount -o remount,rw /[/FONT] and now every command gives me *Structure needs cleaning* or *command not found*. It looks like I can still switch folders with *cd* at least.

Can someone please help me? ssh’ing into the machine in a new terminal doesn’t work anymore either. I have rsnapshot backups of the machine but I really hope I won’t need them.

Thank you very much! 

Mary

---

### Post by guiverc on 2023-02-06
You do realize Ubuntu 16.04 LTS, or the 2016-April release of Ubuntu, reached the end of it's five years of *standard support* back in April 2021.

An announcement of this can be read here
 - [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)
 with more details here
- [https://ubuntu.com/blog/ubuntu-16-04-lts-transitions-to-extended-security-maintenance-esm](https://ubuntu.com/blog/ubuntu-16-04-lts-transitions-to-extended-security-maintenance-esm)

If a file-system has flipped from ***RW*** (*read-write*) to ***RO*** (*read-only*), there is a reason, ranging from corruption to failing hardware, that should be explored and not just ignored. Your logs are where to look for clues, but as you're using an EOSS (*end of standard support*) system, I do hope you've enabled *ESM* so as to get security patches if your machine is online.

---

