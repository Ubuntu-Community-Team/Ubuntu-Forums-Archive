---
title: "unreadable huge cups/error_log (400MB??)"
date: 2007-09-12
forum: Server Platforms
---

### Post by gerbazio on 2007-09-12
Hi everybody,

I've found a huge logfile in my /var/log/cups directory:

-rw-r--r-- 1 cupsys lp 443736220 2007-09-12 11:47 error_log

it can't be read (appears empty with "more" and binary with "less")

all old (logrotated) copies are very small (few hundreds bytes) and readable

What can be the cause?? How can I read this file?

thanks a lot

 andrea

---

### Post by craigp84 on 2007-09-12
Ok, clearly something's gone wrong here! Are there any clues in other log files such as syslog/messages or i guess any other logs under /var/log may just hold a clue.

You can use tail and head from the command line to view parts of the file, or alternatively you could use vim (easier).

You say it appears to be binary content, that suggests cups went through a code path it shouldn't have, possibly someone has tried to make it do this - does your cups daemon listen on the network at large, or just 127.0.0.1? It's possible someone's sent junk to cups in an attempt to cause a buffer overflow or similar. This would be serious as potentially this could be a vehicle for an attack of some sort.

Use the "last" command to try to track down who was logged on at the time, do they have any clues?

Do you have the sysstat package installed (if not, go do it now! :-) ) - maybe there are some abnormal profiles in network traffic or disk/cpu usage around the time of the binary blob in the log file?

Other than that, i guess you could try to recreate the issue. Can you mimick the workload you expect would have been present at the time of the blob? Can you attempt to trace through what happened that way?

Are there any core files have been created? i.e. was cups down and that's why you noticed this log file?

Bit of a brain dump but hope this helps.

-c

---

