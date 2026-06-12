---
title: "Am I hacked?"
date: 2009-09-21
forum: Security
---

### Post by mrcoulson on 2009-09-21
What does it mean when /var/log/auth.log tells me "User child is on pid..."?  Should I be as concerned as I am or is this something I'd know about if I were a Linux expert?

Jeremy

---

### Post by denver on 2009-09-21
Would help if you posted that portion of your log so we can take a closer look at what happened before and after.

---

### Post by mrcoulson on 2009-09-21
Okay.  Please hold...

---

### Post by mrcoulson on 2009-09-21
Okay, here it is.  It's a little sanitized so I'm not giving away too much information.

Sep 21 09:00:01 MYSERVER CRON[25323]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 21 09:00:01 MYSERVER CRON[25324]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 21 09:00:01 MYSERVER CRON[25324]: pam_unix(cron:session): session closed for user root
Sep 21 09:00:01 MYSERVER CRON[25323]: pam_unix(cron:session): session closed for user root
Sep 21 09:03:19 MYSERVER sshd[25305]: Connection closed by my.XP.machine.IPaddress
Sep 21 09:03:19 MYSERVER sshd[25305]: Transferred: sent 502408, received 9256 bytes
Sep 21 09:03:19 MYSERVER sshd[25305]: Closing connection to my.XP.machine.IPaddress port 3903
Sep 21 09:03:19 MYSERVER sshd[25297]: pam_unix(sshd:session): session closed for user myuser
Sep 21 09:03:23 MYSERVER sshd[25370]: Connection from my.XP.machine.IPaddress port 1234
Sep 21 09:03:28 MYSERVER sshd[25370]: Found matching DSA key: string:of:characters
Sep 21 09:03:28 MYSERVER sshd[25370]: Found matching DSA key: string:of:characters
Sep 21 09:03:28 MYSERVER sshd[25370]: Accepted publickey for myuser from my.XP.machine.IPaddress port 1234 ssh2
Sep 21 09:03:28 MYSERVER sshd[25370]: pam_unix(sshd:session): session opened for user myuser by (uid=0)
Sep 21 09:03:28 MYSERVER sshd[25370]: User child is on pid 25378
Sep 21 09:06:24 MYSERVER sudo: myuser : TTY=pts/0 ; PWD=/home/myuser ; USER=root ; COMMAND=/usr/bin/vi /etc/ssh/sshd_config
Sep 21 09:06:53 MYSERVER sudo: myuser : TTY=pts/0 ; PWD=/home/myuser ; USER=root ; COMMAND=/etc/init.d/ssh restart

---

### Post by mrcoulson on 2009-09-21
By the way, "child" is not listed in cat /etc/passwd.

Jeremy

---

### Post by SlugSlug on 2009-09-21
what does 
ps -ef |grep 25378


show?

---

### Post by mrcoulson on 2009-09-21
myuser 25378 25370  0 09:03 ?        00:00:01 sshd: myuser@pts/1
myuser 25379 25378  0 09:03 pts/1    00:00:00 -bash
myuser 26445 25379  0 10:31 pts/1    00:00:00 grep 25378

Jeremy

---

### Post by cdenley on 2009-09-21
It looks like it is simply logging the PID of the child process which sshd spawned for the session created in the line above it. I don't recally ever seeing such logging on an ubuntu server. What version are you running?
```

lsb_release -a
ssh -V

```

Any special configuration?
```

grep ^[^#] /etc/ssh/sshd_config

```

---

### Post by mrcoulson on 2009-09-21
I'm running Server 9.04.  OpenSSH says 5.1p1.

I do have some special changes to the config file.  I'm using verbose logging.  I've changed the port and disabled password logins.  

So, I gather that it's not something that indicates trouble and I should slow my heart rate back to where it was this morning before work?

Jeremy

---

### Post by __p1n__ on 2009-09-21
You logged in through ssh, right?  The bash shell that you're running (pid 25379) was spawned by the ssh connection process (pid 25378.)  It's a process itself, a process that is a child of the parent (ssh connection) process.

The grep command (pid 26445) was spawned by your bash process (pid 25379) and is a child of that.

Signals can be propagated through process hierarchies (parent/child/...) Environmental variables are also propagated down through a tree.  IO handles can also be transferred between member processes.  When a child process terminates then SIGCHILD is sent to the parent process.

---

### Post by openfly on 2009-09-22
Actually they are all just joshing you.  Child is a notorious hacker trained by the likes of peer and fork.  His notorious exploits have hacked many a persons user experience into an ownage nightmare.

---

