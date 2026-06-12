---
title: "Bugs.."
date: 2006-07-28
forum: Ubuntu System Panel
---

### Post by chanders on 2006-07-28
Please post bugs [here]("https://launchpad.net/products/usp/+bugs") on Lauchpad

You can also post theme here but you stand a better chance of getting them fixed if they are on launchpad...


(Medium) * Sometimes clicking on the toggle buttons on the left, more than one pane is affected
(High) * USP hidden behind panel
(Low) * Cannot move applet with middle click
(Low) * Xsession warning when logging out

---

### Post by lazyd2 on 2006-07-28
With v0.28 I can't get USP to become transparent (setting w:Menu:90 in gconf-editor)

---

### Post by chanders on 2006-07-28
> **lazyd2 said:**
> With v0.28 I can't get USP to become transparent (setting w:Menu:90 in gconf-editor)

That is an oversight on my part... Will fix in next release.... In fact I will fix it now ;) 

Standby...

---

### Post by _simon_ on 2006-07-29
I use c:Usp:80 - works fine...

I found a bug (i think)

The logout button is not using my theme logout button (OSX). All the other icons seem to be fine.

And another.

Synaptic opens in another viewpoint rather than the current one.

And one more :)

The command to run Evolution was incorrect for some reason.

It was "evolution --component" instead of "evolution --component=mail"

and

In All Applications -> Games, I only have Cedega listed although I should actually have 6 other entries. I can't drag and drop into this menu... how do i add them?

Screenshot:

[[IMG]http://i17.photobucket.com/albums/b96/snewberry1980/Screenshots/th_games.png[/IMG]](http://i17.photobucket.com/albums/b96/snewberry1980/Screenshots/games.png)

---

### Post by Hells_Dark on 2006-07-29
Hi,

USP Version : 0.29-1
Here is my bug : A size icon problem.
[[img]http://pix.nofrag.com/54/64/996caaa6844f6e6c673b0f58c8eet.jpg[/img]](http://pix.nofrag.com/54/64/996caaa6844f6e6c673b0f58c8ee.html)

(Look at lock screen icon, Mouse icon, etc.)

---

### Post by _simon_ on 2006-07-29
My applications menu has items I've never heard of and not seen before and others that are missing!

---

### Post by chanders on 2006-07-29
The whole reading 'All Applications' need a rewrite using gmenu.. I will have to make this a priority over the cosmetic items, just so you all know..

---

### Post by lazyd2 on 2006-07-29
That would be great

---

### Post by _profox on 2006-07-29
> **_simon_ said:**
> I use c:Usp:80 - works fine...

I found a bug (i think)

The logout button is not using my theme logout button (OSX). All the other icons seem to be fine.
I will see what I can do about this.

> **_simon_ said:**
> And another.

Synaptic opens in another viewpoint rather than the current one.

And one more :)

The command to run Evolution was incorrect for some reason.

It was "evolution --component" instead of "evolution --component=mail"
You are probably the same guy as on compiz.net? :D
Anyway, this problem is fixed in the next release

But I can't reproduce the viewport problem. Synaptic opens in the correct viewport here...

> **_simon_ said:**
> and

In All Applications -> Games, I only have Cedega listed although I should actually have 6 other entries. I can't drag and drop into this menu... how do i add them?
Chanders is rewriting this piece of the code and he made it the top priority :) so it will probably work better in the next release

---

### Post by lazyd2 on 2006-07-29
> But I can't reproduce the viewport problem. Synaptic opens in the correct viewport here...I had the same problem where synaptic opened in "workspace 2" but I dragged to "workspace 1", then closed it and re-opened it. Since then I had no more problems...

---

### Post by _profox on 2006-07-29
> **_profox said:**
> I will see what I can do about this.
Wrong "Quit..." icon:

Was using the wrong icon there. Chanders, use "gnome-logout" instead of "gtk-quit".

I also think "gtk-add" is better than the "synaptic" icon by the way, what do you think?

Anyway. Alot of problems seem to be causing trouble with the icon sizes.
This is because some themes don't have the same icons in all sizes.

Solution: use well supported icon sizes... this should limit the icon size bugs?
Better solution: write a function that resizes the bigger icons, for icons that miss the needed size?

I'm not sure how I would do this. But if chanders is too busy, I might start googling a little bit... But I'm not sure if the icon sizes can be checked/changed in Python. I think this is a Glade thing.

But on the other hand, I'm just Python'ing for 1 day and this is the first time I opened the Glade file, so I'm not sure if what I'm saying is correct Just correct me if I'm wrong? chanders? :)

Edit: and please make the System Management buttons as high as the places buttons, otherwise some themes could cause some fonts to display incorrectly (IndustrialTango theme in my case)

---

### Post by chanders on 2006-07-29
> **_profox said:**
> Wrong "Quit..." icon:

Was using the wrong icon there. Chanders, use "gnome-logout" instead of "gtk-quit".

Fixed..

> **_profox said:**
> I also think "gtk-add" is better than the "synaptic" icon by the way, what do you think?

Looks good but we will keep it consistent...

> **_profox said:**
> Anyway. Alot of problems seem to be causing trouble with the icon sizes.
This is because some themes don't have the same icons in all sizes.

Solution: use well supported icon sizes... this should limit the icon size bugs?
Better solution: write a function that resizes the bigger icons, for icons that miss the needed size?

A function is already written for Applications, I will modify the code to work with the rest of USP. Next release+1

> **_profox said:**
> Edit: and please make the System Management buttons as high as the places buttons, otherwise some themes could cause some fonts to display incorrectly (IndustrialTango theme in my case)

Fixed in the next release

---

### Post by _profox on 2006-07-29
Are you on steroids or something? :D :eek: You are razing through development like nothing I have seen before :) you're really doing a great job!! Seriously! If development keeps going on like this, you'll reach a stable 1.0 in no time ;)

---

### Post by Note360 on 2006-07-29
We should add beta versions for the small fixes that profoX does (the not full version). Oh and if you want to help please check in at the bug tracking post. Thank you very much.

---

### Post by _simon_ on 2006-07-30
> **_profox said:**
> I will see what I can do about this.


You are probably the same guy as on compiz.net? :D
Anyway, this problem is fixed in the next release

But I can't reproduce the viewport problem. Synaptic opens in the correct viewport here...


Chanders is rewriting this piece of the code and he made it the top priority :) so it will probably work better in the next release

Hi chanders, yes it is I! ;)

It has worked better this time but still not right.

My Games menu should have the following entries:

[[IMG]http://i17.photobucket.com/albums/b96/snewberry1980/Screenshots/th_games2.png[/IMG]](http://i17.photobucket.com/albums/b96/snewberry1980/Screenshots/games2.png)

As you can see, USP has 2 Cedega entries. 
3 of the items in the menu should be cedega related:

1. Cedega itself
2. Dawn of War
3. Winter Assault

UT 2004 is also missing from games.

I have located all 3 in the Accessories menu for some reason, although both Dawn of War and Winter Assault have lost their icons (which are currently stored in /home).

I can launcg Cedega from games (first entry)
I can launch UT2004 from Accessories
Dawn of War and Winter Assault won't launch.

If it helps at all I use the following commands for each and location for icons:

Cedega 
Command "/usr/bin/cedega"
Icon "/usr/share/icons/Cedega.xpm"

Dawn of War 
Command "nonXgl cedega -run 'DOW' 'DawnofWar'"
Icon "/home/simon/icons/40k Icons/marineicon2.ico"

Winter Assault 
Command "nonXgl cedega -run 'DOW' 'WinterAssault'"
Icon "/home/simon/icons/40k Icons/sorceroricon.ico"

UT2004 
Command "nonXgl /home/simon/games/ut2004/ut2004"
Icon "/home/simon/icons/UE3 Original Logo256.png"

Others in Games:
TOCrossfire 
Command "nonXgl /home/simon/runTOC.sh"
Icon "/home/simon/games/ut2004/TOCrossfire/Help/icons/TOC_LOGO_COLORED.png"

Enemy territory 
Command "nonXgl /home/simon/games/enemy-territory/et"
Icon "/home/simon/games/enemy-territory/ET.xpm"

---

### Post by chanders on 2006-07-30
> **_simon_ said:**
> Hi chanders, yes it is I! ;)

