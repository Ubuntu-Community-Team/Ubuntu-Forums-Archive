---
title: "Apache + python app"
date: 2006-08-21
forum: Server Platforms
---

### Post by catfox on 2006-08-21
Hi all,
I've got an apache setup which rewrites requests of subdomains like:

[http://www.ubuntu.yourlinux.org/](http://www.ubuntu.yourlinux.org/)

it takes the ubuntu part of the url and then calls the corresponding python app which is in
/home/username/yourlinux/ubuntu

there are several linux sites, ubuntu, redhat, suse etc. at the moment, when i add a new site i have to create a new filesystem directory with the python app (/home/username/yourlinux/new_distro) and alter it's source to have the url.

i want to do this but only have the one python app on the filesystem, so apache will query the app and send the variable name to the source code.

does anyone know the technique used for this and have any hints for achieving it?

many thanks for reading.

---

