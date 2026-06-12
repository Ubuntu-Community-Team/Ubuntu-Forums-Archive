---
title: "Ubuntu One exclude/ignore folder"
date: 2012-01-19
forum: Ubuntu One (CLOSED)
---

### Post by Frozen Forest on 2012-01-19
It's possible to ignore folders with Ubuntu One? I found these links regarding the subject
[http://askubuntu.com/questions/26658/is-it-possible-to-exclude-a-file-or-folder-from-being-synced-while-it-is-in-a-d](http://askubuntu.com/questions/26658/is-it-possible-to-exclude-a-file-or-folder-from-being-synced-while-it-is-in-a-d)
[http://ubuntuforums.org/showthread.php?t=1581747](http://ubuntuforums.org/showthread.php?t=1581747)
First link give an example in how to ignore files, when I tried this for a folder did I get the following error message. The second link give an explanation regarding the problem with excluding folder but it's from 2010 and I was hoping it would have changed but now, has it?

Also found this bug report [https://bugs.launchpad.net/ubuntuone-client/+bug/484204](https://bugs.launchpad.net/ubuntuone-client/+bug/484204) but this also is quite old.

Added lines
```

\A.metadata\Z
\A\.metadata\Z # tried also
\Abin\Z

```Error message
```

Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntuone-client/ubuntuone-syncdaemon exited with status 1

```

---

### Post by oldos2er on 2012-01-19
Moved to Ubuntu One.

---