It has worked better this time but still not right.

My Games menu should have the following entries:

[[IMG]http://i17.photobucket.com/albums/b96/snewberry1980/Screenshots/th_games2.png[/IMG]](http://i17.photobucket.com/albums/b96/snewberry1980/Screenshots/games2.png)

As you can see, USP has 2 Cedega entries. 
3 of the items in the menu should be cedega related:

1. Cedega itself
2. Dawn of War
3. Winter Assault

UT 2004 is also missing from games.

I have located all 3 in the Accessories menu for some reason, although both Dawn of War and Winter Assault have lost their icons (which are currently stored in /home).

I can launcg Cedega from games (first entry)
I can launch UT2004 from Accessories
Dawn of War and Winter Assault won't launch.

If it helps at all I use the following commands for each and location for icons:

Cedega 
Command "/usr/bin/cedega"
Icon "/usr/share/icons/Cedega.xpm"

Dawn of War 
Command "nonXgl cedega -run 'DOW' 'DawnofWar'"
Icon "/home/simon/icons/40k Icons/marineicon2.ico"

Winter Assault 
Command "nonXgl cedega -run 'DOW' 'WinterAssault'"
Icon "/home/simon/icons/40k Icons/sorceroricon.ico"

UT2004 
Command "nonXgl /home/simon/games/ut2004/ut2004"
Icon "/home/simon/icons/UE3 Original Logo256.png"

Others in Games:
TOCrossfire 
Command "nonXgl /home/simon/runTOC.sh"
Icon "/home/simon/games/ut2004/TOCrossfire/Help/icons/TOC_LOGO_COLORED.png"

Enemy territory 
Command "nonXgl /home/simon/games/enemy-territory/et"
Icon "/home/simon/games/enemy-territory/ET.xpm"



I dont know why this should be happening because gmenu brings up the GNOME menu as it is. Did you create these items yourself? If you did, make sure they have proper 'categories' sections in their .desktop files..

I will look into it as I thought that this gmenu thing would solve this problem..

Anyone else having problems with their menus?

---

### Post by _simon_ on 2006-07-30
I beleieve I did create them. Do .desktop files get created automatically or is that something I would need to do?

---

### Post by _simon_ on 2006-07-30
Found another bug :)

If you enable "do_not_filter"

Then the headings in the "All Applications" do not work.

e.g. If I click on "Office" nothing will happen.

---

### Post by chanders on 2006-07-30
> **_simon_ said:**
> Found another bug :)

If you enable "do_not_filter"

Then the headings in the "All Applications" do not work.

e.g. If I click on "Office" nothing will happen.

Good find! I will fix that in the next release... Thanks!

---

### Post by chanders on 2006-07-30
> **_simon_ said:**
> I beleieve I did create them. Do .desktop files get created automatically or is that something I would need to do?

Well it's good that you created them but you need to make sure you stick to the .desktop spec and include all the fields. Eg. The Categories field is used for sorting so you need to have something like

Categories=Games

in the files for them to show up properly under 'Games'

---

### Post by _simon_ on 2006-07-30
> **chanders said:**
> Well it's good that you created them but you need to make sure you stick to the .desktop spec and include all the fields. Eg. The Categories field is used for sorting so you need to have something like

Categories=Games

in the files for them to show up properly under 'Games'

Not sure what I am doing wrong but I made one for UT2004 but it's not taking effect.

is this correct? I've never made one before.

```

[Desktop Entry]
Encoding=UTF-8
Name=Unreal Tournament 2004
GenericName=
Comment=
Exec=nonXgl /home/simon/games/ut2004/ut2004
Terminal=false
MultipleArgs=false
Type=Application
Icon=/home/simon/Icons/UE3 Original Logo256.png
Categories=Games

```

---

### Post by chanders on 2006-07-30
> **_simon_ said:**
> Not sure what I am doing wrong but I made one for UT2004 but it's not taking effect.

is this correct? I've never made one before.

```

[Desktop Entry]
Encoding=UTF-8
Name=Unreal Tournament 2004
GenericName=
Comment=
Exec=nonXgl /home/simon/games/ut2004/ut2004
Terminal=false
MultipleArgs=false
Type=Application
Icon=/home/simon/Icons/UE3 Original Logo256.png
Categories=Games

```

Sorry, it should be game and look something like this

Categories=GNOME;GTK;Game;

Dont forget to remove and re-add the applet...

---

### Post by _simon_ on 2006-07-30
> **chanders said:**
> Sorry, it should be game and look something like this

Categories=GNOME;GTK;Game;

Dont forget to remove and re-add the applet...

I must still be doing something wrong as it's still not working :(

Edit: might help if I actually put it in usr/share/applications/ lol - working now! :) thank you.

---

### Post by chanders on 2006-07-30
> **_simon_ said:**
> I must still be doing something wrong as it's still not working :(

Edit: might help if I actually put it in usr/share/applications/ lol - working now! :) thank you.

Excellent!

---

### Post by _simon_ on 2006-07-30
However.... lol

USP doesn't seem to like .ico (I have 2 ico files for Dawn of War and WA.

I know the path is correct as the icon is displaying for the .desktop file but in USP it's a white square with a red x through it.

Edit: I've converted them to .png and all is well again :)

---

### Post by MrJeremyB on 2006-07-30
In the settings tab Network says "Wired Network: Device not configured." I connect to the Internet through a wireless connection. It would be nice if USlab would notice this.  Thanks for working hard!

Edited: Sorry I didn't read your intro clearly enough. Not too hard to change with gconf, but. . .perhaps it could be automatic or perhaps a right click would change it.

---

### Post by _profox on 2006-07-30
> Found another bug

If you enable "do_not_filter"

Then the headings in the "All Applications" do not work.

e.g. If I click on "Office" nothing will happen.
I'm going to try to fix this bug, or are you already working on it, chanders? :)

---

### Post by augied on 2006-07-30
Since I upgraded to v0.30, the menu no longer grabs focus when it is opened.  This means that A, the search bar doesn't get focus, and B, clicking somewhere else on the screen fails to close the menu until I have clicked on the menu itself, giving it the focus.

---

### Post by _profox on 2006-07-30
It's working fine here, augied... Did you remove and add the applet again after installation of the new version?

---

### Post by augied on 2006-07-30
> **_profox said:**
> It's working fine here, augied... Did you remove and add the applet again after installation of the new version?
Yes.

---

### Post by _profox on 2006-07-30
@chanders: you did not apply my patch to be able to drag the desktop folder to places, was something wrong with it, or did you forget?

---

### Post by Note360 on 2006-07-30
Ok I almost have the first bugtracking done.

---

### Post by _simon_ on 2006-07-30
I believe this to be a bug - copied from another thread by myself.

> **chanders said:**
> if /apps/usp/do_not_filter is checked, applications are not filtered when you type

Try leaving the toggle pane open but check /apps/usp/use_toggle_icon and see what you get ;)

That sort of works for me.

If I have "All Applications" open when i try typing then nothing changes - which is great.

If I have the favourite applications open then it changes to "All Applications"

---

### Post by _profox on 2006-07-30
> **_profox said:**
> I'm going to try to fix this bug, or are you already working on it, chanders? :)

Fixed the do_not_filter bug, patch coming up soon
edit: I shouted too early, with this fix, an old bug has returned... but I'm not giving up :) I'm going back to the original, and I'm going to do it in a better way :)

---

### Post by _profox on 2006-07-30
I had some time off and I tried again :) success!
The filter now behaves like it should. I've been testing it as much as possible

