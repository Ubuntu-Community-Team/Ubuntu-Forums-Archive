---
title: "juju ppa:juju/stable gives errors on sudo apt-get update"
date: 2013-08-24
forum: Ubuntu Cloud and Juju
---

### Post by bmullan2 on 2013-08-24
Installed the juju ppa so I could update to the 1.12.x release on my Ubuntu 13.04 x64 bit desktop.

$** sudo add-apt-repository ppa:juju/stable**

$ **sudo apt-get update**

This gives out the error:
[INDENT][B][I]Fetched 12.3 kB in 13s (876 B/s)                                                                                 
W: Failed to fetch [http://ppa.launchpad.net/juju/stable/ubuntu/dists/raring/Release.gpg](http://ppa.launchpad.net/juju/stable/ubuntu/dists/raring/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-11 - System error)

E: Some index files failed to download. They have been ignored, or old ones used instead.[/I][/B]
[/INDENT]

Not sure  why that error as I just checked launchpad for juju-hackers:

[https://launchpad.net/~juju/+archive/stable](https://launchpad.net/~juju/+archive/stable)

And launchpad says Ubuntu 13.04 is supported with the PPA ??

---

### Post by bmullan2 on 2013-08-24
whatever the repository problem was it has cleared itself... update now works.

---

