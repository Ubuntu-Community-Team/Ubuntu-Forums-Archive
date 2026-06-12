---
title: "Idea for a new interface..."
date: 2011-06-02
forum: The Cafe
---

### Post by Ghost|BTFH on 2011-06-02
I've been wondering where to post this and someone suggested the Cafe for it, so here I am.

First, let me say I have no programming experience or amazing skills other than the fact I've been using Linux for ages and I'm a computer repair tech by trade.

With that in mind, I've had this idea that just won't let go of me so I have decided to share it with the community in hopes some brilliant programmer(s) will see it, love it and run with it.

Let me make this clear - I want you to take this idea and do whatever you want with it.  If it's a great idea, fine - consider it my tiny contribution to the community.  If it's not great, well...maybe the community can shape it into something amazing.

The bottom line is, the direction of desktops currently in Linux is taking a rather depressing turn and I'm hoping to breathe a little new life into it with an idea that (I hope) is fresh and exciting...so, here it goes:

A hive-style tile set of icons covering the desktop (or in part).

Each tile has six sides...when depressed, the tile explodes (raises up), enlarges and then displays six more tiles around it, with more options.

For example, you have a tile marked "Office" and you depress it.

Now "Office" is enlarged as the primary focus on the screen and six more tiles surround it, "Calc" "Impress" "Draw" "Math" "Writer" and "Dictionary"

Any of which may now be touched (clicked) to bring up said program.

My idea for minimizing/maximizing items is to utilize the standard program title bars and X [] _ buttons. However, minimizing would shrink the program into the TILE it came from, making the root tile (in the above example, "Office") glow. Touching the root tile would bring up the other tiles, with the one active and minimized, glowing. Touching that one would then show mini-tile windows of each process of the program running (Think Windows Preview in Hex format).  Clicking on the central tile would then load another clone of the program.  (Example:  "Internet" tile is clicked, then "Firefox".  Later, bringing up "Internet" and "Firefox" would show an additional tile showing one Firefox process up and running.  This would be displayed around the central "Firefox" tile.  If the "Firefox" tile is pressed again, a second Firefox process would be loaded and so on)

I think the concept may be challenging (especially when you add into it the idea of 3D, a ball of hex tiles that can be shrunk down out of the way when not in use, etc) but I think the effect and the flexibility allowed the user (considering each tile could be a shortcut OR a menu+sub-menus) would be well worth it.

Basically, it would allow a user to either dump all shortcuts into the hive, custom sort them into groups, or into sub-groups, utilizing as little or as much space as they desired, dependent upon their personal preferences.

With a setup like this, for example, I would toss all the important daily programs I use as individual tile-shortcuts. The rest of them, I would set up in an array of menu groupings with no sub-menus (I personally hate sub-menus).  Someone else however might love the idea of their entire system broken down into a single root menu + sub-menus galore.

I was also considering utilizing the tiles as placeholders for widgets as well.  You could, for example, utilize a tile for your weather.  A click on it would bring up an enlarged tile showing more detail, or perhaps a ring of tiles, with a brief day by day forecast, etc.  Clicking on the enlarged tile would then take the person to their preferred weather app/website/etc.

For menus requiring more than six places, I could see the hive tiles growing more tiles as needed. ergo, instead of six tiles around the center one, it would have those six plus more added onto the base six, expanding outward in a ring. If this sounds confusing, I can always try to draw a mock-up of what I'm trying to explain.

So, what do you guys think? Crazy? Genius? Waste of bandwidth?

Please, discuss!

Cheers,
Ghost|BTFH

---

### Post by Noz3001 on 2011-06-02
It sounds a bit like the recently announced Windows 8 interface, but slightly better. Sounds good. I might have a go at implementing this at some point ;D

---

### Post by Joe of loath on 2011-06-02
People won't like it. Why? Because when it comes out, people will be making up excuses about why it's crap, and why we should all keep on using Unity/Gnome 3 for ever.

On a more serious note, it does seem interesting. I can't visualise it, but from what I can imagine it sounds good.

---

### Post by Noz3001 on 2011-06-02
> **Joe of loath said:**
> People won't like it. Why? Because when it comes out, people will be making up excuses about why it's crap, and why we should all keep on using Unity/Gnome 3 for ever.

On a more serious note, it does seem interesting. I can't visualise it, but from what I can imagine it sounds good.

Those people who want to worship one environment can just go back to Mac or Windows if they only want to moan about having more than one option ;D

---

