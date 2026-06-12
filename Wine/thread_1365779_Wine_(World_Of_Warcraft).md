---
title: "Wine (World Of Warcraft)"
date: 2009-12-27
forum: Wine
---

### Post by JohanA on 2009-12-27
Since an update from blizzard I can no longer use the  wow icon on my desktop to start wow so i have to use the wow.exe to start the game but when I typed my account name/password I get this message:

[IMG]http://file:///home/azumor/Pictures/Screenshot-1.png[/IMG]                                  Microsoft Visual C++ Runtime Library
 

 Runtime Error!
 

 Program: _C:\Program_ Files\World of Warcraft\Wow.exe
 

 R6034
 An application has made a attempt to load the C runtime library incorrectly
 Please contact the application's support team for more information
 

and when i pressed on the OK button and get back to the log in page for wow it say's:

                                 There was an error loging in. Please try again later. If the problem persist, please contact Technical Support at: [eu.blizzard.com/support/index.xml?gameld=11&rootCategoryld=2100]
 


If anyone know how to fix this or what's the problem is please tell me what I need to do to fix it hate playing world of warcraft on crappy vista ](*,)
[IMG]http://file:///home/azumor/Pictures/Screenshot-1.png[/IMG]

---

### Post by jflaker on 2009-12-27
[http://www.linux-noob.com/forums/index.php?/topic/2108-creating-a-launcher-for-a-program-installed-with-wine/](http://www.linux-noob.com/forums/index.php?/topic/2108-creating-a-launcher-for-a-program-installed-with-wine/)

Essentially, the command is 

wine "c:\path\To\Your\wow.exe"

that *should* launch wow.exe

---

### Post by JohanA on 2009-12-27
The wow start icon work now but still get the Error

Microsoft Visual C++ Runtime Library
 

 Runtime Error!
 

 Program: _C:\Program_ Files\World of Warcraft\Wow.exe
 

 R6034
 An application has made a attempt to load the C runtime library incorrectly
 Please contact the application's support team for more information
 

and when i pressed on the OK button and get back to the log in page for wow it say's:

 There was an error loging in. Please try again later. If the problem persist, please contact Technical Support at: [eu.blizzard.com/support/index.xml?gameld=11&rootCategoryld=2100]



please help

---

### Post by jflaker on 2009-12-27
OK then...remove Wine COMPLETELY through synaptic and reload it....WOW folders should still be there..

run the configure wine first and imitate Win XP...you should be good

---

### Post by Alatar1 on 2009-12-28
update your runtime library.. its noted on a thread here

[http://forum.winehq.org/viewtopic.php?t=7040](http://forum.winehq.org/viewtopic.php?t=7040)

---

