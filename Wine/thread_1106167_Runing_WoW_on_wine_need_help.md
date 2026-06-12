---
title: "Runing WoW on wine need help"
date: 2009-03-25
forum: Wine
---

### Post by aredhel on 2009-03-25
I am new to the forums, and i need help.
i am new to ubuntu and am trying to acquaint myself with the OS.
finding a how to on the forums for wow(a game i used to play on windows) i went ahead and followed the directions and installed wine and the full game. now the cinematics' work great but after they finish and the login screen should pop up but all i get is an error. and the WoW error page comes up asking what i was doing before the crash. but i don't ever get past that.... anybody experience this? or any ideas on what to do?

---

### Post by 3Miro on 2009-03-25
I am using wine, but not for WoW. If I were you I would go to the winehq forum and AppDataBase and look for an answer there. I think your chances there would be better.

---

### Post by aredhel on 2009-03-25
thanks ill try

---

### Post by Roosje on 2009-03-25
> **aredhel said:**
> I am new to the forums, and i need help.
i am new to ubuntu and am trying to acquaint myself with the OS.
finding a how to on the forums for wow(a game i used to play on windows) i went ahead and followed the directions and installed wine and the full game. now the cinematics' work great but after they finish and the login screen should pop up but all i get is an error. and the WoW error page comes up asking what i was doing before the crash. but i don't ever get past that.... anybody experience this? or any ideas on what to do?

Hi,

A quick Google delivered me this sites with relevant info:

[http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)
[http://video.google.com/videosearch?hl=en&q=howto+wine+wow&um=1&ie=UTF-8&ei=MG3KSfXwGsKz-Qbm0MXMBg&sa=X&oi=video_result_group&resnum=4&ct=title#](http://video.google.com/videosearch?hl=en&q=howto+wine+wow&um=1&ie=UTF-8&ei=MG3KSfXwGsKz-Qbm0MXMBg&sa=X&oi=video_result_group&resnum=4&ct=title#)
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
[http://www.linuxforums.org/forum/wine/62932-howto-installing-world-warcraft-wine.html](http://www.linuxforums.org/forum/wine/62932-howto-installing-world-warcraft-wine.html)

Hope they can get you on the way, and have fun playing!

Wilco

---

### Post by M3TA4 on 2010-09-12
Before anything make sure you have 3d rendering
(to get to terminal it is different for most distro's. And i can't remember howto for ubuntu. I think it is; Right click desktop--->run command--->type "console"(kubuntu=konsole)(LXDE=lxterminal)... )
type in terminal
```
$glxinfo |grep rendering
```
($=not superuser #=superuser)
and you should see something like this
```
direct rendering: Yes
```
(you can also run glxgears -info. Which will give you more infomation about your graphics driver i believe)
now if you do have it type this into terminal.(assuming that you have wine1.2 installed.)
```
#winecfg
```
in the graphics tab-->check the box beside emulate a desktop
also have a look at sounds tabs and test it.

another good thing to get is winetricks.
(type this in terminal)
```
$wget http://www.kegel.com/wine/winetricks

```
then type..
```
$sh winetricks

```

install directx9 and dotnet11(dotnet20-30 doesnt work on some distro's, just use 11 for now)through there gui.
Also...
[http://wowonwine.blogspot.com/]("http://wowonwine.blogspot.com/")
try this tut out.

and if fails again. Try changing winecfg settings or winetricks settings till it works..

hope this helps

---

### Post by cwwilson721 on 2010-09-12
Forget previous post.

ALOT of it is NOT applicable to Ubuntu. The poster is using shortcuts that don't exist in Ubuntu, running cli in su (Which is NOT recommended in Ubuntu), and a few other issues.

Not to mention installing/running in DirectX will make your install run SLOWER. (ALWAYS run in opengl.)

Thanks for the attempt, [M3TA4]("http://ubuntuforums.org/member.php?u=782387"), but you will just confuse the OP with that stuff. I've been running wine/WoW since vanilla under MANY distro's, and do know what I'm talking about.

What WILL help is to look in the Ubuntu forum a bit more, and maybe search the forums.

A few things:

[LIST]
[*]There is a[ wine forum here]("http://ubuntuforums.org/forumdisplay.php?f=313"), with a [VERY good WoW post]("http://ubuntuforums.org/showthread.php?t=579378")
[*]The only thing I'd change to make life alot easier is to ONLY install WotLK, then patch (Why install 3 DVDs, or who knows how many cd's. You end up with the correct files if you just install WotLK, then patch)
[*]We need your videocard, version of wine, and if WoW has been patched to latest version
[/LIST]

---

