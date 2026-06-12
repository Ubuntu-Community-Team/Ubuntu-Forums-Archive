---
title: "Proftpd Time issues"
date: 2007-08-13
forum: Server Platforms
---

### Post by jsaumer on 2007-08-13
Hello,

For some reason the timestamps on my files in my proftpd server do not match to the system time on the server.

The hour is 5 hours ahead of what it should be.

Any tips on how to resolve this?

Thanks,
jsaumer

---

### Post by a9k on 2007-08-17
By default, ProFTPd will display times in GMT. Could that be your problem?

Look in /etc/proftpd.conf for a section labelled <global>. To show local time in the logs you would need to add a line in that section saying ```
TimesGMT off
```

Don't forget to restart the server if you change proftpd.conf

---

