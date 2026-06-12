---
title: "open source replacement for MS-Access"
date: 2016-07-01
forum: Ubuntu Application Development
---

### Post by Bunny Boy on 2016-07-01
I have experience using MS-Access to develop simple database applications, but I'd like to keep my new project open source.  So far, every gui platform I have found has serious inadequacies.  For example libreoffice base and kexi both don't support UPDATE queries.  I have also tried MySQL Workbench and SQLiteman but can't seem to figure out how to do anything like I want, which is create forms that will allow users to update my tables. 

I really don't need to do anything more complicated than have the user input increment or decrement a field for a selected row, but so far I have found nothing that will enable me to do what is very easy in MS-Access. I don't even need a database server, since I'll just be using one computer to modify a single file. 

I'm running Ubuntu 16.04.

Any suggestions?

---

### Post by QIII on 2016-07-01
Well...

As much as I hate to say it, MS Access is simply the most feature-rich, self-contained, small-scale database there is on the market.  It is terribly inefficient; makes Edgar Codd himself roll in his grave; generally creates bad habits in both programming and database design; uses macros that are nearly impossible to debug; etc, etc.

But, it's a complete package.  That you won't find in the open source world. 

You can start with something like MySQL and learn to use language/IDE of your choice to connect to and manipulate database objects, create forms and reports etc.  But it won't all be "under one roof."

---

### Post by Bunny Boy on 2016-07-01
> **QIII said:**
> Well...

You can start with something like MySQL and learn to use language/IDE of your choice to connect to and manipulate database objects, create forms and reports etc.  But it won't all be "under one roof."

I haven't been able to figure out how to create forms with MySQL Workbench.  Is there another IDE that is maybe a little straight forward, or some kind of tutorial for Workbench?

---

### Post by oldfred on 2016-07-01
I used Access a lot at work. But did not use macros, but vb scripts and often copied the sql code in query into my code behind the forms. I wanted to learn SQL and knew basic so not difficult. Ended up converting many to just a front end into MS-SQL server for multiple user access.

Now retired and looked at various options.Ended up with python as scripting language with geany as editor, qt as gui using qt designer, and sqliteman to test sql statements using SQLite, which I then copy into my python. I also then had to learn each separately. Steep learning curve and more effort required to glue pieces together. Also in python used HttpWidget to do Web look ups.  Saved many links which I can post if interested, but there probably are easier ways.

Some simply python examples with sqlite:
[http://zetcode.com/db/sqlitepythontutorial/](http://zetcode.com/db/sqlitepythontutorial/)

---

