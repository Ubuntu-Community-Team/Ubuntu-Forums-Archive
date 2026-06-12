---
title: "Wine not loading UltraSurf"
date: 2011-05-22
forum: Wine
---

### Post by xXzero_contentXx on 2011-05-22
Hi everybody!  I new to ubuntu. I have ubuntu 11.04.  I just installed Wine 1.3 by using the terminal.  I'm trying to get it to open UltraSurf but it will not open saying missing MFC42.dll. Can anyone please help me before i tear my head off.  It was bad enough that i spent 2 days trying to tackle installing Ubuntu to my external harddrive so i can dual boot with Windows on my laptop.  I almost jumped out the window on that one and if i had landed and still was alive then i would have torn my head off!!!

---

### Post by bobwyajnr on 2011-05-23
Hi **UltraSurf**

Top marks for question that is clear and shows that you've actually had a go yourself (wish everyone would do that - subtle hint)!! :popcorn:

The command **winetricks** is a little script that pulls in 'real' Windows libraries and .dlls's you may need to get programs working Wine.

Make sure you have it installed by typing:
```
winetricks --version
```
(or look in Synaptic)

MFC42.dll is from the Visual C++ 6.0 re-distributable package, which you findout by typing:
```
winetricks mfc42
```
(NB no .dll extension, must be lowercase)
That command will download and launch the Visual C++ re-distributable package (which contains a .dll file: MFC42.dll) and install it for you. :D

Bob

---

### Post by xXzero_contentXx on 2011-05-23
Thanks a lot mate for the reply.  I figured it out somehow but to let u know the steps that finally worked for me and also for whoever else reads this.    See the other sites tell u to either copy the .dll from windows if u have it or go to a dll download site or to install from the Visual C++ package. Well the first step didnt work as i do have windows and copied it to Ubuntu folder inside the directory of wine. Fail. Next step try to download Visual C++ packages-Fail!!! Windows Visual C++ package has a windows installer-how can u use a windows installer to install on a Ubuntu OS. Last step is what worked for me. I downloaded the dll from [http://www.dll-files.com/](http://www.dll-files.com/) but didnt really completely work but didnt give me mfc42 error. I really dont know what made it work at the end of it all but i did install a few more packages and installed java if that made a difference.   I wish i had known about your way.  That wouldve probably been the correct thing to do. At least i know now about winetricks.  Perhaps i bit of more than i can chew being that im only 3 days wet into Ubuntu.  Thanks again for the help  Cheers!

---

### Post by Zipdaman12 on 2011-09-12
Hey, thanks for all of your help.

I had winetricks installed so I used the command shared here to download and install the mfc42 dll file.

However, I am still getting this error when I try and run u95.exe:

The ordinal 6880 could not be located in the dynamic link library mfc42.dll


Any idea what I need to do?


Thanks,

Zip

---

### Post by $p00ky on 2012-01-08
Hi.
Doesn't work on Ubuntu 11.10.
No matter if we copy/paste mfc42.dll from our Windows system, from internet, or using winetricks, UltraSurf 1103 does't find the DLL...
Any suggestion?

[IMG]http://img818.imageshack.us/img818/7821/screenshotat20120109105.png[/IMG]

---

### Post by $p00ky on 2012-01-08
[COLOR="Red"]Edit: Sorry for the double post.
I don't know why but if I edit without going to "Advanced Editing" it posts a new message instead of editing...

Please delete this message (I didn't find any *delete* button...).[/COLOR]

---

### Post by bobwyajnr on 2012-01-09
> **$p00ky said:**
> Hi.
Doesn't work on Ubuntu 11.10.
No matter if we copy/paste mfc42.dll from our Windows system, from internet, or using winetricks, UltraSurf 1103 does't find the DLL...
Any suggestion?


I guess you try:
```
winetricks vcrun6
ln -s ~/.wine/drive_c/windows/system32/mfc42.dll ~/.wine/drive_c/Program\ Files/Ultrasurf
```
To create a soft-link to the "missing" dll - in the applications working directory.

I usually run my WINE applications by moving the UNIX Shell PWD (Present Working Directory) to the applications root folder as well:
```
cd ~/.wine/drive_c/Program\ Files/Ultrasurf
wine u1103.exe
```
That might make a difference??

Bob

---

### Post by CGi on 2012-05-28
woah! its really working bob.. tnx

---

### Post by bobwyajnr on 2012-05-30
> **CGi said:**
> woah! its really working bob.. tnx

Hmmm, delay much ):P

I can't take any credit for the amazing work the Wine dev's do. I always encourage folk to put some coinage the way of [Code Weavers]("http://www.codeweavers.com/") who support the WINE project with hosting... [Or donate directly to Wine]("http://www.winehq.org/donate/"). [It's been in active development for development for nearly 2 decades.]("http://wiki.winehq.org/WineHistory") That is a represents a lot of developer time!!

Is it just me or the Wine subforum been moved to a rather obscure place :confused:

Bob

---

