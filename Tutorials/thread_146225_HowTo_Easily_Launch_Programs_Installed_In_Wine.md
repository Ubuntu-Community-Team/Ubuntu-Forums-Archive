---
title: "HowTo: Easily Launch Programs Installed In Wine"
date: 2006-03-17
forum: Tutorials
---

### Post by noob_Lance on 2006-03-17
Hey, I thought i would share an easy way to launch your programs that you have installed with Wine (not xwine because guis are for suckers :p)

But Here Ill Set you through the process.. .its rather short so try to keep attention focused lol.

In this HowTo, im going to use the Program i reciently installed, Photoshop :)

First Step. 
Open Applications Menu Editor
Applications > System Tools > Application Menu Editor

Second Step. 
Click The New Menu Button.

Fill Out Wine Apps (or whatever you want) for the name. and hit enter. You can Add an Icon if you wish, i prefer to keep mine default for now. 

Third Step.
Click On The New Menu Item You Just Created. Now Click The Button That Says New Entry. 

Fill Out the Form the way you like. 
as for the command. youll want to enter:
wine /home/{user}/.wine/drive_c/Program\ Files/{path to your program.exe}

Choose an Icon If You Wish, again i didnt due to preference. And lastly you want to click the 'run in terminal' button. 

Close The Menu Editor And Voila! You Now have a quick and easy way to launch your favorite windoz programs ^_^. I think this is a good howto.. considering if its one youll use alot... doing this will save you quite some time in the end.. 

Enjoy!

---

### Post by somedolphin on 2006-07-28
Thanks.
Very Helpful.

Ike

---

### Post by crayak27 on 2006-07-28
Or if you're not using gnome, you could create a bash alias by adding a line similar to this to your ~/.bash_aliases:

alias program_name='wine /home/{user}/.wine/drive_c/Program Files/{path to your program.exe}'

this would allow you to start the program from the terminal.

nice guide by the way :)

---

### Post by Hairy_Palms on 2006-07-29
or you can use the wine virtual path
wine "C:\Program Files\Program\program.exe"

---

### Post by sa-mejia on 2009-08-06
In my case, only the second method worked ('wine "C:\Program Files...").

The first method ('wine /home/{user}/.wine/drive_c/Program\ Files...') did not.

Anyone has any idea why?

S.

---

### Post by score100 on 2010-04-19
^^ same for me.

---

### Post by wachin on 2012-08-04
Example, I have installed e-Sword 10 on Ubuntu 12.04 LTS, with wine 1.4, and to launch put on terminal:


wine "C:\Program Files\e-Sword\e-Sword.exe"


And working. It should be as it is here, closed in quotes the program path with "\" writen.

God Bless You

---

