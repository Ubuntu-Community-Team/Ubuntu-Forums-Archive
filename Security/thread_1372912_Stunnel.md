---
title: "Stunnel"
date: 2010-01-05
forum: Security
---

### Post by cucuru on 2010-01-05
hello, I'm trying connect two computers with stunnel (I have to connect more than one, but I'm starting)

What I want:

Connect the computer as in ssh mode, I mean, I use a console in my local computer to do operation in the remote.

What I have:

I commented all the connection preconfigurated in stunnel.conf and put a new one:

```

[tunnelSSL]
accept = localhost:5544
connect = xx.xx.xx.xx:4455

```

the same in both computers but changing the port number.

with netstat I saw that there isn't any connection, so I tried the example in the web page:

[http://www.stunnel.org/examples/generic_tunnel.html](http://www.stunnel.org/examples/generic_tunnel.html)

But nothing. What is my problem? 

Thank you. Regards

---

