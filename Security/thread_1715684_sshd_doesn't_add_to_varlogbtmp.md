---
title: "sshd doesn't add to /var/log/btmp"
date: 2011-03-27
forum: Security
---

### Post by Mozai on 2011-03-27
Bad login attempts via ssh (package 'openssh-server') doesn't add to /var/log/btmp.  This is different from other flavours of Linux I have used.

There's a well-known quirk where sshd won't add to btmp if the owner isn't root and permissions are anything other than 0600.  That was the first thing I fixed.  And yet:

```

equius:~$ ls -l /var/log/btmp
-rw------- 1 root utmp 768 2011-03-27 11:47 /var/log/btmp
equius:~$ ssh asdf@localhost
asdf@localhost's password: 
Permission denied, please try again.
asdf@localhost's password: 
Permission denied, please try again.
asdf@localhost's password: 
Permission denied (publickey,password).
equius:~$ ls -l /var/log/btmp
-rw------- 1 root utmp 768 2011-03-27 11:47 /var/log/btmp
equius:~$ sudo lastb
btmp begins Sun Mar 27 11:47:36 2011

```

I know it's not a systemwide failure, I believe it's just sshd:
```

equius:~$ sudo login
equius login: asdf
Password: 
Login incorrect
^C
equius:~$ ls -l /var/log/btmp
-rw------- 1 root utmp 1152 2011-03-27 11:56 /var/log/btmp
equius:~$ sudo lastb
UNKNOWN  pts/2                         Sun Mar 27 11:56 - 11:56  (00:00) 
btmp begins Sun Mar 27 11:47:36 2011
equius:~$ 

```

How do I coerce sshd to add entries to /var/log/btmp, just as sshd does on other distributions of Linux?

---

### Post by cariboo on 2011-03-27
Try the **last** command, it works for me.

---

### Post by Mozai on 2011-03-27
> **cariboo907 said:**
> Try the **last** command, it works for me.

Do you know the difference between 'last' and 'lastb' ?

'last' reads /var/log/wtmp, and shows successful logins.
'lastb' reads **/var/log/btmp**, and shows unsuccessful logins.

Furthermore, I didn't ask "how do I see a list of who logged in recently."  I asked "how do I get ssh to add to btmp," which, since you must already know the purpose of /var/log/btmp either from the examples I described or by typing "[tt]man last[/tt]", would only be unsuccessful login attempts.

I already said in my first post that 'lastb' works properly.  The issue is that sshd isn't adding records to /var/log/btmp.  If you think I'm being unclear, look at the subject line of this thread again.

---

### Post by cariboo on 2011-03-27
If you are trying to see if bad logins aren't logged, why not use better examples, I see nothing about a bad ssh login in any of your examples. As far as I know bad ssh login attempts aren't logged in btmp. They are logged in /var/log/auth.log:

```
cat /var/log/auth.log | grep cariboo
Mar 27 12:44:08 chilanko sshd[20207]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=alexis  user=cariboo
Mar 27 12:44:10 chilanko sshd[20207]: **Failed password for cariboo from 192.168.1.225 port 40425 ssh2**
Mar 27 12:44:15 chilanko sshd[20207]: pam_sm_authenticate: username = [cariboo]
Mar 27 12:44:15 chilanko sshd[20207]: Accepted password for cariboo from 192.168.1.225 port 40425 ssh2

```

**Edit** After some more checking, it looks like it is only Debian/Ubuntu that don't log bad ssh logins. It may be time to file a bug. Now to change the openssh-server back to key based logins. :)

---

### Post by Mozai on 2011-03-27
> **cariboo907 said:**
> I see nothing about a bad ssh login in any of your examples.

Then you didn't look at the third line of the first example.
```
equius:~$ ssh asdf@localhost
```

Maybe I should've been more explicit by stating that 'asdf' is not a valid username on this host.

> **cariboo907 said:**
> ... it looks like it is only Debian/Ubuntu that don't log bad ssh logins *to /var/log/btmp*. It may be time to file a bug.

Thought so.  I've seen questions about this issue dating back to 2007, so I wanted to check with the community first to make sure I wasn't missing something.  Most Linuxes I've used, /var/log/wtmp is a record of valid logins & system restarts, and /var/log/btmp is for invalid logins attempts.  Some tools for blackballing brute-force password attempts will check on /var/log/btmp to see who's being naughty.

> **cariboo907 said:**
> Now to change the openssh-server back to key based logins.
Ah, but if they got in, that would be in wtmp, not btmp.  If I put 'PasswordAuthentication no' in /etc/sshd/sshd_config, I expect it will still append the invalid login attempts to /var/log/btmp.

***> but why not (a) whitelist known friendly servers (b) make sshd listen on an alternate TCP port (c) something else so dictionary attacks won't clog up your logfiles?***

Because dictionary attacks are one of a handful of ways idiots will attempt to break in, and the easiest to detect.  If I detect multiple invalid logins, I can blackball that IP address and put a stop to any other ways they will try to break into my machine.  sshd is the bait and /var/log/btmp database is more efficient to parse than text files.

***> It would be more efficient if you used 'iptables -m recent' ***

I know I know, but I'm on a VPS and the kernel pushed on me by the host machine doesn't have hooks for libxt_recent.so.  I filed a bug with the hosting company but I don't know if they'll ever get back to me. :(

---

### Post by Mozai on 2011-03-27
Filed the bug.
[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/743858](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/743858)

I don't know how to mark this thread as "resolved but not solved."

---

### Post by cariboo on 2011-03-27
I'd suggest leaving it open, in case others may want to chime in. BTW my personal server will never be open to the internet, I'm just lazy, and it easier to use public/private keys to log in.

---

