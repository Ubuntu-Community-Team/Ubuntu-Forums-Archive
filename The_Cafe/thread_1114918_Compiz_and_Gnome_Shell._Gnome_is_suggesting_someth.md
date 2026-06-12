---
title: "Compiz and Gnome Shell. Gnome is suggesting something really dumb."
date: 2009-04-03
forum: The Cafe
---

### Post by Islington on 2009-04-03
> Doing something about gnome-shell. GNOME-Shell is a tricky issue for us because it integrates the window manager with the panel (or at least loads the panel as a plugin to the window manager). This basically means that if you launch compiz in future GNOME versions, you lose your panel. KDE sort of has a similar issue, in that the desktop is tied in with the panel, but that makes sense anyways because there aren’t really any other desktop shells that are designed to replace the default desktop (other than SpringDesk of course, but that is on hold ATM and would probably have a panel of it’s own). I already made a post to the GNOME-desktop-devel about this, but they have told me that tight integration is needed between the panel and the window manger so that the ‘overview’ mode can be done correctly (which I disagree with, you could just have shell expose it’s drawing handle and register functions in the WM (or it’s plugins) that would do the overlay mode for you). Unfortunately, their view on this is that ‘people want it to Just Work (TM) and don’t really care about other window managers’, hence locking out compiz from GNOME. Yeah, inter-project co-operation. It sucks. We basically have two options - fork / rewrite shell and maintain it for compiz (and allow it to be compatible with it’s own set of extensions), which we can’t do with the amount of developers we have or convince the GNOME folks to turn shell into a lib that can easily be used with other WM’s.from [Sam (Developer)](http://smspillaz.wordpress.com/2009/04/02/compiz-09x-where-are-we-now-and-where-to-from-here/)

Not allowing me to change window manager, without losing functionality? W.T.F. Just Work(tm) doesn't mean that I have to be stuck with an inferior product(Metacity), which I cant replace. I had quite enough of that in Windows (Still cant remove IE). Look, I am just a user, I know no languages other than some BASIC. And I know that the developers don't really have to care about anything I say. But please, I really do feel this is a mistake. Isn't Linux supposed to be small independent programs working together? Please, Please, Please don't take away my option/freedom to change window managers.

What do you feel about this? Is there any way we can contact any gnome devels and beg/whine at them to change their mind?

---

### Post by Polygon on 2009-04-03
i don't really see why they are doing this...they must have some reasoning

either way its stupid. major distros like ubuntu and maybe others are shipping with compiz. I'm sure the collective complaining from the linux world will get them to change it.

---

### Post by Mehall on 2009-04-03
To paraphrase Homer Simpson,

"You don't like it, go to Crunchbang"

Or any other WM, tbh.

I only use GDM, but it could easily be replaced by SLiM if it had to be.

---

### Post by Mr. Picklesworth on 2009-04-03
On the other hand, the shell as a window manager has many visual effects that, frankly, already work better than Compiz.

Further, GNOME is *meant* to be an integrated solution. If you want something modular, use one of the myriad of such window managers / desktop environments out there, like XFCE. For that matter, this change just puts GNOME in the same style as those (quite successful!) window managers that people happily work with completely, like Wmii or Awesome.
I can't say I really understand the whole "window manager + panel" thing yet in terms of what it brings to the table, but I can see how it would help with transitions to have all that stuff handled in one place. I suspect it would let the environment apply little quirks to window management such as tracking which launcher an application came from and performing awesome stuff with the knowledge. (Although that could still be done without taking over window management outright).

Compiz is becoming redundant and simply is not going to work as a drop-in replacement for the big desktop environments. This has always been inevitable. The mature choice would be for the Compiz people to accept that and either target the more modular environments or start accepting what the thing presently is: A (fantastic) *experiment* that had its moment in the sun. Compiz has a lot of great effects code, and the Compiz developers know that code best, so I think it would be pretty cool of them to start contributing to their favourite desktop-integrated window managers directly (be they KWM or Metacity) instead of struggling to maintain a redundant product where such a thing doesn't need to exist.

---

### Post by forrestcupp on 2009-04-03
I agree with Mr. Picklesworth.  Compiz is awesome.  But I think it is just a temporary patch to catch us up with the times until the major DE's get around to becoming relevant.  KDE has never really worked excellently with Compiz, and they finally got around to incorporating their own compositing with decent effects.  I believe that is where Gnome is heading, and where it must head if it wants to remain relevant.  They already have good compositing with Metacity; now they just need to polish it up with a good arsenal of effects to go with it.

Compiz is just a bandage that is coming close to having served its purpose.  But we're thankful for what it has done for us.

---

### Post by gnomeuser on 2009-04-03
Integration here allows for less abstraction and better functionality as well as stability. Aside that Compiz have never shown any interest in addressing any number of the issues that stopped it from being a good windows manager for GNOME, why then should GNOME suddenly up and add unneeded abstraction layers to please Compiz when Mutter is perfectly capable of doing the exact same thing only better from the prespective of GNOME.

Regardless, read the whole thread, it is amply addressed why this is being proposed. It is one of many possible routes to take, it is not being proposed without clear reasoning, go back and read Havoc' post please.

---

### Post by Monster_user on 2009-04-03
Well, I don't use Metacity, or Gnome very often. 

I'm not too sure I'm fond of this idea. KDE4 still isn't as effecient as Compiz on several tasks. I find myself changing the Window Manager, just to improve desktop performance. Leaving the same effects enabled.

*Transparent Windows when moving, shadows, Expose', Taskbar Thumbnails.*

If Gnome can't match the performance of Compiz, I may never use Gnome again.

---

### Post by Sealbhach on 2009-04-03
Having to use Compiz Fusion icon to change window manager whenever I want to play games or use Google Earth is not a great solution. I would still like to have all the fancy effects though.


.

---

### Post by smartboyathome on 2009-04-03
I think they are going the way of Enlightenment. ;)

---

### Post by Skripka on 2009-04-03
> **smartboyathome said:**
> I think they are going the way of Enlightenment. ;)
 
You mean Gnome 3.0 is going to take 4 years to come out of beta? :lolflag:

---

### Post by chris4585 on 2009-04-03
> **monster_user said:**
> well, i don't use metacity, or gnome very often. 

I'm not too sure i'm fond of this idea. Kde4 still isn't as effecient as compiz on several tasks. I find myself changing the window manager, just to improve desktop performance. Leaving the same effects enabled.

*transparent windows when moving, shadows, expose', taskbar thumbnails.*

if gnome can't match the performance of compiz, i may never use gnome again.

[color="red"][size="7"]+1[/size][/color]

I agree, except I use Gnome and Compiz often, and this would probably be horrible for me, I'd just switch to openbox again.

---

### Post by Mr. Picklesworth on 2009-04-03
> **chris4585 said:**
> [color="red"][size="7"]+1[/size][/color]

I agree, except I use Gnome and Compiz often, and this would probably be horrible for me, I'd just switch to openbox again.

So there's the other side to this story:

OpenBox is a window manager that you load as a full session, featuring launchers and panels built right in to the WM. As are MANY others, with really the only major *exceptions* being Xfce, Kde and Gnome.

What is so different about Gnome doing this vs. OpenBox?

---

### Post by cinna on 2009-04-03
KDE is nothing like this anymore, where the panel reflects the theme selected, In kde it is possible to mix and match any aspect of a theme with other themes, beit panel, start menu, and so on

---

### Post by smartboyathome on 2009-04-03
> **Skripka said:**
> You mean Gnome 3.0 is going to take 4 years to come out of beta? :lolflag:

I mean Enlightenment is what the devs call a "desktop shell", since it is similar to what Windows desktop shells are, and now Gnome is going that route.

It is true though, E17 is much like Debian Testing, liable to break at any time! :P

---

### Post by pt123 on 2009-04-03
More backward views and steps by Gnome, Compiz is very popular and one of the main attractions on the Linux Desktop to bring in new users. 
They need to be able to provide a better solution so people still can continue to use compiz. Canonical needs to step in and put the foot down.

Gnome should work on something more useful to the user like changing the number of lines scrolled by the mousewheel.

This would be a disaster like Gnome trying to implement Webkit into Epiphany.

---

### Post by mc4100 on 2009-04-03
Here's the discussion on [desktop-devel]("http://www.mail-archive.com/desktop-devel-list@gnome.org/msg15602.html").
I know compiz is one of the big things attracting new-users, and, though I use metacity, I still find compiz rather useful and like to switch between them. Hence, this is a bit of a blow:
> So, basically, no I don't see a way that GNOME Shell coexists with
Compiz other than as two separate shells for the GNOME desktop.

---

### Post by gnomeuser on 2009-04-03
> **mc4100 said:**
> Here's the discussion on [desktop-devel]("http://www.mail-archive.com/desktop-devel-list@gnome.org/msg15602.html").
I know compiz is one of the big things attracting new-users, and, though I use metacity, I still find compiz rather useful and like to switch between them. Hence, this is a bit of a blow:

And you, like pretty much everyone in this thread, completely and entirely miss the point of the d-d-l thread. Read it, nobody is taking your bling away, it is no longer being fueled by compiz for various technical reasons. It will in the future be provided by an integrated solution called Mutter which is extendable to bring all the useless crack Compiz has. And even at that, this is just one of 3 proposed options which is up for debate.

---

### Post by pt123 on 2009-04-03
> **gnomeuser said:**
>  Read it, nobody is taking your bling away, it is no longer being fueled by compiz for various technical reasons.
Haha more like informing on Compiz and trying to steal it's clientèle. 

Gnome needs to stop using the dirty tactics to steal markets, they are acting like Microsoft. 

Just like how Firefox has more users than Epiphany because it is far more powerful and innovative, Compiz will be to what ever Gnome produces. 

This will be another half complete application like other Gnome applications that are pathetic attempts to steal market share from renown open source applications.

Just another waste of resources by Gnome. Rather than working on new concepts to improve their forte,  they are trying to steal markets and seize control of areas other open source organisations have created through innovation.

---

### Post by SomeGuyDude on 2009-04-03
> **Mr. Picklesworth said:**
> So there's the other side to this story:

OpenBox is a window manager that you load as a full session, featuring launchers and panels built right in to the WM. As are MANY others, with really the only major *exceptions* being Xfce, Kde and Gnome.

What is so different about Gnome doing this vs. OpenBox?

Wait, what? OpenBox has panels and launchers built into the WM??

---

### Post by cinna on 2009-04-03
Relevant to the thread [http://www.youtube.com/watch?v=Y9KC7uhMY9s](http://www.youtube.com/watch?v=Y9KC7uhMY9s) :lolflag:

---

### Post by forrestcupp on 2009-04-04
> **pt123 said:**
> 
Just like how Firefox has more users than Epiphany because it is far more powerful and innovative, Compiz will be to what ever Gnome produces.
No, Firefox has more users than Epiphany because they have a Windows version and it's pretty much the offspring of Netscape Navigator.

You can't compare the Compiz/Mutter thing to Firefox/Epiphany; it's a totally different scenario.  I guarantee that if Gnome made it impossible to run Firefox, there would be a lot more Linux users using Epiphany.

Anyway, if they truly make Mutter extendable, the community will come up with effects that equal Fusion's.

---

### Post by linuxisevolution on 2009-04-04
We could just make compiz have it's own similar panels ;)


Or Compiz could join with Gnome...

I think this is a good idea, because Gnome is very unstable on this system... It will crash to the point were I can't click anything, and I lose my panels.

Running 2.22.3...

---

### Post by Monster_user on 2009-04-04
Are you running Compiz?

---

### Post by damis648 on 2009-04-04
> **linuxisevolution said:**
> We could just make compiz have it's own similar panels ;)


Or Compiz could join with Gnome...

I think this is a good idea, because Gnome is very unstable on this system... It will crash to the point were I can't click anything, and I lose my panels.

Running 2.22.3...

Well Compiz joining GNOME would be an interesting idea. I would vouch for it. :popcorn: GNOME could have unrivaled compositing.

EDIT: As long as there was support for non-compositing and compatibility with older hardware.

---

### Post by linuxisevolution on 2009-04-04
> **Monster_user said:**
> Are you running Compiz?

Me? Yes.

---

### Post by linuxisevolution on 2009-04-04
> **Monster_user said:**
> Are you running Compiz?

It happens when I'm not using it though. And when it does happen I have to ctrl+alt+backspace and then I can't log back in. (well sometimes I can but just pidgin and my wallpaper come up, and no panels or icons).

I can log back into Gnome though if I use openbox as the wm.

---

### Post by linuxisevolution on 2009-04-04
> **damis648 said:**
> Well Compiz joining GNOME would be an interesting idea. I would vouch for it. :popcorn: GNOME could have unrivaled compositing.

EDIT: As long as there was support for non-compositing and compatibility with older hardware.

+1

XFCE and kde have their own compositing, why not Gnome? :p

---

### Post by damis648 on 2009-04-04
> **linuxisevolution said:**
> +1

XFCE and kde have their own compositing, why not Gnome? :p

Well GNOME 3 is planning to integrate Clutter as a compositing engine, but somehow I still like Compiz. Maybe if they did join they could better integrate the compositing like Vista and Mac OS X, where every part of the system is composited, not just animating windows but transparent glass and fun little animations.:popcorn:

---

### Post by linuxisevolution on 2009-04-04
> **damis648 said:**
> Well GNOME 3 is planning to integrate Clutter as a compositing engine, but somehow I still like Compiz. Maybe if they did join they could better integrate the compositing like Vista and Mac OS X, where every part of the system is composited, not just animating windows but transparent glass and fun little animations.:popcorn:

Exactly, except the kernel devs would never integrate the gui with the kernel, thats one of the reason Windows sucks so badly...


Maybe there could be a desktop kernel, with the gui integrated, and a server kernel, with no gui integration, but still Xorg compatible. That's what syllable OS is doing.

Very efficient that way too.:popcorn:

---

### Post by sertse on 2009-04-04
Or the completely out there thought.

Compiz evolves as a wm/de/whatever itself?

It's already somewhat possible to have "compiz standalone" as shown by some of those in the sceenshot thread. Having deskmenu (Compiz having a right click menu, like xfce/*box) goes some way into making it work...)

---

### Post by linuxisevolution on 2009-04-04
> **sertse said:**
> Or the completely out there thought.

Compiz evolves as a wm/de/whatever itself?

It's already somewhat possible to have "compiz standalone" as shown by some of those in the sceenshot thread. Having deskmenu (Compiz having a right click menu, like xfce/*box) goes some way into making it work...)

Compiz already is a wm itself..

---

### Post by &#32 Greg on 2009-04-04
I happen to like/use compiz; it makes me more efficient (except when I start playing with water/fire effects). I don't think that this will even necessarily be bad for it; as sertse said it can end up evolving into a standalone... maybe package a desktop bar, a right click menu, Avant, PCManFM, SLiM,and gqview or the like and call it a DE.

---

### Post by linuxisevolution on 2009-04-04
It seems that with Linux almost everything goes into it's own project with time.

Then they all get clashed together to form a Distro.

Then that distro starts setting a "standard" (like compiz+Gnome) and things become a mess...


Oh well...

---

### Post by &#32 Greg on 2009-04-04
That's part of the reason I like Arch, actually. A distro is just someone else's idea of an ideal desktop packaged so others can see. My ideal desktop is probably different from there's so I'd rather start minimally.

---

### Post by linuxisevolution on 2009-04-04
> **  Greg said:**
> That's part of the reason I like Arch, actually. A distro is just someone else's idea of an ideal desktop packaged so others can see. My ideal desktop is probably different from there's so I'd rather start minimally.

Arch is what Ubuntu should have been.

FreeBSD is what Linux should have been...

---

### Post by 23meg on 2009-04-04
This reminded me of a point I had made regarding Compiz [three years ago]("http://ubuntuforums.org/showthread.php?p=1127262#post1127262") (the level of the discussion warrants no excuses for quoting myself):

[QUOTE=23meg]Compared to the sophistication of Xglx/Xegl or AIGLX, Compiz is a very superficial bit of software, and it may not even find widespread use and be remembered as a technology teaser in the future, since for example Metacity already has its own composite manager, and other projects may come along that can replace it, while borrowing code from it. Many of the freedesktop.org developers feel that it's easier to integrate a compositor into a window manager that's taken years to mature than make an app written from scratch be both a compositor and a window manager, and Compiz is trying to do the latter.[/QUOTE]

Compiz did "find widespread use", due to the fact that it was later shipped as a default in Ubuntu and some other popular distributions. It probably did inspire and encourage many would-be FOSS users. It did "win" that part of the challenge on the simplest of terms that the history of software development has favored time after time: on terms of *being immediately available* where no alternatives exist, albeit at a half-baked state.

Looking at how much Compiz has matured as a WM along these years, how well the dirty hacks that tie the composited and non-composited desktop experiences together are holding up, how consistent those two sets of experiences are, and how well Compiz plays along with GNOME, X, Flash, Firefox and other important desktop oriented upstreams that are high priority for Ubuntu as of today, you can draw your own conclusions from the above prediction.

---

### Post by linuxisevolution on 2009-04-04
Why can't everything stay the way it is?


The only thing I dislike is Xorg...

---

### Post by BGFG on 2009-04-04
> **linuxisevolution said:**
> Why can't everything stay the way it is?


Because Linux is evolution. ;)

---

### Post by smartboyathome on 2009-04-04
> **linuxisevolution said:**
> Why can't everything stay the way it is?

From the movie Ratatouille:
"You can't change nature, son. That is how things are."
"Change *is* nature, Dad. The part that we influence. And it [change] start when we decide."
Because everything changes over time, nothing can stay the same forever. That is why stuff like this happens.

---

### Post by days_of_ruin on 2009-04-04
Has anyone here seen the screencasts? It looks real slick.
[http://live.gnome.org/GnomeShell/Screencasts]("http://live.gnome.org/GnomeShell/Screencasts")

---

### Post by gnomeuser on 2009-04-04
> **linuxisevolution said:**
> 
The only thing I dislike is Xorg...

You're in luck, X is gradually being pushed into the 21th century with DRI2, MPX and KMS as well as XI2. And further on in our bright future we might even get to architect Wayland to replace the existing X server.

There arte many things I dislike about Linux and would like to see improved though, luckily it is happening little by little.

---

### Post by cardinals_fan on 2009-04-04
> **linuxisevolution said:**
> 
The only thing I dislike is Xorg...
So try Xvesa :)

