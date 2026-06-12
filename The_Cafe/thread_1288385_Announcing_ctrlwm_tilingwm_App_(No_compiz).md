---
title: "Announcing ctrlwm: tiling/wm App (No compiz)"
date: 2009-10-11
forum: The Cafe
---

### Post by zlatkart on 2009-10-11
- Tile windows with different layouts and options (e.g. offset for free space for conky/screenlets...).
- Placing windows maximized horizontal/vertical left/right.... when mouse pointer reaches the screen borders (-s). Something similar to Win 7.
...
...
...

The -mn option is needed as offset for the window decoration vertical/horizontal (otherwise 4 20 is used as default). If you have space between the windows try smaller values. If the windows overlap higher values

Comments, ideas for new functions and help programming,would be appreciated. 

Newest Version here

[http://gtk-apps.org/content/show.php?content=114565](http://gtk-apps.org/content/show.php?content=114565)

---

### Post by etnlIcarus on 2009-10-11
Is it a full window manager or just a utility for manipulating open windows?
Also, can I get clarification on the, "no compiz", bit; do you mean it's incompatible with compiz?

I also take it your inspiration came from wmctrl?

---

### Post by zlatkart on 2009-10-11
It's just an utility for manipulating open windows. I like the standard Gnome wm but wanted some functionality

It's incompatible with compiz and unfortunately e17.

Some code came from wmctrl.

I wanted to see if there is any interest in this, before writing a "manual".

---

### Post by etnlIcarus on 2009-10-11
I've become quite dependant upon compiz and quite a few other probably have, as well. You're probably limiting your audience a bit there. Had you considered contacting wmctrl's developer and rewriting your functionality as a patch?

---

### Post by zlatkart on 2009-10-11
As I don't use compiz and I wrote this originally for myself I don't really care about the small audience. But I thought about rewriting the App so it would work with e17 and therefore with compiz too. If there are people out there who would like to use this with compiz I'll try to speed up development.
I thought about patching wmctrl, but it's not so much code taken from there and wmctrl gives functionality to manage windows/workspaces as ctrlwm manages windows and workspaces

---

### Post by zx6zx6 on 2009-10-11
This kind of app is deadly useful with common 16x9 wide screen nowaday. Who want to waste their screen just to display ad and blank? Have two windows side by side is very productive. Just glancing and getting what you need from the another windows is soooo great.
There are many guys out there keep moanning that tile or cascade windows isn't necessary and try to teach me about multiple workplaces whenever I mention it. Poor them. I think they still stuck in they 14 inches 800x600 CRT screen.
I'm currently in work, so I'll try this right after I come home and give feedback for this app.

---

### Post by skooter1121 on 2009-10-13
I've been using wmctrl to load FireFox and OO Writer directly into other workspaces, so they are easily available.

I also have installed tile 0.7.4 a X11 window tiling utility by
Greg Schenzel  [email]inittab@unixdev.net[/email] Which lets me place two  panel icons HORIZONTAL and VERTICAL to reposition open windows. This works great, Open two new Nautilus windows and they automatically resize themselves to 1/2 page.

This is a exceptionally valuable tool. To have two File Manager windows open on the same screen for drag/move/drop has made my life so much easier. Even more so on my EeePC 9 inch screen, where I can actually do some serious file/folder management. Plus I can always easily open my other workspaces.

I have not looked at your utility yet but it sounds great. Windows has had this since Win 95. You might want to look at the WinSplit utility at winsplit-revolution.com for some ideas. I have installed this on hundreds of Windows PC any everybody loves it.

Pay no attention to those nay sayers, multiple windows on ONE screen is a great compliment to having programs running on other workspaces. Can't wait to use it on my 42" HDTV

On my EeePC I do not have compiz installed (only a 4 gig SDD). I'm sure that the NetBook community who like to run a lean and mean OS would welcome your utility. (Say NO to eye candy!)

Would be great if you would compile a .deb package.

-Skooter

---

### Post by etnlIcarus on 2009-10-13
Tile/cascade was introduced in XP, not 95.

---

### Post by skooter1121 on 2009-10-14
Well...

Since you have mentioned an error in a very minor statement in my post. I am replying in kind.

From Wikipedia: Tiling window manager

[I]History

The first version (Windows 1.0) featured a tiling window manager, partly because of litigation by Apple claiming ownership of the overlapping window desktop metaphor. But due to complaints, the next version (Windows 2.0) followed the desktop metaphor. All later versions of the operation system stuck to this approach as the default behaviour.[/I]

Who can trust Wikipedia anyway! So I just cranked up my Toshiba 386-20 1850 Laptop 4 megs of RAM with Windows 3.1 for giggles and yep it's there! 

Apology acknowledged. I'd rather hear more comments about this utility.

-Skooter

---

### Post by etnlIcarus on 2009-10-14
> Since you have mentioned an error in a very minor statement in my post.Christ. Another one.

> Apology acknowledged.What exactly would I be apologising for?

And it's a bit of a stretch to claim 3.1 has tiling window management, when it only available in MDIs.

---

### Post by skooter1121 on 2009-10-14
Sorry if I've offended you.

Just trying to keep this thread on track, and provide the developer with valuable input.

-Skooter

---

### Post by etnlIcarus on 2009-10-14
Sorry if I've offended you also.

---

### Post by zlatkart on 2009-10-14
Now I had a quick look on WinSplit, and it seems to be a similar approach. I think if you like WinSplit, you should like ctrlwm. I don't use Windows at home, so if you are familiar with WinSplit you could tell me what could be worth implementing in ctrlwm.

I will post an update soon, and  a deb file with  it .

---

### Post by skooter1121 on 2009-10-14
Great, I'd love to give your program a try.

I set my WinSplt program a while ago, and only copy my saved settings to other machines. It was very awkward to setup. I'll take a closer look at it so I can offer some suggestions to you.

-Skooter

---

### Post by zlatkart on 2009-10-14
OK

[SIZE=1](But you can really try it by copying the binary to your home. Then create x starter with path & the wanted options. In Terminal type ./ctrlwm for help/options)[/SIZE]

---

### Post by zlatkart on 2009-10-14
Now I made an update and there is also a deb file available. Hope it works.

---

### Post by skooter1121 on 2009-10-14
I've installed the .deb and here is my first comment.

Only used ctrlwm -t so far. I launch it from a panel launcher, called ***PaneFill Windows*** (bad pun but catchy name suitable for a GUI). 

With 2 windows open on the desktop. It does not appear to tile them completely flat on the desktop. There is a slight overlap of the second window left edge over the left windows right edge. 

If more than 2 windows are open and ***PaneFill*** is executed it only further compounds the overlap.

Thought I'd let you know this before I review any further.

-Skooter

---

### Post by zlatkart on 2009-10-14
> With 2 windows open on the desktop. It does not appear to tile them completely flat on the desktop. There is a slight overlap of the second window left edge over the left windows right edge. 
For this you have to set the -mn option. Try my suggested values. It's because of the decoration set by the window manager.

> If more than 2 windows are open and ***PaneFill*** is executed it only further compounds the overlap.
?

---

### Post by zlatkart on 2009-10-14
try     -mn 8 30    as option.

---

### Post by skooter1121 on 2009-10-14
Great,

ctrlwm -t -mn 10.25 55 works for me but... it leaves a space on the bottom.



And ctrlwm -z -u leaves a ghosted blank lined grid on the desktop, which disappears when I move a window around.


-Skooter

---

### Post by zlatkart on 2009-10-15
> Great,

ctrlwm -t -mn 10.25 55 works for me but... it leaves a space on the bottom.

That's strange. Maybe its the 10.25 causing the problem. As there are no 1/4 Pixel 10 should have the same output. Did you try the -o option with this? You could post the output of wmctrl -d.


> And ctrlwm -z -u leaves a ghosted blank lined grid on the desktop, which disappears when I move a window around.

It's much easier  drawing on the root window, than erasing it (That's the bug I've mentioned on top). I hope I'll get a solution for this soon. Now you can use -z without -u or live with it.

---

### Post by zlatkart on 2009-10-15
x

---

### Post by h0bbe on 2009-10-16
I just started looking for a way to tile windows from different programs in Ubuntu and to my surprise it isn't possible by default! I've used this alot at work since I got my big widescreen monitor and now I've bought one for my home computer running Ubuntu and want to do the same.

Great work! I'm surely a potential user but I do need a manual and want it to be really easy to use 8-[

The functionality suggested in this post on [http://brainstorm.ubuntu.com/idea/428/](http://brainstorm.ubuntu.com/idea/428/) would be nice:
> **CydeSwype wrote on the 18 Dec 08 at 06:24 **	
i'd like to see the ubuntu implementation smarter than the windows "tile" feature. specifically, there should be a "lock tiles" feature so that once the windows are tiled, one window can be resized and all the other windows should resize with it, to remain "tiled." this would be especially handy for watching a movie in one window of the tile, having a browser in another "tile," etc. the user could resize the movie playing in one window to make it bigger and all the other windows would get smaller. would be nice to drag a window/tile to another window/tile to "swap" tiles also. tile usually assumes the user wants all windows the same size...but this is rarely the case. 

Keep on working, it's a very useful app!!

EDIT: Have you seen this "simple program", [http://code.google.com/p/tile-windows/](http://code.google.com/p/tile-windows/)?

---

### Post by etnlIcarus on 2009-10-16
If you're not hell-bent on automated tiling, you can do the same thing with wmctrl. Just whip out your calculator, [create shell scripts with the relevant arguments](http://ubuntuforums.org/showthread.php?t=1282386), and map them to shortcut keys (varies with environment).

I've got Alt+1 ~ Alt+0 mapped with windows sizes (as fractions of total screen size) 1/8th x 1/3rd, 2/8ths x 1/3rd, 3/8ths x 1/3rd, 3/8ths x 1/2, 3/8ths x 2/3rds, 1/2 x 1/2, etc

[wmctrl](http://tripie.sweb.cz/utils/wmctrl/) is in the repos.

---

### Post by zlatkart on 2009-10-16
> I do need a manual and want it to be really easy to use 8-[I'll try to edit my first post, so it will be clear how to use it. The best would be to try my suggestions. I terminal type ctrlwm or ctrlwm --help.

> The functionality suggested in this post on [http://brainstorm.ubuntu.com/idea/428/](http://brainstorm.ubuntu.com/idea/428/) would be nice:
I am currently working on this. Could take a while though.

> EDIT: Have you seen this "simple program", [http://code.google.com/p/tile-windows/](http://code.google.com/p/tile-windows/)?Now I have.

---

### Post by zlatkart on 2009-11-05
first post updated

---

### Post by zlatkart on 2012-12-31
New update available

---

### Post by Linuxratty on 2012-12-31
> **zlatkart said:**
> 
I wanted to see if there is any interest in this, before writing a "manual".

If you add superkey mouse scroll to zoom in and out I'd be interested.

---

### Post by zlatkart on 2012-12-31
> **Linuxratty said:**
> If you add superkey mouse scroll to zoom in and out I'd be interested.

;) Now there's 3 years since then. What would you like to zoom in and out?

---

### Post by zlatkart on 2013-01-03
Next update

---

### Post by overdrank on 2013-01-03
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

