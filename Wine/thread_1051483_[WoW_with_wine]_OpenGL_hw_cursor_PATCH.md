---
title: "[WoW with wine] OpenGL hw cursor PATCH"
date: 2009-01-26
forum: Wine
---

### Post by SKLP on 2009-01-26
Hi!

Some of you who play WoW with its OpenGL mode have probably noticed that support for Hardware Cursor is not available. 

Well, I had this problem for a while as well: DirectX providing hw cursor support, and OpenGL providing much higher fps..

So I cooked up a patch to wine which makes wine ignore Windows program's requests to change the cursor (e.g. hide it ), so it will simply show the X arrow cursor all the time. This cursor (the normal X cursor) will move faster than the frame rate, so it's a kind of hw cursor. The patch will make wow display 2 cursors, one normal X cursor moving at full speed, and the slow wow cursor lagging behind depending on fps. 

That said, for me personally it has improved my game play especially when healing in lower fps situations.
I've been using the patch for i guess a few months now, So I thought I'd share it with you guys in case anyone is interested :)

Good luck.

UPDATE: Check out the updated instructions by Doctor Debian: [http://ubuntuforums.org/showpost.php?p=7643957&postcount=82](http://ubuntuforums.org/showpost.php?p=7643957&postcount=82).

---

### Post by phlack on 2009-01-29
Thanks for posting this. It may be useful to me. I'm having another issue entirely. If no one replies soon, I'll start a new thread. Beyond a certain upward angle, my cursor disappears entirely in game. It still functions but is invisible. 
If I'm on a flying mount, It vanishes if I'm looking straight ahead or up. I have to look down to see it. So, It sounds to me like it may have something to do with background. I dunno though. I'm gonna try this.

If anyone else can think of anything else, lemme know.

phlack

---

### Post by phlack on 2009-01-29
anyway to fix this without having to recompile from source?

---

### Post by SKLP on 2009-01-30
not as far as I know :/
Use debian-style build so you get a deb and not mess up your filesystem (through make install)
basically like this( if u dont know):
1) sudo apt-get install build-essential fakeroot devscripts
2) sudo apt-get build-dep wine
3) apt-get source wine
4) cd wine-1.whatever
5) dch -i 
the new changelog entry should have a very high version number so it wont be replaced automatically from the repositories when a new version becomes available
6) apply any patches
7) dpkg-buildpackage -rfakeroot -us -uc -b
This should put some deb files outside the directory (in ..)

gl

---

### Post by Ameneon on 2009-01-30
> **phlack said:**
> Thanks for posting this. It may be useful to me. I'm having another issue entirely. If no one replies soon, I'll start a new thread. Beyond a certain upward angle, my cursor disappears entirely in game. It still functions but is invisible. 
If I'm on a flying mount, It vanishes if I'm looking straight ahead or up. I have to look down to see it. So, It sounds to me like it may have something to do with background. I dunno though. I'm gonna try this.

If anyone else can think of anything else, lemme know.

phlack

Not my solution, but

```
/console farclip 499
```

in the game chat will probably solve the problem as it sounds exactly like the problem I had. The explanation was given in this thread:

[http://ubuntuforums.org/showthread.php?t=1052433](http://ubuntuforums.org/showthread.php?t=1052433)

Worked just dandy for me at least :)

---

### Post by johnl on 2009-01-30
> **phlack said:**
> Thanks for posting this. It may be useful to me. I'm having another issue entirely. If no one replies soon, I'll start a new thread. Beyond a certain upward angle, my cursor disappears entirely in game. It still functions but is invisible. 
If I'm on a flying mount, It vanishes if I'm looking straight ahead or up. I have to look down to see it. So, It sounds to me like it may have something to do with background. I dunno though. I'm gonna try this.

If anyone else can think of anything else, lemme know.

phlack

What happens is that the mouse cursor is incorrectly being drawn 'under' certain terrain elements, notably the sky.

I have read that this was a bug introduced in the latest WoW version -- it's not on the wine side. The workaround that was posted was to use the hardware cursor option, which of course you can't do under opengl.

It is fairly frustrating.  Sorry I can't help more.

---

### Post by Active123 on 2009-01-31
I found a workaround for the cursor disappearing.  Basically you just need to reduce the "View Distance" to the lowest setting that works for you.  It is under Video > Effects.  That corrected my problem with the cursor disappearing in the "sky".

---

### Post by Ameneon on 2009-01-31
I shall not make a bet on this but I do believe that adjusting the view distance is what the command I pasted above (which you enter in the chat) does, and rather than setting it to the minimum that will work for you (which doesn't make sense if you think about it, we want long view distance, not short, right?) it sets it to maximum - almost, as the problem only appears if you attempt to show maximum view distance.

---

### Post by Doctor Debian on 2009-01-31
Patch isn't working, patching with

patch -p0 < wine-cursor-patch.txt

In the mouse directory results in

Hunk #1 FAILED at 185.
Hunk #2 succeeded at 737 with fuzz 2 (offset -173 lines).
Hunk #3 FAILED at 756.

---

### Post by Active123 on 2009-01-31
Ok, I didnt clearly understand what the console command was for.  That worked for me too.  Im still shaking my head at how dumb I feel :)

---

### Post by Doctor Debian on 2009-01-31
I don't find changing the farclip a fix, rather a disadvantage. I absolutely hate not being able to see anything while flying >.>

EDIT: It appears there are multiple mouse.c files. Which directory is the intended file to be patched in?

---

### Post by SKLP on 2009-02-01
Sorry.... guess I'll make a new patch against the whole wine folder. 

So apply it like this:
```
cd wine-1.1*
patch -p1 < /path/to/patch-file
```

---

### Post by Doctor Debian on 2009-02-02
Works great =D

---

### Post by isit on 2009-02-05
Thanks for great idea, i did some improvements to it :) 

1. Put [http://swa.org.ru/wow/Cursor.rar](http://swa.org.ru/wow/Cursor.rar) to the wow_directory/Interface (wow_directory/Interface/Cursor/Point.blp) - it will hide WoW internal cursor. 

2. Slightly modified patch to use XC_left_ptr instead of XC_arrow: [http://swa.org.ru/wow/wine-cursor-patch-new1.txt](http://swa.org.ru/wow/wine-cursor-patch-new1.txt) 

3. Put big shiny cursor theme for your xorg 

And voilà, we have hardware cursor in opengl mode and no problems with hiding cursor in the far distance :)

---

### Post by SKLP on 2009-02-05
> **isit said:**
> Thanks for great idea, i did some improvements to it :) 

1. Put [http://swa.org.ru/wow/Cursor.rar](http://swa.org.ru/wow/Cursor.rar) to the wow_directory/Interface (wow_directory/Interface/Cursor/Point.blp) - it will hide WoW internal cursor. 

2. Slightly modified patch to use XC_left_ptr instead of XC_arrow: [http://swa.org.ru/wow/wine-cursor-patch-new1.txt](http://swa.org.ru/wow/wine-cursor-patch-new1.txt) 

3. Put big shiny cursor theme for your xorg 

And voilà, we have hardware cursor in opengl mode and no problems with hiding cursor in the far distance :)You're welcome.

Thx for the "improved" patch. However I don't really consider hiding the real wow cursor an improvement, because it provides extra info e.g. information about what im pointing at e.g. a repair npc

---

### Post by isit on 2009-02-05
No, it removes only main pointer. You still can see every special pointers near 'hardware' one.

---

### Post by isit on 2009-02-05
Looking how to extract native Pointer.blp to convert it to xpm and put in xorg cursor theme as some custom arrow :)

---

### Post by SKLP on 2009-02-05
Hehe ok :)

Although I believe it's against the WoW EULA to replace game files like this. (and could in theory get u banned)
I think so atleast but unsure.

---

### Post by SKLP on 2009-02-05
Should be pretty easy to extract the real Pointer file though, as there are, I believe, quite a few MPQ tools out there...

---

### Post by isit on 2009-02-05
No, it's like an addon, not replacing anything in MPQ. Alot of custom cursors for wow on curse.com provided this way

---

### Post by SKLP on 2009-02-05
Yes but not clear if they are allowed if they aren't normal addons (which reside in Interface/AddOns/*), AFAIK
But maybe it's fine to use em anyways i dont know

---

### Post by isit on 2009-02-05
it's a part of AddOnKit from official site [http://us.blizzard.com/support/article.xml?articleId=21466](http://us.blizzard.com/support/article.xml?articleId=21466), so i'm sure it's ok.

anyway, i tried to use native cursor and it sucks ( too huge and ugly :) ) using now ComixCursors-opaque-Blue-Regular and i'm very happy! it's almost HW cursor. need to check it in 25man soon :)

---

### Post by dardack on 2009-02-05
> **isit said:**
> it's a part of AddOnKit from official site [http://us.blizzard.com/support/article.xml?articleId=21466](http://us.blizzard.com/support/article.xml?articleId=21466), so i'm sure it's ok.

anyway, i tried to use native cursor and it sucks ( too huge and ugly :) ) using now ComixCursors-opaque-Blue-Regular and i'm very happy! it's almost HW cursor. need to check it in 25man soon :)

Ok what did you do?  Just curious.  What I mean is the ComixCursors thing, where does it go?

---

### Post by isit on 2009-02-06
[www.xaprb.com/blog/2006/04/24/beautiful-x11-cursors/](www.xaprb.com/blog/2006/04/24/beautiful-x11-cursors/)

---

### Post by SKLP on 2009-02-10
Isit, Could you please send me your extracted/converted wow cursor please. Thanks

---

### Post by Alakabaster on 2009-02-10
Thanks for making that, isit, it's great!

One small thing, though: Whenever one pushes a mouse button and then moves the mouse (which will move either the camera or the character and the camera, depending on which mousebutton one took), the cursor doesn't simply vanish (as it does originally), but jump to the center and "jiggle around". After one releases the button, the cursor jumps back to where it was before. It's not really a show-stopper, but slightly annoying, is there any chance you could change that? Maybe you don't have to hide the cursor, just make it stay where it was before... and if that's too much, maybe just get right of the "jiggling"?

If not, no problem, it's still much better than keeping it as it was :) Thanks again :)

---

### Post by Mmmbopdowedop on 2009-02-10
> **SKLP said:**
> Hi!

Some of you who play WoW with its OpenGL mode have probably noticed that support for Hardware Cursor is not available. 

Well, I had this problem for a while as well: DirectX providing hw cursor support, and OpenGL providing much higher fps..

So I cooked up a patch to wine which makes wine ignore Windows program's requests to change the cursor (e.g. hide it ), so it will simply show the X arrow cursor all the time. This cursor (the normal X cursor) will move faster than the frame rate, so it's a kind of hw cursor. The patch will make wow display 2 cursors, one normal X cursor moving at full speed, and the slow wow cursor lagging behind depending on fps. 

That said, for me personally it has improved my game play especially when healing in lower fps situations.
I've been using the patch for i guess a few months now, So I thought I'd share it with you guys in case anyone is interested :)

Good luck.

Hi there, firstly i'd like to thank you for this script you made, nice job, really seems a hell of a lot smoother using the default mouse rather than the OpenGL drawn one.

I think i'd prefere to keep it this way, rather than be able to use the WoW Hardware Cursor.

> **isit said:**
> Thanks for great idea, i did some improvements to it :) 

1. Put [http://swa.org.ru/wow/Cursor.rar](http://swa.org.ru/wow/Cursor.rar) to the wow_directory/Interface (wow_directory/Interface/Cursor/Point.blp) - it will hide WoW internal cursor. 


This is great too, helps to identify what the NPC's are as someone stated.

> **Alakabaster said:**
> Thanks for making that, isit, it's great!

One small thing, though: Whenever one pushes a mouse button and then moves the mouse (which will move either the camera or the character and the camera, depending on which mousebutton one took), the cursor doesn't simply vanish (as it does originally), but jump to the center and "jiggle around". After one releases the button, the cursor jumps back to where it was before. It's not really a show-stopper, but slightly annoying, is there any chance you could change that? Maybe you don't have to hide the cursor, just make it stay where it was before... and if that's too much, maybe just get right of the "jiggling"?

If not, no problem, it's still much better than keeping it as it was :) Thanks again :)

But I have to agree with this guy, when moving with the mouse (Like most players do), the mouse jumps right back into the center of the screen until released, now, say I was PvPing I usually have to click on the health bars of players when there's several, rather than tab-targetting for hours.
It's hard to do that when you've no idea where the cursor is as soon as you let go with it. :-)

Very distracting seeing this little thing "Jiggle'ing" around in the center there.

But again, appreciate this script, it's nice & all, just don't think I could cope with all the time just yet.
It would be nice for healing though, massive improvement there.

Edit: Been playing with it for a bit now, it's definately alot better than the OpenGL cursor once you get used to it.

I encourage everyone to give this a try if they have low fps and struggle with the OpenGL cursor. :)

---

### Post by SKLP on 2009-02-12
Could be possible to modify wine to hide the X cursor when right mousebutton is being held down. Although it's probably not so easy to do considering that it probably should not hide the cursor if it's just a rightclick (if the button is only down for an instant).
I'm not going to try anyways as I don't consider the "Jiggling" much of a problem once you get used to it.

---

### Post by larsson on 2009-02-13
this is the wrong way of doing it in so many ways, but.. enjoy :P

---

### Post by Alakabaster on 2009-02-15
> **larsson said:**
> this is the wrong way of doing it in so many ways, but.. enjoy :P

Thanks for that :) Doesn't compile though:

```
mouse.c: In function 'X11DRV_ButtonPress':
mouse.c:1072: error: expected expression before 'Pixmap'
mouse.c:1073: warning: ISO C90 forbids mixed declarations and code
mouse.c:1077: error: 'blank' undeclared (first use in this function)
mouse.c:1077: error: (Each undeclared identifier is reported only once
mouse.c:1077: error: for each function it appears in.)
make[2]: *** [mouse.o] Error 1
make[2]: Leaving directory `/home/pips/wine-1.1.14-patch2/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/pips/wine-1.1.14-patch2/dlls'
make: *** [dlls] Error 2

```

This is on Gentoo, though, there might be issues ^^

---

### Post by SKLP on 2009-02-15
Thx for that one. I'm gonna try it soon.

---

### Post by cb951303 on 2009-02-16
> **Alakabaster said:**
> Thanks for that :) Doesn't compile though:

```
mouse.c: In function 'X11DRV_ButtonPress':
mouse.c:1072: error: expected expression before 'Pixmap'
mouse.c:1073: warning: ISO C90 forbids mixed declarations and code
mouse.c:1077: error: 'blank' undeclared (first use in this function)
mouse.c:1077: error: (Each undeclared identifier is reported only once
mouse.c:1077: error: for each function it appears in.)
make[2]: *** [mouse.o] Error 1
make[2]: Leaving directory `/home/pips/wine-1.1.14-patch2/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/pips/wine-1.1.14-patch2/dlls'
make: *** [dlls] Error 2

```

This is on Gentoo, though, there might be issues ^^

getting errors at the same line, slightly different error though. I'll paste soon.

---

### Post by cb951303 on 2009-02-16
> **isit said:**
> Thanks for great idea, i did some improvements to it :) 

1. Put [http://swa.org.ru/wow/Cursor.rar](http://swa.org.ru/wow/Cursor.rar) to the wow_directory/Interface (wow_directory/Interface/Cursor/Point.blp) - it will hide WoW internal cursor. 

2. Slightly modified patch to use XC_left_ptr instead of XC_arrow: [http://swa.org.ru/wow/wine-cursor-patch-new1.txt](http://swa.org.ru/wow/wine-cursor-patch-new1.txt) 

3. Put big shiny cursor theme for your xorg 

And voilà, we have hardware cursor in opengl mode and no problems with hiding cursor in the far distance :)

now if we can find a solution for jiggling (preferably by hiding the cursor while left and right press-holding) it would be the perfect WoW experience :)

---

### Post by larsson on 2009-02-17
updated for left and right button.. enjoy :)

it still is the wrong way of doing it in so many ways, i urge someone with knowledge of wine's(thread) inner workings to make this proper..

---

### Post by cb951303 on 2009-02-17
here is a patched wine package. I should have renamed it to something like wine_patched but I didn't bother :p. The package source is the one provided at winehq ubuntu download page.

[http://www.4shared.com/file/88136543/e3c9775b/wine_1114winehq0ubuntu810-0ubuntu1_i386.html](http://www.4shared.com/file/88136543/e3c9775b/wine_1114winehq0ubuntu810-0ubuntu1_i386.html)

EDIT: this is for patch **wine-cursor-patch-new.txt**

---

### Post by cb951303 on 2009-02-17
> **larsson said:**
> updated for left and right button.. enjoy :)

it still is the wrong way of doing it in so many ways, i urge someone with knowledge of wine's(thread) inner workings to make this proper..

tested, it works.

but shouldn't it make the cursor invisible when the mouse buttons are held pressed. currently it disappears even with single clicks.

I'm working on a slightly more complex version. Cursor will disappear only when its located in a small box on the center of the screen and the buttons are held pressed. Again not perfect but, optimum solution with what we have.

---

### Post by dardack on 2009-02-20
> **isit said:**
> it's a part of AddOnKit from official site [http://us.blizzard.com/support/article.xml?articleId=21466](http://us.blizzard.com/support/article.xml?articleId=21466), so i'm sure it's ok.

anyway, i tried to use native cursor and it sucks ( too huge and ugly :) ) using now ComixCursors-opaque-Blue-Regular and i'm very happy! it's almost HW cursor. need to check it in 25man soon :)

Ok I got this working, but WoW still uses like I would call it the windows default mouse icon instead of xorg's theme'd icon.  Any ideas?

EDIT for clarification:  Wine uses window's themed mouse icon's.  Therefore the WoW window also uses these themed mouse icon and not xorgs.

---

### Post by Snypercell on 2009-02-20
> **dardack said:**
> Ok I got this working, but WoW still uses like I would call it the windows default mouse icon instead of xorg's theme'd icon.  Any ideas?

in which folder do you stick this? wow addons?

---

### Post by Snypercell on 2009-02-20
> **Snypercell said:**
> in which folder do you stick this? wow addons?

nvm....

---

### Post by Snypercell on 2009-02-20
> **SKLP said:**
> not as far as I know :/
Use debian-style build so you get a deb and not mess up your filesystem (through make install)
basically like this( if u dont know):
1) sudo apt-get install build-essential fakeroot devscripts
2) sudo apt-get build-dep wine
3) apt-get source wine
4) cd wine-1.whatever
5) dch -i 
the new changelog entry should have a very high version number so it wont be replaced automatically from the repositories when a new version becomes available
6) apply any patches
7) dpkg-buildpackage -rfakeroot -us -uc -b
This should put some deb files outside the directory (in ..)

gl


how do i install the patch? not there yet, but thought i'd get a head start

---

### Post by Snypercell on 2009-02-22
what do i do afer step 5, and before 6? this is what i'm looking at after i enter the command in 5:

___________________________________________________________________________
wine (1.0.0-1ubuntu4~hardy1ubuntu1) hardy; urgency=low

  *

 -- James Rutland <snypercell@BlackBoook>  Sun, 22 Feb 2009 12:03:01 -0700

                                                              [ Read 3123 lines ]
^G Get Help            ^O WriteOut            ^R Read File           ^Y Prev Page           ^K Cut Text            ^C Cur Pos
^X Exit                ^J Justify             ^W Where Is            ^V Next Page           ^U UnCut Text          ^T To Spell

___________________________________________________________________________

---

### Post by dardack on 2009-02-22
Don't know why you want to make a .deb file.  You can just compile from source and install wine.
If you have previously installed wine you need to uninstall it first.

```
sudo apt-get build-dep wine
```
then download wine source 1.14 (or 1.15 the patch here should work in both)
extract the source somewhere
open a terminal and cd to where the source is
```
patch -p1 < /path/to/patch-fil
./configure
make depend
make
sudo make install
```

You should then have a fully functioning patch wine install.

---

### Post by dardack on 2009-02-23
BTW, I now have xorg cursors in wine.  I had compiled wine with the patch, but didn't install and didn't reboot when I tried it out.  I have since installed the patch version and rebooted, and now have Xorg cursors in wine (WoW).  I personally like the ComixCursors-black regular, it's a bit transparent, so when you mouse over things in WoW, you can see the whole icon underneath the cursor.  With a non transparent cursor, i sometimes couldn't always see the sword.

---

### Post by Mmmbopdowedop on 2009-02-23
> **cb951303 said:**
> getting errors at the same line, slightly different error though. I'll paste soon.

Did you find a solution for this btw?

I did an upgrade in Debian and it must have updated Wine at the same time, so I needed to patch again, only this time I got errors, gutted. :(

Any help would be appreciated. :)

---

### Post by h2sammo on 2009-02-23
> **dardack said:**
> Don't know why you want to make a .deb file.  You can just compile from source and install wine.
If you have previously installed wine you need to uninstall it first.

```
sudo apt-get build-dep wine
```
then download wine source 1.14 (or 1.15 the patch here should work in both)
extract the source somewhere
open a terminal and cd to where the source is
```
patch -p1 < /path/to/patch-fil
./configure
make depend
make
sudo make install
```

You should then have a fully functioning patch wine install.

ok...is downloading the wine source 1.14...etc any different than installing wine through the APT repository?
can you give an example of how the 
```
patch -p1 < /path/to/patch-fil
./configure
make depend
make
sudo make install
```
is supposed to look like?

---

### Post by dardack on 2009-02-24
> **h2sammo said:**
> ok...is downloading the wine source 1.14...etc any different than installing wine through the APT repository?
can you give an example of how the 
```
patch -p1 < /path/to/patch-fil
./configure
make depend
make
sudo make install
```
is supposed to look like?

Yes the APT repository only has wine version 1.01? (something like that the stable version), wine 1.14 is stable but not supported by ubuntu i think.  I forget how it works.  Anyways, i don't know what you mean by look like.  You open a terminal (if you have generic ubuntu) click Applications->Accesories->Terminal (and no i can't spell accesories).

Once that opens you'll have something like:
```
<name of your computer>-$
``` with a blinking cursor.

Now you have to know where you extracted the wine source to and where you downloaded the patch txt file.  For me it's in my /home/myname/Downloads folder, whereas Wine source is extracted to /home/myname/Programs folder.  So i'll give you example based on this.  From the blinking cursor:

```

sudo apt-get build-dep wine (this is required to make sure you have all libraries wine needs to build)
cd /home/myname/Programs/wine-1.14
patch -p1 < /home/myname/Downloads/patch.txt (i forget exact name, i renamed mine)
./configure
make depend
make
sudo make install

```

Just type that all out.  Hope that helps.

---

### Post by formulajay on 2009-02-28
> **isit said:**
> Thanks for great idea, i did some improvements to it :) 

