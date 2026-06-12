---
title: "lighttpd slow"
date: 2011-10-21
forum: Server Platforms
---

### Post by sartic on 2011-10-21
I know that I have slow internet (upload is 512kbps) but dl from my web server never reached near max (40-50KB), average is 8-12KB.
I am using pfsense as fw and nat to my web server (dynamic ip).
What can I check or do?
I moved all my big files to external mirror 4 now.

ps: all my web pages r static (i removed all dynamic modules from lighttpd).

---

### Post by sartic on 2011-10-23
Something limits bandwidth per connection in default setup.
I used dl manager to dl file over 5MB and it easy hits my ul caps.

Hints?

---

### Post by crav on 2011-10-23
Are you delivering all your http content over port 80? (the default) Many ISPs throttle or block incoming connections on port 80 to prevent you from hosting a site on your home connection. You may want to try using an alternative port if only to check whether throttling on the port may be an issue.

You've stated that your upload speed is 512 kbps. Is this the speed your ISP has *told you* you're capable of hitting, or is this a tested and confirmed speed?

---

### Post by sartic on 2011-10-24
Ul caps speed is ok. 
I will test this idea afternoon, thx.

---