Changes:
+ application category buttons are still clickable when you have do_not_filter on
+ menu does NOT go to all applications when you have do_not_filter on

The patch will probably be included in the next version, I'm going to post it in the Beta/Patch category now :)

---

### Post by _simon_ on 2006-07-30
I don't know if this is a USP bug as such but I'm a bit puzzled.

In Graphics, Inkscape seems to have been replaced by "Remove Package" the comment does however match Inkscape. The icon is that of a box rather than the inkscape icon.

The inkscape.desktop appears fine:

```

[Desktop Entry]
Name=Inkscape Vector Illustrator
Comment=Create and edit Scalable Vector Graphics images
Comment[ca]=Creeu i editeu imatges de gràfics de vectors escalables
Comment[cs]=Vytvá&#345;ejte a upravujte vektorovou grafiku (SVG)
Comment[de]=Skalierbare Vektorgrafiken (SVG) erzeugen und bearbeiten
Comment[es]=Cree y edite Gráficos Vectoriales Escalables (SVG)
Comment[eu]=SVG irudiak sortu eta editatu
Comment[fr]=Créer et éditer des images Scalable Vector Graphics
Comment[hu]=Scalable Vector Graphics (méretezhet&#337; vektorgrafika, SVG) képek létrehozása és szerkesztése
Comment[it]=Crea e modifica immagini Scalable Vector Graphics
Comment[nl]='Scalable Vector Graphics (SVG) '-tekeningen maken en bewerken
Comment[nn]=Lag og rediger skalerbare vektorbilete (SVG)
Comment[pa]=&#2616;&#2581;&#2631;&#2610;&#2631;&#2604;&#2610; &#2613;&#2632;&#2581;&#2591;&#2608; &#2583;&#2608;&#2622;&#2603;&#2623;&#2581;&#2616; &#2586;&#2623;&#2673;&#2596;&#2608; &#2604;&#2595;&#2622;&#2579; &#2565;&#2596;&#2631; &#2616;&#2635;&#2599;&#2635;
Comment[pl]=Utwórz i edytuj rysunki wektorowe SVG
Comment[ru]=&#1057;&#1086;&#1079;&#1076;&#1072;&#1074;&#1072;&#1090;&#1100; &#1080; &#1080;&#1079;&#1084;&#1077;&#1085;&#1103;&#1090;&#1100; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1103; &#1074; SVG
Comment[sl]=Ustvarjaj in urejaj SVG vektorske slike
Comment[sr]=&#1055;&#1088;&#1072;&#1074;&#1113;&#1077;&#1114;&#1077; &#1080; &#1091;&#1088;&#1077;&#1106;&#1080;&#1074;&#1072;&#1114;&#1077; SVG &#1074;&#1077;&#1082;&#1090;&#1086;&#1088;&#1089;&#1082;&#1080;&#1093; &#1089;&#1083;&#1080;&#1082;&#1072;
Comment[sr@Latn]=Pravljenje i ure&#273;ivanje SVG vektorskih slika
Comment[uk]=&#1057;&#1090;&#1074;&#1086;&#1088;&#1077;&#1085;&#1085;&#1103; &#1090;&#1072; &#1088;&#1077;&#1076;&#1072;&#1075;&#1091;&#1074;&#1072;&#1085;&#1085;&#1103; &#1074;&#1077;&#1082;&#1090;&#1086;&#1088;&#1085;&#1080;&#1093; &#1075;&#1088;&#1072;&#1092;&#1110;&#1095;&#1085;&#1080;&#1093; &#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1100;

Encoding=UTF-8
Version=1.0

Type=Application
Categories=Application;Graphics;VectorGraphics;GTK;

MimeType=image/svg+xml

FilePattern=inkscape
Exec=inkscape %F
TryExec=inkscape
Terminal=false
StartupNotify=true

Icon=inkscape.png
X-Ubuntu-Gettext-Domain=inkscape
X-AppInstall-Package=inkscape
X-AppInstall-Section=main

```

[[IMG]http://i17.photobucket.com/albums/b96/snewberry1980/Screenshots/th_inkscapemissing.png[/IMG]](http://i17.photobucket.com/albums/b96/snewberry1980/Screenshots/inkscapemissing.png)


Any ideas? :confused:

---

### Post by chanders on 2006-07-30
> **_simon_ said:**
> I don't know if this is a USP bug as such but I'm a bit puzzled.

In Graphics, Inkscape seems to have been replaced by "Remove Package" the comment does however match Inkscape. The icon is that of a box rather than the inkscape icon.

The inkscape.desktop appears fine:

```

[Desktop Entry]
Name=Inkscape Vector Illustrator
Comment=Create and edit Scalable Vector Graphics images
Comment[ca]=Creeu i editeu imatges de gràfics de vectors escalables
Comment[cs]=Vytvá&#345;ejte a upravujte vektorovou grafiku (SVG)
Comment[de]=Skalierbare Vektorgrafiken (SVG) erzeugen und bearbeiten
Comment[es]=Cree y edite Gráficos Vectoriales Escalables (SVG)
Comment[eu]=SVG irudiak sortu eta editatu
Comment[fr]=Créer et éditer des images Scalable Vector Graphics
Comment[hu]=Scalable Vector Graphics (méretezhet&#337; vektorgrafika, SVG) képek létrehozása és szerkesztése
Comment[it]=Crea e modifica immagini Scalable Vector Graphics
Comment[nl]='Scalable Vector Graphics (SVG) '-tekeningen maken en bewerken
Comment[nn]=Lag og rediger skalerbare vektorbilete (SVG)
Comment[pa]=&#2616;&#2581;&#2631;&#2610;&#2631;&#2604;&#2610; &#2613;&#2632;&#2581;&#2591;&#2608; &#2583;&#2608;&#2622;&#2603;&#2623;&#2581;&#2616; &#2586;&#2623;&#2673;&#2596;&#2608; &#2604;&#2595;&#2622;&#2579; &#2565;&#2596;&#2631; &#2616;&#2635;&#2599;&#2635;
Comment[pl]=Utwórz i edytuj rysunki wektorowe SVG
Comment[ru]=&#1057;&#1086;&#1079;&#1076;&#1072;&#1074;&#1072;&#1090;&#1100; &#1080; &#1080;&#1079;&#1084;&#1077;&#1085;&#1103;&#1090;&#1100; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1103; &#1074; SVG
Comment[sl]=Ustvarjaj in urejaj SVG vektorske slike
Comment[sr]=&#1055;&#1088;&#1072;&#1074;&#1113;&#1077;&#1114;&#1077; &#1080; &#1091;&#1088;&#1077;&#1106;&#1080;&#1074;&#1072;&#1114;&#1077; SVG &#1074;&#1077;&#1082;&#1090;&#1086;&#1088;&#1089;&#1082;&#1080;&#1093; &#1089;&#1083;&#1080;&#1082;&#1072;
Comment[sr@Latn]=Pravljenje i ure&#273;ivanje SVG vektorskih slika
Comment[uk]=&#1057;&#1090;&#1074;&#1086;&#1088;&#1077;&#1085;&#1085;&#1103; &#1090;&#1072; &#1088;&#1077;&#1076;&#1072;&#1075;&#1091;&#1074;&#1072;&#1085;&#1085;&#1103; &#1074;&#1077;&#1082;&#1090;&#1086;&#1088;&#1085;&#1080;&#1093; &#1075;&#1088;&#1072;&#1092;&#1110;&#1095;&#1085;&#1080;&#1093; &#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1100;

Encoding=UTF-8
Version=1.0

Type=Application
Categories=Application;Graphics;VectorGraphics;GTK;

MimeType=image/svg+xml

FilePattern=inkscape
Exec=inkscape %F
TryExec=inkscape
Terminal=false
StartupNotify=true

Icon=inkscape.png
X-Ubuntu-Gettext-Domain=inkscape
X-AppInstall-Package=inkscape
X-AppInstall-Section=main

```

[[IMG]http://i17.photobucket.com/albums/b96/snewberry1980/Screenshots/th_inkscapemissing.png[/IMG]](http://i17.photobucket.com/albums/b96/snewberry1980/Screenshots/inkscapemissing.png)


Any ideas? :confused:

My Inkscape looks fine, hmmmm... Does your .desktop file have thoses spaces or did  you include the space just to point out it is ok?

The .desktop file should not have any spaces...

---

### Post by _profox on 2006-07-30
Also post your ~/.usp/applications/inkscape.desktop please :)
("gedit ~/.usp/applications/inkscape.desktop" to view in gedit)

---

### Post by _simon_ on 2006-07-30
The spaces were already there.

I haven't got an inkscape.desktop in ~/.usp/applications, only the following:

```

evolution-mail.desktop  gimp-2.2.desktop                update-manager.desktop
gaim.desktop            ooo-writer.desktop
gconf-editor.desktop    Unreal Tournament 2004.desktop

```

---

### Post by chanders on 2006-07-30
> **_simon_ said:**
> The spaces were already there.

I haven't got an inkscape.desktop in ~/.usp/applications, only the following:

```

evolution-mail.desktop  gimp-2.2.desktop                update-manager.desktop
gaim.desktop            ooo-writer.desktop
gconf-editor.desktop    Unreal Tournament 2004.desktop

```

He meant /usr/share/applications....
~/.usp/applications onlu have .desktop files for your Favourite applications..

---

### Post by _simon_ on 2006-07-30
There wasn't one in /usr/share/applications/

The one I quoted above was in /usr/share/app-install/desktop/

I've created one which has now added it to Graphics but I still have the "Remove Package" listed that does nothing but has Inkscapes comment field :confused:

I've tried viewing /use/share/applications/ in icon view but the icon that's displaying for Remove Package isn't in there.

lol now I am more confused.

I found another "Remove Package" with the same box icon in "System Tools", the comment this time is "Directly edit your entire configuration database" again, clicking on it does nothing.

Neither the name or icon appears in Alacarte. However I notice the same icon used for GDebi Package Installer which i don't have set to display in Alacarte but the comment for that is "Install and view software packages"

On a side note, I notice a few .desktop files for the same program e.g. evolution has 2, do I need 2 or can I delete one?

---

### Post by chanders on 2006-07-30
> **_simon_ said:**
> There wasn't one in /usr/share/applications/

The one I quoted above was in /usr/share/app-install/desktop/

I've created one which has now added it to Graphics but I still have the "Remove Package" listed that does nothing but has Inkscapes comment field :confused:

I've tried viewing /use/share/applications/ in icon view but the icon that's displaying for Remove Package isn't in there.

lol now I am more confused.

I found another "Remove Package" with the same box icon in "System Tools", the comment this time is "Directly edit your entire configuration database" again, clicking on it does nothing.

Neither the name or icon appears in Alacarte. However I notice the same icon used for GDebi Package Installer which i don't have set to display in Alacarte but the comment for that is "Install and view software packages"

LOL, your system sounds like spagethi!  Basically USP uses GNOME to provide the menu. It is not supposed to show anything that is not in you gnome menu.... You need to hunt down those .desktop files that you created ...

Most .desktop files should be in ~/.local/share/applications and /usr/share/applications. I wouldnt advise putting them anywhere else as they clutter your suystem or worse.. leave ghost entries ;-)

