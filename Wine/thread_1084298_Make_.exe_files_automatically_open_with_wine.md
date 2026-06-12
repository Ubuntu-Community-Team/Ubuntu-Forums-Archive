---
title: "Make .exe files automatically open with wine?"
date: 2009-03-01
forum: Wine
---

### Post by josephellengar on 2009-03-01
Right now mine open with the archive manager, and it's really annoying. Any help would be appreciated.

---

### Post by konqueror7 on 2009-03-01
its just similar to windows, right clicka specific file with a *.exe extension, select 'Properties', then on the 'Open With' tab select 'Wine'...

---

### Post by josephellengar on 2009-03-02
> **konqueror7 said:**
> its just similar to windows, right clicka specific file with a *.exe extension, select 'Properties', then on the 'Open With' tab select 'Wine'...

I did that, and it still automatically opens with the archive manager.  I have to right click every time.

---

### Post by airtonix on 2009-03-02
go back to the properties - > open with tab and remove archive manager.

i suspect you didnt make sure the 'wine' entry was radio checked.

if you look here you will notice that it's possible to select archive manager but not have it as the loader

[IMG]http://dl.getdropbox.com/u/180039/Screenshot-Wow.exe%20Properties.png[/IMG]

Make sure the radio check box is selected for your loader program of choice.

---

### Post by no_angst on 2009-12-08
Thanks guys!  This was bugging me as well.  I guess Nautilus or Wine automatically set it in previous Ubuntu versions during the Wine install?  Anyway, good tip, thanks!

---

