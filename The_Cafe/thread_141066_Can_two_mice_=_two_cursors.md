---
title: "Can two mice = two cursors?"
date: 2006-03-07
forum: The Cafe
---

### Post by cyberb0b on 2006-03-07
I have two eyes.

I have two hands.

I have two USB mice.

I have two mission-critical applications running, firefox and klickety.

Can I have two cursors on one screen so I can truely multitask?

Just a thought.

---

### Post by Bandit on 2006-03-07
Damn good question... I have never tried it before..
If it works like a touchpad and mouse on the same machine. Both will just control on single mouse courser..
Cheers,
Joey

---

### Post by lolocaust on 2006-03-07
I've tried a ps/2 mouse and a usb mouse in windows; both controlled the same cursor, and if Bandit's correct about the trackpad & mouse, I guess it would be the same with two mice in ubuntu.

---

### Post by red_Marvin on 2006-03-07
Since, to my knowledge, almost any api existent today can only have one widget
focused at a time, so two cursors would just inactivate each other's active windows.

---

### Post by stuporglue on 2006-03-07
My guess is that if you could get them to show up as two different devices, you could do it. 

From the xorg.conf: 

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

If one mouse showed up as /dev/input/mice and the other as /dev/input/mice2, you might be able to add a new "Section InputDevice2" to xorg.conf and have it work. 

If you can't get two separate devices in the first place, I don't think there's a chance.

---

### Post by aysiu on 2006-03-07
I have two mice, and they control the same cursor.

I don't see how having two separate mouse cursors would *help* you multi-task. If anything, it would make things more confusing.

