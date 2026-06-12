---
title: "bulk file rename script"
date: 2013-02-19
forum: Server Platforms
---

### Post by cabalsdemon on 2013-02-19
i have email from a backup  and they have different endings then my email now on my ubuntu server i need to rename the last part of every file in this directory "ezewhcom_2,"  without quotes to a the word "new" without quotes
and i am not sure how to do this
can someone please help me

thank you very much

---

### Post by hawkmage on 2013-02-19
I often use bash variable substitution with a for statement to do things like this but without a better example of what the original name is and what you want to change it to I can't say if it will work.

---

### Post by cabalsdemon on 2013-02-20
my email folder i am putting back in to my web server because it crashed an this is a backup of my files well they have the wrong extension for it to read them right so i need to change the extension so it can

ezewhcom_2, is on the ending of every email in the folder i just need to change all of them to new i would do it manually but there are 11 thousand files :lolflag:

---

### Post by schragge on 2013-02-20
There's [rename.ul]("http://manpages.ubuntu.com/manpages/precise/en/man1/rename.ul.1.html") command for it.
```

find mailfolder/ -type f -name \*ezewhcom_2, -exec rename.ul ezewhcom_2, new {} +

```
Or try [rename]("http://manpages.ubuntu.com/manpages/precise/en/man1/prename.1.html") script that comes with perl. It understands perl regular expressions.
```

find mailfolder/ -type f -exec rename 's/ezewhcom_2,$/new/' {} +

```

---

### Post by cabalsdemon on 2013-02-20
well i didnt try the rename.ul  but rename isnt working i dont undestand

---

### Post by cabalsdemon on 2013-02-20
never mind you are right brain fart putting wrong letters in thank you very much schragge

---

### Post by hawkmage on 2013-02-20
OK, I would have done this:
```
cd /mailfolder
for F in *.ezewhcom_2;do mv ${F} ${F/.ezewhcom_2/.new}
```

---