### Post by Copper Bezel on 2011-06-02
> It sounds a bit like the recently announced Windows 8 interface, but slightly better. 

My thought as well. Yeah, I kind of want to see a mockup of this to get a sense of how it would work.

I do think that the sub-menus could draw on what's been done with quicklists or jumplists. I'm a DockBarX fanboy, myself, and I wouldn't know how to go back to not having recent documents per application and media controls in my dock icons, but I think that could be taken further with things like, say, the menus that indicator applets present.

---

### Post by Ghost|BTFH on 2011-06-03
Okay, I'm not the greatest graphic artist in the world (especially at 8am) but here's a very rough basic concept design for what I have in mind - I'm sure it could be made much more elegant than this. :)

I'm also thinking that right clicking on an object would give you other options as well, just as it does in most OSes.

Another idea was using a mouse bump on the edge of a screen to bring up the "hive" to get quick access to all files, etc.

If you guys want a larger image, let me know and I'll host the original file on my website.

Cheers,
Ghost|BTFH

---

### Post by mehaga on 2011-06-03
I had almost the exact same idea a year or two ago. I beat you, that's all I had to say, bb.

Ok, seriously... I don't remember the details, but I do remember that, instead of your hive and hexagons, I was thinking about using a shape that has as many sides as the item it represents has sub-items. You can see how it got complicated at the very beginning... :) 
What's your solution, you get max 6 items/sub-categories per category and that's that? Also, I realise the pic you posted is just a sketch, but I wouldn't like all the items displayed at all times, I'd rather just see the current set, and have a way of getting back to its parent (probably by keeping the parent in the middle, as on your drawing...) I love the idea, I hope someone finds time to implement it.

---

### Post by Merk42 on 2011-06-03
What if a submenu has more than 6 items?
If I have an application launched that is obscuring the hive, how do I launch another/manage open windows?

---

### Post by mehaga on 2011-06-03
> **Merk42 said:**
> If I have an application launched that is obscuring the hive, how do I launch another/manage open windows?
You'd have to have be able to launch it with a keyboard shortcut, mouse click/gesture... WinKey? :)

---

### Post by Ghost|BTFH on 2011-06-03
Here's a mockup of how to handle menus greater than six items...as you can see, the hive simply grows to accommodate whatever is needed.  The other one shows how sub-menus could be handled in a layered effect.

Note, by adding a single additional layer, up to 18 menu items can be offered in this way while still allowing a very smooth and simple interface that can still be read easily.

The sub-menus are ugly, in my opinion, although that may very well come from my dislike for sub-menus in general.  I did try to make them as non-ugly as possible without going through the hassle of massively re-coloring everything (Which would definitely be a fantastic feature if all lower level menus were grayed out in some fashion I believe).

It would also be possible to implement it in such a way that the entire SCREEN would be lightly grayed out with the exception of the objects in the top layer - thus providing ease of view AND an obvious area to click on to simply collapse the whole menu system (if the user accidentally clicked on a menu object, for example).

Also, I absolutely agree with utilizing a keyboard shortcut for bringing the "hive" forward of any window, or utilizing a mouse gesture to do the same.  I think it would be an exceptional way of elegantly being able to bring forth a object system without having to switch screens, desktops, changing sizes, moving windows or anything else.  I think this is the most inelegant utility in the current desktop concept - the user MUST go to the menu system.

In this model, the "hive" serves the queen/king (user) and therefore comes to THEM when summoned. :)

~Ghost|BTFH

---

### Post by BrokenKingpin on 2011-06-03
I think the idea is sort of cool, I just do not get what it really gives the user. A standard Applications menu supports any type of hierarchy you want, and is very easy to navigate and use... this would make it more time consuming to navigate applications.

I think KDE actually has the best design for a desktop right now (just maybe not the best implementation at this point). The desktop is very modularized, where you can have any number of widgets and panels to plug into the desktop, customizing it any way you want. So to add new functionality to the desktop is just a matter of creating a new widget or panel type and then you can just add it to the desktop.

One thing that sort of proves this concept in KDE is that you can switch from the traditional desktop layout (single panel) to a netbook interface with changing one simple setting, completely transforming the desktop of the fly. I am not saying KDE is perfect, but I really like the architecture of the desktop.

---

### Post by aaaantoine on 2011-06-03
> **vekaz said:**
> You'd have to have be able to launch it with a keyboard shortcut, mouse click/gesture... WinKey? :)

So basically, (it sounds like) the hex grid would replace Gnome Shell's dashboard.

