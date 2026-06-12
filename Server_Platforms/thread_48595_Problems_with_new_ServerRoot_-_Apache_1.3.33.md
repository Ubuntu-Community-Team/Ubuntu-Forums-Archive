---
title: "Problems with new ServerRoot - Apache 1.3.33"
date: 2005-07-13
forum: Server Platforms
---

### Post by Daz on 2005-07-13
Hi,

I was wondering if someone can help me...

I am have installed the apache-perl package (Apache 1.3.33 web-server with mod_perl already included) and need it to start with a new ServerRoot directory (as all of the config files etc. for the app I am trying to set up are in /usr/local/ensembl/conf)

So, after stopping the apache-perl server I am using the command:

```
/usr/sbin/apache-perl -d /usr/local/ensembl
``` 
to restart it again.

But, it always reverts back to the original ServerRoot and gets all of it's confiuration information from /etc/apache-perl/httpd.conf...

Any ideas how I could stop this happening and possibly make /usr/local/ensembl the permanent ServerRoot directory?

Thanks in advance!

Daz

---

### Post by LordHunter317 on 2005-07-13
Why are you trying to use a different configuration?  Why not replace the stock configuration?

No, I'm not sure why it's happening but I'm not sure why you're trying to do things that way, either.

---

### Post by Daz on 2005-07-13
Hi,

Sorry, I didn't explain properly...

I'm trying to set-up a mirror of the bioinformatics website/database [Ensembl](http://www.ensembl.org) and the entire site is contained under one directory root - all the config files, cgi scripts, the lot.  The recommended way they suggested doing things was to start up the apache server and just specify a ServerRoot to the install directory, and the config files would take care of the rest.  (Unfortunately not quite so in my case...)

Do you think just copying the config files (about 10 of them) into the /etc/apache-perl directory would work?

Thanks!

Daz

---

### Post by Daz on 2005-07-13
Hi.

Sorry LordHunter317 - i've been a bit of a fool!  :roll: 

If I had read the site install instructions, it suggests the best approach is to build apache from source...

I have done this now, and it set's the site up happily!  :smile:

---

