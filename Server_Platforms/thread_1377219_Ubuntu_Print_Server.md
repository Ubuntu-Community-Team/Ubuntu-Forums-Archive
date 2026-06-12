---
title: "Ubuntu Print Server"
date: 2010-01-10
forum: Server Platforms
---

### Post by Nxion on 2010-01-10
Well I was doing some googleing and foind some guides but they were pretty old like badger days. My questions is has anyone setup a print server yet in Karmic. I have never done so and would like to learn how but I am not having the best of luck

---

### Post by HermanAB on 2010-01-10
I believe that all you need to do is:
$ sudo apt get cups

---

### Post by munky99999 on 2010-01-10
Samba print server 

[https://help.ubuntu.com/9.10/serverguide/C/samba-printserver.html](https://help.ubuntu.com/9.10/serverguide/C/samba-printserver.html)

---

### Post by noway2 on 2010-01-10
Depending on your needs, it may not even be that complicated.  If you have a printer attached to a computer that you wish to share, you can set the printer as shared.  Then, on the other systems, you can set the server settings under printers to show printers shared by other systems.  No special 'server' software required.

---

