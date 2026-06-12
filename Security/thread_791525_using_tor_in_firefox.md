---
title: "using tor in firefox"
date: 2008-05-12
forum: Security
---

### Post by scientist1971 on 2008-05-12
I installed tor with sudo apt-get install tor
I installed the tor button add on in firefox
I went to torcheck with tor off to note my IP address
When I enabled tor I could not access any sites and firefox gave me this message:
The proxy server is refusing connection
Firefox is configured to use a proxy server that is refusing connections.

    *   Check the proxy settings to make sure that they are correct.

    *   Contact your network administrator to make sure the proxy server is
          working.
In firefox --> edit --> preferences --> advanced --> network --> connection settings I am unsure what to enter in the socks host and port boxes
Anyone know how to do this?

---

### Post by cdenley on 2008-05-12
I think tor button assumes you are using privoxy.

[http://www.torproject.org/docs/tor-doc-unix.html.en#privoxy](http://www.torproject.org/docs/tor-doc-unix.html.en#privoxy)

---

### Post by Dr Small on 2008-05-12
Yeah, you need to disable privoxy in the Tor button. I run Tor without privoxy all the time, and privoxy is not needed.

---

### Post by Sp|ke on 2008-05-23
> **Dr Small said:**
> Yeah, you need to disable privoxy in the Tor button. I run Tor without privoxy all the time, and privoxy is not needed.

Strictly speaking your right, privoxy is not needed, however without it you run the risks of DNS leaks. I would suggest always to run **browsers** through privoxy first.

---

