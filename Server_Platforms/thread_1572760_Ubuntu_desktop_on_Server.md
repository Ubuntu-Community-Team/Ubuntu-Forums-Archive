---
title: "Ubuntu desktop on Server"
date: 2010-09-11
forum: Server Platforms
---

### Post by joemost on 2010-09-11
Is it possible to set up ubuntu on a webserver so when i go to the servers url, I can login to my ubuntu desktop (running on the server). So asscess the ubuntu desktop from a server on a url.

---

### Post by johngreth on 2010-09-11
is this what you're looking for?

[http://www.stone-ware.com/](http://www.stone-ware.com/)

---

### Post by HermanAB on 2010-09-12
Howdy,

Make a virtual machine and use ssh -X -C -c blowfish user@hostname to connect to a desktop session.

---

### Post by johngreth on 2010-09-12
You need to install ssh on the server for that to work (at least I did with 9.10). Anyway, now I am very interested in this as it may help me as well. How would you go about doing that? I've only ever used virtual box to make a virtual machine. If that is correct, what OS? Thanks.

---

