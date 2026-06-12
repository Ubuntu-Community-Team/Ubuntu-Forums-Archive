---
title: "Why I don't use XGL"
date: 2006-06-11
forum: The Cafe
---

### Post by forrestcupp on 2006-06-11
I recently did a clean install of Dapper.  I got everything to work perfectly.  I installed my nVidia drivers, and they worked like a charm.  I got everything set up how I liked it, and I installed Neverball which is an opengl game that my little boy really likes to play.  My next project was to try to get Xgl working.  I had already read all the posts, and I knew it was probably going to be an all day job to get it working.  To my surprise, I got it working perfectly pretty quickly.  I even made a little script to get it to automatically come on when I booted (only after making sure it was going to run right).  It was really cool.  I loved the wobbly windows, the clicking on the screen and dragging the rotating cube around.  It worked just as well as the preview videos, only it looked even more beautiful in real time.  Then I went to play Neverball.  I clicked on the menu entry, and absolutely nothing happened.  This is what they don't tell you.  Full screen opengl games don't work with Xgl.  I know you can set your computer up to run certain apps as non-Xgl, but that is really a pain.  Is the "Eye Candy" really worth it when it renders some parts of your computer totally worthless.  Why do I care about wobbly windows if it means I can't use my computer for everything I could before.  So because I didn't have that much invested into my system yet, I did another clean install to ensure that all the hacking I had to do was completely erased.  Hopefully someday they will get some of these problems fixed.

---

### Post by Stormy Eyes on 2006-06-11
That's a reasonable objection. I had to disable Xgl because it and video players like Xine and Mplayer don't cooperate.

---

### Post by GarethMB on 2006-06-11
I've stopped using XGL because i think it makes my laptop hotter

---

### Post by Nano Geek on 2006-06-11
I have also stoped using Xgl because it made Blender crash.

---

### Post by Anduu on 2006-06-11
[QUOTE=Stormy Eyes]That's a reasonable objection. I had to disable Xgl because it and video players like Xine and Mplayer don't cooperate.[/QUOTE]

Mplayer works fine with XGL for me.Make sure MPlayer isn't tryin to use "gl/gl2" output.I use "xv" and DVD's/wmv etc are smooth as silk.

---

### Post by 23meg on 2006-06-11
> This is what they don't tell you. Full screen opengl games don't work with Xgl. They do tell you; this is well known and stated in many guides and threads. And there are known workarounds too, such as [this one]("http://ubuntuforums.org/showthread.php?t=176636").
> 
Is the "Eye Candy" really worth it when it renders some parts of your computer totally worthless. Why do I care about wobbly windows if it means I can't use my computer for everything I could before.The point and goal of XGL / AIGLX isn't eye candy but GPU based hardware acceleration of X server operations. 

It's well known that XGL / AIGLX / Compiz aren't ready for day to day use in their recent versions, and neither is the lower level infrastructure such as video hardware drivers. And we need to test them to the greatest extent possible to spot and remove bugs, ensure compatibility with all modern video hardware and share the love. 

Here's what I do: I have only the old versions of XGL and Compiz from the Dapper repos installed on my Dapper install, and they seem to be doing fine so far. They're easy to remove because I don't have to add any external repositories and upgrade to newer versions of some libraries from them. I have the latest versions from Quinn's repo on my Edgy testing install and I upgrade them whenever updates arrive. This way I can both have a stable daily working environment and an up-to-date testing environment.

---

### Post by fuscia on 2006-06-11
i've never been all that thrilled with the results (except for one person's screenshot). then, when i looked into using it, the 'bigpainintheass' warning light went off.

---

### Post by Stew2 on 2006-06-11
[QUOTE=fuscia]i've never been all that thrilled with the results (except for one person's screenshot). then, when i looked into using it, the 'bigpainintheass' warning light went off.[/QUOTE]

Hey, I've got that same warning light on my computer... it's just to the left of the "Ihavetoreinstallnow" button. :D

---

### Post by bruce89 on 2006-06-11
I just can't be arsed until it is one checkbox away...

