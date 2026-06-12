---
title: "MySQL MS Access compatibility"
date: 2008-11-21
forum: Server Platforms
---

### Post by reg4c on 2008-11-21
Hey, 

I have a MySQL database on one server and an MS Access database on the other.

Now, its easier for me to create a MySQL database then an MS Access.

Does anyone have any idea how I can convert MySQL DB to MS Access format and vice versa.

Cheers

---

### Post by dgoosens on 2008-11-21
if you only need to do this once...
you can convert them with the TRIAL version of NAVICAT:
[http://www.navicat.com/]("http://www.navicat.com/")

the Linux version of this tool just runs in Wine, so you might want to start Windows, install Navicat, do the export and go back to Ubuntu...

otherwise...
you can always export as tab seperate file...

dGo

---

### Post by koenn on 2008-11-21
> **dgoosens said:**
> 
otherwise...
you can always export as tab seperate file...

dGo

good idea. You can even export tables, views, ... into 'create table', 'create view' sql scripts, which you can use to recreate the database on an other system.

---

