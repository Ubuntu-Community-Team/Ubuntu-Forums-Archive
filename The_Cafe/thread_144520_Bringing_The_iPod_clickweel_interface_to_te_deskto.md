---
title: "Bringing The iPod clickweel interface to te desktop"
date: 2006-03-14
forum: The Cafe
---

### Post by OfficerDick on 2006-03-14
Hi i got this great idea, and i wrote a page about it. Basicly its exchanging the context menu with a more advanced iPod'ish clickwheel.
[http://ungefair.dk/clickwheel.pdf](http://ungefair.dk/clickwheel.pdf)
Please read the .pdf and give me your thoughts or other situations where the clickwheel could be used. And contact me if you are an programmer willing to sacrifice some time creating this app

Thx

-OfficerDick

---

### Post by Brunellus on 2006-03-14
isn't this what the synaptics touchpad driver was for?

---

### Post by OfficerDick on 2006-03-14
This is a GUI and not a touchpad driver

---

### Post by Brunellus on 2006-03-14
[QUOTE=OfficerDick]This is a GUI and not a touchpad driver[/QUOTE]
a good demonstration of Fitts' Law at work (quicker to acquire radiating rather than dropdown menus).  


There are Firefox extensions that make context-menus circular and radiating.  

The most interesting way to move forward would be to see if Nautilus could be tweaked to make this possible;  then it would be a matter of putting the necessary nautilus scripts into the right-click context menu, which would then radiate outwards from the pointer.  This would naturally limit the total number of buttons (sectors)....but I'm not a UI engineer, so.

---

### Post by engla on 2006-03-14
I know you will be disappointed, but:

I've seen a great, working use of this idea. It's in the very very good launcher/gatherer/tool Quicksilver for Mac OS X.

It's my favorite OS X application, and the only one I'm still missing in Ubuntu. This radial menu (called 'Constellation') is just one of it's many, many plug-ins.

[http://quicksilver.blacktree.com/](http://quicksilver.blacktree.com/)
[http://docs.blacktree.com/quicksilver/plug-ins/constellation](http://docs.blacktree.com/quicksilver/plug-ins/constellation)

I'll come up with screenshots and post them for you,
basically it's operation is 
1. Select something in a file viewer or just a text snippet or image in any other app, or, drag anything to a predefined hot spot on screen.
2. Pie menu pops up, allowing you to choose between actions that are contextually chosen (fits the mime-type). If the pie menu "overflows", you can click it and it flips like a coin to the next "page"

You can add a hotkey for a special Quicksilver catalog search, thereby giving you (for example) a menu of Open applications, All applications, recent files etc.

Yes, I think it's fantastic... it's not open source though, but it's free.

---

### Post by stuporglue on 2006-03-14
Probably not a good idea. Here's why.

1) Apple legal would have problems with it. There was a Windows CE music playing app that had the ipod wheel interface. Apple shut them down right quick.

2) It's hard to use. There was at one time a firefox gestures extension that used a pop-up wheel. You'd right click and this circle would appear. Depending on which way you gestured, different stuff would happen. Having the mouse slightly crooked would select the wrong option. 

That said, maybe the idea isn't bad, just the implementation I used. And maybe if it weren't a music program Apple legal wouldn't mind.

---

### Post by engla on 2006-03-14
Hope you see this as inspiration and acknowledgement, and not as some show-off from an outsider [not me]. The first thing I want is for this to be available in Ubuntu, it's ubuntu I use every day!


Here are some screenshots from the little evil empire in the blue mountains.
Note that Quicksilver is a third-party-app however.

1. Selection + hotkey => Radial context menu
2. Showing how "Open with..." pops up from 1.
3. Some radial iTunes menu. And some of the prefs

---

### Post by super on 2006-03-14
i think this would be too difficult to use with a mouse on a pc. it would just require too much coordination and would not have as much room for error as vertical menus.

however on a touchpad or laptop this would be perfect.

EDIT: on a second thought, after looking at the above screenshots, maybe it wouldn't be too bad. only one way to find out i guess!

---

### Post by tikal26 on 2006-03-14
I use Modo form luxology and they have what they call pie menues. It is something like that and I always thought that it would be nice to have the same kind of functionality in other progrmas, but I was thinkking programs like the gimp or krita. Also, kde haas a thing call katapult that works like apple's quicksilver and its developed by the kubuntu staff so maybe they could add something like this in the futre.

---

### Post by Alpha_toxic on 2006-03-14
I'd say this will be way cool!
btw, about Apple legal: I don't see any link betwen this thing and ipod's weel. I mean on the ipod you have to turn the weel to get to the right option, while here it will be just a circle menu instead of a drop-down one, no rotating or anything (I'm right, yes?).
I also think that it would be better if the menu appears after a single click (not holding), just like a normal drop-down menu and with some rotating animation while appearing this will be a killer! I hope someone develops this [-o<

---

### Post by Kvark on 2006-03-14
This is called a [Pie Menu]("http://en.wikipedia.org/wiki/Pie_menu") and it is fairly popular in games because it is faster to use then a normal right click menu. Once you remember which option is in which direction you don't need to see the menu, read the options and aim at the one you want. Right click while moving the mouse upwards and you'll activate the top option or while moving the mouse downwards to the left and you'll activate the option in that direction. The whole menu interaction is 1 click so by the time it takes for a normal right click menu to appear a pie menu is already done.

It would be great to have it as an option in gtk which type of menu to use on right click. A separate add on like the Firefox pie menu extension isn't any good though cause it doesn't work in all programs. It really needs to work in all programs, i guess that means it has to be a part of gtk.

---

### Post by Brunellus on 2006-03-14
[QUOTE=Kvark]This is called a [Pie Menu]("http://en.wikipedia.org/wiki/Pie_menu") and it is fairly popular in games because it is faster to use then a normal right click menu. Once you remember which option is in which direction you don't need to see the menu, read the options and aim at the one you want. Right click while moving the mouse upwards and you'll activate the top option or while moving the mouse downwards to the left and you'll activate the option in that direction. The whole menu interaction is 1 click so by the time it takes for a normal right click menu to appear a pie menu is already done.

It would be great to have it as an option in gtk which type of menu to use on right click. A separate add on like the Firefox pie menu extension isn't any good though cause it doesn't work in all programs. It really needs to work in all programs, i guess that means it has to be a part of gtk.[/QUOTE]
it would kick *** for the gIMP.  a real colorwheel!

---

### Post by OfficerDick on 2006-03-14
[QUOTE=engla]Hope you see this as inspiration and acknowledgement, and not as some show-off from an outsider [not me]. The first thing I want is for this to be available in Ubuntu, it's ubuntu I use every day!


Here are some screenshots from the little evil empire in the blue mountains.
Note that Quicksilver is a third-party-app however.

1. Selection + hotkey => Radial context menu
2. Showing how "Open with..." pops up from 1.
3. Some radial iTunes menu. And some of the prefs[/QUOTE]

I have a mac to. i Recently bought my iMac 20" ... appereantly the pie menu wont work under rossetta :( so i'll haf to wait for an universal, again:( But it is a fine machine

---

### Post by OfficerDick on 2006-03-14
[QUOTE=Kvark]This is called a [Pie Menu]("http://en.wikipedia.org/wiki/Pie_menu") and it is fairly popular in games because it is faster to use then a normal right click menu. Once you remember which option is in which direction you don't need to see the menu, read the options and aim at the one you want. Right click while moving the mouse upwards and you'll activate the top option or while moving the mouse downwards to the left and you'll activate the option in that direction. The whole menu interaction is 1 click so by the time it takes for a normal right click menu to appear a pie menu is already done.

It would be great to have it as an option in gtk which type of menu to use on right click. A separate add on like the Firefox pie menu extension isn't any good though cause it doesn't work in all programs. It really needs to work in all programs, i guess that means it has to be a part of gtk.[/QUOTE]

Thats what i mean ... if it could work in all prgrams it would kick *** ... but it has to be them all. imagine full screen editing with gimp and no toolbox thats all in the pie menu

---

### Post by ssam on 2006-03-14
i use [http://www.radialthinking.de/radialcontext/](http://www.radialthinking.de/radialcontext/) in firefox.

---

### Post by Jucato on 2006-03-14
This is a neat idea! Although of course confusing at first, but sure beats the hell out of your regular drop down menus.

Also, I don't think there will be a legal problem with Apple if you don't call it an iPod clickwheel. There are many alternative names. Pie Menu like Kvark said. Or Radial Menu, which is used in the Neverwinter Nights game. The idea isn't really a monopoly of Apple. The implementation/interface though, has to be different. :D

---

### Post by Mez on 2006-03-15
have a look at the "kommando" app for KDE - this does waht you want I believe

---

### Post by Jucato on 2006-03-15
That's exactly what I was talking about. I saw it before in KDE-Apps but forgot the name. Here's the link:
[http://www.kde-apps.org/content/show.php?content=29514]("http://www.kde-apps.org/content/show.php?content=29514")

---

### Post by OfficerDick on 2006-03-15
[QUOTE=Fenyx]That's exactly what I was talking about. I saw it before in KDE-Apps but forgot the name. Here's the link:
[http://www.kde-apps.org/content/show.php?content=29514]("http://www.kde-apps.org/content/show.php?content=29514")[/QUOTE]
Well im still on mac ... and when i use ubuntu i prefer gnome ...

---

### Post by engla on 2006-03-15
[QUOTE=Fenyx]That's exactly what I was talking about. I saw it before in KDE-Apps but forgot the name. Here's the link:
[http://www.kde-apps.org/content/show.php?content=29514]("http://www.kde-apps.org/content/show.php?content=29514")[/QUOTE]
Looks really cool. Now, could we do somehting like that for nautilus with a plugin?

---

### Post by Alpha_toxic on 2006-03-15
[QUOTE=Mez]have a look at the "kommando" app for KDE - this does waht you want I believe[/QUOTE]
I just tried that. It's pretty nice, but is static (I mean it shows the same buttons/options no matter what program you are using) and I think we need sth more like a drop-down context menu, one that has different options depending on what you right-clicked on.
AFAIR The Sims 2 used exactly the kind of menus we need, although they had text instead of icons.

---