In light of Gnome Shell's interface proving to actually be somewhat useful, this is not a bad idea.

---

### Post by Ghost|BTFH on 2011-06-03
Yes, this could absolutely be incorporated into what we currently have or be redesigned to become a new desktop environment.  As little or as much work/design and creativity as desired.

As for what the user gets out of this...number one on the list is versatility.  Every menu, every object, every icon can be custom set into a tile of their choosing.  If I want 20 program shortcuts, a menu with 15 sub menus and iconic widgets all piled into a neatly interlinking hive, I can.  If I want to change that around, I can.  That's the whole idea behind this.

The interface gives a user a faster, more direct and "in your face" menu system.  Literally, it leaps into the center of your screen as opposed to having to move your mouse and eyes over to wherever the menu is stuck at.

Once a user organized it the way they wanted, they would know, for example, where all their multimedia objects are, where their weather and clock objects are, their news ticker, the web browser, email, etc etc etc.

I could even see super tiles being utilized - I use Firefox, Thunderbird, Banshee and Pidgin all the time.  Fine, I have one tile that's set with those icons all added into it.  With a special command, like a double click instead of single click - it would instantly give the command to open EACH OF THOSE ITEMS instead of just going through and grabbing one with each click after navigating the menus.

The options for this idea are limited only by our brilliant community.

Cheers,
Ghost|BTFH

---

### Post by Sui Nim Tao on 2011-06-03
So how does this fit together then....... we push the windows key and the hex grid fades onto screen, could we have mouse gestures to help pick tiles...... slide up and tap, slide down and tap to select etc... or maybe the mouse scroll made the highlighted hex go round the inner hex clockwise and so on highlighting each one as you scroll....

If you had this fade in with transparency so you could see the desktop or open apps in the background, this would look nice.

It sort of reminds me a bit of star trek when they click on stuff and it zooms forward.

So how could you introduce window switching in there, don't want yet another interface without the ability to see open windows ;)

Paul

---

### Post by Ghost|BTFH on 2011-06-03
> **Sui Nim Tao said:**
> So how could you introduce window switching in there, don't want yet another interface without the ability to see open windows ;)

Paul

I agree with you - we wouldn't want yet another interface that hinders the user.  I was contemplating the combination of being able to fade in the interface added with the ability to see the ones active by having them glow (could also have them group together in a cluster at the center) and be able to just click on and jump from one application/window to another.  For instance, 2 versions of firefox open, for a quick switch, you could alt-tab or use a mouse gesture to bring up the hive, click the location of Firefox, then click on the instance running that you want to switch to.

The idea isn't polished obviously, but this was the rough idea I had.  If anyone has a more elegant method to suggest - I'm all ears. :)

And yes, after years of Star Trek and Sci-Fi in general, something just clicked in my brain (this would be several months ago) and it's been rolling around creating this since then.  I would love a modern, slick interface like this and I think there are a lot of users who'd enjoy it as well.

My mockups do it no justice to what I see in my mind's eye.

Cheers,
Ghost|BTFH

---

### Post by Dustin2128 on 2011-06-03
It sounds weird, but I feel like this concept is familiar. It'd be awesome on a touch screen but I don't think the interface would translate well to a mouse/keyboard. Maybe an android interface? It'd be fitting with android 3.0 being called honeycomb. I might be interested in helping work on something like this actually.

---

### Post by athenroy on 2011-06-03
I'd like to see it working, it does sound interesting.  Even if someone just came up with one cell for a demo, say for LibreOffice or Open Office.  Trying to remember if I saw something similar in maybe E17?

---

### Post by Ghost|BTFH on 2011-06-03
Sadly, I have zero programming skills, but I would love to see this happen.  I would be a happy and willing tester/manager/cheerleader/innocent bystander/pizza delivery guy for this endeavor. :)

---

### Post by Dustin2128 on 2011-06-03
> **Ghost|BTFH said:**
> Sadly, I have zero programming skills, but I would love to see this happen.  I would be a happy and willing tester/manager/cheerleader/innocent bystander/pizza delivery guy for this endeavor. :)
Hm... payment for my time would be approximately 24 Pepperoni Pizzas, which I use to supplement the dollar and euro as a delicious medium of exchange. Having nothing pressing in my schedule though, and having a clear idea of this interface's looks and functionality.... I'll play around with the concept of it as a compiz plugin maybe. For some reason android uses java for the UI with which I have no experience, plus I have no tablet sized devices to experiment with (for which I think this would be the ideal interface).

---

