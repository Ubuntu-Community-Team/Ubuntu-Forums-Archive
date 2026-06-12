---
title: "apache2, private web directories"
date: 2009-02-15
forum: Server Platforms
---

### Post by sjl127 on 2009-02-15
On a web host, say if you visit,

[http://www.blahblah.com/picures/picture.jpg](http://www.blahblah.com/picures/picture.jpg)

and you then visit, 

[http://www.blahblah.com/pictures/](http://www.blahblah.com/pictures/)

How can you make it so that directory comes up to the user to have no access?

---

### Post by hrod beraht on 2009-02-15
The Indexes option is what drives that. If there is no index.html page or equivalent in a directory, a formatted list of the files will be shown instead.

To turn off that list of files, in your httpd.conf file put a *minus* indexes option, as in:

```
<Location />
Options -Indexes
</Location>
```

For further options, see [[COLOR="Blue"]this Apache docs page[/COLOR]]("http://httpd.apache.org/docs/2.0/mod/core.html#options").

Bob

---

### Post by sjl127 on 2009-02-15
Most importantly, thanks for telling me where to look, it worked well.

---

