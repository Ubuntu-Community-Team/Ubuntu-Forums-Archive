---
title: "wine+ wow+ intel hd graphics!!!! help please"
date: 2011-02-27
forum: Wine
---

### Post by michael5593 on 2011-02-27
ok so i was following a tut on how to run wow in wine on ubuntu 10.10  now i am getting a msg when i try to launch wow that says  

YOUR3D ACCELERATOR  CARD IS NOT SUPPORTED BY WOW PLEASE INSTALL A 3D ACCELERATOR CARD WITH DUAL- TMU SUPPORT....

my guess is that i need to have intel drivers....
but i can do 3d cube and stuff so im guessing no, i read that wine is a  32 bit os emu i think i am using a 64 bit ubuntu never the less i am  using intel hd graphics my computer is

acer aspire 5742z. look at specs if needed someone please help me get wow to  be playable

thanks so much!!!!

ok well i got it to work without open gl now.... and i got like 15 fps -.- and my surroundings are all strobing in colors please help.....

---

### Post by HeadHunter00 on 2011-02-27
to run it with opengl, execute it from the command line: wine /wherever/you/installed/wow/executable/or/shortcut -opengl
for example, for me its on my desktop, so wine ~/Desktop/wow.exe -opengl

---

### Post by michael5593 on 2011-02-28
no i run fine in d3d mode..... smooth as can be..... but i have idk black shading under my npcs.... like the ground isnt loaded how do i fix this?....

---

### Post by michael5593 on 2011-02-28
help please it seems to be my shadow detail, but wow wont let me turn it up! and i could on win 7 !!! why not here!!!

---

### Post by cogadh on 2011-02-28
Linux, even Linux with Wine, is not Windows, that's why. You can't compare how software (especially games) worked in Windows to how you expect them to work in Linux, you are "comparing apples and oranges", as they say.

As for your problem, I think you missed the point of HeadHunter00's post: WOW needs to be run in OpenGL through Wine. Running it with Direct3D doesn't work all that well, which is probably why you are seeing problems with it. Check the WOW how-to in the Ubuntu community documentation for more info: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Tweak42 on 2011-02-28
> **michael5593 said:**
> help please it seems to be my shadow detail, but wow wont let me turn it up! and i could on win 7 !!! why not here!!!

Short answer:  Wow does not support higher shadow level detail in opengl mode until Blizzard implements it.

That answer and many more are found here: 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549)

---

### Post by cwwilson721 on 2011-02-28
The missing details, and black backgrounds, etc, are WELL KNOWN Intel issues while trying to run WoW on older Intel integrated video in D3D mode. IT WON'T WORK IN WINE.

To get it to MAYBE work with wine, you MUST append the "-opengl" switch to the end of the launch command, or add ```
SET gxApi "OpenGL"
```in config.wtf. If you use the append method, the appropriate line gets added to config.wtf anyway.

A quick serach of this forum would have told you all this, anyway, so I'm just telling you what you already knew, because
[COLOR="Red"]YOU DID SEARCH THE FORUM FIRST, RIGHT?[/COLOR]

---

### Post by michael5593 on 2011-03-01
no no no lol,
ok let me try again....

i have a intel hd graphics card....
i use wine in ubuntu 10.10
i had set my wow game mode or whatever to "opengl"
when i clicked wow it says some weird message refering to no open gl or w/e

that states the following

YOUR 3D ACCELERATOR  CARD IS NOT SUPPORTED BY WOW PLEASE INSTALL A 3D ACCELERATOR CARD WITH DUAL- TMU SUPPORT....

keep in mind i did not do the wine reg edit....

but on ubuntu i can do all my 3d cube fire magic lamp... all of the effects.... what is wrong and how do i fix it?.... someone please help i want to be 100% ubuntu this is the only thing stop me...

and my graphics card is new the whole lap top is...
my laptop model is

Acer Aspire 5742z.
please feel free to go to site and read specs i really need help.

---

### Post by cwwilson721 on 2011-03-02
Again....

[COLOR="Red"][SIZE="3"]SEARCH THE FORUM FOR "WOW+INTEL"[/SIZE][/COLOR]

You will magically know what the issue is, and not have to ask.

---

