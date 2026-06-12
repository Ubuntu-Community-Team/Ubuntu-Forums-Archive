---
title: "Multi Website Webserver"
date: 2007-05-10
forum: Server Platforms
---

### Post by pkarjala on 2007-05-10
So.  I know that I can set up a webserver and point various DNS entries to the IP of that webserver.  No problem; our company has ownership of a hundred or so variations of our actual site name, just point their DNS entry to our website, and wait for it to propagate.

Trickier, however, is what our boss has asked me to try and set up.  He'd like to serve multiple different websites from the same LAMP server box.  Basically, if [www.foo.com](www.foo.com) and [www.server.com](www.server.com) both resolved to our webserver, would there be a way to serve up a different content based on the requesting URL?

I imagine it would involve setting up more than one Apache daemon to listen on different ports for web services based on the request, but that sounds like it'd be an inelegant solution.  Thus, I turn to here for any other ideas, or experiences that people have had in this particular vein of web server hosting.

Many thanks in advance!

---

### Post by bukwirm on 2007-05-10
You're probably looking for [virtual hosts]("http://httpd.apache.org/docs/2.2/vhosts/").

---

### Post by pkarjala on 2007-05-11
Perfect--thank you!

---

