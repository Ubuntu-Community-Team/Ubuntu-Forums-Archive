---
title: "PostgreSQL (Make) Tutorial files How?"
date: 2009-05-31
forum: Server Platforms
---

### Post by Petrik on 2009-05-31
I am trying to follow the tutorial on the PostgreSQL site. I downloaded the documentation files through synaptics but Found "Make" is still required for the files in the tutorial directory.

I am not familiar with how this works and just running make in this directory doesn't work. I get

make: pg_config: Command not found
make: *** No targets.  Stop.

---

### Post by alastair on 2009-05-31
I think you might have to install :

libpq-dev

as well, to get pg_config.

---

### Post by alastair on 2009-05-31
Oh, and the way to discover what package a command might be in, is to visit the Ubuntu packages search site :

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

and in the section "Search the contents of packages", type in :

pg_config

and hit the search button.

---