### Post by mehaga on 2011-06-03
For now, I can only try to help you with developing the idea further. 

If there are more than 6 items, you could show 6 and hide the remaining, only showing that there's more (somehow, perhaps a tiny arrow or something...). Then, you allow the user to 'rotate' the items around the parent item, hiding the first item and showing the next one... 

Here's an idea about navigation (before someone asks whether we would still use/need keyboard :p) 

You could navigate the hive via numpad. Use numpad buttons to point to the direction of the item you want to select. Two numbers that don't point to a side could be used for rotation. Middle key for 'back' (middle - parent category... am I over-explaining this? :)). 

I don't know how practical that would be for our fingers, but to me it sounds logical and natural, so there would be virtually no learning curve... This whole hive thing feels more natural than 'mousing' through a complex menu (and the horror of misclicking when you're three levels deep, and have to repeat all the pointing and clicking...)

Bravo, Ghost :)

---

### Post by DangerOnTheRanger on 2011-06-03
Sounds cool. :)
Now, I could help (albeit intermittently) with programming. Maybe a quick window manager, that someone else will have to test in a VM for me :D

But seriously, this sounds like a good idea, and I'm willing to lend my programming expertise to help out.

---

### Post by Dustin2128 on 2011-06-03
I can't decouple this from a touch screen in my mind. A good interface idea I thought of is to have it calibrate to the size of the user's hand so that each honeycomb comes up under a finger to speed up reaction time, but maybe I'm just throwing out ideas at random to see if any of them stick.

---

### Post by ClientAlive on 2011-06-03
> **Ghost|BTFH said:**
> Okay, I'm not the greatest graphic artist in the world (especially at 8am) but here's a very rough basic concept design for what I have in mind - I'm sure it could be made much more elegant than this. :)

I'm also thinking that right clicking on an object would give you other options as well, just as it does in most OSes.

Another idea was using a mouse bump on the edge of a screen to bring up the "hive" to get quick access to all files, etc.

If you guys want a larger image, let me know and I'll host the original file on my website.

Cheers,
Ghost|BTFH


Perhaps compiz fusion itself could be a foundation for implementing something like that. They already have the desktop cube and 3d effects and it is something that works by other's contributions. A person might be able to take a couple already existing things, fuse them together and add to it/ put finishing touches and get what you are describing. For example - compiz + some existing desktop environment + tweaking. Work with their source codes to strip out the parts that are useful and combine those parts into one then add to and tweak that to perfection.

I also had an idea of the nature yours is but I won't put it in here cause that would be rude.

:)

---