---

### Post by Mr. Picklesworth on 2009-04-04
> **days_of_ruin said:**
> Has anyone here seen the screencasts? It looks real slick.
[http://live.gnome.org/GnomeShell/Screencasts]("http://live.gnome.org/GnomeShell/Screencasts")

Also, if you are curious what GNOME Shell is all about, it's actually fairly stable *right now*. You can follow the instructions under "Building" and "Running" in the [Gnome Shell Wiki page]("http://live.gnome.org/GnomeShell").

Just make sure you DO THIS IN A DIFFERENT USER ACCOUNT. I created a regular (not administrator) account called test-user and did all the building / running in there. I did this under Jaunty with jhbuild and gnome-devel installed from the repos (probably some other stuff needed as well, but I don't know what since I already had all the dependencies). Good luck!

Keep in mind that this project is young and ripe for all sorts of contributions, and that nothing is close to final.

It's inspired me to peek at the source code because I just realized this could, with some work, completely solve that problem with apps such as music players and instant messagers trying to shrink themselves away by abusing the notification area. (How about dragging them into a little dock to the side of the Activities screen, where they remain as full windows / turn into applets... then when they want attention they can use the standard window urgency hint and expect the awesome WM to, err, do something awesome!).

Not that the problem needs as much solving with this anyway, though; Gnome Shell's notification area looks super pretty, with even spacing and icon sizes at last :)

---

### Post by pt123 on 2009-04-04
> **forrestcupp said:**
> No, Firefox has more users than Epiphany because they have a Windows version and it's pretty much the offspring of Netscape Navigator.

You can't compare the Compiz/Mutter thing to Firefox/Epiphany; it's a totally different scenario.  I guarantee that if Gnome made it impossible to run Firefox, there would be a lot more Linux users using Epiphany.

Please on Linux itself (and on Gnome) Firefox has more users than Epiphany by a mile. It is a far advanced browser made by an organisation that's main focus is browsers, it is not some hack job that imports most of the core code from another organisation's hard work, that Epiphany is. 

Rofl if Gnome made it impossible to run Firefox most users and distributions like Ubuntu will move to KDE. The browser is the most important application on the user's desktop, and Firefox carries a lot of weight. For them to have captured 20% marketshare from Microsoft speaks volumes for their browser. 
 
People cry about Microsoft using dirty tactics to give them an advantage when entering a rival's market, Gnome is doing the same. 

If anything they should make it possible for Compiz to still run on Gnome and also develop Mutter, let the user decide which is the better application.

---

### Post by linuxisevolution on 2009-04-04
> **BGFG said:**
> Because Linux is evolution. ;)

haha gotcha.

I was waiting for someone to catch that question and tie it with my name :p

---

### Post by Sand &amp; Mercury on 2009-04-05
I gave Gnome-Shell a go yesterday. It's nowhere near finished yet, but it's surprisingly mature and stable for me, even if the presentation right now leaves much to be desired.

If this is to be the replacement for Compiz, I'll have no complaints.

---

### Post by forrestcupp on 2009-04-05
> **pt123 said:**
> Please on Linux itself (and on Gnome) Firefox has more users than Epiphany by a mile. It is a far advanced browser made by an organisation that's main focus is browsers, it is not some hack job that imports most of the core code from another organisation's hard work, that Epiphany is. 

I hear ya.  But my point was that they already have a huge market share on Windows.  Most Linux users start on Windows.  When they switch to Linux, they are going to use something they're familiar with if it's available.  That's why Firefox is used in Linux much more than Epiphany.

I'm not saying that Firefox isn't better than Epiphany.  But I *am* saying that Epiphany isn't as bad as people think and that a lot of people have a bad opinion of Epiphany without even trying it.

---

### Post by hanzomon4 on 2009-04-05
> **forrestcupp said:**
> I hear ya.  But my point was that they already have a huge market share on Windows.  Most Linux users start on Windows.  When they switch to Linux, they are going to use something they're familiar with if it's available.  That's why Firefox is used in Linux much more than Epiphany.

I'm not saying that Firefox isn't better than Epiphany.  But I *am* saying that Epiphany isn't as bad as people think and that a lot of people have a bad opinion of Epiphany without even trying it.

I can't even turn spellcheck on... I try it every new release and it sucks every time.

---

### Post by BGFG on 2009-04-05
> **linuxisevolution said:**
> haha gotcha.

I was waiting for someone to catch that question and tie it with my name :p

I like your style :)
as for 3.0, i'll take the wait and see approach. Or just until it's stable enough... Would like to see what the OpenSolaris engineers will do with it considering it's being redone in one of their native codes.

---

### Post by pt123 on 2009-04-05
> **forrestcupp said:**
> But I *am* saying that Epiphany isn't as bad as people think and that a lot of people have a bad opinion of Epiphany without even trying it.
I wouldn't blame them it has been a been a mess since they started trying to switch over to webkit. Developers just ignore serious bugs on Epiphany-Gecko.

---

### Post by forrestcupp on 2009-04-06
> **pt123 said:**
> I wouldn't blame them it has been a been a mess since they started trying to switch over to webkit. Developers just ignore serious bugs on Epiphany-Gecko.

Well, that may be.  But before they started to switch, I wouldn't say it was a total disaster.  

But it's true that things are always messy during that major of a transition.  I think in the long run it may be a decent choice to switch to webkit.  It's hard to say.  On one hand, there are a lot of web pages that support Firefox/Gecko that won't support webkit yet.  But on the other hand, Gecko seems clunkier.

---

### Post by Mr. Picklesworth on 2009-04-06
> **forrestcupp said:**
> Well, that may be.  But before they started to switch, I wouldn't say it was a total disaster.  

But it's true that things are always messy during that major of a transition.  I think in the long run it may be a decent choice to switch to webkit.  It's hard to say.  On one hand, there are a lot of web pages that support Firefox/Gecko that won't support webkit yet.  But on the other hand, Gecko seems clunkier.

I, for one, can confirm that the WebKit version is stupendously smooth and low on memory consumption. It blows the Gecko version (and, by extension, Firefox) out of the water in that department. Granted, still buggy, but it looks good for a stable WebKit-powered Epiphany in 2.28 (thus Ubuntu 9.10). Actually, the whole GNOME platform is moving to WebkitGTK, over from a horrible mix of Gecko and GTKHTML (or whatever it was called). So far it's a nice transition.

> **pt123 said:**
> Please on Linux itself (and on Gnome) Firefox has more users than Epiphany by a mile. It is a far advanced browser made by an organisation that's main focus is browsers, it is not some hack job that imports most of the core code from another organisation's hard work, that Epiphany is. 

Rofl if Gnome made it impossible to run Firefox most users and distributions like Ubuntu will move to KDE. The browser is the most important application on the user's desktop, and Firefox carries a lot of weight. For them to have captured 20% marketshare from Microsoft speaks volumes for their browser. 
 
People cry about Microsoft using dirty tactics to give them an advantage when entering a rival's market, Gnome is doing the same. 

If anything they should make it possible for Compiz to still run on Gnome and also develop Mutter, let the user decide which is the better application.

I get the feeling that you really need to read [The Cathedral and the Bazaar]("http://catb.org/~esr/writings/cathedral-bazaar/") (or [listen to the talk]("http://catb.org/~esr/writings/cathedral-bazaar/linux1_d50_96kbs.mp3")) or something.

GNOME isn't going to make it impossible to run Firefox, but a good platform chooses certain components to use by default and runs with them. If that wasn't allowed to happen, we wouldn't have an operating system. Imagine, for example, if GNOME never decided on a UI toolkit and we had GTK + Qt and a bit of FLTK all mixed in one place. Sure, you could go and say "GNOME is awesome for giving the all-important options!" but hardly anyone would care because GNOME would be *unusable*.
You can't throw the user, or the developers of a distro, a pile of bricks and tell him "build your own! Isn't it nice that we thought of you and left everything unassembled!"
And yes, having a billion options, even in a pre-assembled operating system, is no different.

If you want to fiddle, use apt-get source and have fun. GNOME is moving to git this month, so that should be *particularly* fun quite soon.
If you don't want to bother with that, I don't see why you expect developers to waste their time building secondary features for no good reason. 


As for the Epiphany vs. Firefox thing, which I think it would be really unfair to get into, let's look at it this way (the sensible way): Epiphany is not directly "competing" with Firefox. Sure, Epiphany *users* are, but that's different. Epiphany is offering an alternative web browser that fits snugly into the GNOME platform and that uses GTK; two features not offered by Firefox. (Looking like GTK is not the same as using it. I can make Windows' UI look like GTK, but it's still a horrible static positioned UI system).

No, Epiphany isn't Firefox + GNOME, but neither is Chrome or Opera. They all offer good and bad points.

Lastly, calling it a hack job is really uncalled for. I would almost think you're trying to incite a riot.
It doesn't sound like you much like or trust GNOME, so perhaps you should use Kubuntu, or (if you are okay with small chunks of the project like Glib) Xubuntu.
I should warn you about Kubuntu: it dares to make decisive choices about the platform since developers need solid ground to work on.



Oops! Before I go, I guess I forgot to address the important part. Compiz does run in GNOME with the shell. It's just that now the window manager carries more weight, as it also involves itself with closed windows and applications. If you run Compiz, you lose the shell. It's no different from how, before, running Compiz lost you sensible window stacking. Compiz is quite a flexible window manager, so I'm sure they can put in a solution if they need to, but poking Mutter full of callbacks won't solve anything.

---

### Post by Monster_user on 2009-04-07
> **Mr. Picklesworth said:**
> Oops! Before I go, I guess I forgot to address the important part. Compiz does run in GNOME with the shell. It's just that now the window manager carries more weight, as it also involves itself with closed windows and applications. If you run Compiz, you lose the shell. It's no different from how, before, running Compiz lost you sensible window stacking. Compiz is quite a flexible window manager, so I'm sure they can put in a solution if they need to, but poking Mutter full of callbacks won't solve anything.

There is a difference between loosing sensible Window Stacking, and loosing the shell altogether. Many don't even use Window Stacking, and prefer the "Expose' " feature instead. 

The shell however, is such a critical element. If Mutter is adopted, there would be no simple method of allowing Compiz to continue to function.

If Compiz moves to create their own shell, it would put them just short of a full-blown Desktop Environment. They might just piggyback on the Gnome back-end for a while,...

---

### Post by pt123 on 2009-04-07
> **Mr. Picklesworth said:**
> I, for one, can confirm that the WebKit version is stupendously smooth and low on memory consumption. It blows the Gecko version (and, by extension, Firefox) out of the water in that department. Granted, still buggy, 
This is another the problem they are so late on deliverables, this will plaque Mutter too. What is worse is that if they break  Compiz,  thwy're are not giving users an option to use Compiz till Mutter is actually a complete and better solution. 

> 
I get the feeling that you really need to read [The Cathedral and the Bazaar]("http://catb.org/~esr/writings/cathedral-bazaar/") (or [listen to the talk]("http://catb.org/~esr/writings/cathedral-bazaar/linux1_d50_96kbs.mp3")) or something.
lol handing reading materials, sounds like brainwashing.

> 
GNOME isn't going to make it impossible to run Firefox, but a good platform chooses certain components to use by default and runs with them. 
I hope this doesn't refer to me, as I was only replying to another post discussing a ridiculous scenario.

> 
Epiphany is offering an alternative web browser that fits snugly into the GNOME platform and that uses GTK; two features not offered by Firefox. 
I have less of an issue with providing alternatives. But you shouldn't disadvantage a competitor (Compiz) to provide your own (Mutter) that is a Microsoft practice. The real loser is the user. 

> 
Lastly, calling it a hack job is really uncalled for. I would almost think you're trying to incite a riot.
It is the way are handling it in the last few releases. 

> 
It doesn't sound like you much like or trust GNOME, so perhaps you should use Kubuntu,
 
Kubuntu is like the "step child" in the Ubuntu fam. and it receives little attention. I also don't like the cluttered nature of the KDE UI.

---

### Post by Mr. Picklesworth on 2009-04-08
But this is what you are missing: Nobody is being attacked here. One product is simply becoming more powerful while another horrible, bloated, old, usability-challenged and frankly unfixable component (gnome-panel) is being dropped.

Meanwhile, it looks like the Compiz folks may approach this in a way that improves their product anway, realizing that the different desktop environments are moving towards strong integration between a window manager and the rest of the platform. (Which demands a specific WM be used).
The sensible approach to keeping Compiz alive is a Compiz desktop environment, and with the existing stuff they could achieve that admirably.
Doing so is completely logical and requires less work for all parties involved.


> **pt123 said:**
> lol handing reading materials, sounds like brainwashing.
Depends.  Do you actually care about this stuff or are you just raising a fuss for the sake of raising a fuss?
For most of the free software community, understanding that work is part of the path to enlightenment ;)

Feel free to maintain / help maintain / encourage the existence of a branch of gnome-shell detached from the window manager. Maybe once the dust has settled the change in functionality won't be too big and you'll be owed beers for life.

A note about software releases: Breaking major version means changes. That means deprecating stuff. It means that old software, old ideas, stop applying. Period.
If that didn't happen, you could be staring at a black & white screen with Microsoft DOS installed. One nice thing about it all being open source is that the projects (or at least their code) do not die; just products derived from those projects.


