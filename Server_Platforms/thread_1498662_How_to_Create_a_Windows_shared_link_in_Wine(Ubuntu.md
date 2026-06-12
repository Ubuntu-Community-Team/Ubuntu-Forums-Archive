---
title: "How to Create a Windows shared link in Wine(Ubuntu)"
date: 2010-06-01
forum: Server Platforms
---

### Post by harsha.angadi on 2010-06-01
I have installed Windows 2003 Server, on that i have installed VMware and in VMware i have installed Ubuntu.Now my requirement is i want to run a Windows Application shortcut from Ubuntu, for that i have installed wine on Ubuntu.Now i have copied and pasted the Shortcut of that Windows Application on Ubuntu's Desktop. When i check the Windows Application shortcut properties its path will be something like this \\192.168.1.15\Application\Application.exe, but i am unable to run that Application shortcut in Ubuntu. If i try samething on the other windows system on network it works fine. Actually its a thin client server architecture where i want my thin client to use ubuntu and access the windows application shortcut and run the windows application shortcut on ubuntu.
To be more clear my windows 2003 server runs a windows application which has MSSQL as database. Now on my ubuntu system the login page is able to popup but when i give username and password it gives something like server not found,how do i need to approach this issue.
Please help me in this regard. If this is not clear please tell me how should be my input. Thanking you in advance.

---

### Post by new_tolinux on 2010-06-01
At start \\ is something Windows uses, not something Ubuntu uses.
In Ubuntu you'll normally mount a share to a folder.

It may be that replacing the backslashes (\) with slashes (/) does the trick.

---

### Post by harsha.angadi on 2010-06-01
I have succeeded in mounting the drive now when i try to open the application its not able to connect to server/database. Login screen is able to popup in Ubuntu system but when i give user name and password is not able to connect to database.How to create a database connection.so that the application runs smoothly.Thanks in advance.

---

