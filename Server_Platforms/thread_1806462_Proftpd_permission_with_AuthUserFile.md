---
title: "Proftpd permission with AuthUserFile"
date: 2011-07-17
forum: Server Platforms
---

### Post by BrandonSk on 2011-07-17
Hello all,
I am having a permission problem with Proftpd. For last 8 hours I read every possible guide and forum, but none seem to address my issue. After a lot of trial and error I think I narrowed down the issue, but I can't find a solution to it.

Situation:
**Server**
...is using AuthUserFile and AuthGroupFile directives. In these files I have users and groups defined. One of the users is oracle (ID 1100) belonging to group FtpFullControl (ID 1100).
Server runs under User ftp (ID 108 ) and Group ftp (ID 1002).

**Directories**
Directory /srv is set as home folder for user oracle (in AuthUserFile).
In the filesystem, srv is owned by root/root. Subdirectories (e.g. /srv/public) are owned by user ftp and group ftp. Permissions on them are 775 (recursively it applies to all subfolders and files).

When I log-in to ftp, I can see and browse the contents of /srv and all sub directories. However, I cannot create directory or upload any file (no matter in which subdirectory), resulting with Permission denied error (usually 550).

_**This is what I think the problem is:**_
The daemon (sorry if wrong terminology) is run under user ftp (just as it should, as it is specified by User ftp directive).
As soon as I log in, a new process (?) is started, but it is run under UserID of 1100, which corresponds to oracle user id in the AuthUserFile. (oracle user does not exist in the system). And therefore any upload I try to make, results in permission denied as user with ID 1100 has only rx permision in /srv and below. (When I tried chmod 777, it of course worked, but I do not want 777).

For better illustration, the output of ps:
```
root@server:~# ps aux | grep proftpd
ftp 13182 0.0 0.3  7296 1548 ?       Ss   00:18   0:00 proftpd: (accepting connections)
1100  13187 0.3 0.4 7464 2136 ? S 00:18 0:00 proftpd: oracle - ::ffff:192.168.111.11: IDLE
root     13189  0.0  0.1   4148   852 pts/0    S+   00:18   0:00 grep --color=auto proftpd

```

[B]Questions:
[/B]1) Is my thinking and identification of the issue correct?
2) How do I fool / force proftpd to always run as "ftp" system user and not to create sub-processes with IDs from AuthUserFile?

Thank you all in advance for answers.
Cheers,
Brandon.

---

### Post by BrandonSk on 2011-07-30
I was going to bump this, but folks at proftpd have replied to my question there.

The answer also finally cleared out my confusion around access control of proftpd (e.g. file system permissions vs. <Limit>) and difference how system and virtual users are handled. I posted a small summary there.

If you are interested in the answer, please follow this link:
[http://forums.proftpd.org/smf/index.php/topic,6095.0.html](http://forums.proftpd.org/smf/index.php/topic,6095.0.html)

Cheers,
B.

---