---

### Post by _simon_ on 2006-07-30
The ones I have created I have only been putting in /usr/share/applications/ I'll check out the other location!

---

### Post by _profox on 2006-07-30
[COLOR="Red"]**VERY IMPORTANT !!!**[/COLOR]
[B]All bugs that haven't been resolved yet, and all new bugs have to be reported on our malone bugtracker!!
Please goto [https://launchpad.net/products/usp/+bugs](https://launchpad.net/products/usp/+bugs) to find and report bugs!
Don't report bugs here anymore! Thanks :)
[/B]

---

### Post by _simon_ on 2006-07-30
There was an inkscape.desktop one in local, I've removed it and it's removed one of the "Remove Package" listed, now I have to work out which the other is.

---

### Post by Note360 on 2006-07-30
Ok please report all bugs at [http://launchpad.net/products/usp](http://launchpad.net/products/usp) as well as here so we can divy and manage it better (and post patches to it). Thank you.

---

### Post by _simon_ on 2006-07-30
So confused.

Got rid of both of the "Remove Package" entries... well sort of.

1 remains but it's now taken on the comment from Automatix and I have no idea why. The automatix.desktop file is ok and Automatix IS displaying.

As a test I removed automatix.desktop and now the Remove Package has taken on the comment from Movie Player.

SOLVED!

It was "3rd Party Package Manager" aka "autopackage-manager-gtk"

---

### Post by _simon_ on 2006-07-31
I don't know if this is a USP bug so only posting here for now...

This command will work from terminal:

```

nonXgl cedega -run 'DOW' 'DawnofWar'

```

It will also run fine from the standard Gnome menu and the Slab menu but it will not run from USP.

I have the following in .desktop:

```

[Desktop Entry]
Encoding=UTF-8
Name=Dawn of War
GenericName=
Comment=
Exec=nonXgl cedega -run 'DOW' 'DawnofWar'
Terminal=false
MultipleArgs=false
Type=Application
Icon=/home/simon/Icons/40k Icons/marineicon2.png
Categories=GNOME;GTK;Game;

```

---

### Post by Note360 on 2006-07-31
ok I will start a Technical Support forum for problems that are not bugs ok. (It is easier to use a bug tracker) 


_simon_ - Hmm should work. Try making a shell script that launches the application then using the add custom application launcher in the add to panel menu link to the script. now that it is on the panel  pin USP and drag it into Favorite apps and launch it. If that doesnt work come back.

```

#!/usr/bin/sh

nonXgl cedega -run 'DOW' 'DawnofWar

```

that should work

---

### Post by _profox on 2006-07-31
> **_simon_ said:**
> I don't know if this is a USP bug so only posting here for now...

This command will work from terminal:

```

nonXgl cedega -run 'DOW' 'DawnofWar'

```

It will also run fine from the standard Gnome menu and the Slab menu but it will not run from USP.

I have the following in .desktop:

```

[Desktop Entry]
Encoding=UTF-8
Name=Dawn of War
GenericName=
Comment=
Exec=nonXgl cedega -run 'DOW' 'DawnofWar'
Terminal=false
MultipleArgs=false
Type=Application
Icon=/home/simon/Icons/40k Icons/marineicon2.png
Categories=GNOME;GTK;Game;

```
are you trying to run it as a favourite application or in the all applications menu?

try to add it to favourites and give me the contents of the file:
~/.usp/applications/whatever-the-name-is.desktop

---

### Post by _simon_ on 2006-07-31
> **_profox said:**
> are you trying to run it as a favourite application or in the all applications menu?

try to add it to favourites and give me the contents of the file:
~/.usp/applications/whatever-the-name-is.desktop

I have tried both but neither works.

Contents of ~/.usp/applications/dawn-of-war.desktop

```

[Desktop Entry]
Encoding=UTF-8
Name=Dawn of War
Comment=
Exec=nonXgl cedega -run 'DOW' 'DawnofWar'
Icon=/home/simon/Icons/40k Icons/marineicon2.png
GenericName=
Terminal=false

```

---

### Post by Note360 on 2006-07-31
My way was just a work around.

here is what one of mine looks like
```

[Desktop Entry]
Encoding=UTF-8
Name=AbiWord Word Processor
Comment=AbiWord Word Processor
Exec=abiword
Icon=abiword
GenericName=Abiword
Terminal=false

```

maybe try turning Terminal to true.

---

### Post by Note360 on 2006-07-31
Is the Icon working? cause in Unix based systems you type spaces as a \  followed by a space.

Edit: ONLY IN PATHNAMES

---

### Post by _simon_ on 2006-07-31
> **Note360 said:**
> ok I will start a Technical Support forum for problems that are not bugs ok. (It is easier to use a bug tracker) 


_simon_ - Hmm should work. Try making a shell script that launches the application then using the add custom application launcher in the add to panel menu link to the script. now that it is on the panel  pin USP and drag it into Favorite apps and launch it. If that doesnt work come back.

```

#!/usr/bin/sh

nonXgl cedega -run 'DOW' 'DawnofWar

```

that should work

It will not allow me to drag it into favourites.

---

### Post by Note360 on 2006-07-31
are you sure? oh sorry let me clear that up. You make a Application Launcher in the gnome panel and then drag that to favorites or you make another desktop file drag that to the gnome panel and then into the favorites.

---

### Post by _simon_ on 2006-07-31
> **Note360 said:**
> Is the Icon working? cause in Unix based systems you type spaces as a \  followed by a space.

Edit: ONLY IN PATHNAMES

The icon works fine and I tried terminal=true earlier but no luck.

---

### Post by _simon_ on 2006-07-31
> **Note360 said:**
> are you sure?

lol yes, I tried to drag it in at least 5 times to different areas of the favourite menu - between existing apps, after existing apps, onto the space etc.

---

### Post by _simon_ on 2006-07-31
Ok, I just made a new launcher in the panel then dragged it to favourites in USP.

If I launch it from the gnome panel it runs.

If I launch it from USP favourites it does not.

/.usp/applications/dow.desktop contents:

```

[Desktop Entry]
Encoding=UTF-8
Name=DOW
Comment=
Exec=nonXgl cedega -run 'DOW' 'DawnofWar'
Icon=/home/simon/Icons/40k Icons/marineicon2.png
GenericName=
Terminal=false

```

---

### Post by Note360 on 2006-07-31
ok hmm odd. I am actually having a simular problem with a texteditor called scribes.

---

### Post by _simon_ on 2006-07-31
as long as it's not just me ;)

---

### Post by _profox on 2006-07-31
> **_simon_ said:**
> I have tried both but neither works.

Contents of ~/.usp/applications/dawn-of-war.desktop

```

[Desktop Entry]
Encoding=UTF-8
Name=Dawn of War
Comment=
Exec=nonXgl cedega -run 'DOW' 'DawnofWar'
Icon=/home/simon/Icons/40k Icons/marineicon2.png
GenericName=
Terminal=false

```

Okay.. it works fine here, without nonXgl (because I don't have nonXgl...)
Try running usp in a window and try to run your program from there.. does it give a message in the terminal window?

just run:
/usr/bin/usp run-in-window

in your terminal
you don't have to close the USP in your panel

to stop the new usp window, press ctrl+c in the terminal

---

### Post by Note360 on 2006-07-31
I fixed scribes by removing %f

---

### Post by _simon_ on 2006-07-31
> **_profox said:**
> Okay.. it works fine here, without nonXgl (because I don't have nonXgl...)
Try running usp in a window and try to run your program from there.. does it give a message in the terminal window?

just run:
/usr/bin/usp run-in-window

in your terminal
you don't have to close the USP in your panel

to stop the new usp window, press ctrl+c in the terminal

I get this error in terminal:

```

ERROR: No game group ''DOW'' exists.

```

---

### Post by Note360 on 2006-07-31
that is significant. Does Dow exist try it without DOW

---

### Post by _profox on 2006-07-31
> **Note360 said:**
> I fixed scribes by removing %f

I think this problem was already fixed? otherwise write a new patch for it ;)

---

### Post by _simon_ on 2006-07-31
> **Note360 said:**
> that is significant. Does Dow exist try it without DOW

I'm not sure what you mean.

DOW exists within Cedega.

I know for a fact that the command is correct as it has always worked and still works from Gnome menu, Slab menu, panel and desktop launchers.

---

### Post by Note360 on 2006-07-31
Well you could just launch cedega and then click DOW. I dont have this problem as I am on a PPC so I have no Cedega so I am just talking.

---

### Post by _simon_ on 2006-07-31
Yes I could but.....

If there is no fix for this then I will, however I'm hoping someone can get it to work.

---

### Post by _profox on 2006-07-31
Report it to the bugs section in launchpad if you can.. that makes it easier for us: [https://launchpad.net/products/usp/+bugs](https://launchpad.net/products/usp/+bugs)

---

### Post by Note360 on 2006-07-31
Well, put Cedega in their for now and try this in the next release. We will try and figure something out. The next relese should be out tonight or tomorrow.

---

### Post by _simon_ on 2006-07-31
> **_profox said:**
> Report it to the bugs section in launchpad if you can.. that makes it easier for us: [https://launchpad.net/products/usp/+bugs](https://launchpad.net/products/usp/+bugs)

Done... hope I put enough info in... not done a proper bug report before.

---

### Post by _profox on 2006-08-01
> **_simon_ said:**
> Done... hope I put enough info in... not done a proper bug report before.

A fix is committed. It will most likely get accepted.
In the meantime you can fix your application by editing the desktop file.

Please tell me, who/what application made the menu/.desktop entry for that game?

Just make it: cedega --run DOW DawnofWar
instead of: cedega --run 'DOW' 'DawnofWar'

however, in the next version, you can do both ;) if the patch gets accepted.. it probably will

---

### Post by _simon_ on 2006-08-01
thank you - it does work without the ''''

I made the .desktop file. I believe i got the command from the Cedega forums.

---

### Post by _profox on 2006-08-01
Yes, that's the main problem then :)
You're not supposed to use a --> ' <-- in a command.
You can, but it will be ignored by the terminal.
And with the latest patch, USP will ignore it too.

---

### Post by Hells_Dark on 2006-08-02
I have a new (very small) bug with the new release :
I dont know if that's normal, but the text is cut withy some applications :
[[img]http://pix.nofrag.com/fe/b8/93ecfcb632008dce8ecdfc2e5862t.jpg[/img]](http://pix.nofrag.com/fe/b8/93ecfcb632008dce8ecdfc2e5862.html)
And there isn't the "..."

---

### Post by _profox on 2006-08-02
The code that takes care of the ".." is sucky :) It doesn't care about font sizes etc. I will fix this in one of the following releases by using ellips, please report a bug on [http://www.launchpad.net/products/usp](http://www.launchpad.net/products/usp)

---

### Post by Hells_Dark on 2006-08-02
I reported it.

---

### Post by Uncle Spellbinder on 2006-08-02
First, I really love USP. So much better than the default Ubuntu menu.

Small problem. Using 0.31, under "Settings" which brings up "Computer". Clicking "Control Center" does nothing. But If I add it to favorites, it opens just fine.

---

### Post by lazyd2 on 2006-08-02
> **Uncle Spellbinder said:**
> First, I really love USP. So much better than the default Ubuntu menu.

Small problem. Using 0.31, under "Settings" which brings up "Computer". Clicking "Control Center" does nothing. But If I add it to favorites, it opens just fine.

Do you have Ubuntu Control Center installed? If not 
```
sudo apt-get install gcontrol
```

---

### Post by Uncle Spellbinder on 2006-08-02
> **lazyd2 said:**
> Do you have Ubuntu Control Center installed? If not 
```
sudo apt-get install gcontrol
```

Thanks. The "control center" I added to favorites opens the default control center, I guess. And the one in "Computer" opens Gcontrol.

---

### Post by lazyd2 on 2006-08-02
> **Uncle Spellbinder said:**
> Thanks. The "control center" I added to favorites opens the default control center, I guess. And the one in "Computer" opens Gcontrol.
Problem solved then...:)

---

### Post by Uncle Spellbinder on 2006-08-02
> **lazyd2 said:**
> Problem solved then...:)

Indeed!  Thank you very much. :wink:

---

### Post by lazyd2 on 2006-08-02
> **Uncle Spellbinder said:**
> Indeed!  Thank you very much. :wink:
Anytime :-D

---

### Post by gruvsyco on 2006-08-03
I've got my USP set up by default to load showing only the applications menu... on startup, it does not show any of the management icons along the left until I open and then close the places section.

---

### Post by lazyd2 on 2006-08-03
*edit*

---

### Post by chanders on 2006-08-03
> **gruvsyco said:**
> I've got my USP set up by default to load showing only the applications menu... on startup, it does not show any of the management icons along the left until I open and then close the places section.

This bug was patched by **vonpmg** and will be fixed in the next release...

---

### Post by gruvsyco on 2006-08-03
sweet!

---

### Post by airwolf on 2006-08-03
I am not sure if it is just me or a bug. After I add the terminal to favorites and then launch it, the current working directory is set to root rather then the default user home folder. This of course is no big deal but I would just like to get a confirmation whether it happens to me or everyone else as well.

Thanks.

---

### Post by _profox on 2006-08-03
It happens here too....

---

### Post by gruvsyco on 2006-08-03
yup, here too

---

### Post by lazyd2 on 2006-08-03
The same thing happens when you want to save something(Save as...)in Gimp for example. The default should be the "home directory" and not the "file system"(don't know if its common to everyone).

When Gimp is launched from the default Gnome menu it has as default save point my /home directory...

---

### Post by PsyberOneZero on 2006-08-03
I too get the / bug, it's more annoying than anything.

I've also got a new one, with USP loaded my CPU shoots up to 100%, now I am using Edgy AMD64, so I'm the minority of the minoritym but is there a way to chase this down (gdb/valgrind?)

Great Work!

---

### Post by lazyd2 on 2006-08-03
For the "root" problem the bug has been reported

[Applications launched from USP point to "root" directory.]("https://launchpad.net/products/usp/+bug/55127")

---

### Post by RawMustard on 2006-08-03
Just installed Bonfire CD-DVD burning app.  It needs a -p %u argument which when run from usp causes this error.

Error while loading the project:
the project could not be opened.

Once I close the error dialog, the app starts up normaly.
It works fine in standard gnome menu!

Also, if I add %u to firefox, it takes me to some strange website :(

---

### Post by _profox on 2006-08-04
I think that's related to the previous bug, but I'm not sure

---

### Post by Gioppo on 2006-08-04
I upgraded to 0.32 and I still have the same problem:

I change the applet icon to a custom one, and it is resized without any reason:

[[IMG]http://img60.imageshack.us/img60/784/problemrd2.png[/IMG]](http://imageshack.us)

The icon's the same. On the left it is used with the gnome-menu, on the right with USP.

Am I doing something wrong?

Oh, I forgot: gnome, wm metacity, icon theme OSX (based on Tango)

---

### Post by _profox on 2006-08-04
What's the size of your bar? I think it resizes to the size to fit in a 24px gnome-panel.

---

### Post by Gioppo on 2006-08-04
> **_profox said:**
> What's the size of your bar? I think it resizes to the size to fit in a 24px gnome-panel.


The bar size is only 22 (i resized the image to make the problem more visible).

By the way, I tried to resize the bar to fit the image (both reducing and improving it's height) and it showed the same problem. It keeps a border aroud it, that is highlited when I click on it.

---

### Post by chanders on 2006-08-04
> **Gioppo said:**
> The bar size is only 22 (i resized the image to make the problem more visible).

By the way, I tried to resize the bar to fit the image (both reducing and improving it's height) and it showed the same problem. It keeps a border aroud it, that is highlited when I click on it.

Have you tested with another theme jst to see what would happen? The USP menu is a ToggleButton and maybe your theme sets ToggleButtons differently...

Try a variety of scenarios like different icon names, panel sizes and themes and post your results. It would help us track down the bug :D

---

### Post by Hells_Dark on 2006-08-04
What about my my icon size bug ? It's annoying..

---

### Post by lazyd2 on 2006-08-05
Don't know if its really a bug, but here it goes:

Wanted to try a new application [(Panda DesktopSecure)]("http://ubuntuforums.org/showthread.php?t=230022") from dapper-commerical repository. As you can see from the screenshot it creates a new menu entry. The problem is that it will not show in USP...:p

---

### Post by chanders on 2006-08-05
> **lazyd2 said:**
> Don't know if its really a bug, but here it goes:

Wanted to try a new application [(Panda DesktopSecure)]("http://ubuntuforums.org/showthread.php?t=230022") from dapper-commerical repository. As you can see from the screenshot it creates a new menu entry. The problem is that it will not show in USP...:p

It seems that the plugin system will have to be put on pause while I work on this. This should be solved in the next release...

Quick question.. Do the panda items show up in "All Applications"?

---

### Post by lazyd2 on 2006-08-05
> Quick question.. Do the panda items show up in "All Applications"?Yes they do.
Sorry for the trouble, but I had to ask...

---

### Post by lazyd2 on 2006-08-05
@chanders: I have attached the installation locations(in case you need them)

---

### Post by _profox on 2006-08-05
We need to make the groups dynamic instead of static buttons. This should get high priority

---

### Post by chanders on 2006-08-05
> **_profox said:**
> We need to make the groups dynamic instead of static buttons. This should get high priority

Already has, and I am already working on it ;)

---

### Post by Oppi on 2006-08-06
Hi

Can anybody tell me, why the application "Nautilus Browser in root mode" does not work? 

This is the only application that does not start when i want to open it from app-menu is USP.

Is it a bug ?

greetings, Oppi

---

### Post by Danny Boy on 2006-08-06
> **Uncle Spellbinder said:**
> First, I really love USP. So much better than the default Ubuntu menu.

Small problem. Using 0.31, under "Settings" which brings up "Computer". Clicking "Control Center" does nothing. But If I add it to favorites, it opens just fine.

Same Here :)
> **lazyd2 said:**
> Do you have Ubuntu Control Center installed? If not 
```
sudo apt-get install gcontrol
```

What repostitiory is it on? 
```
dan@BigDan:~$ sudo apt-get install gcontrol
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcontrol
```

Thank you in advnace, 
Dan

---

### Post by chanders on 2006-08-06
> **Danny Boy said:**
> Same Here :)


What repostitiory is it on? 
```
dan@BigDan:~$ sudo apt-get install gcontrol
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcontrol
```

Thank you in advnace, 
Dan

it's in Quinn's repository... See [http://xgl.compiz.info](http://xgl.compiz.info) for details

---

### Post by Gioppo on 2006-08-06
> **chanders said:**
> Have you tested with another theme jst to see what would happen? The USP menu is a ToggleButton and maybe your theme sets ToggleButtons differently...

Try a variety of scenarios like different icon names, panel sizes and themes and post your results. It would help us track down the bug :D

Ok, I'll do it asap

I already tried different names and panel sizes, and it behave the same way.

I'll try to change theme to see if it's a theme problem.

---

### Post by Danny Boy on 2006-08-06
> **chanders said:**
> it's in Quinn's repository... See [http://xgl.compiz.info](http://xgl.compiz.info) for details

Thanks that was easy :) BTW if I didn't mention it before USP is an awesome app!

---

### Post by orb9220 on 2006-08-09
Was working until I upgraded to 33.

Launches from main menu just fine.
Deleted usp icon from favourites. And readded still no go.

Name
DvD Shrink

Generic Name
DVD Movies

exec
wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe"

icon
/usr/share/pixmaps/DVDShrink.png

Hope this helps and can be fixed,

---

### Post by Gioppo on 2006-08-10
> **Gioppo said:**
> Ok, I'll do it asap

I already tried different names and panel sizes, and it behave the same way.

I'll try to change theme to see if it's a theme problem.

I just switched to xgl + compiz, and the problem stays the same.

I'll try to switch icon theme, maybe it's a problem related to tango icons.

---

### Post by chanders on 2006-08-10
> **orb9220 said:**
> Was working until I upgraded to 33.

Launches from main menu just fine.
Deleted usp icon from favourites. And readded still no go.

Name
DvD Shrink

Generic Name
DVD Movies

exec
wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe"

icon
/usr/share/pixmaps/DVDShrink.png

Hope this helps and can be fixed,

This seems to be a problem with the space in the exec command. This has been popping up recently... I will ask one of the devs to take a look at it. If they cant I will as soon as I launch the plugin system...

---

### Post by vonpmg on 2006-08-10
> **chanders said:**
> This seems to be a problem with the space in the exec command. This has been popping up recently... I will ask one of the devs to take a look at it. If they cant I will as soon as I launch the plugin system...

Please Chanders, continue with your work in the plugin system. It's very important ;) 
I'll try to fix this bug (Bug #55793).
Actually i fix the %f,%F,... part.
I am going to fix the spaces in arguments.

---

### Post by Hells_Dark on 2006-08-12
Hi,
I'm trying the new version (0.4).
I still have problems with my icons...

I've got a new icon problem with the place pannel icon on the left, and the icon size bug in the application pannel.

[[img]http://pix.nofrag.com/62/8d/791a593aa0f34352f556da2c2afbt.jpg[/img]](http://pix.nofrag.com/62/8d/791a593aa0f34352f556da2c2afb.html)

That's really not pretty.

---

### Post by chanders on 2006-08-12
> **Hells_Dark said:**
> Hi,
I'm trying the new version (0.4).
I still have problems with my icons...

I've got a new icon problem with the place pannel icon on the left, and the icon size bug in the application pannel.

[[img]http://pix.nofrag.com/62/8d/791a593aa0f34352f556da2c2afbt.jpg[/img]](http://pix.nofrag.com/62/8d/791a593aa0f34352f556da2c2afb.html)

That's really not pretty.

I will try to fix this.. I's so hard to find default icon names... so many different themes have different icons missing...

Suggest one that is in all themes and i will make the change.. If you want you can change the name in line 245 in /usr/bin/usp

---

### Post by lazyd2 on 2006-08-12
Don't know if this is a bug or thats the way its supposed to be...

Why doesn't "Places" use the hole height of the pane when on its own?(dont like the scrollbar)

If this is a bug, can it be fixed?

---

### Post by chanders on 2006-08-12
> **lazyd2 said:**
> Don't know if this is a bug or thats the way its supposed to be...

Why doesn't "Places" use the hole height of the pane when on its own?(dont like the scrollbar)

If this is a bug, can it be fixed?

Thats because the 'Places' plugin has a fixed height. I will make this configurable so do not despair. Again sleep was the culprit ;)

Just for the time being put another plugin under it, like system_management :)

---

### Post by lazyd2 on 2006-08-12
[QUOTE=chanders]Just for the time being put another plugin under it, like system_management [/QUOTE]
lol, thanks chanders...

---

### Post by atie on 2006-08-12
I have this entry as one of favorite applications.

> 
cat /home/atie/.usp/applications/Eclipse.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Eclipse
Comment=Eclipse IDE
Exec=/home/atie/bin/eclipse.sh
Icon=/home/atie/eclipse/icon.xpm
GenericName=
Terminal=false


But, USP can't execute it by clicking. USP version is 0.40-1.

---

### Post by fantan on 2006-08-12
Hi chanders,

Today night I downloaded and installed the new version (0.4-1) of the usp. It is done very-very fine, my congratulations!
However I found some bugs in it:

1. I realized you use the first version of my Hungarian translation, although there were three errors in it. A week ago I fixed them and sent the fixed version to you. Now I send the last, fixed version again.
2. The names of the panes are in English, although in the gconf-editor I corrected the names of panes from English to Hungarian (apps/usp -> key:pane_order -> Edit key).
3. By right-clicking on the pane Places, there is the word "Edit" which I didn't found in the source for translation. Because of this, in the Hungarian version besides of the names of the panes just one word "Edit" is in English.
   
My last, corrected version of the translation is as follows:
> 
# SOME DESCRIPTIVE TITLE.
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
# Albert Fazakas <fantan@axelero.hu>, 2006.
# This is the second fix.
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: 0.32\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: 2006-08-07 11:24+0100\n"
"Last-Translator: Albert Fazakas <fantan@axelero.hu>\n"
"Language-Team: Albert Fazakas <fantan@axelero.hu>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=hu_HU.UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "Helyek"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "Alkalmazások"

#: usp.glade:247
msgid "Settings"
msgstr "Beállítások"

#: usp.glade:598
msgid "System Management"
msgstr "Adminisztráció"

#: usp.glade:663
msgid "Install Software"
msgstr "Szoftver telepítés"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "Vezérl&#337;központ"

#: usp.glade:788
msgid "Lock screen"
msgstr "Képerny&#337;zár"

#: usp.glade:852
msgid "Quit..."
msgstr "Kilépés..."

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "Számítógép"

## 
#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr "<span size=\"small\">Minden alkalmazás</span>" # fix

#: usp.glade:1287
msgid "All Applications"
msgstr "Minden alkalmazás"

#: usp.glade:1345
msgid "<span size=\"small\"> Favourites</span>"   # fix
msgstr "<span size=\"small\"> Kedvencek</span>"     # fix

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> Kellékek</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> Játékok</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> Grafika</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> Internet</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> Iroda</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> Programozás</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> Audio és Video</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> Rendszereszközök</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> Beállítások</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> Minden</span>"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">További alkalmazások...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr "Írd be, mit keressek"

#: usp.glade:2216
msgid "Search"
msgstr "Keresés"

#: usp.glade:2516
msgid "Network"
msgstr "Hálózat"

#: usp.glade:2640
msgid "Date and Time"
msgstr "Dátum és id&#337;"

#: usp.glade:2764
msgid "Theme"
msgstr "Téma"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "Képerny&#337; felbontás"

#: usp.glade:3037
msgid "Configure your system"
msgstr "Rendszerkonfigurálás"

#: usp.glade:3133
msgid "Move up"
msgstr "Mozgatás fel"

#: usp.glade:3142
msgid "Move down"
msgstr "Mozgatás le"

#: usp.glade:3151
msgid "Edit labels"
msgstr "Cimkék módosítása"

#: usp.glade:3160
msgid "Insert separator"
msgstr "Elválasztó csík beszúrása"

#: usp.glade:3169
msgid "Insert space"
msgstr "Üres hely beszúrása"

#: usp.glade:3178
msgid "Remove"
msgstr "Eltávolítás"

#: usp.glade:3187
msgid "Edit item"
msgstr "Tétel módosítása"

#: usp.glade:3256
msgid "Name"
msgstr "Név"

#: usp.glade:3300
msgid "Generic name"
msgstr "Általános név"

#: usp.glade:3343
msgid "Comment"
msgstr "Megjegyzés"

#: usp.glade:3386
msgid "Exec"
msgstr "Futtatás"

#: usp.glade:3429
msgid "Icon"
msgstr "Ikon"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "Hozzáadás a kedvencekhez"



Please, send me the new source for the translation.

My Congratulations again and best regards,

fantan

---

### Post by Hells_Dark on 2006-08-12
> **chanders said:**
> I will try to fix this.. I's so hard to find default icon names... so many different themes have different icons missing...

Suggest one that is in all themes and i will make the change.. If you want you can change the name in line 245 in /usr/bin/usp

Ok, thanks.
That's the worst bug i have since the begining.
I'm however using the gnome icon theme..:( 

But, i still trusting in you :mrgreen:

---

### Post by chanders on 2006-08-12
> **atie said:**
> I have this entry as one of favorite applications.

But, USP can't execute it by clicking. USP version is 0.40-1.

Did it work in a previous version of USP?

---

### Post by atie on 2006-08-12
> **chanders said:**
> Did it work in a previous version of USP?
Never mind. I put "#!/bin/bash" (without "") line to the top of my eclipse.sh, then it's working now.

---

### Post by mattisking on 2006-08-13
Having a small problem with 0.40. Places won't fill up the entire pane, even though I moved the System menu elsewhere. An image is attached.

The new version is really nice. I'm excited about the plugin system. I'm looking forward to being able to customize the look of some of them (like the time/date plugin) with more configuration options in future version.

---

### Post by Fass on 2006-08-13
> **mattisking said:**
> Having a small problem with 0.40. Places won't fill up the entire pane, even though I moved the System menu elsewhere. An image is attached.

I was going to report this last night, but I was too lazy to provide pics and explain what I meant. The scroll bar is annoying and ugly, IMO. Places should fill up the pane, and should also "push down" whatever is below it if there is something below it, until there is no space left in the pane. Only then should you get a scroll bar.

---

### Post by _simon_ on 2006-08-13
To confirm - I have the same problem with places having a scroll bar.

---

### Post by Hells_Dark on 2006-08-13
> **chanders said:**
> I will try to fix this.. I's so hard to find default icon names... so many different themes have different icons missing...

Suggest one that is in all themes and i will make the change.. If you want you can change the name in line 245 in /usr/bin/usp

What i don't understand, it's that with USP 0.3x i didn't have this first problem with the place icon :neutral:

---

### Post by Uncle Spellbinder on 2006-08-13
> **_simon_ said:**
> To confirm - I have the same problem with places having a scroll bar.

Confirmed here as well.

**EDIT:**
Might it be related to the ***compact_system_management*** choice in Gconf? Previously, when I checked that box, Places would expand. This is no longer the case.

---

### Post by lazyd2 on 2006-08-13
For the "Places" pane problem, check [here]("http://www.ubuntuforums.org/showpost.php?p=1372288&postcount=119")

---

### Post by chanders on 2006-08-13
> **lazyd2 said:**
> For the "Places" pane problem, check [here]("http://www.ubuntuforums.org/showpost.php?p=1372288&postcount=119")

Places and height is now configurable in the new release (0.41)

/apps/usp/plugins/applications/height
/apps/usp/plugins/places/height

---

### Post by lazyd2 on 2006-08-14
> **chanders said:**
> Places and height is now configurable in the new release (0.41)

/apps/usp/plugins/applications/height
/apps/usp/plugins/places/height

Thank you chanders :-({|=

---

### Post by Uncle Spellbinder on 2006-08-14
@ lazyd2

How did you move *System Management* to it's own area?

---

### Post by lazyd2 on 2006-08-14
> **Uncle Spellbinder said:**
> @ lazyd2

How did you move *System Management* to it's own area?

Just add "newpane" in **plugins_list**

Check mine, below...

---

### Post by Uncle Spellbinder on 2006-08-14
I'm an idiot!  I found the plugins list and added "newpane". Worked. I ended up putting System Management under Computer.


Ha ha.  Ya just beat me. :)

---

### Post by lazyd2 on 2006-08-14
> **Uncle Spellbinder said:**
> I'm an idiot!  I found the plugins list and added "newpane". Worked. I ended up putting System Management under Computer.
lol

---

### Post by Uncle Spellbinder on 2006-08-14
What font is that. Like it a lot.

---

### Post by lazyd2 on 2006-08-14
> **Uncle Spellbinder said:**
> What font is that. Like it a lot.
Its called *Swis721 Cn BT*
(if you can't find it send me a pm)

---

### Post by Sammi on 2006-08-14
First off: Nice work chanders! :KS

Second: I only want to complain about one little problem: :D ;)
The menu doesn't disapear like I would like it to do when it loses fokus. Most menues I have used do this, but with this menu I have to click either on some link inside the menu or on the menu button itself to get it to disapear.

Don't know if this is a bug or a missing feature.

---

### Post by Uncle Spellbinder on 2006-08-14
> **Sammi said:**
> First off: Nice work chanders! :KS

Second: I only want to complain about one little problem: :D ;)
The menu doesn't disapear like I would like it to do when it loses fokus. Most menues I have used do this, but with this menu I have to click either on some link inside the menu or on the menu button itself to get it to disapear.

Don't know if this is a bug or a missing feature.



Make sure it isn't "pinned". I thought the same thing, but when I un-highlighted the small thin bar on the top left of USP, all was fine.

---

### Post by Sammi on 2006-08-14
I'm sure I have tried having that "pin" in both positions before... but anyway: that solved my problem, thanks! :D

---

### Post by LordMau on 2006-08-17
> **Sammi said:**
> I'm sure I have tried having that "pin" in both positions before... but anyway: that solved my problem, thanks! :D

Hmm no you're correct this stuck behaviour still exists. I'll describe how it happens here in my system:

[LIST=1][*]Newly logged in, I click the USP button. Once open I glide the cursor over the menu WITHOUT clicking. Leaving the menu area CLOSES USP. Nice effect! Like activating focus-follows-mouse.
[*] Next click panel button again. USP menu opens. Now click on the desktop. USP closes.
[*]Next, I open USP, I select an item from the USP. As expected USP closes then the app starts.[*]Now click the USP once again. Then do not select anything from the menu. Let the cursor leave the menu area. Menu doesnt close.[*]Now click on the desktop. USP still doesn't close.[*]Click on any dead area in the USP. Menu still doesn't close.[*]Only by selecting a menu item within USP or clicking the panel button again will close USP.
[/LIST]

To restore the initial behaviour I had to logout/login or maybe removing/ reinstalling the applet would work.

I last used 0.33 before 0.41, and that older USP had the proper behaviour in this regard. BTW was the effect described in 1. a conscious design, or does it just happen to me?

---

### Post by SlyBlyahoff on 2006-08-24
Hello all. 
Sorry if my post is not at place but i think maybe it is for this Topic.
I have that kind of problem or bug, i don't know how exactly to call it.
I didn't restart my ubuntu 5.10 for maybe already 48 hours, which i think is something normal. But unexpected this morning my firefox started to crash. 
While i am surfing the net on eny kind of pages when i click on some link to post something or to load other related page and my firefox browser is closing itself and erasing all the cache memory. 
Please tell me do you know some reason for that. What is the problem in that case. 

10X all of you in advance.

---

### Post by minisori on 2006-08-25
Hmm for some reason now the weather pluging is loading in another window when i start usp. And in the panel it says plugin weather not found. :-s

---

### Post by lazyd2 on 2006-08-25
> **minisori said:**
> Hmm for some reason now the weather pluging is loading in another window when i start usp. And in the panel it says plugin weather not found. :-s
Thats weird...I got that too:-k

---

### Post by lazyd2 on 2006-08-25
> **minisori said:**
> Hmm for some reason now the weather pluging is loading in another window when i start usp. And in the panel it says plugin weather not found. :-s

> **lazyd2 said:**
> Thats weird...I got that too:-k

Bug report has been [submited]("https://launchpad.net/products/usp/+bug/57740")

---

### Post by minisori on 2006-08-25
Lol and now for some reason is working again :-s weird

---

### Post by lazyd2 on 2006-08-25
> **minisori said:**
> Lol and now for some reason is working again :-s weird

Its working now here as well :-k ](*,) :mrgreen:

---

### Post by mejy on 2006-08-29
I don't know if this is a known bug or even intentional, but there is a gap of about 10 pixls between the top of the menu and the bottom of the menubar.  I tried searching but couldn't find anything relevant.

---

### Post by chanders on 2006-08-29
> **mejy said:**
> I don't know if this is a known bug or even intentional, but there is a gap of about 10 pixls between the top of the menu and the bottom of the menubar.  I tried searching but couldn't find anything relevant.

Try setting panel_size to 1, this will be fixed in the next release...

---

