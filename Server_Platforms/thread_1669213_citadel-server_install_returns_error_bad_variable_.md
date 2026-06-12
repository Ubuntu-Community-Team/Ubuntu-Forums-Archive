---
title: "citadel-server install returns error bad variable name"
date: 2011-01-17
forum: Server Platforms
---

### Post by walter_j on 2011-01-17
I'm trying to install citadel server on ubuntu server 10.04 via apt-get install citadel-server. I get an error at:

setting up citadel-server (7.71-1)
export: 106: 007: bad variable name

dpkg script exits with error code 1.

would this be due to unmet dependency?

Walter

PS. filed a bug in launchpad

---

### Post by walter_j on 2011-02-05
same error in 10.10 and 10.04,

---

### Post by HermanAB on 2011-02-06
Howdy,

Go to [http://citadel.org](http://citadel.org) and run the Easy Install script instead of using apt-get.

---

