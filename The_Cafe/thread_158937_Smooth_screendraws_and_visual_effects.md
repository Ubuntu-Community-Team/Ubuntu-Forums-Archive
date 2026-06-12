---
title: "Smooth screendraws and visual effects"
date: 2006-04-12
forum: The Cafe
---

### Post by 2cute4u on 2006-04-12
Ive been a Mac user since i was 6 and I just tried linux the other day.   My Mac is pretty old (g4 400 mhz sawtooth) but the screendrawing is really smooth with OS X and it has lots of visual effect that I find really help the desktop experience seem more natural.  These windows that collapes rather than just disapear; drop shadows on windows and menus; menus that pull down instead of just apearing, and select on mouse up; etc.

When I tried using KDE  3.2 on a freinds 1.25 ghz PC, it lacked all of these effects and felt clunky and sluggish kind of like windows, and also ended up having slow redraw artifacts and trailers.  I never got to try Gnome so I don't know what it's like.

If I bought a PC and put [k]ubuntu on it, could I get a Mac like smoothness and effect? How do KDE and Gnome compare in these features? What kind of Hardware would I need to get?

---

### Post by Virogenesis on 2006-04-12
accelerated desktops are enabled by using xgl/compiz  which basicaly uses the graphics card like what mac and microsoft doing with vista .
compiz allows the user to have a 3d cude virtual desktop much like the cube on mac os which allows you to switch users.
Compiz also allows for trans effects , wobbly windowss and shadows .
This stuff can't really be enabled in breezy but dapper has support when tweakedd.

---

### Post by woedend on 2006-04-12
if you have a decent video card, I would honestly recommend gnome with xgl/compiz.  You'd love it.

---

### Post by DoubleClicker on 2006-04-12
[QUOTE=Virogenesis]accelerated desktops are enabled by using xgl/compiz  which basicaly uses the graphics card like what mac and microsoft doing with vista .
compiz allows the user to have a 3d cude virtual desktop much like the cube on mac os which allows you to switch users.
Compiz also allows for trans effects , wobbly windowss and shadows .
This stuff can't really be enabled in breezy but dapper has support when tweakedd.[/QUOTE]
So its not part of the default install for dapper? How easy is it for a linux newbie to do?  How does it compare to aqua extreme on a mac?

[QUOTE=woedend]if you have a decent video card, I would honestly recommend gnome with xgl/compiz.  You'd love it.[/QUOTE]
what's a decent video card?  does the CPU matter at all? 
so gnome can do it, but not KDE?

---

### Post by woedend on 2006-04-12
of course cpu matters - to an extent.  You do not need the latest and greatest, but I wouldn't try it on a 100 mhz processor.  I'm not sure actual requirements have been set - thats an interesting question i'd like to gain feedback on actually.  Of course theoretically as long as the video card was supported anything is possible, but i imagine you'd have slow motion/tearing/ugliness.  As far as video goes, from what I understand, nvidia works about the best, ATI seems to work for a lot of people, others have done it with other brands but you'd have to search the forum.  I personally have 128 mb nvidia fx5200 - about 3 years old now...and it does the job just fine.  And yes, you can use xgl/compiz with kde, but I just think it looks better with gnome(its preference though, if you are a kde fan try it out).  As far as a linux newbie doing it...sure...its very very simple(seriously, maybe 3 or 4 steps at the most) and plenty of guides on the board.  search for compiz and watch :)  But I didn't mention, but previous poster did, only for dapper or later.

---

### Post by helpme on 2006-04-12
> **DoubleClicker]So its not part of the default install for dapper? 
[/QUOTE]
No, it's not.
[QUOTE=DoubleClicker]
How easy is it for a linux newbie to do?
[/QUOTE]
Though it isn't really complicated ([XGLHowto]("https://wiki.ubuntu.com/XglHowto")[compizhowto]("https://wiki.ubuntu.com/compiz")) I certainly wouldn't recomend it for a newbie, unless you have a test install on which you can happily play around.
Also, you might want to give Suse Enterprise Desktop a spin when it is released in the summer, as afaik they plan to integrate it.

[QUOTE=DoubleClicker]
How does it compare to aqua extreme on a mac?
[/QUOTE]
Favourably.  said:**
> 
what's a decent video card?

