---
title: "additional directory being inserted in path for displaying virtual host in Apache2"
date: 2014-05-25
forum: Server Platforms
---

### Post by Robertjm on 2014-05-25
Got a strange one here.

I recently blew away my old installation of Precise Pangolin and replaced it with a completely fresh install of Trusty Tahr.

My public_html file is basically the default:

/var/www/mydomain/public_html

and within that folder I have an index.html file.

When I try entering in localhost, or mydomain, I get a listing directory listing, which in this case is link to the public_html folder. When I click on it and then click the index.html file to display it the web browser's URL changes to: /www.mydomain.com/mydomain/index.html.

I have no idea where the "extra folder is coming out of.

Another strange thing is that it keeps telling me it's on Port 80, though I've changed my HTTP port on my router to something else. However, when I change the ports.conf file to show listening on the other port, and restart Apache it fails completely. Only after changing it back to listening on Port 80 does it work, albeit with the strangeness above.

Suggestions on what I need to check to get rid of the anomaly above?

Thanks!!

Robert

---

