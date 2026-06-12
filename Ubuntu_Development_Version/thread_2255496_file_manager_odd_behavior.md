---
title: "file manager odd behavior"
date: 2014-12-05
forum: Ubuntu Development Version
---

### Post by edsloter on 2014-12-05
I have the file manager ticked to the launcher bar, I can left click it and it does absolutely nothing at all, I must right click and open a new window before the file manager will open at all, even when no other instances are running.

---

### Post by ventrical on 2014-12-05
Works fine here.

---

### Post by edsloter on 2014-12-06
any help on fixing this issue?

---

### Post by mc4man on 2014-12-06
you can try this - 
right click on launcher icon > unlock from launcher
Then - 
alt+F2 > nautilus -q
alt+F2 > gtk-launch nautilus
Lock that icon & test

If still the same then look in ~/.local/share/applications & /usr/local/share/applications  for a nautilus .desktop, if found delete

---

### Post by rburkartjo on 2014-12-07
and works fine on my end. just upgraded to 15.04 today.

---

### Post by edsloter on 2014-12-13
well I got it working, although 

```
ed@ed-X551MA:~$ gtk-launch nautilus
gtk-launch: no such application nautilus
ed@ed-X551MA:~$ 


```

gtk-launch didn't work. i just typed nautilus and it worked.

---

### Post by mc4man on 2014-12-13
> **edsloter said:**
> well I got it working, although 

```
ed@ed-X551MA:~$ gtk-launch nautilus
gtk-launch: no such application nautilus
ed@ed-X551MA:~$ 


```

gtk-launch didn't work. i just typed nautilus and it worked.

"nautilus" in the terminal runs the nautilus binary (typically /usr/bin/nautilus), gtk-launch nautilus uses nautilus.desktop to run whatever is on it's Exec= line (typically Exec=nautilus --new-window %U

So for whatever reason you've lost nautilus.desktop in an applications folder that's searched (typically /usr/share/applications with a display name of Files, a real name of nautilus.desktop

---

