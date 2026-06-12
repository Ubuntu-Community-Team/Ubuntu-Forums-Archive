---
title: "What's the secret to using Wine/"
date: 2009-12-18
forum: Wine
---

### Post by Docaltmed on 2009-12-18
This is going to sound like a complaint, but it isn't.

I have yet to get a single program to work under Wine. These are industry-specific apps, so I'm not finding any help from the Wine database. But on the other hand, they aren't very complicated, either. Just a couple of VBasic programs.

I don't even know where to begin to debug the things, so I guess that's what I'm asking. What error messages should I look for, is there a class of error message that should red-flag the app as a hopeless case? Download dlls? 

Actually, I just want you guys to tell me what the secret password is to make all these programs work!

---

### Post by ajackson on 2009-12-18
There is always the [sticky]("http://ubuntuforums.org/showthread.php?t=885111") at the top of this forum or the [Getting Help]("http://www.winehq.org/help/") page over at the Wine website.

---

### Post by ajgreeny on 2009-12-18
You could always start the program using the terminal instead of the Wine menu.  You may then get some error which could help.

---

### Post by beastrace91 on 2009-12-18
> **ajgreeny said:**
> You could always start the program using the terminal instead of the Wine menu.  You may then get some error which could help.

+1 on that one. Also - keep in mind Wine technology is no where near perfect, in some cases the applications just won't run (yet).

~Jeff

---

### Post by JayKay3000 on 2009-12-18
My secret that works is:


[LIST]
[*]stick with the free open source software.
[/LIST]


[LIST]
[*]Keep windows duel booted as it's just a lot simpler and thats going to use... ...what? an extra 15GB to keep it on your system.
[/LIST]

---

### Post by beastrace91 on 2009-12-18
> **JayKay3000 said:**
> [LIST]
[*]Keep windows duel booted as it's just a lot simpler and thats going to use... ...what? an extra 15GB to keep it on your system.
[/LIST]

My bare 7 install with just a couple apps takes 22gigs... Meaning it eats 30 gigs of my HDD >.< Stupid bloated OS

~Jeff

---

### Post by YokoZar on 2009-12-19
> **Docaltmed said:**
> This is going to sound like a complaint, but it isn't.

I have yet to get a single program to work under Wine. These are industry-specific apps, so I'm not finding any help from the Wine database. But on the other hand, they aren't very complicated, either. Just a couple of VBasic programs.

I don't even know where to begin to debug the things, so I guess that's what I'm asking. What error messages should I look for, is there a class of error message that should red-flag the app as a hopeless case? Download dlls? 

Actually, I just want you guys to tell me what the secret password is to make all these programs work!
If they're all visual basic apps, they're probably breaking for the same reason.

Try getting [Winetricks](http://wiki.winehq.org/winetricks) and using it to install the appropriate Visual Basic Runtime from Microsoft.  Wine's out of the box support for visual basic apps isn't very good (as you've noticed), but having the Microsoft runtime there can help.

---

### Post by Docaltmed on 2009-12-19
ka-ching! Thank you very much YokoZar, that was exactly what I needed!

> **YokoZar said:**
> If they're all visual basic apps, they're probably breaking for the same reason.

Try getting [Winetricks](http://wiki.winehq.org/winetricks) and using it to install the appropriate Visual Basic Runtime from Microsoft.  Wine's out of the box support for visual basic apps isn't very good (as you've noticed), but having the Microsoft runtime there can help.

---

