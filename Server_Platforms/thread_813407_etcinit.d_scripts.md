---
title: "/etc/init.d scripts"
date: 2008-05-30
forum: Server Platforms
---

### Post by dkasak on 2008-05-30
I'm rebuilding a server that was running email & web servers on Gentoo. I had dbmail-2.3 running. Ubuntu only packages version 2.2, and the database format has changed, meaning that I can't run a 2.2 server with my 2.3 database schema.

So I've built dbmail from source, with the options:

./configure --prefix=/usr --with-mysql --with-sieve=/usr

This went fine, and installed server binaries into /usr/sbin ... ie where the init scripts expect them.

... BUT ...

When I run '/etc/init.d/dbmail start' ***absolutely nothing*** happens ... except the init scripts ***claim*** that the daemons have been started. They don't start.

I can run dbmail-imapd manually, and it connects to my database and I can see my email in evolution. What's up with the init scripts?

Nothing is appearing in any logs. Is there a way to get some debugging info from the init scripts?

---

### Post by quelx on 2008-05-30
Are you using the version 2.2 init scripts from Ubuntu? if not would you mind posting what you are using?

---

### Post by Dr Small on 2008-05-30
Check the source of the init script to see how it is starting the daemon. If you see it is wrong, correct the problem.

---

### Post by dkasak on 2008-05-30
> **quelx said:**
> Are you using the version 2.2 init scripts from Ubuntu? if not would you mind posting what you are using?

Yeah I'm using the 2.2 init script ( which wasn't removed when I removed the dbmail package ). AFAIK when I updated from 2.2 to 2.3 on Gentoo I used the same startup script. Also, there is no Ubuntu script in the 'contrib' folder in the source. There are Gentoo init scripts ...

No. Wait. There is a Debian init script in the debian folder. It's basically exactly the same as the one I'm now using:

```
dan@centenitos:/usr/src/dbmail-2.3.2/debian$ diff dbmail.init /etc/init.d/dbmail 
49c49
< 	mkdir -p -m 0755 ${PID_DIR}
---
>         mkdir -p -m 0755 ${PID_DIR}
52a53
> 
dan@centenitos:/usr/src/dbmail-2.3.2/debian$ 
```

Anyway, I'd like to know more about the init scripts under Ubuntu. Is it possible to make them log somewhere, and turn up the verbosity? Under Gentoo, the start-stop-daemon logs to syslog.

---

### Post by quelx on 2008-05-30
**/etc/syslog.conf** controls what gets logged and its verbosity.  The rest are controlled by their respective **.conf** files...  Not a good answer...  Have you tried debugging the init script by hand, or visually trace it, (whatever that's called) to see that it's hitting the daemon start command?

---

### Post by pr144 on 2008-06-30
> **dkasak said:**
> I'm rebuilding a server that was running email & web servers on Gentoo. I had dbmail-2.3 running. Ubuntu only packages version 2.2, and the database format has changed, meaning that I can't run a 2.2 server with my 2.3 database schema.

So I've built dbmail from source, with the options:

./configure --prefix=/usr --with-mysql --with-sieve=/usr

This went fine, and installed server binaries into /usr/sbin ... ie where the init scripts expect them.

... BUT ...

When I run '/etc/init.d/dbmail start' ***absolutely nothing*** happens ... except the init scripts ***claim*** that the daemons have been started. They don't start.

I can run dbmail-imapd manually, and it connects to my database and I can see my email in evolution. What's up with the init scripts?

Nothing is appearing in any logs. Is there a way to get some debugging info from the init scripts?


I recently converted from Fedora to Ubuntu and I am having the same problem...did you resolve this issue?


Peter

---

