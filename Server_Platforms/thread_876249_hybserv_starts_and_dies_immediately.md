---
title: "hybserv starts and dies immediately"
date: 2008-07-31
forum: Server Platforms
---

### Post by tsudonymn on 2008-07-31
I've setup a ircd-hybrid 7.x.x server on Hardy and I wanted to setup Hybserv2 for the IRC services. Both were installed via synaptic. The ircd-hybrid server is up and running but when I start hybserv it dies imediately. The hybserv log show only

```

root@ghost:/etc/hybserv# tail -f /var/log/ircd/hybserv.log 
Thu Jul 31 14:45:10 2008 Hybserv2 TS services version 1.9.2-debian-4 started
Thu Jul 31 14:45:45 2008 Hybserv2 TS services version 1.9.2-debian-4 started
Thu Jul 31 14:45:55 2008 Hybserv2 TS services version 1.9.2-debian-4 started

```

At first the command returned the following:

```

irc@ghost:/etc/hybserv$ hybserv
Hybserv2 TS services version 1.9.2-debian-4 by Hybserv2 team
Compiled at Nov  8 2006, 14:26:32
WARNING: Unable to read pid file /var/run/ircd/hybserv.pid
No users (O:) specified for access to services in /etc/hybserv/hybserv.conf (at least one user should be added)

```

So I touched the pid file and made sure it was owned by irc/irc via:

```

root@ghost:~# touch /var/run/ircd/hybserv.pid
root@ghost:~# chown irc /var/run/ircd/hybserv.pid
root@ghost:~# chgrp irc /var/run/ircd/hybserv.pid

```

That gets rid of the warning but hybserv still dies...

For reference yes there are O: lines...

```

irc@ghost:/etc/hybserv$ cat hybserv.conf|grep O:
# O: lines specify users who will have access to Hybserv.  The first
O:tsudonymn@ghost:AnEncryptedPass:segj

```

strace shows hybserv reading from /etc/hybserv/hybserv.conf

```

open("/etc/hybserv/hybserv.conf", O_RDONLY|O_LARGEFILE) = 3
fstat64(3, {st_mode=S_IFREG|0660, st_size=5591, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fc9000
read(3, "# The .include directive is avai"..., 4096) = 4096
read(3, ", and the type of connection to "..., 4096) = 1495
read(3, "", 4096)                       = 0
close(3)                                = 0

```

I suspect if I could figure out why it thinks there are no O: lines it would start fine but that's only because it's beating me over the head with that message and dying.

So I'm stumped and hoping someone else has a clue cause there is very little about hybserv2 to be found via google. Certainly nothing on troubleshooting past "check the log."

Thanks in advance,
Chris

p.s.

Here's what I've used as guides thus far...

[http://hybserv2.sourceforge.net/HybservCompileAndRun](http://hybserv2.sourceforge.net/HybservCompileAndRun)

[http://hybserv2.sourceforge.net/HybservConfiguration](http://hybserv2.sourceforge.net/HybservConfiguration)

---

### Post by tsudonymn on 2008-08-01
Ahhh sometimes it just takes another pair of eyes.

So it was indeed the O: lines. Too bad Hybserv2 doesn't bother to give any meaningful feedback concerning it's log file. As it turns out there was a field missing. So for future reference to anyone else...

O:user@host:SomePassword:YourNickHere:<flags>

The flags are listed in the docs.

Hope this helps anyone else daring down the Hybserv path.

---