---

### Post by disturbed1 on 2006-06-11
I don't get the whole XGL/AIGL/Compiz thing either. Besides the woble windows and cube, most is already built into Xorg using the composite features. Shadows, translucent, minimize and maximize effects. Use xcompmgr to enable/disable/tune these effects

Here's a pretty good article on X's composite
[http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency](http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency)

---

### Post by forrestcupp on 2006-06-11
> **23meg]They do tell you said:**
> this one[/URL].


I actually tried this workaround to the letter before I ditched Xgl.  For whatever reason it didn't work on my system.  Even if it did work, it is still a pain in the behind compared to just being able to go to Applications/ Games and click on Neverball.  I'm just saying that I hope that sometime these things will be addressed from within Xgl.  I know we need to give it time, but with Windows Vista coming out, I was just hoping we could beat them to the punch.

---

### Post by 23meg on 2006-06-11
[QUOTE=disturbed1]I don't get the whole XGL/AIGL/Compiz thing either. Besides the woble windows and cube, most is already built into Xorg using the composite features. Shadows, translucent, minimize and maximize effects. Use xcompmgr to enable/disable/tune these effects

Here's a pretty good article on X's composite
[http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency](http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency)[/QUOTE]
[http://xgl.freedesktop.org/wiki/Software_2fXgl](http://xgl.freedesktop.org/wiki/Software_2fXgl)

Read the part titled "Technical Features". To repeat, the main point of XGL / AIGLX isn't eye candy but GPU based hardware acceleration of X server operations. OpenGL based eye candy is just one of the things that becomes doable in this new paradigm.

---

### Post by joflow on 2006-06-11
Its the reason why I use linux more then windows now.  And I know if it was easier to install, I could convert atleast 10 people over to linux (atleast until Vista comes out)

---

### Post by disturbed1 on 2006-06-11
[quote=23meg][http://xgl.freedesktop.org/wiki/Software_2fXgl]("http://xgl.freedesktop.org/wiki/Software_2fXgl")

Read the part titled "Technical Features". To repeat, the main point of XGL / AIGLX isn't eye candy but GPU based hardware acceleration of X server operations. OpenGL based eye candy is just one of the things that becomes doable in this new paradigm.[/quote]

Ummmm, what do you think the composite extension in Xorg does?

XGL doesn't add anything new besides eye candy ;)

---

### Post by richbarna on 2006-06-11
I played with it for a while and showed off to my friends with it.
The first problem was it knocked out my Alt buttons, so no more |@#~½¬{[]}\~.
I realised that it was a work in progress, and also the novelty wore off.
I'm back to a basic Dapper Gnome desktop now until I figure out how to get some more RAM and solaris for Sun's Project Looking Glass working.

I didn't know about "xcompmgr" either, have a play with that later ;)

---

### Post by 23meg on 2006-06-11
[QUOTE=disturbed1]Ummmm, what do you think the composite extension in Xorg does?

XGL doesn't add anything new besides eye candy ;)[/QUOTE]
XGL has nothing to do with eye candy; Compiz which runs on top of it does, and other software that can be written can. XGL itself is just a basic X server architecture which layers X over OpenGL.

[http://www.freedesktop.org/wiki/Software/CompositeExt](http://www.freedesktop.org/wiki/Software/CompositeExt)

The composite extension does an entirely different thing and isn't meant to be hardware accelerated.

---

### Post by disturbed1 on 2006-06-11
> **23meg]XGL has nothing to do with eye candy said:**
> http://www.freedesktop.org/wiki/Software/CompositeExt[/URL]

The composite extension does an entirely different thing and isn't meant to be hardware accelerated.

It uses XAA which is 2d accelerated through most cards (Nvidia for one ;) ) using the renderaccel option.

---

### Post by 23meg on 2006-06-11
[QUOTE=disturbed1]It uses XAA which is 2d accelerated through most cards (Nvidia for one ;) ) using the renderaccel option.[/QUOTE]
XAA isn't just used by composite; it's ancient anyway and doesn't bring a performance benefit to modern hardware. It was replaced by EXA in Xorg 6.9, which accelerates the Render extension and has no direct relation with composite. Both are driver-specific and EXA is seen as a transitory technology intended for the period until GL based X becomes standard on modern hardware.

