---
title: "Suspected Corrupted Root Certificates"
date: 2010-12-25
forum: Security
---

### Post by kelvinator on 2010-12-25
My desktop 10.10 is unable to access SOME https websites from all installed browsers (Firefox, Chrome and Opera).

In firefox I get the error message "Firefox can't establish a connection to the server at www.[nameofsite.com]"

One suggestion that I encountered was that the Root Certificates were outdated and/or corrupted and needed to be reset.

A Google search came with the suggestion:
FIX THE ROOT CERTIFICATES ON YOUR SYSTEM
Open Your browser and navigate to the following URL.
Once at the web page follow the directions to reset your root certificates.

[https://getca.verisign.com/](https://getca.verisign.com/)

Unfortunately this website is one of the problem connections.

How can I fix this?

Another PC with a fresh installation of 10.10 does not display these problems.

---

### Post by kelvinator on 2010-12-26
The solution to this problem was less complex than I feared.
The IP Tables settings were incorrectly configured.

After installing GuardDog I was able to allow the traffic that was being blocked and the connection worked.:popcorn:

---

