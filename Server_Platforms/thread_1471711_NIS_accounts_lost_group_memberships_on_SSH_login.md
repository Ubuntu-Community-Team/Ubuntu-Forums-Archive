---
title: "NIS accounts lost group memberships on SSH login"
date: 2010-05-03
forum: Server Platforms
---

### Post by blackjade on 2010-05-03
My situation is a bit complex , so I will try to describe it clearly. Sorry for my English.

We have a small network consists of 5 servers, providing SSH for several groups of users.  We want the users (e.g., me) be able to log in to any of the servers with their own account. So, we define the user accounts in a server that runs NIS service, and configure all the other servers as NIS clients. We also defined several groups for different user groups, so some users belong to several groups. All the user information is populated by NIS. This setup is working in Ubuntu 8.04, AMD64.

Now I upgrade the servers to Ubuntu 10.04 64Bit. The problem is, now if I log in to one of the NIS client servers using SSH, my group membership is lost. However, when I log in directly to the server, the group membership is retained.

For example, in the /etc/group file, I defined the user tliu as a number of awww group:

```

tliu:x:1004:
agroup:!:2000:tliu,ian,verickson
awww:!:2010:tliu,bstark,verickson

```If I log in locally (as tliu), I belongs to 3 groups: tliu, agroup and awww.

```

[16:09:24]tliu@venus:~$ groups
tliu agroup awww

```But if I log in via SSH, I only belongs to tliu group:

```

tliu@mars:~$ ssh venus
Enter passphrase for key '/home/tliu/.ssh/id_rsa': 
Linux venus 2.6.32-21-server #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.04 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Mon May  3 16:14:57 PDT 2010

  System load: 0.0               Memory usage: 11%   Processes:       116
  Usage of /:  3.1% of 29.53GB   Swap usage:   0%    Users logged in: 1

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Mon May  3 16:12:20 2010 from localhost
[16:14:57]tliu@venus:~$ groups
tliu
[16:15:00]tliu@venus:~$ 

```Original I though it's because the PAM authentication, so I set UsePAM to no in /etc/ssh/sshd_config, but that did not work. Any suggestions?

---

### Post by nibor_ on 2010-05-04
Your problem is probably related to this bug: [https://bugs.launchpad.net/ubuntu/+source/nis/+bug/553142](https://bugs.launchpad.net/ubuntu/+source/nis/+bug/553142)

---

### Post by scenered on 2010-05-04
Have the same problem with SSH logins. I upgraded my NIS clients from 9.10 server to 10.04 server. When logging in through SSH, the groups from the NIS server are missing. 
When running a 'su user' command after the SSH login, the groups show fine.
So there seems to be a problem with the SSH login on the 10.04...
When logging in through SSH on a 9.10 it works fine.
The NIS server is running on a 9.10 server edition.

---

### Post by nibor_ on 2010-05-04
> **scenered said:**
> Have the same problem ...

Please add that comment to the bug report and set "this bug affects me".

---

### Post by blackjade on 2010-05-04
A possible fix to the SSH problem is to edit /etc/nsswitch.conf: group:          compat nis
(instead of)
group:          compat
 As suggested by Bernhard M. in a Launchpad post: [https://bugs.launchpad.net/ubuntu/+source/nis/+bug/553142](https://bugs.launchpad.net/ubuntu/+source/nis/+bug/553142)

---

### Post by jlinkels on 2011-06-23
The solution by **blackjade** worked for me in Debian. Thanks!

jlinkels

---

