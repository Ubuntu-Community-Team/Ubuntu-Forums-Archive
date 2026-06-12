---
title: "Samba sharing a subdirectory in a private directory?"
date: 2009-04-15
forum: Server Platforms
---

### Post by wkulecz on 2009-04-15
I have a private home directory permissions 700.  Inside this I have a directory I'd like to share that is 775 user.group me.sambauser  Samba advertises it, but I get not accessible error "The network name cannot be found".

Two other shares user.group sambauser.sambauser are shared correctly, although these are on another filesystem.

I have:
valid users = sambauser 
in all the stanzas 

and:
force user = me
force group sambauser
in the stanza for the share within the private sub directory.

What is really making zero sense, is occasionally it will connect.

--wally.

---

### Post by wkulecz on 2009-04-16
I posted this message and went home in frustration with access denied.

Come in this morning, it works fine.

Perhaps some state is maintained on the Windows side for a time that is not flushed when I do /etc/init.d/samba restart

Question is will it be fubar again after I reboot either or both machines?

--wally.

---