1. Put [http://swa.org.ru/wow/Cursor.rar](http://swa.org.ru/wow/Cursor.rar) to the wow_directory/Interface (wow_directory/Interface/Cursor/Point.blp) - it will hide WoW internal cursor. 

2. Slightly modified patch to use XC_left_ptr instead of XC_arrow: [http://swa.org.ru/wow/wine-cursor-patch-new1.txt](http://swa.org.ru/wow/wine-cursor-patch-new1.txt) 

3. Put big shiny cursor theme for your xorg 

And voilà, we have hardware cursor in opengl mode and no problems with hiding cursor in the far distance :)


I tried this and it just leaves a white box where the cursor used to be. So, I see the wine cursor, which I want displayed, but I see a white box where the original wow cursor used to be. I just want the wow cursor to be gone. If anyone has any idea how to remedy that, it would be greatly appreciated.

---

### Post by dardack on 2009-02-28
> **formulajay said:**
> I tried this and it just leaves a white box where the cursor used to be. So, I see the wine cursor, which I want displayed, but I see a white box where the original wow cursor used to be. I just want the wow cursor to be gone. If anyone has any idea how to remedy that, it would be greatly appreciated.

Don't know.  I put the Cursor.rar contents into <wow directory>/Interface and no more wow cursor.

---

### Post by _silence on 2009-03-02
ok I'm a new linux user so I don't know much on how to compile something.I've read all the posts in this tread but I don't understand what I need to do to make this patch for wine to work.So if anyone of you can make a simple guide step by step would be appreciated.

Thanks for your time.

---

### Post by formulajay on 2009-03-03
> **dardack said:**
> Don't know.  I put the Cursor.rar contents into <wow directory>/Interface and no more wow cursor.


I have used the Point.blp file to successfully make WoW's main cursor disappear, but it will only last until I quit the game and then it will proceed to use the white box as the cursor.

It seems to work only when it wants to, I have to load the game over and over until it decides to hide the cursor rather then display a white box in it's place.

---

### Post by Mmmbopdowedop on 2009-03-08
> **Pey Tudor said:**
> Did you find a solution for this btw?

I did an upgrade in Debian and it must have updated Wine at the same time, so I needed to patch again, only this time I got errors, gutted. :(

Any help would be appreciated. :)

Sorted this, downloaded the libasound2 deb from the Experimental Debian Repos and used the package that you uploaded to 4shared, is now working again, so thanks for the package! :)

---

### Post by GodveX on 2009-03-09
Can anyone do a step by step on how to patch this problem because linux right now is hard for me just switched to ubuntu from xp and dont wanna switch back since i found it comfortable all i have is this tiny problem and dont know how to solve it =/

EDIT: No Problem I Solved it thanks anyway

---

### Post by f2ip on 2009-03-09
> **cb951303 said:**
> here is a patched wine package. I should have renamed it to something like wine_patched but I didn't bother :p. The package source is the one provided at winehq ubuntu download page.

[http://www.4shared.com/file/88136543/e3c9775b/wine_1114winehq0ubuntu810-0ubuntu1_i386.html](http://www.4shared.com/file/88136543/e3c9775b/wine_1114winehq0ubuntu810-0ubuntu1_i386.html)

EDIT: this is for patch **wine-cursor-patch-new.txt**

thanks for the easy install!

one question, though. did you modify the cursor patch at all? i'm asking because when i installed your patched wine-1.1.14 it managed to keep my themed cursor while in WoW. today i noticed wine-1.1.16 was out so i downloaded it and applied the cursor patch to it, however, my themed cursor does not carry over into WoW now and i get the default cursor instead.

---

### Post by cb951303 on 2009-03-10
> **f2ip said:**
> thanks for the easy install!

one question, though. did you modify the cursor patch at all? i'm asking because when i installed your patched wine-1.1.14 it managed to keep my themed cursor while in WoW. today i noticed wine-1.1.16 was out so i downloaded it and applied the cursor patch to it, however, my themed cursor does not carry over into WoW now and i get the default cursor instead.

Nope I didn't modify it.
You can compare the mouse.c files from 1.1.14 and 1.1.16 to see if there is anything else added (by wine team?) that could cause it:popcorn:

---

### Post by urd on 2009-03-16
> **SKLP said:**
> Sorry.... guess I'll make a new patch against the whole wine folder. 

So apply it like this:
```
cd wine-1.1*
patch -p1 < /path/to/patch-file
```

when i use cd wine-1.1* says this


```
urd@urd-laptop:~$ cd wine-1.1*
bash: cd: wine-1.1*: No such file or directory

```

---

### Post by dardack on 2009-03-17
> **urd said:**
> when i use cd wine-1.1* says this


```
urd@urd-laptop:~$ cd wine-1.1*
bash: cd: wine-1.1*: No such file or directory

```

First, it's not wine-1.1*, the * is representative of the current version of wine you downloaded, this patch works with 1.12 through 1.14 at least (for me it does anyways).  So you want to remove the * and put in the number for what version you downloaded.

Also, Did you extract the wine source to you ~ directory?  Cause you'll want to cd to were you extracted it first.

---

### Post by kronostm on 2009-03-23
First of all I want to thank everyone that worked for this patch. It is WAAY more than Blizz does for Linux community, so grats, nice job.

however ...
I have patched my wine-1.1.17 on ubuntu 8.04 and no result, I have the same cursor with the same latency as before patch.
  The patch applied correctly , wine compiled with no error, though no change in HWCursor. Anyone experienced something like this? Anyone tried the patch with wine-1.1.17?

P.S. I have checked the file mouse.c and it was modified according to the patch, so everything ok on that side.

---

### Post by mendres on 2009-03-24
I patched latest version 1.1.17 today, here is the package for download:

[http://files.filefront.com/wine+1117+1+i386deb/;13519258;/fileinfo.html](http://files.filefront.com/wine+1117+1+i386deb/;13519258;/fileinfo.html)

Tested on Ubuntu 8.10! Have fun with it :)

---

### Post by squaffbag on 2009-03-27
I also patched 1.1.17 - it is without a doubt more acceptable than without patching, but I still find the cursor lagging a bit - even with mouse sensitivity/speed turned right down

I guess if anything it stopped me from being a 'clicker' and got me into keybinding :)

Still... a better fix is needed - so far I've just re-grouped all things 'not' keybound to a small area of my action bar to prevent hair loss

---

### Post by fredslacks on 2009-04-13
Okay I am having some trouble patching the new cursor to wine.

I have updated all of the files using the first step.  I put the cursors folder in the right place for WoW.  I am trying to patch the text file to wine and cannot get my terminal to find the txt file.

Heres what I'm doing:


The txt file is on my desktop and I have renamed it to patch.txt

patch -p1 </home/myname/desktop/patch.txt
and I get no such file or directory.

I'm sure I'm not the only one out there with this problem is there any help?

---

### Post by pissedoffdude on 2009-04-14
> **fredslacks said:**
> Okay I am having some trouble patching the new cursor to wine.

I have updated all of the files using the first step.  I put the cursors folder in the right place for WoW.  I am trying to patch the text file to wine and cannot get my terminal to find the txt file.

Heres what I'm doing:


The txt file is on my desktop and I have renamed it to patch.txt

patch -p1 </home/myname/desktop/patch.txt
and I get no such file or directory.

I'm sure I'm not the only one out there with this problem is there any help?

Linux is case-sensitive, so make sure you're capitalizing Desktop.  If in doubt, you can always drag and drop the patch.

---

### Post by Mmmbopdowedop on 2009-04-15
> **isit said:**
> Thanks for great idea, i did some improvements to it :) 

1. Put [http://swa.org.ru/wow/Cursor.rar](http://swa.org.ru/wow/Cursor.rar) to the wow_directory/Interface (wow_directory/Interface/Cursor/Point.blp) - it will hide WoW internal cursor. 



Has this file changed or something? I just downloaded it, placed it in the folder and the cursor's still there, maybe they changed it with patch 3.1 as it was fine until I installed it this morning. :(

Edit: Nevermind, scrap this, it's the client that's changed, not this. :P

---

### Post by kronostm on 2009-04-16
having the same problem, as of patch 3.1 Point.blp seems to be useless.

Anyone with a workaround?

---

### Post by f2ip on 2009-04-17
3.1 seems to have broken the no cursor patch that's posted here. I'm going to try to make my own but I need to read up on how to make a custom cursor first. =)

After some reading I have found out that all custom cursors have been affected. I haven't ran across anyone with knowledge of how or why but I'll keep my fingers crossed. Maybe some digging around with the add-on dev kit will reveal some answers.

---

### Post by Xpander69 on 2009-04-17
patch works fine
but just cant hide wow cursor anymore :(
if anyone know how to do that, pls post here.
its pretty annoying to play now
all worked so good before 3.1

btw strange thing, when u run wow in d3d mode then cursor is hidden with that cursor file
but in opengl not...strange isnt it?

---

### Post by f2ip on 2009-04-17
hrmmm... that is strange. Unfortunately I can't duplicate your findings due to d3d not working for me under Linux at all (game locks up immediately). When I boot Windows, which uses directX of course, custom mouse pointers don't work for me there either.

---

### Post by Xpander69 on 2009-04-18
u can start with d3d in linux, when u disable pixel shaders and vertex shaders in winecfg.

...still have to figure out how to hide the damn laggy mouse in opengl:S


Edit: checked again. now its really odd what i found, in d3d mode, when hardware cursor is enabled ,then the Point.blp works, but when i disable hardware cursor then normal cursor is show again :(

---

### Post by Sezotove on 2009-04-19
So ive been trying to get this for a few hours now, and this is what i have done...
```

1) sudo apt-get install build-essential fakeroot devscripts
2) sudo apt-get build-dep wine
3) apt-get source wine
```

and then after i do that i try and use 

```
4) cd wine-1.whatever
```

But it does nothing, and ive changed the "1.whatever" to 1.1.19 and 1.1.14 and still this is what i get...

```
sezotove@sezotove-laptop:~$ cd wine-1.1.19
bash: cd: wine-1.1.19: No such file or directory
sezotove@sezotove-laptop:~$ 
```

```
sezotove@sezotove-laptop:~$ cd wine-1.1.14
bash: cd: wine-1.1.14: No such file or directory
sezotove@sezotove-laptop:~$ 
```

the only thing i can get is...
```
sezotove@sezotove-laptop:~/.wine$
```

which i fine, and i do the patching and this is what happens....

```
sezotove@sezotove-laptop:~/.wine$ patch -p1 < /home/sezotove/Desktop/winepatch.txt
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -Naur wine-1.1.14/dlls/winex11.drv/mouse.c wine-1.1.14-patched/dlls/winex11.drv/mouse.c
|--- wine-1.1.14/dlls/winex11.drv/mouse.c	2009-01-30 17:54:01.000000000 +0100
|+++ wine-1.1.14-patched/dlls/winex11.drv/mouse.c	2009-02-01 12:58:26.000000000 +0100
--------------------------
File to patch: 
```


So.... now i have NO IDEA what to do.
I wouldnt mind just dragging the file over, but i dont know where to put the file.
Another thing is that i dont know where the source was downloaded to. :( Help me please.

---

### Post by Xpander69 on 2009-04-19
1.1.19 compiles fine with the cursor patch.. just do:

sudo apt-get build-dep wine

download wine source from winehq.org

extract the source somewhere

open a terminal and drag the folder of ur wine source into it and write cd infront of it

f.e cd /home/myname/Desktop/wine1.1.19-source/

then write next

patch -p1 < /path/to/patch-file

./configure

make depend

make

sudo make install


works fine..
tho there is no use to use that curosor patch anymore, since wow 3.1 breaks the wow own cursor overwriting.

---

### Post by f2ip on 2009-04-20
sezotove, download the source from [http://prdownloads.sourceforge.net/wine/wine-1.1.19.tar.bz2](http://prdownloads.sourceforge.net/wine/wine-1.1.19.tar.bz2)
 and then extract it. once you you have the actual source folder you can apply the patch as has been described above.

---

### Post by cyclic on 2009-04-21
change the first 2 lines of the patch to this:

--- ./dlls/winex11.drv/mouse.c	2009-01-30 17:54:01.000000000 +0100
+++ ./dlls/winex11.drv/mouse.c	2009-02-17 16:20:12.000000000 +0100

then patch from the top level wine source directory.

cyclic

---

### Post by nsfnd on 2009-04-22
> **Xpander69 said:**
> patch works fine
but just cant hide wow cursor anymore :(
if anyone know how to do that, pls post here.
its pretty annoying to play now
all worked so good before 3.1

btw strange thing, when u run wow in d3d mode then cursor is hidden with that cursor file
but in opengl not...strange isnt it?

I thought they changed it back, i was running game in d3d without realizing.

---

### Post by dardack on 2009-04-25
I've been running in 3.1 and 3.1.1 and the cursor hiding still works for me.  Don't know why it's nto for you guys.

EDIT: Ok just upgarded to 9.04 Jaunty and now it doesn't work.  Sigh.

---

### Post by loklaan on 2009-05-02
Bump

Any progress?

---

### Post by dardack on 2009-05-02
> **BuNsiE said:**
> Bump

Any progress?

It's a blizzard issue.  A bunch of posts on the UI & Macro forums for WoW.  No official word from blizz yet if this was intended or a bug.  I have 2 posts i bump every day in UI and Bug forums.  Still no answer.

---

### Post by loklaan on 2009-05-02
Oh ok now I see, thanks. Damn Blizzard!

---

### Post by manulul on 2009-06-14
Thanks for this messages, they helped me a lot !

I recently installed Ubuntu 8.10 & Wine + WOW. Works fine with opengl except lag cursor, very unpleasant when you need to heal a 25 people raid ;)

I applied the patch on wine to makes the system cursor appears and it works very well. Thanks for this patch !

Nevertheless I see both WOW cursor & system cursor. I can play but the best would be if i could hide the wow cursor.

I'll continue to find an issue ;) We'll keep in touch ! ;)

---

### Post by SKLP on 2009-06-14
> **manulul said:**
> Thanks for this messages, they helped me a lot !

I recently installed Ubuntu 8.10 & Wine + WOW. Works fine with opengl except lag cursor, very unpleasant when you need to heal a 25 people raid ;)

I applied the patch on wine to makes the system cursor appears and it works very well. Thanks for this patch !

Nevertheless I see both WOW cursor & system cursor. I can play but the best would be if i could hide the wow cursor.

I'll continue to find an issue ;) We'll keep in touch ! ;)I'm glad you like the patch. We were able to hide the wow cursor before, but it seems a change in wow 3.1 made this impossible.

---

### Post by McAngel on 2009-06-18
Is this file "wine-cursor-patch-btn0and2.txt" the last good patch? Or there is another one?

---

### Post by SKLP on 2009-06-25
> **McAngel said:**
> Is this file "wine-cursor-patch-btn0and2.txt" the last good patch? Or there is another one?I don't know of any newer one, at least.

---

### Post by nskirov on 2009-07-12
Update: Works with 1.1.25

---

### Post by Doctor Debian on 2009-07-19
Updated for Karmic Koala 9.10:

NOTE: This tutorial is actively updated, and contains the latest information for patching. This post should be all you need to have a working hardware cursor.

Alright everyone, I've found a great, legal way to reimplement the cursor hiding for this patch AND keep the WoW cursor only inside of wine apps.

Firstly, install the required packages to build wine by typing

```
sudo apt-get build-dep wine1.2
```

Get the source of wine by typing

```
apt-get source wine1.2
```

When the source is retrieved, type

```
cd wine1.2-*
```

Proceed to download my patch by typing in

```
wget http://www.basixcomputer.com/wine-cursor-patch-new.txt
```

Install the patch with

```
patch -p1 < wine-cursor-patch-new.txt
```

If the patching has succeded, it should display a single line with the file it has patched.

Before installing, you must first change the version number to make sure it doesn't get overwritted. Edit the debian/changelog file, and change the "ubuntu(number)" in the first line to "ubuntu10".

Change into the previous directory (if you entered the changelog's directory), and build the package with

```
dpkg-buildpackage -uc -us -b
```

Now, wait a long time. When it's completed, type in

```
dpkg -i wine1.2_(wineversion)~ubuntu~(ubuntuversion)-0ubuntu10_(arch).deb
```

Or simply double click the package in that directory. Either way, it will overwrite the existing wine.

Then, you must copy the custom cursor file for use in wine. Download the file here

[http://www.basixcomputer.com/circle](http://www.basixcomputer.com/circle)

and save it into your current cursor directory (e.g /usr/share/icons/DMZ-White/cursors for gnome, /usr/share/icons/oxy-white/cursors for kde)

OPTIONAL STEP FOR GAUNTLET IN-GAME: (if you just want the normal cursor in game, don't do this)

Finally, download the MPQ here

[http://www.basixcomputer.com/patch-f.MPQ](http://www.basixcomputer.com/patch-f.MPQ)

and place it into your Data folder in your World of Warcraft folder. The patch is now installed!

To use the patch, change your World of Warcraft launcher to

```
env WINE_CURSOR=anything; wine (world of warcraft path)

```
Congratulations, enjoy your new cursor.

Andrew

Thanks to WowZym for parts of the tutorial, and Larsson for patch toggling!

---

### Post by loklaan on 2009-07-20
> **Doctor Debian said:**
> 
Then, download mpqedit at [http://www.zezula.net/download/mpqediten32.zip]("http://www.zezula.net/download/mpqediten32.zip") (has a platinum rating in wine)


Isn't editing wow's data files againt the eula?

---

### Post by Doctor Debian on 2009-07-20
> **BuNsiE said:**
> Isn't editing wow's data files againt the eula?

EDIT: Made it compliant with the TOS. Damn I'm fast.

Andrew

---

### Post by Xpander69 on 2009-07-20
works great thank you **Doctor Debian**

---

### Post by Doctor Debian on 2009-07-20
> **Xpander69 said:**
> works great thank you **Doctor Debian**

Glad to help :)

---

### Post by Xpander69 on 2009-07-20
noobish question :D

is it possible to make a command to call the local linux curosor in wine?.

with that i mean. f.e. this applys to all games, but shooters are real pain with the local linux cursor in middle of screen :)

would be nice to have a command to activate this patch.

maybe its impossible, dont know nothing about coding :popcorn:

---

### Post by Doctor Debian on 2009-07-20
> **Xpander69 said:**
> noobish question :D

is it possible to make a command to call the local linux curosor in wine?.

with that i mean. f.e. this applys to all games, but shooters are real pain with the local linux cursor in middle of screen :)

would be nice to have a command to activate this patch.

maybe its impossible, dont know nothing about coding :popcorn:

I don't believe that what you're saying is possible with this patch. Basically, the patch eliminates custom cursors/mouse grabbing and makes the cursor disappear when a button is pressed. If the patch is causing problems for yourself in other wine applications, try creating a second installation of wine (not just wineprefixes) for WoW. I'm not quite sure on how this is done however.

BTW, the patch is incredibly hack-ish and there's really not much control over it.

Andrew

---

### Post by Mmmbopdowedop on 2009-07-20
Thanks Doctor Debian, installed this this morning, much appreciated, works great. :)

Glad I don't have the laggy mouse following behind anymore. :)

---

### Post by Doctor Debian on 2009-07-20
Just added new functionality to keep the old WoW cursor when in WoW, while retaining the hardware functionality! Check my old post for install instructions. Would love if someone would test, as I'm not beside a working installation of WoW ATM.

Andrew

---

### Post by larsson on 2009-07-20
> **Xpander69 said:**
> noobish question :D

is it possible to make a command to call the local linux curosor in wine?.

with that i mean. f.e. this applys to all games, but shooters are real pain with the local linux cursor in middle of screen :)

would be nice to have a command to activate this patch.

maybe its impossible, dont know nothing about coding :popcorn:

Here you go.
it still is the wrong way of doing it in so many ways, i urge someone with knowledge of wine's(thread) inner workings to make this proper..

```
# just set the enviorment variable to anything.
export WINE_CURSOR=whatever
wine Wow.exe -opengl
```

```
# just don't have the enviorment variable set to anything.
unset WINE_CURSOR
wine MISE.exe
```


While i agree with Andrew that the patch is hack'ish, but lack of control? come on.

---

### Post by Doctor Debian on 2009-07-20
Alright, thanks :) going to implement this into my patch.

---

### Post by SKLP on 2009-07-21
Nice stuff! Although I don't play WoW atm, but it's good to see it still works :)
Anyways, a tip: It would be good if install guides used dpkg-buildpackage rather than make install directly... Really to build a clean copy of wine and install it cleanly all one has to do is (supposing you have winehq repository for both binary and source):
```

$ sudo apt-get install build-essential devscripts fakeroot
$ sudo apt-get build-dep wine
$ mkdir build
$ cd build
$ apt-get source wine
$ cd wine-*
$ dpkg-buildpackage -rfakeroot -us -uc -b
```
Now packages should exist in the build directory, which can be installed using sudo dpkg -i <deb-name>. Before the dpkg-buildpackage call, one can apply a patch, and I would also reccomend typing dch -i (which will allow you to modify the package version), bumping the version a bit is good if you have a patched program and don't want it to get replaced from a non-patched package from the repositories.
I'm just saying please dont write guides where you install programs in a non-debian way ;-)

Also, it might be good if [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) is updated with the latest patches and so on ;-) A lot more people will probably find it then. As thats first if you google for "wow ubuntu".

---

### Post by ipx on 2009-07-21
> **Doctor Debian said:**
> EDIT: Now with REAL wow cursor! You need to recompile wine with the modified patch and install the deb if you want it.

Alright everyone, I've found a great, legal way to reimplement the cursor hiding for this patch AND keep the WoW cursor only inside of wine apps.

First, download my custom cursor file [here]("http://www.basixcomputer.com/circle"). Copy that file into /usr/share/icons/DMZ-white/cursors/ . Overwrite the existing file. This will only work in WoW :) 

Proceed to download the latest wine source from winehq.org. Then, download my patch [here]("http://www.basixcomputer.com/wine-cursor-patch-new.txt"), and copy it into your wine source directory (e.g wine-1.1.26). To build dependencies, run
```
sudo apt-get build-dep wine
```
Proceed to execute the patch in the wine directory with 
```
patch -p1 < wine-cursor-patch-new.txt
```
then type in
```
./tools/wineinstall
```
to install wine. Wait a long time.

Then, download my custom MPQ file from [here]("http://www.basixcomputer.com/patch-f.MPQ"). Place it in your /home/user/.wine/drive_c/Program Files/World of Warcraft/Data directory.

Finally, when running WoW, change your launcher to assign a value to WINECURSOR before starting it, e.g
env WINE_CURSOR=anything; wine /home/user/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Wow.exe -opengl

I know using a custom cursor set is a mess, and assigning the wow cursor to the circle was just ridiculous. But this is intended to be a temporary solution until Blizzard smartens up and implements a real opengl cursor.

**A note on legality with the TOS:** the TOS states that it is prohibited to modify existing MPQ files. By adding a new MPQ file, we can legally and easily implement the HW cursor.

What I'm working on next:
-World of warcraft native cursors with patch - DONE
-Patch "switching on and off" - DONE - Thanks a ton, larsson.

Andrew

Thank you sir! I've been waiting for this :)

---

### Post by Doctor Debian on 2009-07-21
> **SKLP said:**
> Nice stuff! Although I don't play WoW atm, but it's good to see it still works :)
Anyways, a tip: It would be good if install guides used dpkg-buildpackage rather than make install directly... Really to build a clean copy of wine and install it cleanly all one has to do is (supposing you have winehq repository for both binary and source):
```

$ sudo apt-get install build-essential devscripts fakeroot
$ sudo apt-get build-dep wine
$ mkdir build
$ cd build
$ apt-get source wine
$ cd wine-*
$ dpkg-buildpackage -rfakeroot -us -uc -b
```
Now packages should exist in the build directory, which can be installed using sudo dpkg -i <deb-name>. Before the dpkg-buildpackage call, one can apply a patch, and I would also reccomend typing dch -i (which will allow you to modify the package version), bumping the version a bit is good if you have a patched program and don't want it to get replaced from a non-patched package from the repositories.
I'm just saying please dont write guides where you install programs in a non-debian way ;-)

Also, it might be good if [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) is updated with the latest patches and so on ;-) A lot more people will probably find it then. As thats first if you google for "wow ubuntu".

Why not just use checkinstall? It's easier for newbies.

---

### Post by Tycho Quad on 2009-07-22
Will this patch switch to the appropriate cursor for each situation? for example, will it turn into a money bag when hovering over a lootable corpse, or a cog on something usable? Disabled versions of these?

---

### Post by Doctor Debian on 2009-07-22
> **Tycho Quad said:**
> Will this patch switch to the appropriate cursor for each situation? for example, will it turn into a money bag when hovering over a lootable corpse, or a cog on something usable? Disabled versions of these?

Essentially, it will appear below the glove upon hovering over an action. It's very usable.

Andrew

---

