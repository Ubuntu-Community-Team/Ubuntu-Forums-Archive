---
title: "Medibuntu"
date: 2012-10-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jmore9 on 2012-10-01
Hello 

I am trying to get medibuntu repo working on 12.10 but all i get is the following errors :

jeffrm@jeffm-MS-7108:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list 
--2012-10-01 16:47:12--  [http://www.medibuntu.org/sources.list.d/quantal.list](http://www.medibuntu.org/sources.list.d/quantal.list)
Resolving [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org](www.medibuntu.org))... 88.191.127.22
Connecting to [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org)|88.191.127.22|:80](www.medibuntu.org)|88.191.127.22|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-10-01 16:47:13 ERROR 404: Not Found.


Any ideas on how to fix this or is it not fixable right now ?

Thanks in advance for any help.

---

### Post by wojox on 2012-10-01
I had to add them manually and import the key.
```
deb http://packages.medibuntu.org/ quantal free non-free
```

---

### Post by arpanaut on 2012-10-01
OR: simply edit the sources to read precise instead of quantal until the final release,
at which time medibuntu will update their repositories.

---

### Post by jmore9 on 2012-10-01
OK I will try both and see which one works for me.  thanks

---

