---
title: "Python packages"
date: 2015-12-02
forum: Ubuntu Development Version
---

### Post by owen9 on 2015-12-02
Hi, i am working on a re master script for an open source OS (The Linux schools project) there is an error when creating a  re master with python packages in the chroot, we have had a similar error before but with java not python so we fixed this by removing java packages of the install list, i need to do the same for python however i am not sure which of the packages in the list require python, is there a way to check if a certain program requires python?

---

### Post by zika on 2015-12-02
I would start with this nice thread: [http://askubuntu.com/questions/80655/how-can-i-check-dependency-list-for-a-deb-package](http://askubuntu.com/questions/80655/how-can-i-check-dependency-list-for-a-deb-package) ...  ;)

---

### Post by owen9 on 2015-12-02
Ok thank you, very helpful,

---

### Post by T.J. on 2015-12-02
Try apt-cache depends <package name>

---

### Post by zika on 2015-12-02
> **T.J. said:**
> Try apt-cache depends <package name>As I understood the OP's question, it is a bit other way around. He wants to find all packages that depend on python. I might be wrong...

---

### Post by owen9 on 2015-12-02
Thank you this is a bit quicker!

---

### Post by oldfred on 2015-12-02
Are you into the issue of python2 or python3?

Ubuntu defaults to python2 currently, but you can specify python3 for programs that are python3.
But distributions are in the midst of converting everything from 2 to 3. But they have said for years that python2 would not be standard in next version.

 Ubuntu 16.04 LTS Will Try To Be Python-3-Only, No Python 2 By Default
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.04-Python-3-Hopes](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.04-Python-3-Hopes)

---

### Post by owen9 on 2015-12-02
Python 3 is the issue in chroot, when creating a remaster.

---

