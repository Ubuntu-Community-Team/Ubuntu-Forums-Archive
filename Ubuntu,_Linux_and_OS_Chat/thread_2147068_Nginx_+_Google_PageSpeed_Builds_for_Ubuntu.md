---
title: "Nginx + Google PageSpeed Builds for Ubuntu"
date: 2013-05-20
forum: Ubuntu, Linux and OS Chat
---

### Post by sandyd on 2013-05-20
After seeing that Google Pagespeed now has a nginx module ([https://github.com/pagespeed/ngx_pagespeed](https://github.com/pagespeed/ngx_pagespeed)), I have created an experimental repository for it.

It is available at [https://launchpad.net/~sandyd/+archive/nginx-current-pagespeed](https://launchpad.net/~sandyd/+archive/nginx-current-pagespeed)

[s]You will have to build it yourself (two lines really)[/s], but I would love if some people could test it.

If anyone wants the package sources, see the directions at [https://github.com/celenebjvl/nginx-latest-pagespeed](https://github.com/celenebjvl/nginx-latest-pagespeed)
**Notes:**
[LIST]
[*][s]The version number still hasnt been updated, but it matches the current Ubuntu release. I will fix that later[/s]
[*][s]This was tested on 12.04 only, I will provide a 12.10/13.04 version later on if I have time[/s]
[*]
[/LIST]

---

### Post by teward on 2013-05-20
> **sandyd said:**
> After seeing that nginx now supports Google Pagespeed ([https://github.com/pagespeed/ngx_pagespeed](https://github.com/pagespeed/ngx_pagespeed)), I have created an experimental repository for it.

You will have to build it yourself (two lines really), but I would love if some people could test it.

Instructions at [https://github.com/celenebjvl/nginx-pagespeed](https://github.com/celenebjvl/nginx-pagespeed)

Show me in the changelogs for nginx where that's supported.  Third party modules aren't part of nginx and therefore can't be used to say "oh hey nginx supports this"

---

### Post by sandyd on 2013-05-20
> **Lord of Time said:**
> Show me in the changelogs for nginx where that's supported.  Third party modules aren't part of nginx and therefore can't be used to say "oh hey nginx supports this"

well, Google PageSpeed supports nginx now :D

---

### Post by sandyd on 2013-05-21
Repository now updated with proper debian naming along with source package so that Ubuntu wont freak out over the versioning.

---

### Post by geaden on 2013-05-21
Hello everyone! Will this package update my current nginx installation without pagespeed? Thanks.

---

### Post by sandyd on 2013-05-21
> **geaden said:**
> Hello everyone! Will this package update my current nginx installation without pagespeed? Thanks.

Not at the moment.

---

### Post by sandyd on 2013-05-23
Updated to nginx 1.4.1

---

### Post by hmoen on 2013-12-08
I'm a noob to ubuntu and currently on U12.04 and have following installed:
nginx
nginx-common
nginx-full
I added your PPA and did "apt-get update".

How would I go about installing the new nginx-full with pagespeed enabled since it won't upgrade?  Also, once installed what do I need to add to my nginx.conf to enable pagespeed?

Thank you in advance.

---

