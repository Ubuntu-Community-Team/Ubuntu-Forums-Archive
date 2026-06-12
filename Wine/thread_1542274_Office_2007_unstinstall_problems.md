---
title: "Office 2007 unstinstall problems"
date: 2010-07-30
forum: Wine
---

### Post by mads2106 on 2010-07-30
Hi everyone. 
I have a problem installing Microsoft office 2007. First i encountered an error under installation, but i just continued and i didn't notice what the error was about. Smart enough.. eh. 
But after the installation Word and Exel worked, but the rest crashed when i tried to start them.
I tried to uninstall it, but i just got an error. Then I browsed my C drive for the office files and deleted them.. well some of them. 
Because there is still some left that i can't delete. I tried to uninstall WINE, but that didn't work. 
Then i tried to install Office 2007 again but i just got an error message saying that it had encountered a problem. 
I don't know what to do at this point.. 
In the first place i just want Office removed from my computer, so if someone can help me with that it would be perfect.
All the files that i can't delete has a locked padlock in the down right corner. 
Ubuntu 10.4
Wine 1.1.42
Wine config: libraries -  ritched20 (native) and usp10 (native, builtin)

---

### Post by asdfoo on 2010-07-30
a) you shouldn't be using 1.1.42 it's very old in terms of how often wine is released and it had some installer problems - please update to 1.3.0

b) to start afresh, move or remove your wine prefix ~/.wine and run the installer again - uninstalling is not very reliable at present.

---

### Post by mads2106 on 2010-07-31
How do i update it? When i downloade it from Ubuntu software center it is just the version that i get.. 
and can you explain the uninstall process (b)? I am new in Linux so a step by step guide would be great.
Thanks for your time :)

---

### Post by asdfoo on 2010-07-31
to update goto [http://winehq.org](http://winehq.org) and follow the download instructions for Ubuntu

to remove your existing Wine data do:

mv ~/.wine ~/.wine-old

---

### Post by ronnielsen1 on 2010-08-01
Also google[COLOR=Blue] office 2007 winehq[/COLOR] 

It's an excellent how to,
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

They have links on this page for excel, word, powerpoint etc. Office 2007 works great but you have to set the library overrides or it will crash on you.

---

### Post by mads2106 on 2010-08-01
When i write that in the Terminal it just gives me this message back: 
hellemann@hellemann-laptop:~$ mv ~/.wine ~/.wine-old
mv: cannot stat `/home/hellemann/.wine': No such file or directory

---

### Post by mads2106 on 2010-08-01
Thanks for the advice :) It looks like a good guide. 
I just need to get the old installation of Office removed from my computer so i can start over again otherwise it just gives me an error message during the installation.

---

### Post by mads2106 on 2010-08-01
Okay i have reinstalled Ubuntu and now got a wine 1.2 version. But it still wont work properly. I tried to do everything in the guides and it just didn't work. Onenote crashes every time i try to start it. I don't really know what to do at this point.

---

### Post by ronnielsen1 on 2010-08-01
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12899](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12899)> **Additional Comments**
This program crashes when run in Vista or 7 mode but works ok in XP mode.


Are you running in XP mode?

You might want to check out native linux apps for a one note replacement. If you look through the next link, you'll see quite a few options

[http://ubuntuforums.org/showthread.php?t=93742](http://ubuntuforums.org/showthread.php?t=93742)

---

### Post by mads2106 on 2010-08-02
> **ronnielsen1 said:**
> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12899](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12899)

Are you running in XP mode?

You might want to check out native linux apps for a one note replacement. If you look through the next link, you'll see quite a few options

[http://ubuntuforums.org/showthread.php?t=93742](http://ubuntuforums.org/showthread.php?t=93742)

I ran it in XP mode.. so i just deleted all of it and now i am trying to get it to work in a Virtualbox ose. 
But thanks for your help :)

---

