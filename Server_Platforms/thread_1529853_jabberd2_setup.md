---
title: "jabberd2 setup?"
date: 2010-07-12
forum: Server Platforms
---

### Post by rekahsoft on 2010-07-12
Alright so i have been trying to setup a XMPP server for internal chat for a small company..now my issue is i can't get any of componants to connect to the jabberd2-router..I have done the nessessary modification of the xml files in /etc/jabberd2 but i can't figure out what is wrong. Is this a bug or is it a configuration issue (my assumtion is the later). Here are the logs:

Log from /var/log/jabberd2/sm.log
```
Mon Jul 12 19:44:52 2010 [notice] starting up
Mon Jul 12 19:44:52 2010 [notice] id: rekahsoft
Mon Jul 12 19:44:52 2010 [info] process id is 32313, written to /var/run/jabberd2/sm.pid
Mon Jul 12 19:44:52 2010 [info] loading 'mysql' storage module
Mon Jul 12 19:44:52 2010 [notice] initialised storage driver 'mysql'
Mon Jul 12 19:44:52 2010 [notice] modules search path: /usr/lib/jabberd2
Mon Jul 12 19:44:52 2010 [notice] module 'status' added to chain 'sess-start' (order 0 index 0 seq \
0)
Mon Jul 12 19:44:52 2010 [notice] module 'status' added to chain 'sess-end' (order 0 index 0 seq 1)
Mon Jul 12 19:44:52 2010 [notice] module 'iq-last' added to chain 'sess-end' (order 1 index 1 seq 0\
)
Mon Jul 12 19:44:52 2010 [notice] module 'validate' added to chain 'in-sess' (order 0 index 2 seq 0\
)
Mon Jul 12 19:44:52 2010 [notice] module 'status' added to chain 'in-sess' (order 1 index 0 seq 2)
Mon Jul 12 19:44:52 2010 [notice] module 'privacy' added to chain 'in-sess' (order 2 index 3 seq 0)
Mon Jul 12 19:44:52 2010 [notice] module 'roster' added to chain 'in-sess' (order 3 index 4 seq 0)
Mon Jul 12 19:44:52 2010 [notice] module 'vacation' added to chain 'in-sess' (order 4 index 5 seq 0\
)
Mon Jul 12 19:44:52 2010 [notice] module 'iq-vcard' added to chain 'in-sess' (order 5 index 6 seq 0\
)
Mon Jul 12 19:44:52 2010 [notice] module 'iq-ping' added to chain 'in-sess' (order 6 index 7 seq 0)
Mon Jul 12 19:44:52 2010 [notice] module 'iq-private' added to chain 'in-sess' (order 7 index 8 seq\
 0)
Mon Jul 12 19:44:52 2010 [notice] module 'disco' added to chain 'in-sess' (order 8 index 9 seq 0)
Mon Jul 12 19:44:52 2010 [notice] module 'amp' added to chain 'in-sess' (order 9 index 10 seq 0)
Mon Jul 12 19:44:52 2010 [notice] module 'offline' added to chain 'in-sess' (order 10 index 11 seq \
0)
Mon Jul 12 19:44:52 2010 [notice] module 'announce' added to chain 'in-sess' (order 11 index 12 seq\
 0)
Mon Jul 12 19:44:52 2010 [notice] module 'presence' added to chain 'in-sess' (order 12 index 13 seq\
 0)
Mon Jul 12 19:44:52 2010 [notice] module 'deliver' added to chain 'in-sess' (order 13 index 14 seq \
0)
Mon Jul 12 19:44:52 2010 [notice] module 'session' added to chain 'in-router' (order 0 index 15 seq\
 0)
Mon Jul 12 19:44:52 2010 [notice] module 'validate' added to chain 'in-router' (order 1 index 2 seq\
 1)
Mon Jul 12 19:44:52 2010 [notice] module 'presence' added to chain 'in-router' (order 2 index 13 se\
q 1)
Mon Jul 12 19:44:52 2010 [notice] module 'privacy' added to chain 'in-router' (order 3 index 3 seq \
1)
Mon Jul 12 19:44:52 2010 [notice] module 'privacy' added to chain 'out-router' (order 0 index 3 seq\
 2)
Mon Jul 12 19:44:52 2010 [notice] module 'iq-last' added to chain 'pkt-sm' (order 0 index 1 seq 1)
Mon Jul 12 19:44:52 2010 [notice] module 'iq-ping' added to chain 'pkt-sm' (order 1 index 7 seq 1)
Mon Jul 12 19:44:52 2010 [notice] module 'iq-time' added to chain 'pkt-sm' (order 2 index 16 seq 0)
Mon Jul 12 19:44:52 2010 [notice] module 'iq-version' added to chain 'pkt-sm' (order 3 index 17 seq\
 0)
Mon Jul 12 19:44:52 2010 [notice] module 'amp' added to chain 'pkt-sm' (order 4 index 10 seq 1)
Mon Jul 12 19:44:52 2010 [notice] module 'deliver' added to chain 'pkt-user' (order 4 index 14 seq \
1)
Mon Jul 12 19:44:52 2010 [notice] module 'vacation' added to chain 'pkt-user' (order 5 index 5 seq \
1)
Mon Jul 12 19:44:52 2010 [notice] module 'offline' added to chain 'pkt-user' (order 6 index 11 seq \
1)
Mon Jul 12 19:44:52 2010 [notice] module 'disco-publish' added to chain 'pkt-user' (order 7 index 2\
0 seq 0)
Mon Jul 12 19:44:52 2010 [notice] module 'iq-last' added to chain 'pkt-user' (order 8 index 1 seq 2\
)
Mon Jul 12 19:44:52 2010 [notice] module 'session' added to chain 'pkt-router' (order 0 index 15 se\
q 1)
Mon Jul 12 19:44:52 2010 [notice] module 'disco' added to chain 'pkt-router' (order 1 index 9 seq 2\
)
Mon Jul 12 19:44:52 2010 [notice] module 'active' added to chain 'user-load' (order 0 index 21 seq \
0)
Mon Jul 12 19:44:52 2010 [notice] module 'roster' added to chain 'user-load' (order 1 index 4 seq 2\
)
Mon Jul 12 19:44:52 2010 [notice] module 'roster-publish' added to chain 'user-load' (order 2 index\
 22 seq 0)
Mon Jul 12 19:44:52 2010 [notice] module 'privacy' added to chain 'user-load' (order 3 index 3 seq \
3)
Mon Jul 12 19:44:52 2010 [notice] module 'disco-publish' added to chain 'user-load' (order 4 index \
20 seq 1)
Mon Jul 12 19:44:52 2010 [notice] module 'vacation' added to chain 'user-load' (order 5 index 5 seq\
 2)
Mon Jul 12 19:44:52 2010 [notice] module 'active' added to chain 'user-create' (order 0 index 21 se\
q 1)
Mon Jul 12 19:44:52 2010 [notice] module 'template-roster' added to chain 'user-create' (order 1 in\
dex 23 seq 0)
Mon Jul 12 19:44:52 2010 [notice] module 'active' added to chain 'user-delete' (order 0 index 21 se\
q 2)
Mon Jul 12 19:44:52 2010 [notice] module 'announce' added to chain 'user-delete' (order 1 index 12 \
seq 2)
Mon Jul 12 19:44:52 2010 [notice] module 'disco-publish' added to chain 'user-delete' (order 2 inde\
x 20 seq 2)
Mon Jul 12 19:44:52 2010 [notice] module 'offline' added to chain 'user-delete' (order 3 index 11 s\
eq 2)
Mon Jul 12 19:44:52 2010 [notice] module 'privacy' added to chain 'user-delete' (order 4 index 3 se\
q 4)
Mon Jul 12 19:44:52 2010 [notice] module 'roster' added to chain 'user-delete' (order 5 index 4 seq\
 3)
Mon Jul 12 19:44:52 2010 [notice] module 'vacation' added to chain 'user-delete' (order 6 index 5 s\
eq 3)
Mon Jul 12 19:44:52 2010 [notice] module 'status' added to chain 'user-delete' (order 7 index 0 seq\
 4)
Mon Jul 12 19:44:52 2010 [notice] module 'iq-last' added to chain 'user-delete' (order 8 index 1 se\
q 3)
Mon Jul 12 19:44:52 2010 [notice] module 'iq-private' added to chain 'user-delete' (order 9 index 8\
 seq 1)
Mon Jul 12 19:44:52 2010 [notice] module 'iq-vcard' added to chain 'user-delete' (order 10 index 6 \
seq 2)
Mon Jul 12 19:44:52 2010 [notice] module 'iq-version' added to chain 'disco-extend' (order 0 index \
17 seq 1)
Mon Jul 12 19:44:52 2010 [notice] module 'help' added to chain 'disco-extend' (order 1 index 18 seq\
 1)
Mon Jul 12 19:44:52 2010 [notice] version: jabberd2 sm 2.2.8
Mon Jul 12 19:44:52 2010 [notice] attempting connection to router at 127.0.0.1, port=5423
Mon Jul 12 19:44:52 2010 [notice] connection to router established
Mon Jul 12 19:44:52 2010 [notice] router refused bind request (403)
```

