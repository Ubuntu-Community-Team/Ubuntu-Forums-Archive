---
title: "Munin CGI graphing"
date: 2010-11-04
forum: Server Platforms
---

### Post by subquake on 2010-11-04
I need help figuring out how to get the cgi-graph options to operate. The only help I get isfrom the apache error log:
Script timed out before returning headers: munin-cgi-graph
 
I tried switching to the fastcgi, but it doesn't get as far:
File does not exist: /usr/lib/cgi-bin/munin-fastcgi-graph/.../if_eth0-year.png
 
I've tried checking on the permissions, and I believe it to be correctly set up from the multiple tutorial instructions.
The apache alias seems to be set up correctly from the first example.
 
I'm positive that if I took out the CGI method, it would generate the png files properly. The HTML generates just fine judging from the png links.
 
Your help is greatly appreciated!

---

### Post by subquake on 2010-11-04
I've been digging through the munin-users mailing list archives, but haven't found anything, yet.  Is there a better place to look for solutions?

---

### Post by minaev on 2010-11-04
No solution, sorry, but, AFAIK, running Munin in CGI-mode [is not recommended]("http://munin-monitoring.org/wiki/CgiHowto").

I use Munin in the plain cron-based configuration. You should not worry about performance penalty caused by running graph-drawing scripts every five or ten minutes, it is not even noticeable. Do you have any other reasons to choose the hard way?

---

### Post by dapperdanny77 on 2010-11-04
did you try to change apache timeout parameters?
the error message points to that 

what's the value of TimeOut directive?

---

### Post by subquake on 2010-11-05
The hardware isn't new, and it takes 30-40 secs to generate the graphs.  3ghz celeron 2gb ram...
 
As for the apache2 timeout directive, it is at the default 300

---

