---
title: "About ssh port forwarding ."
date: 2013-10-16
forum: Server Platforms
---

### Post by prismctg on 2013-10-16
How to connect remote mysql from local phpMyadmin ? I tried many solution from google , but none of those worked for me

---

### Post by Lars Noodén on 2013-10-16
First, when you are on the remote machine can you use MySQL there?  It has to be up and running.
Second, the recipe below should work unless there is also a copy of MySQL running on the local machine.

```

ssh -L 3306:localhost:3306 prismctg@server.example.org

```

If that works as it should, all you need to do is connect to port 3306 on your local machine and it should be forwarded to the remote machnine.  

However, that's probably what you were able to find in Google already.

---

### Post by Lars Noodén on 2013-10-16
BTW your connection from the local host something like this:

```

mysql -h 127.0.0.1 -P 3306 -u myuser -p

```

As far as I know you do have to have the host named explicitly, otherwise you will get an error.

---

