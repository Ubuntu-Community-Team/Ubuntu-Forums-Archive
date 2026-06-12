---
title: "in love with epiphany"
date: 2005-12-23
forum: The Cafe
---

### Post by akurashy on 2005-12-23
oh no I don't want to start a browser war!, just need to express how awesome is this little browser and how amazing it can be :D, I was well kinda tired of firefox and some other problems I had with it and decided to give it a go with epiphany, so far epiphany is fast, i decided to compile epiphany last version (stable), and well it didn't change to much, i guess it did had some bug fixes, i went and compiled 1.9.3.1 one and well it opens 5x faster than the old one to be honest, and with the epiphany extensions 1.9.3 i really don't know what to say!. 

i suggest for everyone that have a slow computer, (or fast), to try out epiphany, optional of course :D

(to get it from the repo is sudo apt-get install epiphany-browser )

---

### Post by wylfing on 2005-12-23
Yeah, epiphany is nice. It uses the Gecko core, IIRC, so it will render more or less with the same quality as Firefox. It's the rest of it that's leaner and meaner. For the KDE folk, Konqueror is fantastico, especially since KHTML is probably the most technically advanced rendering engine in existence. There's definitely other worthwhile browsers out there.

This is an interesting page viz. browsers:
[http://userlinux.com/cgi-bin/wiki.pl?Browser_Matrix](http://userlinux.com/cgi-bin/wiki.pl?Browser_Matrix)

I also love to push Opera. On my wife's computer (Ubuntu of course), Opera is at least twice as fast as Firefox.

What keeps me using Firefox are the extensions, though, some of which I've found I can't live without.

---

### Post by Perfect Storm on 2005-12-23
Woot!!! Another epiphany user! :razz:

---

### Post by prizrak on 2005-12-23
Epiphany is nice, but the interface isn't as pretty and there are no live bookmarks. Live bookmarks is the thing that keeps on FF no matter what else I try.

---

### Post by Wallakoala on 2005-12-23
I tried it the other day...its nice. I like it, but I also like firefox.

---

### Post by akurashy on 2005-12-23
Here a nice screenshot

[http://static.flickr.com/40/76678245_ffc175c9f2_o.png](http://static.flickr.com/40/76678245_ffc175c9f2_o.png)

I hope they make it better, actually hoping to see a nice future for epiphany

---

### Post by Perfect Storm on 2005-12-23
Here's mine ^^

---

### Post by AlexandreP on 2005-12-24
Oh, someone who did compile Epiphany 1.9.3.1 :)  I'm currently trying to do so, but I don't know exactly what I have to get (dev packages?).  I would also like to use the extensions with it, but again I don't know what to do...

On Epiphany's wiki, it's said that I have to get GTK+ >= 2.6, glib 2.8 and Mozilla Firefox 1.0.x *(I guess it is also possible to use 1.5)* with gtk2 support.  But I'm not a 100% sure I have everything in my computer...  And do I need dev packages for them?

---

### Post by ember on 2005-12-24
A question: Do we have a useful interface for adblocking and working mouse gestures in the latest version of Epiphany. It is quite a while ago, I tried it and I was not very impressed. Yet I am thinking about giving it another try.

---

### Post by asimon on 2005-12-24
I too like epiphany (and konquerer). The only things that bugs me is that these browers are not compatible with the firefox plugins. There are some really convenient firefox plugins for which there is not equivalent for epiphany (or konquerer).

---

### Post by Sheinar on 2005-12-24
Tried the stable release of Epiphany a short while ago. Didn't like it at all. It felt dumbed down and the way the tabs worked was really quite annoying. Maybe that's been changed by now though. I guess I should probably try the unstable release and see if they're working on any noticeable improvements.

---

### Post by Gandalf on 2005-12-24
I compiled the unstable, first i had LOADS of missing dev packages, after that the compilation went smooth except when i installed it (like any other thing i use checkinstall -D to install) it complained about already existing file owned by totem (i have totem 1.3)

now when i run it i get 
> 
Bonobo couldn't locate the GNOME_Epiphany_Automation.server file. You can use bonobo-activation-sysconf to configure the search path for bonobo server files.


anyone have hints for that?

---

### Post by Gandalf on 2005-12-24
[QUOTE=Gandalf]I compiled the unstable, first i had LOADS of missing dev packages, after that the compilation went smooth except when i installed it (like any other thing i use checkinstall -D to install) it complained about already existing file owned by totem (i have totem 1.3)

now when i run it i get 


anyone have hints for that?[/QUOTE]
If someone else faced the same problem as i faced above, then on a Terminal type
```

sudo bonobo-activation-sysconf --add-directory=/usr/local/lib/bonobo/servers/

```

now restart Gnome
```

<Ctrl> + <Alt> + <BackSpace>

```

this should be fixed, BTW it's Very Fast, i'll try to move to it from Firefox :D

P.S: According to [Browser Speed Comparisons](http://www.howtocreate.co.uk/browserSpeed.html) Opera is the fastest browser

---

### Post by akurashy on 2005-12-24
[quote=Gandalf]If someone else faced the same problem as i faced above, then on a Terminal type
```

sudo bonobo-activation-sysconf --add-directory=/usr/local/lib/bonobo/servers/

``` 
now restart Gnome
```

<Ctrl> + <Alt> + <BackSpace>

``` 
this should be fixed, BTW it's Very Fast, i'll try to move to it from Firefox :D

P.S: According to [Browser Speed Comparisons]("http://www.howtocreate.co.uk/browserSpeed.html") Opera is the fastest browser[/quote]

i did face that, i just copied the file of it to the bonobo folder and it got fixed without restarting :D

---

### Post by Gandalf on 2005-12-24
Well I had to restart :(

what you think about Opera guys?

---

### Post by bonzodog on 2005-12-24
sorry gandalf, but I won't use opera as it depends on the qt libs - i.e bits of kde. I am heavily anti-kde, as it is soooo bloated, and won't install anything that depends on qt libs.

---

### Post by Gandalf on 2005-12-24
hmmm Installing it is quite easy and it didn't download lot of dependecy AFAIR

---

### Post by stimpack on 2005-12-24
[QUOTE=bonzodog]sorry gandalf, but I won't use opera as it depends on the qt libs - i.e bits of kde. I am heavily anti-kde, as it is soooo bloated, and won't install anything that depends on qt libs.[/QUOTE]

troll, damn evangelicals.

Not sure about epiphany but the reason I use Firefox over Konq is simple, Adblock and Adblock Filterset.G. Therefore the most desired ability for epiphany and Konq would be to be able to use Firefox plugins.

---

### Post by AlexandreP on 2005-12-24
[QUOTE=bonzodog]sorry gandalf, but I won't use opera as it depends on the qt libs - i.e bits of kde. I am heavily anti-kde, as it is soooo bloated, and won't install anything that depends on qt libs.[/QUOTE]
I tought Opera had its Qt libs built-in its deb package, so it does not download any dependencies from repositories.  I find Opera is fast, like Firefox 1.5, but (1) it is not libre, and (2) it is not well integrated in GNOME.

---

### Post by AlexandreP on 2005-12-24
[QUOTE=Gandalf]I compiled the unstable, first i had LOADS of missing dev packages, [...][/QUOTE]
Do you remember the ones you had to download?  I'm trying to figure out which dev packages I have to get...

The last error I get, for now, is this one:
> 
Package libxslt was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxslt.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxslt' found

I believe it needs Firefox's dev package; in the repository, I only have the devs for Fx 1.0.7, is it possible to use Fx 1.5?

---

### Post by The Warlock on 2005-12-24
I've tried Epiphany, and it's nice that it's all integrated with Gnome and stuff (it's damn fast, too!), however: 

1) Tab behavior is completely dain bramaged. I can't stand it. Whose idea was it to put those tiny arrow buttons there? Just shrink the tabs when they fill the bar. There's a reason why every other tabbed browser (no, Galeon doesn't count) does it this way: it works better. In Epiphany, the little buttons are impossible to hit quickly and I never know how many tabs I have open. It sucks.

Also, the tab bar disappears when there's only one tab. Now, I understand that some people like it that way, but many don't, and this is what a preferences dialog is for. Of course, Epiphany has the gnome mindset of "preferences are evil, and it's better to have less functionality than more, even in programs that would benifit from it", which, interestingly, is also the reason I'm using quod libet instead of rhythmbox, xfwm4 instead of metacity, etc.

2) No adblock. But they're working on that (with filterset-G by default, yay!)

3) No search bar, but that's not nearly as critical as the above issues. Still, it would be nice to have.

