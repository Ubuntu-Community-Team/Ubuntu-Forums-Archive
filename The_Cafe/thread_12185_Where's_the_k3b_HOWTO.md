---
title: "Where's the k3b HOWTO?"
date: 2005-01-22
forum: The Cafe
---

### Post by CowPie on 2005-01-22
It used to be found on ubuntulinux.org wiki, but now the only one I can find is in italian?  I can't find one on the forum either?

---

### Post by Perfect Storm on 2005-01-22
What do want to know?

This is how I did it.
Setup the reportsitories (here's a howto [http://ubuntuguide.org/index.html](http://ubuntuguide.org/index.html) )
then select k3b and cdrdao packages and install them
open the terminal and write:

sudo k3b

---

### Post by jdong on 2005-01-22
[QUOTE=Artificial Intelligence]

sudo k3b[/QUOTE]


That's a no-no. Run **gksudo k3b**. Otherwise, you may break your ICEAuthority. Try **rm -f /home/user/.ICEauthority** if X refuses to start.

---

### Post by Perfect Storm on 2005-01-22
oops  :mrgreen:

---

### Post by CowPie on 2005-01-23
[QUOTE=jdong]That's a no-no. Run **gksudo k3b**. Otherwise, you may break your ICEAuthority. Try **rm -f /home/user/.ICEauthority** if X refuses to start.[/QUOTE]
 Thanks guys, I'll try it...

---

### Post by watchitman on 2005-01-26
That's cool and all but you guys didn't answer his question, what happened to the how-to in the WIKI?

---

### Post by Strid on 2005-03-04
[QUOTE=jdong]That's a no-no. Run **gksudo k3b**. Otherwise, you may break your ICEAuthority. Try **rm -f /home/user/.ICEauthority** if X refuses to start.[/QUOTE]

I've had that problem. What happened, and what did I do wrong? I went crazy and had to reinstall Ubuntu. :) (Newbie here...)

---

### Post by Potemkin on 2005-03-04
[QUOTE=Strid]I've had that problem. What happened, and what did I do wrong? I went crazy and had to reinstall Ubuntu. :) (Newbie here...)[/QUOTE]
I've had the same problem myself a couple of times; you don't have to reinstall Ubuntu to fix it. As the man said, it's caused by K3b changing the permissions of the .ICEauthority file. If X refuses to boot, just open a terminal and delete the file. It's one of those problems which seems catastrophic, but in fact is caused by a small error, and can be fixed very easily.

---

### Post by poofyhairguy on 2005-03-05
[QUOTE=watchitman]That's cool and all but you guys didn't answer his question, what happened to the how-to in the WIKI?[/QUOTE]

Here, I made one:

[http://www.ubuntulinux.org/wiki/K3BHowto](http://www.ubuntulinux.org/wiki/K3BHowto)

---

### Post by BorgHunter on 2005-03-05
[QUOTE=Potemkin]I've had the same problem myself a couple of times; you don't have to reinstall Ubuntu to fix it. As the man said, it's caused by K3b changing the permissions of the .ICEauthority file. If X refuses to boot, just open a terminal and delete the file. It's one of those problems which seems catastrophic, but in fact is caused by a small error, and can be fixed very easily.[/QUOTE]
 Or, you can do **$sudo chown username /home/username/.ICEauthority** which involves less deleting...

It greatly confused me the first time it happened, too. For the record, I still haven't gotten my k3b to work...mostly because I've been too lazy to fiddle with SCSI emulation and such...

---

