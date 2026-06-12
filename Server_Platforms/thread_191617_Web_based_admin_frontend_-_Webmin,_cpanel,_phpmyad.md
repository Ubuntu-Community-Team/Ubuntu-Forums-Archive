---
title: "Web based admin frontend - Webmin, cpanel, phpmyadmin"
date: 2006-06-07
forum: Server Platforms
---

### Post by nigel on 2006-06-07
As above, is there a preferred frontend to manage the server once setup, 

My situation is this 

I have an older machine i want to set up as a testing server (on site) for sites i am developing, (about 5 -6 sites at a time), and would like to be able to manage them through some sort of frontend, 
I have used Cpanel and it does the job, also PHPmyadmin I couldn't be without, is there a preferred webbased frontend for managing the server

I have heard of CPanel, webmin and ispconfig, do they all integrate with phpmyadmin, is there one that is supported on Ubuntu (ie an apt get would install it for me)

I would like also like all the sites to be seperate on the same server, I think it's called virtual hosting, as in i don't need a network card for each, is there a guide to doing this somewhere, or do some of the above frontends support this

Anyhelp would be greatly appreciated

---

### Post by cyracks on 2006-06-08
[quote=nigel]
I have heard of CPanel, webmin and ispconfig, do they all integrate with phpmyadmin, is there one that is supported on Ubuntu (ie an apt get would install it for me)
[/quote] I think webmin is the only control panel in the repo.

---

### Post by A1ex on 2006-06-08
If you're using dapper it is no longer in the repo.

The debian maintainer has stopped packaging it so it's not in Ubuntu.

However, you can still download and install it from [www.webmin.com](www.webmin.com), it just doesn't integrate as well in my opinion.

---