Last but not least:
GNOME is not Microsoft. Or, for that matter, evil. They provide alternatives because alternatives are nice to have, especially when they target different use cases. (Again, modularity is there in countless other desktop environments that don't strive for the same level of cohesiveness).
Further, I think you already know that. Don't bite the hand that feeds you and all that. It makes me sad when people do it.
Thank you.

---

### Post by ghindo on 2009-04-08
> **pt123 said:**
> lol handing reading materials, sounds like brainwashing.It gives you a common point of reference.  "Brainwashing" is a bit of a hyperbole.

---

### Post by malachi1990 on 2009-05-30
Two quick things to add"

A.  Sorry for dredging this up, but it was a stumble on as I tried to start using gnome-shell.

B. To the persons complaining: GNOME-SHELL IS STILL IN ALPHA STAGES!!!!!!!  This is not a final product by any means.  This whole thread is at least 5-6 months early (i.e. once gnome-shell hits beta), and is as such, nearly irrelevant. The Gnome devs haven't had time to implement a solution to this.  

While it is good to bring up concerns, the way this thread is titled is biased against what the GNOME devs are doing.  Not really a good way to go.

---

### Post by don_quixote on 2009-05-30
> **malachi1990 said:**
> Two quick things to add"

A.  Sorry for dredging this up, but it was a stumble on as I tried to start using gnome-shell.

B. To the persons complaining: GNOME-SHELL IS STILL IN ALPHA STAGES!!!!!!!  This is not a final product by any means.  This whole thread is at least 5-6 months early (i.e. once gnome-shell hits beta), and is as such, nearly irrelevant. The Gnome devs haven't had time to implement a solution to this.  

While it is good to bring up concerns, the way this thread is titled is biased against what the GNOME devs are doing.  Not really a good way to go.

I don't know if that's the case; the problem is with the basic functionality of what they're trying to do.  Does it improve UI in any meaningful way?  On the contrary, from what I can see.  

One of the things I like about GNOME is its incrimentalism.  But what they're proposing is dramatic, unnecessary change.  The very *concept* is unnecessary, regardless of whether it's alpha or not.  I think the GNOME shell is very good news for XFCE.

---

### Post by Dimitriid on 2009-05-30
I liked the preview videos of Gnomeshell. I would probably give it a chance. But at the same time I would go back to Open box + Pypannel + Compiz and might use that as my primary desktop. The reason being is that **breaking old functionality should always be the absolute last choice**. The way they are going about spells bad design to me: find a better way to introduce your technology without breaking current functionality.

I also don't buy this "Its linux it needs to evolve!" argument. There is no reason to evolve by incidentally cutting out and blocking competing software. That is something I would expect from microsoft, not from the Linux world.

So while I would try it if it turns out like this I would stop using Gnome ( and incidentally regular flavored Ubuntu ) out of general principle.

---

### Post by omar8 on 2009-05-30
Opensource software needs a new mind set, I haven't seen anything special with Linux in a long time for example (since compiz was made but the whole rotating cube is getting old), Windows 7 has Libraries, a new taskbar, nice graphics, OS X has it's dock, a unified menu, Office 07 made the switch to a Ribbon interface, etc.
The only project which seems to be attempting to do something new is KDE with KDE4 which I think is actually atleast 100x better than KDE3, once it reached KDE4.2 there was just no comparison, yet users still complain, I think this affected other projects which after seeing KDE do what they did no longer want to try and make these large changes. I think Gnome should go for it, they have the man power to make an entire unified experience and if it doesn't turn out to be great I am sure Gnome will be able to do what KDE did with KDE4 and make it better than ever.

---

### Post by wolfyking2 on 2009-05-30
> **Mehall said:**
> To paraphrase Homer Simpson,

"You don't like it, go to Crunchbang"

Or any other WM, tbh.

I only use GDM, but it could easily be replaced by SLiM if it had to be.Did he seriously say that?

---

### Post by Swarms on 2009-05-30
I welcome the changes, compiz is a piece of bloat anyway.
The developer is just angry about the foundation for his works existance is dissolving.

---

### Post by etnlIcarus on 2009-05-30
> **malachi1990 said:**
> GNOME-SHELL IS STILL IN ALPHA STAGES!!!!!!!  This is not a final product by any means.  This whole thread is at least 5-6 months early (i.e. once gnome-shell hits beta), and is as such, nearly irrelevant. The Gnome devs haven't had time to implement a solution to this.  

While it is good to bring up concerns, the way this thread is titled is biased against what the GNOME devs are doing.  Not really a good way to go.Either you didn't read the OP or you didn't understand it. Either way, your comments here are irrelevant.

> **wolfyking2 said:**
> Did he seriously say that?

[Paraphrasing is not the same as quoting](http://www.thefreedictionary.com/paraphrase).

> **Swarms said:**
> I welcome the changes, compiz is a piece of bloat anyway.I hope you enjoy your 'mutter', then. Lord knows if you don't enjoy it, you'll likely have to find a whole new DE, rather than just a new WM.

---

### Post by Swarms on 2009-05-30
> **etnlIcarus said:**
> 
I hope you enjoy your 'mutter', then. Lord knows if you don't enjoy it, you'll likely have to find a whole new DE, rather than just a new WM.

I sure will, it will enable tighter desktop visuals which is already avaible in OSs like OSX and Win7.

---

### Post by Islington on 2009-05-30
> **Swarms said:**
> I sure will, it will enable tighter desktop visuals which is already avaible in OSs like OSX and Win7.

in theory. what worries me is that as much as I love gnome, it tends to strip features because "PEOPLE DUN USE COMPLEX STUFF DURRR.." essentially we will end up with 3 plugins (cub+wall+wobbly) and the complex configuration parts of those plugins will be striped out. The wall plugin for example offers tons of options on how/what to bind when edge flipping/moving with window/within a wall.

---

### Post by Swarms on 2009-05-30
Only techs like us, don't believe doing all that configuring is a waste. 
Gnome have always been trying to appeal for a wider audience.

---

### Post by Islington on 2009-05-30
> **Swarms said:**
> Only techs like us don't believe doing all that configuring is a waste. 
Gnome have always been trying to appeal for a wider audience.

at the cost of its current audience?

---

### Post by Paqman on 2009-05-30
> **Islington said:**
> at the cost of its current audience?

You're talking about software that's still in development. It's a bit premature to declare an exodus.

---

### Post by 3rdalbum on 2009-05-30
I've been using a Gnome Shell snapshot from a couple of weeks back, and it worries me.

Oh sure, it's kinda slick; but doesn't anyone miss the functionality?

For instance, being able to get to a program with a minimum of clicks? Being able to access a control panel the same way as you can access a program, but always gnowing the separation between user (Preferences) and system-wide (Administration) prefs? Doesn't anyone miss having applets on the top panel? Doesn't anyone miss the 40 pixels taken up by the Recent List on the left side of the screen?

How about pieces of signature Gnome UI such as the Places menu?

There are a couple of things about Gnome Shell that I like, but it seems like a big interruption for a small visual benefit. I believe it would have been better to switch the current Gnome interface to Clutter and add Compiz-y desktop effects to Metacity, plus the spiffy desktop organiser from Gnome Shell. Or even keep the current desktop completely and focus on improving integration and consistency (like allowing Rhythmbox to access SMB shares that have been mounted in gvfs?)

Admittedly, the pace of development seems very quick and I haven't used one of the latest snapshots, but I'm concerned for the future of Gnome. Not that it especially bothers me so greatly as I'm equally at home in KDE 4.

---

### Post by Swarms on 2009-05-30
> **Islington said:**
> at the cost of its current audience?

Isn't the philosophy "linux for humanbeings"?, its current audience is a very small segment of the human race.

We are getting a bit off topic here, but I was just pointing out that Compiz is giving a lot of choises that normal people don't want, plus the software is bloated, so change to the current situation should be welcomed by **everyone** who wants Ubuntu to be accepted by the general population.

---

### Post by Dimitriid on 2009-05-30
How can you talk about welcoming "everyone" when Gnome would be doing the exact opposite? There is just no reason to remove old functionality, just add the new shell thing by default and let other people use compiz if they still want to. 

Quite the contrary this is exactly what the Linux community does NOT need: predatory tactics to basically block functionality of others to promote your own product.

---

### Post by etnlIcarus on 2009-05-30
> **Swarms said:**
> I sure will, **it will enable tighter desktop visuals** which is already avaible in OSs like OSX and Win7.

Says it all, really. Your argument really isn't worth entertaining.

---

### Post by Swarms on 2009-05-30
> **Dimitriid said:**
> How can you talk about welcoming "everyone" when Gnome would be doing the exact opposite? There is just no reason to remove old functionality, just add the new shell thing by default and let other people use compiz if they still want to. 

Quite the contrary this is exactly what the Linux community does NOT need: predatory tactics to basically block functionality of others to promote your own product.

This is just the way Gnome is heading, you are as said before, perfectly able to choose something else.

> **etnlIcarus said:**
> Says it all, really. Your argument really isn't worth entertaining.

Good try avoiding...

---

### Post by etnlIcarus on 2009-05-30
> **Swarms said:**
> Good try avoiding...
Who's avoiding? Your argument was, "tighter visuals", trumps functionality. Even if we were to grant you your false dilemma, purely for the sake of argument, only a completely irrational individual (or potential Gnome developer) would come to the conclusion that it's acceptable to take away or deny the user functionality, for the sake of *'isn't it prettyful!'*

You argued yourself into the most idiotic of corners. Worse yet was your stubborn refusal to acknowledge or identify your own fallacy, which begged this explanation for the benefit of you and you, alone.

You argued something really, really stupid. You then followed up by childishly trying to spin my reluctance to dignify your idiocy into a concession of defeat. I'm quite certain the only person you're convincing here is yourself ...but then I suspect that's all that matters, anyway.

---

### Post by Mr. Picklesworth on 2009-05-30
> **Dimitriid said:**
> How can you talk about welcoming "everyone" when Gnome would be doing the exact opposite? There is just no reason to remove old functionality, just add the new shell thing by default and let other people use compiz if they still want to. 

Quite the contrary this is exactly what the Linux community does NOT need: predatory tactics to basically block functionality of others to promote your own product.

You're thinking this way out of proportion. It isn't predatory tactics; it is just a natural, interesting (and common) choice to directly connect the window manager and the rest of the shell. To explain this all really quickly, since I think I've already explained it multiple times: Nobody has a problem that GDM feels nicer than XDM or KDM when they are logging in to a GNOME session. Nobody has a problem, or should have a problem, that they can't 'put Compiz in their Fluxbox.'

Also, GNOME is a platform. There are different products making use of its technologies for different interfaces right now. Two strong examples are Moblin and Maemo. Nothing is changing; just a new desktop, like Moblin is or HP's MIE, but this one happens to be the default focus for the GNOME project.


Further, maintaining the rather hopeless case that is GNOME Panel and an old branch of Metacity *alongside* new stuff is not an option. If you want, maintain it yourself (GNOME is still quite modular) or hope that there is a distro out there insane enough to do so. I bet it'll last three months before they realize it is not as perfect as they thought.

---

### Post by arsenic23 on 2009-05-30
I'm all for replacing Compiz with something more efficiant and streamlined, but I just don't know if GnomeShell is it.  I just don't think the direction it *appears* to be going in is going to create an environment that I want to use.

---

### Post by Swarms on 2009-05-30
> **etnlIcarus said:**
> Who's avoiding? Your argument was, "tighter visuals", trumps functionality. Even if we were to grant you your false dilemma, purely for the sake of argument, only a completely irrational individual (or potential Gnome developer) would come to the conclusion that it's acceptable to take away or deny the user functionality, for the sake of *'isn't it prettyful!'*

You argued yourself into the most idiotic of corners. Worse yet was your stubborn refusal to acknowledge or identify your own fallacy, which begged this explanation for the benefit of you and you, alone.

You argued something really, really stupid. You then followed up by childishly trying to spin my reluctance to dignify your idiocy into a concession of defeat. I'm quite certain the only person you're convincing here is yourself ...but then I suspect that's all that matters, anyway.

Hey ho Silver, good job overanalyzing there. You take one remark (maybe tight was a bad choice of word), and create an entire opinion that is not even true...
I never meant that visuals should trump functionality, we already have Compiz for that. I mean that desktop effects for the gnome desktop could be so much better than Compiz already are.

You are quite vicous, but maybe you just had a bad day at work and just had to let some steam out...

---

### Post by Dimitriid on 2009-05-30
> **Mr. Picklesworth said:**
> You're thinking this way out of proportion. It isn't predatory tactics; it is just a natural, interesting (and common) choice to directly connect the window manager and the rest of the shell. To explain this all really quickly, since I think I've already explained it multiple times: Nobody has a problem that GDM feels nicer than XDM or KDM when they are logging in to a GNOME session. Nobody has a problem, or should have a problem, that they can't 'put Compiz in their Fluxbox.'

Also, GNOME is a platform. There are different products making use of its technologies for different interfaces right now. Two strong examples are Moblin and Maemo. Nothing is changing; just a new desktop, like Moblin is or HP's MIE, but this one happens to be the default focus for the GNOME project.


Further, maintaining the rather hopeless case that is GNOME Panel and an old branch of Metacity *alongside* new stuff is not an option. If you want, maintain it yourself (GNOME is still quite modular) or hope that there is a distro out there insane enough to do so. I bet it'll last three months before they realize it is not as perfect as they thought.

I don't know why you say its "a hopeless case" when it has served people for so long the way it is right now. You seem to be happy to cheer new for the sake of new only and imply that right now the window decorator as a separate option is completely and utterly broken when it works perfectly fine.

I happen to want software that is modular, in fact a lot of people go to great efforts to introduce that as a feature ( see arch and KDEmod ).

---

### Post by don_quixote on 2009-05-30
> **omar8 said:**
> Opensource software needs a new mind set, I haven't seen anything special with Linux in a long time for example (since compiz was made but the whole rotating cube is getting old), Windows 7 has Libraries, a new taskbar, nice graphics, OS X has it's dock, a unified menu, Office 07 made the switch to a Ribbon interface, etc.
The only project which seems to be attempting to do something new is KDE with KDE4 which I think is actually atleast 100x better than KDE3, once it reached KDE4.2 there was just no comparison, yet users still complain, I think this affected other projects which after seeing KDE do what they did no longer want to try and make these large changes. I think Gnome should go for it, they have the man power to make an entire unified experience and if it doesn't turn out to be great I am sure Gnome will be able to do what KDE did with KDE4 and make it better than ever.

Do you know how old most of the OS X UI is now?  It's seen incrimental changes, but no release has done anything as drastic as what GNOME is proposing.  

And Compiz isn't about the 'cube that's getting old' it's about added functionality, which it delivers in spades.  I don't have any of its flashy desktop effects, but the modifiable interface provides additional functionality at a fast speed, and -- here's the important part -- *improves my productivity greatly.*  Surely, the path to a wider adoption of Linux is through tools that make you work more efficiently, not through an interface that appears broken on arrival.


> **Swarms said:**
> I welcome the changes, compiz is a piece of bloat anyway.
The developer is just angry about the foundation for his works existance is dissolving.

Oh, yes, I'm sure the shell will be the most efficient piece of software ever unleashed.  In any case, the developer's work will live on as people start migrating to XFCE.

---

### Post by Islington on 2009-05-30
> **Dimitriid said:**
> I don't know why you say its "a hopeless case" when it has served people for so long the way it is right now. You seem to be happy to cheer new for the sake of new only and imply that right now the window decorator as a separate option is completely and utterly broken when it works perfectly fine.

I happen to want software that is modular, in fact a lot of people go to great efforts to introduce that as a feature ( see arch and KDEmod ).

I don't think you completely grasp the background problem of this. The current option of using gnome panel and metacity is working because of a lot of ugly hacks. These hacks work, but basing and growing anything on them is not safe, as such the innovation is slowing down. Gnome Shell is clever because it will be well designed from the beginning. THere may even be something to make the compiz plugins work in shell at some point in the future. The point I am trying to make is that there will be a world of hurt for people like myself with lower end systems, if the composition doesn't work, or more likely is slow as molasses in january. Take for example kde4, I like it.

Kwin is however is still a bit of a frozen turd.Its getting better, but still lags,glitches, lacks options. Until it matures I can use compiz with kde4. *There will be no such fallback in Gnome Shell.*

---

### Post by Dimitriid on 2009-05-30
> **Islington said:**
> I don't think you completely grasp the background problem of this. The current option of using gnome panel and metacity is working because of a lot of ugly hacks. These hacks work, but basing and growing anything on them is not safe, as such the innovation is slowing down. Gnome Shell is clever because it will be well designed from the beginning. THere may even be something to make the compiz plugins work in shell at some point in the future. The point I am trying to make is that there will be a world of hurt for people like myself with lower end systems, if the composition doesn't work, or more likely is slow as molasses in january. Take for example kde4, I like it.

That sounds ok to me. Thanks for explaining properly. Also you admit that you have a very low end system which is nice instead of going for "compiz sucks, its bloated" cause to me, when it works perfectly fine with 4 year old computers then you really need to know that its your problem you have a 6 or 7 year old system and stop blaming new technologies you shouldn't be trying to begin with.

---

### Post by etnlIcarus on 2009-05-30
> **Swarms said:**
> I never meant that visuals should trump functionalityThen perhaps your should choose your responses more carefully.

> **don_quixote said:**
> And Compiz isn't about the 'cube that's getting old' it's about added functionality, which it delivers in spades.  I don't have any of its flashy desktop effects, but the modifiable interface provides additional functionality at a fast speed, and -- here's the important part -- *improves my productivity greatly.*  Surely, the path to a wider adoption of Linux is through tools that make you work more efficiently, not through an interface that appears broken on arrival.
+1

---

### Post by Swarms on 2009-05-31
> **etnlIcarus said:**
> Then perhaps your should choose your responses more carefully.


+1
Just like you shouldn't make up contradictions from a simple word.

We both learned something new then.

---

### Post by etnlIcarus on 2009-05-31
A word cannot constitute a contradiction. You need at least two words to achieve that.

And yeah, blaming others for your inability to communicate is sure to get you far.

---

### Post by Swarms on 2009-05-31
> **etnlIcarus said:**
> A word cannot constitute a contradiction. You need at least two words to achieve that.

And yeah, blaming others for your inability to communicate is sure to get you far.

Meh, you are really something special.

---

### Post by etnlIcarus on 2009-05-31
I ...can't think of a response to that. Congratulations: you've out-smugged me.

---

### Post by [h2o] on 2009-05-31
I think it is time for everyone to just calm down.
Personally I don't use compiz anymore since it just won't play nice with some apps (although I am quite sure the ATI drivers are at fault here), but my impression is that yes, it has some features that improves productivity. Compiz was a really important to get everyone working on a more good looking desktop and using 3d-effects, but I think it has played out its role. I think desktop effects should be tied to the DE to get a more consistent visual experience.

Gnome-Shell in its current state is also really promising. If you try it be warned that there are plenty of rough edges, but then remember (as usual) that it is not a final product.

I for one will welcome change :)

---

### Post by don_quixote on 2009-05-31
> **'[h2o] said:**
> Gnome-Shell in its current state is also really promising. If you try it be warned that there are plenty of rough edges, but then remember (as usual) that it is not a final product.

From a productivity standpoint, what exactly is promising about it in its current state?  

For compiz, it's obvious: grouping of windows, multiple minimization options, selective maximization, a very efficient wall/expose (not some weird combination), hot corners, all fully configurable to personalized key bindings.  Currently, this combination also integrates well with GNOME panel as a multi-purpose 'dock' something that's going bye-bye with the shell where the developers are forcing the application launcher aspect through the currently *extremely intrusive* side bar.  What, exactly, is broken in the original implementation of the panel that required these rather drastic changes??? 

GNOME shell requires a DRASTIC rethink in order to be useful, but seeing as how GNOME developers seem to be massively resistant to changing their pet ideas and would rather publicly insult compiz developers, I am holding out little hope.

---

### Post by benj1 on 2009-05-31
i think modularity has served us well. 
Saying that compiz has served its purpose is missing the point that improvements in other window managers only came about because of(or at least were accelerated by) compiz.

---

### Post by [h2o] on 2009-06-01
> **don_quixote said:**
> From a productivity standpoint, what exactly is promising about it in its current state?
I like the new "Activity" concept. Also, I think using the entire screen as overlay when about to launch applications is neat. I mean, I have a large screen, so when I want to launch a program, why should all applications be listed in a small rectangle that takes up at most 5-10% of my screen space?

> GNOME shell requires a DRASTIC rethink in order to be useful, but seeing as how GNOME developers seem to be massively resistant to changing their pet ideas and would rather publicly insult compiz developers, I am holding out little hope.
I think a drastic rethink is perfectly in order. When the change comes, if you are not happy with how the shell works then that's a shame, but then there are other DEs to choose from.

---

### Post by [h2o] on 2009-06-01
> **benj1 said:**
> i think modularity has served us well.
While I do like the concept of modularity in general, it has the drawback that stuff easily gets inconsistent.

> Saying that compiz has served its purpose is missing the point that improvements in other window managers only came about because of(or at least were accelerated by) compiz.
Which was kind of my point. Compiz was what started it all, but now I think it is better if all the bling could be handled by the DE itself instead of gluing something on top of it.

I just want to make it perfectly clear that I don't have anything against Compiz. I've been a user since the first releases and for the most time I have really liked it.

---

### Post by etnlIcarus on 2009-06-01
> **'[h2o] said:**
> While I do like the concept of modularity in general, it has the drawback that stuff easily gets inconsistent.
As an avid Xfce fan, I call bulls**t.

---

### Post by don_quixote on 2009-06-01
> **'[h2o] said:**
> Which was kind of my point. Compiz was what started it all, but now I think it is better if all the bling could be handled by the DE itself instead of gluing something on top of it.

Although I'm not sure I agree, the pivotal question here is - does the proposed change to the DE introduce all the beneficial aspects of Compiz?  Clearly, the answer as it currently stands, is no.  It does, however, break Compiz, so what we are left with is a shell that currently can't even scale without going into the stupid workspace overlay, something that's certainly not necessary 99% of the time.  Worst of all, the GNOME devs are perfectly frank in their admission that most of such functionality isn't going to be in there because of the ill-thought-out HIG.  As it stands, Gnome Shell will not be a drop-in replacement for Compiz (unlike KWin, which is picking up much if not all of its functionality).  Not even close.

---

### Post by pt123 on 2009-06-01
> **don_quixote said:**
>  Worst of all, the GNOME devs are perfectly frank in their admission that most of such functionality isn't going to be in there because of the ill-thought-out HIG.  As it stands, Gnome Shell will not be a drop-in replacement for Compiz (unlike KWin, which is picking up much if not all of its functionality).  Not even close.
Exactly. 

Lets not forget Gnome's history of bungled applications that are inferior to it's competitors.
Epiphany
F-Shot
Empathy
Vinagre
Gnome Screensaver
Gnumeric

Gnome should stop competing with applications and focus on technologies and tools that will improve the development of applications.

---

### Post by [h2o] on 2009-06-01
> **etnlIcarus said:**
> As an avid Xfce fan, I call bulls**t.
Never used xfce, so I can't really comment on that.

> **don_quixote said:**
> Although I'm not sure I agree, the pivotal question here is - does the proposed change to the DE introduce all the beneficial aspects of Compiz?  Clearly, the answer as it currently stands, is no.  It does, however, break Compiz, so what we are left with is a shell that currently can't even scale without going into the stupid workspace overlay, something that's certainly not necessary 99% of the time.  Worst of all, the GNOME devs are perfectly frank in their admission that most of such functionality isn't going to be in there because of the ill-thought-out HIG.  As it stands, Gnome Shell will not be a drop-in replacement for Compiz (unlike KWin, which is picking up much if not all of its functionality).  Not even close.
What I think are "the beneficial aspects of Compiz" seem to in some way end up in the Shell in some form in the end. Really, debating over what Gnome shell can and can't do is a bit moot at this point as it is still in really heavy development.

Anyway, the point I am trying to get across is that the change seem to be coming whether you like it or not, and you have two options if you don't like it: Either get engaged and make sure that the shell ends up the way you want it. Or you could always bitch about it and swith to Xfce.

---

### Post by [h2o] on 2009-06-01
> **pt123 said:**
> Exactly. 

Lets not forget Gnome's history of bungled applications that are inferior to it's competitors.
Epiphany
F-Shot
Empathy
Vinagre
Gnome Screensaver
Gnumeric

Gnome should stop competing with applications and focus on technologies and tools that will improve the development of applications.

Empathy is actually starting to get really good. I have prefered it over Pidgin since 8.10 and apart from "MSN smileys" I can't really think of any feature that I had in Pidgin that is not available in Empathy. My starting to use Empaty was however more an ideological choice as I really think Telepathy is the way to go when it comes to IM.

---

### Post by DemonBob on 2009-06-01
Is it really that bright to be arguing about a piece of software before it gets to a production ready release. A 100 or even a 1000 things can change from what you see it as now. 

I'm not saying i particularly like the idea of the new menu, but I'm not going to judge it until it gets to a more usable state.... I do believe however that starting from scratch is a good idea on the DE, since gnome-panel and metacity is pretty much hacked to get with patches.

---

### Post by etnlIcarus on 2009-06-01
> **'[h2o] said:**
> Never used xfce, so I can't really comment on that.I recommend trying it before claiming modularity leads to inconsistency. Xfce provides for a much more cohesive experience than any integrated environment I've used.

[quote=pt123]**Epiphany**
F-Shot
**Empathy**
Vinagre
Gnome Screensaver
**Gnumeric**[/quote]Highlighted applications all represent pretty quality software. Can't speak for F-Spot or Vinagre as I've never had much use for them. Gnome-Screensaver is the only one I could fairly describe as, "inferior".

---

### Post by benj1 on 2009-06-01
> **'[h2o] said:**
> 
Which was kind of my point. Compiz was what started it all, but now I think it is better if all the bling could be handled by the DE itself instead of gluing something on top of it.

I just want to make it perfectly clear that I don't have anything against Compiz. I've been a user since the first releases and for the most time I have really liked it.

my point was, that in the future, the gnome devs may think people want feature x whereas a group of programmers (i'll call them compris) may think feature y is better, at present everyone is free to choose if they want feature x or feature y, if gnome is wrong and everyone flocks to compris gnome can implement feature y, in the future this may not be possible, compris have the option of implementing an entire DE just for feature y, or we have to shout at the gnome devs to get them to implement feature y.

i take your point about integration, but compared to windows, gnome and linux in general have a much more integrated feel.

---

### Post by t0p on 2009-06-01
Gahh, forget the bling.  See-through windows and twirling cubes - who needs 'em?  In fact, who needs a gui?  Let's regress to the cli and have to learn bash to do anything.  Luddism is a very attractive proposition...

---

### Post by Islington on 2009-06-01
> **t0p said:**
> Gahh, forget the bling.  See-through windows and twirling cubes - who needs 'em?  In fact, who needs a gui?  Let's regress to the cli and have to learn bash to do anything.  Luddism is a very attractive proposition...

[img]http://ubuntuforums.org/images/smilies/eusa_clap.gif[/img]

---

### Post by sertse on 2009-06-01
Yeah, it kinda pointless to comment about modularity, if one has never tried XFCE, which is the largest/most popular project showcasing it...

Also, HIG is not inherently "ill thought out". It is just a particular POV on how software should be presented. Sane defaults, easy to understand interfaces and not overwhelming users with options that only "power users" appreciate is a perfectly valid view. Sure not for everyone, especially the "power users" but it doesn't make it less legitimate, just a different opinion. The audacity of some people who believe their worldview is the only one to take..  

Agreeing that epiphany, gnumeric and empathy are somewhat successful projects, or at least one where clear potential can be seen in. 

To the above the above comment; My sig actually links to a project excatly focusing on how user friendly the CLI can acutally be. Try it sometime :P

---

### Post by pt123 on 2009-06-01
let's not forget about how much Compiz pushed the Video card companies like Nvidia (esp. them), ATI/AMD and Intel to update their drivers and support new abilities. 

While Gnome has been always archaic. They still can't support the lines scrolled in a mouse wheel. 

You don't one foundation/company to control or steal marketshare from these innovative projects/companies by using an unfair advantage, this reaks of atrocities commited by Microsoft in the past.

---

### Post by etnlIcarus on 2009-06-01
Okay, lets steer this away from, "the Gnome devs kick babies and microwave kittens!", territory. The issue is, quite simply, that *in this instance*, the Gnome devs decided not to play nice with the rest of the FOSS community and it's Gnome's users who are ultimately going to pay the price.

---

### Post by pt123 on 2009-06-01
> **etnlIcarus said:**
> Okay, lets steer this away from, "the Gnome devs kick babies and microwave kittens!", territory. 
I am calling it how I see it, when Microsoft do anything similar the FOSS world are always up in arms.

---

### Post by etnlIcarus on 2009-06-01
> **pt123 said:**
> I am calling it how I see it.

By bringing up how Gnome application X, Y and Z are, "inferior".

> when Microsoft do anything similar the FOSS world are always up in armsFirstly, this is hardly comparable to a lot of the **** MS have pulled. Secondly, other people's bad behaviour does not excuse your own. Didn't your mother teach you that lesson?

---

### Post by [h2o] on 2009-06-01
> **pt123 said:**
> I am calling it how I see it, when Microsoft do anything similar the FOSS world are always up in arms.
It's not like there is a mission to destroy Compiz on Gnome. They came up with a really neat idea that happens to be incompatible with Compiz. I fail to see the evil in that. :confused:

---

### Post by pt123 on 2009-06-01
> **etnlIcarus said:**
> By bringing up how Gnome application X, Y and Z are, "inferior".
Because they are inferior to the main competitors in the field, i.e. Firefox, Pidgin, Picasa, OOO's Calc, xvncviewer. 
> 
Firstly, this is hardly comparable to a lot of the **** MS have pulled. 
It is one aspect of it, MS used their control of the OS to take over the market in other applications. 
Gnome is doing something very similar by using their control of the DE to takeover Compiz's market. 

> **'[h2o] said:**
> They came up with a really neat idea that happens to be incompatible with Compiz. I fail to see the evil in that. :confused:
lol a neat idea, which is a rip of compiz and what is worse is that compiz will no longer work on Gnome. 

It is like Google coming and introducing a new browser and then saying their search engine will no longer work with Firefox. Then telling Firefox to go and develop their own search engine. Then attempting to justify it by saying these days search is integral to the browsing.

---

### Post by [h2o] on 2009-06-01
> **pt123 said:**
> lol a neat idea, which is a rip of compiz and what is worse is that compiz will no longer work on Gnome.
Sure, it's a rip of Compiz in the sense that both use compositing. I fail to see how they are similar in any other way.
If the functionality that Compiz offers is made available in Gnome-shell, then I really don't understand why anyone would care whether Compiz works with it or not.

> It is like Google coming and introducing a new browser and then saying their search engine will no longer work with Firefox. Then telling Firefox to go and develop their own search engine. Then attempting to justify it by saying these days search is integral to the browsing.
No. That is not the same thing.

---

### Post by etnlIcarus on 2009-06-01
[quote=me]Okay, lets steer this away from, "the Gnome devs kick babies and microwave kittens!", territory. The issue is, quite simply, that in this instance, the Gnome devs...[/quote][quote=you]I am calling it how I see it, when Microsoft do anything similar the FOSS world are always up in arms.[/quote][quote=me]By bringing up how Gnome application X, Y and Z are, "inferior".[/quote][quote=you]Because they are inferior to the main competitors in the field, i.e. Firefox, Pidgin, Picasa, OOO's Calc, xvncviewer.[/quote]

I'll leave you to mull over how nonsensical this line of reasoning has become.

> It is one aspect of it, MS used their control of the OS to take over the market in other applications.
Gnome is doing something very similar by using their control of the DE to takeover Compiz's market. I honestly can't imagine why the Gnome devs would care enough about compiz to deliberately lock it out. You're delving into conspiracy theory territory, here.

Also worth mentioning is Gnome *only just barely* leads the linux DE space and this is primarily due to Gnome's cooperation with the leading distros. The Gnome devs aren't going to *deliberately* screw themselves over - *thoughtlessly* screwing themselves over is another matter entirely and an order of magnitude more likely, as well.

---

### Post by Mr. Picklesworth on 2009-06-01
> **'[h2o] said:**
> It's not like there is a mission to destroy Compiz on Gnome. They came up with a really neat idea that happens to be incompatible with Compiz. I fail to see the evil in that. :confused:

Thank you, good sir, for entering this thread with common sense in gear. (Where is that thumbs up button?...)

-

If you don't like GNOME Shell, this is perfect. You can install Compiz, set it as your window manager and run that. Maybe add gnome-do to your startup options. You lose the GNOME Shell overlay thing and you get your precious window manager. Compiz is only incompatible with GNOME Shell as far as it is presently incapable of doing all the stuff it does.

As for consistency, yes it does matter. Notice how in Compiz every plugin pulls random colours and fonts to use out of a hat and you just have to hope it doesn't completely clash with everything else. Regardless, it always does (even with the defaults between different Compiz plugins). This is more than consistency. This changes how people approach the software, and it destroys the capability of colours and fonts to subtly provide the user with hints.

In Gnome Shell, you can expect those sorts of colours (and fonts!) to be completely consistent.

---

### Post by don_quixote on 2009-06-01
> **Mr. Picklesworth said:**
> If you don't like GNOME Shell, this is perfect. You can install Compiz, set it as your window manager and run that. Maybe add gnome-do to your startup options. You lose the GNOME Shell overlay thing and you get your precious window manager. Compiz is only incompatible with GNOME Shell as far as it is presently incapable of doing all the stuff it does.

GNOME Shell is the new panel - so the fact that Compiz breaks the panel is, in fact, the whole problem.  System tray, application launching, GNOME-panel specific apps are all gone under the new implementation and are a part of the shell.  Which means you can't just put Compiz in and everything is the same as usual.  At that point, it's hardly even GNOME.  If all Compiz broke was the overlay, I could care less - it's clunky and dead on arrival.    


> **Mr. Picklesworth said:**
> As for consistency, yes it does matter. Notice how in Compiz every plugin pulls random colours and fonts to use out of a hat and you just have to hope it doesn't completely clash with everything else. Regardless, it always does (even with the defaults between different Compiz plugins). This is more than consistency. This changes how people approach the software, and it destroys the capability of colours and fonts to subtly provide the user with hints.

I'm really not sure what you mean here.  Can you specify?  I don't seem to have random 'fonts' or 'colours' with compiz.

---

### Post by days_of_ruin on 2009-06-01
I don't see why one couldn't easily revert to the old gnome-panel.
Hopefully the gnome devs will still support the current setup and make 
it really easy to change between them.

---

### Post by pt123 on 2009-06-01
> **'[h2o] said:**
> If the functionality that Compiz offers is made available in Gnome-shell, then I really don't understand why anyone would care whether Compiz works with it or not.
That is the problem with it would be bungled attempt like Gnome's other applications. It wouldn't provide all the useful compiz utilities it will be limited by the outdated HiG. It would be slow like Gnome's metacity compositing. 
They are giving the user an inferior product and what is worse they are preventing the user from running a superior product. 

> **etnlIcarus said:**
> I'll leave you to mull over how nonsensical this line of reasoning has become.
If you are afraid to discuss the merits of other applications to their counter parts you are only deluding yourself to think this application will be different.
> 
I honestly can't imagine why the Gnome devs would care enough about compiz to deliberately lock it out. You're delving into conspiracy theory territory, here.
I wouldn't say the devs but the heads they are interface control freaks. Compiz is extremely popular and it is how most gnome users interact with interface.  

For all you Gnome Boys out there who feel how Gnome applications are of good quality. Trying open Epiphany and changing the value for "Number of lines scrolled" by the mouse wheel, (hint: you have to use about:config).

---

### Post by OutOfReach on 2009-06-01
In my opinion, I don't like where GNOME 3.0 is going....

---

### Post by dicairo on 2009-06-01
what i can say??? i watched a video on youtube and its really sucks and i hope that gnome team see all these opinions ; i cant imagine ubuntu without compiz or with this new cofiguration its really very bad :( at the end i think microsoft will thank gnome team for thiss :)

---

### Post by sertse on 2009-06-01
Compiz was never part of GNOME. Therefore GNOME never had an obligation to Compiz. Compiz is "just" an independently made addon that worked really well with GNOME. 

As there was never any obligation in the first place, GNOME has not done anything technically or morally wrong. It was always been Y (Compiz)'s responsibility, as a unofficial 3rd-party addon to work with X.  

Frankly the entitlement mentality, people have that X software must work with Y even though X had Y in mind in their own plans is sickening. 

Also lol "I don't like (Gnome-app) so it must be universally and undisputedly true, and everyone who disagrees is wrong". People like certain apps for many reasons, it is not your right to tell them that liking them is wrong. 

I already justified HIG in my earlier post. It just a particular POV, not one everyone follows, but unlike your world, multiple POV can exist and not the case where one is "right" and the other is "wrong"

---

### Post by don_quixote on 2009-06-01
> **sertse said:**
> Compiz was never part of GNOME. Therefore GNOME never had an obligation to Compiz. Compiz is "just" an independently made addon that worked really well with GNOME. 

And that's why a lot of distributions (including Ubuntu) bundled together Compiz with GNOME, because it was and is a gazillion times better than pure GNOME ever was.  So, this 'just' addon is largely responsible for GNOME's popularity and usability over its competitors.


> **sertse said:**
> As there was never any obligation in the first place, GNOME has not done anything technically or morally wrong. It was always been Y (Compiz)'s responsibility, as a unofficial 3rd-party addon to work with X.  

GNOME is making it impossible for Compiz to work with the shell; Compiz developers have suggested various, relatively simple ways, in which Compiz could plug into the shell.  GNOME devs have stubbornly refused to consider this, and have partaken in basically belittling and name calling of Compiz developers.  If you think that's a professional way to act, OK.  I think it doesn't speak very highly of them, especially given the fact that the popularity of the GNOME desktop would be far lower without Compiz.   


> **sertse said:**
> Frankly the entitlement mentality, people have that X software must work with Y even though X had Y in mind in their own plans is sickening. 

So if it were possible for GNOME to break all the currently written GTK applications, well that would be anyone's fault but GNOME's?  What I find sickening is the mentality that DEVELOPER is BEYOND CRITICISM.  It's not like one or two people are expressing concern over the direction the GNOME shell is heading in.  

Once again - is the shell replicating the functionality that has the potential to dramatically increase productivity?  N.o.  The shell looks to almost be inherently designed to slow things down.  OK, maybe it makes sense on netbooks, but as a shell for laptops and desktops it is inherently a flawed design.  Maybe GNOME devs should think about these concerns instead of shrugging them off as if they are irrelevant.

---

### Post by Mr. Picklesworth on 2009-06-01
> **don_quixote said:**
> Maybe GNOME devs should think about these concerns instead of shrugging them off as if they are irrelevant.

**Hm, maybe that's why it's in early mockup stages right now...

---

### Post by Islington on 2009-06-01
> **Mr. Picklesworth said:**
> **Hm, maybe that's why it's in early mockup stages right now...

you arguments dont seem as inflamed as others, so I ask this of you. Do you really feel it is okay for gnome to make a big change without some sort of graceful fallback? Compiz will be eventually replicated (the useful bits, early on, the flashy bits later.) it might not be as configurable but eventually it will be integrated. What is your argument as to compiz being blocked from even being a fallback (not even KDE has done this.)


I have accepted the argument that compiz was a temporary thing, but to block it from working as the backup, because the devs have come up with some new clever idea, seems to me extremely wanton.

edit: by block I mean that running it will actually cause a *loss* of functionality.

---

### Post by Pogeymanz on 2009-06-01
That's why I think Compiz just needs to become its own DE. Compiz-deskmenu needs to be officially supported, make their own panel and middle-click menu, then just steal PCManFM/Thunar and a terminal and you have yourself a DE.

End of problem. I've always disliked Gnome anyway.

---

### Post by Mr. Picklesworth on 2009-06-01
> **Islington said:**
> you arguments dont seem as inflamed as others, so I ask this of you. Do you really feel it is okay for gnome to make a big change without some sort of graceful fallback? Compiz will be eventually replicated (the useful bits, early on, the flashy bits later.) it might not be as configurable but eventually it will be integrated. What is your argument as to compiz being blocked from even being a fallback (not even KDE has done this.)


I have accepted the argument that compiz was a temporary thing, but to block it from working as the backup, because the devs have come up with some new clever idea, seems to me extremely wanton.

edit: by block I mean that running it will actually cause a *loss* of functionality.

In fact, I do think it is okay. The old version is right there to be happily used since it does, as others have mentioned, *work* fine and other stuff can probably be backported around it as people desire. That's up to distributions, and I am sure we can trust someone to take up the task for a while. The possibility of a lightweight GNOME Shell alternative has been discussed on its mailing list, and the decision seems to be (though this could change) that it would be a waste of effort. XFCE achieves this sort of thing fine, is lighter than GNOME and manages a similar feel with the same general set of technologies. It would be better in the long run to point older computers towards XFCE and possibly implement some of peoples' favourite GNOME panel applets for the XFCE panel.

Similar deal here, really. Waste of effort to maintain new alternatives within GNOME when alternatives that people like already exist and old stuff can be happily retrieved at any given time since it is free software.

It is definitely well known (though so far unmentioned, again because the project is early in its life) that a transition plan needs to be in place. Parallel installation of Metacity / GNOME Shell is being worked on (--finished?--) so I would not be surprised to see the current way be maintained for a while in a form that distros like Ubuntu can ship :)


And again, Compiz isn't being blocked at all; this is the same as the situation where if I turn on Compiz I lose that cool minimized window thumbnail feature of Metacity. It just happens that the feature in Metacity is considerably larger and (possibly) more desirable.

Or, considering how GNOME Shell will be quite extensible (it uses Javascript, remember), perhaps a better analogy of the flaw in this "GNOME blocking Compiz" claim would be the situation right now where Firefox doesn't use GTK and thus doesn't fit perfectly into GNOME and... uhh... that's it.
(For what it's worth, I've recently moved back to Firefox from Epiphany because I discovered the stupendously awesome Feedly extension).

---

### Post by etnlIcarus on 2009-06-01
> **Mr Picklesworth]You can install Compiz, set it as your window manager and run that. Maybe add gnome-do to your startup options. You lose the GNOME Shell overlay thing and you get your precious window manager. Compiz is only incompatible with GNOME Shell as far as it is presently incapable of doing all the stuff it does.

