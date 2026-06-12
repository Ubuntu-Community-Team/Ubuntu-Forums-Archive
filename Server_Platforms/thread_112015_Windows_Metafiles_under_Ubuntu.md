---
title: "Windows Metafiles under Ubuntu"
date: 2006-01-03
forum: Server Platforms
---

### Post by Oceola on 2006-01-03
I was concerned over the recent warning from Secunia and Frsirt
[http://secunia.com/advisories/](http://secunia.com/advisories/)
[http://www.frsirt.com/](http://www.frsirt.com/)
 in regard to the Windows Meta File problems. It's serious for Windows..
[http://secunia.com/advisories/18255/](http://secunia.com/advisories/18255/)
...and I was wondering if the half dozen or so files in the repositories or under our current softwars are vulnerable.
**libwmf0.2-7** Windows metafile conversion library
Both abiword and Gimp depend on this file

**python2.4-imaging** Python Imaging Library
Dependants: Python-imaging, python2.4-imaging-sane, python2.4-reportlab, python2.4-hymlgen

**Python-imaging  Python Imaging Library**The Python Imaging Library (PIL) 
Dependants: python-imaging-sane, python-reportlab

Also libwmf-dev and Libwmf-doc

---

### Post by hav0x on 2006-01-03
Get serious ... that "exploit" is not actually an exploit... ITS AN ACTUAL FEATURE.
It's dependant on one of those gd<whatever>.dll. T'is a serious issue and windows users should be on their toes. But it's hardly unexpected or even original considering Microsoft's history.
It wont afect non Windows OSes. There's a "demo" of the exploit available i think (might have seen it on /.) Someone should try to wine it! lol

---

### Post by Oceola on 2006-01-05
The reason I posted here was I was looking for something more than a denial or a guffaw. Particularily when Secunia has been fairly accurate and mentioned other systems may be compromised.

With so many different cross platorm programs it seemed logical to ask in a respected Linux forum like this one.

---

### Post by nocturn on 2006-01-05
[QUOTE=Oceola]The reason I posted here was I was looking for something more than a denial or a guffaw. Particularily when Secunia has been fairly accurate and mentioned other systems may be compromised.

With so many different cross platorm programs it seemed logical to ask in a respected Linux forum like this one.[/QUOTE]

It seems that ALL released versions of Windows are affected, this includes everthing from 3.1 up.  But note that even 98 and ME are out of luck on patches...

Non-microsoft systems are not vulnerable.

---

### Post by Oceola on 2006-01-05
Thanks for that....it's all I was looking for.
Wasn't trolling.

---

