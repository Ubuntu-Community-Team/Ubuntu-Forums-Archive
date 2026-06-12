---
title: "ssh to 2 machines behind firewall"
date: 2009-08-28
forum: Server Platforms
---

### Post by Adina on 2009-08-28
just a quick question. I have 2 machines on a lan behind a monowall. I have configured ssh on both machines to listen on different ports (none of them is 22). I can connect with ssh to both machines no problem. I just wonder if this is the normal way to do this. I mean connect to the public ip/domain on the monowall wan port and use different port number to separate between the 2 machines on the lan subnet. Is this the way you guys do this?

---

### Post by volkswagner on 2009-08-28
You could reduce your risk by limiting access to one machine.  Once you ssh into machine1, you can ssh to machine2 from machine1.

Just a thought.

---

### Post by SoulMazer on 2009-08-28
Yeah, that's how I do mine. As for security, I disable root login and reduce the number of MaxStartups.

---

