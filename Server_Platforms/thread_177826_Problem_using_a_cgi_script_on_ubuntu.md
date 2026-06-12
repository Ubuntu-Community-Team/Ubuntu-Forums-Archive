---
title: "Problem using a cgi script on ubuntu"
date: 2006-05-16
forum: Server Platforms
---

### Post by jrobinson5 on 2006-05-16
Hello everyone.

I'm trying to set up an ubuntu server (normal installation, not server installation) to run [this]("http://www.jmarshall.com/tools/cgiproxy/") cgi script. I copied the cgi file to /usr/lib/cgi-bin/, but whenever I try to load that page, on the server or on a different Ubuntu computer, the firefox "wheel" will spin for half  a second, and the page I was last at will show up. I don't know whatelse to say, but I will be happy to answer questions.

I'm typing this from my laptop, and obviously the config file is on my server, so I will put it in here asap.

Thanks a lot,
James Robinson

---

### Post by peanut butter on 2006-05-17
you must change the first line to #!/usr/bin/perl if its not alredy.
p.s. iwould recomend phproxy on sourceforge. as its faster and lesso f a system hog.

---

### Post by jrobinson5 on 2006-05-20
Ok, I installed phproxy and libapache2-mod-php5 and I get the index page fine, but whenever I type in a page and press enter, I get:


Fatal error: Only variables can be passed by reference in /var/www/PHProxy.class.php on line 177

What gives?

---

