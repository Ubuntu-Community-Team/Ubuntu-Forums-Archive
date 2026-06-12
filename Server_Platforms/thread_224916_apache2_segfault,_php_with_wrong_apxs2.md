---
title: "apache2 segfault, php with wrong apxs2"
date: 2006-07-28
forum: Server Platforms
---

### Post by jfdill_2 on 2006-07-28
I had to compile a custom php4 for Informix database support :insert vomitting smiley here: and it was driving me crazy that I could run the php script from the command line and generate valid html, but the apache2 child process would segfault when I tried to access the php script via a browser.  If I ran "apache2 -X" the php script would also work fine.  It looks like we don't like forking for some reason.

I think the problem was that I had apache2-threaded-dev installed so the build process was using the apxs2 for threaded apache2 to build mod_php4. I have tried removing apache2-threaded-dev and installing apache2-prefork-dev

apt-get install apache2-prefork-dev

I hope that it will work now when I compile php4 again, will report back.  Here is what the error messages look like:

[Fri Jul 28 15:43:58 2006] [notice] child pid 4003 exit signal Segmentation fault (11)
[Fri Jul 28 15:43:58 2006] [notice] child pid 4004 exit signal Segmentation fault (11)

Edit:  Woohoo it works!

---