For me the advantage of having two mice is using the left hand or right hand as suits my fancy (I'm not really ambidextrous, but I am when it comes to computer mice).

---

### Post by Bragador on 2006-03-07
Haha I was actually thinking about that last week.

Having two cursors would actualy be great. It would feel more natural when you control your applications. Also the desktops could be improved as to be more "real".

I think it would be especially useful for 3d graphics since the artist could hold and move one object while moving the light source at the same time.

Could be great for games too. two 12 buttons mice could be the next way of playing 3d games. Imagine using to control the driving device and the other mouse to push buttons and manipulate your gun. 

It would be the next step before virtual gloves I think.

---

### Post by Perfect Storm on 2006-03-07
Right hand on the mouse and left on the keyboard to write that is what I find easist.
2 mouse = click feast? Surely instead of damage in one arm of countless times with a mouse it's now possible to get both arms damaged :P

---

### Post by IYY on 2006-03-07
Even one mouse is too much. The key to true efficiency is learning how to use the keyboard properly.

---

### Post by DigitalDuality on 2006-03-07
well you go ahead and use your keyboard.

i'll copy/paste thank you very much.

---

### Post by YourSurrogateGod on 2006-03-07
Having two mice would be a disaster if you think about it.

Lets say you have 2 apps running and both of those apps have a text box of some sort. Each mouse clicks its own app in order to get it into focus and you start typing. The question here is, how would the OS know to which text box the characters go to? It doesn't. That's the problem.

Ahh... you might say now, well, what if you have 2 keyboards as well, so that one would input stuff to the same area as the first mouse and such? In that case, you might as well have a terminal set up where each person logs into their account. That way, sanity can be preserved.

---

### Post by xequence on 2006-03-07
[QUOTE=DigitalDuality]well you go ahead and use your keyboard.

i'll copy/paste thank you very much.[/QUOTE]

So CTRL + C and CTRL + V isnt using a keyboard?

---

### Post by Bragador on 2006-03-07
[QUOTE=YourSurrogateGod]Having two mice would be a disaster if you think about it.

Lets say you have 2 apps running and both of those apps have a text box of some sort. Each mouse clicks its own app in order to get it into focus and you start typing. The question here is, how would the OS know to which text box the characters go to? It doesn't. That's the problem.

Ahh... you might say now, well, what if you have 2 keyboards as well, so that one would input stuff to the same area as the first mouse and such? In that case, you might as well have a terminal set up where each person logs into their account. That way, sanity can be preserved.[/QUOTE]

OS will have to implement the two mice eventually in one way or another because when we will be using our hands to manipulate virtual desktops it will come to that.

---

### Post by gord on 2006-03-07
when input devices were being developed (70's or so), the idea of two mice came but it was found that it was incredibly hard to use and was very counter productive. thus we resolved to using one.

---

### Post by aerials on 2006-03-07
There was just something similar on gizmodo:
[http://www.gizmodo.com/gadgets/peripherals/digital-cowboy-dctpm1-dualpointer-mouse-solution-in-search-of-a-problem-158929.php](http://www.gizmodo.com/gadgets/peripherals/digital-cowboy-dctpm1-dualpointer-mouse-solution-in-search-of-a-problem-158929.php)

But there you have one mouse and two pointers, between which you can switch via a mouse button. But since it seems to be done in the driver, it won't work with linux. 

I guess this would be quite useful on a dual monitor layout, altough I have my mouse pointer acceleration on such a high level that I can move it from one corner to the other with just a wink of my eye ;)

---

### Post by briancurtin on 2006-03-07
[QUOTE=IYY]Even one mouse is too much. The key to true efficiency is learning how to use the keyboard properly.[/QUOTE]
bingo

[QUOTE=DigitalDuality]well you go ahead and use your keyboard.

i'll copy/paste thank you very much.[/QUOTE]
youre welcome. ill continue to use my faster and more efficient keyboard shortcuts long past the time where you need to take breaks every 20 minutes and wear a wrist brace since your wrists are in pain.

---

### Post by aysiu on 2006-03-07
Mouse = inefficient.

Even my wife, who's a graphic design, had to get a Wacom tablet because the pen made more sense to her than a mouse.

I prefer the keyboard--it's precise, faster, and better for my wrists. I can copy, paste, switch apps, shut down the computer, launch applications, close tabs... do just about everything faster than I can with a mouse. 

Very seldom do I use the mouse--mainly for web browsing, as the Mouseless Browsing Extension in Firefox made pages take too long to render (especially in the Ubuntu Forums), as every single link had to have a number next to it.

---

### Post by Orunitia on 2006-03-07
[QUOTE=briancurtin]the time where you need to take breaks every 20 minutes and wear a wrist brace since your wrists are in pain.[/QUOTE]


Sorry but my wrists don't hurt every 20 minutes after using a mouse. In fact, my wrists never hurt after using a mouse, and I'm on the computer a lot.

---

### Post by gord on 2006-03-07
give it a few years Orunitia

---

### Post by aysiu on 2006-03-07
[QUOTE=Orunitia]Sorry but my wrists don't hurt every 20 minutes after using a mouse. In fact, my wrists never hurt after using a mouse, and I'm on the computer a lot.[/QUOTE] You must have some ergonomic setup then. My wrist hurts if I use the mouse too much.

---

### Post by Orunitia on 2006-03-07
[QUOTE=aysiu]You must have some ergonomic setup then. My wrist hurts if I use the mouse too much.[/QUOTE]

Nope, I just have a microsoft optical mouse sitting on a flat desk, and I use it several hours a day.

---

### Post by bonzodog on 2006-03-07
It won't be long before flat screen touch sensitive LCD's are around, so you just use your fingers to manipulate the interface, and I hope that the computer interface from 'Minority Report' makes it to market one day soon...The US military are already working on a similar system:
[http://www.newscientist.com/article.ns?id=dn7271](http://www.newscientist.com/article.ns?id=dn7271)

---

### Post by Kvark on 2006-03-07
[QUOTE=cyberb0b]I have two eyes.

I have two hands.

I have two USB mice.

I have two mission-critical applications running, firefox and klickety.

Can I have two cursors on one screen so I can truely multitask?

Just a thought.[/QUOTE]
Multitasking is about switching the focus of both your mental concentration and your input devices back and fourth between windows quickly. You can't concentrate at 2 different thoughts at once even if you had 2 mouse pointers. The best you can do is switch your concentration quickly back and fourth between the tasks and then you might just as well switch the pointer back and fourth too.

[QUOTE=Bragador]OS will have to implement the two mice eventually in one way or another because when we will be using our hands to manipulate virtual desktops it will come to that.[/QUOTE]
[QUOTE=bonzodog]It won't be long before flat screen touch sensitive LCD's are around, so you just use your fingers to manipulate the interface, and I hope that the computer interface from 'Minority Report' makes it to market one day soon...The US military are already working on a similar system:
[http://www.newscientist.com/article.ns?id=dn7271](http://www.newscientist.com/article.ns?id=dn7271)[/QUOTE]
When you use a keyboard, touchpad or trackball only your fingers are moving. Even when you use a mouse, pen, joystick or steering wheel your hands have something to rest their weigth on.

If you would be sitting there waving your hands in front of you making strange gestures with virtual gloves or poking your screen until it's all greasy then your hands would have nothing but thin air to support their weight on. It would feel great the first 5 minutes but after an 8 hour workday at the 'Minority Report' office I think you'd be very tried from holding your arms up in the air without anything to support their weight on.

A less triesome future scenario would perhaps be to control the mouse pointer and type text directly without relaying through hand or finger motions. Some entirely paralyzed patients already do this but it's still far too slow to compete with a mouse and keyboard yet.

---

### Post by cyberb0b on 2006-03-08
I never said using two mice would be efficient.  It would just be a cool thing to play with.

Especially with dual-monitors.

Or a multiplayer game where both people use one of the mice at the same time.  Maybe a shooter similar to Time Crisis for the PS2 [http://www.thunderboltgames.com/reviews/ps2/timecrisis3_3.jpg](http://www.thunderboltgames.com/reviews/ps2/timecrisis3_3.jpg)

---

### Post by mcduck on 2006-03-08
Uhh. I often have two computers running on my desk (so there's 2 mice an 2 keyboards). Whatever I do, I always grab the wrong mouse/kb first, then spend couple of seconds wondering why nothing happens and finally realise that I'm controlling the wrong computer. Not very efficient :D

Anyway, I prefer keyboard. It's the fastest way, and easier on my right wrist (that is in pretty bad shape after all the years between DOS 6 and Ubuntu when I had no proper CLI. And certain accident including snowboard, big jump and finding out in the air that there's no snow on the landing.. :rolleyes:  )

---

### Post by poofyhairguy on 2006-03-08
My head just exploded.

---

### Post by Bragador on 2006-03-08
[QUOTE=Kvark]If you would be sitting there waving your hands in front of you making strange gestures with virtual gloves or poking your screen until it's all greasy then your hands would have nothing but thin air to support their weight on. It would feel great the first 5 minutes but after an 8 hour workday at the 'Minority Report' office I think you'd be very tried from holding your arms up in the air without anything to support their weight on.[/QUOTE]

It depends of the settings. If you move your hands while putting your forearms on your thighs or a desk there is no problem.

---

### Post by Perfect Storm on 2006-03-08
Not to mention if you like to eat while on your PC. The screen will be messy :mrgreen:

---

### Post by JackDog on 2006-03-08
I know you can have two separate desktops with their own keyboard and mouse setup. Basically giving you the ability to share a single system with two people. Its actually not a bad idea...

Instead of spending $1k for an office developer workstation (not including monitor/keyboard/mouse),  Spend $2k.  Get a VT dual or quad processor machine with 4GB of RAM and a raid5 array. Place a USB dock under each monitor and run Xen. Add a second video card and map one to each virtual machine. Two machines in one. Since both developers will rarely compile at the same time, they can benefit from the extra resources available when they need them. Kind of like terminal services, but without the insanity? :twisted:

---

### Post by shiona on 2006-09-23
Somewhere i came across an lib which accepted two mice and was able to read all button states and two locations. We just need someone to hack x.org to work with it and then a wm to support two cursors :D
BTW I've been thinking that for about 8 years now, ever since I first played settlers 2 multiplayer.

---

### Post by NoTiG on 2006-09-23
In minority report Tom cruise uses both hands to control the interface.... like conductors sticks though not mice

---

### Post by RAV TUX on 2006-09-23
I have actually used two usb mice at once.

---

### Post by bobbybobington on 2006-09-24
i remember seeing a video of a linux desktop (modified x?)that supports two users at the same time. hopefully ill find the link

---

### Post by xhaan on 2006-09-24
> **mcduck said:**
> Uhh. I often have two computers running on my desk (so there's 2 mice an 2 keyboards). Whatever I do, I always grab the wrong mouse/kb first, then spend couple of seconds wondering why nothing happens and finally realise that I'm controlling the wrong computer. Not very efficient :D

Anyway, I prefer keyboard. It's the fastest way, and easier on my right wrist (that is in pretty bad shape after all the years between DOS 6 and Ubuntu when I had no proper CLI. And certain accident including snowboard, big jump and finding out in the air that there's no snow on the landing.. :rolleyes:  )

Sounds like you need a KVM switch. :D 
I too would rather use a keyboard, but it can be hard to make myself do it becuase I'm so used to gaming with a mouse...

Also, in this one game I remember there was a guy who supposedly used two mice somehow to cheat and control two different characters at the same time...

---

### Post by djsroknrol on 2006-09-24
Xserver will allow for multiple instances of desktops which could have multiple (up to 8 I believe) keyboards and mice, but not in the same instance or desktop.
A simple xorg.conf rewrite does the trick...I'm in the middle of a 4 seat, multi-head project right now...

---

### Post by NiceGuy on 2006-09-24
> **Orunitia said:**
> Sorry but my wrists don't hurt every 20 minutes after using a mouse. In fact, my wrists never hurt after using a mouse, and I'm on the computer a lot.
Your not alone with that, I've spent excessive amounts of time everyday on a pc since I was about 9 and I haven't had any problems with my wrists yet - touch wood (that's over 13 years if your interested). Back problems? Yes, and I went through a stage of bad headaches, but no problems with my wrists, although the skin on my hand (where it touches the desk) is extremely smooth :-? 

> **djsroknrol said:**
> Xserver will allow for multiple instances of desktops which could have multiple (up to 8 I believe) keyboards and mice, but not in the same instance or desktop.
A simple xorg.conf rewrite does the trick...I'm in the middle of a 4 seat, multi-head project right now...

So just for clarification, are you saying you are setup to, for example, have two different users logged in and working on the same machine using separate screens, keyboards and mice at the same time, ie. for all intents and purposes it would be like 2 machines in one? If that's correct could you please post your/an example xorg.conf because that is exactly the setup a friend of mine is trying to achieve.

Many thanks!

---

### Post by BoyOfDestiny on 2006-09-24
Sorry if I'm repeating something in thread, I didn't comb through all the posts:

Manymouse, noticed it when launching zsnes from commandline

[http://www.icculus.org/manymouse/](http://www.icculus.org/manymouse/)

From the page though...

"Support for X11 XInput is planned, but is still unimplemented"

So there are ways for your app to offer support for multiple mice, I have no idea if it's the default (I've never even tested multiple mice, just aware of manymouse...)

As for ergonomics, I cannot tell you how much I like a mouse pad with a big gel wrist rest.

---

### Post by djsroknrol on 2006-09-24
>  So just for clarification, are you saying you are setup to, for example, have two different users logged in and working on the same machine using separate screens, keyboards and mice at the same time, ie. for all intents and purposes it would be like 2 machines in one? If that's correct could you please post your/an example xorg.conf because that is exactly the setup a friend of mine is trying to achieve.

Many thanks!

Yes, that's right....I don't have access to xorg.conf file at this time, as the machine is not running currently, but I followed Chris Tyler's blog notes here:
 [http://blog.chris.tylers.info/index.php?/archives/14-Multiseat-X-Under-X11R6.97.0.html#extended]("http://blog.chris.tylers.info/index.php?/archives/14-Multiseat-X-Under-X11R6.97.0.html#extended")

There was also a discussion on this same subject in the desktop section here:

[http://ubuntuforums.org/showthread.php?t=160969]("http://ubuntuforums.org/showthread.php?t=160969")

The one I'm working on is for a kiosk type of info desk. It's 4 headed and uses the ps/2 keyboard and mouse for one head and a usb hub connecting the other 3 sets of usb keyboards and mice, with 4 pci video cards..it's been something I've pieced together from spare parts and work on here and there where time permits....I hope this helps you...

---

### Post by NiceGuy on 2006-09-25
Many thanks djsroknrol, I'll pass the info on to my friend - although I'll probably endup doing the work. He is a bit of a windows fan who I'm trying to convert (well maybe not convert - more make him aware of other options). This will probably be one to chalk up on the linux can do/ windows can't list!
Now if we could only get Sims 2 working on linux (for his wife) then we might be on to something!

---

### Post by djsroknrol on 2006-09-25
> **NiceGuy said:**
> Many thanks djsroknrol, I'll pass the info on to my friend - although I'll probably endup doing the work. He is a bit of a windows fan who I'm trying to convert (well maybe not convert - more make him aware of other options). This will probably be one to chalk up on the linux can do/ windows can't list!
Now if we could only get Sims 2 working on linux (for his wife) then we might be on to something!

I miss Sims 2 as well....but I can do without it as long as I'm getting my work done...;)

---

### Post by pelle.k on 2006-09-25
> Since, to my knowledge, almost any api existent today can only have one widget
focused at a time, so two cursors would just inactivate each other's active windows.
 That is really _too_ bad. Developers should really implement such features _now_. We already have 15" touch screens at decent prices.

> I don't see how having two separate mouse cursors would help you multi-task. If anything, it would make things more confusing.
Maybe two regular mice would be, but not two hands. we do it all the time.
Move two windows at a time. control brush size width while painting a stroke in some gfx program, moving two troups at once in a strategy game etc etc wouldn't be awkward any longer :)

> OS will have to implement the two mice eventually in one way or another because when we will be using our hands to manipulate virtual desktops it will come to that. Yeah, i saw this sci-fi movie where this guy was in front of a _large_ widescreen lcd (or such), almost like a real table where he controlled everything with his two hands of course, resizing windows, pressing buttons etc, and it all looked so smooth. I really feel handicaped by my mouse most of the time. I love keyboard shortcuts, but thats only for "clicking" actions.

> You can't concentrate at 2 different thoughts at once even if you had 2 mouse pointers. The best you can do is switch your concentration quickly back and fourth between the tasks and then you might just as well switch the pointer back and fourth too. Thats where you are wrong. According to studies in NLP the average human can hold 7 plus or minus 2 chunks of information in our conscious thinking at any one time. Even far more with "automotive" training, like when driving a car for example.

> It depends of the settings. If you move your hands while putting your forearms on your thighs or a desk there is no problem
Thankyou.

> In minority report Tom cruise uses both hands to control the interface.... like conductors sticks though not mice :)

---

### Post by qalimas on 2006-09-25
> **mcduck said:**
> Uhh. I often have two computers running on my desk (so there's 2 mice an 2 keyboards). Whatever I do, I always grab the wrong mouse/kb first, then spend couple of seconds wondering why nothing happens and finally realise that I'm controlling the wrong computer. Not very efficient :D

Anyway, I prefer keyboard. It's the fastest way, and easier on my right wrist (that is in pretty bad shape after all the years between DOS 6 and Ubuntu when I had no proper CLI. And certain accident including snowboard, big jump and finding out in the air that there's no snow on the landing.. :rolleyes:  )

I'm not suer if this was commented on in the rest of the thread, as I stopped on your post just to reply so I wouldnt forget ;)  But you should look into an application called Synergy, it's a really useful little tool.  There is a howpto on setting it up in the how-to area.  It won't take you more than... 3 minutes, tops ;)

---

### Post by v8YKxgHe on 2006-09-25
What would be the advantage of 2 cursors?!

> I have two eyes.

I have two hands.

I have two USB mice.

Yet only 1 brain. How would you control 2 mice/cursors to do different things at the same time?

Edit: Or have I got the wrong idea? do you mean for the same PC? :-D ](*,)

---

### Post by alecjw on 2006-09-26
Somone said that the 2 cursors would just keep selecting each other eg in menus. Sureley, then there should be one dominant one. If 2 things are being selected, one with each mouse, the dominant mouse should select. To distinguish between the two, the dominant one shouold be larger and one colour (blue?) and the other should be smaller and a different colour (red?)

---

### Post by theDaveTheRave on 2008-04-20
I was wondering this myself just today.

I use a laptop with a funny multidirectional square centre keypad (bit like on modern mobiles) that is great for navigating back and forth between pages on the net.

I have a second trackball (no problematic wrist ache as only my thumb moves around on the ball) plugged into a usb port (most of the time!).

I use the buttons on both the toucpad and the external mouse for selecting / scrolling etc.

Maybee I could set the touchpad to only switch between virtual desktops and the external mouse buttons as normal ones?

do you think that may be possible??

Anyway having 2 mice is more efficient most of the time (the scroll button on the mouse is great), 

I guess the problem would be getting the config to notice when there was an extra mouse plugged into the USB and to change.

Anyway it did seem like a good idea to have 2 mice and pointers, but after a little thought, probably not!

Dave

---

### Post by klange on 2008-04-20
Interesting bump. I suggest that anyone still wondering about this (seeing as how the topic was from '06) read about [MPX](http://en.wikipedia.org/wiki/MPX). [(Or look at their own site)](http://wearables.unisa.edu.au/mpx/).

---

### Post by ssam on 2008-04-20
you want Multi-pointer X Server
[http://en.wikipedia.org/wiki/MPX](http://en.wikipedia.org/wiki/MPX)

"Inclusion of MPX into X.Org is likely with X11R7.5, which will follow X11R7.4 at an unspecified date"

--
i must be slow today :-)

---

### Post by pelle.k on 2008-04-20
MPX is still scheduled for inclusion. Probably in xorg server 1.5 or 1.6.

---

### Post by Frak on 2008-04-20
> **DigitalDuality said:**
> well you go ahead and use your keyboard.

i'll copy/paste thank you very much.
Shift + arrow keys to select text.
Ctrl + C to copy, Ctrl + V to paste.
Shift + Insert to paste into console.

---

### Post by LaRoza on 2008-04-20
[img]http://img181.imageshack.us/img181/8060/necromancingsv7.jpg[/img]

---

