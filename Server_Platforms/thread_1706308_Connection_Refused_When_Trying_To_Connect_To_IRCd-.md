---
title: "Connection Refused When Trying To Connect To IRCd-Hybrid"
date: 2011-03-13
forum: Server Platforms
---

### Post by nathanpc on 2011-03-13
I have a Rackspace server running Ubuntu Lucid Lynx, where I have installed an IRCd-Hybrid. I can connect to the IRC server using irssi that was installed on the same machine where the server is, but when I try to access it from my computer at home or my friends try I get this error:
```
Connection Refused
```
What should I do?

---

### Post by dumpster25 on 2011-07-31
You gotta change the ircd.conf file and set that users should be allowed to connect from other ip-addresses

---

