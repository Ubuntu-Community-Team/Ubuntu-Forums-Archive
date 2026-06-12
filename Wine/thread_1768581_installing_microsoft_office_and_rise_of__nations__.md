---
title: "installing microsoft office and rise of  nations  using  wine"
date: 2011-05-27
forum: Wine
---

### Post by quarkhirad on 2011-05-27
I have  office 2010 student and  home edition  of microsoft. I realised  that  wine can install  office   2007. But when i  try  the  procedure given in  the website wine  reports   please  mount  office 12 (office  2007) . How  do  i install office 2010 using wine.


[HTML]
http://ubuntuguide.net/install-microsoft-office-2007-pro-and-fix-wordppt-in-ubuntu-11-04-natty[/HTML]


When i open wine tricks, install a game. I can install the demo version of Rise of nations. However i  have the original cd.How do i install the original.

---

### Post by wildmanne39 on 2011-05-27
> **quarkhirad said:**
> I have  office 2010 student and  home edition  of microsoft. I realised  that  wine can install  office   2007. But when i  try  the  procedure given in  the website wine  reports   please  mount  office 12 (office  2007) . How  do  i install office 2010 using wine.


[HTML]
http://ubuntuguide.net/install-microsoft-office-2007-pro-and-fix-wordppt-in-ubuntu-11-04-natty[/HTML]


When i open wine tricks, install a game. I can install the demo version of Rise of nations. However i  have the original cd.How do i install the original.
Hi, have not had much luck with wine I use virtualbox with windows inside if I must have a program that is only run on windows, but with libre office there is really no need for microsoft office.

---

### Post by Anuovis on 2011-05-27
You install apps much like you did in Windows. Find the exe setup file, right click on it, *Properties>Open With*, check Wine there. Now you can double click any exe file and it will be opened like in Windows.

Wine has this sort-of-C-disk that you can browse which is a folder in your Ubuntu system but organized like a regular Win C would be. Your software will be there.

You might also want to visit Wine settings and set a path to your CD contents from there or switch between windowed/fullscreen mode. Sometimes it's necessary to play with those in order to run the software sucessfully.

There are also several tweak programs for Wine. 
One is WineTricks, I have no idea what this does, never used it and last time I checked it was in alpha version. Try avoiding that unless you know it will improve you experience.

Another is called PlayOnLinux. It comes with a database of software and helps you install various things from the list by picking the good working configuration automatically. Not necessary but might be helpful. It creates these wine prefixes which are like virtual C disks, stored in home/*yourusername*/.PlayOnLinux (click ctrl+H to view hidden folders like this one).

Might be a lot to swallow at one time but try and play around with Wine, if an app is decently supported it should work out one way or another.

---

### Post by quarkhirad on 2011-05-27
> **Anuovis said:**
> You install apps much like you did in Windows. Find the exe setup file, right click on it, *Properties>Open With*, check Wine there. Now you can double click any exe file and it will be opened like in Windows.

Wine has this sort-of-C-disk that you can browse which is a folder in your Ubuntu system but organized like a regular Win C would be. Your software will be there.

You might also want to visit Wine settings and set a path to your CD contents from there or switch between windowed/fullscreen mode. Sometimes it's necessary to play with those in order to run the software sucessfully.

There are also several tweak programs for Wine. 
One is WineTricks, I have no idea what this does, never used it and last time I checked it was in alpha version. Try avoiding that unless you know it will improve you experience.

Another is called PlayOnLinux. It comes with a database of software and helps you install various things from the list by picking the good working configuration automatically. Not necessary but might be helpful. It creates these wine prefixes which are like virtual C disks, stored in home/*yourusername*/.PlayOnLinux (click ctrl+H to view hidden folders like this one).

Might be a lot to swallow at one time but try and play around with Wine, if an app is decently supported it should work out one way or another.

Thanks but  when i opened RON cd and opened the file  nations.exe with wine it started the  setup. However after entering the cd key it  said cannot  load  pidgen.dll. Please   help

---

