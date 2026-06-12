---
title: "how to make any application recognized in system"
date: 2012-03-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by aithox on 2012-03-20
I have an executable FlashPlayer (downloaded form adobe years ago ) , I want make it as my default player for *.swf , there was an extra option to run application as command on older version of ubuntu (gnome)..
by now i can't find that option any more .. m using Ubuntu 12.04 ..
 :guitar:

---

### Post by nothingspecial on 2012-03-20
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by dcstar on 2012-03-20
> **aithox said:**
> I have an executable FlashPlayer (downloaded form adobe years ago ) , I want make it as my default player for *.swf , there was an extra option to run application as command on older version of ubuntu (gnome)..
by now i can't find that option any more .. m using Ubuntu 12.04 ..


Install up to date packages using the appropriate tools, do not try to install out of date packages on new systems - that is just insane.

---

### Post by Gregory Lee on 2012-03-21
> **aithox said:**
> I have an executable FlashPlayer (downloaded form adobe years ago ) , I want make it as my default player for *.swf , ...
I haven't done this, but you may be able to accomplish this in Firefox by going to Edit > Preferences > Applications, then find the content type Shockwave Flash file in the left column (probably you want /x-shockwave-flash), click on that line and click at the right to get the submenu item "Choose other ...".  You should be able to substitute your own favorite swf player program.  (I'm not implying this is a good thing to do ...)

Similarly, using Nautilus, if you right click on a .swf file, you can change the player program for that file to one of your own choice, though I'm unclear how you make that choice general for all .swf files.

---

### Post by aithox on 2012-03-21
> **Gregory Lee said:**
> I haven't done this, but you may be able to accomplish this in Firefox by going to Edit > Preferences > Applications, then find the content type Shockwave Flash file in the left column (probably you want /x-shockwave-flash), click on that line and click at the right to get the submenu item "Choose other ...".  You should be able to substitute your own favorite swf player program.  (I'm not implying this is a good thing to do ...)

Similarly, using Nautilus, if you right click on a .swf file, you can change the player program for that file to one of your own choice, though I'm unclear how you make that choice general for all .swf files.

It work , but it run both Firefox any My flashPlyer :D ,,
i put my flashplayer under /usr/bin .. so i can run via terminal like this "flashplayer flasfile.swf" ..can i get it work as default player without firefox ??

---

### Post by mc4man on 2012-03-21
If these are local .swf files then one of a couple of ways, assumes ~/.local/share/applications exists, if not then make one

Create a .desktop, a simple Ex. - 

```
gedit ~/.local/share/applications/flashplayer.desktop
```

Replace blue to suit

```
[Desktop Entry]
Version=1.0
Name=[COLOR="Blue"]What Ever You Want[/COLOR]
Comment=
Exec=[COLOR="Blue"]/usr/bin/whatever[/COLOR] %U
Icon=[COLOR="Blue"]/full/path/to/icon/if/you/wish[/COLOR]
Terminal=false
Type=Application
Categories=AudioVideo;Player;
MimeType=application/x-shockwave-flash;  
```

Save, close, then 
```
gedit  ~/.local/share/applications/mimeapps.list
```

there are 2 sections, under the "[Default Applications]" section add or replace if there
```
application/x-shockwave-flash=flashplayer.desktop
```

Under the "[Added Associations]" add this if not there - 
```
application/x-shockwave-flash=flashplayer.desktop;
```

If the line happened to be there then just append to end
```
flashplayer.desktop;
```

You may need a log out, then just check/set under properties of any one .swf file

---

### Post by aithox on 2012-03-21
> **mc4man said:**
> If these are local .swf files then one of a couple of ways, assumes ~/.local/share/applications exists, if not then make one

Create a .desktop, a simple Ex. - 

```
gedit ~/.local/share/applications/flashplayer.desktop
```

Replace blue to suit

```
[Desktop Entry]
Version=1.0
Name=[COLOR="Blue"]What Ever You Want[/COLOR]
Comment=
Exec=[COLOR="Blue"]/usr/bin/whatever[/COLOR] %U
Icon=[COLOR="Blue"]/full/path/to/icon/if/you/wish[/COLOR]
Terminal=false
Type=Application
Categories=AudioVideo;Player;
MimeType=application/x-shockwave-flash;  
```

Save, close, then 
```
gedit  ~/.local/share/applications/mimeapps.list
```

there are 2 sections, under the "[Default Applications]" section add or replace if there
```
application/x-shockwave-flash=flashplayer.desktop
```

Under the "[Added Associations]" add this if not there - 
```
application/x-shockwave-flash=flashplayer.desktop;
```

If the line happened to be there then just append to end
```
flashplayer.desktop;
```

You may need a log out, then just check/set under properties of any one .swf file


WOW..Wo HOo.. now i got it Work perfectly thx so much.. ):P

---

