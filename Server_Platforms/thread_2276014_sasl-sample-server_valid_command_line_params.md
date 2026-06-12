---
title: "sasl-sample-server: valid command line params?"
date: 2015-04-29
forum: Server Platforms
---

### Post by Fraaik on 2015-04-29
Hi ervyone!

One of my servers is "Ubuntu 12.04.5 LTS".
There I've installed sasl2-bin (sasl2-bin_2.1.25.dfsg1-3ubuntu0.1_amd64.deb). 
All is ok so far.

But when I try to test the sasl-sample-server/sasl-sample-client with
command lines like one find everywhere that is

```
sasl-sample-server -s rcmd -p 8000
```

it crashes with

```
sasl-sample-server: SASL Other: Internal Error -4 in ../../lib/server.c near line 1753
sasl-sample-server: SASL Other: Internal Error -4 in ../../lib/server.c near line 1753
sasl-sample-server: SASL Other: Internal Error -4 in ../../lib/server.c near line 1753
sasl-sample-server: Generating client mechanism list: no mechanism available
```

A look at the manpage says: "-p PATH colon-seperated search path for mechanisms"
Ok, it seems all people refer to an older version of sasl-sample-server.

My question: where can I get more information than from manpage?

How can I define on which port the server should listen?
Again manpage says: -i local=IP;PORT set local address to IP, port PORT

But for me the does not work. Server starts with

```
Generating client mechanism list...
Sending list of 4 mechanism(s)
S: UExBSU.......ULU1ENQ==
Waiting for client mechanism...
```

Starting client on the other hand:

```
service=rcmd
Waiting for mechanism list from server...
```


What goes on here?
Any idea?

Ervery hint is welcom!

---