Log from /var/log/jabberd2/s2s.log
```
Mon Jul 12 19:44:52 2010 [notice] starting up (interval=60, queue=60, keepalive=0, idle=86400)
Mon Jul 12 19:44:52 2010 [info] process id is 32318, written to /var/run/jabberd2/s2s.pid
Mon Jul 12 19:44:52 2010 [notice] attempting connection to router at 127.0.0.1, port=5423
Mon Jul 12 19:44:52 2010 [notice] connection to router established
Mon Jul 12 19:44:52 2010 [notice] router refused bind request (403)
```

Log from /var/log/jabberd2/router.log
```
Mon Jul 12 19:44:52 2010 [notice] starting up
Mon Jul 12 19:44:52 2010 [info] process id is 32307, written to /var/run/jabberd2/router.pid
Mon Jul 12 19:44:52 2010 [notice] loaded user table (1 users)
Mon Jul 12 19:44:52 2010 [notice] loaded filters (0 rules)
Mon Jul 12 19:44:52 2010 [notice] [0.0.0.0, port=5423] listening for incoming connections
Mon Jul 12 19:44:52 2010 [notice] [127.0.0.1, port=43681] connect
Mon Jul 12 19:44:52 2010 [notice] [127.0.0.1, port=43681] authenticated as rekd@jabberd-router
Mon Jul 12 19:44:52 2010 [notice] [127.0.0.1, port=43681] tried to bind 'rekahsoft', but their user\
name (rekd) is not permitted to bind other names
Mon Jul 12 19:44:52 2010 [notice] [127.0.0.1, port=43682] connect
Mon Jul 12 19:44:52 2010 [notice] [127.0.0.1, port=43682] authenticated as rekd@jabberd-router
Mon Jul 12 19:44:52 2010 [notice] [127.0.0.1, port=43682] tried to bind 'rekahsoft', but their user\
name (rekd) is not permitted to bind other names
Mon Jul 12 19:44:52 2010 [notice] [127.0.0.1, port=43683] connect
Mon Jul 12 19:44:52 2010 [notice] [127.0.0.1, port=43683] authenticated as rekd@jabberd-router
Mon Jul 12 19:44:52 2010 [notice] [127.0.0.1, port=43683] tried to bind 'rekahsoft', but their user\
name (rekd) is not permitted to bind other names
Mon Jul 12 19:44:52 2010 [notice] [127.0.0.1, port=43681] disconnect
Mon Jul 12 19:44:52 2010 [notice] [127.0.0.1, port=43682] disconnect
Mon Jul 12 19:44:52 2010 [notice] [127.0.0.1, port=43683] disconnect
```

