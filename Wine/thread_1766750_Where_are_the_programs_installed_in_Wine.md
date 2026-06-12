---
title: "Where are the programs installed in Wine?"
date: 2011-05-24
forum: Wine
---

### Post by DayLite on 2011-05-24
I can't find where all the programs are that were installed using wine. I am using Unity and don't no how to find them.

I installed IrfanView with Wine. Now I downloaded the plugIns, the instructions on their site is for windows:
> **How to install IrfanView PlugIns?** 

1) Download all PlugIns, see below
2) Click on the PlugIn file (irfanview_plugins_XYZ_setup.exe)
3) PlugIns will be installed into IrfanView "PlugIns" directory 


Where is the folder?

---

### Post by beew on 2011-05-24
Just open the dash and find them  like you would other programs (check "all applications"). They are no longer "in one place".

---

### Post by DayLite on 2011-05-24
> **beew said:**
> Just open the dash and find them like you would other programs. They are no longer "in one place".

I understand the dash to launch the program.  What I am asking is where is the folder located so I can add some dlls into it.

---

### Post by beew on 2011-05-24
> **DayLite said:**
> I understand the dash to launch the program.  What I am asking is where is the folder located so I can add some dlls into it.

It is still inside ~/.wine/drive_c/Program Files (something like that)

---

### Post by nerdy_kid on 2011-05-24
search for "drive C" in dash.

---

### Post by Paqman on 2011-05-24
Wine has a hidden folder (.wine) within your home directory. Inside that is a fake Windows C drive that it installs everything into.

---

### Post by DayLite on 2011-05-24
> **beew said:**
> It is still inside ~/.wine/drive_c/Program Files (something like that)

I don't know where it is:confused:.  Do I find it under 'file system'. Is it hidden?

---

### Post by beew on 2011-05-24
Open File Manager (top of Unity bar) You should be in your home directory(the directory with your user name). Click "show hidden files" under the "View" tab, you will be able to fine the folder .wine.

---

### Post by uRock on 2011-05-24
Moved to Wine sub-forum.

---

### Post by DayLite on 2011-05-24
> **nerdy_kid said:**
> search for "drive C" in dash.

Thanks :D I found it in the dash.

---