### Post by Dustin2128 on 2011-06-03
I don't think it's quite the same as your idea, but look at some of UDE's stuff: Maybe you could borrow some ideas.
[IMG]http://upload.wikimedia.org/wikipedia/commons/5/54/UDE_Honeycomb.png[/IMG]
[https://secure.wikimedia.org/wikipedia/en/wiki/UDE](https://secure.wikimedia.org/wikipedia/en/wiki/UDE)

---

### Post by ClientAlive on 2011-06-03
> **Dustin2128 said:**
> I can't decouple this from a touch screen in my mind. A good interface idea I thought of is to have it calibrate to the size of the user's hand so that each honeycomb comes up under a finger to speed up reaction time, but maybe I'm just throwing out ideas at random to see if any of them stick.


No, not the same at all. Just in the same category. Really cool what you thought of though.

:D


> **Dustin2128 said:**
> I can't decouple this from a touch screen in my mind. A good interface idea I thought of is to have it calibrate to the size of the user's hand so that each honeycomb comes up under a finger to speed up reaction time, but maybe I'm just throwing out ideas at random to see if any of them stick.

  +1 on that

Hey, check this out:

[http://youtu.be/1IshHkcl5_g](http://youtu.be/1IshHkcl5_g)

---

### Post by Ghost|BTFH on 2011-06-04
[QUOTE=Dustin2128]Hm... payment for my time would be approximately 24 Pepperoni Pizzas, which I use to supplement the dollar and euro as a delicious medium of exchange. Having nothing pressing in my schedule though, and having a clear idea of this interface's looks and functionality....[/QUOTE]

Hmmm...I might be willing/able to make a pizza donation sometime in the future over all of this. :)  Maybe we can have a remote pizza party for all involved afterward, via webcam...of course, my will have to be gluten-free. :/

[QUOTE=Dustin2128]I can't decouple this from a touch screen in my mind. A good interface idea I thought of is to have it calibrate to the size of the user's hand so that each honeycomb comes up under a finger to speed up reaction time, but maybe I'm just throwing out ideas at random to see if any of them stick.[/QUOTE]

Yeah, I was originally focused on the whole keyboard and mouse thing (because I use them) although I could see this used for touch, it wasn't until I just read the above that I could see a whole new way of interaction - 1 tile for each finger, thumb covers 2 tiles, center tile is your special key.  It would completely transform typing. :)

[QUOTE=Dustin2128]I don't think it's quite the same as your idea, but look at some of UDE's stuff: Maybe you could borrow some ideas.[/QUOTE]

UDE looks generally like what I'm talking about - albeit VERY primitive and basic in design.  (Kinda like a Windows 3.1 menu system compared to Windows 7)

[QUOTE=vekaz]If there are more than 6 items, you could show 6 and hide the remaining, only showing that there's more (somehow, perhaps a tiny arrow or something...). Then, you allow the user to 'rotate' the items around the parent item, hiding the first item and showing the next one... [/QUOTE]

Well, the ultimate would be utilizing 3D effects (So perhaps compiz would be THE way to go with this project) and perhaps having the next six options on the outer edge, just showing the very bottom of them.  They could then slide into place by simply clicking or clicking and dragging.  Below is yet another ugly little mock-up to give visualization to my ravings.

Eventually, if you guys actually need something at least semi-decent looking, I could attempt to make some .svg work for the icons/tile sets, although I'm sure in this community there are far better artists than I. :)

[QUOTE=ClientAlive]I also had an idea of the nature yours is but I won't put it in here cause that would be rude. :) [/QUOTE]

Go for it!  Perhaps your idea has some parts to it that mine does not that might improve upon it!  In this day and age of everyone screaming "IP VIOLATION!!!" it's good to remember that in our community, we work together - not apart.

I also like your idea of this being utilized via compiz as a simple addition to what is already available.  I think taking an idea like this and adding it to Unity would transform Unity into a high functioning desktop.

[QUOTE=DangerOnTheRanger]Sounds cool.
Now, I could help (albeit intermittently) with programming. Maybe a quick window manager, that someone else will have to test in a VM for me :)

But seriously, this sounds like a good idea, and I'm willing to lend my programming expertise to help out. [/QUOTE]

As a beta tester for many years, I will happily be the Guinna pig for anyone who wants to help out!  Have VMs will travel. :)

Cheers,
Ghost|BTFH

---

### Post by Sui Nim Tao on 2011-06-04
I do kinda like this, I think it would suit well for touch screens, maybe that could also translate to mouse/keyboard, you would defo need gestures though.

I am more of a java/android guy and I have my own open source project called razorCMS (web app), I am currently redoing the interface for the next release, it's a milestone release, I think this kind of idea would translate quite well to the web application side.

I may have a play and see what I can come up with if i can get five minutes spare, this would work quite well with jquery type stuff.

Interesting...... the latest version of gnome, that which I am not going to mention, the interface I believe uses css and javascript. Not sure but could you get jquery in there some how.

Paul

---

### Post by ClientAlive on 2011-06-04
> **Ghost|BTFH said:**
> 
Quote: Originally Posted by vekaz 
If there are more than 6 items, you could show 6 and hide the remaining, only showing that there's more (somehow, perhaps a tiny arrow or something...). Then, you allow the user to 'rotate' the items around the parent item, hiding the first item and showing the next one...

Well, the ultimate would be utilizing 3D effects (So perhaps compiz would be THE way to go with this project) and perhaps having the next six options on the outer edge, just showing the very bottom of them. They could then slide into place by simply clicking or clicking and dragging. Below is yet another ugly little mock-up to give visualization to my ravings.



What if you had it so that when you touch (or click) one of the tiles it flips over like turning a piece of paper over to the other side. It would be on that back side that the facing item is on (if that makes sense) then if you touch/ click it again it flips over again any you have another side to the tile to put the back side item. That would multiply your tiles by 2 and give you 12 active items per. There's a lot of ways you could organize what you put together on the two sides but one way might be to have one side for opening the app and the other for an active window of the app.

To take that even farther - have you ever split a match book cover? :)  Well, anyway. You could also make each tile split like layers as well as flip. Now, with 2 layers on 1 tile you have a grand total of 4 sides when you flip. With 3 layers you have 6 when you flip. and so on. The number of layers wouldn't have to be pre-determined either some of them could be added as new windows are open for that app. And it's just one tile out of many in the whole object.