4) It would be nice to have some compatability with Firefox plugins, since nobody but the developers are making plugins for Epiphany. Just stuff like BugMeNot and CustomizeGoogle are nice to have.

---

### Post by akurashy on 2005-12-24
[quote=The Warlock]I've tried Epiphany, and it's nice that it's all integrated with Gnome and stuff (it's damn fast, too!), however: 

1) Tab behavior is completely dain bramaged. I can't stand it. Whose idea was it to put those tiny arrow buttons there? Just shrink the tabs when they fill the bar. There's a reason why every other tabbed browser (no, Galeon doesn't count) does it this way: it works better. In Epiphany, the little buttons are impossible to hit quickly and I never know how many tabs I have open. It sucks.

Also, the tab bar disappears when there's only one tab. Now, I understand that some people like it that way, but many don't, and this is what a preferences dialog is for. Of course, Epiphany has the gnome mindset of "preferences are evil, and it's better to have less functionality than more, even in programs that would benifit from it", which, interestingly, is also the reason I'm using quod libet instead of rhythmbox, xfwm4 instead of metacity, etc.

2) No adblock. But they're working on that (with filterset-G by default, yay!)

3) No search bar, but that's not nearly as critical as the above issues. Still, it would be nice to have.

4) It would be nice to have some compatability with Firefox plugins, since nobody but the developers are making plugins for Epiphany. Just stuff like BugMeNot and CustomizeGoogle are nice to have.[/quote]
there IS a search bar, but i removed mine, i don't like having it (since i rarely use it)

