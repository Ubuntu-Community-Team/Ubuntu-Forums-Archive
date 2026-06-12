---
title: "Setting up a Server"
date: 2008-07-15
forum: Server Platforms
---

### Post by kubapl on 2008-07-15
Hi I was just wondering if there's a step by step guild with screen shots that shows someone like me (an amateur) on how to set up a simple web sever at home with some extra features like the plesk control panel and of course mysql.

Thanks

---

### Post by ibutho on 2008-07-15
Hi. Look at the tutorials at [howtoforge]("http://www.howtoforge.com/") and you may find something that helps.

---

### Post by kubapl on 2008-07-15
yeah I have went threw that a couple of times. Without great success. Maybe I'll try again and post my errors here. 

Can someone answer how do I check all the directories I have and sub directories inside a directory I have

---

### Post by davidshq on 2008-07-15
I use slicehost's tutorials. Go to slicehost.com and click on community. They have lots of articles focused on configuring ubuntu from the very basics to deploying apache, mysql, etc.
David.

---

### Post by fragtion on 2008-07-16
> **kubapl said:**
> Can someone answer how do I check all the directories I have and sub directories inside a directory I have
The simplest method of performing a recursive directory listing is with the ls command:

> ls -R

ls -lR


The first is a short listing (filename only) and the second version shows a long listing (the output of ls -l but recursive). These commands will perform the recursive listing from the current working directory. Adding a directory name to the end of the commands will start the listing in that directory.

The find command performs recursive searches by default. To duplicate ls -R, use:

> find . -print


The -print option is the default in many versions of find, so just 'find .' will often work. The find command is extremely powerful and is worth reading a few recipes to learn.

---

### Post by timcredible on 2008-07-16
.

---

