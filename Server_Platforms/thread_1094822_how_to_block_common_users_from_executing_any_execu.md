---
title: "how to block common users from executing any executable file"
date: 2009-03-13
forum: Server Platforms
---

### Post by cswwwb on 2009-03-13
Hi guys,

I am administrating a server for a small group. Users are asked to follow pbs-like job submitting routine.However, my group user usually does not follow the thing and runs jobs directly from prompt. I want to ask whether there is any method to block common user from executing any executable file. The only way they can execute their jobs is from using job-submitting scheduler, such as pbs/maui.

Any one has a suggestion, please give me some hint. Thanks a lot!

btw, the connection between user and server is through SSH.

---

### Post by bluefrog on 2009-03-13
have a look there [http://www.howtoforge.com/chroot_ssh_sftp_debian_etch](http://www.howtoforge.com/chroot_ssh_sftp_debian_etch)

---