The kind of performance benefit GL based X will bring is light years ahead of XAA/EXA.

---

### Post by disturbed1 on 2006-06-11
[quote=23meg]XAA isn't just used by composite; it's ancient anyway and doesn't bring a performance benefit to modern hardware. It was replaced by EXA in Xorg 6.9, which accelerates the Render extension and has no direct relation with composite. Both are driver-specific and EXA is seen as a transitory technology intended for the period until GL based X becomes standard on modern hardware.

The kind of performance benefit GL based X will bring is light years ahead of XAA/EXA.[/quote] 
Which is also depends on your hardware.

Honestly, besides eye candy, what is the benefit of using XGL?

AIGLX is the new edition that will be part of Xorg 7.1, not XGL.

[http://en.wikipedia.org/wiki/AIGLX](http://en.wikipedia.org/wiki/AIGLX)

---

### Post by ComplexNumber on 2006-06-11
> Full screen opengl games don't work with Xgl. they don't work on AIGXL either.

anyway, i'm not interested in all these silly effects. at first, i was like: "wow!". i uninstalled the damn thing after about a day because they lessen usability, the effects become boring and very annoying after a while, and its a resource hog. so i have to ask myself, where is the benefit?

---

### Post by 23meg on 2006-06-11
[QUOTE=disturbed1]Which is also depends on your hardware.[/QUOTE]What doesn't?
> Honestly, besides eye candy, what is the benefit of using XGL?Back to square one: better utilization of your hardware, faster X operation, when the work is done. To help the work get done, they need to be tested as widely as possible, and the current point of using them is just that: testing. They're not ready for prime time and nowhere has anyone said that they are. Using XGL / AIGLX just to make your otherwise stable work setup sexier isn't a good idea in most cases.
[QUOTE=ComplexNumber]so i have to ask myself, where is the benefit?[/QUOTE]
You shouldn't expect "benefit" in the usual sense from software that's largely incomplete and depends on hardware specifics and proprietary third party components. You should just help test / develop / document it if you're into it.

---

### Post by Jason_25 on 2006-06-11
[QUOTE=forrestcupp]I actually tried this workaround to the letter before I ditched Xgl.  For whatever reason it didn't work on my system.  Even if it did work, it is still a pain in the behind compared to just being able to go to Applications/ Games and click on Neverball.[/QUOTE]
There are many workarounds for running open GL accelerated games while you are using xgl/compiz.  On Nvidia hardware, for months now it has been possible to run indirect accelerated GL games at a good framerate.  Starting a new x server from the console or with xgame-gtk2 is another way to do it.  Therefore your initial point is invalid.  Try again next time.  It's fine if you don't want to take part in the xgl/compiz thing, but don't turn others away because you are ill informed.

[QUOTE=disturbed1]Ummmm, what do you think the composite extension in Xorg does?

XGL doesn't add anything new besides eye candy ;)[/QUOTE]
XGL adds lots of new possibilities.  For me, the greatest thing it adds is desktop acceleration.  Adding a 3d card to a mediocre PC can now greatly improve it's desktop performance.

---

### Post by forrestcupp on 2006-06-11
[QUOTE=Jason_25]There are many workarounds for running open GL accelerated games while you are using xgl/compiz.  On Nvidia hardware, for months now it has been possible to run indirect accelerated GL games at a good framerate.  Starting a new x server from the console or with xgame-gtk2 is another way to do it.  Therefore your initial point is invalid.  Try again next time.  It's fine if you don't want to take part in the xgl/compiz thing, but don't turn others away because you are ill informed.[/QUOTE]

I'm not ill informed.  From my very first post in this thread I said I know about the workarounds.  What I keep saying is, it's a pain to either have to hack these things or to have to restart into a new server just to play a game.  When Xgl is stable and the kinks are worked out, I think it will be a great thing, but for now, I don't need it.  What everyone needs to keep in mind is that it is still in testing stage.  When I'm ready to install it again, though, I think I'll leave out the wobbly windows.  Pretty annoying sometimes.

---

### Post by Jason_25 on 2006-06-11
The games I have played on Linux, on average, require more configuration time than using xgame-gtk2 to a launch a new xserver.  This is maybe not the best solution because it uses more ram, and doesn't seem to work with ATI, but it's easy with an nvidia card and a powerful system.

---

### Post by ComplexNumber on 2006-06-11
[quote=23meg]You shouldn't expect "benefit" in the usual sense from software that's largely incomplete and depends on hardware specifics and proprietary third party components. You should just help test / develop / document it if you're into it.[/quote] so tell me, whats the big difference in terms my own 3 criteria that i've already mentioned inbetween now and when all these silly effects are "complete"?
just to remind you, my 3 criteria are here:
> i uninstalled the damn thing after about a day because **(1) **they lessen usability, **(2)** the effects become boring and very annoying after a while, **(3)** and its a resource hog.

---

### Post by 23meg on 2006-06-11
> **ComplexNumber]so tell me, whats the big difference in terms my own 3 criteria that i've already mentioned inbetween now and when all these silly effects are "complete"?
just to remind you, my 3 criteria are here:[/QUOTE]
I'm not talking about the effects you find silly, that is, Compiz, becoming complete but the whole GL-based X technology, whatever it has branched into and will branch into, becoming complete. 

