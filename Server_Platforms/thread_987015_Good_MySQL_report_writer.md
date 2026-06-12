---
title: "Good MySQL report writer"
date: 2008-11-19
forum: Server Platforms
---

### Post by porchrat on 2008-11-19
Hi all.

Title pretty much speaks for itself.  Anyone know of any good MySQL report writers?  I want something that allows actually writing queries (drag and drop stuff would be nice too, but not essential).

Needs to be able to export to .csv or preferably to a spreadsheet format such as .xls or .ods

I've tried SQuirrel, that was pretty good, but now I'm using emma.  They are both good examples of the functionality I need, but SQuirrel has issues with some of the values in my database (displays some of them in hexadecimal), and emma only exports to .csv and I would prefer a .xls export as the .csv does introduce some annoying formatting issues (adding a few blank rows when importing into a spreadsheet etc.)

Any suggestions?

---

### Post by dgoosens on 2008-11-19
hi,

I find the MySQL Workbench does the trick rather well:

[http://dev.mysql.com/downloads/workbench/5.0.html]("http://dev.mysql.com/downloads/workbench/5.0.html")

it is a complete solution for your databases...
and includes a query browser...

---

### Post by porchrat on 2008-11-19
> **dgoosens said:**
> hi,

I find the MySQL Workbench does the trick rather well:

[http://dev.mysql.com/downloads/workbench/5.0.html]("http://dev.mysql.com/downloads/workbench/5.0.html")

it is a complete solution for your databases...
and includes a query browser...

I've tried workbench out before on a Vista machine and I liked it, but there currently isn't a version of it for Linux.  Do you run it in Wine?

---

### Post by dgoosens on 2008-11-19
sorry, I wrote down the wrong link...

here is the alpha release of the workbench for Linux:
[http://dev.mysql.com/workbench/?p=156]("http://dev.mysql.com/workbench/?p=156")

---

### Post by porchrat on 2008-11-19
Alpha seems a little early in the development cycle to me.  What have been your experiences with it?  Is it stable enough to use?

I generally shy away from the alpha releases and only give it a second glance when it is in beta.

---

### Post by dgoosens on 2008-11-19
well,

it's not fully functional yet... but it does work...
AND it has been developed on Ubuntu... so it integrates pretty well...

but, just give it a shot...
if you don't like it, you just delete it right ?

---

### Post by porchrat on 2008-11-19
I'll give that a go if I don't find an alternative by tomorrow, but I really would like to use something that is not in alpha as it is going to be used frequently.

Thank you for the suggestion I had forgotten about that Linux alpha.  It is definitely a possibility.

---

### Post by dgoosens on 2008-11-19
just figured...
while waiting for MySQL Workbench...
maybe you could work with dbdesigner4

[http://fabforce.net/dbdesigner4/index.php]("http://fabforce.net/dbdesigner4/index.php")

---

### Post by kooper on 2011-05-17
I use [Stonefield Query ]("http://www.stonefieldquery.com")and it works great for creating reports.

---

### Post by SeijiSensei on 2011-05-17
I'll just point out that discussions in this thread ended over two years ago, and even if it were more current, I suspect the OP was looking for free, open-source solutions.

---

