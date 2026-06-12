---
title: "HELP: Using an Applications Commandline Parameters"
date: 2009-06-03
forum: Wine
---

### Post by WolfyAU82 on 2009-06-03
How do I use a Windows Application's command line parameters?

For example in windows if I wanted to use a specific setting I'd ordinarily add this to the shortcut or punch it out in the command prompt:

"C:\game\start.exe" -hires

Now how would I use that same switch within the Linux/WINE environment?

---

### Post by asdfoo on 2009-06-03
> **WolfyAU82 said:**
> How do I use a Windows Application's command line parameters?

For example in windows if I wanted to use a specific setting I'd ordinarily add this to the shortcut or punch it out in the command prompt:

"C:\game\start.exe" -hires

Now how would I use that same switch within the Linux/WINE environment?


cd .wine/drive_c/game
wine ./start.exe -hires

---

### Post by WolfyAU82 on 2009-06-05
thanks

---