### Post by cracker89 on 2011-05-27
It might be that you are using a cracked copy of office? thats a bug sometimes. about the game, i suggest a google search for "<game name> ubuntu " it should suffice. what version of wine do u have? reinstalling mebbe?

---

### Post by cracker89 on 2011-05-27
infact, this is the best place to look..    appdb.winehq.org

---

### Post by quarkhirad on 2011-05-27
> **cracker89 said:**
> It might be that you are using a cracked copy of office? thats a bug sometimes. about the game, i suggest a google search for "<game name> ubuntu " it should suffice. what version of wine do u have? reinstalling mebbe?

No my office is an original three user version. I know this as  it is installed on my father windows  dell laptop and on my laptop in  windows. It has been  verified by microsoft as an  original copy as  i have been  able to  download  all  the  updates  for it.

I have 1.3  version.

---

### Post by saugatad on 2011-05-27
Try to install with playonlinux it will certainlty work.

---

### Post by cracker89 on 2011-05-27
> **quarkhirad said:**
> No my office is an original three user version. I know this as  it is installed on my father windows  dell laptop and on my laptop in  windows. It has been  verified by microsoft as an  original copy as  i have been  able to  download  all  the  updates  for it.

I have 1.3  version.

Alright. just checking... thats it sometimes.
Albeit, all the same, maybe thats why.. :D 

i dont know, i dont thinks its been sufficiently tried, if wine isnt doing it try this [www.codeweavers.com/products/cxmac/](www.codeweavers.com/products/cxmac/) theres a free trial on there...

---

### Post by cracker89 on 2011-05-27
look these up. from what i kno theres issues with msoffice 10 and linux still. 

