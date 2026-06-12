---
title: "Wine Source List error"
date: 2010-01-30
forum: Wine
---

### Post by Nordite on 2010-01-30
I am trying to update wine and got this error.
I am new to Ubuntu and don't know what to do.
!DOCTYPE' is not known on line 1 in source list

---

### Post by howefield on 2010-01-30
Post the contents to your sources.list, looks like you have something in there you shouldn't.

From a terminal, type

```
cat /etc/apt.sources.list
```

---

### Post by Nordite on 2010-01-31
Here is what I got:

cat: /etc/apt.sources.list: No such file or directory

Nordite

---

### Post by howefield on 2010-01-31
Many apologies, that was my typo. The command should have been

```
cat /etc/apt/sources.list
```

In essence, what you want to do is edit out the line starting with !DOCTYPE and save the file, then do an update.

To open and edit
```
gksudo gedit ect/apt/sources.list
```

Then update, hopefully with no errors :0
```
sudo apt-get update
```

---

