---
title: "Wine program not locking to launcher"
date: 2012-04-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Baldrick_NZ on 2012-04-14
Hi all,

Up until a couple of updates ago, I had a windows program locked to the launcher, which always showed up on the launcher after reboot.

It doesn't any longer. I can place the program onto the launcher from dash, and it stays there until I reboot, then I have to repeat the process again.

How can I fix this so the program is fixed to the launcher permanently?

Any help would be much appreciated!

---

### Post by mc4man on 2012-04-14
You can only add a .desktop to the launcher so open the file in a text editor & post the contents, maybe something will show up

(if desired open gedit on your desktop then DnD the file from Dash into the gedit window

---

### Post by Baldrick_NZ on 2012-04-14
> **mc4man said:**
> You can only add a .desktop to the launcher so open the file in a text editor & post the contents, maybe something will show up

(if desired open gedit on your desktop then DnD the file from Dash into the gedit window

Thanks for your help, mc4man. Here's the output you requested...
```
[Desktop Entry]
Name=DirEttore
Exec=env WINEPREFIX="/home/baldrick/.wine" wine C:\\\\windows\\\\command\\\\start.exe /Unix /home/baldrick/.wine/dosdevices/c:/users/Public/Start\\ Menu/Programs/MixTime/DirEttore.lnk
Type=Application
StartupNotify=true
Path=/home/baldrick/.wine/dosdevices/c:/DirEttore
Icon=B175_DirEttore.0
```

Just to clarify, I can get the icon to the launcher (dash to launcher), and it'll stay there happily until I reboot or log off. Once rebooted/logged on, it's no longer on the launcher and I have to repeat the process again.

I just need to know how to place the icon back on the launcher permanently, like it has been previously under 12.04.

Cheers.

---

### Post by mc4man on 2012-04-14
Why don't you remove from launcher & do a log out/in.
Then browse to the location of the .desktop in nautilus & DnD from nautilus on to  the unity launcher.
Once in the launcher try a log out/in & see if it sticks

Edit: it's a bit of a wierd Exec= in that .desktop, sometimes progs create 2 .desktops, one is actually a link (DirEttore[COLOR="Blue"].lnk[/COLOR]

---

### Post by Baldrick_NZ on 2012-04-14
> **mc4man said:**
> Why don't you remove from launcher & do a log out/in.
Then browse to the location of the .desktop in nautilus & DnD from nautilus on to  the unity launcher.
Once in the launcher try a log out/in & see if it sticks

Edit: it's a bit of a wierd Exec= in that .desktop, sometimes progs create 2 .desktops, one is actually a link (DirEttore[COLOR="Blue"].lnk[/COLOR]

Hmmm, tried that, can't find a .desktop reffering to direttore, just an .ink file which doesn't DnD onto the launcher.

What file does the launcher refer to in order to know what icons to show?

When I do a nautilus search for .desktop (hidden files showing), there are a myriad of files, but none pertaining to direttore, yet dash sees the icon! Odd...

---

### Post by mc4man on 2012-04-15
Typically the .desktop you posted would be found in ~/.local/share/applications/wine/programs/*
It can be used in the launcher but I've always found that  while it will start the program, when opened the program runs in a wine icon,
 So if not created I'll make a .desktop that uses a direct path to the .exe
(2 different ways depending on whether using windows or linux path format

So worst case you could create a new .desktop (which may be better anyway

 Where is the location of the .desktop you posted before, when you dropped into gedit it would have shown the path in the title bar?

Or with the icon in the launcher run this - the location will be shown 
```
gsettings get com.canonical.Unity.Launcher favorites
```

Edit: while your at it can you post the exact path to the .exe, inc. the name of the .exe -  browse to it in nautilus - /home/baldrick/.wine/drive_c/....

---

### Post by Baldrick_NZ on 2012-04-15
Thanks for your help mc4man, much appreciated!

So, gedit says the path dash is seeing is:
[HTML]~/.local/share/applications/wine/Programs/MixTime[/HTML] which appears to be the Linux path.

The Wine path is:
[HTML]Home/Baldrick/.wine/drive_c/DirEttore[/HTML]

So are you saying we need to create a .desktop file to be added into the Wine Direttore folder which links to the .exe itself, and add that to the launcher instead of adding the icon from dash?

Cheers.

---

### Post by mc4man on 2012-04-15
Maybe a new one but could you clear something up - 
.wine/drive_c/DirEttore
Is that it, in other words DirEttore is the exe file & is sitting loose in drive_c (& has no .exe extension 

Or is it .wine/drive_c/DirEttore/DirEttore.exe

---

### Post by Baldrick_NZ on 2012-04-15
> **mc4man said:**
> Maybe a new one but could you clear something up - 
.wine/drive_c/DirEttore
Is that it, in other words DirEttore is the exe file & is sitting loose in drive_c (& has no .exe extension 

Or is it .wine/drive_c/DirEttore/DirEttore.exe

It's in .wine/drive_c/DirEttore/DirEttore.exe

Sorry for the mix-up.

---

### Post by mc4man on 2012-04-15
You could try this, we'll leave you existing .desktop alone because it does work (sorta) & you can go back to it if needed

Remove it from launcher, then log out/in

In terminal
```
gedit ~/.local/share/applications/DirEttore.desktop
```

Use this & save
```
[Desktop Entry]
Name=DirEttore
Exec=env WINEPREFIX="/home/baldrick/.wine" wine C:\\\\DirEttore\\\\DirEttore.exe 
Type=Application
StartupNotify=true
Path=/home/baldrick/.wine/dosdevices/c:/DirEttore
Icon=B175_DirEttore.0
```

Then open nautilus & browse to .local/share/applications
Inside will be the .desktop, you can do one of 2 things

DnD it on to the launcher, it should the show the icon. Test if it works, if so then log out in to see if it sticks

Or you can test the .desktop first before DnD to the launcher.
To do that right click on the .desktop & mark as executable. It should turn to it's icon .Doible left click & see. If good DnD or pin to launcher

If issues just delete the file

---

### Post by Baldrick_NZ on 2012-04-15
Wow, that worked a treat! Thank you!

So essentially we changed this
```
Exec=env WINEPREFIX="/home/baldrick/.wine" wine C:\\\\windows\\\\command\\\\start.exe /Unix /home/baldrick/.wine/dosdevices/c:/users/Public/Start\\ Menu/Programs/MixTime/DirEttore.lnk
```
for this
```
Exec=env WINEPREFIX="/home/baldrick/.wine" wine C:\\\\DirEttore\\\\DirEttore.exe
```
in the original .desktop file.

Any chance you could explain to me how you came to this conclusion? I'm keen to learn.

Cheers.

---

### Post by mc4man on 2012-04-15
Just a matter of observing in the past when an app made a 'Desktop' laucnher icon & the diff between what wine creates in that wine folder.

For unity the 'real' launcher is preferred because it paths directly to the .exe & in most cases the unity launcher icon starts & controls

The 'wine' .desktop starts the program thru the wine loader "start.exe" so not that suitable.
Though many times it could be usable as you've seen & stay in the launcher  - why not for you not exactly sure, when icons disappear thru log in's it's usually some flaw in the .desktop & or a path issue
(unity can't find it when restarting

There are several ways to write the Exec= using windows paths, sometimes one works better than the other  
I use \\\\ for directory, \\ for spaces in a name, it can be done other ways, sometimes when something works...

The other 2 ways can be seen here (copying from an old post of mine
In these using "..." to account for spaces & \\ for directories

```
env WINEPREFIX="/home/brandon/.wine" wine "C:\\Program Files\\Adobe\\Adobe Photoshop CS2\\Photoshop.exe"

```
```
wine "C:\\Program Files\\Adobe\\Adobe Photoshop CS2\\Photoshop.exe"
```

The diff is the 1st. one defines which wine prefix (you can use as many as you wish though in most cases the default one is al that's needed or used

The 2nd way just assumes ~/.wine 

Most often I'd just use what you're now using or in many cases the program will create one & leave on the Desktop.
If so just move to ~/.local/share/applications, then DnD on to the launcher


Here's the Exec= for EAC, (EAC created it), it shows \\\\ & \\ as described

```
Exec=env WINEPREFIX="/home/doug/.wine" wine C:\\\\Program\\ Files\\\\Exact\\ Audio\\ Copy\\\\EAC.exe 

```

(what I just found out is my favorite iso creator /burning prog - Imgburn, is now crashing window deco, hope that resolves

---

