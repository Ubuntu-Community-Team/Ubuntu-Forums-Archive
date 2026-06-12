---
title: "Warcraft 3 issues"
date: 2008-12-04
forum: Wine
---

### Post by magmon on 2008-12-04
I installed warcraft 3 using wine and removed the movies folder so it will run, but the game is horribly laggy even with everything on low graphics. Is there a fix for this?

---

### Post by mhh91 on 2008-12-04
what is your graphics card??

---

### Post by magmon on 2008-12-04
ATI. I have the proprietary driver for it.

---

### Post by binbash on 2008-12-05
add -opengl : 

wine asdasd.exe -opengl

also be sure you disabled compiz.

---

### Post by magmon on 2008-12-06
Are those codes meant for terminal o.O??

---

### Post by binbash on 2008-12-06
> **magmon said:**
> Are those codes meant for terminal o.O??

yes : 

wine /home/username/.wine/drive_c/Programfiles/etcetc/warcraft.exe -opengl

just fix the way to your warcraft folder

---

### Post by poisonkiller on 2008-12-06
Or if you don't want to use the terminal, right-click Warcraft's shortcut -> Properties -> add " -opengl" (without quotes) in the end of Command:.

---

