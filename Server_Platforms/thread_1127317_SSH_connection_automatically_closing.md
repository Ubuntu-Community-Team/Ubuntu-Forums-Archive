---
title: "SSH connection automatically closing"
date: 2009-04-16
forum: Server Platforms
---

### Post by vergenzt on 2009-04-16
My brother and I have a dedicated server set up at his network (we live in different cities).  We have the DNS all set up, Ubuntu server edition installed, and the SSH server running, and I'm now trying to set up another administrative username for myself.  I'm able to ssh into his username, have already created the new user, and it logs in fine, but for some reason it does not stay connected, and closes the connection immediately.

```

[username]@[localcomp]:~$ ssh [newuser]@[server]
[newuser]@[server]'s password: 
Linux [server] 2.6.27-7-server #1 SMP Tue Nov 4 20:18:35 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

  System information as of Thu Apr 16 10:10:01 EDT 2009

  System load: 0.0               Memory usage: 27%   Processes:       68
  Usage of /:  3.0% of 36.00GB   Swap usage:   0%    Users logged in: 1

  Graph this data and manage this system at https://landscape.canonical.com/
Last login: Thu Apr 16 10:08:29 2009 from [...]
Connection to [server] closed.
[username]@[localcomp]:~$

```

It closes the connection immediately upon logging in for the new account, but not for the original user (the one I set up the new account with).  My brother speculates that I might not have shell permissions or something of that sort.  Any ideas?

---

### Post by brian_p on 2009-04-16
> **vergenzt said:**
> 

It closes the connection immediately upon logging in for the new account, but not for the original user (the one I set up the new account with).  My brother speculates that I might not have shell permissions or something of that sort.  Any ideas?

Suggestions:

1. Run ssh with the -v option.
2. Look at the logs on the server.

---

### Post by vergenzt on 2009-04-16
I've checked the logs after having upped the LogLevel in the config file to verbose, and they didn't provide any useful information, just that I connected then disconnected.

---

### Post by Zeosa on 2009-04-16
check the entry for your user in /etc/passwd and make sure there's a valid shell assigned for the username (/bin/bash).

Also, check the /etc/ssh/sshd_config for any "AllowUsers" or "AllowGroup" statements.

---

### Post by mdittmer on 2010-05-05
Hey.

I am having this problem on Ubuntu Server 9.10.

Any further thoughts? The login user has a valid shell in /etc/passwd and there are no AllowUsers statements in /etc/ssh/sshd_config.

SOLVED: The problem appears to be in a bad release of openssh-client. I tried connecting from a different machine and it worked, so I purged, updated, and reinstalled openssh-client on the machine that was having trouble connecting.

---

### Post by ghost_ryder35 on 2010-05-05
> **vergenzt said:**
> My brother and I have a dedicated server set up at his network (we live in different cities).  We have the DNS all set up, Ubuntu server edition installed, and the SSH server running, and I'm now trying to set up another administrative username for myself.  I'm able to ssh into his username, have already created the new user, and it logs in fine, but for some reason it does not stay connected, and closes the connection immediately.

```

[username]@[localcomp]:~$ ssh [newuser]@[server]
[newuser]@[server]'s password: 
Linux [server] 2.6.27-7-server #1 SMP Tue Nov 4 20:18:35 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

  System information as of Thu Apr 16 10:10:01 EDT 2009

  System load: 0.0               Memory usage: 27%   Processes:       68
  Usage of /:  3.0% of 36.00GB   Swap usage:   0%    Users logged in: 1

  Graph this data and manage this system at https://landscape.canonical.com/
Last login: Thu Apr 16 10:08:29 2009 from [...]
Connection to [server] closed.
[username]@[localcomp]:~$

```

It closes the connection immediately upon logging in for the new account, but not for the original user (the one I set up the new account with).  My brother speculates that I might not have shell permissions or something of that sort.  Any ideas?

is the account disabled/locked in /etc/shadow ?  in /etc/passwd does the user account have the correct shell?  if the shell is /usr/sbin/nologin you would see this behavior.

---

