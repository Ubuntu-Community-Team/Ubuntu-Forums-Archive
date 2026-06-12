---
title: "Possible to import Windows KeePass database into KeePassX?"
date: 2009-03-04
forum: Security
---

### Post by Zirconic on 2009-03-04
I have never been able to import a Windows KeePass 1.x database into KeePassX in Ubuntu. Each time I do I get "Parsing Error: File is not valid KeePassX XML file."  Others have claimed to be able to do it.

Has anyone actually been able to get this to work?

---

### Post by bodhi.zazen on 2009-03-04
You can run Keepass in wine.

---

### Post by Zirconic on 2009-03-06
> **bodhi.zazen said:**
> You can run Keepass in wine.

KeePass won't accept my password when it runs in Wine.

---

### Post by bodhi.zazen on 2009-03-06
OUCH :)

That is odd, I run Keepass in wine all the time.

---

### Post by phaid on 2009-03-06
Can you create a new, test keepass database on windows, put some test information in it and see if that opens?  That should determine if it is an issue with keepassx or the database.  I can open ones created on windows without any issues.  I have KeePassX 0.3.3

---

### Post by Zirconic on 2009-03-08
Phaid,

It worked.  The TEST database I created opened just fine.  Now to figure out why the "real" database won't open.

Thanks again!  At least I've narrowed the possibilities.

---

### Post by Zirconic on 2009-03-08
Found workaround.

1) Create new test database in Windows and export.
2) Open new test database in Ubuntu using Wine.
3) With test database open, import the database you are really after.  It will ask you what you want to do with the currently open (test) database.  Just overwrite it.

Once imported, I exported the database again, closed and reopened KeePass in Wine.  Worked just fine.

Thanks, Phaid!

---

### Post by Zirconic on 2009-03-08
BUT ... KeePass won't perform an Autotype while running from Wine.

Sigh.

---

