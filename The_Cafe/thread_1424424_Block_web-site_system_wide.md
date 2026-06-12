---
title: "Block web-site system wide?"
date: 2010-03-07
forum: The Cafe
---

### Post by Kdar on 2010-03-07
Is there a way to block some web-page across all system? So that.. no matter which browser is used, it will be blocked?

---

### Post by tjwoosta on 2010-03-07
yep, using your /etc/hosts file

Here is an example that works pretty good for some general ad-blocking 

[http://someonewhocares.org/hosts/](http://someonewhocares.org/hosts/)

---

### Post by Kdar on 2010-03-08
OK. I think I got it..

But can I specify a specific message for those blocked sites?

Since now I see this:
> It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.

I know its the index.html on the default location of the server I am using in Ubuntu.. but can I tell it to use another? (with message like: this web-site is blocked).

---

### Post by tjwoosta on 2010-03-08
Not sure. You could also use squid to block sites. Im pretty sure you can change the message that way.

[http://www.freesoftwaremagazine.com/articles/web_blocking_squid](http://www.freesoftwaremagazine.com/articles/web_blocking_squid)

---