As for consistency, yes it does matter. Notice how in Compiz every plugin pulls random colours and fonts to use out of a hat and you just have to hope it doesn't completely clash with everything else. Regardless, it always does (even with the defaults between different Compiz plugins). This is more than consistency. This changes how people approach the software, and it destroys the capability of colours and fonts to subtly provide the user with hints.

In Gnome Shell, you can expect those sorts of colours (and fonts!) to be completely consistent.

...

**Hm, maybe that's why it's in early mockup stages right now...[/quote]Possibly the most ignorant comments in the thread. This doesn't even bear refutation said:**
> If you are afraid to discuss the merits of other applications to their counter parts you are only deluding yourself to think this application will be different.Apparently you're still not getting this: broader criticisms of Gnome do nothing to further this discussion. All I requested was we keep this focussed on the issue at hand. Your comments are borderline ad hominem.

---

### Post by MikeTheC on 2009-06-02
From what I understand, the Compiz people got the Gnome and KDE folk to re-write their stuff once already. I gather the Compiz folks need to get their stuff in order and then very nicely and politely and diplomatically (hey, who am I kidding) go back to Gnome and KDE and work with them on a gradual conversion over so that some future version of each will eventually be able to implement it.

However, far as I'm concerned, even though I really love what Compiz does for me as an end user, those people need to have the courtesy to make doublely, triply, and maybe even quadruply d*mn sure that this is it, and the end, and that the Gnome and KDE folk aren't going to have to uproot all their code on a regular basis.

