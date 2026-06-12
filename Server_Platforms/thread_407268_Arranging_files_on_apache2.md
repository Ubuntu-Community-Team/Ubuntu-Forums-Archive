---
title: "Arranging files on apache2"
date: 2007-04-11
forum: Server Platforms
---

### Post by rangerxlt8 on 2007-04-11
How do I get the folders to be viewed at top of directory, and then loose files to fall in under them.(this is being viewed in firefox)Right now the list of files\directoreis, when pulled up in a web browser, are in alphabetical order.... I need them to be folders followed by loose files... I run Ubuntu Edgy Eft.... Thanks

---

### Post by MJN on 2007-04-12
You can use the following directive:
 
```
IndexOptions +FancyIndexing +FoldersFirst
```
 
...placed inside either just a specifici <Directory></Directory> container, or to be more widely applicable inside <Virtualhost> or the main /etc/apache2/apache2.conf config file for server-wide applicability.
 
Mathew

---

### Post by rangerxlt8 on 2007-04-13
So I added the line in the apache2.conf file and restarted the server, no go...

A line exist in the conf file thats says 
> IndexOptions FancyIndexing

Now I modified that line to match the above line and it changes the way it looks int he web browser but still folders are not ontop...

---

### Post by MJN on 2007-04-13
Try

```
IndexOptions FancyIndexing FoldersFirst
```

(i.e. leaving the +/-'s out)

Mathew

---

### Post by rangerxlt8 on 2007-04-14
Sweet! It worked.  Now my server does not appear to be run by a monkey!

---

