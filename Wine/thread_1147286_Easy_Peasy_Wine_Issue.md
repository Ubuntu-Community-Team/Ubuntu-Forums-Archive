---
title: "Easy Peasy Wine Issue"
date: 2009-05-03
forum: Wine
---

### Post by DeadlyAura on 2009-05-03
I'm currently running Ubuntu 8.10 Intrepid Easy Peasy Edition for my Eee-PC.

Whenever I install a program with wine, the program installs correctly and installs all of the icons correctly in the wine menu.

However, after I remove a program from wine, the shortcut icons in the wine menu do not disappear. In a desperate attempt to get rid of them, I removed wine completely and reinstalled it again. Even after doing this, the icons still appear. This would lead me to believe that the shortcuts are stored in a folder that is unaffected by the wine installer.

Does anyone know a fix for this issue?

Thanks

---

### Post by kostkon on 2009-05-03
You can just right-click on your menu and select *Edit Menus* and the *Alacarte* menu editor will load. Then just delete them from there.

It's indeed easy peasy to remove them ):P

---

### Post by DeadlyAura on 2009-05-03
> **kostkon said:**
> You can just right-click on your menu and select *Edit Menus* and the *Alacarte* menu editor will load. Then just delete them from there.

It's indeed easy peasy to remove them ):P

Actually, right click on the menu didn't work, so I launched it through terminal instead.

I was able to disable the icons in the menu, but for some reason it won't let me actually delete them. Although that isn't a big deal to me, o you have any idea why that is?

---

### Post by kostkon on 2009-05-03
> **DeadlyAura said:**
> Actually, right click on the menu didn't work, so I launched it through terminal instead.
Actually, I meant right-click here
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=112295&stc=1&d=1241378452[/IMG]
not on the Wine menu.
> **DeadlyAura said:**
> I was able to disable the icons in the menu, but for some reason it won't let me actually delete them. Although that isn't a big deal to me, o you have any idea why that is?
Hmmm, sorry no, but it's not a big deal, indeed. Just leave them disabled for the moment.

---

### Post by Maxepr on 2009-05-08
aura, I use ubuntu 9.04. I had the same problem. I deleted a windows program through wine and the icons stayed. I even deleted Wine....they were still there. ARG! Here's what I did, it seemed to work. Right click on "Aplications" on the task bar: Click on "edit Menues". You'll see all your apps on the list. Go to "wine", highlight it and hit "delete". It worked for me. Then I reinstalled "Wine". I am now back to normal. 

Maxepr

---

### Post by Bearded-flower on 2009-05-09
I am using easy peasy (not for much longer HAHAHAhaHA sudo rm-fm will fix that! HAHAHAHA. no actuly im just installing jaunty overtop of it, it has been nothig but trouble for me) i have the exact same problem! GRRRR

---