### Post by Jor_727 on 2009-07-24
Ehmm.. I'm completely new to doing this, and if somebody could please give me some step-by-step instructions on how to patch WoW that would be great!  I really need the cursor to stop lagging...
Thanks!

---

### Post by Doctor Debian on 2009-07-24
> **Jor_727 said:**
> Ehmm.. I'm completely new to doing this, and if somebody could please give me some step-by-step instructions on how to patch WoW that would be great!  I really need the cursor to stop lagging...
Thanks!

What part are you stuck on? BTW, you don't patch wow, you patch wine.

Andrew

---

### Post by BOYerchen on 2009-07-24
Thanks a lot for your work. Still compiling, but the idea sounds great. I hope you'll manage to completely "emulate" the hardware cursor.

I'm probably not the first one with this idea to come up, but is it possible to create a PPA with the latest version of wine with your patch applied?

---

### Post by Doctor Debian on 2009-07-25
> **BOYerchen said:**
> Thanks a lot for your work. Still compiling, but the idea sounds great. I hope you'll manage to completely "emulate" the hardware cursor.

I'm probably not the first one with this idea to come up, but is it possible to create a PPA with the latest version of wine with your patch applied?

I was working on it, but I haven't had much time to work on the patch due to real life concerns and raiding. But yes, I believe creating a PPA is a great idea, and will probably do it in the near future :)

Andrew

---

### Post by Jor_727 on 2009-07-27
I'm stuck actually patching Wine.  I have Wine correctly installed, WoW currently running, although I'm not quite sure what to do...  Do I place the patch in my Wine folder?  Do I execute it?  Do I do both?  If I place it in a folder, what one is it?

---

### Post by Doctor Debian on 2009-07-27
> **Jor_727 said:**
> I'm stuck actually patching Wine.  I have Wine correctly installed, WoW currently running, although I'm not quite sure what to do...  Do I place the patch in my Wine folder?  Do I execute it?  Do I do both?  If I place it in a folder, what one is it?

You can download the latest wine source here:

[http://www.winehq.org/](http://www.winehq.org/)

by clicking on the Development: 1.1.26 (or something) link, and downloading the tar file. Extract that tar file to your home folder (or any other location, just easier for this tutorial).

Open up a terminal and type in:

```
cd wine-1.1.(version number you downloaded)
```

Proceed to execute

```
wget http://www.basixcomputer.com/wine-cursor-patch-new.txt
```

and then type in

```
patch -p1 < wine-cursor-patch-new.txt
```

Before installing, make sure your existing wine install is removed by typing

```
sudo apt-get remove wine
```

This will not remove your WoW installation.

Install the version of wine using

```
./tools/wineinstall
```

And enter your password when it tells you to. Wait a long while.

Then, just follow the rest of my tutorial for custom cursor patching. Have fun!

Andrew

---

### Post by dardack on 2009-07-28
I'll have to go try this when I get home tonite.  But my question is, can I use your MPQ without your custom cursor file.  I like the current cursor that Ubuntu uses that shows in WoW, instead of the hand (well now the hand shows up because of the stupid blocking custom cursors).  

Also I can just run env WINE_CURSOR=xxx; wine.... 

and that will work, i actually don't have to set the WiNE_CURSOR to anything?

---

### Post by sunfire on 2009-07-28
"How to OpenGL hw cursor PATCH" [http://ubuntuforums.org/showpost.php?p=7643957&postcount=82](http://ubuntuforums.org/showpost.php?p=7643957&postcount=82)
is working great, expect Im seeing my Kubuntu desktop-cursor on WoW now, not "hand" anymore. Is there something that I may done wrong on installing / patching wine ? 

My WoW launcher is like this:

LC_CTYPE="fi.FI-iso-8859-15" env WINE_CURSOR=anything; wine "/media/disk/World of Warcraft/Wow.exe"

---

### Post by Jor_727 on 2009-07-28
Thanks Doctor, your instructions worked perfectly!

---

### Post by Doctor Debian on 2009-07-28
> **dardack said:**
> I'll have to go try this when I get home tonite.  But my question is, can I use your MPQ without your custom cursor file.  I like the current cursor that Ubuntu uses that shows in WoW, instead of the hand (well now the hand shows up because of the stupid blocking custom cursors).  

Also I can just run env WINE_CURSOR=xxx; wine.... 

and that will work, i actually don't have to set the WiNE_CURSOR to anything?

If you desire to keep your Ubuntu cursor, just remove the cursor file you patched in the first step. You still must set the WINE_CURSOR variable to something.

Andrew

---

### Post by Doctor Debian on 2009-07-28
> **sunfire said:**
> "How to OpenGL hw cursor PATCH" [http://ubuntuforums.org/showpost.php?p=7643957&postcount=82](http://ubuntuforums.org/showpost.php?p=7643957&postcount=82)
is working great, expect Im seeing my Kubuntu desktop-cursor on WoW now, not "hand" anymore. Is there something that I may done wrong on installing / patching wine ? 

My WoW launcher is like this:

LC_CTYPE="fi.FI-iso-8859-15" env WINE_CURSOR=anything; wine "/media/disk/World of Warcraft/Wow.exe"

Did you follow the first step and replace the "circle" cursor file? That is what is required to use the Wow cursor.

Andrew

(Sorry for double posting!) :)

---

### Post by sunfire on 2009-07-29
> **Doctor Debian said:**
> Did you follow the first step and replace the "circle" cursor file? That is what is required to use the Wow cursor.

Andrew

(Sorry for double posting!) :)

Yes I did. Actually there is no cursor at all when starting game first time, but after alt-tab and back to wow this Kubuntu desktop-cursors starts showing and working.


Can it matter if I have replace circle with your circle after installing wine ? Im sure that I did it before installing but now I have done it couple times again. Maybe I should do all it again..


EDIT: _I logged to my gnome side. There cursor is working perfectly._ I think there is something with my mouse "theme" preferences on KDE side that will not work with patch. I will try find way to get this working on KDE side too. 


Great job Doctor Debian. Thanks a lot :)

---

### Post by dardack on 2009-07-29
> **Doctor Debian said:**
> If you desire to keep your Ubuntu cursor, just remove the cursor file you patched in the first step. You still must set the WINE_CURSOR variable to something.

Andrew

Yea Didn't need to prolly cause i use a different profile for my cursors or soemthing.  Once I added your mpq file the blizz software cursor disappeared, very nice.  

I would use d3d but wow keeps crashing in d3d for me.  But it runs really smooth in d3d in 1.1.26 now.

---

### Post by Doctor Debian on 2009-07-29
> **sunfire said:**
> Yes I did. Actually there is no cursor at all when starting game first time, but after alt-tab and back to wow this Kubuntu desktop-cursors starts showing and working.


Can it matter if I have replace circle with your circle after installing wine ? Im sure that I did it before installing but now I have done it couple times again. Maybe I should do all it again..


EDIT: _I logged to my gnome side. There cursor is working perfectly._ I think there is something with my mouse "theme" preferences on KDE side that will not work with patch. I will try find way to get this working on KDE side too. 


Great job Doctor Debian. Thanks a lot :)

Great to hear you have it working optimally, but if you desire to use it in KDE, put the circle file in your Oxygen cursor directory :) (wherever that may be, I don't use KDE anymore)

Andrew

---

### Post by kylev on 2009-08-14
i followed the instructions, and my cursor has disappeared, i also notice when running wow from a terminal i get a message :   Unable to read extra attributes: "Data\patch-f.MPQ"

any ideas??    i also did this with wine version  wine-1.1.27   could that be it as well,  im stumped.

---

### Post by kylev on 2009-08-14
also now i cant remove wine, using apt-get  to possibly try the steps again,  any help would be great thanks.

---

### Post by Doctor Debian on 2009-08-15
> **kylev said:**
> also now i cant remove wine, using apt-get  to possibly try the steps again,  any help would be great thanks.

If you wish to remove wine, enter your wine build directory (the directory you compiled wine in, e.g wine-1.1.27) and type in

```
sudo make uninstall
```

If you have deleted your source directory, you may manually delete all wine-related binaries in /usr/local/bin.

EDIT: Looks like the patching went wrong during installation. Did you apply the patch with "patch -p1 < patch-name.txt" or "patch -p1 > patch-name.txt"? A common mistake, the first one however is the correct one.

Andrew

---

### Post by gvoima on 2009-08-24
The patch seems to work nice, the cursor is not lagging anymore. But I noticed that you fixed the "on off" thing that you posted? I guess that means the flicking of the cursor.

> What I'm working on next:
-World of warcraft native cursors with patch - DONE
-Patch "switching on and off" - DONE - Thanks a ton, larsson.

I followed the instructions to the letter and the cursor disappears when I don't move the mouse :)
Did you add those changes to the patch that is given in the url below?

I used the links you posted for the cursor files [www.basixcomputer.com/xxx](www.basixcomputer.com/xxx) etc.


oh..and I'm using 1.1.28 dev wine and 8.04 ubuntu with WoW patch 3.2.0a and nvidia 185.18.36 drivers.

oh (again)..when I start it from terminal, it gives an error "Unable to read extra attributes: "Data\patch-f.MPQ""

---

### Post by Doctor Debian on 2009-08-24
> **gvoima said:**
> The patch seems to work nice, the cursor is not lagging anymore. But I noticed that you fixed the "on off" thing that you posted? I guess that means the flicking of the cursor.



I followed the instructions to the letter and the cursor disappears when I don't move the mouse :)
Did you add those changes to the patch that is given in the url below?

I used the links you posted for the cursor files [www.basixcomputer.com/xxx](www.basixcomputer.com/xxx) etc.


oh..and I'm using 1.1.28 dev wine and 8.04 ubuntu with WoW patch 3.2.0a and nvidia 185.18.36 drivers.

Cursor toggling (turning on and off) means only using the patch for Wow and not other wine applications.

The cursor should disappear when you left and right click. This simulates the function of the real hardware cursor.

The on and off patch IS part of the existing post. I've adapted other peoples' suggestions and code into the original post. You should only need to follow the instructions on page 9 :)

EDIT:
About the Patch-f.mpq message- even with it, do you still see the cursor? I don't have an active WoW installation nearby.

Andrew

---

### Post by WowZym on 2009-08-25
Hi there,

I did some testing yesterday on Kubuntu 9.04. Compiled wine 1.1.28 using the Source debs from wineHQ. The patch applies without problems. 

Be sure to have this in your package list (/etc/apt/sources.list):
[FONT=Courier New]deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
[/FONT] 
I followed the command to retrieve all build deps for wine. But I had to install another dev package before the Wine sources would build. I did first[INDENT][FONT=Courier New]sudo apt-get build-dep wine[/FONT]
[/INDENT]then:[INDENT][FONT=Courier New]sudo apt-get install ibgsm1-dev[/FONT]
[/INDENT]Then get the wine sources. I usually compile stuff in /usr/local/src. Get the sources with:[INDENT][FONT=Courier New]apt-get source wine
[/FONT][/INDENT]You will have a directory **wine-1.1.28~winehq0~ubuntu~9.04**.[INDENT][FONT=Courier New]cd wine-1.1.28~winehq0~ubuntu~9.04[/FONT][/INDENT]Then patch the sources:[INDENT][FONT=Courier New]patch -p1 < ../wine-cursor-patch-new.txt[/FONT]
[/INDENT]Now the packages can be build, but to make the package have a different patch number then the usual wineHQ ones we need to edit the debian/changelog file and increase the patch number. If you check that file then you see at the top:
[INDENT][FONT=Courier New]wine (1.1.28~winehq0~ubuntu~9.04-0ubuntu**1**) jaunty; urgency=low[/FONT]
[/INDENT]I changed it into:[INDENT][FONT=Courier New]wine (1.1.28~winehq0~ubuntu~9.04-0ubuntu**10**) jaunty; urgency=low[/FONT]
[/INDENT]So if an updates is done by the winehq guys, it will not directly overwrite the patched Wine we created ourselves.

Now build the whole lot using:[INDENT][FONT=Courier New]dpkg-buildpackage -uc -us -b[/FONT]
[/INDENT]Get yourself some coffee, tea or something else.. This takes some time. I started Wow using the 'normal' wine and did some leveling until it was done. When it is done you can install the freshly build package as usual in Ubuntu using your filemanager or on the commandline. I did:[INDENT][FONT=Courier New]dpkg -i wine_1.1.28~winehq0~ubuntu~9.04-0ubuntu10_i386.deb[/FONT]
[/INDENT]This will automatically update your old wine.

I copied the patched **circle** file in */usr/share/icons/oxy-white/cursors/circle* as I am using Kubuntu.

Now you can run Wow with the hacked hardware cursor using:

[INDENT][FONT=Courier New]export WINE_CURSOR=anything; wine <path to WoW>/Wow.exe -opengl[/FONT]
[/INDENT]
Or if you are using playonlinux then issue the export on the command prompt only and then run playonlinux. Like:
[INDENT][FONT=Courier New]export WINE_CURSOR=anything; playonlinux[/FONT]
[/INDENT]Remeber that you need to run Wow using the System wine then instead of the wine installed by playonlinux.

Have fun with it. Thanks Andrew for your work.

---

### Post by gvoima on 2009-08-25
> **Doctor Debian said:**
> Cursor toggling (turning on and off) means only using the patch for Wow and not other wine applications.

The cursor should disappear when you left and right click. This simulates the function of the real hardware cursor.

The on and off patch IS part of the existing post. I've adapted other peoples' suggestions and code into the original post. You should only need to follow the instructions on page 9 :)

EDIT:
About the Patch-f.mpq message- even with it, do you still see the cursor? I don't have an active WoW installation nearby.

ANOTHER EDIT:
Looks like changes in wine 1.1.28 have prevented the patch from running. For now, I recommend using wine 1.1.27, my last tested version.

Andrew

I can see the cursor when I move the mouse, but it flicks. And when I stop the mouse the cursor disappears.

ok thanks, i'll test wine 1.1.27.

UPDATE:
nope, didn't help to use 1.1.27
i'll continue my efforst some other time, now i have to go :(

---

### Post by Doctor Debian on 2009-08-25
Hello there WowZym;

Great to know that the patch works well with wine 1.1.28. When using the source wine from winehq, a few hunks failed. Odd.

As my skills as a tutorial builder are notoriously low, do you mind if I incorporate the debian packaging part into my tutorial? I couldn't find a way to explain it as simple as you did :)

EDIT: Updated original post.

Andrew

---

### Post by Rinaldus on 2009-08-25
Will I not get ban from Blizz for this hack? I called to their technical support and they said that I can do with my Wine whatever I want, but using custom MPQ in this hack... I'm afraid to get ban for it.

---

### Post by WowZym on 2009-08-26
Doctor Debian, please use my post for your instructions. I see you already did. I hope people benefit from it. I will see if I can find a place to upload my created patched wine version.

---

### Post by Doctor Debian on 2009-08-26
Done :)

i386 (32 bit)