Another thought is for not just the object made of the tiles to expand based on some user action but for each tile itself to expand based on an other user action. Maybe the layers of the tile slide across the screen like the way the card dealer in vegas slides the deck of cards across the table. Cards have two sides too. :)

Also, from the very start, I keep imagining an overall shape like a soccer ball. How many soccer balls could you fit in a 3d box that is the desktop?

These are just thoughts/ brainstorming with you. Maybe it is a catalyst for further discussion - idk . . .

> **Ghost|BTFH said:**
> 
Quote: Originally Posted by ClientAlive 
I also had an idea of the nature yours is but I won't put it in here cause that would be rude. 

Go for it! Perhaps your idea has some parts to it that mine does not that might improve upon it! In this day and age of everyone screaming "IP VIOLATION!!!" it's good to remember that in our community, we work together - not apart.


Thanks for the encouragement. I have a document saved on my computer that I wrote up about it. Maybe I'll start a thread about it and see if people think it's worth anything.

> **Ghost|BTFH said:**
> 
 I also like your idea of this being utilized via compiz as a simple addition to what is already available. I think taking an idea like this and adding it to Unity would transform Unity into a high functioning desktop.


If I understand what you're getting at by that it would also be an approach. I kind of had a different suggestion in mind though and it might be worth clarifying - I'll let you be the judge of that though.

So I was thinking more of a way of approaching the project. I figured that the a core of the gnu license is that you can use and modify the source all you want. So I got to imagining a project like this using the metaphor of physical objects (like someone might have on the work bench in their garage. So humor me for a minute and lets think of an o/s or a de project like that for a minute.

Say one of the objects on your work bench is compiz and the other is gnome (or some other more suitable de). So you open up your tool box and you grab a screw driver and a wrench and whatever else and you go to work tearing them both apart - maybe not to nuts and bolts but down to the chunks that make up the whole.

Now you have these two objects (compiz and some de) sitting in components on your work bench - one on one end of the table and the other on the other end. You select the main components you need from each and maybe you grab some spare parts or a nut or bolt you need to make them fit together from the shelves you have in the back room where you've kept them.

Now this metaphor might be ok to give a general idea but it fails when it comes to relaying fine quality one could end up with when it comes to software and programming.

Maybe a better metaphor would be one of a geneticist. He takes some genes from this organism and some genes from that one and he produces this awesome mutant freak with super powers and the ability to do all kinds of amazing things.  :)

In a nutshell all I was saying though is to take compiz's rendering ability and some destop environment's management ability and fuse them into one via a text editor; then, via that same text editor, add and tweak and whatever - to perfection. It would eliminate a lot of work on a something that is probably a really big project to begin with. Why not stand on the shoulders of giants. They want you to anyway - they gave you permission to do it in their gnu licenses.

> **Ghost|BTFH said:**
> 
As a beta tester for many years, I will happily be the Guinna pig for anyone who wants to help out! Have VMs will travel. 

 Cheers,
 Ghost|BTFH


I hope this isn't inappropriate but I think you may know where I can find something I've been looking for. It would be a very simple question and an even simpler answer. Would you mind if I pm you about it?

---

### Post by Ghost|BTFH on 2011-06-04
[QUOTE=ClientAlive]I hope this isn't inappropriate but I think you may know where I can find something I've been looking for. It would be a very simple question and an even simpler answer. Would you mind if I pm you about it? [/QUOTE]

Ask your questions gatekeeper, I'm not afraid... :D

As for your ideas, I think they're great - if I knew more about programming, I would say, "Oh sure, that's totally possible..." or "Lawl, no wai"  but as it is, I can only say that I'd love to see the best of the best unified into a project like this.

Compiz effects, a file organization tool that blends the best elements together and of course versatility - this is key to me.  If a user wanted to have the ability to use two sides of a tile - it'd be awesome if they could.  Or have it bloom outward, or have it show the edges of another set and have them morph into main view with a wave of the mouse...whatever they want.

Now about the mouse...I was actually thinking there's an aspect of mice that's not generally utilized - click n' hold.  For example, after selecting a tile, holding the left mouse button down might allow you to then move the menu tiles around to give you more options.  And on the root menu, it could be used to move tiles around to arrange them however you wished.  In a 3D aspect, it could be used to rotate the selections, (think Desktop Cube) etc.  But of course, for the moving of tiles, changing your views, etc...the scroll wheel would also be a simple and viable option to give you all sorts of opportunities.

And may I say, the response to this has been far better than I'd ever hoped.  Perhaps we'll actually see a working prototype here in the future!