It's too late now for them to have "gotten it right the first time" so I would say they have a desperate need to "get it right THIS time".

I'm a nice guy, very kind and generous and understanding and diplomatic IRL, but there comes a point where... well, let's just say the Compiz folk are real darn lucky Havoc heads up Gnome and not me, otherwise they might figuratively be staring down the end of a pair of barrels with me telling 'em "So, have you ever been... to a Turkish prison, son?"

---

### Post by [h2o] on 2009-06-02
> **pt123 said:**
> That is the problem with it would be bungled attempt like Gnome's other applications. It wouldn't provide all the useful compiz utilities it will be limited by the outdated HiG. It would be slow like Gnome's metacity compositing. 
They are giving the user an inferior product and what is worse they are preventing the user from running a superior product.
Since Gnome Shell is not complete, how can you make claims for its final feature set or speed? I am quite sure that speed will be looked at, since devs are people like you and me and won't accept sluggishness. As for superior vs. inferior, that is your opinion.

> I wouldn't say the devs but the heads they are interface control freaks. Compiz is extremely popular and it is how most gnome users interact with interface.
Compiz is popular, yes, because it is currently the only widespread compositing window manager for Gnome. Gnome shell is not yet popular because....well it's not finisshed yet :)

> For all you Gnome Boys out there who feel how Gnome applications are of good quality. Trying open Epiphany and changing the value for "Number of lines scrolled" by the mouse wheel, (hint: you have to use about:config).
I agree with you that Epiphany is in many ways inferior to Firefox. But I can't really see how your example is relevant since I can't find any way to do that from the Firefox "preferences" dialog either. What's your point?

---

### Post by dspari1 on 2009-06-02
I think the Gnome team is doing a mistake because by blocking Compiz, Gnome users won't have good compositing effects for a long time.

I'm using Compiz with KDE 4.2.3 (it's the default for Sabayon). I admit that it's not perfect, but it's way better than KDM's compositing, and it should hold me off until KDM's effects matures enough to no longer need Compiz.

---

### Post by [h2o] on 2009-06-02
> **dspari1 said:**
> I think the Gnome team is doing a mistake because by blocking Compiz, Gnome users won't have good compositing effects for a long time. Gnome users will not have "a long time" without compositing effects, since the "replacement" for Compiz, Gnome Shell, is indeed composited. What "good" effects are is of course subjective, but there should be no technical reason that Gnome Shell couldn't look as good as Compiz.

---

### Post by visionaire on 2009-06-02
Hi, i tried to build gnome-shell in Hardy nad have this error

Please run 'sudo apt-get install xulrunner-dev libffi-dev ' and try again.

i did aptitude search and found xulrunner-1.9-dev, install that, but still the same message

It's not possible to intall gnome-shell on hardy?

Thanks =)

---

### Post by Ptero-4 on 2009-06-02
Just tested gnome-shell. One word "CRAPPY". It can't use the old applets I like and you can't customize it's "panel" (even the kde4 one can be customized and holds "applets").

> **'[h2o] said:**
> I like the new "Activity" concept. Also, I think using the entire screen as overlay when about to launch applications is neat. I mean, I have a large screen, so when I want to launch a program, why should all applications be listed in a small rectangle that takes up at most 5-10% of my screen space?


I think a drastic rethink is perfectly in order. When the change comes, if you are not happy with how the shell works then that's a shame, but then there are other DEs to choose from.

Yeah, like which, windoze-clone KDE4, windoze-like lxde, or perhaps the crappy xfce which lacks decent filemanager based CD/DVD burner and archive manager, and lacks a compiz decorator, and an unified appearance manager panel, and I forgot, it's panel can't remember it's settings properly and "loses" or "moves" the applets around for no reason at all.

> **'[h2o] said:**
> Never used xfce, so I can't really comment on that.


What I think are "the beneficial aspects of Compiz" seem to in some way end up in the Shell in some form in the end. Really, debating over what Gnome shell can and can't do is a bit moot at this point as it is still in really heavy development.

Anyway, the point I am trying to get across is that the change seem to be coming whether you like it or not, and you have two options if you don't like it: Either get engaged and make sure that the shell ends up the way you want it. Or you could always bitch about it and swith to Xfce.

Been there, done that. XFCE 4.6.x (dunno about 4.4.x) is crappy. It's panel messes up it's contents constantly. You can't open blank media and/or archives as folders in thunar.

Also, I'm very sure that "mutter" will end up with only the "M$ approved, proffesional" functions from compiz included and everything else (including cube, sphere and wobbly) taken away.

> **Mr. Picklesworth said:**
> Thank you, good sir, for entering this thread with common sense in gear. (Where is that thumbs up button?...)

-


That feature was removed from the forum software a few updates ago, for no reason at all.

> **Mr. Picklesworth said:**
> You're thinking this way out of proportion. It isn't predatory tactics; it is just a natural, interesting (and common) choice to directly connect the window manager and the rest of the shell. To explain this all really quickly, since I think I've already explained it multiple times: Nobody has a problem that GDM feels nicer than XDM or KDM when they are logging in to a GNOME session. Nobody has a problem, or should have a problem, that they can't 'put Compiz in their Fluxbox.'

Also, GNOME is a platform. There are different products making use of its technologies for different interfaces right now. Two strong examples are Moblin and Maemo. Nothing is changing; just a new desktop, like Moblin is or HP's MIE, but this one happens to be the default focus for the GNOME project.


Further, maintaining the rather **hopeless case** that is GNOME Panel and an old branch of Metacity *alongside* new stuff is not an option. If you want, maintain it yourself (GNOME is still quite modular) or hope that there is a distro out there insane enough to do so. I bet it'll last three months before they realize it is not as perfect as they thought.

If you think the gnome's panel is a hopeless case, wait to see the xfce one. After a few days fighting it's permanent "amnesia" (the applets just disappear or appear in a different location (within a panel) and/or panel (if you have a multi-panel setup) from the one you placed them in), you'll see.

> **OutOfReach said:**
> In my opinion, I don't like where GNOME 3.0 is going....

Me neither, I'm sure M$ IS INVOLVED.

> **dicairo said:**
> what i can say??? i watched a video on youtube and its really sucks and i hope that gnome team see all these opinions ; i cant imagine ubuntu without compiz or with this new cofiguration its really very bad :( at the end i think microsoft will thank gnome team for thiss :)

I'm sure it's M$ pulling the strings. They know they can't compete against linux on merit so they have set up a plan to uglify linux, which have going rolling quite succesfully.

About the only way out of this mess would be to fork gnome 2.28 (as soon as it's released), remove the preliminar gnome-shell, make the archive handler treat the archives as folders (instead of volumes), fix the CD/DVD burner so that when you insert a blank disc the "burner folder" appears, remove mono (optional, done just to attract the "boycottnovell" crowds), and integrate it into compiz, that way compiz becomes a full DE and gnome becomes whatever M$ told them to become.

---

### Post by -grubby on 2009-06-02
> **Ptero-4 said:**
> Just tested gnome-shell. One word "CRAPPY". It can't use the old applets I like and you can't customize it's "panel" (even the kde4 one can be customized and holds "applets").



Yeah, like which, windoze-clone KDE4, windoze-like lxde, or perhaps the crappy xfce which lacks decent filemanager based CD/DVD burner and archive manager, and lacks a compiz decorator, and an unified appearance manager panel, and I forgot, it's panel can't remember it's settings properly and "loses" or "moves" the applets around for no reason at all.



Been there, done that. XFCE 4.6.x (dunno about 4.4.x) is crappy. It's panel messes up it's contents constantly. You can't open blank media and/or archives as folders in thunar.

Also, I'm very sure that "mutter" will end up with only the "M$ approved, proffesional" functions from compiz included and everything else (including cube, sphere and wobbly) taken away.



That feature was removed from the forum software a few updates ago, for no reason at all.



If you think the gnome's panel is a hopeless case, wait to see the xfce one. After a few days fighting it's permanent "amnesia" (the applets just disappear or appear in a different location (within a panel) and/or panel (if you have a multi-panel setup) from the one you placed them in), you'll see.



Me neither, I'm sure M$ IS INVOLVED.



I'm sure it's M$ pulling the strings. They know they can't compete against linux on merit so they have set up a plan to uglify linux, which have going rolling quite succesfully.

[img]http://scienceblogs.com/insolence/facepalm.jpg[/img]

---

### Post by days_of_ruin on 2009-06-02
> **visionaire said:**
> Hi, i tried to build gnome-shell in Hardy nad have this error

Please run 'sudo apt-get install xulrunner-dev libffi-dev ' and try again.

i did aptitude search and found xulrunner-1.9-dev, install that, but still the same message

It's not possible to intall gnome-shell on hardy?

Thanks =)

Nope. It might be possible in intrepid but you are best off trying it in
jaunty.

---

### Post by dspari1 on 2009-06-02
> **'[h2o] said:**
> Gnome users will not have "a long time" without compositing effects, since the "replacement" for Compiz, Gnome Shell, is indeed composited. What "good" effects are is of course subjective, but there should be no technical reason that Gnome Shell couldn't look as good as Compiz.

There's no reason why KDM shouldn't have good compositing effects either, but yet it doesn't; it's still playing catchup. I'm sure eventually it will even out, but it will take a long time, so it's a good thing that I'm not blocked from using Compiz until this happens.

Note: It takes a lot of man power to code in all the compositing effects that Compiz has, and Gnome Shell will run into the same problem.

---

### Post by Ptero-4 on 2009-06-02
> **grubby- said:**
> [img]http://scienceblogs.com/insolence/facepalm.jpg[/img]

lol. I was just venting frustration because I can't just have a good, customizable and stable mac-like DE AND keep it (read: Be assured that it won't turn into something dislikable in any further release). KDE already changed and GNOME is on it's way there.

> **dspari1 said:**
> There's no reason why KDM shouldn't have good compositing effects either, but yet it doesn't; it's still playing catchup. I'm sure eventually it will even out, but it will take a long time, so it's a good thing that I'm not blocked from using Compiz until this happens.

Note: It takes a lot of man power to code in all the compositing effects that Compiz has, and Gnome Shell will run into the same problem.

Hmmm. Did you mean KWIN? because IIRC KDM is the display manager (graphical login box).

---

### Post by sertse on 2009-06-02
> **don_quixote said:**
> And that's why a lot of distributions (including Ubuntu) bundled together Compiz with GNOME, because it was and is a gazillion times better than pure GNOME ever was.  So, this 'just' addon is largely responsible for GNOME's popularity and usability over its competitors.

Ok, true. 

> **don_quixote said:**
>  GNOME is making it impossible for Compiz to work with the shell; Compiz developers have suggested various, relatively simple ways, in which Compiz could plug into the shell.  GNOME devs have stubbornly refused to consider this, and have partaken in basically belittling and name calling of Compiz developers.  If you think that's a professional way to act, OK.  I think it doesn't speak very highly of them, especially given the fact that the popularity of the GNOME desktop would be far lower without Compiz.

Really? I'm inclined to believe in etnlIcarus post that

> **etnlIcarus said:**
> The Gnome devs aren't going to *deliberately* screw themselves over - *thoughtlessly* screwing themselves over is another matter entirely..

unless I see otherwise.  

> **don_quixote said:**
> So if it were possible for GNOME to break all the currently written GTK applications, well that would be anyone's fault but GNOME's?  What I find sickening is the mentality that DEVELOPER is BEYOND CRITICISM.  It's not like one or two people are expressing concern over the direction the GNOME shell is heading in.  

Criticism of GNOME is fine. GNOME has an obligation that it's *own* stuff works well, and if it doesn't, we should comment on it. Oh yes, criticism that GNOME Shell sucks because "I can't cube", or whatever feature X for example, is fine.  

I am objecting to this belief, "entitlement mentality" that GNOME has a responsibility to unofficial 3rd party addons, which Compiz, though technologically awesome, is.   

> **don_quixote said:**
>  Once again - is the shell replicating the functionality that has the potential to dramatically increase productivity?  N.o.  The shell looks to almost be inherently designed to slow things down.  OK, maybe it makes sense on netbooks, but as a shell for laptops and desktops it is inherently a flawed design.  Maybe GNOME devs should think about these concerns instead of shrugging them off as if they are irrelevant.

Now you're on point. :) GNOME should look at them, 

I think we've reached an understanding.



I really want to see Compiz standalone develop into it's own DE. As many had had, Compiz deskmenu make it a sort of a  blinged up openbox already. It could team up with AWN, Cairo Dock, Gnome-Do (Which is typically associated with Compiz anyways as bling) for a dock. Fix up emerald as a window decorator etc and it'll be a complete system.

---

### Post by don_quixote on 2009-06-03
> **sertse said:**
> Now you're on point. :) GNOME should look at them, 

I think we've reached an understanding.

Indeed.  If GNOME replicates the functionality of Compiz, I wouldn't be the slightest bit opposed to the Shell; however, I remain skeptical because GNOME has historically been averse to 'complicating.'  

I could indeed care less about the Cube, flames appearing when I close an app, or whatever other silly effects Compiz can do.  I do care, however, about single scale (not wall/scale - which while nice, I don't want all the time), about launching off the panel (not through a clicka-clicka overlay), grouping of Windows, effective minimization, and selective maximization (the last two are not quite as show-stoppers but...).  KWin replicates (i.e. gives user the choice) some, though not all, of this functionality and gives users a choice of whether to use it.  That's the way to do it.

---

### Post by etnlIcarus on 2009-06-03
> **grubby- said:**
> [img]http://scienceblogs.com/insolence/facepalm.jpg[/img]This.

> **sertse said:**
> I am objecting to this belief, "entitlement mentality" that GNOME has a responsibility to unofficial 3rd party addons, which Compiz, though technologically awesome, is.This is a pretty tormented interpretation of people's criticisms. 'Gnome isn't playing nice in the OSS ecosystem' =/= 'Gnome has a, "responsibility", to play nice'. Equally, not having an explicit responsibility to do something is not necessarily a defence for not doing that something.

> I really want to see Compiz standalone develop into it's own DE. As many had had, Compiz deskmenu make it a sort of a  blinged up openbox already. It could team up with AWN, Cairo Dock, Gnome-Do (Which is typically associated with Compiz anyways as bling) for a dock. Fix up emerald as a window decorator etc and it'll be a complete system.What you just described is not even close to a, "complete system" (let alone a stable or user friendly one but that's neither here nor there). Look at what the LXDE or Xfce4 metapackages pull in as an example of what even a basic DE entails.

---

### Post by SmSpillaz on 2009-06-03
Whenever a Compiz dev or myself says something contraversial, it always seems to take me a while to find the flamewar that has happened on the ubuntu forums.

Firstly, I'm the one who wrote the original ML post. Secondly, I felt that my ideas and words were extremely harsh and naive so I wrote another post later on explaining what I meant and also apologizing for the words I had used.

It boils down to this:
 1) My issue with gnome-shell and it's implementation is that it integrates a fundamental part of the desktop - the panel, into the window manager. This means that when you try to launch any other window manager, you loose that fundamental part of your desktop. I don't think this is bad for just compiz, but what if hypothetically the next best thing since mutter comes along and they have to write a whole bunch of redundant code in order to emulate the functionality of the panel.
 2) I already know that putting WM hooks into gnome-shell is going to be impossible. This is due to the design of clutter.
 3) I'm already thinking of a solution that involves expanding cairo-dock to have a top-panel and send signals to compiz to handle the 'overlay mode' feature. It would require nvidia or DRI2, but by the time gnome 3 comes out that would be fairly mainstream.
 4) There seems to be a lot of FUD spread about compiz, mostly along the lines that it is incompatible with a lot of things and other projects will somehow find themselves compatible with them. It's totally untrue - the reason why compiz doesn't play nice with Flash, GL, Video, etc is the reason why KWin and Mutter won't play nice with them. It's the XServer and GLX and more specifically the way they handle the operation that transforms pixmaps to textures. Most of it is going to be solved with UXA and DRI2. Flash, is another issue and it should be using OpenGL or XV to do rendering.

