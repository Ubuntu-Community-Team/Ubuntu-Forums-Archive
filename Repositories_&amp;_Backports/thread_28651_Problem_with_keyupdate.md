---
title: "Problem with keyupdate"
date: 2005-04-21
forum: Repositories &amp; Backports
---

### Post by Spirit on 2005-04-21
I can`t update keys from keyserver 

[B]@enigma:~ # gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg: can't get key from keyserver: Connection timed out
gpg: Total number processed: 0[/B] 

I use kubuntu and few days i cant get update

---

### Post by nocturn on 2005-04-21
[QUOTE=Spirit]I can`t update keys from keyserver 

[B]@enigma:~ # gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg: can't get key from keyserver: Connection timed out
gpg: Total number processed: 0[/B] 

I use kubuntu and few days i cant get update[/QUOTE]

Are you behind a proxy?

Try 'ping wwwkeys.eu.pgp.net'

---

### Post by Spirit on 2005-04-21
Im not behind proxy

PING wwwkeys.eu.pgp.net (194.171.167.147) 56(84) bytes of data.
64 bytes from minsky.surfnet.nl (194.171.167.147): icmp_seq=1 ttl=46 time=118 ms
64 bytes from minsky.surfnet.nl (194.171.167.147): icmp_seq=2 ttl=46 time=109 ms
64 bytes from minsky.surfnet.nl (194.171.167.147): icmp_seq=4 ttl=46 time=197 ms
64 bytes from minsky.surfnet.nl (194.171.167.147): icmp_seq=5 ttl=46 time=183 ms

---

### Post by foodcoman on 2005-04-21
I am having trouble as well all of a sudden on a fresh install.

What Up!

---

### Post by nocturn on 2005-04-22
[QUOTE=Spirit]Im not behind proxy

PING wwwkeys.eu.pgp.net (194.171.167.147) 56(84) bytes of data.
64 bytes from minsky.surfnet.nl (194.171.167.147): icmp_seq=1 ttl=46 time=118 ms
64 bytes from minsky.surfnet.nl (194.171.167.147): icmp_seq=2 ttl=46 time=109 ms
64 bytes from minsky.surfnet.nl (194.171.167.147): icmp_seq=4 ttl=46 time=197 ms
64 bytes from minsky.surfnet.nl (194.171.167.147): icmp_seq=5 ttl=46 time=183 ms[/QUOTE]

You could try adding the protocol:

--keyserver hkp://wwwkeys.eu.pgp.net or --keyserver [http://wwwkeys.eu.pgp.net](http://wwwkeys.eu.pgp.net)

If this fails, can you check another server?

---

