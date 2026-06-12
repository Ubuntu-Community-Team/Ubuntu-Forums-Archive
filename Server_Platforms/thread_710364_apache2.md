---
title: "apache2"
date: 2008-02-28
forum: Server Platforms
---

### Post by gjj391 on 2008-02-28
how can set the /www/ and the /cgi-bin/ directories so that I can save files to them.

right now i have to $ sudo gedit  /path/to/cgi-bin/[filename] with it, thats works.

but i just want to set up a project and keep working within my IDE and not have to keep chmoding file names all day! :(

any advice out there?

---

### Post by az on 2008-02-28
> **gjj391 said:**
> how can set the /www/ and the /cgi-bin/ directories so that I can save files to them.

right now i have to $ sudo gedit  /path/to/cgi-bin/[filename] with it, thats works.

but i just want to set up a project and keep working within my IDE and not have to keep chmoding file names all day! :(

any advice out there?

Set the document root to somewhere in your home directory.  Make sure that apache cannot write to the folder, but that it can read it.

---

