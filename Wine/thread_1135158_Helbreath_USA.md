---
title: "Helbreath USA"
date: 2009-04-24
forum: Wine
---

### Post by wolfyking2 on 2009-04-24
I tried to install Helbreath USA, and the installation went fine.  It had to update, I let it do that, but about halfway the patcher quit.  And now the game won't run because the patcher quits right away.

and I get this error in the terminal

user@ubuntu:~$ '/home/user/Desktop/Helbreath USA.desktop' 
bash: /home/user/Desktop/Helbreath USA.desktop: Permission denied
user@ubuntu:~$ '/home/user/Desktop/Helbreath USA.desktop' 
/home/user/Desktop/Helbreath USA.desktop: line 1: [Desktop: command not found
/home/user/Desktop/Helbreath USA.desktop: line 2: USA: command not found
err:module:import_dll Library msvcp71.dll (which is needed by L"C:\\Program Files\\Helbreath USA\\Helgame.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Helbreath USA\\Helgame.exe" failed, status c0000135
/home/user/Desktop/Helbreath USA.desktop: line 6: Files/Helbreath: No such file or directory

---

### Post by hikaricore on 2009-04-24
Why are you trying to run .desktop files from a terminal...

err:module:import_dll Library **msvcp71.dll** (which is needed by L"C:\\Program Files\\Helbreath USA\\Helgame.exe") not found

Read up on using winetricks and install the appropriate dlls.

---