yet i feel that epiphany should be "standalone" i mean not depending on another browser's libs, because, i think it just would be great.

---

### Post by The Warlock on 2005-12-24
[QUOTE=akurashy]there IS a search bar, but i removed mine, i don't like having it (since i rarely use it)

yet i feel that epiphany should be "standalone" i mean not depending on another browser's libs, because, i think it just would be great.[/QUOTE]
They're working on that; that's what xulrunner will do. Still, it doesn't solve the other major problems I've mentioned.

---

### Post by AlexandreP on 2005-12-24
I got it to work (thanks to Gandalf's trick).

There are two interesting changes I've noted (as a simple user):
- like in Firefox, when entering a secure zone, the address bar's background color turns to yellow and a lock is displayed;
- it is faster than 1.8.  (Could it be faster if I used Fx 1.5-dev package?)

Again, Epiphany is very well integrated in GNOME.  It is functionnal and simple, minimalistic.  A good browser for the ones who just want to browse the web ;)  Things that are still there and that I really like in Epiphany: an integrated session saver and the browser alerts us when leaving a page in which some content has not been posted.

But some evolution is needed:
- Epiphany should be able to remember values we enter in text fields, when browsing websites;
- Even if some preferences can be modified in *about:config*, more preferences should be available through a graphic interface/the preferences' dialog;
- A dialog should not open when a page cannot be loaded.  This "freezes" the use of the browser.  Instead, something like it is used by Firefox 1.5 or Internet Explorer should be done;
- One should be able to copy an image to the clipboard (not just text);

Some suggestions (that may be developed as Epiphany extensions, since it might not be useful for the Average Joe):
- Epiphany should have its own source viewer.  I think using gEdit for that is not good because it is a heavy program (at least, that's the impression I have using it on my old, slow computer).  Maybe something based on Mousepad (Xfce's text editor)...
- Something I like in Firefox ans Opera is the ability to see the pages' titles when exploring the previously visited links in the address bar.  Maybe it can be ported to Epiphany.

About the tabs thing: the use of arrows is the common way to handle multiple tabs in GNOME.  I like that.  Lets say in Firefox I open, I don't know, 50 tabs, and my screen size is not that large: opened tabs would be small and compact, and I would not be able to select the last opened ones because I won't see them.  In Epiphany, tabs are large and I'm able to see the pages' titles even when I have 50 of them opened, and using the arrows I can browse to the last ones.  ***But*** I have to agree that Epiphany could reduce the size of the tabs to allow more of them to fit in the browser without srolling using the arrows.

---

