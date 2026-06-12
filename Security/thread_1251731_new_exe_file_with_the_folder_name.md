---
title: "new exe file with the folder name"
date: 2009-08-28
forum: Security
---

### Post by sudhakar on 2009-08-28
In Samba server, everytime i open a folder a new exe file with the folder name is created. 

For eg. if i open picture file i get a new file called picture.exe.

---

### Post by prshah on 2009-08-28
> **sudhakar said:**
> In Samba server, everytime i open a folder a new exe file with the folder name is created. 

For eg. if i open picture file i get a new file called picture.exe.

That's a Windows trojan at work.

It works in this manner; usually, the extentions are hidden by default in Windows. The trojan, once it infects your system, replaces commonly used folder names with .exe files with the same name, and then hides the original folder.

When you view in explorer, you double click the exe file (extension hidden) which executes the trojan, which infects the system if not already infected, and then displays the hidden folder as normal.

Get a good antivirus / anti spyware utility and clean your Windows system. I recommended Kaspersky, it's not free, but it's light and good.

---

