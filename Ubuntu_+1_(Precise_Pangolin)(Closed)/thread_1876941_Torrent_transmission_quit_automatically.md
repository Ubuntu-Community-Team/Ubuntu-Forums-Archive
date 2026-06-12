---
title: "Torrent transmission quit automatically"
date: 2011-11-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by raja.genupula on 2011-11-07
For the first time of minimize no problem with it but for the second of minimize its quit.

Ubuntu OS- 12.04 Xubuntu
Envi:Gnome-shell

i am trying to report to launchpad bugs but i am failing at calling this transmission torrent from terminal . with what name it gonna invoke from terminal.

one more thing some times file manager also quit automatically.

Thanks in advance

---

### Post by effenberg0x0 on 2011-11-07
apport-bug transmission-gtk
apport-bug nautilus

---

### Post by raja.genupula on 2011-11-20
Not only in 12.04 , in 11.10 also i am facing same issue. please help me to fix this issue.

---

### Post by cariboo on 2011-11-20
Most executables are located in /usr/bin, so if you aren't sure about the full name of an application, you can open a terminal and cd into /usr/bin, then type:

```
ls -l (first 3 or 4 letters of the application name)*
```

for example if for the full name of trnasmission use the following command:

```
ls -l trans*
```

which will result in the following:

```
cariboo@Alexis-2:/usr/bin$ ls -l trans*
-rwxr-xr-x 1 root root  10320 Oct 21 14:26 transist.flt
-rwxr-xr-x 1 root root 736560 Aug  5 00:26 transmission-gtk
```

---

### Post by effenberg0x0 on 2011-11-20
If you want to learn other options:

mlocate transmission (this is the faster one. It uses a database of files in your PC)
whereis -b transmission (-b means binary)
sudo find / -name "*transmission*" (this is the slowest one. No DB. It really searches all folders when you invoke it)
which transmission

If the program is running, you can see the process (and the binary file location):
ps ax | grep -i transmission

There are others.... but these are the common ones. 

In all the cases, you can generally use a wildcard (the asterisk symbol). E.g.: mlocate transmi*

Another way: When you are on any directory and you press the tab key twice, it shows you the files in that directory.

ls -lha /usr/bin/tran <Press tab twice>. 
If transmission is there, it will autocomplete the above command.

---