- Sam

---

### Post by Islington on 2009-06-03
> **SmSpillaz said:**
> Whenever a Compiz dev or myself says something contraversial, it always seems to take me a while to find the flamewar that has happened on the ubuntu forums.

- Sam

Thanks for responding. All interesting things polarize people. They flame because they care. Hopefully your post really does tone down some of the responses and feelings in this thread. Good job on finding solutions and not getting discouraged by the noise.

So is compiz slowly becoming a separate de as others here are suggesting? Compiz menu is pretty neat, if you ask me..

---

### Post by SmSpillaz on 2009-06-03
> **Islington said:**
> Thanks for responding. All interesting things polarize people. They flame because they care. Hopefully your post really does tone down some of the responses and feelings in this thread. Good job on finding solutions and not getting discouraged by the noise.

So is compiz slowly becoming a separate de as others here are suggesting? Compiz menu is pretty neat, if you ask me..

We have no plans to make compiz a separate DE. Unless we suddenly get 50x20^25 developers or have a paid developer to do that. The reason is that we are already porting all 100~ plugins to a totally different architecture (this can take days at a time for some plugins, but at least we have most of animation, elements and some of cube done!)

There are sister projects I started to try and give some more advanced desktop functionality, such as SpringDesk, but due to the fact that all of the developers have virtually no free time, it's pretty much on hold indefinitely.

Personally, I'm not concerned that the 'market share' of compiz is diminishing. People are free to use the default mutter or kwin if they please. As long is there is a means to use compiz on gnome without functionality loss I am happy. (Compiz and Beryl were much better IMO in the days that you had to manually install since the community was much richer - now it is taken for granted).

---

### Post by stwschool on 2009-06-03
I'm a fan of compiz. It's a useful tool when teaching, with stuff like annotate being a useful tool for instance when showing my students something on a video, or highlighting a section of the screen. I also see where gnome-shell is going and think it could be useful. I would however like to see the two being compatible with each other, or at least gnome attempting to offer the same functionality offered by Compiz. If it doesn't, well it's horses for courses. When I need compiz I'll use a desktop that works for that. When I need gnome-shell I'll use that. We all have choice, that's the nature of linux. XFCE's coming along nicely, LXDE is making nice progress (I already prefer pcmanfm to nautilus for speed reasons) and there are others (enlightenment isn't bad). We don't need to jump off any bridges just yet. Change happens, you have choices, and remember you don't have to hit the update button.

---

### Post by don_quixote on 2009-06-03
> **SmSpillaz said:**
> Personally, I'm not concerned that the 'market share' of compiz is diminishing. People are free to use the default mutter or kwin if they please. As long is there is a means to use compiz on gnome without functionality loss I am happy. (Compiz and Beryl were much better IMO in the days that you had to manually install since the community was much richer - now it is taken for granted).

Obviously, I am not a developer but maybe Compiz can work with XFCE devs?  I feel that XFCE would not pull a stunt like this.

---

### Post by etnlIcarus on 2009-06-03
> **don_quixote said:**
> Obviously, I am not a developer but maybe Compiz can work with XFCE devs?  I feel that XFCE would not pull a stunt like this.

Depends upon how much control Xfce asserts over the software/libraries it uses. To a certain degree, Xfce is bound to go in similar directions to Gnome due to their sharing many libraries and Gnome being the much more prominent (and therefore influential) project. As far as current compatibility goes, the only major things missing are a decorator implementation for Xfwm (which is on the drawing board) and there tends to be some disagreement about how workspaces are handled. Xfce isn't likely to go shell anytime soon but an obvious example of how their fates are tied: with there being talk of Gtk+ slowly being superseded by clutter in Gnome, Xfce may soon face a choice between jumping toolkit or falling into obscurity.

That said, from my very limited experience with/less limited watching the Xfce devs, they seem like a somewhat insular group. Hardly hostile or feature-averse but they have a bit of a hard-on for the freedesktop.org specs (it's certainly their current focus) and they're reluctant to implement ideas where there's the potential for bloat or a large rewrite (obviously, there don't have the resources of the larger projects so you can't hold that last one against them).

---

### Post by SmSpillaz on 2009-06-04
We don't have any plans to merge with XFCE either. You can still launch compiz as the window manager in XFCE (and in KDE 4.3 as well - most of the KWin devs are pretty nice to us about that).

There's been other mythconceptions that have seemed to fuel debate in this thread too now that I read it, but I honestly don't have the time to address them. (I'd rather spend my time getting back to my schoolwork and doing some more compiz dev :-])

---

### Post by visionaire on 2009-06-04
> **days_of_ruin said:**
> Nope. It might be possible in intrepid but you are best off trying it in
jaunty.

Thanks, downloading Jaunty now:D

---

### Post by pspsampsp on 2009-09-18
Dont mean to bring up an old(-ish) thread but:

I really like gnome shell , it makes the whole desktop just flow i think if they polish it up a bit it will be pretty awesome. Despite what people say i think gnome 3.0 is going to be great.

---

### Post by practic on 2009-10-16
I looked at the videos for Gnome Shell, and it does look interesting. I'm sure it will be an advance step when it is finished..and if it goes in a direction that many don't like, well I guess it'll just get forked and we'll have another desktop managers to choose from!

Personally, Compiz was one of the things that made me "run and not walk" away from Windows. I love the wobbly windows, they make the whole desktop feel fluid and alive. When I go back to a desktop that doesn't have them, it feels clunky and stiff. I also like the transparency effect when a window is moved or grabbed...I often use this to see something on another window that is underneath the one I am working on. There are a lot of effects that I don't often use, but I'm glad they are there, so that there are choices, and things to experiment with when one way of working becomes too dull. Compiz is like a cupboard full of spices...it makes the food so much more interesting!

Calling it "bloated" and "hack work" is something I can't really sympathize with. What Compiz accomplished with even modest graphic resources is amazing. For example, I'm running it on a netbook with 1gb RAM and integrated graphics and it works wonderfully.

So I'm hoping that Gnome doesn't go about re-inventing the wheel (and in the process gives us something square instead of round!), but somehow collaborates or borrows from the rich heritage that is already there.

---

### Post by lovinglinux on 2009-10-16
> **practic said:**
> I love the wobbly windows, they make the whole desktop feel fluid and alive. When I go back to a desktop that doesn't have them, it feels clunky and stiff. 

I agree. It's weird to log into Windows or even Ubuntu just a after a clean install. Some people say wobbly is crap or something, but it think it is great.


> **practic said:**
> There are a lot of effects that I don't often use, but I'm glad they are there, so that there are choices, and things to experiment with when one way of working becomes too dull. Compiz is like a cupboard full of spices...it makes the food so much more interesting!

I agree again. For instance, the fire effect, which I thought was silly, is excellent when combined with easystroke, because you can see the stroke pattern.

> **practic said:**
> Calling it "bloated" and "hack work" is something I can't really sympathize with. What Compiz accomplished with even modest graphic resources is amazing. For example, I'm running it on a netbook with 1gb RAM and integrated graphics and it works wonderfully.

It works really good for me on a P4 with 2Gb ram. I also have a 250 Mb RAM notebook and it works just fine. Never crashed.

> **practic said:**
> So I'm hoping that Gnome doesn't go about re-inventing the wheel (and in the process gives us something square instead of round!), but somehow collaborates or borrows from the rich heritage that is already there.

I must thank the gnome-shell developers, otherwise I wouldn't make an effort to switch to KDE. I couldn't be happier with my desktop the way it is now. Bye gnome :)

---

### Post by Exodist on 2009-10-16
> **lovinglinux said:**
> 
I must thank the gnome-shell developers, otherwise I wouldn't make an effort to switch to KDE. I couldn't be happier with my desktop the way it is now. Bye gnome :)

I agree. :)

Just did a upgrade to 4.3.2 in Jaunty. Damn this is looking good. Stable, fast and great looking. KDE has finally kicked it up a notch..


Kudoos to the KDE devs..


I know this would never happen, but IMHO Mark should have Ubuntu switch to KDE as main desktop after Lucid.

---

### Post by hoppipolla on 2009-10-16
> **Islington said:**
> "KDE sort of has a similar issue, in that the desktop is tied in with the panel, but that makes sense anyways because there aren’t really any other desktop shells that are designed to replace the default desktop (other than SpringDesk of course, but that is on hold ATM and would probably have a panel of it’s own)." from [Sam (Developer)](http://smspillaz.wordpress.com/2009/04/02/compiz-09x-where-are-we-now-and-where-to-from-here/)

Sorry I'm sure someone's said this already but I just wanted to throw out there in KDE's defense - Compiz works fine on KDE. It would replace Kwin, which is not tied to the panel or the desktop.

---

### Post by Sashin on 2009-10-16
Gnome shell is far from complete, I'm 100% that in time we'll have something far slicker, customizable and functional than what we can see now.

While I do agree that what we have now is much better than Gnome Shell is at present, its incomplete and thus cannot be used as a true indication of what it'll be about.

If there's any serious missing functionality upon its release it'll be demanded by users and will be fixed by its integration in ubuntu which will be in lucid +1. Hopefully all the compiz effects are properly added (unlike k win which feels much worse). Things like the cube, and even wobbly windows were functional, as they helped users visualise things and understand concepts of workspaces, and windows.

---

### Post by DracoJesi on 2009-10-26
> **gnomeuser said:**
> And you, like pretty much everyone in this thread, completely and entirely miss the point of the d-d-l thread. Read it, nobody is taking your bling away, it is no longer being fueled by compiz for various technical reasons. It will in the future be provided by an integrated solution called Mutter which is extendable to bring all the useless crack Compiz has. And even at that, this is just one of 3 proposed options which is up for debate.

so we get to keep our cube and expo and all that good stuff but we may have to wait awhile? that doesn't seem so bad?

is Mutter really better at that stuff than Compiz? because Compiz is pretty darn impressive...... and if I'm going to run something else instead, it had better bring something to the table....

as for Gnome Shell itself.... it looks like it has some useful features although I've only seen it via youtube.... I think I'm going to install it here in a bit......

but two questions, that activity button is pretty handy but what if I want to keep my old menus as well? and I want my applications to be listed on a bottom bar with the desktop selector like we have now? can I do that? or am I stuck to that one configuration because the panel is a crucial part now?

because that would be very inconvenient.... 

and I'm going to have to read this whole thread.....

---

### Post by DracoJesi on 2009-10-26
> **practic said:**
> I looked at the videos for Gnome Shell, and it does look interesting. I'm sure it will be an advance step when it is finished..and if it goes in a direction that many don't like, well I guess it'll just get forked and we'll have another desktop managers to choose from!

Personally, Compiz was one of the things that made me "run and not walk" away from Windows. I love the wobbly windows, they make the whole desktop feel fluid and alive. When I go back to a desktop that doesn't have them, it feels clunky and stiff. I also like the transparency effect when a window is moved or grabbed...I often use this to see something on another window that is underneath the one I am working on. There are a lot of effects that I don't often use, but I'm glad they are there, so that there are choices, and things to experiment with when one way of working becomes too dull. Compiz is like a cupboard full of spices...it makes the food so much more interesting!

Calling it "bloated" and "hack work" is something I can't really sympathize with. What Compiz accomplished with even modest graphic resources is amazing. For example, I'm running it on a netbook with 1gb RAM and integrated graphics and it works wonderfully.

So I'm hoping that Gnome doesn't go about re-inventing the wheel (and in the process gives us something square instead of round!), but somehow collaborates or borrows from the rich heritage that is already there.

This is pretty much how I feel, even if the current compiz is nearing it's end, that doesn't mean we can implement many of those features into Gnome Shell :)

they've done some amazing work :guitar:

---

### Post by t.rei on 2009-11-08
I'm not even shure if I like the concept of gnome shell. Last time I checked it was an unsuable, unconfigurable, uncustomizable piece of blackness... with a clock and some apps in a starter that I couldn't even sort for myself. *g*

---

### Post by zagz on 2009-11-24
> **t.rei said:**
> I'm not even shure if I like the concept of gnome shell. Last time I checked it was an unsuable, unconfigurable, uncustomizable piece of blackness... with a clock and some apps in a starter that I couldn't even sort for myself. *g*


Developers are dammed if they do and dammed if they dont, releasing gnome-shell or any other software early helps the speed of development massively, it opens it up to hundreds of thousands of people to input and help with bug reports. and so on.

---

### Post by tuahaa on 2009-11-24
I tried Gnome Shell and I like it but the problem is Compiz- it doesn't work. The resource consumption is a bit bigger than compiz too. I think Compiz is the only WM with such slick animations (eg wobbly windows) that barely uses system resources...

I'm a bit disappointed that Gnome 3 can't have Compiz, but they might do a bit of tweaking in the future. Or maybe we will see Compiz in KDE5?

---

### Post by Exodist on 2009-11-24
> I use a different window manager, And I feel this is terrible.
 I use a different window manager, And I think that this is fine.
 I use only Metacity, And I feel this is terrible.
 I use only Metacity, And I think that this is fine.


This is prob the most confusing poll yet. How the heck do you guys come up with such crack head poll options.

////////////////////////////////////////////////////////////////////////////////////////

Back on Topic..   


They should not be trying to remake a whole new compositing engine. They should work on adding REAL features back to Gnome and if they got a bit of spare time for stupid mess like this they should help with getting Compiz performance beefed up with out hurting stability. Compiz has enough features, we need more speed and stability from it.

Gnome 3.0s shell mess is nothing more then some person trying to make a name for themself instead of working as a cooperative and improving existing technology we have now. Its cumbersome, excessive and awkward for anyone to get used to using. I for one will say piss on Gnome and move to XFCE with GTK and I have been using Gnome since 1.x.

---

### Post by rolandixor on 2009-11-28
not to say gnome-shell sucks, (it does), but I can't get it to run. I installed the version in karmic. then one from a ppa. next is to compile it. but so far, mutter works (I like mutter) but gnome shell sucks. (btw, mutter isn't nearly as good as compiz. it's not smooth, and really needs work if it's to even come close).

---

### Post by arranmc182 on 2009-12-14
I think that compiz is getting to the point where i dont find it fun any or useful more and the move away from it ok with me compiz was cool to show how a desktop can be but we need to integrate this kind of stuff in to the desktop i think this would make things more stable.

---

### Post by rolandixor on 2009-12-29
at least compiz can start.

---

### Post by thomasmc on 2009-12-29
gnome-shell is kind of neat, except for that THING at the top of the screen. If they think they are going to replace the panel with that, they will kill Gnome dead. They arrogantly think they are going to make us have all exactly the same desktop, with absolutely no configurability whatsoever. If I wanted to be treated like that, I would go back to MS Windows.

It's a good thing that Gnome 3 won't be ready in time for the LTS 10.4 Ubuntu release, because once people actually try the new Gnome shell, most are going to HATE it, and go back to the LTS, and Ubuntu will be in limbo unless they can convince the Gnome devs into fixing what they broke. If they don't pull their heads out of their butts, they just might find that Gnome ends up being little more than a footnote in the Wikipedia entry for Linux.

---

### Post by MasterNetra on 2009-12-30
Far as I'm concerned as long as Gnome has all the options I want/need and remains rock solid then I'll stick with gnome. Even if it means that I will need to get used to a new appearence. Gnome-Shell wasn't that bad, requires some getting used to but meh. Side note Gnome-Shell had a nasty habit of being able to kill my system (freezes) i suspect that won't be a problem though on the actual release. (better not anyway)

---

### Post by jrothwell97 on 2009-12-30
'sfar as I'm concerned, GNOME 3 having an integrated window manager is fine - *on one condition*.

It must *not* slow to a crawl on less powerful machines. The machine I'm using now is from 2003/4-ish, and Compiz manages it just fine. When using GNOME-Shell, on the other hand, it feels like time has stopped - **literally**.

Lower hardware requirements must be taken into account, especially considering that one of Ubuntu's major selling points is that it requires fewer system resources than Windows, and will therefore let you keep your old hardware running longer.

---

### Post by bruno9779 on 2009-12-30
> **mr. Picklesworth said:**
> on the other hand, the shell as a window manager has many visual effects that, frankly, already work better than compiz.

Further, gnome is *meant* to be an integrated solution. If you want something modular, use one of the myriad of such window managers / desktop environments out there, like xfce. For that matter, this change just puts gnome in the same style as those (quite successful!) window managers that people happily work with completely, like wmii or awesome.
I can't say i really understand the whole "window manager + panel" thing yet in terms of what it brings to the table, but i can see how it would help with transitions to have all that stuff handled in one place. I suspect it would let the environment apply little quirks to window management such as tracking which launcher an application came from and performing awesome stuff with the knowledge. (although that could still be done without taking over window management outright).

Compiz is becoming redundant and simply is not going to work as a drop-in replacement for the big desktop environments. This has always been inevitable. The mature choice would be for the compiz people to accept that and either target the more modular environments or start accepting what the thing presently is: A (fantastic) *experiment* that had its moment in the sun. Compiz has a lot of great effects code, and the compiz developers know that code best, so i think it would be pretty cool of them to start contributing to their favourite desktop-integrated window managers directly (be they kwm or metacity) instead of struggling to maintain a redundant product where such a thing doesn't need to exist.

+1

---

### Post by Fri13 on 2009-12-30
> **linuxisevolution said:**
> Exactly, except the kernel devs would never integrate the gui with the kernel, thats one of the reason Windows sucks so badly...


Maybe there could be a desktop kernel, with the gui integrated, and a server kernel, with no gui integration, but still Xorg compatible. That's what syllable OS is doing.

Very efficient that way too.:popcorn:

Linux devs will never integrate the GUI to the linux OS. It will always kept as separated software like this far. The Linux OS does include the support for Xorg, it is needed so we can have a accelerated graphics, but 99.x% of Xorg is still running as outside of the OS. Same thing is with CLI as well. Bash, SH, ZHS etc are all outside of the OS. There is no reasons to the OS have a integrated GUI/CLI.

