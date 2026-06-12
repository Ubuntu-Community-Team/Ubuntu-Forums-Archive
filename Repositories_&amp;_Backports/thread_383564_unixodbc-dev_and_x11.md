---
title: "unixodbc-dev and x11"
date: 2007-03-13
forum: Repositories &amp; Backports
---

### Post by thefool808 on 2007-03-13
Anybody have any clue why the unixodbc-dev package requires all the x11 packages??  The unixodbc package doesnt and supposedly unixodbc-dev is only the headers and schtuff.

There's probably some x-windows config util or something (that I certainly don't need) included with the dev package.  Is there some way I can avoid install all of x11 without compiling from source?

This is gonna screw up my pretty little server install :(

Thanks for the help!

edit: this is for edgy and the package is located here [http://packages.ubuntu.com/edgy/devel/unixodbc-dev](http://packages.ubuntu.com/edgy/devel/unixodbc-dev)

also, I need this for ruby odbc which isnt working and won't compile from source without sql.h (in unixodbc-dev)

---

