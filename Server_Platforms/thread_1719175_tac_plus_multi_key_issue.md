---
title: "tac_plus multi key issue"
date: 2011-04-01
forum: Server Platforms
---

### Post by blakestock on 2011-04-01
Hi everyone,

I'm trying to set up a tacacs server using Ubuntu 10.10 server and I've run into an issue I'm having a hard time finding a work around.

The issue is that for my use we have a lot of different network devices deployed using one of 4 different keys to authenticate the connection to our current TACACS+ server.  While trying to add these keys to the tac_plus.conf file and restarting the service, it would spit an error back at me and say "Error: multiply defined key on lines 10 and 11" and fail the restart of the service to apply the changes.

Is there any way around this? :confused:  Thanks in advanced!

---

