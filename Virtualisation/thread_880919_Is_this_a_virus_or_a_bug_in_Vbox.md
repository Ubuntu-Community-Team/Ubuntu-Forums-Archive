---
title: "Is this a virus or a bug in Vbox?"
date: 2008-08-05
forum: Virtualisation
---

### Post by Dark Aspect on 2008-08-05
Hello

I had windows XP installed on a 12 Gb NTFS virtual disk on Virtualbox for a few windows only applications like win32 compilers and such.I had also created a network shared drive that was my entire home folder on Ubuntu.However at random times when I browsed the networking drive XP would sudden display a BSOD and than reset quickly.I figured since I had browsed the net a little with internet explorer that it was a virus so I deleted my Vbox directory with the 12 Gb windows XP file.

Now I have reinstalled windows XP on Vbox but I still have the same BSOD problem when I click on some files on the network drive.I have scanned my entire 160 Gb Ubuntu system with ClamTk (including my root),so is this a Virus affecting my windows XP or a bug inside Vbox?

all the crashes occurred with .rar files if that makes a difference,

---

### Post by tamoneya on 2008-08-05
sounds more like a bug to me.  It doesnt make much sense for a virus to just BSOD you.  A virus will typically want your computer to remain operational so it can use it as a bot or something like that.  Try filing a bug report with virtualbox.

---

### Post by PCessna on 2008-08-05
Bug, Like the guy above me said, make a bug report, I also have problems dragging files from host to virtual machine, but that's because they haven't developed that feature yet which would save me SOOOOOOOOOOOOO (you get my point) much time.

---

### Post by Masoris on 2008-08-06
Virtualbox shared folder function is always unstable.

Install newest Virtualbox that has the most stable shared folder, if you have still problem on newest version, that will be :sad:.

---

### Post by Dark Aspect on 2008-08-06
Hm,I am the latest version.Its not too bad since I can just restart vbox.Would it make it more stable if the Network shared was only one directory instead of my entire home folder?

I guess I'll send Vbox a bug report.

---

