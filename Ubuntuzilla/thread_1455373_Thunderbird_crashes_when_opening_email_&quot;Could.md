---
title: "Thunderbird crashes when opening email &quot;Could not get the JVM manager&quot;"
date: 2010-04-15
forum: Ubuntuzilla
---

### Post by grahams on 2010-04-15
Installed Thunderbird and it is crashing as soon as I try to read an email

I run from the command line and I get the following.

thunderbird 

(thunderbird-bin:23229): GLib-WARNING **: g_set_prgname() called multiple times
MozPlugger: Error: Failed to execute m4.
MozPlugger: Error: Failed to execute m4.
INTERNAL ERROR on Browser End: Could not get the JVM manager
System error?:: No such file or directory

Looks like something is missing or a link is broken. Any clues on how to fix?

---

### Post by nanotube on 2010-04-16
hi,
is this thunderbird from the ubuntuzilla repository, or from ubuntu repos?

---

### Post by grahams on 2010-04-17
Both fail.

2.0 from the standard ubunto repo, 3.0 from mozilla linux download and from ubuntuzilla.

I have java working and can varify from [http://java.com/en/download/help/testvm.xml](http://java.com/en/download/help/testvm.xml)

Do you know where Thunderbird is looking for the JVM?

---

### Post by nanotube on 2010-04-18
Hi

I have no idea - i didn't think thunderbird can even do java...

Anyway, some googling revealed this page with a fix, give it a try and let me know if it helps:
[http://forums.mozillazine.org/viewtopic.php?f=31&t=50237&start=0&st=0&sk=t&sd=a](http://forums.mozillazine.org/viewtopic.php?f=31&t=50237&start=0&st=0&sk=t&sd=a)

---

### Post by grahams on 2010-04-18
Thanks for the reply

I fixed it with brute force. I uninstalled, tb, firefox, java, jre and deleted all mozilla plugins, then reinstalled them all one by one. 

Every is running fine now.

---

### Post by nanotube on 2010-04-18
heh ok, whatever works. :)

---

