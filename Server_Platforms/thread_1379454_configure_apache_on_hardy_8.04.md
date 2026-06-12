---
title: "configure apache on hardy 8.04"
date: 2010-01-12
forum: Server Platforms
---

### Post by dmatusow on 2010-01-12
I had apache configured (well, it comes configured), but made some updates and now realize that it's no longer working.
 
I can successfully enter [http://localhost](http://localhost) on the server, but can't reach it successfully from another server.  I can see in wireshark that the request gets to the webserver and that the tcp session is successfully established.  I then see nohting coming out of the server.
 
In an effort to get things straightened out, I removed apache2 and apache2-common, including the configuration.  I then rm'd the entire apache2 directory and reinstalled.  I was hoping that this would install the new base configuration, but it still fails.
 
I see that apache2 does not come up successfully.  Below is the messages I get :
 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98) Address already in use: make sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
unable to open logs

Any ideas on how to piece this back together?
 
Thanks!

---

### Post by ICEB3AR on 2010-01-13
That means that you have to put in the apache config the right servername. I Expect that there is nothin in since your update:
[http://httpd.apache.org/docs/1.3/mod/core.html#servername]("http://httpd.apache.org/docs/1.3/mod/core.html#servername")

he uses the local loopback as serveraddress, but not the right domain/ip.

---

### Post by dmatusow on 2010-01-13
I fixed it.  There were some apache tasks running that I didn't look for.  Once I killed those off - works fine! :D

---

