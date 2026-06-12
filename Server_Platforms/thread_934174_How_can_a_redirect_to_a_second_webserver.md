---
title: "How can a redirect to a second webserver?"
date: 2008-09-30
forum: Server Platforms
---

### Post by grs on 2008-09-30
I have two webservers, one an Ubuntu webserver and a Clarkconnect server which is directly linked to the web domain at pointclark.net Between the CC server and the pointclark site it keeps track of my dynamic IP from my ISP and redirects requests to my CC server.

I have found a few things I don't like about the CC web server so I was wondering, is there a way once a request has been redirected to to my CC box can I then redirect it again to an Ubuntu webserver?

---

### Post by volkswagner on 2008-09-30
You would create a permanent redirect.  I am not sure why you would do this.  One machine would probably need apache2 running on a non standard port.  You would then have to mask the redirect to not show the port number.

Why don't you just move your site to the ubuntu machine and set up dynamic dns to that box?

[http://www.webconfs.com/how-to-redirect-a-webpage.php]("http://www.webconfs.com/how-to-redirect-a-webpage.php")

---

