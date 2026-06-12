---
title: "Print from Ubuntu server to Windows XP shared printer"
date: 2009-07-10
forum: Server Platforms
---

### Post by fafifurnir on 2009-07-10
Hello to all

I have Ubuntu server with installed SMB for sharing folders to XP.
Now I need to print from Ubuntu server (no Gui interface) to a printer shared on a XP machine.

I know to do this in desktop enviroment :

      Go to System -> Administration -> Printing and open the New Printer icon.
   2.

      Select Network Printer and Windows Printer (SMB)
         1.

            At Host, enter the computer name or IP-address of the Windows XP machine.
         2.

            At Printer, enter the share name of the printer.
         3.

            At Username, enter guest. 
etc.

How to do this from a command line ?

---

### Post by wojox on 2009-07-10
use

```
lpr /path/to/file/printme.txt
```

---