### Post by The Warlock on 2005-12-24
[QUOTE=AlexandreP]I got it to work (thanks to Gandalf's trick).

There are two interesting changes I've noted (as a simple user):
- like in Firefox, when entering a secure zone, the address bar's background color turns to yellow and a lock is displayed;
- it is faster than 1.8.  (Could it be faster if I used Fx 1.5-dev package?)

Again, Epiphany is very well integrated in GNOME.  It is functionnal and simple, minimalistic.  A good browser for the ones who just want to browse the web ;)  Things that are still there and that I really like in Epiphany: an integrated session saver and the browser alerts us when leaving a page in which some content has not been posted.

But some evolution is needed:
- Epiphany should be able to remember values we enter in text fields, when browsing websites;
- Even if some preferences can be modified in *about:config*, more preferences should be available through a graphic interface/the preferences' dialog;
- A dialog should not open when a page cannot be loaded.  This "freezes" the use of the browser.  Instead, something like it is used by Firefox 1.5 or Internet Explorer should be done;
- One should be able to copy an image to the clipboard (not just text);

Some suggestions (that may be developed as Epiphany extensions, since it might not be useful for the Average Joe):
- Epiphany should have its own source viewer.  I think using gEdit for that is not good because it is a heavy program (at least, that's the impression I have using it on my old, slow computer).  Maybe something based on Mousepad (Xfce's text editor)...
- Something I like in Firefox ans Opera is the ability to see the pages' titles when exploring the previously visited links in the address bar.  Maybe it can be ported to Epiphany.

About the tabs thing: the use of arrows is the common way to handle multiple tabs in GNOME.  I like that.  Lets say in Firefox I open, I don't know, 50 tabs, and my screen size is not that large: opened tabs would be small and compact, and I would not be able to select the last opened ones because I won't see them.  In Epiphany, tabs are large and I'm able to see the pages' titles even when I have 50 of them opened, and using the arrows I can browse to the last ones.  ***But*** I have to agree that Epiphany could reduce the size of the tabs to allow more of them to fit in the browser without srolling using the arrows.[/QUOTE]
The problem is, when the arrows pop up, I'm not sure how many tabs I have open or what is on those tabs, and I tend to have a lot more tabs open at any given time in my browser than I do in, say, gedit. When the tabs are running off the edge in Firefox, I think to myself, "hey, I've got too damn much stuff open, maybe I should close some of these tabs or resize the window or something". In Ephihany, it's more like "hey, where the hell did those other pages I was reading earlier go?!"

But since this is a Gnome issue, maybe that should be a global Gnome option somewhere, like in the Menus & Toolbars dialog in the Preferences menu.

---

### Post by benplaut on 2005-12-25
if it supported firefox extensions, sure! i'd use it! ;)

---

### Post by BLTicklemonster on 2005-12-25
My back and forward mouse buttons don't work in epiphany, and when I view a thread in a forum, then close (not posting, just viewing) it has a hissy fit and says the that if I close, I will lose unsaved changes. I'll stick with the fox for now.

---

### Post by puccaso on 2006-04-21
i like it too
yea i love i guess
but whats stopping me from really loving it
is the tabs
i hate themmmmm, some nasty x on each tab --
is there no way i can remcompile or find howto somehow revert back to
the old tabing format, like tabs in firefoxx... where we have one x on the corner
like the firefox setup... one x on the corner for the current tab

---

### Post by missmoondog on 2006-05-06
epiphany and galeon BOTH rule over firefox in ubuntu/gnome. 
firefox sucks in both windows and linux.

opera rules over all those, but i can't stand the fonts in it in ubuntu, so i use either epiphany or galeon. no particular preference between those 2, except the tabs deal in epiphany. who wants tabs to open in the background all the time? what sense does that make?

---

