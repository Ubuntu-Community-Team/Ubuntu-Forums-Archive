---
title: "[C] How can a thread exit the main program?"
date: 2010-11-24
forum: Ubuntu Dev Link Forum
---

### Post by Royk14 on 2010-11-24
Hi
I'm making a program in C wich is a server that is suppose to receive connections from several clients.
The way I have the program made now, the server will be continuously waiting for clients. So it never shuts down. When I want to shut the server down I have to do the 'Ctrl+C' in the Console.

I'm now thinking about how will I shut the server down correctly.
I was thinking about making a thread that, when there is no client connected, can be able to receive a command from the user (in the server) and shut the server down correctly.
I just don't know how can a thread do that.

Can someone help me?

---

### Post by Royk14 on 2010-11-24
I realized now that I posted this on the wrong section, and I can't delete it.

I already reposted it on the right section, so please delete this one.

---