Cheers,
Ghost|BTFH

---

### Post by scott-ian on 2011-06-04
The concept is good.  I would make it into a Compiz extension, and try to make it so it does not mess with Unity.  I might be able to help, but probably not.

---

### Post by Dustin2128 on 2011-06-04
For more than 6 options, personally I'd have it to where you kind of flick your wrist on the touch screen to rotate more in, some out. I'd like to develop this with muscle memory in mind though...

---

### Post by Copper Bezel on 2011-06-04
I'll be honest: this seems more like a sci-fi film concept designed to remind the viewer that Tom Cruise is in the future than a UI designed around usability. There's nothing uniquely ergonomic or spatially economic or readable about a set of interlocking hexagons, and the exploded menu that leaves the previous menu visible but inaccessible underneath doesn't really serve any particular function. The application tiles have the functions expected of a dock icon nested inside a Dash-like main menu, but the net effect is that you have a Dash-like menu, but then bury the window management functions for running applications inside it.

I don't actually think that a staggered set of hex tiles is going to have a readability or aesthetic advantage over rows and columns of square ones, and a row already shows associations clearly and doesn't need to be based on the number six. Also, square or rectangular metaphors more directly represent the shape of the windows and, ultimately, the display.

Learn from the competition, here. Windows 8 is to have scrollable screens of application tiles that give visual feedback about their status - like notifications - on the home screen, but then can be manipulated to "become" windows, which then use a tiling metaphor for their window management. The advantage is that nothing ever really has to be represented *by* anything - the application "is" the icon.

Gnome Shell's Shell view makes favorite apps, running apps, and workspaces all immediately available. Open windows on the current workspace are all displayed as previews, rather than icons. That doesn't give you Windows 8's fluidly content-first, icon-free universe, but it does create task management that feels like an open workspace; fan everything out, shuffle through to where you need to go. Drag favorite apps or running windows onto any workspace and indulge the most OCD of organizational compulsions.

The spirit of the week is a UI that gets out of the way and lets the apps take center stage - or rather, all of the stage - and you can see that with even Unity, as well, and its tucking away of panels and the title bar. Apps first, usability first, glitz at a distant fourth.

Windows 8's "Start Screen" and Gnome Shell's "Shell View" both take inspiration from the idea of a "home screen" as it's been innovated and refined by iOS, Android, and other tablet OSs. What you're proposing is a variation on that theme. Don't get too caught up in the gimmick of it - consider ergonomics and usability and think about what your interface could *do* that these other variations can't.

I wouldn't depend on click-and-hold, by the way, as that's tablet language for right-click.

---