### Post by reinouts on 2006-05-06
> **AlexandreP]
But some evolution is needed:
- Epiphany should be able to remember values we enter in text fields, when browsing websites said:**
> 
Yes, this is a [known problem](http://bugzilla.gnome.org/show_bug.cgi?id=166172). Apparently it's nontrivial to implement (help appreciated! ;) 
> 
- Even if some preferences can be modified in *about:config*, more preferences should be available through a graphic interface/the preferences' dialog;

Doubtful. What prefs are you thinking of? Epiphany consciously tries to keep the number of preferences as low as possible, and go with good defaults instead. Some options are exposed via gconf.
[quote]
- A dialog should not open when a page cannot be loaded.  This "freezes" the use of the browser.  Instead, something like it is used by Firefox 1.5 or Internet Explorer should be done;

Already fixed in any Epiphany version >1.8 that uses Firefox 1.5 as backend.
> 
- One should be able to copy an image to the clipboard (not just text);

Can you do this in Firefox? I don't think you can. Epiphany (regretfully) depends on [Mozilla](https://bugzilla.mozilla.org/show_bug.cgi?id=21747) for copy/paste functionality.
> 
- Epiphany should have its own source viewer.

Gedit is quite a lot faster in GNOME 2.14 than it used to be. Otherwise, try typing 'view-source:' before the URL in the location bar.
> 
- Something I like in Firefox ans Opera is the ability to see the pages' titles when exploring the previously visited links in the address bar.  Maybe it can be ported to Epiphany.

There are some plans for overhauling the bookmarks/history subsystem, this might be well fixed when we get it done.
> 
***But*** I have to agree that Epiphany could reduce the size of the tabs to allow more of them to fit in the browser without srolling using the arrows.
Dynamically adjusting tab sizes would make it impossible to close a number of tabs in a row  in a few mouse clicks, without having to move your mouse. The way tabs work currently in Epiphany is the best compromise that could be reached within the limitations of the GTK notebook widget.

---

### Post by reinouts on 2006-05-06
[QUOTE=The Warlock]1) Tab behavior is completely dain bramaged. I can't stand it. Whose idea was it to put those tiny arrow buttons there? (...)[/quote]
This is the GTK notebook widget, there's really nothing to be done about the arrow buttons except changing GTK.
> In Epiphany, the little buttons are impossible to hit quickly and I never know how many tabs I have open. 
Which little buttons? Anyhow, if you feel compelled to open a brain-damaging amount of tabs in one window, you can use the Tabs menu and see an overview of all opened tabs.
> 
Also, the tab bar disappears when there's only one tab. Now, I understand that some people like it that way, but many don't, (...)
Just set the gconf key [FONT="Courier New"]/apps/epiphany/general/always_show_tabs_bar[/FONT] to **true**.
> 
3) No search bar, but that's not nearly as critical as the above issues. Still, it would be nice to have.

As someone else already said, a search bar is default in Epiphany since version 1.8.
> 
4) It would be nice to have some compatability with Firefox plugins, since nobody but the developers are making plugins for Epiphany. Just stuff like BugMeNot and CustomizeGoogle are nice to have.
Yes, that would be nice, but unfortunately it's technically next to impossible to implement.

---

### Post by weasel fierce on 2006-05-06
I quite enjoy Epiphany. I used to have a little thing, where it puts a bookmark icon in the system tray, but after reformatting and installing dapper, I havent been able to find it again. 

Any ideas ?

---

### Post by reinouts on 2006-05-06
[QUOTE=weasel fierce]I quite enjoy Epiphany. I used to have a little thing, where it puts a bookmark icon in the system tray, but after reformatting and installing dapper, I havent been able to find it again. 

Any ideas ?[/QUOTE]
Yes, that's the bookmarks tray extension, which is disfunctional in the latest Epiphany-extensions release. However, the deskbar-applet more than makes up for this omission!

---

### Post by Gustavo on 2006-05-06
I like epiphany too but one thing is driving me nuts: when I open a new tab, I have to click on the navigation bar to type the desired address. Is there a way to change this?

---

### Post by Wolki on 2006-05-06
[QUOTE=Gustavo]I like epiphany too but one thing is driving me nuts: when I open a new tab, I have to click on the navigation bar to type the desired address. Is there a way to change this?[/QUOTE]

Yes, use a blank homepage. Epiphany assumes that, if you have a real homepage set, you want the focus to be there so you could type into e.g. a searchbox on that page.

