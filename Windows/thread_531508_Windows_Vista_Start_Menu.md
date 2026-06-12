---
title: "Windows Vista Start Menu"
date: 2007-08-21
forum: Windows
---

### Post by L.A. on 2007-08-21
i know this is an ubuntu forum but i am a user of ubuntu with a question regarding the windows start menu. it is more of a tweak/tutorial question but if it is in the wrong section please move it..

my problem is that i want to delete a file from the start menu but vista doesnt let me and i dont know how to go about doing this. 

here is a pic of the problem circled in red.

when i click the file (MUSIC) nothing happens when i browse its properties it tells me it has 0 bytes and does not show a directory. when i try to move it it doesnt allow me to or to make a shorcut on the desktop. PLEASE HELP!! really annoying

[[IMG]http://img504.imageshack.us/img504/7610/problemae3.png[/IMG]](http://imageshack.us)
[[IMG]http://img504.imageshack.us/img504/7610/problemae3.594bd3b91c.jpg[/IMG]](http://g.imageshack.us/g.php?h=504&i=problemae3.png)

---

### Post by InGunsWeTrust on 2007-08-25
You should always make a registry backup before making changes like that on Windows. My best advice is to try a System Restore and attempt to make the changes again. I presume that the reason that is happening is because your music folder link is referencing a folder that doesn't exist. In Windows XP the path to change where the My Music folder points to is here.

```
HKEY_CURRENT_USER \ Software \ Microsoft \ Windows \ CurrentVersion \ Explorer \ Shell Folders
```

Since few REAL changes were made between Vista and XP, I assume it is still the same. To access that type "regedit" into the run box of Windows and navigate to that key. The changes that need to be made should be apparent. If not let me know.

---

### Post by EndPerform on 2007-08-25
If you right click on the start menu, select properties, you should be able to change the Start Menu properties.  There's a section for the music folder... select "Do not display" and that should remove it.

I'm not in front of my Vista box at the moment, so I apologize for the lack of exact terms

---

### Post by InGunsWeTrust on 2007-08-25
> **EndPerform said:**
> If you right click on the start menu, select properties, you should be able to change the Start Menu properties.  There's a section for the music folder... select "Do not display" and that should remove it.

I'm not in front of my Vista box at the moment, so I apologize for the lack of exact terms

That would simply take away his Music folder. He still wants it he just wants it to work.

---

### Post by smoker on 2007-08-26
just a suggestion, go into the file manager (my computer, or maybe, computer, on vista), look for users, find your name account, then find the start menu folder, open that, and delete the shortcut from there,

best of luck

---

### Post by EndPerform on 2007-08-26
> **InGunsWeTrust said:**
> That would simply take away his Music folder. He still wants it he just wants it to work.

That's what he wants:
> 
my problem is that i want to delete a file from the start menu but vista doesnt let me and i dont know how to go about doing this.


---

### Post by InGunsWeTrust on 2007-08-26
> **EndPerform said:**
> That's what he wants:

Actually I believe he is trying to customize his context menus to have Delete in them so he can delete the contents from the start menu. If you read the tutorial that he posted that he followed that is what it is for. I don't know why were are squabbling over it though he isn't even posting anymore he is probably already done haha.

---

### Post by ocgthatsme on 2007-12-23
Hi there.. I googled this exact problem and came up with this page.. I've tried adjusting the registry links as suggested by InGunsWeTrust but still the link isn't working.. I store all my music on an external harddrive, and for some reason it changed itself from G:\ to H:\ (I think maybe after I installed MagicISO and used a virtual drive when my harddrive wasn't connected. Anyway, that's screwed up all my links, including the 'Music' link on my Vista Start Menu... 
Any help much appreciated! :)

---

### Post by InGunsWeTrust on 2007-12-23
> **ocgthatsme said:**
> Hi there.. I googled this exact problem and came up with this page.. I've tried adjusting the registry links as suggested by InGunsWeTrust but still the link isn't working.. I store all my music on an external harddrive, and for some reason it changed itself from G:\ to H:\ (I think maybe after I installed MagicISO and used a virtual drive when my harddrive wasn't connected. Anyway, that's screwed up all my links, including the 'Music' link on my Vista Start Menu... 
Any help much appreciated! :)

You should just be able to re-edit the links in the same way for G:\WhateverFolderYourMusicIsIn to H:\WhateverFolderYourMusicIsIn or is that for some reason not working?

---

### Post by ocgthatsme on 2007-12-23
Yeh that's working.. I've changed the links in Shell Folders and User Shell Folders in the registry to H:\ instead of G:\.. the link in the start menu still isn't working though :-\

---

### Post by InGunsWeTrust on 2007-12-24
I don't know what to say then, I have had a few friends that have had problems with all kinds of links in their Vista start menu not doing anything when it is clicked on. Try to set it to the default location and see if it is still not working; if it is not then it is a good chance your link is done correctly but there is an unknown problem with your start menu. It would not supprise me if it was just another Vista issue. I know about 6 people that have "upgraded back to XP." And the best advice I can give is to do the same.

---

