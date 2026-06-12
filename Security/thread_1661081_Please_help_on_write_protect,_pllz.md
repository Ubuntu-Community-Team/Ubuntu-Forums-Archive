---
title: "Please help on write protect, pllz"
date: 2011-01-06
forum: Security
---

### Post by iyalah on 2011-01-06
Hi All,

I am new on ubuntu things.

I still searching how to write prote file on ubuntu. I means people could open file but could not copy or move the file. Is it possible on ubuntu?

Thanks in advanced :razz:

---

### Post by JeffDavidoff on 2011-01-06
[SIZE=2]**Write protecting a file using chmod command:**

[/SIZE]   [SIZE=2]Let say you want to write protect the file called data.txt so that no other users can change it, enter:
```
$ chmod go-w data.txt
```To provide back permission use:
```
$ chmod go+w data.txt
```[/SIZE]   [SIZE=2]

For more examples: [Howto: Linux Write protect a file]("http://www.cyberciti.biz/faq/linux-write-protecting-a-file/")[/SIZE]

---

### Post by sanderd17 on 2011-01-06
Check this site as reference: [http://linuxcommand.org/](http://linuxcommand.org/)

the "learning shell" part is short (8 pages to be precise) and should be read by any new linuxer. The "scripting" part isn't needed if you are a regular user.

---

### Post by bodhi.zazen on 2011-01-06
> **iyalah said:**
> Hi All,

I am new on ubuntu things.

I still searching how to write prote file on ubuntu. I means people could open file but could not copy or move the file. Is it possible on ubuntu?

Thanks in advanced :razz:

If they can read a file they can copy it.

You can prevent moving the file with the correct permissions.

---

