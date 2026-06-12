---
title: "inotify process or user"
date: 2008-06-27
forum: Server Platforms
---

### Post by cdenley on 2008-06-27
I just discovered inotify. It will be very useful when client uploads seem to disappear. Now I will be able to tell if they were never uploaded successfully, or if someone just deleted them accidentally.
```

#!/bin/sh
LOGSIZE=500
DIRPATH=/var/uploads
while true; do
  if [ -e /var/log/uploads.log ]; then
    if [ -e /var/log/uploads.log.1 ]; then
      mv -f /var/log/uploads.log.1 /var/log/uploads.log.2
    fi
    mv -f /var/log/uploads.log /var/log/uploads.log.1
  fi
  count=0
  inotifywait -mrq --format "%+e %w%f" \
  "$DIRPATH" -e CREATE,DELETE,MOVED_FROM,MOVED_TO \
  | while [ $count -lt $LOGSIZE ] && read event file; do
      date "+%D %T,$event,$file">>/var/log/uploads.log
      count=`expr $count + 1`
  done
done

```
What inotify doesn't seem to do is tell me the name of the process or user that deleted the file. Can anyone think of any way to accomplish this?

---

### Post by cmdln on 2009-06-04
Did you ever find an answer to determining what process and user actually modified the files monitored with inotify?

---

### Post by cdenley on 2009-06-05
> **cmdln said:**
> Did you ever find an answer to determining what process and user actually modified the files monitored with inotify?

Unfortunately not.

---

### Post by pallinger on 2010-04-15
A quick-and-dirty solution is this:

iwatch -e all_events -c 'ls -lR /proc/[0-9]*/fd/* 2>/dev/null|grep $file ' $file

This way, you get the PID of the process, _if_ it has the file open long enough.

A nice solution is a patched kernel that stores the pid of the process for inotify.

---

