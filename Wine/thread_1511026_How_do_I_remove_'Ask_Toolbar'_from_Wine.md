---
title: "How do I remove 'Ask Toolbar' from Wine?"
date: 2010-06-16
forum: Wine
---

### Post by Rytron on 2010-06-16
Hi.
How do I remove 'Ask Toolbar' from Wine? I hit the remove button but the damn thing just remains. Also this 'Ask Toolbar' is not in ~/.local/share/applications/wine/Programs

:confused:

---

### Post by cogadh on 2010-06-16
You could try deleting the program's directory from Wine's "Program Files" directory, then running Wine's uninstaller again. That might force the uninstaller to error out and offer you the option of removing it from the uninstall list.

---

### Post by ghostborg on 2010-06-16
I have not used Wine in a while but I believe the program Ccleaner ran under it, might help you remove it. 
Funny Ccleaner I think by default ask's if you want the ASK toolbar, uncheck those options, its a great program.
[http://www.piriform.com/ccleaner/download]("http://www.piriform.com/ccleaner/download")

If it's a toolbar, I think you can click on View->Toolbars and uncheck it just to get it out of the way.

---

### Post by Rytron on 2010-06-16
Thank you cogadh & ghostborg. I went to the ~/.wine folder and deleted some suspect folders. Then I tryed uninstalling 'Ask Toolbar' again. No luck. Then I ran CCleaner. Joy. I think it may have been a combination of deleting the folders and CCleaner that finally did the trick. ):P

---

