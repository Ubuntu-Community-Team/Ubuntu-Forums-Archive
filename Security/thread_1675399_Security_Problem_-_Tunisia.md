---
title: "Security Problem - Tunisia"
date: 2011-01-25
forum: Security
---

### Post by simsym05 on 2011-01-25
Good evening,

i'm from Tunisia, i'm using Xubuntu 9.10, inside windows.

The last months, before the revolution in Tunisia, the gouverment was trying to steal our usernames, and passwords, many technic was used for example in frensh language: injection java script.

i see my computer very very slow,
last night i wanted to shutdown the system, but only the os ubuntu has been shutdown but the computer still runing (fun and processor, LED of hard disc...)

i need your help please to scan my computer and check the ports opened.

Thanks in advance.

Samy

---

### Post by Joe of loath on 2011-01-26
I don't think you're going to have a problem. Any attack that may or may not have happened will have been designed for Windows, and won't work in Linux.

---

### Post by nevius on 2011-01-26
Samy, are you running Xubuntu inside a virtual machine (Virtualbox, VMware, etc.) or is it a Wubi or standard install of Xubuntu?

The best utility to do a port scan on your computer is Nmap (or zenmap - the GUI version). It is best to run Nmap from a different computer than the one you are scanning. You can also see what ports Windows is listening on by doing the following from inside Windows. (these are based on what I can remember off the top of my head about Windows XP because I stopped using Windows before Vista / 7)

Click on the Start Menu then look for "Run" and type in the word "command" or "cmd". This should open up the Windows shell. Then type in ```
netstat -a
``` or if you want to see  the executable involved in creating each connection or listening port: ```
netstat -b
``` There are lots of malware / virus scanners out there for Windows. I think Microsoft Security Essentials and Malware Bytes are pretty good. 

In your situation your best option may to be back up your data and reformat / reinstall your windows partition or just install Ubuntu on your computer.

---

### Post by simsym05 on 2011-01-26
Hi Nevius;

I'm using Xubuntu as a partition;
when i run my computer i have the choice to run windows or xubuntu, so it is complitely independant from windows (only the install has been done with windows)

How can  i make a scan for xubuntu, please?

---

