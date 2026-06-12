---
title: "Cgi Scripts (cgiproxy) and ligttpd how do i do it?"
date: 2009-05-01
forum: Server Platforms
---

### Post by pspsampsp on 2009-05-01
i have never used cgi scripts and i have no idea where to start so could someone please tell me what i need to install so that web browsers don't just download the cgi scrip that the server actually executes the script.

(sorry if that doesn't make much sense i have only really used php and html on servers but i have no clue on where to start with a cgi script)

more info: i put the cgi script in /usr/lib/cgi-bin and create a link to it in /var/www using "sudo ln -s /usr/lib/cgi-bin /var/www/cgi-bin" and then use [http://localhost/cgi-bin/nph-proxy.cgi](http://localhost/cgi-bin/nph-proxy.cgi) and the browser pops up a download link. also i made it an executable

---

### Post by Kareeser on 2009-05-08
You may need to enable FastCGI. I'm not too familiar with lighttpd, but someone on the web development forum may have a better idea. I've asked a mod to move it for you.

---

