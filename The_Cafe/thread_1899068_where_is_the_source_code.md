---
title: "where is the source code?"
date: 2011-12-22
forum: The Cafe
---

### Post by loser55 on 2011-12-22
I want to see source code for some of my programs where is it?

---

### Post by amjjawad on 2011-12-22
> **loser55 said:**
> I want to see source code for some of my programs where is it?

Hello and Welcome to Ubuntu Forum :)

Are you talking about the installed application?

---

### Post by cariboo on 2011-12-22
If you have source code enabled in Software Sources, you can download the source code for anything in the repositories. After setting up the source repositories, you can use you favorite method of installing packages, by using for example:

```
linux-source
```

---

### Post by ninjaaron on 2011-12-23
In addition to compiled binaries, some of your applications are almost certainly written in python and Java script, which are uncompiled scripting languages.  You can see their source simply by opening the executable and resources in a text editor (most of these types of files will be stored in /usr, in various sub-folders).

Furthermore, there are many system daemons and init programs which are simple shell scripts.  You can find lots of this kind of source in /etc.

---

### Post by oldos2er on 2011-12-23
```
apt-get source <package>
```

---

