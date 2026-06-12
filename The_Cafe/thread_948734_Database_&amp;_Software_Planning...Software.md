---
title: "Database &amp; Software Planning...Software"
date: 2008-10-15
forum: The Cafe
---

### Post by Black Mage on 2008-10-15
Hi all,

I am going to be design some software & database project with a team and I was wondering if there is software on Ubuntu that can help with drawing schemas, uml diagrams, E-R diagrams, etc.

Thanks

---

### Post by rax_m on 2008-10-15
In the repos : [http://bouml.free.fr](http://bouml.free.fr)

Also made dbdesigner4 and jdbcmanager might be useful.

---

### Post by capink on 2008-10-15
check [power architect]("http://www.sqlpower.ca/page/architect"). It is a java app so it can work in linux and windows.

downlaod the program and start the program by opening the jar file as follows:

```
java -jar /path/to/architect.jar
```

Ofcourse you must have java installed. If not, you have to install it first:

```
sudo apt-get install sun-java6-jre
```

---

### Post by Black Mage on 2008-10-23
Thanks for the info. I wasn't able to get Database4 working because it never could find the correct library, even though I downloaded and installed it.

Power Archicture is a pretty nice program. Has a few bugs that causes hitches here and there, such as actually writing the sql to the database, but overall it helps to lay things out.

---

