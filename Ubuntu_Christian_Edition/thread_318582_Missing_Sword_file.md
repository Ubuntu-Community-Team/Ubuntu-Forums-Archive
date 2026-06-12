---
title: "Missing Sword file"
date: 2006-12-14
forum: Ubuntu Christian Edition
---

### Post by psycosmyth on 2006-12-14
I was trying to reinstall Gnomesword and it seems to be missing a lib file. I have all repositories enabled and I tried the main and US server. Not sure what to do. I could use another Bible study program but I love Sword. Thank you.

---

### Post by montgoej on 2006-12-14
It's an error with the libsword file. You can get a working package for your architecture [[COLOR="Blue"]here[/COLOR]]("http://packages.debian.org/testing/libs/libsword5c2a")(Debian repos).
Hope that helps, if there are further problems PM me.  I submitted a bug report on Launpad a while back, but nothings happened from it yet.
God Bless,
Jordan Montgomery

---

### Post by psycosmyth on 2006-12-14
Bless you! Not for the link, it's down but you did answer my question and I know what action to take. Merry CHRISTmas!:-D

---

### Post by montgoej on 2006-12-14
I see, the link is down. I got it from another post and forgot to check it.
God Bless,
Jordan Montgomery

---

### Post by mhancoc7 on 2006-12-15
Here is the working libsword .deb.

God Bless, Jereme

---

### Post by psycosmyth on 2006-12-16
You rock!
now I need to learn Arabic, apparently it's the default lang, LOL:D

---

### Post by Moe-loves-ayumi on 2006-12-16
Thanks for the .deb

> **psycosmyth said:**
> You rock!
now I need to learn Arabic, apparently it's the default lang, LOL:DI did ```
sudo apt-get install sword-language-pack-fr
```, then started GnomeSword, changed the settings and changing all occurrences of Ara to Fre. You should install the english language pack and try to do the same.

---

### Post by psycosmyth on 2006-12-19
oui!
did it first thing:)

---

### Post by Eladon on 2007-03-12
You can ditch the Arabic text by running the program from the command prompt like this:
```
sudo gnomesword2
```
Click on the **Edit** menu, then **Module Manager**, highlight **Remove** on the left, locate the **AraSVD** text on the right, and click the **Remove** button.

---

