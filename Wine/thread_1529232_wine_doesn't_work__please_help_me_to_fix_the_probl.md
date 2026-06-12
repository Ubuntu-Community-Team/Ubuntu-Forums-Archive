---
title: "wine doesn't work ? please help me to fix the problem that I have with Wine..thanks"
date: 2010-07-11
forum: Wine
---

### Post by alialen on 2010-07-11
I have ubuntu 10.04, and I have to design a website for my friend, therefore, I downloaded Dreamweaver cs5 from adobe website. I found out that I have to install Wine in order to be able to install .exe files on Obuntu, after wine installation I edited the properties of the .exe (dreamweaver) file (execution allowing and opening the program with Wine) . when i click on the file there is a default for extracting adobe Dreamweaver  "C:\users\alialen\Desktop\Adobe CS4\Dreamweaver" so i choose the default folder and then it starts loading the file and extracting it. After it is done loading in about 2 minutes i get a program error in which it says : 

[B]"The program setup.exe has encountered a serious problem and needs to cloes. We are sorry for the inconvenience. 

This can be caused by a problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application 
If this problem is not present under Windows and has not been reported yet, you can report it at http://bugs.winehq.org"[/B]

I wanted to make sure that I installed Wine correctly therefore, I removed it completely from the directory, and installed it through the terminal . 

I tried to explain the problem in details and I am very new to ubuntu so please if you know what causing the problem or how to fix the problem, I would appreciated to read your comments, please explain your answer and comments in details. 

Thank you.

---

### Post by cogadh on 2010-07-12
Did you follow the advice in the error and actually look at Wine's AppDB entry for Dreamweaver CS5?

---

### Post by kyleabaker on 2010-07-12
In the future, you should be more descriptive with your thread subjects. Use something like "Adobe Dreamweaver CS5 crashes in Wine". ;)

Taking a look at the Wine AppDB, you'll notice that there are already poor test case results. Sometimes they include fixes, but most often they don't and you'll end up waiting too long for a solution.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=183](http://appdb.winehq.org/objectManager.php?sClass=application&iId=183)

Your comment mentions Dreamweaver CS5 at first, but then goes on to mention a folder with CS4 in it. For better quality help, you'll need to open the application in a terminal and copy/paste the error messages.
[http://wiki.winehq.org/FAQ#head-3b297df7a5411abe2b8d37fead01a2b8edc21619](http://wiki.winehq.org/FAQ#head-3b297df7a5411abe2b8d37fead01a2b8edc21619)

---

### Post by Rod J on 2010-07-12
Have a look at this page:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20236](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20236)

It pretty much tells you what you need to do. But I wonder if you could have just used a Linux native app to do what you want? Dreamweaver is a complex Windows app to get working in Linux I think, although it does appear to work in Wine.

---

### Post by kyleabaker on 2010-07-12
> **Rod J said:**
> Have a look at this page:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20236](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20236)

It pretty much tells you what you need to do. But I wonder if you could have just used a Linux native app to do what you want? Dreamweaver is a complex Windows app to get working in Linux I think, although it does appear to work in Wine.

I wondered this myself. I just discussed this in another thread that might be useful if you're willing to let go of Windows applications and use something native.

Website design software
[http://ubuntuforums.org/showthread.php?t=1516887](http://ubuntuforums.org/showthread.php?t=1516887)

---

