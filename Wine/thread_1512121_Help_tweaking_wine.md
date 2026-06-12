---
title: "Help tweaking wine"
date: 2010-06-17
forum: Wine
---

### Post by crjackson on 2010-06-17
Hello,

I haven't used wine in years, but now my youngest daughter has to run Wimba Pronto chat for school.  I installed the newest version of wine and the program runs fine.

HOWEVER...

It's ugly as heck.  I remember that there used to be either an application or some settings in general where it could be tweaked to pretty much respect the GTK theme in use, or made to look like it.  The fonts are particularly ugly.

I did install the ms ttf fonts and such, but either they aren't being used, or it just doesn't help.

Please tell me how to make this nice looking.

I did a search and found a couple of guides that didn't help with the font issues at all.

---

### Post by cogadh on 2010-06-17
[http://ubuntuforums.org/showthread.php?t=1050920](http://ubuntuforums.org/showthread.php?t=1050920)

---

### Post by HomeSlixe on 2010-06-17
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=18665](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18665)

if [cogadh]("http://ubuntuforums.org/member.php?u=48823")'s solution doesn't work :p

You may need winetricks
```
wget http://www.kegel.com/wine/winetricks

```To get packages to allow the program to work (as best as it can as it has a bronze rating at appdb).
You may want to review all available content @ [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

Or you can try this if you are absolutely stuck with no guarantees
```
sh winetricks gdiplus gecko dcom98 vcrun2008 ie6 msxml3 vcrun2005sp1
```then,
```
sudo apt-get install msttcorefonts
```Hope this helped!

---

### Post by crjackson on 2010-06-17
> **cogadh said:**
> [http://ubuntuforums.org/showthread.php?t=1050920](http://ubuntuforums.org/showthread.php?t=1050920)

It's a very nice script.  Unfortunately, when font smoothing is enabled, no text is displayed at all.

Running the script again and turning off the smoothing, text returns.

---

### Post by crjackson on 2010-06-17
> **HomeSlixe said:**
> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=18665](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18665)

if [cogadh]("http://ubuntuforums.org/member.php?u=48823")'s solution doesn't work :p

You may need winetricks
```
wget http://www.kegel.com/wine/winetricks

```To get packages to allow the program to work (as best as it can as it has a bronze rating at appdb).
You may want to review all available content @ [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

Or you can try this if you are absolutely stuck with no guarantees
```
sh winetricks gdiplus gecko dcom98 vcrun2008 ie6 msxml3 vcrun2005sp1
```then,
```
sudo apt-get install msttcorefonts
```Hope this helped!

I already tries winetricks and enabled smoothing.  The text disappeared and disabling font smoothing restored it to normal.

I've already installed msttcorefonts and made a simlink to the wine Fonts folder. All fonts are available for wine but it doesn't seem to make any difference.

Please explain this command before I try it.

```
sh winetricks gdiplus gecko dcom98 vcrun2008 ie6 msxml3 vcrun2005sp1
```

How will this help me, and why would I want to install ie6?

---

### Post by HomeSlixe on 2010-06-17
```
sh winetricks gdiplus gecko dcom98 vcrun2008 ie6 msxml3 vcrun2005sp1
```

they are are windows dependencies

---

### Post by crjackson on 2010-06-17
How can I disable or remove fontsmooth-gray? I tried this and it COULD be the reason that I loose text when fotnsmooth is enabled.

---

### Post by HomeSlixe on 2010-06-17
```
winetricks fontsmooth-disable
```

---

### Post by crjackson on 2010-06-17
> **HomeSlixe said:**
> ```
sh winetricks gdiplus gecko dcom98 vcrun2008 ie6 msxml3 vcrun2005sp1
```

they are are windows dependencies

Okay, I did this and still no change.

---

### Post by crjackson on 2010-06-17
> **HomeSlixe said:**
> ```
winetricks fontsmooth-disable
```

I think that disables fontsmooth, but if I try to enable it, I believe it's going straight to fontsmooth-gray and that's why it makes the menus fail to display the text.

---

### Post by cogadh on 2010-06-17
> **HomeSlixe said:**
> ```
sh winetricks gdiplus gecko dcom98 vcrun2008 ie6 msxml3 vcrun2005sp1
```

they are are windows dependencies
Neither Wine or Windows depend on most of those and the ones they do depend on are already present in Wine. All that command does is replace the existing Wine DLLs with the "real" ones from Windows. With the exception of gdiplus, none of them have anything to do with font smoothing and Wine's implementation of gdiplus is already complete in this respect.

---

### Post by HomeSlixe on 2010-06-17
here are some fontsmooth options found by ```
winetricks
```
mabey seting one of these will help?
 fontfix       Fix bad fonts which cause crash in some apps (e.g. .net).
 fontsmooth-bgr        Enables subpixel smoothing for BGR LCDs
 fontsmooth-disable    Disables font smoothing
 fontsmooth-gray       Enables grayscale font smoothing
 fontsmooth-rgb        Enables subpixel smoothing for RGB LCDs

---

### Post by HomeSlixe on 2010-06-17
> **cogadh said:**
> Neither Wine or Windows depend on most of those and the ones they do depend on are already present in Wine. All that command does is replace the existing Wine DLLs with the "real" ones from Windows. With the exception of gdiplus, none of them have anything to do with font smoothing and Wine's implementation of gdiplus is already complete in this respect.


didn't say it would work, just that it might as im gnerally using these for most apps with wine.

---

### Post by cogadh on 2010-06-17
> **crjackson said:**
> I think that disables fontsmooth, but if I try to enable it, I believe it's going straight to fontsmooth-gray and that's why it makes the menus fail to display the text.
Run "winetricks fontsmooth-disable" then run "winetricks fontsmooth-rgb"

> **HomeSlixe said:**
> didn't say it would work, just that it might as im gnerally using these for most apps with wine.
In that case, some friendly advice: when you are trying to help someone with a specific problem, it is not a good idea to clutter the offered solution with extraneous information that has nothing to do with the problem. With Linux in general and Wine in particular, this will only lead to frustration on the part of the person you are trying to help and could also introduce additional issues into the troubleshooting process.

---

### Post by crjackson on 2010-06-18
> **cogadh said:**
> Run "winetricks fontsmooth-disable" then run "winetricks fontsmooth-rgb"

Thanks, I'll run tomorrow and see what happens.

---

### Post by dino99 on 2010-06-18
some times ago i've had to copy/paste the windows fonts to wine app fonts folder to work around this fonts issues with a prog

---

### Post by crjackson on 2010-06-18
> **dino99 said:**
> some times ago i've had to copy/paste the windows fonts to wine app fonts folder to work around this fonts issues with a prog

Thanks, I already did that before posting this thread.

---

### Post by crjackson on 2010-06-18
> **cogadh said:**
> Run "winetricks fontsmooth-disable" then run "winetricks fontsmooth-rgb"

I go the following error;

```
charles@emachines-laptop:~$ winetricks
err:module:attach_process_dlls "rpcrt4.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\cmd.exe" failed, status c0000005
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned empty string
------------------------------------------------------
charles@emachines-laptop:~$
```

---

### Post by crjackson on 2010-06-21
I purged wine and reinstalled.  It fixed the error showing above when I choose RGB fontsmoothing. However, that too causes a loss of all text.

I"m clueless how to fix this UGLY font issue.

---

