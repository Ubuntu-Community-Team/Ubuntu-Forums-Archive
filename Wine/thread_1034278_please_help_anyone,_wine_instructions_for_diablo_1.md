---
title: "please help anyone, wine instructions for diablo 1"
date: 2009-01-08
forum: Wine
---

### Post by Nooblit on 2009-01-08
Ok First I would like to apologize for my lack of knowledge with this. 2nd Thanks for taking the time to help me.

I need help with the instructions below I read to fix it. Ok I am using wine 1.0 on Ubuntu 8.04 (hardy)

When I click play on Diablo 1 it will play the movie and then it will crash  like some of the other people. I read these instructions below to fix this problem and understand the concept of what I need to do but I am at a loss on how to do it. Below is what they said I need to do.

/////////////////////////////////////////////////////////////////////////
Instructions.

You must have DirectDrawRenderer in the registry set to "gdi" (which is the default) for Diablo to work. If you have changed it to "opengl" at any point then the game will crash after the Blizzard logos.

 for your convenience here is a reg file that will change it for you:

-------------start DDrawRender.reg-------------

REGEDIT4
[HKEY_CURRENT_USER\Software\Wine\AppDefaults\Diablo.exe\Direct3D] "DirectDrawRenderer"="gdi"

--------------end DDrawRender.reg--------------

just copy the date NOT including the dashed lines to DDrawRender.reg and then use


wine regedit DDrawRender.reg

to add it to the registry 
///////////////////////////////////////////////////////////////////////

Ok so what I understand from this is I need to copy this hkey thingy and paste it in the DDrawRender.reg. And then use this regedit exe thing I found in my wine folder to add it somehow?

Well First I do not know were the DDrawRender.reg is but I am looking at my wine in /home/me/.wine and I see system.reg ,user.reg and userdef.reg. I assume I need to past it in one of those 3?  And do I need to paste it in a certain spot or overwrite anything to paste it?

Also I found the regedit.exe in /home/me/.wine/drive_c/windows but even if i paste it in one of those other 2 folders, I still do not know what they mean by add it using the regedit. I thought if I paste something in the reg it would work?

Well I hope I was clear on what I do not understand but if you need any more details about something please let me know and I will respond.
Thanks for taking the time to read this long ** post.

---

### Post by Toffeeapple on 2009-01-09
Have you followed the instructions [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498")? in particular the section on "HOWTO: Fixing blank menus"

I have it up and running on my sons PC after following the above mentioned.

Good luck : )

edit: I just realised that you're having trouble using regedit.

In a Terminal type..

```
gedit DDrawRender.reg
```

and then past the following into it.

```
REGEDIT4
[HKEY_CURRENT_USER\Software\Wine\AppDefaults\Diablo.exe\Direct3D] "DirectDrawRenderer"="gdi"
```

save it, then in a terminal again..

```
wine regedit.exe
```

click on Registry/import Registry file.. navigate to where you saved the file DDrawRender.reg

now it should be in the wine registry. Continue with the guide at WineHQ : )

---

