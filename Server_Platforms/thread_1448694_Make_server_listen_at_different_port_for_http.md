---
title: "Make server listen at different port for http?"
date: 2010-04-06
forum: Server Platforms
---

### Post by 14tjoyce on 2010-04-06
How can I set my server to listen at a different port for http access. I would like to use port 8080 (to circumnavigate isp blocks). Also can I do the same thing for sftp connections? Thanks!

---

### Post by s_ø on 2010-04-07
you set the listen directive in the config files to the port you wish to listen to.
for apache in **/etc/apache2/ports.conf**
and in **/etc/apache2/sites-available/default** (assuming you use the default site.)
for ssh in **/etc/ssh/sshd_config**

---

### Post by Ryan Dwyer on 2010-04-07
Or you could leave your server listening on port 80 and just forward 8080 to 80 in your router.

---

### Post by 14tjoyce on 2010-04-07
I used the forwarding through the router method and it worked perfect! thanks!

---

