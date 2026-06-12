---
title: "Character encoding problem"
date: 2007-01-27
forum: Server Platforms
---

### Post by rwilliams on 2007-01-27
I'm using Ubuntu Breezy + Apache2 as a web server.     Although some of the web pages define the character set like this :
> <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
<meta http-equiv="Content-Style-Type" content="text/css"

both Firefox and IE fail to display single quotes correctly (Firefox shows a Question Mark and IE a small square).  Manually switching the browser to View > Character Encoding > Western (ISO 8859-1) fixes the problem - but on the next page refresh it reverts to UTF-8 and the characters again display incorrectly.

The problem occurs with different PC's and different OS's and browsers - so I imagine it's a server problem rather than a client issue.

APache's config file contains the line:
> AddCharset ISO-8859-1    .iso8859-1    .latin1

and the /etc/environment file contains:> LANG=en_US.UTF-8

I've messed around with > sudo dpkg-reconfigure localeconf but with no success....

What am I missing ?   I really would like to fix this irritating problem
Thanks
Rich.

---

### Post by rwilliams on 2007-01-27
Problem solved - for the most part.....

I used > sudo dpkg-reconfigure localeconf

to add > LANG=en_US to the /etc/environment file and 

> en_US ISO-8859-1 to the /etc/locale.gen file  (choosing US-ISO-8859 in dpkg-reconfigure achieves this automatically)

I also uncommented the following line in my Apache config:

> AddDefaultCharset ISO-8859-1

Rich.

---