In 1.x series of Linux OS there was a question among Linux devs that the build own CLI inside the Linux OS. But they dropped it soon of because it brought just problems to have shell inside the OS and double work because GNU project Bash was already great shell running top of the Linux OS.

MS did that stupid thing that it integrated the Windows on Windows 95 to the MS-DOS. Before that the Windows was more like Gnome or KDE. But just a windowing environment top of the MS-DOS. And as far the Window shell has belonged to the MS own operating systems and NT is still same, even on the current release of NT 6.1 what is the OS of windows 7.

And there is a branch of Xorg where it is rewritten to be a very small windowing system and the project has a fork of the Linux OS (= the linux kernel) where the whole windowing system is integrated to the Linux OS. It should be faster and cleaner but not so far it hasn't proofed to be so.

Gnome can do what they want. They should throw Compiz-Fusion out because C-F has never willingly supported other desktop environments (KDE, XFCE, LXDE) so well, they focus has always be on Gnome. And Gnome is not there to support Compiz. If C-F devs are not ready to change their ideas about modularity and fixing C-F how it would be needed, they need to understand that Gnome does what KDE devs did, rejected C-F and build own plugins.

And hey, Canonical is not microsoft, even how much it tries to be and ubuntu is not windows, how much Ubuntu fans want it to be. Canonical does not have power to step foot down to stop Gnome doing what they want. It is Gnome project and if canonical wants, they can fork Gnome and start maintaining it if wanted. They just do not have man power for that task.

And Canonical should start listening the open source projects and not just trying to use them for it's own advantage. The open source world is outside of the Ubuntu, that is something what Ubuntu fans should learn. Ubuntu is just one small distribution among others, even it has great marketing spot on media, it does not make it the leading distribution (Even debian with KDE has over 52 million users on Brazil alone. Think about it with your under 12 million userbase).

Gnome project has own problems already. They want to go more closed source and move away from GNU project. It is just funny that GNOME is a acronym about GNU Network Object Modeling Environment (or similar). Is GNOME ready then change the name as well? GNOME devs are now kissing the cloak of MS with C# and Mono. Not so good idea. Now people have started to hope that Canonical would reject the Gnome and start using KDE SC for mainline. There is everything what is needed and this thing of Gnome shell just supports even that act what canonical should do.

---

### Post by 23meg on 2009-12-30
> **thomasmc said:**
> gnome-shell is kind of neat, except for that THING at the top of the screen. If they think they are going to replace the panel with that, they will kill Gnome dead. They arrogantly think they are going to make us have all exactly the same desktop, with absolutely no configurability whatsoever. If I wanted to be treated like that, I would go back to MS Windows.

GNOME Shell has [an extensions system]("http://live.gnome.org/GnomeShell/Extensions") that makes it possible to tweak every part of the shell with arbitrary JavaScript and CSS on the fly, without even having to recompile it.

---

### Post by forrestcupp on 2009-12-30
> **23meg said:**
> GNOME Shell has [an extensions system]("http://live.gnome.org/GnomeShell/Extensions") that makes it possible to tweak every part of the shell with arbitrary JavaScript and CSS on the fly, without even having to recompile it.

Awesome

---

### Post by thomasmc on 2009-12-30
> **23meg said:**
> GNOME Shell has [an extensions system]("http://live.gnome.org/GnomeShell/Extensions") that makes it possible to tweak every part of the shell with arbitrary JavaScript and CSS on the fly, without even having to recompile it.

So, on the one hand Gnome wants to cripple everything to make it "more usable", eliminating all choice like some sort of software fascists (gnome-screensaver, for example), and on the other, they expect people to write their own javascript extensions and create UUIDs just to configure the shell? WTF?

And, as the link you pointed to clearly states: "The extension system is *not* a replacement for "applets" or "widgets"."

When my old computer died a month ago, I was stuck for a few weeks with an old HP tablet. XP was practically comatose on that 1Ghz cpu, so I installed Xubuntu. I liked it. A lot. In many ways, it's BETTER than Gnome. Gnome should step back and consider that they are only #1 because so many people fled KDE when they tried a similar-but-not-as-stupid stunt. Do they really think those people are going to remain when they shove that ridiculous shell down everyone's throats? I think the big winner when 3.0 comes out won't be Gnome, but XFCE and maybe LXDE. If Gnome won't listen to the users, it will just become irrelevant to them.

And yes, I get that the gnome-panel is a wreck. But throwing everything out and starting over, instead of just fixing it, is like trading in a nice car because you found out it needs new brakes. And you aren't even the one driving the car, and the person driving the car DOESN'T want to trade it in! And from the looks of it, it will be a serious trade DOWN, not trade up.

---

### Post by click4851 on 2009-12-30
my suspicion is that the people/committee making the decisions will do what they think is best regardless of any external stimulus or feedback. They have a goal for the DE and they will view any critical view as either a reluctance to change or a contrary viewpoint. They will make the change even if it's a partial/abject failure, and relives the KDE4 user migration, all in the name of forward motion toward the long term goal. Maybe not the lowest common denominator decision, but is it change for change sake?

---

### Post by thomasmc on 2009-12-30
My New Year's Prediction for 2010:

Within 6 months of releasing Gnome 3.0, they will drop from the #1 slot to #3. Distros that focus on making things easy for new Linux users will drop Gnome like a radioactive hot potato. I can't imagine ever getting a MS Windows user to switch to Linux by showing them that thing they are calling a shell. It's glitzy yes, but not usable, and they've made it damned clear they have no intention of making it usable. I've tried to use it, but it is just too damned much work to get anything done with it, and it gives me a headache jumping in and out like that all the time. (And no, I'm not a n00b, I was programming computers before some of your parents were born.) You can get many of the same glitzy effects in Compiz with  ExpoEdge bound to a corner of the screen, etc., and then you don't lose the functionality of the panel. And the fact that Gnome just doesn't care what the people who actually use Gnome think is maddening, and makes me want to switch to anything else, ASAP.

Gnome
R.I.P.
2010

---

### Post by Mornedhel on 2009-12-30
> **23meg said:**
> GNOME Shell has [an extensions system]("http://live.gnome.org/GnomeShell/Extensions") that makes it possible to tweak every part of the shell with arbitrary JavaScript and CSS on the fly, without even having to recompile it.

Is that how I'm supposed to make Gnome Shell display time in 24h rather than 12 ?  Because right now either the configuration option for that is really really well hidden, or I need a more recent version than the current one on Karmic.

---

### Post by 23meg on 2010-01-01
> **thomasmc said:**
> So, on the one hand Gnome wants to cripple everything to make it "more usable", eliminating all choice like some sort of software fascists (gnome-screensaver, for example),

[No]("http://ubuntuforums.org/showpost.php?p=7761247&postcount=203").

> **thomasmc said:**
> and on the other, they expect people to write their own javascript extensions and create UUIDs just to configure the shell? WTF?

No, just like Mozilla doesn't expect people to write their own Firefox extensions just to configure Firefox.

A significant difference is that GNOME Shell is still **incomplete**, thus some basic configuration facilities are missing at this point.

The extensions system isn't meant as a replacement for basic configuration tools or applets; it's meant for extending GNOME Shell and tweaking its internals beyond the scope of default configuration tools. Once the extensions system matures and people pick up on it, you can expect a huge "marketplace" of GNOME Shell modifications and extensions, similar to addons.mozilla.org, since the system lowers the barriers by using JS and CSS, and making instant modification possible.

> **thomasmc]And, as the link you pointed to clearly states: "The extension system is *not* a replacement for "applets" or "widgets"."[/QUOTE]

So? It doesn't state "GNOME Shell will have no replacement for the existing GNOME applets", right? 

What exactly will replace the GNOME 2.x concept of "applets" is still a matter of debate said:**
> Is that how I'm supposed to make Gnome Shell display time in 24h rather than 12 ? 

No, it will not be on the 2.32 release.

---

### Post by k64 on 2010-01-01
> **Islington said:**
> from [Sam (Developer)]("http://smspillaz.wordpress.com/2009/04/02/compiz-09x-where-are-we-now-and-where-to-from-here/")

Not allowing me to change window manager, without losing functionality? W.T.F. Just Work(tm) doesn't mean that I have to be stuck with an inferior product(Metacity), which I cant replace. I had quite enough of that in Windows (Still cant remove IE). Look, I am just a user, I know no languages other than some BASIC. And I know that the developers don't really have to care about anything I say. But please, I really do feel this is a mistake. Isn't Linux supposed to be small independent programs working together? Please, Please, Please don't take away my option/freedom to change window managers.

What do you feel about this? Is there any way we can contact any gnome devels and beg/whine at them to change their mind?

GNOME Shell drops support for Compiz and uses [Clutter]("http://www.clutter-project.org/") instead, in order to allow applications to also have its effects. Clutter, people, is an OpenGL toolkit/API designed to eliminate hassle for programmers - and allow them to rapidly develop applications and visual effects without writing 1,000 lines of code.

---

### Post by HappinessNow on 2010-01-01
> **smartboyathome said:**
> I think they are going the way of Enlightenment. ;)

> **Skripka said:**
> You mean Gnome 3.0 is going to take 4 years to come out of beta? :lolflag:more like 7 years or maybe indefinitely ever :P

---

### Post by 23meg on 2010-01-01
> **k64 said:**
> GNOME Shell drops support for Compiz and uses [Clutter]("http://www.clutter-project.org/") instead, in order to allow applications to also have its effects. Clutter, people, is an OpenGL toolkit/API designed to eliminate hassle for programmers - and allow them to rapidly develop applications and visual effects without writing 1,000 lines of code.

GNOME Shell doesn't use Clutter "instead of" Compiz; the two are pretty unrelated pieces of technology. And applications can use Clutter regardless of whether the shell / window manager also uses it.

Actually, as far as I know, GNOME Shell doesn't use Clutter for animations at all, but for scene graph layout. Animations are handled with Tweener.

---

