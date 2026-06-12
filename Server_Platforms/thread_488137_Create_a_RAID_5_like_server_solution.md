---
title: "Create a RAID 5 like server solution"
date: 2007-06-29
forum: Server Platforms
---

### Post by etechship on 2007-06-29
I am starting to work with doing open-source Flash streaming (ubuntu and red5). 

I have some new clients that would like a little bit more reliable solution for there streaming . I am wanting to build a radi5 like solution for my servers, and place them in server rooms around the midwest (US).

There are 2 set of servers to this. The Admin servers, the task servers and the side servers. I want to be able to add differant size/spec servers.

The admin servers are the servers that receive all the requests. There are 2 of them that I would like to put in a raid 1 like solution (mirroring) for the 2 of them. These will be used to create

then I will have the task servers (3+ of them) take on the data transfer, which ever one the data is on.

then the side servers are used in case of one of the task servers, or admin servers, fail. The admin server could then build one of the side servers to do the job of down task server.

I know this sounds kinda large, but it would be nice to work.

I am using ubuntu server, and I am willing to install any open-source software, as long as it doesn't create and large security risks.

So, overall, I would have at least 6 servers (look below):
admin: 2 servers
task: 3 servers
side: 1 server

thanks for any help that you can offer me.

---