(If you don't want to do that, ctrl-l will focus the url field and highlight all the text there for easy overwriting. Useful shortcut anyway.)

---

### Post by grte on 2006-05-16
Another Epiphany user, here.  One, thing, though.  When opening a torrent file, epiphany uses it's own client.  Is there anyway I can change it to default to Azureus?

---

### Post by llonesmiz on 2006-05-16
I think that changing the default program used to open torrent files to Azureus could solve that problem. To do that just search for a .torrent file in nautilus, right-click on it, select "properties", then the "open with" tab, press the Add button and select Azureus (if you cant find it try using a custom command). Once you've done that, make sure that the Azureus radiobutton is selected in the "open with" tab.

---

### Post by Gustav on 2006-05-16
[QUOTE=reinouts]Dynamically adjusting tab sizes would make it impossible to close a number of tabs in a row  in a few mouse clicks, without having to move your mouse. The way tabs work currently in Epiphany is the best compromise that could be reached within the limitations of the GTK notebook widget.[/QUOTE]
The problem with the tabs in Epiphany (at least in the breezy version, I haven't tried the new one) it that they **are** dynamically adjusting. When getting so many tabs that they don't fit at one page, the tabs get wider so that they fill up the whole tab area width.

Look at the pictures to get my point. (the first picture has three tabs and the second has four tabs)

---

### Post by manicka on 2006-05-16
If you find Firefox a bit slow, have a look at swiftfox [http://getswiftfox.com/](http://getswiftfox.com/)

---

### Post by grte on 2006-05-16
[QUOTE=llonesmiz]I think that changing the default program used to open torrent files to Azureus could solve that problem. To do that just search for a .torrent file in nautilus, right-click on it, select "properties", then the "open with" tab, press the Add button and select Azureus (if you cant find it try using a custom command). Once you've done that, make sure that the Azureus radiobutton is selected in the "open with" tab.[/QUOTE]

This worked, thank you.

---

### Post by Lopsicle on 2006-05-16
I tried Epiphany but the speed tests I done against Firefox and Opera it always came last? Firefox came first but Opera seemed to run faster so Im not sure ;)

---

### Post by RAV TUX on 2006-05-16
I like Epiphany but I feel Galeon is better. (sad to here the Galeon project got abandoned but they are now making extensions for Epiphany, strange sort of events, the same guy who started Galeon now runs Epiphany)

---

### Post by 23meg on 2006-05-16
[QUOTE=yozef]I like Epiphany but I feel Galeon is better. (sad to here the Galeon project got abandoned but they are now making extensions for Epiphany, strange sort of events, the same guy who started Galeon now runs Epiphany)[/QUOTE]
Epiphany and Galeon [merged]("http://http://www.ubuntuforums.org/showthread.php?t=82375").  Epiphany was forked from Galeon in the first place.

---

### Post by RAV TUX on 2006-05-16
[QUOTE=23meg]Epiphany and Galeon [merged]("http://http://www.ubuntuforums.org/showthread.php?t=82375").  Epiphany was forked from Galeon in the first place.[/QUOTE]


My wording was a bit off mark and you are correct here are the full details:

[http://en.wikipedia.org/wiki/Galeon](http://en.wikipedia.org/wiki/Galeon)

Galeon's initial development team split in 2002 due to disagreements about the target audience. This split led to the creation of Epiphany, a fork of Galeon. Epiphany has since become the default browser of GNOME. On October 22, 2005, the Galeon developers announced plans to stop development of Galeon in its current form, saying "the current approach is unsustainable" in the resources required for maintenance. Instead, they hope to develop a set of extensions for Epiphany to provide similar functionality.


[http://galeon.sourceforge.net/links/history.php](http://galeon.sourceforge.net/links/history.php)
 Galeon, A History
or, why Galeon is the way it is
Chris "Topher" DeRosia - 29 July 2003

This document is intended to provide a brief history of Galeon; where it's been, and how it got to its current status. Galeon's relation to Epiphany will be briefly described.

Once upon a time, Marco Pesenti Gritti decided to make a web browser. He liked the Mozilla project, but wanted something that integrated well with his system and that was fast enough to be usable. Marco wanted a good, solid, simple browser for The Average User, in the Gnome environment, and so around June of 2000, Galeon 0.6 was released.

Galeon was a very popular project, with heavy development. Many features were added, making it a powerful, versatile browser, used by techies and non-techies alike. Releases came as often as Mozilla releases, since the API usually changed slightly with each Mozilla release. And with each release came a few new features. And with each feature came a preference dialog for that feature. Some people considered this to be a good thing, since features provide flexibility, and control. Others felt this to be a bad thing, thinking that too many preference options caused confusion.

In November of 2001, the decision was made to release Galeon 1.0 before Mozilla 1.0 was released. This was based on the belief that while Mozilla was not 1.0 yet, the code and feature set in Galeon was 1.0 quality.

Galeon2

After a series of 1.1.x releases, 1.2 was released on 12 Mar 2002. 1.2 had an enormous number of new features, which pleased the gadgety crowd, but was far from Marco's vision of a simple browser for Everyman.

In March of 2002, GTK 2.0 came out, and many programs began porting to it. The Galeon developers looked at the project and decided that for a number of reasons, a complete re-write was in order. There was pretty much universal agreement on that decision, and on 26 Oct 2002, Galeon 1.3 (sometimes called galeon2) was released. This is one of the reasons that people often say that 1.3 is a "stripped" 1.2, since 1.3 has so many fewer features. While there were feature issues in 1.3, the fact is that 1.3 had NO features when it started, and features are still being built into it.

Marco felt that this was a good time try moving back to the simpler browser he had wanted from the beginning. Rather than simply porting every feature and preference from Galeon 1, he moved slowly, planning feature additions, and weighing the worth of each feature and preference. Far more features were ported than are readily apparent, mostly due to the fact that the GUI preferences interface was much more difficult to plan and construct.

As lead developer, Marco felt justified in modifying the code to create the browser he wanted. This didn't sit well with some of the developers, and a great deal of heated discussion occurred on the galeon-devel list. As Galeon 1.3 releases came out, the discussions got more heated, as people became less and less satisfied with Marco's decisions. In April of 2002, Havoc Pennington wrote a document called "Free software and good user interfaces". The Gnome project had been struggling with uniform human interface guidelines, and after much discussion, Havoc came up with his essay.

The essay got mixed reviews, with some people thinking that it was a GREAT idea to make things uniform and simple; others thought it was a terrible idea to make things so simple because it felt restrictive. The Gnome Human Interface Guidelines (HIG) were made soon after.

A Tale Of Two Opinions

Marco's decisions regarding the interface to Galeon were not universally well received. Some thought it was an excellent idea to move toward a more HIG compliant browser, but since moving in this direction involved reducing the number of available settings in the preferences, and changing the main interface that people had become accustomed to, some thought it would be the downfall of a great browser.

The issues essentially boiled down to two opinions; should Galeon be a simple browser, or should it be a power user's browser?

In November of 2002, after many months of long hard discussion, Marco made the very difficult choice to leave the Galeon development team, and created Epiphany. No longer part of the Galeon team, Marco was free to create what he wanted; a simple, HIG compliant browser. This also freed the Galeon team to mold Galeon into what they wanted; a powerful, flexible browser for people who want to be able to customize to their hearts content.

The Future

So what's next? For the users, they get choice, the glory of the Open Source world. If they want a relatively simple, HIG compliant browser, Epiphany is the way to go. If they want a power user's browser, with features galore, Galeon is the way to go.

"But what about all the features?!?" people ask. "I loved Galeon 1.2, why is Galeon 1.3 such a featureless POS?". Well, it's not a featureless POS. It's a piece of software under development. Devel was a little slow after the split, mostly due to Real Life constrains.

For the Galeon developers, the addition of functionality is a high priority. Galeon itself has much more functionality than the preferences interface would indicate. Gestures, key bindings, and smart bookmarks have all worked for some time, though access was limited to gconf-editor. They simply need to have a preference GUI added.

Some things from the TODO in the Galeon tarball are:

    * Reorganise prefs dialog. (tko)
    * Stylesheet chooser menu. (We had a volunteer?)
    * eggtoolbar (? please ric smile )
    * eggmenubar (philipl)
    * Feature complete tab menu (depends on eggmenubar)
    * tab notebook niceties from epiphany (crispin)
    * Bookmark management that doesn't suck (tko)
          o Galeon 1 style bookmark editor with edit controls in main dialog
          o use xbel properly
    * Cookie management that doesn't suck (probably philipl)
          o Galeon 1 style cookie editor with edit controls in main dialog (spot the pattern? smile )
    * Page info dialog (think mozilla)
          o Clicking security icon should pop up security page in info dialog
    * Native cerificate dialogs
          o Sucks to implement due to strange code factoring in psm
    * Do not set location entry if the user is changing it ! [done]
    * Speedup window creation [some stuff done]
    * Fix exernal downloader + open in new terminal [done?]
    * Test and fix external protocols handling (I got some crashes) [done?]
    * Extensive use of favicons (history, tabs, bookmarks ...) [not there yet]
    * Need a way to get back from fullscreen if you dont know the key [done]
    * Edit->Cut/Copy/Paste need to work also for gtk entries [done?]
    * Fix mime handling dialog to not require to ever go through the apps choice dialog. (My dialog1 proposal on galeon-devel) [done]
    * Tabs context menus [not done - tab menu should also be tab context menu. see above]
    * History context menus [done?]
    * Complete charsets function implementation in mozilla-embed-shell.c, see the FIXME [done?]
    * Reimplement (and maybe redesign) cookie passwords ... filtering [done]
    * Find a way to automagically compute colors for tabs status, that are visible on all themes or get back the color prefs [not done]

As you can see, Galeon has some fairly ambitious goals, as well as having quite a few things done. If you'd like to help, there are numerous things that can be done. Coding, bug reporting, documentation writing, and lucid, positive input are all welcome.

[http://gnomedesktop.org/node/2450](http://gnomedesktop.org/node/2450)
The future of Galeon
Submitted by stro on Sat, 2005-10-22 18:22.  Galeon

Philip Langdale wrote: "Tommi, Crispin and I were all able to attend the GNOME summit last
weekend, even though Crispin had to pay his own way :-) So, it was
a good opportunity for us to sit down and discuss the future of Galeon.
All of us are very much working fulltime which limits the extent to
which we can hack on Galeon and the amount of activity you've observed
speaks for itself.

As such, we've reached the conclusion that we have to change our
approach if we're going to avoid Galeon getting stale or bit-rotting;
which is important for all of us, as we all use Galeon because we
still think it's the best thing out there :-)

So, what does changing our approach mean? It means considering Epiphany
in a new light; Galeon still does a lot of things, small and large, that
Epiphany either doesn't do or doesn't do as well, but at the same time,
there are some areas where they've moved in front, and most importantly
Epiphany has a bunch of active maintainers who are handling the things
that we struggle to do for Galeon. But you say: Epiphany doesn't fit
my needs or I'd be using it already! True, so our proposal is to bring
Galeon to Epiphany.

Epiphany has a powerful extensions mechanism that exposes many of the
core structures of the program and there is a general willingness to
expose more as necessary. This means that many galeon features can be
recast as extensions, and Crispin has already done this for a couple
of things: the sidebar is now in epiphany-extensions and he's got a
few more hidden away such as in-browser view-source. Also don't forget
that some other features have been independently ported as extensions
already, such as the javascript console.
There are a few galeon features which are hard to implement as
extensions and/or are of a class that makes them desirable within the
base Epiphany package, and these should be directly ported. I've already
made a couple of checkins to port back/forward history copying and
middle-clicking on history entries.

Between these two approaches and the more pragmatic direction that
epiphany is moving in these days (heirarchical bookmark support has
just been checked in!), I believe that we can reach a point where
Epiphany + a set of extensions will provide the same functionality that
Galeon does today.

This seems an optimal solution for everyone; it allows us, the galeon
developers, to avoid duplicating work with epiphany team, it will allow
users to leverage the best from both browsers and most importantly, it
puts galeon on a much firmer footing for the future that is not so much
at the mercy of our ability to find time to hack on it.

I hope that this sounds like a good long term strategy to everyone, but
if you do find yourself recoiling from it, do realise that the current
approach is unsustainable and will almost certainly result in galeon
becoming unmaintained or falling too far behind in some areas, meaning
that you'll be struggling to keep using it anyway.

This process will probably take some time given our other commitments,
so we intend to make a formal 2.0 galeon release (long overdue really)
and keep that compiling against newer releases of mozilla, but our
efforts will be directed towards this extension project.

Of course, anybody who wants to help out, either with the extensions
or with maintaining the current galeon codebase, is more than welcome!

I've added a wiki page at: [http://live.gnome.org/Epiphany_2fGaleonIssues](http://live.gnome.org/Epiphany_2fGaleonIssues)
which lists current stuff I can think of. I encourage anyone to add
anything that I've missed, but if you want to list a Galeon 1.2 feature
please categorise it separately :-)"

---

### Post by Zodiac on 2006-05-16
I think I would like it (epiphany) better if I didn't have to have Firefox installed to use it...

---

### Post by isbiyanto on 2010-05-11
> **Wallakoala said:**
> I tried it the other day...its nice. I like it, but I also like firefox.

i am too, (firefox + chrome)

---

### Post by lisati on 2010-05-11
Thread closed, necromancy.

---