### Post by Exodist on 2010-01-01
They still have it listed on the GNOME website to be release next release.. I so doubt it... 
[http://library.gnome.org/misc/release-notes/2.28/#rnlookingforward](http://library.gnome.org/misc/release-notes/2.28/#rnlookingforward)

---

### Post by jackdale on 2010-01-08
All the videos I've seen of the new Gnome Shell look awfully SLOW.

Has anyone reading this used any of the beta versions on a modern computer to see if it is just ancient processors with no RAM (I doubt it) or if it is just a really SLOW way doing things?  I've read some ppl talking about very slow redraws as well...

(Does this spell death for GNOME?):o

---

### Post by jackdale on 2010-01-08
All the videos I've seen of the new Gnome Shell look awfully SLOW.

Has anyone reading this used any of the beta versions on a modern computer to see if it is just ancient processors with no RAM (I doubt it) or if it is just a really SLOW way doing things?  I've read some ppl talking about very slow redraws as well...

(Does this spell death for GNOME?):o

Also, I can use gnome on my very old computer (just with no extra effects) and it can run almost as satisfactorily as my new one (which runs cairo-doc and compiz).  Will this mean that I will need to change to Xubuntu for updates?:(

---

### Post by orlox on 2010-01-09
> **jackdale said:**
> 
Also, I can use gnome on my very old computer (just with no extra effects) and it can run almost as satisfactorily as my new one (which runs cairo-doc and compiz).  Will this mean that I will need to change to Xubuntu for updates?:(

Eventually you will have to choose something different, cause if they keep their plans, hardware acceleration will be required. However, considering ubuntu 10.04 will be a long term support version, you shouldn't really worry about it so much for at least five years, unless you want some cutting edge in that computer.

---

### Post by jackdale on 2010-01-09
I just tried the gnome-shell on my new computer (Dual Core 2.6GHz (x2); 4GB RAM; 1GB GPU).

OK I realise that it is still in development and very obviously still buggy.  HOWEVER, the redraws are unreasonably slow.  I hope that it speeds up.  

One of my concerns is the DOWNGRADE in functionality I like the exposè-style menu bar.  However, will there be window grouping functions, cube functions, active edges, etc, which make COMPIZ a joy to work with and very intuitive?

At this stage, I will be staying with gnome-panel + Compiz.

As for my old computer, it is definitely staying with 10.04.

Also, I use VMWare Fusion 2 in a MacBookPro to carry Ubuntu with me where-ever I go.  Naturally, VMWare F 2 does not have OpenGL support.  Does this mean not virtual ubuntu? (Which is how I discovered ubuntu in the first place!)

---

### Post by gsmanners on 2010-01-09
It seems to me like Gnome Shell should at some point have plugins to emulate the current behavior of Gnome and (if sanity prevails) remove the need for 3D hardware. In fact, the old behavior really should be the default for Gnome. The new features and 3D requirements should be treated as optional.

Failing the above, I can certainly see a mass migration to Xfce (which would put me in good company), and the Ubuntu brand name would suffer some serious credibility problems.

---

### Post by jackdale on 2010-01-09
The Gnome Shell is a CPU glutton:
CPU1 - 56%!
CPU2 - 64%!

No wonder the redraws are so slow.  that's without any app other than the terminal running and system monitor!  What a nightmare.  i hope this is just a VERY EARLY Alpha release...

My CPU @ present with Firefox, Compiz, Cairo-Dock and system monitor:
CPU1: 1%
CPU2: 2%

---

### Post by Redache on 2010-01-09
It's not slated to be released until September iirc. They might push it back to later if it's still problematic.

I like Gnome Shell and have been using it a lot. I haven't noticed the efficiency issues quite so much, could it be something to do with 32 vs 64 bit?.

---

### Post by jackdale on 2010-01-09
> **Redache said:**
> It's not slated to be released until September iirc. They might push it back to later if it's still problematic.

I like Gnome Shell and have been using it a lot. I haven't noticed the efficiency issues quite so much, could it be something to do with 32 vs 64 bit?.

Dunno, I'm using 64bit Ubuntu 9.10 all updates (stable).  Intel Dual Core and NVIDA graphics card (as per my antepenultimate message).

---

### Post by techno-mole on 2010-02-17
i disagree that gnome-shell is a bad idea, im using it and to be honest its running smoother than compiz does, but thats more down to my messing around with compiz more than anything.

im running gnome shell,cairo dock and screenlets along with gnome do and to be honest i have no slow downs or any other graphical issues, or performance issues.

i normally run awn and compiz, and if i feel like it emerald to change themes a bit, just thought id try gs i like gnome shell, and i seem to be getting things done a lot quicker, i disagree that gnome wants to be like kde (ive tried kde 4.4 recently and its pretty good)

heres a radical idea, what about allow users to choose what they want to run ? i dont know enough about programming to know if this is even possible, but what about having an option to choose the window manager at setup ? get partitioning etc out of the way and then give the user the choice to install gnome shell (insert info about gnome shell) or compiz etc etc, like i said i cant program to save my life, but i can explain things quite well, i would be willing to write the descriptions and instructions for installing the various window managers etc at start up

i like gnome shell, i like compiz, i like kde, i like running awn (which needs compiz to be running) i like cairo dock, i can choose what to run myself, installing the various options isnt that difficult, even for noobs, as long as its explained in an easy way, this has been a niggle of mine with ubuntu and linux in general, sometimes how to's etc seem to assume you know how to compile and configure this and that, most people dont, but if it was explained in a little less complicated way people wouldnt be so afraid of trying something new.

---

### Post by techno-mole on 2010-02-17
> **jackdale said:**
> The Gnome Shell is a CPU glutton:
CPU1 - 56%!
CPU2 - 64%!

No wonder the redraws are so slow.  that's without any app other than the terminal running and system monitor!  What a nightmare.  i hope this is just a VERY EARLY Alpha release...

My CPU @ present with Firefox, Compiz, Cairo-Dock and system monitor:
CPU1: 1%
CPU2: 2%

just to add my 2 pence worth, im running - cairo dock, gnome do, gnome shell and screenlets and my dual core athalon isnt even getting warm, on idle both cores arent going over 3% and even when i start doing stuff they arent going above 60% on each core.

my system specs - 
amd athalon x2 6000+ (running at stock speed 3.1ghz)
4gb ddr2 ram @ 800mhz
pci express graphics - nvidia 9500gt - (512mb ddr3 sdram)
2 x sata drives - 1 @ 500gb and 1 @ 250 gb
cmedia pci sound card, not the best but pretty good sound out of it.

---

### Post by Woolio1 on 2010-02-17
So I lose my panel. GREAT! Excellent, in fact. That means I can get rid of that pesky thing...

I've gone to completely using AWN and Compiz, with GTK as my window decorator... Might switch to Emerald, though.

Who needs Metacity?

---

### Post by Psumi on 2010-02-17
> **Woolio1 said:**
> Who needs Metacity?

I'm pretty sure that mutter, the window manager/compositor for GNOME Shell uses metacity.

Then again, I've never tried emerald without compiz.

For those of you who haven't said it yet: Compiz development has slowed or even halted, and there hasn't been a new version in a while.

---

### Post by HTML-insane on 2010-02-21
I'm perfectly fine with integrating compositing effects into existing desktop environments. In fact, compositing is pretty important for my workflow one KDE 4.4's netbook interface, and it's fast and pretty enough that I don't want to change it.

What I'm not particularly fond of is the direction Gnome are going with Gnome Shell... it's like they expect me to be adding/removing virtual desktops all the time, even when all I want to do is open an application from the menu. :/

---

### Post by litemirrors on 2010-02-23
You all won't be so happy once you find out just how much you miss those Compiz effects you're touting as being "eye candy" and "useless". I doubt any new converts will be choosing Ubuntu then and will probably head over to Arch Linux or PCLinuxOS. I can see it all now, but what's more interesting is the seemingly confused people posting saying "Gnome Shell is slower than Compiz" lol Well that's because Compiz functions as ONLY a compositing engine and was written for that purpose, where-as trying to combine it with a Desktop Environment like Gnome is just asking for disaster. Sure have fun when everyone switches to Windows 7 and begins using CubeDesktop or DeskSpace (Active development).

The ONLY reason users come to Linux from Windows 7 is the EYE CANDY, believe me. Why would they ditch an OS they received freely upon purchasing a new PC for Linux? Check out all those Compiz videos on YouTube and tell me half those people didn't run straight to Ubuntu and download it afterward. That's infact why I'm here in the first place, I saw those videos years ago!

That being said people are certainly free to create an entirely opposing Ubuntu distro that supports Compiz and uses the older Gnome.

Noticed yet they took away your login themes by updating gdmsetp? lmao! Way to go!

I think really Compiz developers just need time to work on it, but times gone now and so it's probably going to be abandoned. Unless the original coder comes back and kicks everyones *** by rewriting it into a Desktop Environment. Then say by to Gnome.

I'm blabbering here now, it's frustrating to see Compiz threatened when it's the pinnacle of coolness on any platform. It puts to shame OS X and Windows.

No one comment on this it's more of me lamenting, cherrio!

---

### Post by ibuclaw on 2010-02-23
> **litemirrors said:**
> You all won't be so happy once you find out just how much you miss those Compiz effects you're touting as being "eye candy" and "useless".

As has already been iterated in this thread, compiz was a temporary patch to catch us up with the times until the major DE's get around to becoming relevant.

As for special effects, I don't think many people miss 3ddesktop, or the wonderful Beryl, and I certainly think not many people will miss Compiz when it's time comes round (I am happily using XCompMgr and have never looked back). The legacy it has left, though, will go on in one shape or another. :)

---

### Post by the yawner on 2010-02-23
I think Compiz is still a relevant project in that it's a continuously improving proof of concept. But relying on Compiz alone to provide us with the eyecandy and the more useful stuff is definitely a deterrent on the over-all growth of Gnome.

---

### Post by [h2o] on 2010-02-23
> **litemirrors said:**
> The ONLY reason users come to Linux from Windows 7 is the EYE CANDY, believe me.
No, I don't believe you.

Compiz was a cool proof of concept but we need something more integrated.

---

### Post by techno-mole on 2010-02-23
> 

The ONLY reason users come to Linux from Windows 7 is the EYE CANDY, believe me. Why would they ditch an OS they received freely upon purchasing a new PC for Linux? Check out all those Compiz videos on YouTube and tell me half those people didn't run straight to Ubuntu and download it afterward. That's infact why I'm here in the first place, I saw those videos years ago!



thats an interesting statement, I hadn't seen anything to do with "eye candy" before coming to ubuntu (which wasnt my first choice, tried knoppix first) and for some time I didnt bother with any dektop effects (i use some now for increasing my workflow, window switching mainly)

most people i know that use ubuntu,open suse,fedora etc etc use it because they are fed up with the holes in a lot of microsoft software, how secure is internet explorer now ? how secure is windows full stop ?

since coming over to linux (ubuntu) i have achieved more in my life than i ever did using windows, i have found using ubuntu has meant i have learned more about computers in 3 years than i did in 10 years of using windows, i have found applications that are free and built by people in their spare time to fare surpass a lot of windows expensive software.

in short in my humble opinion people start using linux (what ever flavour) for a variety of reasons (including in some cases the " eye candy ") but mostly because they no longer want to pay through the nose for antivirus software to keep their files safe, or pay through the nose for operating systems like vista, or pay through the nose for office software.

am i saying that the fact that ubuntu, open office etc etc are free is the main reason for moving to linux ? no im not, it may be for some, but for most i think its because they have realized that windows is not the only option, and another reason i feel is the community, generally speaking i have never had a problem with a linux users attitude towards a problem i have had, most seem like nice people,ive made a lot of posts on windows based forums and i can tell you they can be nasty gits.

---

### Post by Mr. Picklesworth on 2010-02-23
> **litemirrors said:**
> The ONLY reason users come to Linux from Windows 7 is the EYE CANDY, believe me.

As a proponent of the “let's not delude ourselves” philosophy, I became exhausted upon reading that.

Well, okay, maybe mobile Linux. WebOS, Android and Maemo have some real consistency and attention to detail. (Especially WebOS since the UI toolkit starts from scratch). The desktop? No.

Compared to Windows 7, our eye candy is really insignificant. Okay, I concede that the windows bounce around very smoothly in a well rendered desktop via GPU support. With some extra plugins, like head tracking and kinetics (there is a kinetics plugin, right?) we can make them bounce around in especially fascinating ways.

Windows's eye candy actually spans WITHIN those windows, with nice animations, consistent shadowing and 3D effects which provide some aid to what someone is actually doing. (Not just navigating between windows, which some would believe is all we do).

If people came to Linux for eye candy, they would go to KDE4, since its eye candy doesn't stop at window management (eg: QT's animation support, Plasma's potential to look really amazing) and it has the prettiest screenshots.

However, given the slow trickle of new users compared to our proprietary competition, and that a properly honest sales pitch on the Linux desktop would not mention eye candy but rather functional stuff such as the compose key, it being Unix-like, free, secure and that the fonts are adjustable, that last paragraph is a moot point.

> **litemirrors said:**
> Noticed yet they took away your login themes by updating gdmsetp? lmao! Way to go!

That happened because the new GDM (which, by the way, clears the way for real eye candy) doesn't support old themes. You can still [install the legacy GDM]("apt:gdm-2.20") if you want it.

---

### Post by litemirrors on 2010-02-23
Gnome didn't need to copy Compiz, they could just continue without compositing. Oh well whatever I had coffee I should make a "who here likes coffee more than tea" thread :L

Compiz RIP

---

### Post by swoll1980 on 2010-02-23
I don't get what the complaint is. You still get a choice, it's use Gnome, or find something else. Nothing is being forced on you.

---

### Post by Radicc on 2010-02-23
I'll probably check it out once it is "finished", but I doubt it will sway me from my current desktop setup.

Openbox + tint2 (& conky for bling, lol).

---

### Post by duanedesign on 2010-02-23
> **litemirrors said:**
> The ONLY reason users come to Linux from Windows 7 is the EYE CANDY, believe me. Why would they ditch an OS they received freely upon purchasing a new PC for Linux? 

Be careful of saying things like 'the only reason users'. Especially if you have no data to back this up. Your sentence should read 'I switched to Linux because...' or 'It is my opinion that....' Just a tip to help you remove fallacies from your writings in the future.

I ditched the OS that came with my computer for many reasons, a rotating cube being low on the list. Since my computer is a tool i use to be more productive the stability Linux provides ensures I have more uptime and spend less time fixing the OS. Also having access to the source code allows me to modify my programs to either fix bugs, or improve my productivity by introducing features that would otherwise be unavailable. Also the open source community allows me to communicate directly with developers and have a say in what features are implemented.

I am going off the subject of this thread so i will wrap it up.

The OS that came on your computer most likely is not 'Free' and i think this reason is the most important reason for using FOSS because it has implementations beyond computers and software. Keep in mind what the community means by free, its not financial. "To use free software is to make a political and ethical choice asserting the right to learn, and share what we learn with others.  Free software has become the foundation of a learning society where we share our knowledge in a way that others can build upon and enjoy...Currently, many people use proprietary software that denies users these freedoms and benefits...The corporations behind proprietary software will often spy on your activities and restrict you from sharing with others. And because our computers control much of our personal information and daily activities, proprietary software represents an unacceptable danger to a free society"[1]

</thread hijack>

[1]http://www.fsf.org/about/what-is-free-software

---

### Post by 23meg on 2010-02-24
> **swoll1980 said:**
> I don't get what the complaint is. You still get a choice, it's use Gnome, or find something else. Nothing is being forced on you.

More like: Use GNOME 3 with GNOME Shell, or disable GNOME Shell and use GNOME Panel, which will still be supported for some time, with Compiz or whatever else you want, or use *another panel* with Compiz or whatever else you want, *or* find something else.

Oh, but whining on forums and playing the "I will switch to $OTHER_DE_OR_OS if things don't work exactly like I want!!1" card is much more fun.

---

### Post by mastaful on 2010-02-24
using gnome-shell pretty much kills off using virtualization

there no way to keep a guest full screen

with compiz you just give the screen a flip.... windows... flip.... linux

gnome-shell once guest is full screen your stuck until you minimize it...and then click fullscreen again to use

.....as of right now anyway.

---

### Post by gsmanners on 2010-02-24
> **23meg said:**
> Oh, but whining on forums and playing the "I will switch to $OTHER_DE_OR_OS if things don't work exactly like I want!!1" card is much more fun.

I switched to Xfce mainly because of bugs in Gnome session which didn't permit me to run alternatives to Metacity and Gnome panel. You know, eventually, people do get fed up with all the "integration" and the bugs that go with it.

---

### Post by practic on 2010-02-24
> **23meg said:**
> Oh, but whining on forums and playing the "I will switch to $OTHER_DE_OR_OS if things don't work exactly like I want!!" card is much more fun.

Yes, precisely! Now let's get this straight...I'm the dictator here, and unless things go EXACTLY as I want them to, then I'll whip out the $HIDDEN_RED_BUTTON in Ubuntu and bring the whole Free Software Foundation to a swift end! Got it??! Good. Signing out...
:D

---

### Post by quequotion on 2010-03-08
> **the yawner said:**
> I think Compiz is still a relevant project in that it's a continuously improving proof of concept. But relying on Compiz alone to provide us with the eyecandy and the more useful stuff is definitely a deterrent on the over-all growth of Gnome.

I somewhat disagree.

A good desktop-manager should manage the desktop: Provide some basic layout and UI options, give the xserver a friendly face and the user a workable PC.

Compiz makes a great extension to a standard desktop-manager, adding some seriously useful functionality in addition to some useless decoration that some people just love. The useful functions it provides, like Scale and Opacify, can be kept out of the desktop-manager to make room for more basic functionality and stabilization.

I'd much rather see Gnome working on ways to wrap QT, KDE and Wine programs and stabilizing gnome-settings-daemon so everything makes sense than developing a redundant composting engine. It's come far, but Gnome still has some rough edges and a lot of chrome to polish.

Continuing with slightly less relevant gripes in no particular order:

It would be nice to have more composting managers available and more up-to-date information about them (I only know of Compiz and KWin and googling either typically gets results one to three years behind development).

"Write programs that do one thing and do it well. Write programs to work together." - Doug McIlroy
I really hate the way so many programs are developed for a specific desktop-manager. This is Micro$haft thinking at work and there should be no need to do this. It would be much better to have a set of standardized programs that run in any desktop-manager and desktop-managers designed to wrap programs appropriately to make a unified UI.... Such programs already exist of course, but are typically not shipped with distros or only used as alternatives to the desktop-manager bound programs. In more simple terms: I'd like to do away with specialized APIs in desktop-managers as it clutters the users hard drives with support libraries limits choices to specialized software.

Compiz needs a little more distinction between low-end and high-end GPU options, so it could be run on either more easily. I think progress is being made on that front, such that one could have a spiffy 2d desktop on a low-end machine or a deliciously gaudy 3d desktop on high-end one, but documentation on current development tends to be incomplete and/or out of date.

Ubuntu has had a "UI update" slated for something like the last five releases which I suppose is what Gnome-shell is meant to be.. but personally I don't see the need for Gnome to take up that bat. There are dozens of ways to make a unique, useful, and comprehensible desktop depending on what users want... and gnome-shell just doesn't offer that much. It's different, but it's not any more or less useful than the previous desktop. I don't feel tasks take me any more or less time to complete. Granted there may be a learning curve I haven't quite gotten over, but that's another problem... *There can be no learning curve* if a desktop-manager is going to be popular enough to boost linux's market share. It would perhaps have been a better idea to unify some of the popular extensions to Gnome and make a "gnome-extended" package based on some surveys of what people really want on, and in, their desktops and how people are using computers these days.  When I first saw gnome-shell I thought "This will be great for palm-tops!" and immediately purged it from my pc. It doesn't have the features I need, it doesn't support the extensions I like, and it didn't offer anything worth occupying a large amount of screen space that wasn't already available in Gnome.

There's a compiz extension in the works known as SpringDesk, which someone mentioned earlier in the thread I believe, which offers a lot more toward a unique and useful change in desktop-management. Unfortunately it's hard to tell how much or if development is progressing on this. It exists only as a mock-up and an empty git repo as far as I know.

/rant

tl;dr: compiz covers functions gnome shouldn't. gnome needs work. gnome-shell wasn't worth the wait.

---

### Post by gsmanners on 2010-03-08
> **quequotion said:**
> "Write programs that do one thing and do it well. Write programs to work together." - Doug McIlroy
...
It would be much better to have a set of standardized programs that run in any desktop-manager and desktop-managers designed to wrap programs appropriately to make a unified UI....

This is another thing I like about Xfce. It's built from the ground up with that philosophy.

> Xfce 4.6 embodies the traditional UNIX philosophy of modularity and re-usability. It consists of a number of components that together provide the full functionality of the desktop environment. They are packaged separately and you can pick and choose from the available packages to create the best personal working environment.

--from the [Xfce homepage]("http://www.xfce.org/")

---

### Post by SmSpillaz on 2010-03-19
Ugh, there seems to be this recurring theme that keeps on coming back here.

In plain english, it is:

1. Compiz isn't integrated into the desktop
so
2. Compiz is just a stop gap measure
therefore.
3. There is a justification for stopping it's effective use on the Gnome desktop.

I'm quite suprised at the lack of research that's actually been done in this thread as to what kind of integration compiz actually offers. If people had been watching the [development]("http://git.compiz.org/") at all, they probably would have noticed that we actually support high levels of integration into the desktop environment to the extent that is technically possible.

A lot of people take for granted the fact that they can keep their metacity window decorations when they use compiz. This is because of all the hard work that has gone into gtk-window-decorator by david_r, maniac, Amaranth, by cleverly using private libraries to get those decorations to work in compiz. They don't necessarily come for free.

Or maybe the fact that compiz would appear to have a high level of integration with KDE's present windows on taskbar, plasma thumbnails and plasma widget sliding might suggest that we put a lot of work into desktop integration. Thankfully, KDE has made this job a lot easier for us by recognizing that people sometimes want to use different compositing managers, so they implemented plasma effects with window properties that can be put in any compositing manager. This was a fairly trivial change, and saved a lot of headache for everyone.

Compiz does actually make an effort to make the fact that you are running a different window manager as transparent as possible and as far as I am concerned, all that integrating a panel into the window manager does (in the same process) is severely hinder this effort - in effect only hurting end users.

---

### Post by Psumi on 2010-03-19
> **litemirrors said:**
> You all won't be so happy once you find out just how much you miss those Compiz effects you're touting as being "eye candy" and "useless". I doubt any new converts will be choosing Ubuntu then...

1. I've not used compiz effects for months due to how low-spec my laptop is that I got recently.

2. Do I care if people come to Ubuntu? No. Because there are a lot of people already who use Ubuntu as ubuntu, not the eye-candy.

---

### Post by Kenny_Strawn on 2010-03-19
> **Psumi said:**
> 1. I've not used compiz effects for months due to how low-spec my laptop is that I got recently.


That may be true, but Mutter is just as bad...

---

### Post by WorLord on 2010-04-08
Well.

It seems no one was thrown into a blind panic at having all their "recent documents" displayed all out-in-the-open like that, just by clicking on the word "Activities".  Huh.

It seems no one got lost at the gigantic, scrollable grid of applications that was presented me when I clicked on that menu.  Alphabetical order is great, I suppose, when you know the exact name of the software you're looking for (they're listed in alphabetical order).  But if all you know is that its the yellow-colored icon in your "sound and video" menu, you're pretty borked.

Thankfully, people *have* noticed the *gigantic* performance difference between Gnome-shell and Compiz.  In no way is that trivial.  Absolutely not.  

Five minutes in, when I couldn't find a clickable way of clearing my "recent documents," I dropped back to the existing simple, clean, effective way of doing things - Gnome 2.28 with Docky.  I just needed some sanity for a while.

---

### Post by etnlIcarus on 2010-04-09
I'd imagine the Recent docs list is resourcing .recently-used.xbel, in which case adding:
```
gtk-recent-files-max-age=0
```
to your .gtkrc-2.0 file, ought to rectify that, at least.


Oh yeah and boo, hiss and etcetera Gnome-Shell. Long live Compiz.

---

### Post by Ozymandias_117 on 2010-05-20
From what all I've seen, it seems like Gnome is trying to help Mark Shuttleworth with his goal of making Ubuntu more and more like Mac (Not necessarily a bad thing, or a good thing, it just is :)) The panel is being designed to have a context sensitive menu like Mac. The way you choose your workspace (According to an OS X user) looks a lot like something they have. I wasn't sure about it when I first saw it on Gnome 3's website, and from youtube... But after using it for a few days, It's becoming my favorite DE. As to the issue of resource usage, I haven't had any problems on a P4 with 512MB of ram and integrated graphics.


Edit: As to the clearing of recent docs, and the complete lack of settings, I assume they will come as gnome-shell gets closer to release. If not, I may start to have a problem with it :P.

---

### Post by ibuclaw on 2010-05-21
> **Ozymandias_117 said:**
> From what all I've seen, it seems like Gnome is trying to help Mark Shuttleworth with his goal of making Ubuntu more and more like Mac (Not necessarily a bad thing, or a good thing, it just is :)).

No where near the truth. Gnome is not really helping Canonical at all. More closer to that Canonical tend to develop their new ideas in closed rooms, and open source them on launchpad when a usable base is ready. Once stabilised and a specification is complete, they then push the code upstream into ie: Gnome, FreeDesktop.org, etc. Once there, the code is either accepted or rejected.

---

### Post by gripen on 2011-02-26
Mutter's performance is not that deplorable in my opinion.:)

Nevertheless I feel that the GNOME shell inetrface is terrible and that it actually decreases productivity rather  than increasing it.:confused:

The addition of the activities button increases the number of movements need to switch a window.This increase in the number of movements translates into a increased amount of time waited .Although the time wasted per each switch is very small, when it adds up it leads to a large amount of time being lost.

What would be amazing is for GNOME 3 to have a task-bar/ dock built in ,in-addition to the activities button.This would allow easy switching between windows.Furthermore it would allow the user to keep note on what applications/windows are open.
Neverthless the functionality of the Activities button should be kept as it is for it  will  make a cool addition like some sort " Universal Manager."(like the mac mission control: please don't hate me for this)

:lolflag:

---

### Post by Quadunit404 on 2011-02-26
Old thread is old.

---

### Post by ibuclaw on 2011-02-26
And on that bombshell, I think it's time to close.

Nighty night. :)

---

