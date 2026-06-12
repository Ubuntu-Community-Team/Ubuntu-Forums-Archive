---
title: "Some nautilus add backs"
date: 2013-02-20
forum: Ubuntu Development Version
---

### Post by mc4man on 2013-02-20
A few things have been added back in nautilus  3.7.90, most notably tree view option in list view & connect to server in sidebar

Somewhat appears that 13.04 will use nautilus 3.8 with the current gtk thru some revert gtk patches. 
(overall a good deal

The option is in preferences as in screen

---

### Post by Baldrick_NZ on 2013-02-20
How do you get into file preferences? I can't see the option in Nautilus.

Cheers.

---

### Post by mcellius on 2013-02-20
>  			 		   		 		 		How do you get into file preferences? I can't see the option in Nautilus.

In Unity, at least for me, it's the Global Menubar (the only menu item there is "Home Folder," go ahead and click it, and you'll see a number of sub-menu items).

---

### Post by mc4man on 2013-02-20
Something a bit different is DnD.
If one DnD's quickly then no different but if you pause or take too long then the folder DnD'ing to opens automatically in that window. Actually not a bad thing.

Where it can get to be a bit of a pain is if DnD'ing something from the Desktop to an open window. Then a ~/Desktop window opens & can get in the way if you don't move fast,  as in real fast.
(gnome-shell doesn't use the Desktop so if & when 3.7/8 shows in unity will be interesting if this behavior is adjusted in some manner.

(if DnD'ing to the Desktop then the open Desktop window is no big deal, same diff

---

### Post by cole.mickens on 2013-02-20
They already tweaking it to keep there from being a weird dangling menu after closing all applications and being dropped on the desktop. It doesn't always work and is sometimes glitchy. They need to just kill off nautilus serving the desktop and get it over with.

So glad we can have some of our basic nautilus functionality back this late through 3.x, yeesh.

---

### Post by mc4man on 2013-02-20
> **cole.mickens said:**
> They already tweaking it to keep there from being a weird dangling menu after closing all applications and being dropped on the desktop. It doesn't always work and is sometimes glitchy. They need to just kill off nautilus serving the desktop and get it over with.

So glad we can have some of our basic nautilus functionality back this late through 3.x, yeesh.

I've no idea if Ubuntu would consider setting nautilus not to handle the Desktop, I'd think there'd be a fair amount of complaint not that that by itself means anything.

In the past there was issue in Unity if nautilus wasn't handling the Desktop, don't quite remember exactly what.
Also the Hud may suffer without a Desktop, myself could care less there but obviously important to Ubuntu. (or at least was..

(- when set to not handle the Desktop then not in Places, returns automatically when handling - screens

If i had to bet I'd say it's staying, at least for now

---

### Post by VinDSL on 2013-02-20
> **mc4man said:**
> In the past there was issue in Unity if nautilus wasn't handling the Desktop, don't quite remember exactly what.
Funny, you should say that...

I never used to let Nautilus handle my desktop(s).  Don't ask me why not... I just didn't.

Then, one day, I was bored and decided to let Nautilus handle the desktop, and it got rid of a nagging issue... but, I can't remember what the issue was.  LoL!

I *think* I simply decided it was better to let Nautilus handle the desktop, than not, and forgot the reason(s).

It was one of those situations where I should have documented it in Gnote or whatever, for future reference, but I didn't.

Now, I'll have to wrack my brain, trying to remember what difference it made...  

Thanks!  :D

---

### Post by Mr. Picklesworth on 2013-02-21
It was a window stacking problem. Unity was doing something strange that led to a lot of its UI (the dash, the launcher) being drawn behind any open windows, unless you had something handling the desktop. Come to think of it, I don't know if it was ever fixed, but I hope it was :o

---

### Post by cole.mickens on 2013-02-21
> **Mr. Picklesworth said:**
> It was a window stacking problem. Unity was doing something strange that led to a lot of its UI (the dash, the launcher) being drawn behind any open windows, unless you had something handling the desktop. Come to think of it, I don't know if it was ever fixed, but I hope it was :o

Yup, still an issue as of a week ago in 13.04. If nautilus isn't drawing the BG, nothing is and weird things happen. I have the launcher hidden and I thought my laptop was hung because it didn't draw my wallpaper over LightDM so it looked like I was at the login screen. (If only Compiz had a wallpaper plugin OH WAIT)

---

### Post by mc4man on 2013-02-21
> **Mr. Picklesworth said:**
> It was a window stacking problem. Unity was doing something strange that led to a lot of its UI (the dash, the launcher) being drawn behind any open windows, unless you had something handling the desktop. Come to think of it, I don't know if it was ever fixed, but I hope it was :o

Doesn't appear to be an issue anymore, initially don't see anything wrong except the upper left panel only clears on switching WS's.
 Hud with no  Desktop seems to work ok on panel items/indicators.

probably will keep nautilus handling here, maybe revert the recent Desktop commits if the pop up windows become annoying

---

### Post by EgoGratis on 2013-02-21
> A few things have been added back in nautilus  3.7.90, most notably tree  view option in list view & connect to server in sidebarGreat!

> I've no idea if Ubuntu would consider setting nautilus not to handle the  Desktop, I'd think there'd be a fair amount of complaint not that that  by itself means anything.Yes this would probably be the turning point for me to look elsewhere. We'll see if it happens.

---

### Post by VinDSL on 2013-02-21
> **mc4man said:**
> Doesn't appear to be an issue anymore, initially don't see anything wrong except the upper left panel only clears on switching WS's.
Ah, yes, that was it!  The upper-left panel...

In my case:  Let's say I was using a browser in WS1, and I switched to WS4 (empty WS / nothing running in it).

The upper-left panel wouldn't clear the name.  It would indicate I was still in the browser WS.

The only way I could clear the upper-left panel was to click on Conky,  which runs in its own window (clearing the name).  Or, I could click on the empty desktop, and it would say "Desktop" (equally irritating).

Letting Nautilus handle the desktop took care of all the nonsense.

I'm making a Gnote of it, this time...  ;)

---

### Post by Mr. Picklesworth on 2013-02-21
> **EgoGratis said:**
> Great!

Yes this would probably be the turning point for me to look elsewhere. We'll see if it happens.

It doesn't have to mean an empty desktop. KDE hasn't had a file manager drawing its desktop for years, now, and it's worked out great. Plasma does have various file-related widgets, but it's far prettier and very flexible - and it makes it really easy for people to choose the file manager(s) they prefer, instead of being tied to the specific one that comes with the system.

With the huge amount of information Unity has access to, there's all sorts of cool stuff that could be done with the desktop that isn't just managing files. And even if it is just managing files, it would be nice to have that done in a way that at least *tries* to fit with the rest of the UI.

So, yes, I'm quite happy that it's getting harder and harder to justify using Nautilus to draw the desktop :)

---

### Post by mc4man on 2013-02-21
The only other diff I see is that without naut handling some of the current & continuing stacking & or focus issues are slightly different
(but still present

So in cases where a nautilus window currently opens under another window it would open on top but without focus.

Focus & or stacking issues in Unity aren't limited to nautilus though it's the most prevalent & reproducible

Some current naut ex. - 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1119798](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1119798)
(noting someone changed my orig. descrip & I don't exactly agree there - no matter, unlikely to be fixed anyway

---

### Post by EgoGratis on 2013-02-21
> It doesn't have to mean an empty desktop. KDE hasn't had a file manager  drawing its desktop for years, now, and it's worked out great. Plasma  does have various file-related widgets, but it's far prettier and very  flexible - and it makes it really easy for people to choose the file  manager(s) they prefer, instead of being tied to the specific one that  comes with the system :)Yes in KDE first thing i do is usually enable classic desktop. Desktop full of icons and folders and right click menu and then i bloat it and bloat it some more and then i clean the mess and do it all over again. There really is nothing like it. Other approaches i know of don't come close and often fall short in many aspects.

> With the huge amount of information Unity has access to, there's all  sorts of cool stuff that could be done with the desktop that isn't just  managing files. And even if it is just managing files, it would be nice  to have that done in a way that at least *tries* to fit with the rest of the UI.Yes if we look how Ubuntu on mobile devices work it's basically Unity in full screen mode Desktop is gone and i guess GNOME with GnomeShell is the same story.

There is nothing wrong with that but where the things starts to get moot is desktop computing where you have keyboard, big screen and mouse... I do believe we will have to let go the way we used computers in the past few decades BUT there really isn't any excuse why this should not be kept in Nautilus/Files for  next decade or more. 

Is it really that hard to maintain the code if it sits there does the universe spin in the wrong direction if the code sits there? Does it take 100 developers just to maintain it? I guess it does not.

I am not against innovation and yes for sure experiment do what ever you like built desktop of the future why not but knowing how things worked in the past removal of the code would only bring wallpaper to stare at and some funky widgets that fall short.

Bottom line leave the code and checkbox there don't act silly and you can still innovate as much as you would like. The fact old (decades old) proven way of desktop computing still sits there doesn't hold you back to create something that will not fall short and will be used for next few decades. BUT WE ARE NOT THERE YET. And no mobile touch UX is not it and i doubt it will be anytime soon it might just complement in some ways traditional desktop and it is sad in a way nobody want's to build and improve classic desktop anymore. For example when was the last new cool feature for classics GNOME  Desktop made? And no GnomeShell is not it!

---

### Post by mc4man on 2013-02-21
On a positive note they did remove DnD hover on the Desktop yesterday though they also removed the Desktop altogether. (bg or whatever
(- something else for Ubuntu to work out...

As far as tree view - 
still has this minor 'resize' issue, not that important.

The folder & arrow size seem a little big here, certainly when I compare to treeview in 3.6.x done thru personal patch.
Don't know which I prefer though am leaning towards later
screen 1 current supported in 3.7.9+, screen 2 unsupported in 3.6.x
(maybe one can resize them, didn't see way yet

---

### Post by jbicha on 2013-02-21
> **mc4man said:**
> (maybe one can resize them, didn't see way yet

On the first tab of preferences, try the list view default zoom.

---

### Post by mc4man on 2013-02-21
> **jbicha said:**
> On the first tab of preferences, try the list view default zoom.
Thanks - sometimes I miss what's right in front of me..

Hopefully your request to merge gets approved.

Edit: - just to note - the resize issue isn't my inability to see resizing list view icons, it's a 'jitter' that can occur in list view when bring nautilus to focus or clicking on window deco, ect. 
Don't know if it occurs in gnome-shell, fairly longstanding in a unity session.

---

### Post by dino99 on 2013-02-22
its Help -> "about" still display 3.6.3  ;)

---

### Post by VinDSL on 2013-02-22
> **dino99 said:**
> its Help -> "about" still display 3.6.3  ;)


[INDENT]:confused:

[[IMG]http://vindsl.com/images/vindsl-desktop-22-feb-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-22-feb-2013-1.png")[/INDENT]

---

### Post by dino99 on 2013-02-22
> **VinDSL said:**
> :confused:

i'm not using the gnome3 ppa here; and it still show 3.6.3  ;)
but hey, nothing to scratch my hair :)

---

### Post by VinDSL on 2013-02-22
> **dino99 said:**
> i'm not using the gnome3 ppa here; and it still show 3.6.3  ;)
but hey, nothing to scratch my hair :)
Heh!  Thanks, for the clarification...  ;)

---

