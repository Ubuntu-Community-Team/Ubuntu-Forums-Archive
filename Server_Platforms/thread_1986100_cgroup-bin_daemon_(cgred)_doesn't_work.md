---
title: "cgroup-bin daemon (cgred) doesn't work"
date: 2012-05-24
forum: Server Platforms
---

### Post by ocwo92 on 2012-05-24
I can't get the cgred daemon, which applies control group rules, to work.

My cgroup environment appears to be fine; at least cgexec applies the proper control groups as expected. However, the cgred daemon seems to completely ignore the rules.

The /etc/cgrules.conf file contains:

```
testuser:unrar     cpu     batchjob/
```

and when the cgred daemon is started in debug mode, it reveals that it parses the rule:

```
testuser@home:$ sudo cgrulesengd -d
CGroup Rules Engine Daemon log started
Current time: Thu May 24 13:43:20 2012

Opened log file: -, log facility: 0, log level: 7
Proceeding with PID 23393
Rule: testuser:unrar
  UID: 1000
  GID: N/A
  DEST: batchjob/
  CONTROLLERS:
    cpu

Started the CGroup Rules Engine Daemon.
  :
```

However, when testuser starts an unrar command that lasts several minutes, the cgrulesengd log shows no indication whatsoever that unrar is being run, let alone being classified as cpu:batchjob.

The log does indicate that cgrulesengd receives some events (apparently making it unrelated to [this bug]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=609004")), because it contains output such as:

```
Cgroup change for PID: 24935, UID: 118, GID: 126, PROCNAME: /usr/lib/nagios/plugins/check_all_procr.sh OK
EXEC Event: PID = 24938, tGID = 24938
Cgroup change for PID: 24938, UID: 118, GID: 126, PROCNAME: /usr/bin/tr OK
EXEC Event: PID = 24939, tGID = 24939
Cgroup change for PID: 24939, UID: 118, GID: 126, PROCNAME: /usr/bin/wc OK
EXEC Event: PID = 24942, tGID = 24942
Cgroup change for PID: 24942, UID: 118, GID: 126, PROCNAME: /usr/bin/tr OK
EXEC Event: PID = 24943, tGID = 24943
Cgroup change for PID: 24943, UID: 118, GID: 126, PROCNAME: /bin/ps OK
```

But, no mention of unrar. How do I make it work?

---

### Post by ocwo92 on 2012-05-24
I got a little closer to the reason why the rules daemon fails. I notized that with unzip instead of unrar, the process is recognized and reclassified. The reason seems to be that unrar is part of the alternatives system, that is, /usr/bin/unrar is a symbolic link to /etc/alternatives/unrar, which in turn is a symbolic link to /usr/bin/unrar-nonfree. So, by entering unrar-nonfree in the rules file and executing unrar-nonfree instead of unrar, the process is recognized by cgred and reclassified.

However, I have to call unrar-nonfree explicitly; it doesn't suffice to enter unrar-nonfree in the rules file.

How might I work around this problem?

---

### Post by ocwo92 on 2012-05-24
Bingo. [According to some emails on the libcg development list]("http://www.mail-archive.com/libcg-devel@lists.sourceforge.net/msg03253.html"), the rules engine daemon doesn't handle symbolic links properly.

Hopefully the fix will be included soon in the Ubuntu repositories; in the meantime I might want to build the package myself and include the patch.

---

### Post by ocwo92 on 2012-05-25
> **ocwo92 said:**
> in the meantime I might want to build the package myself and include the patch.

And so, version 0.83rc1 of the libcgroup1 package is now available as a PPA here: [https://launchpad.net/~ole.wolf/+archive/libcgroup](https://launchpad.net/~ole.wolf/+archive/libcgroup). Note that this package include the daemons otherwise found in the cgroup-bin package in the current distribution.

Edit: as of this writing, the repository doesn't seem to have published the files yet. I'm sure this will happen within a few hours.

---