[http://en.opensuse.org/Xgl](http://en.opensuse.org/Xgl)
This should give you an idea.
[QUOTE=DoubleClicker]
does the CPU matter at all? 
[/quote]
At the moment it does matter, as many things that will later be done with the GPU once the drivers are ready are at the moment done in software.
That said, it runs just fine here on a quite dated athlon.
[QUOTE=DoubleClicker]
so gnome can do it, but not KDE?[/QUOTE]
Yes and No. Compiz, which is the window manager + composite manager that will give you all the nice effects can run on both Gnome and KDE. However, the Gnome integration seems to be better at the moment, though I must admit I haven't really tried it on KDE yet.

Finally, if you want some nice effects without all the trouble, KDE and xfce both come with composite manager per default. They will not give you all the effects that something like Quartz extreme will give you, but they will at least give you some effects and smooth redrawings.
All you really have to do is enable the composite extension with something like this in your xorg.conf:
Section "Extensions"
        Option  "Composite" "Enable"
EndSection

---

### Post by MenZa on 2006-04-12
[.](http://www.ubuntuforums.org/showpost.php?p=910759&postcount=191)

---

### Post by 2cute4u on 2006-04-12
> **helpme]No, it's not.

Though it isn't really complicated ([XGLHowto]("https://wiki.ubuntu.com/XglHowto")[compizhowto]("https://wiki.ubuntu.com/compiz")) I certainly wouldn't recomend it for a newbie, unless you have a test install on which you can happily play around.
Also, you might want to give Suse Enterprise Desktop a spin when it is released in the summer, as afaik they plan to integrate it.

Favourably.  said:**
> 

The XGLHowto you gave states:> Just to be clear, there are packages for XGL in Ubuntu Dapper, but they will not be installed by default, are not officially supported and might or might not break your system. In any case there is a lot of work going on on XGL since it is still experimental software, and these packages will definitely be outdated.
Just to be clear, there are packages for XGL in Ubuntu Dapper, but they will not be installed by default, are not officially supported and might or might not break your system. In any case there is a lot of work going on on XGL since it is still experimental software, and these packages will definitely be outdated.   
This doesn't sound like something I would want to use, at least not for dapper maybe in the next relaease it will be better.  


[QUOTE=helpme]Finally, if you want some nice effects without all the trouble, KDE and xfce both come with composite manager per default. They will not give you all the effects that something like Quartz extreme will give you, but they will at least give you some effects and smooth redrawings.
All you really have to do is enable the composite extension with something like this in your xorg.conf:
Section "Extensions"
        Option  "Composite" "Enable"
EndSection
Can you say more about what KDE composite manager will and won't give me, compared to Xgl/Compiz.

---

### Post by helpme on 2006-04-12
[QUOTE=2cute4u]
Can you say more about what KDE composite manager will and won't give me, compared to Xgl/Compiz.[/QUOTE]
Well, first off all, it will make the tearing if you move apps go away.
Second, you'll get nice dropshadows and for example it's possible to make the windows translucent when you move them.

XGL/Compiz offers a lot more then this, like wobbly windows (windows, ehm, wobble when you move them, a 3d cube when you change your virtual desktops, apps actually fade in and out of your mouse cursor when you open and close them, etc.

But if you just want some nice eye-candy without all the trouble, I'd go for the KDE composite manager.

---

### Post by woedend on 2006-04-12
i've not had one crash out of it.  The only bug I can think of at all is that in mplayer when i push the menus at the top become unreadable..odd as it may sound.  But XGL / compiz I don't think will ever be released as 'stable' as it right now seems to be a perpetual work in progress(correct me if i am wrong, please).  But, if you are at all interested, you should check out [http://compiz.ed3n.com/](http://compiz.ed3n.com/), a compiz board, they also keep the xgl and compiz packages up to date(compared to the outdated official ubuntu versions helpme listed).  But, I think its harsh to say XGL/compiz could break your system.  It might not work, and crash for a few people, but its very simple to disable back to normal if you so choose.

---

### Post by Stormy Eyes on 2006-04-12
> **2cute4u]The XGLHowto you gave states:  
This doesn't sound like something I would want to use, at least not for dapper maybe in the next relaease it will be better.  [/quote]

Don't be put off. What they're saying is basically doublespeak that says, "Hey, this stuff works pretty well for us, but we wrote it and we know how it works. We can't and won't guarantee that it will work for you. If you want to use it, fine, but we're not promising anything, so don't come after us with a sledgehammer if Xgl/Compiz breaks your installation or converts your girlfriend to lesbianism."

You *can* use Xgl and Compiz said:**
> Can you say more about what KDE composite manager will and won't give me, compared to Xgl/Compiz.

KDE's composite manager will probably crash more often, be slower, and both move and resize operations will be rougher. However, that's been *my* experience, and I am not overly fond of KDE to begin with. Your experience may be different.

---

### Post by bonzodog on 2006-04-12
If you want translucent menus and drop shadows, and translucent panels, and a mac OS like interface, install xubuntu-desktop, which is the xfce desktop. The composite manager is enabled from Dapper onwards, and it is REALLY cool.
Screenshot here of my desktop:
[http://www.ubuntuforums.org/gallery/showimage.php?i=2040&original=1&c=13](http://www.ubuntuforums.org/gallery/showimage.php?i=2040&original=1&c=13)

Also, this environment is much smaller and less of a drain on limited resources.

---

### Post by poofyhairguy on 2006-04-12
[QUOTE=2cute4u]
Can you say more about what KDE composite manager will and won't give me, compared to Xgl/Compiz.[/QUOTE]

What it will give:

Drop shadows that you can change. Controls over how translucent you want you window borders to be. Better KDE integration. 

What it won't give:

Everything else. Compiz is an Opengl compositor, and it is light years beyond KDE's solution at this point. It gives you an Expose like function, a "minimise trick," window wobbles, cube flips, amazing zooming effects, rain on your desktop (if you setup can take it), live ALT- TAB, and so much more.....

Compiz is the only thing we have even close to OSX. Some people like to tread lightly with it because its new and it requires a bigger commitment, but if you are on the forum asking for eye candy advise then you are ready for XGL/Compiz. Nothing else will satisfy you.

I have written most of the Composite guides. All of them require editing som config file to work. Might as well just go for the gold and try Compiz in Dapper. Everything else (including KDE's Compositor) is SOOOOOOOO 2005.

---

### Post by 2cute4u on 2006-04-14
How well does compiz work in KDE compared to gnome??
In KDE does it support global menues or is that a function of kwin?
Does compiz work with either kwin or metacity themes or do we have to wait for commpiz themes to be created?

---

### Post by woedend on 2006-04-14
the only way it works with themes is loosely color.  Menu color, progress bar, and titlebar color is about it(probably icons too).  Basically most things except the titlebar itself.  This is for gnome, I would assume the same for kde(actually, in gnome changing the theme crashes the theme manager, and doesn't take full effect until you restart gnome).  Since compiz is its own window manager, it would need its own themes, for gnome or for kde.

---

### Post by Virogenesis on 2006-04-14
[QUOTE=2cute4u]How well does compiz work in KDE compared to gnome??
In KDE does it support global menues or is that a function of kwin?
Does compiz work with either kwin or metacity themes or do we have to wait for commpiz themes to be created?[/QUOTE]
Compiz is currently only themable  by hacks   I saw someone do it so   it can be done I won't suggest it  mind you.
A new metacity does exist that supports a bit of eye candy but really I would dn't bother with that due  to compiz being great.
Ps: when i did try ythe new metsacity I wcouldn't gey any of theb  eye candy to work.

---

### Post by mstlyevil on 2006-04-14
[QUOTE=2cute4u]How well does compiz work in KDE compared to gnome??
In KDE does it support global menues or is that a function of kwin?
Does compiz work with either kwin or metacity themes or do we have to wait for commpiz themes to be created?[/QUOTE]

If you have at leat 10 gigs of space on your hard drive, try out Dapper and dual boot. Then install Compiz and see how well it works for you.

You could also try the kororaa live CD without having to install anything. It only works on a win pc but if you have a friend with a pc, maybe they will let you try out the live cd on it. 

[http://kororaa.org/](http://kororaa.org/)

---

