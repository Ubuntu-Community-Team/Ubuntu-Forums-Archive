---
title: "Pipe stdin AND stdout via Netcat"
date: 2007-06-27
forum: Server Platforms
---

### Post by piers on 2007-06-27
This is probably a basic shell problem, but how can send and receive data via netcat so that I can interact with with an application.

In this example I want to interact with top (and only top) via a telnet app.
```
top | nc -l -p 3333
```

When I hit 'q' on the client machine I can see the 'q' appear in the remote console, but it doesn't interact with top.

Please help! :p

Thanks!

---

### Post by piers on 2007-07-11
I hope nobody minds if I bumps this ;) If this is possible then the limitations for prototyping server side software is endless.

---

