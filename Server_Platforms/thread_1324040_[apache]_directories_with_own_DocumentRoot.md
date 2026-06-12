---
title: "[apache] directories with own DocumentRoot"
date: 2009-11-12
forum: Server Platforms
---

### Post by silvernewt on 2009-11-12
hi all,

i have apache 2.2 running on hardy which i'm setting up as a development server. i have a dyndns.org domain which points to my network.

what i'd like to do is set up several testing sites as sub directories of this domain, but each should have their own DocumentRoot directive.

eg:
mysite.dyndns.org (DocumentRoot is set as /var/www)
mysite.dyndns.org/siteA (DocumentRoot is set as /var/www/siteA/htdocs)
mysite.dyndns.org/siteB (DocumentRoot is set as /var/www/siteB/htdocs)
mysite.dyndns.org/yetAnotherSite (DocumentRoot is set as /var/www/yetAnotherSite/htdocs)

can this be done with virtualhosts?

i don't want to access them as [http://siteA](http://siteA) by hacking hosts files, as:
1) i have a mixture of linux & windows machines & don't want the hassle of setting it up
2) it needs to be accessible from any computer & i can't tell people to go modifying their hosts files before they can see the work i'm completing.

i did try whacking DocumentRoot settings into a <directory> directive but (as i thought it would be) that was too simple a solution to work.

if someone could throw up an example or point me in the direction of the answer that would be great, i've spent 2 days googling & hacking but have come to a dead end!

thanks, Neal

---

### Post by Lars Noodén on 2009-11-12
With virtual hosts either the hostname should be different or the port.  

e.g.
mysiteA.dyndns.org
mysiteB.dyndns.org
mysiteC.dyndns.org

Otherwise, if you just want to map a directory to another part of the server, then use the [Alias](http://httpd.apache.org/docs/2.2/mod/mod_alias.html#alias) directive.  Be sure to set the right permissions for those directories in the vhost using the Directory run time directive.

---