### Post by ClientAlive on 2011-06-04
The guys in this [http://youtu.be/RZcJOZC38iQ](http://youtu.be/RZcJOZC38iQ) video don't have tiles but they do have flipping something over. I don't remember what point it's at in the vid (maybe half way or something) but you could see something like that there.

------------------------

Edit:

> **Ghost|BTFH said:**
> 
Now about the mouse...I was actually thinking there's an aspect of mice that's not generally utilized - click n' hold.  For example, after selecting a tile, holding the left mouse button down might allow you to then move the menu tiles around to give you more options.  And on the root menu, it could be used to move tiles around to arrange them however you wished.  In a 3D aspect, it could be used to rotate the selections, (think Desktop Cube) etc.  But of course, for the moving of tiles, changing your views, etc...the scroll wheel would also be a simple and viable option to give you all sorts of opportunities.



A guy could make handles you can grab with the mouse at a certain point or points on the object and be able to hold down the button and drag in a certain motion (such as rotating or zig zag or whatever) to get a certain, defined response from the system. Sort of the way you have those touch screen phones where you can trace a certain shape on the screen and it makes it do a certain function. So you can define a certain motion of the mouse pointer. When it has grabbed ahold of the handle and made that motion the system would do X function. You could even let the user have the option of defining the motions for the action if you wanted to.

You could use the little hand icon like in pdf readers instead of a classic arrow pointer. Or any icon for that matter.

---

### Post by Ghost|BTFH on 2011-06-05
[QUOTE=Copper Bezel]Also, square or rectangular metaphors more directly represent the shape of the windows and, ultimately, the display.[/QUOTE]

Which benefits us how?  It looks like the screen, ergo it's good?  The fundamentals of the view screen are flawed as well, but it's what we use, isn't it?  Our eyes see the world in an oval shape, not square, not rectangular.  Using the hex grid would give us a more smooth flowing design with the focus being usability and flexibility.  If I have to flip through half a dozen screens to find 1 tile, I'd consider that a very weak design that DOESN'T have usability in mind.

I believe in this case, looking at the competition serves (once more) with an excellent example of how NOT to do it.

[QUOTE=Copper Bezel]The advantage is that nothing ever really has to be represented by anything - the application "is" the icon.[/QUOTE]

Just curious - by that reasoning, wouldn't the application itself have to be in some sort of active (ie running) state to make something like that effective?  If so, aren't you basically loading every program you consider worth making a tile of each time you boot up, thus wasting gobs of resources?

I still feel the hex tile system could really take off and be very beneficial for the end user.  It gives them flexibility number one - and to me, that's the single most important thing in design - let the user change what they want to change.

Secondly, I think the layering would be very easy on the eyes, having everything come up center screen would definitely make for a far less confusing layout of menu items and having a large hex to click on is a far far easier target than a thin long rectangle of a menu list.

Your mileage may vary.

Cheers,
Ghost|BTFH

---

### Post by mehaga on 2011-08-06
Aloha,

I made a prototype of an app. launcher *loosely* based on this idea. Please test it and tell me if it's worth further development.

You should know the following before you decide to test it.
At the moment, everything is hard-coded, so you can't add/remove or configure items (available items are randomly chosen applications and categories...) So, it's very incomplete (and kinda ugly), but I think it's good enough for just testing the idea. It's written with QT, so you'll need QT libs to run it.

A readme file is included, but basically:
- use numpad or mouse to navigate,
- middle item shows current category/sub-menu; click it or press 5 to go 
  back to parent category,
- plus/minus or scroll to 'rotate',
- press zero to show search box, esc. to hide it,
- if search shows only one item, hit enter to activate it.
- there's no 'close' button, so you can only close the menu via task manager; 
  likewise, you can only move it by alt-dragging...

I also decided to try ubuntu one, so I put it there:
[https://files.one.ubuntu.com/rt_4uL-wRvinT-rS5GV8cA](https://files.one.ubuntu.com/rt_4uL-wRvinT-rS5GV8cA)
(I never used ubuntu one before, I hope it 'just works' :))

And once again, thank you for the idea ghost :)

---

### Post by neu5eeCh on 2011-08-06
Either patent it or make a piece of software that uses this so you can claim prior art. Fast. Seriously. That or watch it disappear into the portfolio of a patent troll. I kid you not.

---

### Post by Ghost|BTFH on 2011-08-06
I have something better than that - it's been posted here. :)

---

### Post by Ghost|BTFH on 2011-08-06
> **vekaz said:**
> Aloha,

I made a prototype of an app. launcher *loosely* based on this idea. Please test it and tell me if it's worth further development.

And once again, thank you for the idea ghost :)

Aloha brah,

You're very welcome and I hope you get Ubuntu One set up and working properly soon - that link's not working.

Cheers,
Ghost|BTFH

---

### Post by mehaga on 2011-08-06
Not working? <spanks ubuntu one> 
Ok, this should work: [http://www.megaupload.com/?d=NTMT9GO6](http://www.megaupload.com/?d=NTMT9GO6)

---

### Post by cariboo on 2011-08-07
IF you want people to download your file, use something like sourceforge, forcing people to use for pay download sites is just plain wrong.

---

### Post by mehaga on 2011-08-07
> **cariboo907 said:**
> IF you want people to download your file, use something like sourceforge, forcing people to use for pay download sites is just plain wrong.

Thank you for your advice. I'm not forcing anyone do anything, though :) It seemed like an easy option and it's free...

---

### Post by mehaga on 2011-08-07
Ok, it was easier than I thought it would be :)

[sourceforge]("http://sourceforge.net/projects/zemenu/files/Menu.tar.gz/download")

---

### Post by lovinglinux on 2011-08-07
I haven't read the entire thread, but I saw some concerns on how to deal with more than 6 sub-options.  Take a look at [Pearltrees]("http://www.pearltrees.com"), it might give you some ideas. I know this has nothing to do with a Desktop environment, is flash based and is for bookmark sharing, but the way it handles branches is very interesting. The user can create trees of bookmarks, organizing them according to a logical hierarchy. When a branch has to many childs, it changes shape to accommodate them. In your app would be trees of app launchers and files.

---

### Post by Linuxratty on 2011-08-07
I like this IF I could hide it...To access the hive would need to be a little hive icon,or tucked away in a menu..I do not like icons on my desktop,except on the task bars.

---

