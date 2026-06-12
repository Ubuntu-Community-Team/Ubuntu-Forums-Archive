---
title: "Problem with cpu 100%"
date: 2010-12-03
forum: Server Platforms
---

### Post by wenfi on 2010-12-03
Ih to everybody,
i have a problem with some process, perl and php in my webserver.
i did:
#netstat -p | grep <pid_cpu_100%>
and i notice this in the output:
Admin.channel.allexis.:ircd ESTABLISHED 7690/php

i have to worry about it?
thanks to all!!
bye

---

### Post by SeijiSensei on 2010-12-03
If you're asking this question, I take it you're not running an IRC server?

If so, you've been exploited and someone's pushing IRC traffic through your server.  

Run "ps | ax" and find the process id.  (From the message below it's probably 7690.)  Then issue "kill -9 pid" replacing pid with the actual value.  Now run "locate ircd" to track down the server and remove it.  It might be in /tmp.  One way to protect yourself from that again is to create a separate partition for /tmp and mount it noexec.

Then you need to figure out how you got exploited.  I can't answer that for you, I'm afraid.

---

### Post by wenfi on 2010-12-03
thanks for your help!!
it seems an irc web chat installed by a client in his domain.
bye

---

### Post by wenfi on 2010-12-04
can you explain why "fakeproc take so much?"
#netstat -p | grep 27950 (this pid CPU 100%)
Output: Admin.channel.allexis.:ircd ESTABLISHED 27950/fakeproc

then i did:

#locate ircd

Output:
/root/.etc/misc/ircd.conf
/usr/local/lxlabs/kloxo/httpdocs/htmllib/filecore/lxetc/misc/ircd.conf

How can understand which files are used by that process?

in "/proc/27950/fd/"
i found those elements:
pipe:[291223]
pipe:[291287]
pipe:[291287]
socket:[291304]

it seems about kloxo (panel installed in the server), so i think it's ok...do you have other ideas?
thanks in advance!

---

