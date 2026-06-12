---
title: "Think I have path wrong"
date: 2010-11-30
forum: Wine
---

### Post by von Stalhein on 2010-11-30
Hi all,.
I'm trying to sort a menu entry for COD 1. If I navigate to the CoDSP.exe file in the c: drive, right click, and open with "Wine Windows Program Loader" there are no issues. When I try and put the code below in a menu launcher it goes pear shaped.

The menu entry 
```
 "/home/me/.wine/dosdevices/c:/Program Files/Call of Duty/CoDSP.exe"

```in terminal gives the following output as it tries to start:```
fixme:win:EnumDisplayDevicesW ((null),0,0x206f4cc,0x00000000), stub!

```
I get windows telling me ```
Couldn't load default.cfg. Make sure COD is run from the correct folder
```

Thanks for any assistance.

Oh sorry, Wine 1.2.1 if it makes any difference

---

### Post by ronnielsen1 on 2010-11-30
If the folder has more than one name you have to do the following:

Change

>  "/home/me/.wine/dosdevices/c:/Program Files/Call of Duty/CoDSP.exe"

to /home/me/.wine/dosdevices/c:/Program\ Files/Call\ of\ Duty/CoDSP.exe

---

### Post by Verbeck on 2010-11-30
try changing it to
```

wine "/home/me/.wine/dosdevices/c:/Program Files/Call of Duty/CoDSP.exe"
```
or```

wine /home/me/.wine/dosdevices/c:/Program\ Files/Call\ of\ Duty/CoDSP.exe

```

---

### Post by von Stalhein on 2010-12-01
Thanks guys, no luck.

I browse the Wine C: drive, and it's definitely at```
/home/me/.wine/dosdevices/c:/Program Files/Call of Duty/CoDSP.exe
```

With " at either end nothing happens.
Without" the same message as in the OP appears.
I tried with the extra slashes and without - I understand why the slashes are there now.

Might have to keep doing it the manual way - it's not that I play it that much but it's been annoying me that I couldn't make the link work.

---

### Post by Verbeck on 2010-12-01
here's a command entry that works for me
```

env WINEPREFIX="/home/username/.wine" wine C:\\Program\ Files\\Big\ City\ Adventure-Sydney\ Australia\\BigCityAdventureSyd.exe

```theres a single** [SIZE=2]\[/SIZE]** before every space and** [SIZE=2]\\[/SIZE] **for changing directories..

so you can try
env WINEPREFIX="/home/username/.wine" wine C:\\Program\ Files\\Call\ of\ Duty\\CoDSP.exe

hope this helps

---

### Post by von Stalhein on 2010-12-02
Thanks Verbeck - I'm presently trying ```
env WINEPREFIX="/home/me/.wine" wine C:\\Program\ Files\\Call\ of\ Duty\\CoDSP.exe
```
and getting the same error messages as above, so I know we're close.

I might muck about a bit with the "C" drive part, as it is allegedly trying to start in the wrong directory.

---

### Post by cogadh on 2010-12-02
Make script that does this:
```
cd ~/.wine/drive_c/Program\ Files/Call\ of\ Duty
wine CoDSP.exe
```
Then make your shortcut point at the script

---

### Post by von Stalhein on 2010-12-03
> **cogadh said:**
> Make script that does this:
```
cd ~/.wine/drive_c/Program\ Files/Call\ of\ Duty
wine CoDSP.exe
```
Then make your shortcut point at the script

Love your work. :biggrin:

And I've written a script. Awesome.

Thanks very much, this has been annoying me for ages.

---

### Post by cogadh on 2010-12-03
Glad to help. Sorry for not making the instructions more detailed, I was a little rushed when I typed that.

---

