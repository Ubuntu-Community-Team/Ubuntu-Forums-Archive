---
title: "FreeNX - how to avoid multiple concurrent sessions for a remote user"
date: 2007-04-28
forum: Server Platforms
---

### Post by destr0y on 2007-04-28
Hi all,

I've discovered the awesome FreeNX as a means of remotely accessing my Fiesty box.  Quite simply, its awesome, its exactly what I've been looking for (remote terminal for multiple users).  The only problem I've got with it, is that if a user doesn't log their X session out, it just sticks around.  Any subsequent FreeNX login (for the same user) results in a new X session, while their orphaned one just sits there consuming RAM.... I'm running Fiesty on a p3 500mhz compaq armada laptop, with 256mb ram.  As you can guess, there ain't too much RAM to begin with :)  

Is there a way to force FreeNX to reconnect back to a previously orphaned session?  if not, how can I expire an orphaned session and automatically force it to be logged off/reset?

Cheers,
Brett

---

### Post by taenus on 2007-04-30
I have not personally used FreeNX, but I administer a NoMachine ("real NX") custer.  This may not apply, but the following may help.

/usr/NX/etc/node.cfg
    # this obscure bit add a time out to disconnect idle sessions.
    AGENT_EXTRA_OPTIONS_X = "-timeout 4800"

/usr/NX/etc/server.cfg
    # Set the maximum number of concurrent NX sessions that can be run by
    # a single user.
    SESSION_USER_LIMIT = "2"

---

