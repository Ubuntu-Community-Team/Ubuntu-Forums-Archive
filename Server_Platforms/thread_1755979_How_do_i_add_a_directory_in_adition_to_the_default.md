---
title: "How do i add a directory in adition to the default 'www' to apache2"
date: 2011-05-11
forum: Server Platforms
---

### Post by superdaveozzborn on 2011-05-11
I have been searching the web and Ubuntu forums all day looking for an answer to what I initially thought would be a simple thing to do. I have set up a lamp server and started creating my network site, however was not long before I ran into an issue with fire fox not allowing me to access locally linked files that are shared on the network which works fine in IE. after several hours of trying to find a work around, I have been unsuccessful in creating a link that would work in both IE and FF. 
so I got this bright idea see:), to just make the website include the network shared content, unsharing them of course and simply adding them to my Apache server, well the more I read the more confusing it all became. do I use simlinks or do I create a server for each location/hard drive?
I really need a how to for big dummies on adding additional directories to Apache similar to adding virtual directors to IIS for windows.

any links or direction would be greatly appreciated.
thank you very much.

---

### Post by superdaveozzborn on 2011-05-11
well I got it working, I added a symbolic link to the www folder, not really shire about the security when doing it this way but it seams to be working......

has any one any input on doing it this way?

---

### Post by Lars Noodén on 2011-05-12
A symbolic link is fine.  

If you want to do the same thing using only Apache directives, then look at the directives [directory](http://httpd.apache.org/docs/2.2/mod/core.html#directory) and [alias](http://httpd.apache.org/docs/2.2/mod/mod_alias.html#alias).

---

### Post by superdaveozzborn on 2011-05-12
thank you Lars for taking the time to answer my question, still very new to Apache.

---

