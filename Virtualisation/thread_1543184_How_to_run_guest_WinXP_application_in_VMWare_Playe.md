---
title: "How to run guest WinXP application in VMWare Player"
date: 2010-07-31
forum: Virtualisation
---

### Post by ZeroLinux on 2010-07-31
I worked around this problem until solved it
Task: Run, for example, ms word application installed in guest winxp os from host ubuntu os by clicking on the name of the document
Sulution:
1) Create a file, for example, winword in /bin directory
(sudo gedit /bin/winword) with the following content
vmware-unity-helper --run "/home/USERNAME/vmware/Windows XP/Windows XP.vmx" winword $1 
(don't miss $1 - without it only apllication will start, with %1 we have confusing error)
where USERNAME, and "Windows XP" are yours
2) Make it executable (sudo chmod +x /bin/winword)
3) Connect winword with the needed extention to start MS Word along with your file

It works only with English named files

---

