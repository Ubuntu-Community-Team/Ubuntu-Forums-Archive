---
title: "Updating Multiple Computers"
date: 2009-01-28
forum: Server Platforms
---

### Post by watson516 on 2009-01-28
If I connect multiple computers running Ubuntu to a Ubuntu server, is it possible to download the needed updates with the server and then send those updates to the network and have each computer automatically update using the server files so that each computer doesn't have to go and download the updates wasting my bandwidth?

---

### Post by HermanAB on 2009-01-28
The best way is to install a Squid proxy server.  That will improve you internet connection in general, not only for updates.

Hope that helps!

Herman

---

### Post by cariboo on 2009-01-28
The package you are looking for is apt-cacher. Follow [this]("http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher") howto.

Jim

---