[http://ubuntuforums.org/showthread.php?t=1235167](http://ubuntuforums.org/showthread.php?t=1235167)


appdb.winehq.org/objectManager.php?sClass=version&iId=17336

and this too should prove helpful.. personally i dont think its worth all the effort, the functionality's going to be slightly deferred.

---

### Post by quarkhirad on 2011-05-27
> **saugatad said:**
> Try to install with playonlinux it will certainlty work.

After  installing playonlinux using apt-get install playonlinux. i opened play  on linux and  then clicked  on install.  on the  left pane  i  clicked  on  games. I can see  a  list  of games but no  Rise  of  nations.  Please help. Also while playonlinux was downloading  updates  my net  connection dropped. As  a  result now when i open play on linux it  says you  do not seem  to be  connected to the net. Now that  my net is  back  how do  i tell it to download updates


In the list of games i saw prince of persia. When i clicked on apply to install the game it first started downloading wine 1.1. When i have wine  1.3 installed already .  Help!!!

---

### Post by cracker89 on 2011-05-27
> **quarkhirad said:**
> After  installing playonlinux using apt-get install playonlinux. i opened play  on linux and  then clicked  on install.  on the  left pane  i  clicked  on  games. I can see  a  list  of games but no  Rise  of  nations.  Please help. Also while playonlinux was downloading  updates  my net  connection dropped. As  a  result now when i open play on linux it  says you  do not seem  to be  connected to the net. Now that  my net is  back  how do  i tell it to download updates


In the list of games i saw prince of persia. When i clicked on apply to install the game it first started downloading wine 1.1. When i have wine  1.3 installed already .  Help!!!



playonlinux for msoffice. i think they have made a claim to office 2010

---

### Post by Anuovis on 2011-05-27
> **quarkhirad said:**
> After  installing playonlinux using apt-get install playonlinux. i opened play  on linux and  then clicked  on install.  on the  left pane  i  clicked  on  games. I can see  a  list  of games but no  Rise  of  nations.


Not all games are in the list. Try the regular Wine then.

> 
Also while playonlinux was downloading  updates  my net  connection dropped. As  a  result now when i open play on linux it  says you  do not seem  to be  connected to the net. Now that  my net is  back  how do  i tell it to download updatesRestart and try again, usually it works well without updating though.

> In the list of games i saw prince of persia. When i clicked on apply to install the game it first started downloading wine 1.1. When i have wine  1.3 installed already .It's normal. Some software works better with older versions of Wine. PlayOnLinux can maintain several Wine versions on your PC and assign them to certain applications. Your main Wine installation remains unaltered. 

E.g. You may have Wine 1.3 but your PlayOnLinux can use Wine 1.2 for one application, Wine 1.3 for another and Wine 1.0.3 for the third one. However, all these different versions are only available through PlayOnLinux.

---

### Post by quarkhirad on 2011-05-29
> **cracker89 said:**
> playonlinux for msoffice. i think they have made a claim to office 2010

Oh yeah i installed it. Microsoft office works on ubuntu 11.04 using play on linux. I have been successful in editing a file saving it in .XLSX and .xls formats.        

After registering it on the web it asks regarding updates for offce. I chose using recommended setting and then it popped a dialogue saying cannot get updates. Though i have an internet connection.One more thing is that the ribbon is a bit sluggish while changing tabs(eg:changing from home tab to view tab). 

I dont know of any other bugs.

Thanks cracker89

---

### Post by cracker89 on 2011-05-29
> **quarkhirad said:**
> Oh yeah i installed it. Microsoft office works on ubuntu 11.04 using play on linux. I have been successful in editing a file saving it in .XLSX and .xls formats.        

After registering it on the web it asks regarding updates for offce. I chose using recommended setting and then it popped a dialogue saying cannot get updates. Though i have an internet connection.One more thing is that the ribbon is a bit sluggish while changing tabs(eg:changing from home tab to view tab). 

I dont know of any other bugs.

Thanks cracker89

i think the thanks goes to saugatad... no the updates wont work. its a windows-linux dll thing.. i dont know how u can fix that, but i doubt u'll really miss the updates. :P search the forum, you;ll find something or the other.cheerios

---

### Post by Mark Phelps on 2011-05-31
I just looked through the WineHQ pages for the Office 2010 components, and they are rated GARBAGE -- meaning, they will NOT work, regardless of what product you use.

Realize that it took them three years after the release of office 2007 to get SOME of the components working reasonably well.

Unless some miracle occurs, it's likely to take the same timeframe for Office 2010.

---

### Post by cracker89 on 2011-05-31
Hmm...

I found these, but i cant see them right now. behind a college router. Hope they something helpful..

YouTube - Office 2010 on Linux using Wine!
31 Dec 2010 ... It starts but it crashes very often. Im using wine 1.3.10 and Ubuntu 10.10 x86_64. Word 2010 and Excel 2010. (sorry for my bad english)
[www.youtube.com/watch?v=Ae-Qgd-WG8Q](www.youtube.com/watch?v=Ae-Qgd-WG8Q) - Cached

YouTube - OFFICE 2010 ON LINUX
23 Feb 2010 ... Added to queue Office 2010 on Linux using Wine!by ...
[www.youtube.com/watch?v=jx_eZp310Sc](www.youtube.com/watch?v=jx_eZp310Sc) - Cached
Show more results from youtube.com

Buggy seems like...

---

### Post by uRock on 2011-05-31
Moved to *Wine*.

---

### Post by tejaswidp on 2011-05-31
> **wildmanne39 said:**
> Hi, have not had much luck with wine I use virtualbox with windows inside if I must have a program that is only run on windows, but with libre office there is really no need for microsoft office.
i second that:D

---

### Post by cracker89 on 2011-05-31
dlol... hmm, but sometimes the macro's and formatting needs, say in a law office, as i would need, can be done with a fair amount ease and less amt of time in msoffice, and libre office cant really do it for me in that sense. Any easy, working, fast and practical ways to get the macro's down in libre office?

I know off topic, but i doubt this is worth starting a thread over..

---

### Post by quarkhirad on 2011-07-10
Hey guys ok. I got to install  office 2010 and i can save new files and create files.The problem  is that  when i try to open a  file that was created by office2010 it gives an error 

QUOTE]Their is no windows program configured to open this type of file.[/QUOTE] 


Ps note:The file i  am  trying to  open was created  using office2010 when  i  was  booted  in windows   

Help

---