[http://www.basixcomputer.com/wine_1.1.28~winehq0~ubuntu~9.04-0ubuntu1_i386.deb](http://www.basixcomputer.com/wine_1.1.28~winehq0~ubuntu~9.04-0ubuntu1_i386.deb)

AMD64 (64 bit)

[http://www.basixcomputer.com/wine_1.1.28~winehq0~ubuntu~9.04-0ubuntu10_amd64.deb](http://www.basixcomputer.com/wine_1.1.28~winehq0~ubuntu~9.04-0ubuntu10_amd64.deb)

Andrew

---

### Post by Doctor Debian on 2009-08-27
> **Rinaldus said:**
> Will I not get ban from Blizz for this hack? I called to their technical support and they said that I can do with my Wine whatever I want, but using custom MPQ in this hack... I'm afraid to get ban for it.

You *shouldn't* get banned, as Warden (Blizzard's game modifications detector) does not actively scan interface files. If you wish, you can simply not add the MPQ and have the old, laggy cursor underneath the hardware cursor.

Andrew

---

### Post by edwford on 2009-09-09
When I run wine from the terminal, I get "unable to read extra attributes /data/patch-f.mpq" aswell. I'm pretty sure I've done everything according to your guide. Also is this

> Done

i386 (32 bit)

[http://www.basixcomputer.com/wine_1....untu1_i386.deb](http://www.basixcomputer.com/wine_1....untu1_i386.deb)

AMD64 (64 bit)

[http://www.basixcomputer.com/wine_1....tu10_amd64.deb](http://www.basixcomputer.com/wine_1....tu10_amd64.deb)

the wine installer with patch applied? Just to clarify. I tried using that too and to no avail. I can't quite figure it out. 

Also the ```
env WINE_CURSOR=anything
``` segment of the launcher command. Can you give an example of what "anything" should be set to if it is not meant to be as shown above. 

I get the feeling I'm making the simplest mistake somewhere. I'm not a linux expert by any means, but have a basic understanding, and generally if there's a tutorial, I can get it to work if it doesn't right away, but I'm stumped. Thanks.

---

### Post by Doctor Debian on 2009-09-11
> **edwford said:**
> When I run wine from the terminal, I get "unable to read extra attributes /data/patch-f.mpq" aswell. I'm pretty sure I've done everything according to your guide. Also is this



the wine installer with patch applied? Just to clarify. I tried using that too and to no avail. I can't quite figure it out. 

Also the ```
env WINE_CURSOR=anything
``` segment of the launcher command. Can you give an example of what "anything" should be set to if it is not meant to be as shown above. 

I get the feeling I'm making the simplest mistake somewhere. I'm not a linux expert by any means, but have a basic understanding, and generally if there's a tutorial, I can get it to work if it doesn't right away, but I'm stumped. Thanks.

Anything is ANYTHING. You just need to assign any value to the string. Try just keeping it the way it is.

Andrew

---

### Post by cptalpha on 2009-09-14
This works out for me, i followed all your instructions and i got a hardware cursor now. Except the icon was all messed up, all i got was a white square with some randomly placed black dots in it.

I removed the patch-f.MPQ from WoW's DATA folder. The icon went back to the 'usual' hand icon and the cursor still behaves as a hardware cursor. Just thought i should mention this.

Thanks a lot !

---

### Post by Doctor Debian on 2009-09-15
> **cptalpha said:**
> This works out for me, i followed all your instructions and i got a hardware cursor now. Except the icon was all messed up, all i got was a white square with some randomly placed black dots in it.

I removed the patch-f.MPQ from WoW's DATA folder. The icon went back to the 'usual' hand icon and the cursor still behaves as a hardware cursor. Just thought i should mention this.

Thanks a lot !

In 3.2 it looks like Blizzard is blocking model editing functionality. There is another way to remove the underlying cursor, but it has a chance to render your data files invalid. For now, simply not using the custom MPQ option is the best option. Thanks for your input!

Andrew

---

### Post by Erestar on 2009-09-22
Seems like after the 3.2.2 patch my hardware cursor no longer appears. Doctor D, will you have a chance to most graciously lend your time to get this working with the new patch?

If not, can you suggest a means to revert to the stock cursor without having to recompile wine?

Thank you very much!

---

### Post by Erestar on 2009-09-22
> **Erestar said:**
> 

If not, can you suggest a means to revert to the stock cursor without having to recompile wine?



Answered my own question.

Turns out if you just move patch-f.mpq from your Data directory the normal cursor returns.

---

### Post by kszyh on 2009-09-24
Hi, do you have any idea why this is not working in World of Warcraft with patch 2.4.3 ?

I looked into console and see:
```
Unable to read extra attributes: "Data\patch-f.MPQ"
```

---

### Post by Doctor Debian on 2009-09-25
As I stated previously, there is no way to use the wow gauntlet any longer without violating the EULA and risking your account being banned. I have noted in the tutorial that installing the patch-f.MPQ file is optional.

Andrew

---

### Post by Ramjke on 2009-09-27
I did all the instructions and I have earned the hardware cursor: instead of hand-cursor on the screen running the standard cursor ubuntu. The problem is this: when I pinched the left or right mouse button, the cursor does not disappear, but moves in the middle of the screen and twitch there when I try to turn your character.

---

### Post by sunfire on 2009-09-28
Anyone tested this with Wine 1.1.30 yet ?


Cursors is working perfect in Gnome with wine 1.1.29 and OK with KDE-side.( Wine uses Onxygen cursor some weird reason. And yes, I have copied new cursors all oxygen and oxy folders. I have no idea why Im failing but im satisfied with the oxygen cursor in wow atm. )

---

### Post by Mmmbopdowedop on 2009-09-29
Hi, can you confirm if hiding the cursor works in 3.2 or is that what you meant when you said the `Gauntlet` doesn't work any longer`? :)

I've read your reply several times and maybe i'm failing, but I can't get an answer from it and it isn't working for me any longer after a format.

Please try to be clear in your reply, thanks in advance. :)

Sorry to directly seek an answer.

---

### Post by Xpander69 on 2009-09-30
yes wow original cursor hiding works in 3.2, with patch-f.mpq

too bad that i have to use wine 1.1.26 with that cursor patch, cuz all versions above this have bug that the cursor still remains in middle of screen when pressing buttons (not disapearing)

---

### Post by Zularan on 2009-10-15
Confirming this works with latest Wine 1.1.31 in Karmic 64b 9.10, followed Docs instructions patching Wine src and building it, no problems so far just tooling around in Dal.

This OpenGL hardware thing was the major obstacle playing the game, especially as a healer. Will keep you posted if anything breaks.

---

### Post by Zularan on 2009-10-16
Also thought I'd mention (slightly off this topic) if you're rebuilding Wine it's worthwhile doing this patch as well to fix the keyboard repeat issue:

[http://ubuntuforums.org/showthread.php?p=7467947#post7467947](http://ubuntuforums.org/showthread.php?p=7467947#post7467947)

Solves the issue with keyboard repeating while running (and means not having to disable keyboard repeating in gnome preferences), works fine so far with the latest versions posted in my last post above. 

I'm not sure how to merge patch files together (cursor and keyboard fix) and wasn't sure if it was just a matter of appending one to the other. But doing this at the patch part of the instructions in this cursor thread worked and I'm no longer running like an idiot when holding down 'W'.

---

### Post by Doctor Debian on 2009-10-27
> **Zularan said:**
> Also thought I'd mention (slightly off this topic) if you're rebuilding Wine it's worthwhile doing this patch as well to fix the keyboard repeat issue:

[http://ubuntuforums.org/showthread.php?p=7467947#post7467947](http://ubuntuforums.org/showthread.php?p=7467947#post7467947)

Solves the issue with keyboard repeating while running (and means not having to disable keyboard repeating in gnome preferences), works fine so far with the latest versions posted in my last post above. 

I'm not sure how to merge patch files together (cursor and keyboard fix) and wasn't sure if it was just a matter of appending one to the other. But doing this at the patch part of the instructions in this cursor thread worked and I'm no longer running like an idiot when holding down 'W'.

The repeat key issue was an issue in wine? I had thought it was the xserver, as it performed well before Jaunty.

---

### Post by Zularan on 2009-10-27
Jaunty and karmic have the repeat issue,  I'm not sure on previous releases. Disabling repeat in the xserver kind of fixed it as it disabled repeating altogether. Not all wine apps had the issue but wow does, and was only the forwadr key from what I recall. The wine patch from the other game thread seems to correct it.

Holding down 'w' made you run forward but seemed to spam stop-start so the animation has you skipping or something. Patching wine has it behaving as normal. I'm guessing it was a wine issue from what I read researching the problem. I'll try find the references when I get home as I'm fairly certain it was a change in wine not xserver. I could be wrong.

---

### Post by Kabaal on 2009-11-01
I used the patch and it all works great if I run it from a custom launcher. Problem is I want to run it with a bash script to avoid the annoying key-repeat bug.

My script looks like this:
```

#! /bin/bash

xset -r 25
xset -r 24
xset -r 39
xset -r 26

env WINE_CURSOR=anything; wine "C:\Program Files\World of Warcraft\Wow.exe"

echo "Reenabling auto repeat"
xset r 25
xset r 24
xset r 39
xset r 26

```

Using this doesnt work though, the game starts but I cant see my cursor (The hardware accelerated one). Any thoughts or solutions?

---

### Post by Zularan on 2009-11-02
> **Kabaal said:**
> I used the patch and it all works great if I run it from a custom launcher. Problem is I want to run it with a bash script to avoid the annoying key-repeat bug.

My script looks like this:
```

#! /bin/bash

xset -r 25
xset -r 24
xset -r 39
xset -r 26

env WINE_CURSOR=anything; wine "C:\Program Files\World of Warcraft\Wow.exe"

echo "Reenabling auto repeat"
xset r 25
xset r 24
xset r 39
xset r 26

```

Using this doesnt work though, the game starts but I cant see my cursor (The hardware accelerated one). Any thoughts or solutions?

Quick glance you still need to run WoW in OpenGL, try change this line of your script.
```
env WINE_CURSOR=anything; wine "C:\Program Files\World of Warcraft\Wow.exe -opengl"
```
also have the patch_f.mpq in your data directory for the cursor.

Hope this helps

also if you're okay with compiling wine, this additional patch fixed the repeat thing for me, do it straight after doing the cursor patch prior to compiling
[http://ubuntuforums.org/showpost.php?p=7467947&postcount=7](http://ubuntuforums.org/showpost.php?p=7467947&postcount=7)

---

### Post by SKLP on 2009-11-07
I just updated the WoW ubuntu howto ( [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ), one of the things i did was to provide a link to this thread. I also updated my front page post (in this thread) to provide a link to Doctor Debian's howto.

If you have time Doctor Debian, it might be better to include your howto in the main ubuntu wow howto? (Just an idea)

---

### Post by Doctor Debian on 2009-11-19
Thanks, I'll do it later this week when I have time.

Andrew

---

### Post by Joe Zero on 2009-11-22
Ok, I'm pretty new to Linux. I had been playing WoW on Ubuntu for some time, but decided to stick with Vista when I got my new laptop because of the mouse lag. I happened to see this thread and excitedly installed Mint 7.  And then ran into a snag.

I downloaded the source for Wine 1.1.33 and applied both of the aforementioned patches- but when I tried "dpkg-buildpackage -uc -us -b" I got the error, "dpkg-checkbuilddeps: failure: cannot read debian/control: No such file or directory"

And before that I had gotten a similar error but with debian/changelog instead. (so I installed Wine with Synaptic and got the changelog from usr/share/doc/wine and created the directory and used that...) but this control file I'm sure is important and should be done right.

So if the entire debian directory is missing from the wine-1.1.33.tar.bz2, where do I get it and can I somehow proceed without it? Or am I just missing something really obvious?


Thanks, 

Joe

---

### Post by SKLP on 2009-11-22
> **Joe Zero said:**
> Ok, I'm pretty new to Linux. I had been playing WoW on Ubuntu for some time, but decided to stick with Vista when I got my new laptop because of the mouse lag. I happened to see this thread and excitedly installed Mint 7.  And then ran into a snag.

I downloaded the source for Wine 1.1.33 and applied both of the aforementioned patches- but when I tried "dpkg-buildpackage -uc -us -b" I got the error, "dpkg-checkbuilddeps: failure: cannot read debian/control: No such file or directory"

And before that I had gotten a similar error but with debian/changelog instead. (so I installed Wine with Synaptic and got the changelog from usr/share/doc/wine and created the directory and used that...) but this control file I'm sure is important and should be done right.

So if the entire debian directory is missing from the wine-1.1.33.tar.bz2, where do I get it and can I somehow proceed without it? Or am I just missing something really obvious?


Thanks, 

JoeIt looks like you are using the wine tarball from winehq ;)
The debian directory is debian-specific (also applies to Ubuntu/Mint).
You can get the proper source using "apt-get source". 
Check out Doctor Debian's guide: [http://ubuntuforums.org/showpost.php?p=7643957&postcount=82](http://ubuntuforums.org/showpost.php?p=7643957&postcount=82) 

Good luck ;)

---

### Post by Joe Zero on 2009-11-23
Thank you for your reply, SKLP. I had tried to follow the Doctor's guide originally and ended up with 

```
joezero@X-A6920G ~ $ sudo apt-get build-dep wine1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list

```Which was when I got the tarball from winehq. So I did some more research, gave
 ```
sudo gedit /etc/apt/sources.list 
```a try. And un-commented all source repositories and just kept getting 

```
joezero@X-A6920G ~ $ sudo apt-get build-dep wine1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/packages.linuxmint.com_dists_gloria_main_source_Sources - open (2 No such file or directory)
```I re-commented everything I had just un-commented and tried adding
```
#deb-src http://wine.sourceforge.net/apt/ source/ 
``` to my sources.list and crossed my fingers.

Now I get 
```
joezero@X-A6920G ~ $ sudo apt-get build-dep wine1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for wine1.2

```instead.

I know my lack of basic Linux skills is what's really getting in the way, and while I'm learning alot I know I'm getting this thread off topic! My apologies.

...so if it would be too much of an ordeal to get 
```
sudo apt-get build-dep wine1.2
```working for me, is there just an alternative way for me to get the Debian source so that I might apply the patch?

Thanks again,

Joe

---

### Post by SKLP on 2009-11-24
It seems you did everything right except refresh APT after changing sources.list. 
```
sudo apt-get update
```

Good luck

And you don't need any special wine source repositories if you are running 9.10

---

### Post by goatgonads on 2009-11-29
Everything works fine here, in game I have the normal white pointer. My only problem is that when I click anything ingame, it shows the white cursor in the center of the screen until I let go of the mouse button. Any Ideas on how to fix this?

---

### Post by Makhno on 2009-12-02
Patch worked (at last)...
Thanks a lot Dr and all the people that participated. Really appreciate it.

---

### Post by awilkie on 2009-12-02
Hi,

New to the forums.  I have the wine-cursor-patch-new.txt in my .wine directory but when I try to use the command patch -p1 < wine-cursor-patch-new.txt, I get the following error:

If 'patch' is not a typo you can use command-not-found to lookup the package that contains it, like this:  cnf patch

What can I do to get around this?  Which file is the patch being added to and what portions of the code need to be inserted?

I'm using openSUSE 11.2 with wine 1.1.28

---

### Post by Iksf on 2009-12-06
> **goatgonads said:**
> Everything works fine here, in game I have the normal white pointer. My only problem is that when I click anything ingame, it shows the white cursor in the center of the screen until I let go of the mouse button. Any Ideas on how to fix this?

Got that too but dont really consider it a problem, for most left click actions it happens to fast to see. Right click is annoying but not majorly so. 

Also just another point, combine this with the pulseaudio wine version for getting 2 birds with 1 stone :D

---

### Post by loltim on 2009-12-19
hei, I follows this guide up to when I was going to typ in:
**patch -p1 < wine-cursor-patch-new.txt **
I get this out put then:
[B]can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- ./dlls/winex11.drv/mouse.c    2009-07-17 18:38:57.000000000 +0200
|+++ ./dlls/winex11.drv/mouse.c    2009-07-21 03:50:35.000000000 +0200
--------------------------
File to patch:[/B]
I don't know what to typ in :S tryed somethings with no succes... and the thing next to change the number after Ubuntu{number}, call me slow but I don't know were I change it, do u mean in the patch file ? 

Would really like to get this to work, have pretty bad fps in raids so having a less or none lagging mouse is love :D

---

### Post by Brebs on 2009-12-21
> **loltim said:**
> can't find file to patch at input line 3
|--- ./dlls/winex11.drv/mouse.c    2009-07-17 18:38:57.000000000 +0200

You need to run that command in the right directory in the source tree. The right directory is where this works:

ls dlls/winex11.drv/mouse.c

---

### Post by svev on 2009-12-24
Hey guys is this works also with wow 3.1.3??

---

### Post by Masaaki on 2009-12-28
Hey Doctor Debian, ([COLOR=Red][COLOR=Black]AND[/COLOR] ATTENTION KDE USERS[/COLOR])

It would be great if you can note in your tutorial on page one for KDE/Kubuntu users to launch WoW with:

```
**[COLOR=Red]export[/COLOR]** WINE_CURSOR=anything; wine (world of warcraft path)
```
(export is used *instead* of using [COLOR=Red]**env**[/COLOR])

If KDE users do not use export instead of env to set the variable, **the hardware cursor will not work!!**

Your instructions about copying to /usr/share/icons/oxy-white/cursor are correct.

Thanks for the great tutorial!

---

### Post by hisotaso on 2010-01-10
Well everything went fine for me until this step: 

```
dpkg -i wine1.2_(wineversion)~ubuntu~(ubuntuversion)-0ubuntu10_(arch).deb
```

I'm not sure what the data in parenthesis should be. I'm running wow from my windows partition, ubuntu 9.10 32, wine 1.1.8. So I need to know what to type in for (wineversion), (ubuntuversion), and (arch). Thanks in advance and thanks for all your hard work.
Oh I might add that it says I can also click on the package in that directory, but i see no package there. There are several scripts, but for fear of doing something wrong I was hesitant to just start trying them. One last thing, after getting stuck on this step, I figured I'd log in and do my dailes, but there was no cursor! I could see buttons being highlighted as if i was hovering over them when i moved the mouse around, but i cannot see a cursor. So i booted into windows and the same thing, no cursor. Any ideas on that front?

---

### Post by Rinaldus on 2010-01-12
I didn't understand is legal to add custom patch-f.MPQ?
> I've found a great, **legal** way to reimplement the cursor hiding for this patch AND keep the WoW cursor only inside of wine apps.
but you said later:
> As I stated previously, there is no way to use the wow gauntlet any longer without violating the EULA and risking your account being banned. I have noted in the tutorial that installing the patch-f.MPQ file is optional.
Without this patch-f.MPQ I see both in-game gaunlet and custom circle, it's not beautiful. With this file I see only circle, it's better.

---

### Post by Rinaldus on 2010-01-12
> **Rinaldus said:**
> 
Without this patch-f.MPQ I see both in-game gaunlet and custom circle, it's not beautiful.
The problem is solved. I made my own cursor with size 1x1 pixel and standart gaunlet cursor looks like now as gaunlet with smaaaaaaaalest dot on finger. And it's hardware! :) You don't need custom MPQ file now. :)

---

### Post by dmcfarland on 2010-01-18
I cannot apply the patch. This is the error msg I get. 

can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- ./dlls/winex11.drv/mouse.c    2009-07-17 18:38:57.000000000 +0200
|+++ ./dlls/winex11.drv/mouse.c    2009-07-21 03:50:35.000000000 +0200
--------------------------

---

### Post by Sayajin on 2010-01-20
Hi,

I am running SuSE 11.2, and wanted to get this "hack" working for me on wow, i downloaded wine 1.1.33 src, added the patch with "patch -p1 < wine-cursor-patch-new.txt", but since i couldnt use "dpkg-buildpackage -uc -us -b" i used the builder that comes with wine "./tools/wineinstall".

i have copied the circle cursor to the correct theme directories, yet when i open wow with opengl there is no "hardware" curser, just the software one.

i have trying using the export & env command and neither seem to be brining me joy.

any suggestions?
yes i know this is an ubuntu forum >.>

---

### Post by mikerhinos on 2010-01-22
Same problem here , Ubuntu 9.10 32bits , wine version 1.1.31

Patching :
```

    patching file dlls/winex11.drv/mouse.c
Hunk #3 succeeded at 945 (offset 2 lines).
Hunk #4 succeeded at 953 (offset 2 lines).
Hunk #5 succeeded at 963 (offset 2 lines).
Hunk #6 succeeded at 1058 (offset 2 lines).
Hunk #7 succeeded at 1100 (offset 2 lines).

```

Installing from .deb created in ../ directory
Absolutely no change with cursor :confused:

---

### Post by duscar on 2010-02-16
> **mikerhinos said:**
> Same problem here , Ubuntu 9.10 32bits , wine version 1.1.31

Patching :
```

    patching file dlls/winex11.drv/mouse.c
Hunk #3 succeeded at 945 (offset 2 lines).
Hunk #4 succeeded at 953 (offset 2 lines).
Hunk #5 succeeded at 963 (offset 2 lines).
Hunk #6 succeeded at 1058 (offset 2 lines).
Hunk #7 succeeded at 1100 (offset 2 lines).

```

Installing from .deb created in ../ directory
Absolutely no change with cursor :confused:

im also getting this, but going through with the installation seems to have fixed it. maybe a placebo effect? any idea if this means the patch failed or succeeded?

---

### Post by lacktorium on 2010-02-19
mine gives me an error in chunk 6 and wont build the package because of it. ubuntu 9.10 x64 wine 1.1.31 it errors out with
```

mouse.c: In function ‘X11DRV_ButtonPress’:
mouse.c:1095: error: redeclaration of ‘hwgl’ with no linkage
mouse.c:1093: note: previous declaration of ‘hwgl’ was here
make[3]: *** [mouse.o] Error 1
make[3]: Leaving directory `/home/lacktorium/wine1.2-1.1.31/dlls/winex11.drv'
make[2]: *** [winex11.drv] Error 2
make[2]: Leaving directory `/home/lacktorium/wine1.2-1.1.31/dlls'
make[1]: *** [dlls] Error 2
make[1]: Leaving directory `/home/lacktorium/wine1.2-1.1.31'
make: *** [build-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
```

edit: got wine 1.1.39 applies fine will post update if it works ingame

---

### Post by lacktorium on 2010-02-20
Whoo yes it works, not as good as D3d but playable. i had so much to say on how i got mine working i made a new thread here [http://ubuntuforums.org/....]("http://ubuntuforums.org/showthread.php?p=8854333#post8854333")

---

### Post by Alethenorio on 2010-02-20
Is there any way to test whether hardware cursor is working? I have compiled wine with the patch but I am uncertain whether it is working or not.

I noticed that the mouse still nearly freezes on the loading screen, does that mean it is not working?

Regards
Alex

---

### Post by ChrissyA on 2010-03-07
> Code:
 	dpkg -i wine1.2_(wineversion)~ubuntu~(ubuntuversion)-0ubuntu10_(arch).deb 
Or simply double click the package in that directory. Either way, it will overwrite the existing wine.

Ok, got to this part.. And then I get "cannot access archive: No such file or directory"
So I guess I am writing something wrong, could someone make and example or two on how it should be written? Fill in the forms so I can see how it's supposed to look, have a feeling I am doing some very stupid mistakes with ~ and other signs... 

I am such a noob that I couldn't find the package in the directory either... Print screen or spelling it out for dummies would be much appreciated!

;)

---

### Post by Iksf on 2010-03-19
Well for everyone who was having problems compiling this Iv run one up, this is Wine 1.1.31 compiled on Ubuntu Lucid. It uses the Pulseaudio wine branch, so byebye sound problems too. Hope this can help some of you

[http://www.mediafire.com/?mcm2wmnyrym]("http://www.mediafire.com/?mcm2wmnyrym")

---

### Post by inspiteofmyself on 2010-03-26
i have everything working as i want it to work (except for one issue). i compiled the current wine source from the ubuntu source package... everything went according to play. i am using the patch in this thread, and patches for winepulse. no issues compiling, everything works. the first time i ran i had no WoW cursor, and i could use the X hardware cursor in the game (the normal white pointer). it was awesome.

then i decided to try and use the circle cursor posted here, and now i get no cursor at all. moving the mouse will eventually highlight something on the login screen and i can login and guess which way to move to click things as needed, but this is really undesirable. the following command-line is what i used to test the custom X cursor:

```
env WINE_CURSOR=anything; wine "C:\World of Warcraft\Wow.exe" -opengl
```

the game runs, but i see no cursor at all now. i did copy the circle file to the appropriate cursor directory and i changed its permissions to match the permissions of the rest of the files in that folder. it is owned by root and the file is readable by users. i can open it in gimp just fine and see the gauntlet.

what am i missing here?

oh i failed to mention that if i tab out of the game, and then click the window to get back into it, the white cursor returns and i can see what im doing again. this happens regardless of whether i set WINE_CURSOR

---

### Post by concept08 on 2010-03-26
i have been doing lots of research on how to get FPS up in WOW

There is a few things that i have learned

you can use a command called nice to determine processing priority for WOW / Wine

Another thing that can be done is to change swappiness this will change the effect of the memory usage in conjunction with the swap file.

implementing these changes are not recommended for the person who does not understand them.

But the final thing that i have read and have not had a chance to test out as much as i would like to is this command 

metacity --replace

now it is reported that WOW runs better under wine when Compiz is disabled and metacity is used.

The problem with this is simply this. The cursor patch does not work when Compiz is disabled and wow is used under wine.

The patch works perfectly for me and always has. but not under metacity.

Some users have reported up to a 40% gain in frame rates and that would mean i would be at 30-40 FPS in Dalaran. compared to my 6-10.

my setup is old but its not that bad but its not that great compared to what is out there

Asus p4sda+ premium mother board
3 gigs memory 
3.6 ghz overclocked processor
cheetah 10000 rpm sata drives
a great NVIDIA graphics card (cant remember exact spec now)
Coolbits enabled and works great

and the patch makes it all playable.

The only thing that i have left to test out is launching Wine under its own X session. but i cannot get wine to boot with its own X session with WOW successfully.

So amongst this overflow of information does anyone have any idea why the Cursor patch does not work with metacity?

And thanks for this wonderful patch that you provided all of us. It has actually made game play a great deal better and more effective.
Thanks

---

### Post by inspiteofmyself on 2010-03-26
that could be my issue then. i have always disabled compiz and run metacity when doing anything with opengl acceleration. will test that out now and edit this post with the results.

** EDIT **
nope...still just got the white cursor. wow cursor (gauntlet in game) was hidden. the replacement x gauntlet is not activating when the game runs. oh well..id love to get this gauntlet to work :(

for no reason at all i just tried a new command-line for running WoW and it worked...this is so odd. lol

---

### Post by ronkkrop on 2010-04-08
This patch works great and i applaud your work.  However, is it possible to make it so that when you right or left click, the cursor disappears?  when i rightclick to turn, the cursor kind of jiggles around in the centre of my screen, it really is only a minor annoyance, but i'm pretty anal about stuff like that.  If it helps I used to have a patch for wine v1.1.16 that i found on a mailing list, maybe the code can be ninja'd? i don't know.

[http://archives.free.net.ph/message/20090306.024128.1846fb99.pt.html](http://archives.free.net.ph/message/20090306.024128.1846fb99.pt.html)

---

### Post by ronkkrop on 2010-04-09
> **ronkkrop said:**
> This patch works great and i applaud your work.  However, is it possible to make it so that when you right or left click, the cursor disappears?  when i rightclick to turn, the cursor kind of jiggles around in the centre of my screen, it really is only a minor annoyance, but i'm pretty anal about stuff like that.  If it helps I used to have a patch for wine v1.1.16 that i found on a mailing list, maybe the code can be ninja'd? i don't know.

[http://archives.free.net.ph/message/20090306.024128.1846fb99.pt.html](http://archives.free.net.ph/message/20090306.024128.1846fb99.pt.html)

I have managed to fix this problem myself.  If any of you are wanting the same functionality as what i mentioned above, navigate to your mouse.c find the function update_mouse_state, and then make the changes below...

```
static void update_mouse_state( HWND hwnd, Window window, int x, int y, unsigned int state, POINT *pt )
{
    struct x11drv_thread_data *data = x11drv_thread_data();
    char *hwgl;

    get_coords( hwnd, window, x, y, pt );
    hwgl = getenv("WINE_CURSOR");

    /* update the cursor */
    
    if (hwgl == NULL){
      if (data->cursor_window != window)
      {
        data->cursor_window = window;
        wine_tsx11_lock();
        if (data->cursor) XDefineCursor( data->display, window, data->cursor );
        wine_tsx11_unlock();
      }
    }
    
```

---

### Post by PelztierZwo on 2010-04-12
Hello!

First of all: Thank you all so much for everything. I followed the guides and I now have a properly working hardware cursor. I used my own "circle" file but that's not important I think.

The only thing that I wasn't able to do was to **"remove" or "disable" the original WoW cursor**. The patch-f.mpq file didn't help and I couldn't find any other way of hiding it.

Edit #1:
I patched a blank cursor instead of the normal pointer into locale-xxXX.MPQ but that's against the EULA, isn't it.

Edit #2:
Oh and thanks ronkkrop! Your little patch works very well. Although sometimes, when you press both mouse buttons almost simultaneously, the "jiggling" cursor in the middle of the screen does not disappear. And there is something else that's not quite right: When you press both mouse buttons and then release the right one the cursor dances in the screen center again. But now it's much better than before. I am grateful for your fix! :)

How did you do it? Is there a legal way? Can you help me, please? :)

I'm using Ubuntu 9.1 (x86) and WoW 3.3.3 (11723).

---

### Post by ronkkrop on 2010-04-13
> **PelztierZwo said:**
> Hello!

First of all: Thank you all so much for everything. I followed the guides and I now have a properly working hardware cursor. I used my own "circle" file but that's not important I think.

The only thing that I wasn't able to do was to **"remove" or "disable" the original WoW cursor**. The patch-f.mpq file didn't help and I couldn't find any other way of hiding it.

Edit #1:
I patched a blank cursor instead of the normal pointer into locale-xxXX.MPQ but that's against the EULA, isn't it.

Edit #2:
Oh and thanks ronkkrop! Your little patch works very well. Although sometimes, when you press both mouse buttons almost simultaneously, the "jiggling" cursor in the middle of the screen does not disappear. And there is something else that's not quite right: When you press both mouse buttons and then release the right one the cursor dances in the screen center again. But now it's much better than before. I am grateful for your fix! :)

How did you do it? Is there a legal way? Can you help me, please? :)

I'm using Ubuntu 9.1 (x86) and WoW 3.3.3 (11723).



Unfortunately there is no way to hide the wow cursor without violating the EULA since 3.1.  As for my fix listed above, i did test for the behaviour you spoke of and i was able to replicate it.  However, I don't think its possible to fix it without rewriting all of update_mouse_state checking for button clicks and changing the mouse pointer every time it's called, which would be quite frequent (and therefor quite laggy).

---

### Post by airtonix on 2010-04-13
you can change the cursor without touching wine source code by the way.

Just use a transparent texture.

---

### Post by ronkkrop on 2010-04-13
> **airtonix said:**
> you can change the cursor without touching wine source code by the way.

Just use a transparent texture.

Yes you can, but that's not the purpose of this patch.  This patch is to add hardware mouse functionality to WoW.  The changes to the wine source have nothing to do with removing the wow cursor(the mpq file does that).

---

### Post by n4h0j on 2010-04-14
> **ronkkrop said:**
> I have managed to fix this problem myself.  If any of you are wanting the same functionality as what i mentioned above, navigate to your mouse.c find the function update_mouse_state, and then make the changes below...

```
static void update_mouse_state( HWND hwnd, Window window, int x, int y, unsigned int state, POINT *pt )
{
    struct x11drv_thread_data *data = x11drv_thread_data();
    char *hwgl;

    get_coords( hwnd, window, x, y, pt );
    hwgl = getenv("WINE_CURSOR");

    /* update the cursor */
    
    if (hwgl == NULL){
      if (data->cursor_window != window)
      {
        data->cursor_window = window;
        wine_tsx11_lock();
        if (data->cursor) XDefineCursor( data->display, window, data->cursor );
        wine_tsx11_unlock();
      }
    }
    
```

Silly question: Where can I find this "mouse.c"? :)

---

### Post by PelztierZwo on 2010-04-14
> **n4h0j said:**
> Silly question: Where can I find this "mouse.c"?

Starting from the wine source dir, it's in **./dlls/winex11.drv**.

---

### Post by gurth4ng on 2010-05-01
Just checking…

The original post from **Doctor Debian** ([post #82]("http://ubuntuforums.org/showpost.php?p=7643957&postcount=82")) still applies for the latest WoW and Wine right?

I'm about to give it a go on Ubuntu 10.04.

---

### Post by PelztierZwo on 2010-05-01
> **gurth4ng said:**
> Just checking…

The original post from **Doctor Debian** ([post #82]("http://ubuntuforums.org/showpost.php?p=7643957&postcount=82")) still applies for the latest WoW and Wine right?

I'm about to give it a go on Ubuntu 10.04.

Yes, patching WINE (wine-1.1.42) still works (for me) on 9.10 with 3.3.3 (11723). I didn't do all this dpkg packaging stuff and just configured, made and installed it. I also wasn't able to change the version number to prevent accidental updates by apt (synaptic). But that's just because I'm new and unexperienced.

This post is a little easier to understand (at least for me): [http://bit.ly/aAFnD9](http://bit.ly/aAFnD9). I hope it can help you, too.

The only thing that doesn't work anymore is the patch-f.mpq file. You'll have to edit the locale-xxXX.MPQ in ./Data/xxXX directly which is against the TOS. Replacing the X11 cursor file just as Dr Debian says in his original post still works very well. I just removed the Pointer.blp and the Attack.blp (not sure if this is the correct name) from the MPQ and replaced it with the empty one which you can extract from the patch-f.MPQ file and you only see two cursors when you hover over a vendor etc.

Also don't forget to update ./dlls/winex11.drv/mouse.c with the awesome patch from n4h0j.

One other problem: When I did all this wine only supported OSS in the end. If this happens to you too and you want to wrap it to pulseaudio simply use padsp. The launcer then looks something like this: *Exec=env WINE_CURSOR=anything; env WINEPREFIX="/home/USERNAME/.wine" padsp wine "C:\\PATH\\TO\\WORLDOFWARCRAFT\\Wow.exe" -opengl*.

Long story short: Yes it still works on 9.10 but I have no idea about 10.04. Please post here when you have more info on 10.04. I'm very interested to see if it works or not. :)

---

### Post by gurth4ng on 2010-05-01
thanks a lot for your quick answer, you've been very helpful, I will give it a go later today or tomorrow and i will let you know how it goes :)

---

### Post by nirvy on 2010-05-01
> **PelztierZwo said:**
> Long story short: Yes it still works on 9.10 but I have no idea about 10.04. Please post here when you have more info on 10.04. I'm very interested to see if it works or not. :)

It works fine on ubuntu 10.04, too!

---

### Post by awilkie on 2010-05-02
When I get to the step where you enter

dpkg -i wine1.2_(wineversion)~ubuntu~(ubuntuversion)-0ubuntu10_(arch).deb
I receive an error telling me that '(' was an unexpected character.

Am I doing anything wrong?  I also can't seem to find a .deb file anywhere in the wine1.2* directory.

---

### Post by gurth4ng on 2010-05-03
> **awilkie said:**
> When I get to the step where you enter

dpkg -i wine1.2_(wineversion)~ubuntu~(ubuntuversion)-0ubuntu10_(arch).deb
I receive an error telling me that '(' was an unexpected character.

Am I doing anything wrong?  I also can't seem to find a .deb file anywhere in the wine1.2* directory.

you are meant to replace that with the version number of Wine you are using.

---

### Post by gurth4ng on 2010-05-03
> **PelztierZwo said:**
> Long story short: Yes it still works on 9.10 but I have no idea about 10.04. Please post here when you have more info on 10.04. I'm very interested to see if it works or not. :)

I'm afraid you attempts of trying to play World of Warcraft on Ubuntu 10.04 have come to a stall. My (rather old) computer uses AGP and i have an ATI Radeon x850, which doesnt work with WoW on OpenGL because of a known issue of the opensource driver.

I also have an ancient Nvidia GeForce FX 5200, and i was trying to get it to work with that, but It turns out that while the game will indeed start, the performance on either Ubuntu or Windows is very bad.

Bah :( So i'm stuck with playing WoW in Windows i guess :P

---

### Post by n4h0j on 2010-05-03
> **ronkkrop said:**
> I have managed to fix this problem myself.  If any of you are wanting the same functionality as what i mentioned above, navigate to your mouse.c find the function update_mouse_state, and then make the changes below...

```
static void update_mouse_state( HWND hwnd, Window window, int x, int y, unsigned int state, POINT *pt )
{
    struct x11drv_thread_data *data = x11drv_thread_data();
    char *hwgl;

    get_coords( hwnd, window, x, y, pt );
    hwgl = getenv("WINE_CURSOR");

    /* update the cursor */
    
    if (hwgl == NULL){
      if (data->cursor_window != window)
      {
        data->cursor_window = window;
        wine_tsx11_lock();
        if (data->cursor) XDefineCursor( data->display, window, data->cursor );
        wine_tsx11_unlock();
      }
    }
    
```

If anyone got to this page looking for a solution for how to solve this problem in Arch Linux. Then this might be of interest:

[http://bbs.archlinux.org/viewtopic.php?pid=752884#p752884](http://bbs.archlinux.org/viewtopic.php?pid=752884#p752884)

---

### Post by awilkie on 2010-05-04
> **gurth4ng said:**
>                                                       [SIZE=1]                     [/SIZE]>                  
                 [I][SIZE=1]When I get to the step where you  enter

dpkg -i  wine1.2_(wineversion)~ubuntu~(ubuntuversion)-0ubuntu10_(arch).deb[/SIZE] [SIZE=1]
I receive an error telling me that '(' was an unexpected character.

Am I doing anything wrong?  I also can't seem to find a .deb file  anywhere in the wine1.2* directory.[/SIZE][/I]
                                 
[SIZE=1]you are meant to replace that with the version number of Wine you  are using.[/SIZE][SIZE=1]

So, am I meant to type it like wine1.2_1.4blahblah?

Can you give me an example?

[/SIZE]

---

### Post by gurth4ng on 2010-05-04
> **awilkie said:**
> [SIZE=1]

So, am I meant to type it like wine1.2_1.4blahblah?

Can you give me an example?

[/SIZE]

I havent followed this tutorial so i might be missing something, but i assume that this command will do the trick:

dpkg -i wine1.2*.deb

tell me if it works :)

---

### Post by awilkie on 2010-05-04
Ok, so I tried that & got this response:

[INDENT]dpkg: error processing wine1.2*.deb (--install):
[/INDENT][INDENT] cannot access archive: No such file or directory
[/INDENT]
Also, when I do an ls in the wine1.2-1.1.42 folder, there are no .deb files.

---

### Post by randomei on 2010-05-10
**awilkie** try to do it in upper folder

---

### Post by randomei on 2010-05-10
> **Iksf said:**
> Well for everyone who was having problems compiling this Iv run one up, this is Wine 1.1.31 compiled on Ubuntu Lucid. It uses the Pulseaudio wine branch, so byebye sound problems too. Hope this can help some of you

To compile Pulseaudio wine branch:
```
sudo apt-get build-dep wine1.2
sudo apt-get install autoconf libtool bzr
```
Then in your home folder:
```
bzr branch lp:~ubuntu-wine/ubuntu/lucid/wine1.2/wine1.2+winepulse
```

Then **cd** to **wine1.2+winepulse** and continue with hw cursor patch:

> **Doctor Debian said:**
> Proceed to download my patch by typing in

```
wget http://www.basixcomputer.com/wine-cursor-patch-new.txt
```

Install the patch with

```
patch -p1 < wine-cursor-patch-new.txt
```

If the patching has succeded, it should display a single line with the file it has patched.

Before installing, you must first change the version number to make sure it doesn't get overwritted. Edit the debian/changelog file, and change the "ubuntu(number)" in the first line to "ubuntu10".

Change into the previous directory (if you entered the changelog's directory), and build the package with

```
dpkg-buildpackage -uc -us -b
```

Now, wait a long time. When it's completed, type in

```
dpkg -i wine1.2_(wineversion)~ubuntu~(ubuntuversion)-0ubuntu10_(arch).deb
```

Or simply double click the package in that directory. Either way, it will overwrite the existing wine.

Then, you must copy the custom cursor file for use in wine. Download the file here

[http://www.basixcomputer.com/circle](http://www.basixcomputer.com/circle)

and save it into your current cursor directory (e.g /usr/share/icons/DMZ-White/cursors for gnome, /usr/share/icons/oxy-white/cursors for kde)

Note that the compiled packages will be in your home folder.

You can also combine this with:

> **ronkkrop said:**
> I have managed to fix this problem myself.  If any of you are wanting the same functionality as what i mentioned above, navigate to your mouse.c find the function update_mouse_state, and then make the changes below...

```
static void update_mouse_state( HWND hwnd, Window window, int x, int y, unsigned int state, POINT *pt )
{
    struct x11drv_thread_data *data = x11drv_thread_data();
    char *hwgl;

    get_coords( hwnd, window, x, y, pt );
    hwgl = getenv("WINE_CURSOR");

    /* update the cursor */
    
    if (hwgl == NULL){
      if (data->cursor_window != window)
      {
        data->cursor_window = window;
        wine_tsx11_lock();
        if (data->cursor) XDefineCursor( data->display, window, data->cursor );
        wine_tsx11_unlock();
      }
    }
    
```

Tested on Lucid and works great!

---

### Post by WrenDarkcloud on 2010-05-10
OK did what [randomei]("http://ubuntuforums.org/member.php?u=952910") has posted above, but now when I start WoW, I am now getting this error.

```
wren@wrenlinux:~$ wine /home/wren/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000135

```

I have searched some info about it, but can't get it to work now. Here are my specs.

Processor        : 4x AMD Phenom(tm) II X4 965 Processor
Memory            : 2057MB (755MB used)
Operating System    : Ubuntu 10.04 LTS
OpenGL Renderer        : GeForce 9500 GT/PCI/SSE2 1GB

---

### Post by randomei on 2010-05-11
May be branch was not downloaded completly. Try to download and compile it again:
```
bzr branch lp:~ubuntu-wine/ubuntu/lucid/wine1.2/wine1.2+winepulse
cd wine1.2+winepulse
wget http://lightndarkness.com/files/wine-cursor-patch-new1.txt
patch -p1 -b < wine-cursor-patch-new1.txt
```
> **Doctor Debian said:**
> If the patching has succeded, it should display a single line with the file it has patched.

Before installing, you must first change the version number to make sure it doesn't get overwritted. Edit the debian/changelog file, and change the "ubuntu(number)" in the first line to "ubuntu10".

Change into the previous directory (if you entered the changelog's directory), and build the package with

```
dpkg-buildpackage -uc -us -b
```

Now, wait a long time. When it's completed

If there are any errors when patching or compiling, please post it.
Don't forget to change audio driver in winecfg to PulseAudio.

Start Wow with this command (from wow folder):

```
env WINE_CURSOR=1 nice -20 wine Wow.exe -opengl
```

---

### Post by WrenDarkcloud on 2010-05-11
Yeah. I redid everything again. Still getting that opengl32.dll error. Well worse case I can re-install the Software channel version of wine and play with d3d and the annoying white square, but I really liked opengl mode over it. A lot more stable. I will keep searching around to see if I can find an answer to the issue. Thank you for your reply :).

```
wren@wrenlinux:~/.wine/drive_c/Program Files/World of Warcraft$ env WINE_CURSOR=1 nice -20 wine Wow.exe -opengl
err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\Wow.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\Wow.exe" failed, status c0000135
```

---

### Post by randomei on 2010-05-11
Have you got any errors when patching and compiling?
What graphics card do you have?

---

### Post by WrenDarkcloud on 2010-05-11
Patch went on with no problems, compiling it came up with no errors either, other than a user defined name, I guess the author name, but that was ignored by the compiler. I am using a GeForce 9500 GT 1GB PCI-E x16 card, the video drivers are the ones that lucid comes with the 195.36.15 version. 

Also I checked the branch download, didn't see any errors there also. I will keep looking around for more info. But I think I did all the steps correctly.

Worse case I just re-install the older version for now to at least play the game.

Again thank you for your reply. :)

---

### Post by ronkkrop on 2010-05-11
I decided I wanted to make an actual patch file to include the work from the previous patch author, as well as include my changes from a few pages back(the jiggly mouse, page 18 ).  Before I did that however, I wanted to make sure the glitch where when you click both mouse buttons the desired functionality stops.  On top of this I currently have no access to my desktop because my Power supply died.   So... 

Included is an updated patch file **THAT HAS NOT BEEN TESTED.  PLEASE TEST IT,** and report the findings here.

copy the below attachment to your wine-1.1.xx folder, run:
```

patch -p1 < wow-hw-cursor-20100511.txt

```

---

### Post by vivnet on 2010-05-13
I had a modified version of the original wow cursor patch that was working perfectly in all cases.

However, wine 1.1.44 has made a large amount of changes to dlls/winex11.drv/mouse.c and it no longer applies or functions after I tried to implement an upgrade of it.

Has anyone seen a new patch designed for 1.1.44? Or has anyone managed to modify the existing patch to work with 1.1.44?

Note: the patch in the previous post is dated after the release of 1.1.44 but is built from mouse.c in 1.1.43.

---

### Post by svev on 2010-05-13
The Dr. Debian instructions need an update...;)

---

### Post by ronkkrop on 2010-05-15
> **vivnet said:**
> I had a modified version of the original wow cursor patch that was working perfectly in all cases.

However, wine 1.1.44 has made a large amount of changes to dlls/winex11.drv/mouse.c and it no longer applies or functions after I tried to implement an upgrade of it.

Has anyone seen a new patch designed for 1.1.44? Or has anyone managed to modify the existing patch to work with 1.1.44?

Note: the patch in the previous post is dated after the release of 1.1.44 but is built from mouse.c in 1.1.43.

Yes it is because the looking at the mouse.c source in 1.1.44, the changes I had made from a few pages back should no longer be necessary.

In answer to your request, I should get my computer operational this coming weekend at which time ill make a new patch to support 1.1.44 (if somebody else doesn't do it in the meantime.)  

NOTE: Just from a quick overview, the only changes in wine 1.1.44 that effect anything with this patch are made to update_mouse_state, and thus really shouldn't take very long to rewrite.

---

### Post by WrenDarkcloud on 2010-05-16
Ok. I was able to get it fixed apparently I had some old wine files in the /usr/local/bin folder. Cleared out any wine references. Redid randomei steps, now it works like a charm. Now in opengl with the mouse fix :)

FPS is pretty high now. 130 FPS now even in Dalaran. And pulseaudio is working perfect with it.

Just letting you know if you have the same issues make sure to check out the /usr/local/bin see if you have any rogue wine files there :).

---

### Post by mtzavarAS on 2010-05-17
Any update for the new wine and new Ubuntu??

Ty in advance

---

### Post by Sayajin on 2010-05-18
ye i installed the patch and added the .mpq file to wow data folder, but the software cursor is invisible...now im not sure if its me doing something wrong, or if its cause this patch was made for ubuntu 9.x, im using 10.04 32bit ubuntu.

---

### Post by vivnet on 2010-05-18
Sayajin, that is because you have not replaced the 'circle' cursor file.  Read the steps again and pay attention to that step.

The MPQ file is intended to hide the cursor.  I replaced the circle cursor provided with my desktop arrow cursor (just copy it and rename it to circle).

---

### Post by ErikHogue on 2010-05-20
I've tried going step by step with Randomei's steps and I always get stuck at trying to install the patch. When I enter the command "patch -pl < wine-cursor-patch-new.txt" it comes up with the following, what can I do? 
patching file dlls/winex11.drv/mouse.c
Hunk #1 FAILED at 175.
Hunk #2 FAILED at 185.
Hunk #3 FAILED at 943.
Hunk #4 FAILED at 951.
Hunk #5 FAILED at 961.
Hunk #6 FAILED at 1056.
Hunk #7 FAILED at 1098.
7 out of 7 hunks FAILED -- saving rejects to file dlls/winex11.drv/mouse.c.rej

---

### Post by vivnet on 2010-05-20
ErikHogue, though you didn't provide any information about the version of wine you're applying this to, I'm going to assume the version is 1.1.44.

The latest version this patch will apply to is 1.1.43.  Currently there has been no revised patch for 1.1.44 that I have been able to find.

---

### Post by ErikHogue on 2010-05-20
Yes, it is wine 1.1.44, I updated not long ago in hopes that it might make a difference. It helped with framerates, but obviously isn't helping with the mouse issue. 
If only Blizzard would just make an OpenGL cursor, this is such a ridiculous step.

---

### Post by mtzavarAS on 2010-05-21
I wonder if we could combine this script with an addon of WoW so the pointer could change to the rest of the pointers in WoW. Then we would have a real HW cursor . Damn i have no programing skills :(

---

### Post by mtzavarAS on 2010-05-21
Here is a list of the pointers that Wow uses in game

---

### Post by D4nilox on 2010-05-22
Use the Tutorial today ( 22 Mai / 2010) and works fine, Ubuntu 10.04 Wine 1.2.42

---

### Post by randomei on 2010-05-23
> **ErikHogue said:**
> I've tried going step by step with Randomei's steps and I always get stuck at trying to install the patch. When I enter the command "patch -pl < wine-cursor-patch-new.txt" it comes up with the following, what can I do? 
patching file dlls/winex11.drv/mouse.c
Hunk #1 FAILED at 175.
Hunk #2 FAILED at 185.
Hunk #3 FAILED at 943.
Hunk #4 FAILED at 951.
Hunk #5 FAILED at 961.
Hunk #6 FAILED at 1056.
Hunk #7 FAILED at 1098.
7 out of 7 hunks FAILED -- saving rejects to file dlls/winex11.drv/mouse.c.rej

Maybe you start patch in wrong folder?

---

### Post by dardack on 2010-05-23
I have come  up with a patch for 1.2-rc1, because of the changes to mouse.c in 1.2.

This is my first patch, but I've tested with 1.2-rc1 fresh extract and it works for me.  Please backup your mouse.c just in case.

DO NOT USE IF NOT USING wine 1.2-rc1 (and possibly any 1.2+), if using 1.1.*, please use old patch:

Please let me know if this works for anyone else, as I like to stay up on fresh wine sources, especially as we move to 1.2.

---

### Post by SamD42 on 2010-05-24
Just compiled and installed Wine 1.2-rc1 with your revised patch Dardak, works perfectly on my system, cheers!

---

### Post by dardack on 2010-05-24
> **SamD42 said:**
> Just compiled and installed Wine 1.2-rc1 with your revised patch Dardak, works perfectly on my system, cheers!

Glad to hear it.  I use this for all my wine compiles, cause I hate the windows/wine arrow and would rather have the default linux system arrow I have set up in my profile.

---

### Post by hallon on 2010-05-25
> **dardack said:**
> Glad to hear it.  I use this for all my wine compiles, cause I hate the windows/wine arrow and would rather have the default linux system arrow I have set up in my profile.

So did I and it works great :-) Nice to have normal cursor in Spotify! Keep up the good work! :guitar:

Maybe there's a way to incorporate pulse audio support too for 1.2-rc1 gonna look into it abit :biggrin:

---

### Post by dardack on 2010-05-25
> **hallon said:**
> So did I and it works great :-) Nice to have normal cursor in Spotify! Keep up the good work! :guitar:

Maybe there's a way to incorporate pulse audio support too for 1.2-rc1 gonna look into it abit :biggrin:

There is.  Check out winepulse:

[http://art.ified.ca/?page_id=40]("http://art.ified.ca/?page_id=40")

You have to compile wine yourself with these patches.  Um I believe all the audio/config files for Winepulse changed in 1.1.44 so there was no need to change it for 1.2rc1 like the mouse patch here.


You can read why they won't incorporate pulse into wine on that dudes page.  basically I found this cause WoW was having sound issues for me with my sound card in ALSA.  Be warned, the winepulse for ventrilo kinda sux, i always set a reg alsa for vent, reg pulse for wow, but now that mangler kicks *** I haven't used vent in forever.

If interested in Mangler (vent client for linux):

[www.mangler.org]("http://www.mangler.org")

EDIT:  BTW I wrote some code to TTS when someone enters a channel with their name/phonetic, cause I didn't just like a dinging sound, I wanted to know who entered the channel (in case I was talking about them).

---

### Post by hallon on 2010-05-25
> **dardack said:**
> There is.  Check out winepulse:

[http://art.ified.ca/?page_id=40]("http://art.ified.ca/?page_id=40")

You have to compile wine yourself with these patches.  Um I believe all the audio/config files for Winepulse changed in 1.1.44 so there was no need to change it for 1.2rc1 like the mouse patch here.


You can read why they won't incorporate pulse into wine on that dudes page.  basically I found this cause WoW was having sound issues for me with my sound card in ALSA.  Be warned, the winepulse for ventrilo kinda sux, i always set a reg alsa for vent, reg pulse for wow, but now that mangler kicks *** I haven't used vent in forever.

If interested in Mangler (vent client for linux):

[www.mangler.org]("http://www.mangler.org")

EDIT:  BTW I wrote some code to TTS when someone enters a channel with their name/phonetic, cause I didn't just like a dinging sound, I wanted to know who entered the channel (in case I was talking about them).

Thanks for the tip on Mangler. Already using it since a few days back and it absolutely kicks serious bum! :mrgreen:

I just read about pulseaudio on that page you linked.. so maybe not long till we get to use OpenAL with pulseaudio support. Sounds awsome, cant wait! :) 

..building a new package of wine now with pulseaudio patches and your mouse patch :) *fingers crossed* Currently using it with spotify and OSS emulation through padsp but I cant seem to play two OSS applications (both through wine) simultaneously using padsp. The sound quality seem much higher now though than with ALSA. Might be my imagination.. but I seem to have noticed a slight digital distortion previously.

.. still compiling :P

EDIT:
Hmm.. some errors with mp3 library and a bunch of struggles with pulseaudio ended with me ditching pulseaudio altogether. Happy user of just pure ALSA now, and amixer for keyboard volume control :) superb sound and no popping in Warcraft either. I wonder what I will miss pulseaudio for..

---

### Post by dardack on 2010-05-25
> **hallon said:**
> Thanks for the tip on Mangler. Already using it since a few days back and it absolutely kicks serious bum! :mrgreen:

I just read about pulseaudio on that page you linked.. so maybe not long till we get to use OpenAL with pulseaudio support. Sounds awsome, cant wait! :) 

..building a new package of wine now with pulseaudio patches and your mouse patch :) *fingers crossed* Currently using it with spotify and OSS emulation through padsp but I cant seem to play two OSS applications (both through wine) simultaneously using padsp. The sound quality seem much higher now though than with ALSA. Might be my imagination.. but I seem to have noticed a slight digital distortion previously.

.. still compiling :P

EDIT:
Hmm.. some errors with mp3 library and a bunch of struggles with pulseaudio ended with me ditching pulseaudio altogether. Happy user of just pure ALSA now, and amixer for keyboard volume control :) superb sound and no popping in Warcraft either. I wonder what I will miss pulseaudio for..


Are you on 64bit Ubuntu?  and did you do sudo build-dep wine?

---

### Post by hallon on 2010-05-26
> **dardack said:**
> Are you on 64bit Ubuntu?  and did you do sudo build-dep wine?

As it happens I actually am on 64-bit, Linux Mint 8(Ubuntu Karmic derivate)

First compile with just your patch went ok, then after doing the other patches for pulseaudio, I for some reason did ./configure (the instructions advised me to) and got some warnings about missing mp3 libraries, which I installed. Those libraries are the ones giving me errors now when doing dpkg-buildpackage -rfakeroot -us -uc -b

trying to find logfiles of the error but I think I was abit too quick deleting the folder and settling for a pulseaudio free environment. I'll give it another go later on today if you're interested in exactly what errors I got :)

---

### Post by dardack on 2010-05-26
> **hallon said:**
> As it happens I actually am on 64-bit, Linux Mint 8(Ubuntu Karmic derivate)

First compile with just your patch went ok, then after doing the other patches for pulseaudio, I for some reason did ./configure (the instructions advised me to) and got some warnings about missing mp3 libraries, which I installed. Those libraries are the ones giving me errors now when doing dpkg-buildpackage -rfakeroot -us -uc -b

trying to find logfiles of the error but I think I was abit too quick deleting the folder and settling for a pulseaudio free environment. I'll give it another go later on today if you're interested in exactly what errors I got :)

Yea there was a change you had to make in the audio for mp3, post the error I can remember what it was.  IIRC that is.  Also, you do need the dev libraries of pulse for winepulse IIRC also.

EDIT: Also after applying the pulse patches did you do the: autoreconf

---

### Post by Brebs on 2010-05-26
dardack's patch a few posts above, works great to reduce the annoying mouse lag in Thief 2 under wine. So, many thanks.

I've noted this on the [Mouse too slow / lags in games](http://bugs.winehq.org/show_bug.cgi?id=7640) wine bug.

---

### Post by hallon on 2010-05-26
> **dardack said:**
> Yea there was a change you had to make in the audio for mp3, post the error I can remember what it was.  IIRC that is.  Also, you do need the dev libraries of pulse for winepulse IIRC also.

EDIT: Also after applying the pulse patches did you do the: autoreconf

Yes I ran autoreconf as adviced.

I don't know how much you get from this error message but here goes. This is the end of the output from compiling:
```
make[2]: Leaving directory `/home/bobbo/winestuff2/wine1.2-1.2~rc1/dlls/winemapi'
make[2]: Entering directory `/home/bobbo/winestuff2/wine1.2-1.2~rc1/dlls/winemp3.acm'
x86_64-linux-gnu-gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wstrict-prototypes -Wtype-limits -Wwrite-strings -Wpointer-arith  -Wall -g -O2  -o mpegl3.o mpegl3.c
../../tools/winegcc/winegcc -m32 -B../../tools/winebuild --sysroot=../.. -fasynchronous-unwind-tables -shared ./winemp3.acm.spec mpegl3.o        -o winemp3.acm.so  -lwinmm -luser32 -lkernel32  ../../libs/port/libwine_port.a -lmpg123   
mpegl3.o: In function `MPEG3_Reset':
/home/bobbo/winestuff2/wine1.2-1.2~rc1/dlls/winemp3.acm/mpegl3.c:211: undefined reference to `mpg123_feedseek'
collect2: ld returned 1 exit status
winegcc: x86_64-linux-gnu-gcc failed
make[2]: *** [winemp3.acm.so] Error 2
make[2]: Leaving directory `/home/bobbo/winestuff2/wine1.2-1.2~rc1/dlls/winemp3.acm'
make[1]: *** [dlls/winemp3.acm] Error 2
make[1]: Leaving directory `/home/bobbo/winestuff2/wine1.2-1.2~rc1'
make: *** [build-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2

```

Interesting part seem to be this:
[I]mpegl3.o: In function `MPEG3_Reset':
/home/bobbo/winestuff2/wine1.2-1.2~rc1/dlls/winemp3.acm/mpegl3.c:211: undefined reference to `mpg123_feedseek'[/I]
Here's the code from the c-file
```

/***********************************************************************
 *           MPEG3_Reset
 *
 */
static void MPEG3_Reset(PACMDRVSTREAMINSTANCE adsi, AcmMpeg3Data* aad)
{
    mpg123_feedseek(aad->mh, 0, SEEK_SET, NULL);
    mpg123_close(aad->mh);
    mpg123_open_feed(aad->mh);
}
```

And the includes:
```

#include "config.h"
#include "wine/port.h"

#include <assert.h>
#include <stdarg.h>
#include <string.h>

#ifdef HAVE_MPG123_H
# include <mpg123.h>
#else
# ifdef HAVE_COREAUDIO_COREAUDIO_H
#  include <CoreFoundation/CoreFoundation.h>
#  include <CoreAudio/CoreAudio.h>
# endif
# ifdef HAVE_AUDIOTOOLBOX_AUDIOCONVERTER_H
#  include <AudioToolbox/AudioConverter.h>
# endif
# ifdef HAVE_AUDIOTOOLBOX_AUDIOFILE_H
#  include <AudioToolbox/AudioFile.h>
# endif
# ifdef HAVE_AUDIOTOOLBOX_AUDIOFILESTREAM_H
#  include <AudioToolbox/AudioFileStream.h>
# endif
#endif

#include "windef.h"
#include "winbase.h"
#include "wingdi.h"
#include "winuser.h"
#include "winnls.h"
#include "mmsystem.h"
#include "mmreg.h"
#include "msacm.h"
#include "msacmdrv.h"
#include "wine/debug.h"

```

maybe the function mpg123_feedseek is defined in mpg123.h, and that's where the change must be done? Maybe it would have failed on the rest of the functions called in MPEG3_Reset as well :)

EDIT:
Found a possible solution to the problem here [http://ubuntuforums.org/showthread.php?t=1299539](http://ubuntuforums.org/showthread.php?t=1299539)
Trying it now :)

---

### Post by vbundi on 2010-05-27
I've patched wine 1.1.42 and moved patch-f.mpq to my data folder.  My cursor is invisible now.  I am assuming my wow cursor is invisible and my X11 cursor just isn't showing up for some reason.  Am I missing a step?

---

### Post by ronkkrop on 2010-05-28
Well, I'm finally back from the dead, and here to give you all the most recent patch.  This patch is for wine1.2-rc1+.  Please note:  THIS PATCH HAS NOT BEEN EXTENSIVELY TESTED.  If you notice any strange behaviour, please post in this thread.

Benefits of this patch:
--changes all non-wow wine apps to use the x cursor (thanks dardak), wow still uses the gaunt.

--jiggly cursor is fixed: cursor will disappear when you right or left click so that when you look around, the cursor doesn't jiggle in the middle of the screen.



To install this patch:
```
patch -p1 < wine-hw-cursor-20100528.txt
```

If you've already compiled wine1.2-rc1+ and don't want to sit through a full compile again:
```

patch -p1 < wine-hw-cursor-20100528.txt
cd ./dlls/winex11.drv
make clean
make
sudo make install

```

---

### Post by vbundi on 2010-05-28
The Instructions below are meant to be a summary, and I take no credit.
I have tested the above patch by ronkkrop and it works great.

All commands are done as the user (not root)

1. Download 1.2-rc1+ sourcecode from Winehq [http://ibiblio.org/pub/linux/system/emulators/wine/wine-1.2-rc1.tar.bz2](http://ibiblio.org/pub/linux/system/emulators/wine/wine-1.2-rc1.tar.bz2)
2. Download ronkkrop's patch from above post.
patch -p1 < wine-hw-cursor-20100528.txt (from within wine-1.2-rc1)
3. ./configure && make && sudo checkinstall
4. wget [http://www.basixcomputer.com/circle](http://www.basixcomputer.com/circle)
5. mv circle /usr/share/icons/DMZ-White/cursors/
6. To start wow, use the command below substituting <USER> with your username
7. * OPTIONAL * Supposedly violates Bliz EULA
wget [http://www.basixcomputer.com/patch-f.MPQ](http://www.basixcomputer.com/patch-f.MPQ)
mv patch-f.MPQ to /home/<USER>/drive_c/Program\ Files/World\ of\Warcraft/Data/

***
env WINE_CURSOR=1 nice -20 wine /home/<USER>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -opengl
***

You can place that command in a bash script
vi wow.bsh

#!/bin/bash
<the above command>

(save)
chmod +x wow.bsh

You can now run wow by doing ./wow.bsh


I have compiz disabled
In winecfg under video, I have emulate a virtual desktop, and allow the window manager to control wine (bottom two checkboxes)

Working in Lucid i386 using Nvidia hardware.

Thanks to everyone that has helped.

---

### Post by svev on 2010-05-29
I have just done this but i can't see Wine in the application bar..what's wrong??:(

---

### Post by vbundi on 2010-06-01
If you followed my instructions, you won't have wine in your application menu.  I'm sure it can be added in though, maybe I just missed a step.

---

### Post by dardack on 2010-06-01
> **ronkkrop said:**
> Well, I'm finally back from the dead, and here to give you all the most recent patch.  This patch is for wine1.2-rc1+.  Please note:  THIS PATCH HAS NOT BEEN EXTENSIVELY TESTED.  If you notice any strange behaviour, please post in this thread.

Benefits of this patch:
--changes all non-wow wine apps to use the x cursor (thanks dardak), wow still uses the gaunt.

--jiggly cursor is fixed: cursor will disappear when you right or left click so that when you look around, the cursor doesn't jiggle in the middle of the screen.



To install this patch:
```
patch -p1 < wine-hw-cursor-20100528.txt
```

If you've already compiled wine1.2-rc1+ and don't want to sit through a full compile again:
```

patch -p1 < wine-hw-cursor-20100528.txt
cd ./dlls/winex11.drv
make clean
make
sudo make install

```


Glad I could help in some small way.  I've actually gotten used to the jiggly cursor and look for it, heh.

---

### Post by Ysam on 2010-06-06
Edit:

I followed the instructions on this page [http://ubuntuforums.org/showpost.php?p=7643957&postcount=82]("http://ubuntuforums.org/showpost.php?p=7643957&postcount=82") but when I enter the game, I dont see a cursor at all. It is there, I can see the menu items being lit when I accidentally hover over them.

Could someone help ? 

Thanks

---

### Post by ronkkrop on 2010-06-06
> **Ysam said:**
> Edit:

I followed the instructions on this page [http://ubuntuforums.org/showpost.php?p=7643957&postcount=82]("http://ubuntuforums.org/showpost.php?p=7643957&postcount=82") but when I enter the game, I dont see a cursor at all. It is there, I can see the menu items being lit when I accidentally hover over them.

Could someone help ? 

Thanks

did you follow this step:

Then, you must copy the custom cursor file for use in wine. Download the file here

[http://www.basixcomputer.com/circle](http://www.basixcomputer.com/circle)

and save it into your current cursor directory (e.g /usr/share/icons/DMZ-White/cursors for gnome, /usr/share/icons/oxy-white/cursors for kde)

---

### Post by Ysam on 2010-06-07
> **ronkkrop said:**
> did you follow this step:

Then, you must copy the custom cursor file for use in wine. Download the file here

[http://www.basixcomputer.com/circle](http://www.basixcomputer.com/circle)

and save it into your current cursor directory (e.g /usr/share/icons/DMZ-White/cursors for gnome, /usr/share/icons/oxy-white/cursors for kde)

I just did that step again to make sure I did it well, but the problem persists.

---

### Post by ronkkrop on 2010-06-07
> **Ysam said:**
> I just did that step again to make sure I did it well, but the problem persists.

If you have Compiz, disable it, then try changing the command line you use to EXACTLY this:

```
env WINE_CURSOR=123456; wine "C:\Program Files\World of Warcraft\Wow.exe -opengl"
```

or if using KDE(which is my suspicion):
```
export WINE_CURSOR=123456; wine "C:\Program Files\World of Warcraft\Wow.exe -opengl"
```

Let me know if you experience any change.

---

### Post by Ysam on 2010-06-07
> **ronkkrop said:**
> If you have Compiz, disable it, then try changing the command line you use to EXACTLY this:

```
env WINE_CURSOR=123456; wine "C:\Program Files\World of Warcraft\Wow.exe -opengl"
```

or if using KDE(which is my suspicion):
```
export WINE_CURSOR=123456; wine "C:\Program Files\World of Warcraft\Wow.exe -opengl"
```

Let me know if you experience any change.

I redid the entire procedure, used your commands and it solved my problem!

Even though I did not do the optional part of the instruction (to keep the gauntlet cursor ingame) I do see the usual gauntlet cursor, but it is as responsive as it should be. :D

Thanks a lot for your help.

---

### Post by laeg_ on 2010-06-07
I use Wine 1.2-rc2, do I need to edit your tutorial to account for this or...? Just I don't really understand what the tutorial does exactly at each step and whether or not it will replace my current version with an older one, and I'd like to keep 1.2-rc2 as it's vastly improved other games for me.

Also, as I've said I play other games - will the hardware hack affect them in any bad way?

---

### Post by ronkkrop on 2010-06-07
> **laeg_ said:**
> I use Wine 1.2-rc2, do I need to edit your tutorial to account for this or...? Just I don't really understand what the tutorial does exactly at each step and whether or not it will replace my current version with an older one, and I'd like to keep 1.2-rc2 as it's vastly improved other games for me.

Also, as I've said I play other games - will the hardware hack affect them in any bad way?

Download my patch from the previous page, follow the instructions on the following post.  I have not tested it in rc2 as the patch was made for rc1, but it should still work.

In the patch that I made, for applications that are not run with WINE_CURSOR variable it will change their cursor to use the X cursor.  If this is of concern to you, I'll tell you now that for the next minor rewrite, I intend to make that configurable via the WINE_CURSOR variable.

---

### Post by ronkkrop on 2010-06-08
I decided to make a new patch (compatible with 1.2-rc+) to address what I mentioned in the above post.  This patch is designed to address 3 modes of functionality.  Again,  **THIS PATCH HAS NOT BEEN EXTENSIVELY TESTED**, so if you notice any strange behaviour, please post your symptoms in this thread.

Modes of this patch:
-Allows X cursor inside Wine apps, including no jiggle when looking/moving around.
-Allows X cursor inside Wine apps, disabling the "no jiggle" feature.
-Allows gaunt cursor inside Wine apps, including no jiggle when looking/moving around.
-Default: No alteration whatsoever


How to install this patch:
```

1. Download and extract wine-1.2-rc2
2. Download my attachment and copy it to wine-1.2-rc2 root folder.
3. Run the following commands:
patch -p1 < wine-hw-cursor-20100608.txt
./configure
make
sudo make install

```


How to use this patch:
I decided to make the WINE_CURSOR environment variable more useful and is the source for the multiple modes of functionality.  Setting the environment variable to one of the following will have the indicated result.

X - Uses the X cursor with "no jiggle" DISABLED.
ex:
```

env WINE_CURSOR=X; wine "C:\Program Files\Ventrilo\Ventrilo.exe"         ....(for GNOME)

export WINE_CURSOR=X; wine "C:\Program Files\Ventrilo\Ventrilo.exe"         ....(for KDE)

```

XNOJIG - Uses the X cursor with "no jiggle" ENABLED.
ex:
```

env WINE_CURSOR=XNOJIG; wine "C:\Program Files\World of Warcraft\Wow.exe -opengl"       ....(for GNOME)

export WINE_CURSOR=XNOJIG; wine "C:\Program Files\World of Warcraft\Wow.exe -opengl"       ....(for KDE)

```

ANYTHING - Uses gaunt in game with "no jiggle" ENABLED.  (functions exactly as before, so no change should be necessary if you don't want it).
ex
```

env WINE_CURSOR=lkjlkjfd; wine "C:\Program Files\World of Warcraft\Wow.exe -opengl"       ....(for GNOME)

export WINE_CURSOR=lkjfmnkkf; wine "C:\Program Files\World of Warcraft\Wow.exe -opengl"       ....(for KDE)

```

---

### Post by hallon on 2010-06-12
> **ronkkrop said:**
> I decided to make a new patch (compatible with 1.2-rc+) to address what I mentioned in the above post.  This patch is designed to address 3 modes of functionality.  Again,  **THIS PATCH HAS NOT BEEN EXTENSIVELY TESTED**, so if you notice any strange behaviour, please post your symptoms in this thread.

Modes of this patch:
-Allows X cursor inside Wine apps, including no jiggle when looking/moving around.
-Allows X cursor inside Wine apps, disabling the "no jiggle" feature.
-Allows gaunt cursor inside Wine apps, including no jiggle when looking/moving around.
-Default: No alteration whatsoever


How to install this patch:
```

1. Download and extract wine-1.2-rc2
2. Download my attachment and copy it to wine-1.2-rc2 root folder.
3. Run the following commands:
patch -p1 < wine-hw-cursor-20100608.txt
./configure
make
sudo make install

```


How to use this patch:
I decided to make the WINE_CURSOR environment variable more useful and is the source for the multiple modes of functionality.  Setting the environment variable to one of the following will have the indicated result.

X - Uses the X cursor with "no jiggle" DISABLED.
ex:
```

env WINE_CURSOR=X; wine "C:\Program Files\Ventrilo\Ventrilo.exe"         ....(for GNOME)

export WINE_CURSOR=X; wine "C:\Program Files\Ventrilo\Ventrilo.exe"         ....(for KDE)

```

XNOJIG - Uses the X cursor with "no jiggle" ENABLED.
ex:
```

env WINE_CURSOR=XNOJIG; wine "C:\Program Files\World of Warcraft\Wow.exe -opengl"       ....(for GNOME)

export WINE_CURSOR=XNOJIG; wine "C:\Program Files\World of Warcraft\Wow.exe -opengl"       ....(for KDE)

```

ANYTHING - Uses gaunt in game with "no jiggle" ENABLED.  (functions exactly as before, so no change should be necessary if you don't want it).
ex
```

env WINE_CURSOR=lkjlkjfd; wine "C:\Program Files\World of Warcraft\Wow.exe -opengl"       ....(for GNOME)

export WINE_CURSOR=lkjfmnkkf; wine "C:\Program Files\World of Warcraft\Wow.exe -opengl"       ....(for KDE)

```

Compiling with rc3! :popcorn:

*holding thumbs*

---

### Post by ronkkrop on 2010-06-13
> **hallon said:**
> Compiling with rc3! :popcorn:

*holding thumbs*

Let us know how it works out.

---

### Post by agaida on 2010-06-14
Filed this in launchpad.
[https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/593539](https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/593539)

---

### Post by hallon on 2010-06-14
> **ronkkrop said:**
> Let us know how it works out.

Compile went fine, after changing the mpg-seek reference for 64-bit! :) Did a little silent edit "Last edited by hallon; 2 Days Ago at 01:54 PM.. Reason: Flawless compile! \o/ Thanks alot for this patch ronkkrop!" but it was maybe abit too silent :p

EDIT:
Just compiled rc4 with the same patch, flawless :)

---

### Post by Iksf on 2010-06-22
WOOOP!
Cataclysm Beta patch notes....

"# OpenGL Hardware Cursor support (can be enabled on the Video Resolution Panel).
# Improved water and lava rend...."

Cataclysm rev 12266

---

### Post by ronkkrop on 2010-06-22
> **Iksf said:**
> WOOOP!
Cataclysm Beta patch notes....

"# OpenGL Hardware Cursor support (can be enabled on the Video Resolution Panel).
# Improved water and lava rend...."

Cataclysm rev 12266

very excellent!

---

### Post by Metrop021 on 2010-06-22
> **Iksf said:**
> WOOOP!
Cataclysm Beta patch notes....

"# OpenGL Hardware Cursor support (can be enabled on the Video Resolution Panel).
# Improved water and lava rend...."

Cataclysm rev 12266

very nice :)

---

### Post by hallon on 2010-06-24
> **Iksf said:**
> WOOOP!
Cataclysm Beta patch notes....

"# OpenGL Hardware Cursor support (can be enabled on the Video Resolution Panel).
# Improved water and lava rend...."

Cataclysm rev 12266

Lovely!!

but this thread will die with it ;( that's kinda sad, no?

---

### Post by l1nuxfre4k on 2010-06-26
hey all.
just fixed this for my WOW and i got a problem :p
if i press alt and try pressing something it wont work.
i mean like if you wanna switch weapon and such.
are there a solution for this?

---

### Post by Metrop021 on 2010-06-27
> **l1nuxfre4k said:**
> hey all.
just fixed this for my WOW and i got a problem :p
if i press alt and try pressing something it wont work.
i mean like if you wanna switch weapon and such.
are there a solution for this?

gonna go out on a limb and say your sticky keys keybind for ubuntu is alt (not sure if its shift by default or alt...) try to diable it in the compiz settings. or just try to disable compiz

---

### Post by MerlinX420 on 2010-06-27
I've dug through this post all day trying everything and i can't get this to work. I have an AMD64 and the pre-packaged versions are for 32 bit.
I can't use any of the above mentioned wine versions because they do NOT SUPPORT PULSE AUDIO. Hardware cursor without audio is fail.

I can't seem to find a source version of wine with pulse and with my limited bandwidth I can't go around DL'ing everything in hopes that i get it to work.

Is there anyway to apply this patch to an already installed version of Wine?
I have 1.1.42 with pulse audio back-end running on Ubuntu 10.04 and can't figure this out.

- A little bit later in the day -

Seems I've found a wine with pulse audio WITH HWC support for OpenGL.

[https://launchpad.net/~vivnet/+archive/vivnet-wine]("https://launchpad.net/~vivnet/+archive/vivnet-wine")

" A compilation of wine with several feature enhancing or bug fixing patches applied. Specifically: fixes for crashing in Counter-Strike: Source and Half-Life 2: Multiplayer (freetype.patch); fix for keyboard event issues that result in repeated pressing of a key that is held down (keyevent.patch); a pulseaudio driver; OpenGL Hardware Cursor support for World of Warcraft (only hwc packages)."

After Installing the PPA I continued to follow these steps:

wget [http://www.basixcomputer.com/circle](http://www.basixcomputer.com/circle)
sudo mv circle /usr/share/icons/DMZ-White/cursors/   (since the target dir are locked to root sudo had to be used to move the file)

* OPTIONAL * Supposedly violates Bliz EULA
wget [http://www.basixcomputer.com/patch-f.MPQ](http://www.basixcomputer.com/patch-f.MPQ)
mv patch-f.MPQ to /home/<USER>/drive_c/Program\ Files/World\ of\Warcraft/Data/

env WINE_CURSOR=1 nice -20 wine /home/<USER>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -opengl

I still have i guess what is termed as the "jiggly" mouse.

---

### Post by Brebs on 2010-06-28
> **MerlinX420 said:**
> PULSE AUDIO
See [Fedora's patches](http://cvs.fedoraproject.org/viewvc/rpms/wine/F-13/).

winepulse*.patch
README-FEDORA-PULSEAUDIO

---

### Post by Iksf on 2010-06-29
Hmm if theyr giving Cata a OpenGL hardware cursor maybe theyl be upgrading the whole thing. OpenGL vs DirectX aside, on WoW the OpenGL implementation is no where near the DirectX one

---

### Post by hallon on 2010-06-29
> **Iksf said:**
> Hmm if theyr giving Cata a OpenGL hardware cursor maybe theyl be upgrading the whole thing. OpenGL vs DirectX aside, on WoW the OpenGL implementation is no where near the DirectX one

I'm not sure if this is all true, but the OpenGL implementation** for the windows platform** is experimental and not supported by blizzard. 

On OS X it is ofc, since that's the 3D API available for that platform. Not all GL extentions are available on OS X though, as on windows (with gpu vendors own drivers being used there regardless of windows lack of OpenGL support) So on the major OpenGL platform WoW is being distributed for, there is no full fledged OpenGL implementation to make use of. Maybe that is what's holding blizzard back in further improving the OpenGL implementation in WoW?

Only speculations ofcourse, they might have workarounds I have no idea of :) Someone with knowledge please enlighten me if I am wrong!


EDIT: Successful compile for rc6 too with wine-hw-cursor-20100608. Although patch said something about an offset now, so they might have done a slight change in the source file.

---

### Post by gilberto.nakamura on 2010-07-05
As said previously in this thread, Cataclysm have a built-in HW mouse support for opengl. It works perfectly at the moment. If I'm following correctly the blizz beta posts and suggestions, it was implemented only after requests by users. They already had hw mouse on opengl implementation for Mac, but not for windows which explain why it was so easy to implement.

But I still doubt they will give equal opportunities for both platforms. Reason is the new damm water. As the time I wrote this post, beta client crashes when underwater in opengl mode. It's a known problem but it persists for some time now. It affects opengl under wine and windows =/ 

Also, shadows, sunshafts and water reflection only work in d3d9ex or d3d11 mode

---

### Post by Arythael on 2010-07-05
Following Doctor Debian's guide (post 82 in this thread) seemed to work, until I tried to install the final .deb file to update/patch wine. It won't let me run the .deb because I have a more recent version of wine (1.2-rc6) installed. How can I download the latest version of wine source/build-dep? Or, if I have to uninstall wine then install using the patched .deb (because 1.2-rc6 is the latest version), is it safe (read: won't cause errors/problems) to backup my C:\ as is, then paste it back into wine's folder structure after i reinstall and run winecfg?

Also, I deleted all of the source/build-dep files from my home directory manually. "sudo apt-get built-dep wine1.2" won't redownload them (it returns 0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.). What's the proper way to tell apt-get to remove the files, so I can run commands like "sudo apt-get built-dep wine1.2" again?

---

### Post by dardack on 2010-07-06
> **Arythael said:**
> Following Doctor Debian's guide (post 82 in this thread) seemed to work, until I tried to install the final .deb file to update/patch wine. It won't let me run the .deb because I have a more recent version of wine (1.2-rc6) installed. How can I download the latest version of wine source/build-dep? Or, if I have to uninstall wine then install using the patched .deb (because 1.2-rc6 is the latest version), is it safe (read: won't cause errors/problems) to backup my C:\ as is, then paste it back into wine's folder structure after i reinstall and run winecfg?

Also, I deleted all of the source/build-dep files from my home directory manually. "sudo apt-get built-dep wine1.2" won't redownload them (it returns 0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.). What's the proper way to tell apt-get to remove the files, so I can run commands like "sudo apt-get built-dep wine1.2" again?

Why do you want to build-dep again?  if you installed wine with apt-get, just sudo apt-get remove wine

Go to winehq.org and download the most current source.  Use my patch if just just want HW cursor and don't care about hiding the jiggling, or get that other guys patch that also hides cursor when looking around.  Once you patch the source, ./configure, make, sudo make install

Also, if your compiling your own and want Pulse compiled into wine (which I do and love), grab the wine pule patches also.

---

### Post by Arythael on 2010-07-06
> **dardack said:**
> Why do you want to build-dep again?
 
Because it's step 1 in Doctor Debian's guide. And as far as I can understand, I need to compile wine myself in order to apply the hwc patch.

Edit: I really didn't understand what build-dep does. After looking into it, I think I can see why I wouldn't need to run it again.

> **dardack said:**
> Also, if your compiling your own and want Pulse  compiled into wine (which I do and love), grab the wine pule patches  also.

I don't see any benefits from this, audio works perfectly fine in the version of wine from "sudo apt-get install wine," which I would assume is simply the compiled source.

---

### Post by hallon on 2010-07-09
These are the steps I take when dl:ing and compiling new wine, if any one new to it is interested :)

$ apt-get source wine
$ cd wine-whateveritgotwithaptget
$ dch -i (to edit the version to later)
$ patch -p1 < wine-hw-cursor-20100608.txt
$ scite dlls/winemp3.acm/mpegl3.c
and change mpg123_feedseek(aad->mh, 0, SEEK_SET, NULL);
to
mpg123_feedseek_64(aad->mh, 0, SEEK_SET, NULL);
in mpegl3.c since I run 64-bit system and compiling with mp3 support.

dpkg-buildpackage -rfakeroot -us -uc -b

install packages and ta-da! :-) works every time

---

### Post by Iksf on 2010-07-11
> **gilberto.nakamura said:**
> As said previously in this thread, Cataclysm have a built-in HW mouse support for opengl. It works perfectly at the moment. If I'm following correctly the blizz beta posts and suggestions, it was implemented only after requests by users. They already had hw mouse on opengl implementation for Mac, but not for windows which explain why it was so easy to implement.

But I still doubt they will give equal opportunities for both platforms. Reason is the new damm water. As the time I wrote this post, beta client crashes when underwater in opengl mode. It's a known problem but it persists for some time now. It affects opengl under wine and windows =/ 

Also, shadows, sunshafts and water reflection only work in d3d9ex or d3d11 mode

Good! Might be weird to say that as its errors etc but it means Blizzard are doing something with OpenGL. Hopefully an overhaul to OpenGL 3

---

### Post by manji_kun on 2010-07-11
this is a bit strange, i've been running WoW on ubuntu since 9.04, 9.10 offered some really nice fps, and recently i updated to 10.04, oddly enough im getting some weird visual glitches, like if i angle the camera view all textures fade into a solid color, or the brightness will drop drastically.

anyone know how to fix this? i tried tinkering with the video settings in game and nothing seems to work for me.

---

### Post by dardack on 2010-07-15
> **Arythael said:**
> <snip>

I don't see any benefits from this, audio works perfectly fine in the version of wine from "sudo apt-get install wine," which I would assume is simply the compiled source.

2 reasons.  First you asked where you could get the newest version of wine source, so assuming your compiling.  sudo apt-get install wine, doesn't install from source, and if your installing this way, you don't need build-dep wine anyways.

Second, your posting in a thread dedicated to modifying wine in source to add a faux HW Cursor for OpenGL.  And my point was if your compiling wine for the HW patch anyways, might as well compile pulse in also.  Lots of people have issues with wine/alsa and running wow and a vent client at same time (I was one of em).  So I went add the pulse in.  Plus it's nice to controll all wine programs sound with pulse manager.

---

### Post by hallon on 2010-07-15
> **dardack said:**
> 2 reasons.  First you asked where you could get the newest version of wine source, so assuming your compiling.  sudo apt-get install wine, doesn't install from source, and if your installing this way, you don't need build-dep wine anyways.

Second, your posting in a thread dedicated to modifying wine in source to add a faux HW Cursor for OpenGL.  And my point was if your compiling wine for the HW patch anyways, might as well compile pulse in also.  Lots of people have issues with wine/alsa and running wow and a vent client at same time (I was one of em).  So I went add the pulse in.  Plus it's nice to controll all wine programs sound with pulse manager.

Try Mangler for ventrilo client.

I threw pulse audio out awhile ago and have been settled just ALSA and everything works wonderfully. No popping cracking or delayed sound anymore. That can of course be hardware specific issues I have. Mangler works with ALSA too and simultaneously with WOW w/o pulseaudio.

Ofc you'll lack the ability to control each individual application with a mixer, but since most applications producing sound has a built in volume control I don't see the problem with this :p

---

### Post by dardack on 2010-07-15
> **hallon said:**
> Try Mangler for ventrilo client.

I threw pulse audio out awhile ago and have been settled just ALSA and everything works wonderfully. No popping cracking or delayed sound anymore. That can of course be hardware specific issues I have. Mangler works with ALSA too and simultaneously with WOW w/o pulseaudio.

Ofc you'll lack the ability to control each individual application with a mixer, but since most applications producing sound has a built in volume control I don't see the problem with this :p

I needed to go to pulse for wow's sound to work perfectly myself.

---

### Post by hallon on 2010-07-15
> **dardack said:**
> I needed to go to pulse for wow's sound to work perfectly myself.

oh.. :o  what didn't work? just curious, not questioning your decision.

Personally I had problems with popping and cracking sound, also sound getting out of sync with the game (WoW) when using pulse along with wine. That was wine w/o pulse audio patch though. But then I got other issues with pulse audio and Renoise (tracker program) so had to ditch it altogether. :/ The idea of PA is good though.

---

### Post by Bulpup on 2010-07-22
> **hallon said:**
> These are the steps I take when dl:ing and compiling new wine, if any one new to it is interested :)

$ apt-get source wine
$ cd wine-whateveritgotwithaptget
$ dch -i (to edit the version to later)
$ patch -p1 < wine-hw-cursor-20100608.txt
$ scite dlls/winemp3.acm/mpegl3.c
and change mpg123_feedseek(aad->mh, 0, SEEK_SET, NULL);
to
mpg123_feedseek_64(aad->mh, 0, SEEK_SET, NULL);
in mpegl3.c since I run 64-bit system and compiling with mp3 support.

dpkg-buildpackage -rfakeroot -us -uc -b

install packages and ta-da! :-) works every time

Bear with this greenhorn, please. :( This has been rather scary for me.

Okay. After ](*,) repeatedly and going from annoyed to laughing hysterically with disbelief over how many extra things I had to install just to get this list of instructions *started* (rassumfrassum wine repository not even having the source), I finally ran into this:

```
executor@Dante ~/wine-1.2 $ dpkg-buildpackage -rfakeroot -us -uc -b
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package wine
dpkg-buildpackage: source version 1.2~winehq0~ubuntu~10.04-0ubuntu10
dpkg-buildpackage: source changed by N Tak <executor@Dante>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: warning: debian/rules is not executable: fixing that.
 fakeroot debian/rules clean
 debian/rules build
 fakeroot debian/rules binary
 dpkg-genchanges -b >../wine_1.2~winehq0~ubuntu~10.04-0ubuntu10_amd64.changes
dpkg-genchanges: warning: the current version (1.2~winehq0~ubuntu~10.04-0ubuntu10) is smaller than the previous one (VERSION)
dpkg-genchanges: error: cannot read files list file: No such file or directory
dpkg-buildpackage: error: dpkg-genchanges gave error exit status 2
executor@Dante ~/wine-1.2 $
```

I have no idea what I broke this time. Help, please? All I want is the damned non-laggy pointer. :(

---

### Post by Morganvd on 2010-07-24
You might think this weired but I had a friend with the same problem today, Yet all he had to do to fix it was clear his cache (wow game cache). Hope it helps someone

---

### Post by hallon on 2010-07-25
> **Bulpup said:**
> Bear with this greenhorn, please. :( This has been rather scary for me.

Okay. After ](*,) repeatedly and going from annoyed to laughing hysterically with disbelief over how many extra things I had to install just to get this list of instructions *started* (rassumfrassum wine repository not even having the source), I finally ran into this:

```
executor@Dante ~/wine-1.2 $ dpkg-buildpackage -rfakeroot -us -uc -b
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package wine
dpkg-buildpackage: source version 1.2~winehq0~ubuntu~10.04-0ubuntu10
dpkg-buildpackage: source changed by N Tak <executor@Dante>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: warning: debian/rules is not executable: fixing that.
 fakeroot debian/rules clean
 debian/rules build
 fakeroot debian/rules binary
 dpkg-genchanges -b >../wine_1.2~winehq0~ubuntu~10.04-0ubuntu10_amd64.changes
dpkg-genchanges: warning: the current version (1.2~winehq0~ubuntu~10.04-0ubuntu10) is smaller than the previous one (VERSION)
dpkg-genchanges: error: cannot read files list file: No such file or directory
dpkg-buildpackage: error: dpkg-genchanges gave error exit status 2
executor@Dante ~/wine-1.2 $
```

I have no idea what I broke this time. Help, please? All I want is the damned non-laggy pointer. :(

ah, hm.. you did do "dch -i" and raise the version number? :o

avoid using letters in the version number.. just add a 0 or 1, or 2, or 3 (you get the idea) thats what I do and it usually works :) so if the version says "1.2~winehq0~ubuntu~10.04-0ubuntu10" I change it to "1.2~winehq0~ubuntu~10.04-0ubuntu11"

---

### Post by Bulpup on 2010-07-26
> **hallon said:**
> ah, hm.. you did do "dch -i" and raise the version number? :o

avoid using letters in the version number.. just add a 0 or 1, or 2, or 3 (you get the idea) thats what I do and it usually works :) so if the version says "1.2~winehq0~ubuntu~10.04-0ubuntu10" I change it to "1.2~winehq0~ubuntu~10.04-0ubuntu11"

This is the funny thing: that changelog file and the debian directory it's supposed to be in didn't exist when I tried compiling things the first time. :confused: In my exasperated desperation, I ended up creating both the directory and the file from scratch (by which I mean I opened gedit and named it "changelog") and put that single line in it. This is probably why things broke, lol.

The friend of mine responsible for getting me to install Linux got to hear me ranting and raving throughout the process; she thinks I should be turned loose on the dev team because I seem to keep finding all the strange things, and I think she might be right. :biggrin:

---

### Post by n4h0j on 2010-07-28
> Finally, download the MPQ here

[http://www.basixcomputer.com/patch-f.MPQ](http://www.basixcomputer.com/patch-f.MPQ)

and place it into your Data folder in your World of Warcraft folder. The patch is now installed!

This link no longer works, it gives me 404. Anyone has the patch and can post it here again?

---

### Post by dardack on 2010-07-30
> **n4h0j said:**
> This link no longer works, it gives me 404. Anyone has the patch and can post it here again?

I'll host it:

[http://dardack.is-a-geek.org/wowpatch/](http://dardack.is-a-geek.org/wowpatch/)

---

### Post by Iksf on 2010-08-06
cursor patch missing too

---

### Post by dardack on 2010-08-06
> **Iksf said:**
> cursor patch missing too

Which cursor patch?

---

### Post by cheesemidget on 2010-08-07
all items hosted on basixcomputer.com are no longer

---

### Post by Doctor Debian on 2010-08-08
Hi everyone;

The BasixComputer server's hard drive crashed recently, rendering most of the data irretrievable. I've reuploaded most of the files and updated the patch to the version compatible with Wine 1.3/1.2. I apologize for my lack of activity in this thread, as I no longer play WoW and have been very busy with work.

Andrew

---

### Post by Doctor Debian on 2010-08-08
Also, if anyone could provide me with a copy of the "circle" cursor file, that would be greatly appreciated ;)

Thanks!
Andrew

---

### Post by nikkoname on 2010-08-10
I also need patch-f cirle, i can't download ç_ç

---

### Post by IngoWagner on 2010-08-10
I am following this
[http://ubuntuforums.org/showpost.php?p=7643957&postcount=82](http://ubuntuforums.org/showpost.php?p=7643957&postcount=82)

I'm ok untill I try the following:
ingo@ingo-pc:~/wine1.2-1.1.42$ sudo patch -p1 < wine-cursor-patch-new.txt 

I get this:
Hunk #1 succeeded at 45 (offset 1 line).
Hunk #2 FAILED at 201.
Hunk #3 succeeded at 1057 (offset 152 lines).
Hunk #4 succeeded at 1099 (offset 152 lines).
1 out of 4 hunks FAILED -- saving rejects to file dlls/winex11.drv/mouse.c.rej

I kept going and followed the rest of the guide but then the cursor doesn't show up, I guess the Hunk failed thing is the error and I can't fix it...

Any ideas?
Thank you.

[EDIT]: I made it work downloading the ViVnet Wine:
[https://launchpad.net/~vivnet/+archive/vivnet-wine](https://launchpad.net/~vivnet/+archive/vivnet-wine)
If anyone is interested.

---

### Post by dardack on 2010-08-10
> **Doctor Debian said:**
> Also, if anyone could provide me with a copy of the "circle" cursor file, that would be greatly appreciated ;)

Thanks!
Andrew

Sorry I would, but I never used your circle cursor.  I liked my black theme for Ubuntu, so I always changed the patch just a tad, to use the same cursor as was default for ubuntu, so you never saw a difference.

---

### Post by dardack on 2010-08-10
> **IngoWagner said:**
> I am following this
[http://ubuntuforums.org/showpost.php?p=7643957&postcount=82](http://ubuntuforums.org/showpost.php?p=7643957&postcount=82)

I'm ok untill I try the following:
ingo@ingo-pc:~/wine1.2-1.1.42$ sudo patch -p1 < wine-cursor-patch-new.txt 

I get this:
Hunk #1 succeeded at 45 (offset 1 line).
Hunk #2 FAILED at 201.
Hunk #3 succeeded at 1057 (offset 152 lines).
Hunk #4 succeeded at 1099 (offset 152 lines).
1 out of 4 hunks FAILED -- saving rejects to file dlls/winex11.drv/mouse.c.rej

I kept going and followed the rest of the guide but then the cursor doesn't show up, I guess the Hunk failed thing is the error and I can't fix it...

Any ideas?
Thank you.

[EDIT]: I made it work downloading the ViVnet Wine:
[https://launchpad.net/~vivnet/+archive/vivnet-wine](https://launchpad.net/~vivnet/+archive/vivnet-wine)
If anyone is interested.


More then likely your patching 1.1.42 with the patch for 1.2 which are not compatible.

EDIT: see post 212 and 224.

---

### Post by Silentzor on 2010-08-13
Hey everyone, been reading this thread all morning.

First of all thanks to everyone for helping/contributing.

I'd like to ask,
is the circle file necessary? The link given is broken and i can't seem to find it anywhere else.

Thanks

---

### Post by Iksf on 2010-08-14
Think iv got it will check in a sec, stuck in gentoo kernel hell atm
edit:
If you need any other files as well i installed it on a friends computer and know for a fact i didnt clean up after, can get them off him

---

### Post by Iksf on 2010-08-14
Ok here we are got it

---

### Post by Silentzor on 2010-08-14
> **Iksf said:**
> Ok here we are got it

Thanks a lot mate!

I followed vbundi's guide (page 23 #225), and it works like a charm on ubuntu 10.04 64bit.

---

### Post by DeadEyeDoc on 2010-08-14
Hi there,

Im a complete noob when it comes to linux. Ive been trying to sort this cursor problem out on wow for a while now. 

I downloaded the first patch and i kept getting:

Hunk #1 FAILED at 44.
Hunk #2 FAILED at 201.
Hunk #3 FAILED at 895.
Hunk #4 FAILED at 937.
4 out of 4 hunks FAILED

So i then read on and found the new patch. I tried with that but got the same problem :confused:.
Then i tried to follow:

1. Download 1.2-rc1+ sourcecode from Winehq [http://ibiblio.org/pub/linux/system/....2-rc1.tar.bz2]("http://ibiblio.org/pub/linux/system/emulators/wine/wine-1.2-rc1.tar.bz2")
2. Download ronkkrop's patch from above post.
patch -p1 < wine-hw-cursor-20100528.txt (from within wine-1.2-rc1)
3. ./configure && make && sudo checkinstall
4. wget [http://www.basixcomputer.com/circle](http://www.basixcomputer.com/circle)
5. mv circle /usr/share/icons/DMZ-White/cursors/
6. To start wow, use the command below substituting <USER> with your username
7. * OPTIONAL * Supposedly violates Bliz EULA
wget [http://www.basixcomputer.com/patch-f.MPQ](http://www.basixcomputer.com/patch-f.MPQ)
mv patch-f.MPQ to /home/<USER>/drive_c/Program\ Files/World\ of\Warcraft/.

Ok, so Ive downloaded all the relevant files, but i dont understand how to use  1.2-rc1... :(
I dont know if i have to run it, install it or... anything. I feel like if i get that sorted then I can complete the rest.

Thanks for all this help guys,

Your friendly Linux Noob
DeadEyeDoc :D

---

### Post by svev on 2010-08-17
> **vbundi said:**
> The Instructions below are meant to be a summary, and I take no credit.
I have tested the above patch by ronkkrop and it works great.

All commands are done as the user (not root)

1. Download 1.2-rc1+ sourcecode from Winehq [http://ibiblio.org/pub/linux/system/emulators/wine/wine-1.2-rc1.tar.bz2](http://ibiblio.org/pub/linux/system/emulators/wine/wine-1.2-rc1.tar.bz2)
2. Download ronkkrop's patch from above post.
patch -p1 < wine-hw-cursor-20100528.txt (from within wine-1.2-rc1)
3. ./configure && make && sudo checkinstall
4. wget [http://www.basixcomputer.com/circle](http://www.basixcomputer.com/circle)
5. mv circle /usr/share/icons/DMZ-White/cursors/
6. To start wow, use the command below substituting <USER> with your username
7. * OPTIONAL * Supposedly violates Bliz EULA
wget [http://www.basixcomputer.com/patch-f.MPQ](http://www.basixcomputer.com/patch-f.MPQ)
mv patch-f.MPQ to /home/<USER>/drive_c/Program\ Files/World\ of\Warcraft/Data/

***
env WINE_CURSOR=1 nice -20 wine /home/<USER>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -opengl
***

You can place that command in a bash script
vi wow.bsh

#!/bin/bash
<the above command>

(save)
chmod +x wow.bsh

You can now run wow by doing ./wow.bsh


I have compiz disabled
In winecfg under video, I have emulate a virtual desktop, and allow the window manager to control wine (bottom two checkboxes)

Working in Lucid i386 using Nvidia hardware.

Thanks to everyone that has helped.

All clear but i don't understand one thing: before doing these steps, i have to uninstall the existing wine (not patched) or not??
Is this guide works also on 64 bit??
tx

---

### Post by Doctor Debian on 2010-08-18
> **Iksf said:**
> Ok here we are got it

Thanks for finding that ;)! I've uploaded it back to the BasixComputer server so it has a permanent home.

---

### Post by DeadParrot on 2010-09-04
That's what I get when I attempt to install the original patch 

> lukas@M1330:~/wine1.2-1.1.42$ patch -p1 < wine-cursor-patch-new.txt
patching file dlls/winex11.drv/mouse.c
Hunk #1 succeeded at 45 (offset 1 line).
Hunk #2 FAILED at 201.
Hunk #3 succeeded at 1057 (offset 162 lines).
Hunk #4 succeeded at 1143 (offset 162 lines).
1 out of 4 hunks FAILED -- saving rejects to file dlls/winex11.drv/mouse.c.rej
lukas@M1330:~/wine1.2-1.1.42$ 

I'm just starting out with Ubuntu, hence would prefer really thorough answers, but anything will do :D

---

### Post by loklaan on 2010-09-04
This has been mentioned before, but I think it is worth bumping so it can reach everyone. Blizzard has included a perfect working OpenGL hardware cursor to the next expansion for WoW, Cataclysm.

Very good news for all. This will encourage more Linux+WoW.

---

### Post by nikkoname on 2010-09-06
Guys.... i did install wine patcher as you said but.....
the cursor turn invisibile at the first click...everywhere I click in wow window the cursor disappear

edit: when mouse is over a mob i see the "sword" or over a vein i see the pick, all other simbol but not the "default hand"
edit:  when wow starts i see a cursor, the hand when i put cirle file in /usr/share/icons or a simple circle when i do not. But at the first click anywhere it disappear....
ideas?

SOLVEDDDDDD
> Hi there,

Im a complete noob when it comes to linux. Ive been trying to sort this cursor problem out on wow for a while now. 

I downloaded the first patch and i kept getting:

Hunk #1 FAILED at 44.
Hunk #2 FAILED at 201.
Hunk #3 FAILED at 895.
Hunk #4 FAILED at 937.
4 out of 4 hunks FAILED

So i then read on and found the new patch. I tried with that but got the same problem :confused:.
Then i tried to follow:

1. Download 1.2-rc1+ sourcecode from Winehq [http://ibiblio.org/pub/linux/system/....2-rc1.tar.bz2]("http://ibiblio.org/pub/linux/system/emulators/wine/wine-1.2-rc1.tar.bz2")
2. Download ronkkrop's patch from above post.
patch -p1 < wine-hw-cursor-20100528.txt (from within wine-1.2-rc1)
3. ./configure && make && sudo checkinstall
4. wget [http://www.basixcomputer.com/circle](http://www.basixcomputer.com/circle)
5. mv circle /usr/share/icons/DMZ-White/cursors/
6. To start wow, use the command below substituting <USER> with your username
7. * OPTIONAL * Supposedly violates Bliz EULA
wget [http://www.basixcomputer.com/patch-f.MPQ](http://www.basixcomputer.com/patch-f.MPQ)
mv patch-f.MPQ to /home/<USER>/drive_c/Program\ Files/World\ of\Warcraft/.

Ok, so Ive downloaded all the relevant files, but i dont understand how to use  1.2-rc1... :sad:
I dont know if i have to run it, install it or... anything. I feel like if i get that sorted then I can complete the rest.

Thanks for all this help guys,

Your friendly Linux Noob
DeadEyeDoc
I did like in quotes but between 3rd and 4th point i did:
> sudo make install

---

### Post by Zenlol on 2010-09-06
I went through most of the steps here without a problem but when I went to enter this line...

dpkg -i wine1.2_(wineversion)~ubuntu~(ubuntuversion)-0ubuntu10_(arch).deb

It told me this...

bash: syntax error near unexpected token `('

I was confused but after reading that you could also double click the file, I tried doing that. However there are about 5 files with relatively the same name so I'm unsure about which one to pick. 
 Here's what it looks like...

[http://img816.imageshack.us/img816/7633/screenshotoy.png](http://img816.imageshack.us/img816/7633/screenshotoy.png)

Thank you for reading.

---

### Post by nikkoname on 2010-09-07
> **Zenlol said:**
> I went through most of the steps here without a problem but when I went to enter this line...

dpkg -i wine1.2_(wineversion)~ubuntu~(ubuntuversion)-0ubuntu10_(arch).deb

It told me this...

bash: syntax error near unexpected token `('

I was confused but after reading that you could also double click the file, I tried doing that. However there are about 5 files with relatively the same name so I'm unsure about which one to pick. 
 Here's what it looks like...

[http://img816.imageshack.us/img816/7633/screenshotoy.png](http://img816.imageshack.us/img816/7633/screenshotoy.png)

Thank you for reading.
simply open your home folder, you'lll see a few .deb file....you just need to double click on wine1.2_1.2-0ubuntu10-lucid3_i386.deb

---

### Post by nikkoname on 2010-09-07
guys, but why when i use
> sudo get source wine1.2I get wine1.2-1.1.42 and not 1.2-1.2?


EDIT: guys, another problem comes up.... when i right-click for camera/pg moving the cursor appears in the center of wow windows and seems to be blocked, i can move camera but i see the cursor over my pg.... it's....stressful xD

---

### Post by Tletl on 2010-09-18
Hopefully this thread doesn't die. This patch has made many games playable, including Ragnarok Online (the one I tried).

Thank you so much for the patch! Compiled on Wine 1.2 :D

---

### Post by Glaucous on 2010-10-01
> **BuNsiE said:**
> This has been mentioned before, but I think it is worth bumping so it can reach everyone. Blizzard has included a perfect working OpenGL hardware cursor to the next expansion for WoW, Cataclysm.

Very good news for all. This will encourage more Linux+WoW.

Yup, it works great. I have the Cataclysm Beta and it works quite nicely.

---

### Post by svev on 2010-10-07
It'all ok with the patch..but i don't know where to put the circle file in XFCE4...:(:(:(:(:(
someone could help me?

---

### Post by dardack on 2010-10-12
THIS IS NO LONGER NEEDED as of PATCH 4.0.1.  HW OPEN GL CURSOR is now standard with wow.

---

### Post by _outlawed_ on 2010-10-12
> **dardack said:**
> THIS IS NO LONGER NEEDED as of PATCH 4.0.1.  HW OPEN GL CURSOR is now standard with wow.

Is about time Blizzard listened to us, we've been crying out for this for how long now? lol

---

### Post by evailya on 2010-10-13
OK so i have patch 4.0.1 installed but when i log on the and select a character my screen goes blank ive tried it in wine and cross over both have same result. Any ideas as to how to fix that?

---

### Post by TimeSInk on 2010-10-13
Similar problem to above. 

Starting with OpenGl gives me the hand cursor and a black screen; starting without OpenGl gives me a black background to with limited foreground objects (I can see the login boxes, but the details for the video settings are hidden in the background.

nVidia on-board video, 4.01 copied from a Windows box (due to the permissions lockout problem).

Thanks for any ideas.

---

### Post by _outlawed_ on 2010-10-13
Have you two tried any of these troubleshooting tips?

[https://help.ubuntu.com/community/WorldofWarcraft#Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft#Troubleshooting)

---

### Post by TimeSInk on 2010-10-13
Thank you, Dan. Sometimes you forget to double check the 'old school' fixes!

Nope, not in my case this time: I'd removed some of that last year since I found I did not need to run under OpenGl. In the case of the new patch (and the nVidea card likely), implementing those fixes has no effect on either a direct call to wow.exe or a call with OpenGl flagged. 

...but hey, it appears the hardware mouse cursor is working under both!

---

### Post by _outlawed_ on 2010-10-13
Not even the M2UseShaders thingy worked?

---

### Post by TimeSInk on 2010-10-13
Nope, and I recall that being a major save that last time things borked. 

At this point I'm working my way though config.wtf's "gx" settings one at a time, disabling and re-enabling.

---

### Post by TimeSInk on 2010-11-02
It took a while. Final fix (after a new vid card and updates and all sorts of unsuccessful tweakage): I updated to Wine 1.3.x and it fired up on the first try. The Launcher worked properly also and pulled down the latest update for Cata.

Now to undo all the tweaks!

---

### Post by cwwilson721 on 2010-11-02
> **TimeSInk said:**
> It took a while. Final fix (after a new vid card and updates and all sorts of unsuccessful tweakage): I updated to Wine 1.3.x and it fired up on the first try. The Launcher worked properly also and pulled down the latest update for Cata.

[COLOR="Blue"]Now to undo all the tweaks![/COLOR]

'Specially since HW Cursor is supported now.

It just seems faster, too. [After making my video for YouTube to prove that Linux/wine/WoW was faster than Window 7/WoW]("http://www.youtube.com/watch?v=xQFBK1yNIxE"), I thought back to 3.x patch era.

And I think WoW/wine HAS been getting faster and faster.

And about time to get an integrated HW cursor for OpenGL!

---

### Post by zong1 on 2010-11-14
> **Doctor Debian said:**
> Updated for Karmic Koala 9.10:

NOTE: This tutorial is actively updated, and contains the latest information for patching. This post should be all you need to have a working hardware cursor.

Alright everyone, I've found a great, legal way to reimplement the cursor hiding for this patch AND keep the WoW cursor only inside of wine apps.

Firstly, install the required packages to build wine by typing

```
sudo apt-get build-dep wine1.2
```

Get the source of wine by typing

```
apt-get source wine1.2
```

When the source is retrieved, type

```
cd wine1.2-*
```

Proceed to download my patch by typing in

```
wget http://www.basixcomputer.com/wine-cursor-patch-new.txt
```

Install the patch with

```
patch -p1 < wine-cursor-patch-new.txt
```

If the patching has succeded, it should display a single line with the file it has patched.

Before installing, you must first change the version number to make sure it doesn't get overwritted. Edit the debian/changelog file, and change the "ubuntu(number)" in the first line to "ubuntu10".

Change into the previous directory (if you entered the changelog's directory), and build the package with

```
dpkg-buildpackage -uc -us -b
```

Now, wait a long time. When it's completed, type in

```
dpkg -i wine1.2_(wineversion)~ubuntu~(ubuntuversion)-0ubuntu10_(arch).deb
```

Or simply double click the package in that directory. Either way, it will overwrite the existing wine.

Then, you must copy the custom cursor file for use in wine. Download the file here

[http://www.basixcomputer.com/circle](http://www.basixcomputer.com/circle)

and save it into your current cursor directory (e.g /usr/share/icons/DMZ-White/cursors for gnome, /usr/share/icons/oxy-white/cursors for kde)

OPTIONAL STEP FOR GAUNTLET IN-GAME: (if you just want the normal cursor in game, don't do this)

Finally, download the MPQ here

[http://www.basixcomputer.com/patch-f.MPQ](http://www.basixcomputer.com/patch-f.MPQ)

and place it into your Data folder in your World of Warcraft folder. The patch is now installed!

To use the patch, change your World of Warcraft launcher to

```
env WINE_CURSOR=anything; wine (world of warcraft path)

```
Congratulations, enjoy your new cursor.

Andrew

Thanks to WowZym for parts of the tutorial, and Larsson for patch toggling!


Hi, 

I tried this but it would not work with my wine 1.2, so I downloaded and installed wine 1.3 from the repos.  How could I apply this patch and rebuild using 1.3:

#  apt-get build-dep wine1.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for wine1.3
#  apt-get build-dep wine1.3.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for wine1.3.6
# wine --version
wine-1.3.6

---

### Post by cwwilson721 on 2010-11-14
Most of this whole post is not needed, because the newest WoW (4.0.1) has an opengl hardware cursor now.

---

### Post by mepatuhoo on 2010-11-14
i think that we should all boycott WOW till they release the native Linux client. if you want are cash make us a native WOW, blizzard. on that part if we start boycotting all there games till they get the idea that where here and where not going to stand for them ignoring us then they will move. we can play chicken better then blizzard can. there are a lot more Linux users that play WOW then you would think. if all Linux users stand together we are a force that no one wants to mess with. we will not be silenced blizzard!!!! and i will not use wine when they could have easily released the Linux client that they made years ago.

---

### Post by zorg2 on 2010-11-15
I am not playing W.O.W so their client does not affect me. I am interested purely with the hardware mouse pointer. 

Many other games have the same mouse problem with wine 1.3.6 (and wine 1.2).
Example of these games are :-
Anarchy Online
Neocron
I am sure there are many others. It makes these games pointless to play.  This is why I want to apply the patch to the latest wine.  I did try with wine 1.2, but it failed when I ran 
dpkg-buildpackage -uc -us -b

Cheers, z



PS. Yes, I know that this thread has been hi-jacked, albeit in a very  related sort of way.  I would ask this question on the AO forums, but  one has to pay for a subscription to post there, yet I won't part with  money until I know that I can play AO on WINE or a native client is  released.

P.P.S Posted from another account because I had to create a new one - password forgetten - and Opera does not allow one to view saved passwords. In process of moving back to Firefox because of it.

---

### Post by dardack on 2010-11-15
> **zorg2 said:**
> I am not playing W.O.W so their client does not affect me. I am interested purely with the hardware mouse pointer. 

Many other games have the same mouse problem with wine 1.3.6 (and wine 1.2).
Example of these games are :-
Anarchy Online
Neocron
I am sure there are many others. It makes these games pointless to play.  This is why I want to apply the patch to the latest wine.  I did try with wine 1.2, but it failed when I ran 
dpkg-buildpackage -uc -us -b

Cheers, z

PS. Yes, I know that this thread has been hi-jacked, albeit in a very  related sort of way.  I would ask this question on the AO forums, but  one has to pay for a subscription to post there, yet I won't part with  money until I know that I can play AO on WINE or a native client is  released.

P.P.S Posted from another account because I had to create a new one - password forgetten - and Opera does not allow one to view saved passwords. In process of moving back to Firefox because of it.

Did you get my patch a few pages back?  I could repost it.  It works in 1.2/.3.  However, in other games, unless there is some way to hide their cursor like there was in wow, you'll see your Xcursor and the game's cursor.

This is how you build it in ubuntu anyways.

sudo apt-get build-dep wine
download source
unpack sourch
get my patch
cd into source directory 
patch -p1 < /path/to/where/you/downloaded/my/patch
./configure
make
sudo make install

All done.

---

### Post by dardack on 2010-11-15
> **mepatuhoo said:**
> i think that we should all boycott WOW till they release the native Linux client. if you want are cash make us a native WOW, blizzard. on that part if we start boycotting all there games till they get the idea that where here and where not going to stand for them ignoring us then they will move. we can play chicken better then blizzard can. there are a lot more Linux users that play WOW then you would think. if all Linux users stand together we are a force that no one wants to mess with. we will not be silenced blizzard!!!! and i will not use wine when they could have easily released the Linux client that they made years ago.

Really dude?  Get a grip.  Linux users are probably not even 1% and even if 5%, you really think they are going to create a client for 5% when that 5% can still play with wine?  They have actively helped wine/crossover (when users were banned for wine/crossover they fixed it rather quickly).  I also believe I once read a story where they actually tested their client with wine and such.

As for the linux client like 6 years ago for the beta/alpha, I don't blame them for not releasing.  You're talking many different types of linux distro's.  On top of that, basically only 1 type of card back then, and even to some extent true now, works well in 3d opengl on linux (nvidia, binary drivers).

So when you release a native client, you have to support it.  OK so you now have to support a native client with many people on linux that have no clue.  It's not meant as an offense at all, just that many people just want to use their computer and not mess with it, and for basic day to day use, linux can be that.  But when your talking about gaming linux is not there.  So now your asking blizzard to support a client across multiple OS's that each have different things going on, denying people access if not using nvidia (back then you would have to), and dealing with all the customer support for <5% of your user base prolly even less.

So, why you happily boycott, I happily play, because their stuff all works in wine (SC2, Sc1, war 2/3, WoW, diablo, diablo2 yes I have played all of these on linux in wine, some require a few hacks here and there, but wow runs f'ing great) without too much problems.  Heck SC2 I didn't have to do anything and it just worked for me.  I support Blizz because at least WoW they program in OpenGL for windows (wish they had for sc2, but still worked great) and their stuff works.  Now maybe with activision that will start to go away, but for now, I'm happy.

---

### Post by Zorael on 2010-11-24
I'm trying to apply this patch to work with Diablo 2. I'm running Kubuntu maverick and I followed [this guide](http://ubuntuforums.org/showpost.php?p=7643957&postcount=82) as linked on the first page.

I pulled the sources for wine1.2 from the maverick repositories, downloaded the patch to the **debian/patches/** directory and added an entry for it in the **series** file, then bumped the version number in **debian/changelog** and sent it to Launchpad for building. It compiled nicely, and the build logs showed it applying the patch.

```
*[...]*
Applying patch desktop-launcher-noexec
patching file tools/wine.desktop

Applying patch CJK-registry
patching file tools/wine.inf.in
Hunk #1 succeeded at 589 (offset 5 lines).

Applying patch photoshop-install-fix.patch
patching file dlls/msi/action.c

[B]Applying patch wine-cursor.patch
patching file ./dlls/winex11.drv/mouse.c
Hunk #4 succeeded at 992 (offset 1 line).[/B]
*[...]*
```

But even so, launching Diablo 2 (in windowed mode) I still get the gauntlet cursor. I made sure to download the "circle" cursor file and place it in **/usr/share/icons/oxy-white/cursors/**.

Did I miss something? I'd really like to get this to work. My netbook is otherwise fast enough to play Diablo 2 on, if it weren't for the lack of hardware cursors.

---

### Post by Zorael on 2010-11-25
To update, if I set WINE_CURSOR=fgsfds and open up winecfg, it uses the gauntlet cursor properly. If I set WINE_CURSOR=X it uses my X cursor instead of the boring Wine cursor.

But regardless of what I set WINE_CURSOR to, it always uses the gauntlet in Diablo 2, and it seems to not be a hardware cursor, as it lags around and has generally lower framerate than if I drag it outside the game window.

---

### Post by Zorael on 2010-12-18
Right, so to update for anyone googling "diablo 2 wine", I did some digging and found out that Diablo 2 just calls for Wine to hide the cursor as soon as it enters the game window, which (even with the patch from this thread) meant that you only got the normal game gauntlet cursor that obviously has to follow the game's own framerate.

I modified the patch a bit, so now it checks another environment variable (WINE_CURSOR_NOEMPTY) to see if it should hide the cursor at all, ever. I left in the extra behavior that hides the cursor if you press a button, but it also listens to a new environment variable (WINE_CURSOR_ALT) for toggling the behavior.

WINE_CURSOR can be set to either CROSS, PLUS, CIRCLE, TREK, or anything else to get the normal left-pointer cursor of your theme. They correlate to the cursors of your cursor theme (**/usr/share/icons/<theme>/cursors/**). I figure TREK is obscure enough that you can replace that one with a custom one. WINE_CURSOR_NOEMPTY and WINE_CURSOR_ALT just need to be defined and have any contents to be set. 

I made my own Diablo 2 gauntlet from an ingame screenshot, as the new WoW gauntlet posted earlier ("circle") didn't really fit with the one from the older game. See the attached screenshot. (Those cursors are normally just ontop of eachother; I'm forcing them apart here to show their likeness.)

I'm attaching the patch. I used the **wine_1.3_** source from Christoph Korn's PPA (without explicit permission! hwrr) ([**ppa:c-korn/ppa**](https://launchpad.net/~c-korn/+archive/ppa)), which includes the [**WinePulse**](http://art.ified.ca/?page_id=40) patch to get PulseAudio support. This patch works against that source. Compiled packages can be found at [my PPA](https://launchpad.net/~zorael/+archive/ppa/+packages). Copy the packages to your own PPA, download the .debs manually, or add the entire PPA to your software sources.

I may compile a thread just for Diablo 2, but later.

---

### Post by TbMa on 2011-05-19
I am very sorry for posting here, but is there way to get this patch work on latest wine 1.3.19(20)? I am still a wotlk player and playing in opengl mode result my cursor lagging.
Seems patch aint get updates :(

---

### Post by Zorael on 2011-05-20
> **TbMa said:**
> I am very sorry for posting here, but is there way to get this patch work on latest wine 1.3.19(20)?
Recent 1.3.19+ have some rehauled cursor behavior (introducing [bugs in several games](http://bugs.winehq.org/show_bug.cgi?id=27156)), so it's not as easy as just changing a few lines in the patch. I'm not proficient enough at C to write an altogether new one.

---

### Post by Zorael on 2011-05-24
That said, I managed to rework it a bit and it seems to work again. I'm attaching one patch for 1.3.18 (which is before that [nasty bug that makes games unplayable](http://bugs.winehq.org/show_bug.cgi?id=27156) snuck in), and one for current git (1.3.20 + some) as of today, 110525.

Environment variables:

1. **WINECURSOR**
This tells Wine to override its normal cursor with what you specify. The presets you can supply are **PLUS**, **CROSS**, **CIRCLE** and **TREK**. The latter two are sort of useless so feel free to replace the cursor files in **/usr/share/icons/<cursortheme>/cursors/**. Aside from those, you can also specify a number that corresponds to an entry in **/usr/include/X11/cursorfont.h**, which in turn points to a cursor (in that cursortheme directory). You'll need the [**libx11-dev**](apt://libx11-dev) package for that file. Note that if you enter an invalid value (not defined in cursorfont.h), Wine might not start.

2. **WINECURSORALWAYS**
This tells Wine to ignore calls for hiding the cursor. This is basically what you want for WoW, Diablo 2, Dead Space and other games that does its own software cursor instead of providing one for Wine to use natively. Setting this to anything makes Wine always display it, and you get the fake hardware cursor.

3. **WINECURSORHIDE**
This tells Wine to hide the cursor when you press a mouse button. So if you're playing a game where you hold a button for long periods of time (e.g. pan camera), and Wine keeps its cursor displayed (since you made it ignore calls to hide it with WINECURSORALWAYS), you can specify here which buttons *when held* should hide the cursor. You supply it as a number that correspond to all the mouse buttons you want to hide (**1** being left, **2** being middle, **3** being right, etc) added together, but *as exponents minus 1 to 2*. Put simpler;
```
Left mouse button:       **1** (2&#8304;)
Middle mouse button:     **2** (2¹)
Right mouse button:      **4** (2²)
Fourth mouse button:     **8** (2³)
Fifth:                  **16** (2&#8308;)
Sixth:                  **32** (2&#8309;)
Seventh:                **64** (2&#8310;)
Eighth:                **128** (2&#8311;)
Nineth:                **256** (2&#8312;)
```
Again, add together the ones you want. So if you want the cursor to hide when holding the right mouse button, just set it to **4**. If you want it to hide when you hold the right *and* fourth mouse button, set it to **12** (**4+8**). It's not an easy solution to use, but it's an easy way to embed information into a single number for an environment variable. Refer to **xev** output if you don't know what number a specific button is.

Examples;
```
$ WINECURSOR=PLUS WINECURSORALWAYS=1 WINECURSORHIDE=3 wine explorer /desktop=Diablo2,800x600 "Diablo II.exe"
```

```
#!/bin/bash

WINECURSOR=CROSS
WINECURSORALWAYS=1
WINECURSORHIDE=1 # left button

wine WoW.exe
```

etc. Hope it helps.

---

### Post by TbMa on 2011-06-03
> **Zorael said:**
> 

etc. Hope it helps.

nice. thanks. do you know any PPA which contains wine with pulseaudio and your hw-cursor patches?

---

### Post by Zorael on 2011-06-03
> **TbMa said:**
> nice. thanks. do you know any PPA which contains wine with pulseaudio and your hw-cursor patches?
Not that I'm aware; I just compiled the packages myself. I should be able to create one though, but I would probably only make it compile 1.3.18 packages until the erratic mouse behavior bug has been fixed. From what I've read it seems to be an X bug (xinput2), so the fix may be a while.

(disabling xinput2 support when configuring the build may work around it; I haven't tried.)

---

### Post by TbMa on 2011-06-03
> **Zorael said:**
> Not that I'm aware; I just compiled the packages myself. I should be able to create one though, but I would probably only make it compile 1.3.18 packages until the erratic mouse behavior bug has been fixed. From what I've read it seems to be an X bug (xinput2), so the fix may be a while.

(disabling xinput2 support when configuring the build may work around it; I haven't tried.)

1.3.21 is out and mouse bug is fixed (:

---

### Post by Zorael on 2011-06-03
> **TbMa said:**
> 1.3.21 is out and mouse bug is fixed (:
I'm still not at my desktop machine so I can't try it out, but the comments over on the bugtracker suggest the bug remains in 1.3.21?

[Comment #32 and #33 by karabaja](http://bugs.winehq.org/show_bug.cgi?id=27156#c32);
> **karabaja]It seems this bug still happens on alot of games, including:

Starcraft: Brood War (when rectangle-selecting units with mouse, after which
the game crashes when you release the mouse button)

P.S. Using wine 1.3.21.[/quote]
[Comment #34 by Evan Goers](http://bugs.winehq.org/show_bug.cgi?id=27156#c34) said:**
> This is still a problem in wine-1.3.21(actually, latest git). CounterStrike:
Source and possibly every other Source engine game is affected. Seemingly at
random, the mouse jumps in a way that you are instantly looking at the ground.
[Comment #35 by 3vil](http://bugs.winehq.org/show_bug.cgi?id=27156#c35);
> **3vil]I can confirm what Evan said in #34.

While the problem has been significantly reduced, it does occasionally and
randomly still seem to change where you're looking in Source games.  I tested
with L4D2 and the current git.[/quote]
[Comment #37 by Axel Angel](http://bugs.winehq.org/show_bug.cgi?id=27156#c37) said:**
> I can confirm this bug in Portal2. It happens in the git version I've installed
today.
Informations: wine-1.3.21, Gentoo Linux 2.6.36-gentoo-r5 #3 SMP Sat Mar 26
17:53:26 CET 2011 x86_64 Intel(R) Core(TM)2 Quad CPU Q9450 @ 2.66GHz
GenuineIntel GNU/Linux nvidia-drivers-260.19.36 and it happens often when you
play the game causing unexpected deaths! :P

etc.

---

### Post by sebasrodri on 2012-02-13
I need some beginner help here, it's my first time with Linux and i lack knowledge to understand these posts.
I'm using Wow 3.3.5a (private server) and today's latest stable wine (1.2? I got it from [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)).
I downloaded the txt file from post 224. That's all I reached, if I type "patch -pl <wine-hw-cursor-2010528.txt" i get "No such file or directory". I don't know how to continue.

Thanks for the response.

---

### Post by Tweak42 on 2012-02-15
Have you installed the dependencies and source code for wine1.2 as described in [post#82]("http://ubuntuforums.org/showpost.php?p=7643957&postcount=82")?  Also the syntax for the patch command should be "-p1" not "-pl" and spaces on both sides of "<" mark.  The command should be:
```
patch -p1 < wine-hw-cursor-2010528.txt
```
Note: this only will work if you in the same directory with the patch file and the wine source code. 

> **sebasrodri said:**
> I need some beginner help here, it's my first time with Linux and i lack knowledge to understand these posts.
I'm using Wow 3.3.5a (private server) and today's latest stable wine (1.2? I got it from [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)).
I downloaded the txt file from post 224. That's all I reached, if I type "patch -pl <wine-hw-cursor-2010528.txt" i get "No such file or directory". I don't know how to continue.

Thanks for the response.

---

