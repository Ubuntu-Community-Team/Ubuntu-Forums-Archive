---
title: "Unable to connect to web/Connection refused"
date: 2011-02-14
forum: Server Platforms
---

### Post by dpcreemer on 2011-02-14
I have a new Ubuntu server (10.10), named Denholm, recently installed and updated.  I came in this morning, attempted to add a package with apt-get, and got a "Connection refused" response.  I have another server (also 10.10), named Moss, on the same network that can connect successfully.  Google has not been any help.

Here's what I've found/tried so far:

This doesn't look like and apt problem anyway, but the sources.list files on Denholm and Moss are identical.

I can ping [www.google.com](www.google.com) (and other sites) successfully from Denholm.

I have tried 'wget [www.google.com](www.google.com)'.  From Moss the wget is successful, but from Denholm I get "Connection refused."  

I have a web server on Moss and Denholm can successfully access it.

To the best of my knowledge, Denholm is not configured to use a proxy server (no http_proxy variable set).

Any help would be greatly appreciated.

---

### Post by dpcreemer on 2011-02-14
Problem resolved itself.  I literally walked away from it for 1 hour and it when I came back it was working.

---

