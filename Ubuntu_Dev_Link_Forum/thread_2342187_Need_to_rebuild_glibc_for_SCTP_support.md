---
title: "Need to rebuild glibc for SCTP support?"
date: 2016-11-04
forum: Ubuntu Dev Link Forum
---

### Post by bingasedu on 2016-11-04
I'm using lksctp and I've run into unexpected behavior with getaddrinfo(). If the service arg to getaddrinfo() is specified as a number rather than a name, getaddrinfo() returns addrinfo structures for all the protocols it knows about (it does not examine the /etc/services database). After installing lksctp, this should include IPPROTO_SCTP, but doesn't. It looks to me like getaddrinfo() is actually returning addrinfo structures for all the protocols it knew about at the time it was built. How can I rebuild glibc to include support for SCTP, or how can I install a version of glibc that supports SCTP? Thanks for any help.

---

### Post by bingasedu on 2016-11-14
I think can answer my own question: It turns out that there is too much existing code which assumes that hints.ai_socktype = SOCK_STREAM and hints.ai_protocol = 0 _means_ TCP, and versions of getaddrinfo() who's results included addrinfo structures containing IPPROTO_SCTP in this case, caused problems. As a result, when the service arg to getaddrinfo() is specified by port number, the results will never include IPPROTO_SCTP. You need to set hints.ai_protocol = IPPROTO_SCTP if you want the results to include IPPROTO_SCTP. An alternative is to edit the /etc/services database to include the name of your service and the fact that is uses SCTP, and then specify the service arg by name. In this case getaddrinfo() will examine the /etc/services database and return results based on what it finds there.

---

