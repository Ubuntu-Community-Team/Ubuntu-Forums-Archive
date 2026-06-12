---
title: "Installing Postgres cube data type"
date: 2010-09-13
forum: Server Platforms
---

### Post by krokodil on 2010-09-13
When trying to setup the MusicBrainz database I get the following error:

```
ERROR:  type "cube" does not exist
```

As far as I can tell to fix this I need to install the Postgres-contrib package as well as the Postgres.

My problem is that I have installed both packages (not at the same time) but I am still getting the above error. I have tried restarting and stopping Postgres. I tried have reinstalling both packages.

Does anyone know if I need to do something to "activate" the cube datatype? Maybe add a line to a config file?

Kind regards,
Rudolf

---

### Post by krokodil on 2010-09-13
Turns out I have to install the cube SQL. You do this by running the following command in psql:

```
\i /usr/share/postgresql/8.4/contrib/cube.sql
```

---

