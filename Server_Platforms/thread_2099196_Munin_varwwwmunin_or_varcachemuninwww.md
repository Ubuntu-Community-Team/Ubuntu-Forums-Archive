---
title: "Munin: /var/www/munin or /var/cache/munin/www?"
date: 2012-12-28
forum: Server Platforms
---

### Post by OliverHaslam on 2012-12-28
Hi guys,
 
I've just installed Munin for the first time in around twelve months, and I've hit a familiar error.
 
I remember from last year that there is an oddity where Munin wants to keep its html files in /var/cache/munin/www, rather than the usual /var/www/munin. I seem to remember being able to change the config files accordingly, and force the app to put the files in the right place, and everything worked fine.
 
Tonight though, I managed to make Munin write the files to the correct directory, but for some reason Apache isn't pointing to them correctly.
 
For example, the monitoring should be available at website.com/munin - website.com is in /var/www - but for some reason Apache keeps pointing to where Munin originally wanted to put the files. If I copy everything back to /var/cache/munin/www, it works.
 
Is there an Apache setting I have missed anywhere? I'm not sure where it could be, but something is obviously stopping Apache from serving website.com/munin from /var/www/munin.
 
All that make any sense?
 
 
Cheers.

---

### Post by pkloves on 2013-02-24
I'm sure you've got this worked out already, but for others who are struggling with it, here's some information:

The default installation creates a symlink in /etc/apache2/conf.d directory to the apache.conf config.  If you update munin.conf and change the htmldir setting, you will also need to update the apache.conf config.  Change 

```
Alias /munin /var/cache/munin/www
<Directory /var/cache/munin/www>
```

to 

```
Alias /munin /var/www/munin
<Directory /var/www/munin>
```

While upgrading to a new Ubuntu server, I copied over my old munin config files, and it started writing them to /var/www/munin, but the web page still pointed to the old ones.   It took me a few minutes to figure it out.

---

### Post by kOoLiNuS on 2013-04-12
_thanks_ for the tip @pkloves ... you made my day ... I had empty graphs for two days (with the -nan sign under the bottom of each of them).
I just changed that file and everything now is working !!!

---