Compared to the sophistication of Xglx/Xegl or AIGLX, Compiz is a very superficial bit of software, and it may not even find widespread use and be remembered as a technology teaser in the future, since for example Metacity already has its own composite manager, and other projects may come along that can replace it, while borrowing code from it. Many of the freedesktop.org developers feel that it's easier to integrate a compositor into a window manager that's taken years to mature than make an app written from scratch be both a compositor and a window manager, and Compiz is trying to do the latter.

> (1) they lessen usability,This is a Compiz matter, not an XGL/AIGLX one, and a matter of personal preference said:**
> (2) the effects become boring and very annoying after a while,Again Compiz, and personal preference. You can easily make them a lot more subtle with the gset-compiz GUI configuration tool if you find them "too much" by default (like me).

> (3) and its a resource hog.Now *this* is an XGL/AIGLX matter. Right now the majority of the operations are driven by Mesa and are thus powered by your CPU. When things are complete, the part of your GPU that's manufactured to do 3D graphics will do the dirty 2D work of the X server, and as a result you'll have an X that hogs your CPU much less than even today's Xorg, is much more responsive (no window resizing and redrawing delays, just like OSX's Quartz) and is capable of lots of eye candy and GL-based usability improvements. A part of your computer that you've paid for, which sits idle all the time except when you're playing games, will be utilized to accelerate the X server, which in its bare-bones state is horribly slower than the Windows GUI and Quartz.  

What I've been stressing since my first post is that it's *this* part that's the main reason of existence of XGL and related technologies. All the eye candy is just a bonus side effect and Compiz is just the tip of the iceberg.

---

### Post by ComplexNumber on 2006-06-11
> This is a Compiz matter, not an XGL/AIGLX one, and a matter of personal preference you've just said it youself. its a personal preference matter.....nothing more, nothing less. no amount of stability, gee-whizz special effects are ever  going to change that. i was going to go on and further pick out your replies, but i'll just be repeating myself. you haven't changed anything that i've already said because its still as valid.
and no, its not a compix/AIGXL/XGL matter, and never will be.

---

### Post by DigitalDuality on 2006-06-11
d

---

### Post by 23meg on 2006-06-11
I'm not trying to change anyone's mind; I'm just stating the technical facts upon the terms Compiz and XGL being used interchangeably multiple times. As I said, if you're into the idea of having a fast X server that fully utilizes your hardware within a about couple of years,  with the features of Compiz as just the icing on the cake, you can contribute today by testing, reporting bugs, documenting features and placing feature requests. This is where X is heading and that's the whole deal.

