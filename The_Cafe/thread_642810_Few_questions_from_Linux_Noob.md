---
title: "Few questions from Linux Noob"
date: 2007-12-17
forum: The Cafe
---

### Post by LinuxTryOut on 2007-12-17
Hey guys, I got a few questions would like to ask. I could answer them by myself but I need it to be more accurate. So, please do me favor by answer few simlple questions. 


1/ what does this command cal 2001 >> 2002 accomplish ?
2 / What do the letters ugo does when look at the file listing?
3/ Define the role of the tail command.
4/ how to add a user account in Linux and have that account be the startup account when the computer is booted.
5/ shell script might be used in how many ways in linux.

---

### Post by frup on 2007-12-17
4/ how to add a user account in Linux and have that account be the startup account when the computer is booted.

Do you mean log in straight away without needing user and password entered?
Did you want that via command line only or just any method of doing it?

---

### Post by jrusso2 on 2007-12-17
Sounds like someone doesn't want to do their homework assignment.

---

### Post by cookieforyou on 2007-12-17
> Sounds like someone doesn't want to do their homework assignment.
:D

1/ Install Ubuntu
2/ Read the FAQ

:D

1/ what does this command cal 2001 >> 2002 accomplish ?
```
cal 2001 >> 2001
``` would be a better idea (creates a calender of 2001 in a file called '2001'). :)
EDIT: '>>' causes the file to be appended with latest listing, ie later doing 'cal 2007 >> 2001' would add the 2007 calender at the end of the '2001' calender created above.

3/ Define the role of the tail command.
```
tail /var/log/messages
```would list the last 10 lines of a file (/var/log/messages in this case).

```
tail -f /var/log/messages
``` on the other hand would continually list the last 10 lines, even if the file were to grow.

4/ [COLOR="Cyan"]how to add a user account in Linux[/COLOR] [COLOR="Red"]and have that account be the startup account when the computer is booted[/COLOR].

Cyan: You need to do a bit of reading up
```
man useradd
```
Red:```
System > Administration > Login Window > Security
```

5/ shell script might be used in how many ways in linux.

I don't know.

---

### Post by fatality_uk on 2007-12-17
> **jrusso2 said:**
> Sounds like someone doesn't want to do their homework assignment.

:lolflag: priceless, but very possible ;)

---

### Post by LinuxTryOut on 2007-12-17
> **jrusso2 said:**
> Sounds like someone doesn't want to do their homework assignment.
Hahhaha it's not like that, I just wanna make sure i have the best answers for the above questions. BTW, thank you Cookieforyou

---

