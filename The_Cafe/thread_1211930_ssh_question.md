---
title: "ssh question"
date: 2009-07-13
forum: The Cafe
---

### Post by SpriteSODA on 2009-07-13
Hi guys, I've got a tricky problem: I was granted access to a server via ssh. the server has other servers connected to it, and in order to access them, i do it with an ssh connection inside the ssh, visualization:

my prompt> ssh server.server.com
      server> ssh server2
        server2> ..

How can I access server2 with a graphical sftp application?

---

### Post by ssam on 2009-07-13
these might help you

[https://www.nbcr.net/pub/wiki/index.php?title=SSH%2C_SCP_Tunneling](https://www.nbcr.net/pub/wiki/index.php?title=SSH%2C_SCP_Tunneling)
and
[http://www.taclug.org/wiki/SSH](http://www.taclug.org/wiki/SSH)

---

### Post by sanemanmad on 2009-07-13
You can port forward.
```

serv1> ssh -L 22:localhost:2222 server.server.com
serv2> ssh -L 2222:localhost:22 server2
```

Now you can use sftp://localhost like normal and all should work

---

