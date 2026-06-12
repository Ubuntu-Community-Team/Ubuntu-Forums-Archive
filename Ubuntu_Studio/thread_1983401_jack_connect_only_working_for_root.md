---
title: "jack_connect only working for root?"
date: 2012-05-20
forum: Ubuntu Studio
---

### Post by sgx on 2012-05-20
I just noticed this, while trying to find a low-cpu guitar setup,
After I start jackd, trying to connect the jackd ports using
jack_connect fails, asking if it is running (which it is)

The same process, done as root, works. I did notice an issue also
with jack_disconnect, if the command is to disconnect one side of stereo signal, it takes sound down both sides, but leaves one connection still drawn in qjackctl. Reconnecting the one side
reconnects both

jack_connect system:capture_1 system:playback_1
jack_connect system:capture_2 system:playback_2

both work as root. :guitar:

When run as user, this error occurs: 

Cannot open jack_connect client
jack server not running? 

Cheers

---