---

### Post by mcduck on 2006-06-12
[QUOTE=23meg]I'm not trying to change anyone's mind; I'm just stating the technical facts upon the terms Compiz and XGL being used interchangeably multiple times. As I said, if you're into the idea of having a fast X server that fully utilizes your hardware within a about couple of years,  with the features of Compiz as just the icing on the cake, you can contribute today by testing, reporting bugs, documenting features and placing feature requests. This is where X is heading and that's the whole deal.[/QUOTE]
Exactly.

And if you don't like the effects Compiz provides, just turn them off. You still get hardware accelerated desktop.

Anyway, I must be damn lucky as I don't have any problems with video or 3D games. I'm using lates XGL and Compiz packages from QuinnStorm's repos, and I don't need any tweaks to play Neverball fullscreen.

In the beginning there was some problems, and with XGL/Compiz available in Ubuntu repos there probably still are, but at least for me thay are all gone now :)

Just like DigitalDuality said, I can do anything I did before with XGL/Compiz, and in my opinion many Compiz plugins actually make my computer more usable (not wobbly windows, but with good settings it's not disturbing at all. I rather like it and normal, rigid windows now feel unnatural to me). And in the end, my desktop works is way faster and snappier than with normal X.

---

### Post by Jucato on 2006-06-12
Why does everyone equate XGL with Compiz? Why does everyone think that all XGL is about is wobbly windows and rotating cubes?

XGL is a new X server architecture that runs on top of OpenGL, **X** on Open**GL**. Whereas the old X server architecture does it other way around, running OpenGL on top of X (GLX).
Compiz is just a composite manager, similar to xcompmgr and kompmgr, which takes advantage of this new technology. Compiz is just an example of one of the possibilities of using XGL. it is not the be all and end all of XGL. It just so happens that it is the most famous one since it was released/revealed to the public together.

What are the benefits of a technology such as XGL? Remember Vista? Remember what kind of hardware you need to have for those kind of effects? Now look at what Compiz can do with XGL, on relatively moderate hardware requirements. What this means is that with XGL, you don't really need to have super hardware to get super performance.

But right now, the only thing we have working with XGL is Compiz. But who knows what we can have in the future? XGL is relatively new, so give it a chance to grow.

If it hasn't be said enough times, I'll say it again: XGL is not Compiz.
XGL = X server on OpenGL
Compiz = composite manager (using XGL)
XGL = hardware accelerated graphics
Compiz = wobbly windows and rotating cubes, using hardware accelerated graphics.

---

### Post by forrestcupp on 2006-06-12
[QUOTE=mcduck]

Anyway, I must be damn lucky as I don't have any problems with video or 3D games. I'm using lates XGL and Compiz packages from QuinnStorm's repos, and I don't need any tweaks to play Neverball fullscreen.

[/QUOTE]

Can you explain how to set this up?  Do the threads and howtos on setting up XGL and Compiz work the same with these packages, except for the fact that you download newer packages from somewhere else?  How do I set my computer up to download from QuinnStorm's repos?  If what you say is true, and they have already fixed these issues, then maybe I'd be willing to give it another shot.

---

### Post by 23meg on 2006-06-12
Here's how: pick the appropriate guide for your setup [here]("http://www.compiz.net/viewforum.php?id=5"). This is another common bit misinformation: thinking XGL / Compiz are still at the state they were frozen for Dapper release months ago. They're way ahead of that.

---

### Post by forrestcupp on 2006-06-12
OK 23meg,

I went to the Compiz forums like you said, and did everything it says.  With a little tweaking everything works pretty well.  I can even play Neverball fullscreen without any workarounds.  After some tweaking, the framerate isn't even that bad.  My only complaint is that now I'm missing some textures in Neverball (white patches in places that are supposed to be textured green, and no textures on the coins).  This is messed up now even when compiz is not activated.  I use an nvidia card.  Any ideas?  Other than this, I'm happy with it now.

---

### Post by sharkboy on 2006-06-12
I'm using Xgl+compiz on a debian sid installation for my everyday working use. I don't play much games, but it took me three minutes to adjust a few icon launchers so that they use the existing server on :93.

Anyway, I think that xgl and compiz have a few very pratical uses for my work. Especially the opacity thingy, which allows me to read another text while writing my own, and the sort-all-windows plugin. But the most important gain is that it makes my desktop come alive. I work up to 12 hours a day, mostly with LaTeX, kdvi, emacs, evolution, firefox and tomboy, which on a regular desktop isn't that exiting. But now it is a little bit exiting, and even a pleasure sometimes :). The desktop feels smooth, dynamic and very fast. I've made a few adjustments, most notably lowering the wobbly values, and compiz has kind of blend into the desktop rather than being in my face. I went back to my laptop, which has a regular desktop, this afternoon, and it immediately felt very square and dead. I don't know what is really the definition of eye-candy, but I don't sit and stare at compiz -- I work with it and much better and more comfortably than I ever did without it.

---

### Post by K.Mandla on 2006-06-12
I too have moved away from XGL. I like it, I think it's fun, but I'm trying to rely on secondhand and free computers rather than upscale high-end machines, and what I have will barely run it. So while it's cool, I think I'll wait a while before tinkering with it some more.

---

### Post by 23meg on 2006-06-12
[QUOTE=sharkboy]compiz has kind of blend into the desktop rather than being in my face. [/QUOTE]

[QUOTE=sharkboy]I don't know what is really the definition of eye-candy, but I don't sit and stare at compiz -- I work with it and much better and more comfortably than I ever did without it.[/QUOTE]Well said. Eye candy is actually a bit of an understatement for Compiz at its present state.

[QUOTE=forrestcupp]I went to the Compiz forums like you said, and did everything it says. With a little tweaking everything works pretty well. I can even play Neverball fullscreen without any workarounds. After some tweaking, the framerate isn't even that bad. My only complaint is that now I'm missing some textures in Neverball (white patches in places that are supposed to be textured green, and no textures on the coins). This is messed up now even when compiz is not activated. I use an nvidia card. Any ideas? Other than this, I'm happy with it now.[/QUOTE]I'm afraid I can't help you, but it's expectable. You'll probably find others with similar experiences and maybe workarounds if you ask at the Compiz forums.

Be advised though that what you have right now is very close to the latest state of Compiz and it may make your environment unstable. My advice: for long term use turn off the water, neg, dock and miniwin plugins to improve stability.

---

### Post by Puffball on 2006-06-13
I too have problems using OpenGL applications with XGL turned on, but adding an item that uses the command "metacity --replace" turns it off quickly, and then GL applications work. To turn XGL back on, I just add another item to the GNOME panel which points to my compiz startup script.

It being as easy as clicking makes it much easier and more practical, I think. Also not a bad idea, if you couldn't care about gl applications, to use this incase compiz crashes. The only problem with starting any GL application with it turn on, however, is it actually restarts my computer, rather than exiting with an error.

---

### Post by forrestcupp on 2006-06-13
[QUOTE=Puffball]I too have problems using OpenGL applications with XGL turned on, but adding an item that uses the command "metacity --replace" turns it off quickly, and then GL applications work. To turn XGL back on, I just add another item to the GNOME panel which points to my compiz startup script.
[/QUOTE]

This is very informative and useful, but it didn't solve my texture problem.  I have this problem now whether compiz is enabled or not.

---

### Post by forrestcupp on 2006-06-13
I finally found out that even though compiz is not enabled, my computer still boots to xgl, which is where the problem is with my textures.  So I edited /etc/gdm/gdm.conf-custom and under the [servers] section I added 1=Standard.  Now I can just hit ctrl-alt-F7 and ctrl-alt-F8 to switch between an xgl server and a standard xorg server for my games.  Sometimes I have to use F9 instead of F7.  It's easy to do, and it works great.  No more complaints

---

### Post by Jason_25 on 2006-06-13
Here's Open GL on top of xgl/compiz.  This is on a very run of the mill pc with only a pci graphics card.

---

