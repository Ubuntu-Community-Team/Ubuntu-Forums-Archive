---
title: "Redirect file to and running filter program for ubuntu on bash windows 10"
date: 2017-09-28
forum: Ubuntu, Linux and OS Chat
---

### Post by kloxe1987 on 2017-09-28
Hi all,currently i am using Ubuntu on Windows 10.
However, when i trying to use ProJect < text.dat   (ProJect is my filter programs)

The following error code occur: 
ProJect:command not found

Is it necessary to create a exe file to make this works?And how?
My directory only have text.dat file and ProJect.cpp file.

---

### Post by TheFu on 2017-09-29
The error says that the file "ProJect" doesn't exist in the PATH.  If it is in the current directory, try ./ProJect.  Case matters.  BTW, not having the current directory in the PATH is very smart from a security standpoint.

Specify the fill path to the program/script you want to use.
Or put that directory into your (the userid used in the shell) PATH environment variable.

A .cpp file is not a program. You'll need to compile it into an executable and ensure the file permissions are set to include executable for the userid trying to run the program. Did you do that?

If you want to become a Unix programmer, it would be good to learn a little more about the OS.  My top tips:
* Never forget that Unix is multi-user.  Always.
* ALL FILES and directories have permissions.
* Everything is a file, unless it is a process.
* Manage your environment carefully for each program that isn't run by an end-userid.

---

### Post by ian-weisser on 2017-09-29
Perhaps a silly question, but have you compiled the ProJect.cpp code into an executable?
If so, where did you put the executable?
C++ is a compiled language, not a scripting language.

---

