---
title: "AutoRun.exe"
date: 2011-02-25
forum: Wine
---

### Post by USAFDirtBoyz10 on 2011-02-25
I've had issues with installing software and drivers from disks that require AutoRun.exe.  Does anyone know how to solve this issue.  Also, I am new to Ubuntu and to Linux.  I have always used Windows as an OS, and I would like to know more about Ubuntu.  I am currently using Ubuntu 10.10.

---

### Post by cogadh on 2011-02-25
First of all, you can't install drivers with Wine, Windows drivers do not work in Linux, no matter how you try to install it. As for installing software from disk, by default, Ubuntu prevents executables from running (its a security feature), but you can get around it by using the terminal to "wine" the executable:
```
cd /media/<disk mount path>
wine autorun.exe
```
Change that "<disk mount path>" to the correct directory for the disk you are trying to install software from.

---

### Post by USAFDirtBoyz10 on 2011-02-25
I apologize for my ignorance on the issue.  I realized after reading several of the other forums that wine was not the correct subject.  However, I would appreciate it if someone could run me through installing motherboard drivers from the install disk.  Or if the drivers need to be installed at all.

---

### Post by cogadh on 2011-02-25
Like I said, you can't install Windows drivers in Linux, no matter what. Most of the time, you aren't going to need anything like mobo drivers anyway (Linux handles that stuff natively) but if something like that is required, you should check the mobo manufacturer's website for Linux specific drivers.

---

### Post by USAFDirtBoyz10 on 2011-02-25
I appreciate the help, and again sorry for my ignorance.

---