Log from /var/log/jabberd2/c2s.log
```
Mon Jul 12 19:44:52 2010 [notice] starting up
Mon Jul 12 19:44:52 2010 [info] process id is 32323, written to /var/run/jabberd2/c2s.pid
Mon Jul 12 19:44:52 2010 [notice] modules search path: /usr/lib/jabberd2
Mon Jul 12 19:44:52 2010 [info] loading 'mysql' authreg module
Mon Jul 12 19:44:52 2010 [notice] initialized auth module 'mysql'
Mon Jul 12 19:44:52 2010 [notice] [localhost.localdomain] configured; realm=localhost.localdomain, \
registration enabled
Mon Jul 12 19:44:52 2010 [notice] attempting connection to router at 127.0.0.1, port=5423
Mon Jul 12 19:44:52 2010 [notice] connection to router established
Mon Jul 12 19:44:52 2010 [error] router refused bind request (403)
```

If you need more info about my configuation feel free to ask. Currently i have it setup for mysql authentication and storage...i actually would like to either disable logging or perhaps do temorary logging? I also would like to know the most secure way to setup a jabber server...i'm thinking maybe tunneling  using ssh or afaik jabberd2 has support for ssl/tls? How to i set this up? I found that there is very little documentation for jabberd2. Thanks for the help; Regards rekahsoft

*EDIT*: i forgot to mention i am running ubuntu 10.04 LTS :P

---

### Post by Fatman_UK on 2010-07-28
I'm looking for Jabberd2 docs myself. No luck yet.

SSH is awesome, but I try not to tunnel TCP connections over it. Why? Because SSH itself uses TCP, and TCP over TCP gets nasty when packets start dropping. I prefer TCP over UDP. Check out OpenVPN for setting up a UDP tunnel. It's a more complete solution for tunnelling than SSH anyway.

```
router refused bind request (403)
```

Looks like the geniuses who wrote Jabberd2 reused TCP terminology and HTTP error codes. That'll make it even harder to get help. :( 

What's that 'bind' stuff happening with 'rekahsoft' and 'rekd' in router.log?

TLS is so easy to set up. I have it enabled on my c2s right now. It's all done in the <local> part of c2s.xml. My <id> tag looks like this:

```
<id pemfile='/etc/ssl-certs/jabber.pem' instructions='false' require-starttls='true' register-enable='true'>my.jabber.tld</id>
```

That's it my friend. That's the whole thing. (Change "my.jabber.tld" to your server's domain.) You can add

```
<ssl-port>5223</ssl-port>
<pemfile>/etc/ssl-certs/jabber.pem</pemfile>
```

if you like, but these last two lines are only for old-style SSL connections. So you would leave these lines out because you want as secure a setup as possible.

---

### Post by w2vy on 2010-08-23
> **Fatman_UK said:**
> I'm looking for Jabberd2 docs myself. No luck yet.


[Jabberd 2 Doc Project]("http://www.jabberdoc.org/FrontPage")

I just started working on it...

It seems when you install jabberd2 it does not create a mysql db
so I am not looking for the setup file mentioned in the docs

tom

---

