---
title: "APT-GET ERROR - Please help me!"
date: 2005-06-05
forum: Repositories &amp; Backports
---

### Post by cusco on 2005-06-05
hi.. I messd arround with armagetronad.. then I wanted to remove it and I got this error:

cusco@Portatil:~$ sudo apt-get remove armagetronad
Reading package lists... Done
Building dependency tree... Done
E: The package armagetronad needs to be reinstalled, but I can't find an archive for it.
cusco@Portatil:~$

then I open synaptic and it says...

E: The package armagetronad needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.




now everytime I want to use apt-get for anything I can't:

cusco@Portatil:~$ sudo apt-get install supertux
Reading package lists... Done
Building dependency tree... Done
E: The package armagetronad needs to be reinstalled, but I can't find an archive for it.
cusco@Portatil:~$


Please help me

---

### Post by cusco on 2005-06-05
sory this is in hoary.. my mistake :(

---

### Post by az on 2005-06-05
1.  I moved your thread, as you mentioned...

2.  Where did you get this package?

3.  Does

sudo dpkg --clear-avail

help?


If not, then it is a dependancy thing:  post the result from

apt-cache show armagetronad

---

