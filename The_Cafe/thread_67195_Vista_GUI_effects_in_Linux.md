---
title: "Vista GUI effects in Linux"
date: 2005-09-19
forum: The Cafe
---

### Post by kcy29581 on 2005-09-19
Hi all,

How can you get the GUI effects in the Vista Builds like transparancy, transluency, fading effects when maximising/minimising windows, etc in Linux?

Bear in mind I obviously use Gnome. I believe most effects work in KDE, but I'm not sure. However I would prefer stuff like that in Gnome. If they are available options already please direct me.

Any help with this or advise would be great.

Flamers please shut it...

---

### Post by Kyral on 2005-09-19
XCompmgr and Transset are available, but they are very buggy

As for the eyecandy.. would I *like *it? Yes. Do I *need* it? Nope. I have my desktop laid out very well. If I need so see something (like an IM Window) I either have an audio cue that fires off to get my attention, a visual cue (like the gaim-guifications), or both. But maybe I'm just getting old (HOLY COW! I'm saying that and I'm only 19!)

---

### Post by poofyhairguy on 2005-09-19
[QUOTE=kcy29581]Hi all,

How can you get the GUI effects in the Vista Builds like transparancy, transluency, fading effects when maximising/minimising windows, etc in Linux?
[/QUOTE]

You use xcompmgr. It really only works with an modern Nvidia card (I have bought two for this reason) and it has problems. I can tell you from using it everyday that when you use xcompmgr with its effects turned on (fading and or drop shadows) you have to live with the fact that the xserver will sometimes crash (I get around this by having the "session saver" extension in Firefox and by typing everything important in OO.org2 so it can be recovered). Also you can use a script found in the xcompmgr thread to turn on and off the effect- I turn it off when I'm doing stuff on my computer that I CAN'T have crash.

[http://ubuntuforums.org/showthread.php?t=20769](http://ubuntuforums.org/showthread.php?t=20769)

Unfortunately xcompmgr hasn't been worked on since 2004. KDE has it own compmgr that I hear will work great in KDE 3.5, but Gnome plans include nothing like that- Gnome's plan so far is to just make things work with xcompmgr.

Basically if you want those effects now and you want them stable too you can't have that. If you can live with crashing then you can have it now (I'm using it right now). If you just want and accerated desktop (no tricks like fading) and you don't want crashes you can have that now:

[http://slashdot.org/comments.pl?sid=161495&threshold=0&commentsort=0&tid=131&mode=thread&cid=13506790](http://slashdot.org/comments.pl?sid=161495&threshold=0&commentsort=0&tid=131&mode=thread&cid=13506790)

When KDE 3.5 comes out I plan to switch just for the better compmgr. Gnome cares usuability more than eye candy so if you are a big Gnomer but you like those effects you might want to start trying to like KDE. (the other problem is that Gnome doesn't want to make a working compmgr when now you must have a very certain card (nvidia) and that card's non OSS drivers to get it all to work. If you study the history of Gnome, you find that to the developers being free counts more than anything else).

So, yes you can have it now. But just like Vista now you must have the correct video card for it to be accerated (I think Vista needs a ATI 9800, Xcompmgr needs Nvidia) and just like Vista is buggy and crashy.

If you need more information PM me....I love eye candy so I might know more about stupid xcompmgr than any person should.

---

### Post by angkor on 2005-09-19
[QUOTE=kcy29581]Hi all,
GUI effects in the Vista Builds like transparancy, transluency, fading effects when maximising/minimising windows, etc in Linux?
[/QUOTE]

These effects are already available in Linux and OSX.  Xcompmgr was quite stable on my system as long as I didn't use the dropshadow stuff. But yes, it's all a bit too new to be entirely stable.

---

### Post by poofyhairguy on 2005-09-19
[QUOTE=Kyral]XCompmgr and Transset are available, but they are very buggy[/QUOTE]

Buggy by Unix standards. Stable by Windows ME standards.

> 
As for the eyecandy.. would I *like *it? Yes. Do I *need* it? Nope. I have my desktop laid out very well. 

Its about more than eye candy. Xcompmgr and Vista's Aero (I think that is what its called) make it so that your GPU draws your screen. When I run xcompmgr I can move my windows around without any "ghosting" - even when my CPU is at 100%. Why? Because my Nvidia 6600 GT is doing the work. These two tools make your whole desktop seem faster.

Now that I have used a desktop with acceration, I can't go back.

---

### Post by poofyhairguy on 2005-09-19
[QUOTE=angkor]These effects are already available in Linux and OSX.  Xcompmgr was quite stable on my system as long as I didn't use the dropshadow stuff. But yes, it's all a bit too new to be entirely stable.[/QUOTE]

I will say, out of xcompmgr's three effects (fading, drop shadows, and transparancy) the drop shadows are by FAR the buggiest. I never use them. I just use fading.

---

### Post by Lovechild on 2005-09-19
[QUOTE=poofyhairguy]Buggy by Unix standards. Stable by Windows ME standards.



Its about more than eye candy. Xcompmgr and Vista's Aero (I think that is what its called) make it so that your GPU draws your screen. When I run xcompmgr I can move my windows around without any "ghosting" - even when my CPU is at 100%. Why? Because my Nvidia 6600 GT is doing the work. These two tools make your whole desktop seem faster.

Now that I have used a desktop with acceration, I can't go back.[/QUOTE]

Actually that would be largely due to XDamage, X is now only redrawing the damaged parts of the screen - it's a composite feature.

As for acceleration, EXA is being worked on for R300 and the nv driver so we don't need that fault driver that messes everything up with it's brokeness.

---

### Post by poofyhairguy on 2005-09-19
[QUOTE=Lovechild]Actually that would be largely due to XDamage, X is now only redrawing the damaged parts of the screen - it's a composite feature.[/QUOTE]

Good point. 

> 
As for acceleration, EXA is being worked on for R300 and the nv driver so we don't need that fault driver that messes everything up with it's brokeness.

I can't wait for that whole new framework and KDE 4.0. EXA is proof that KDE won't let Vista win at Eye Candy.

---

### Post by poofyhairguy on 2005-09-19
Good article I don't agree with but explains the future kinda:

[http://www.freedesktop.org/~jonsmirl/graphics.html](http://www.freedesktop.org/~jonsmirl/graphics.html)

---

### Post by drizek on 2005-09-19
i dont understand why suse/red hat/mandriva dont hire people to work on xgl.

---

### Post by pmj on 2005-09-19
As others have said, xcompmgr can give you a few nice effects. However, it's extremely buggy. Since poofyhairguy didn't mention any other problems than stability, I'll just go ahead and mention a few more.

If you have an Nvidia card, you will need to use the right driver or else things will be very unstable. Sometimes xcompmgr just closes itself for no obvious reason. Effects like fading and especially shadows are sometimes buggy. Transparency on windows will cause artifacts on rounded corners. It's very difficult to make certain applications always start as transparent. It has memory leaks. Sometimes it makes Xorg use a lot more CPU than it should. While some problems can be fixed by restarting xcompmgr,  doing so might cause all sorts of weird problems with other applications.

So yeah, you can try xcompmgr, but prepare for a struggle. And you just have to accept that it won't be anywhere near Vista in quality.

---

### Post by Knome_fan on 2005-09-19
[QUOTE=poofyhairguy]Good article I don't agree with but explains the future kinda:

[http://www.freedesktop.org/~jonsmirl/graphics.html](http://www.freedesktop.org/~jonsmirl/graphics.html)[/QUOTE]

It's amazing that you don't agree with the article, as you obviously didn't even understand it:

> Its about more than eye candy. Xcompmgr and Vista's Aero (I think that is what its called) make it so that your GPU draws your screen. When I run xcompmgr I can move my windows around without any "ghosting" - even when my CPU is at 100%. Why? Because my Nvidia 6600 GT is doing the work. These two tools make your whole desktop seem faster. 

xcompgr != Aero
xcompgr != gpu drawing your screen

---

### Post by GeneralZod on 2005-09-19
[QUOTE=drizek]i dont understand why suse/red hat/mandriva dont hire people to work on xgl.[/QUOTE]

Novell already employ David Reveman who is really the father of xgl.  It's a crying shame that no one picked up Jon Smirl, though - wish I had loads of money, then I'd hire him on.  Oh well :)

---

### Post by Knome_fan on 2005-09-19
The good news is that trolltech and Zack Rusin seem to really put a lot of work into xgl.
[http://users.ox.ac.uk/~chri1802/kde/zrusin-X-future.html](http://users.ox.ac.uk/~chri1802/kde/zrusin-X-future.html)

---

### Post by Kyral on 2005-09-19
Hmm, KDE 3.5 to have a good compmgr. Hmm

Right now the only reason I use GNOME is because I know how to work it...when is KDE 3.5 supposed to come out? :P

---

### Post by GeneralZod on 2005-09-19
[QUOTE=Knome_fan]The good news is that trolltech and Zack Rusin seem to really put a lot of work into xgl.
[http://users.ox.ac.uk/~chri1802/kde/zrusin-X-future.html](http://users.ox.ac.uk/~chri1802/kde/zrusin-X-future.html)[/QUOTE]

Pretty much every project I'm interested in - from X eye-candy, to the KDE-ification of Firefox - Zack's name always seems to pop up.  The guy must be inhumanly talented.

---

### Post by kcy29581 on 2005-09-19
thanks for the replies guys, lots to read up on!

got to find out how to enable all this stuff in ubuntu now. I think I'm gonna install a second Ubuntu which I'll use as my "minefield" for beta software!O:)

---

### Post by Lovechild on 2005-09-19
[QUOTE=poofyhairguy]
I can't wait for that whole new framework and KDE 4.0. EXA is proof that KDE won't let Vista win at Eye Candy.[/QUOTE]

Why do you equate EXA with KDE, it's an X framework, and once in place it will allow everyone to accelerate eye candy effects - my point was that the instability of the x tools most likely are caused by the nvidia module, not the tools themselves or GNOME.

You shouldn't abandon GNOME because of a misconception. GNOME will provide you with eyecandy, the coming releases are already set to add eyecandy as features are moved from the development project into metacity and gtk-cairo engines is appear to render your widgets.

If you feel KDE is a better project then fine, but don't blame GNOME for stuff like the utter brokenness of the nvidia module.

---

### Post by poofyhairguy on 2005-09-19
[QUOTE=Lovechild]Why do you equate EXA with KDE, it's an X framework, and once in place it will allow everyone to accelerate eye candy effects[/QUOTE]

Because I personally believe that KDE will use it best first. Thats just my opinion though.

> 
 - my point was that the instability of the x tools most likely are caused by the nvidia module, not the tools themselves or GNOME.

When its just using the CPU for xcompmgr is does crash less so you could be correct.

> 
You shouldn't abandon GNOME because of a misconception. GNOME will provide you with eyecandy, the coming releases are already set to add eyecandy as features are moved from the development project into metacity and gtk-cairo engines is appear to render your widgets.

Its just my personal opinion that the Gnome eye candy framework (say Luminocity and Cairo) is behind KDE's framework in the "wow" areas. KDE 3.5 will have a more stable (therefore usable) compmgr built into its window manager, while currently Luminocity is even called by its creator a "toy." Even XFCE now has a decent compmgr built into its window manager. The proposed eye candy future for KDE is much clearer the Gnome's. Most say KDE 4 will be out next year, but for the life of me I can't find where Gnome developers say "this release we are hoping to incorporate the luminocity stuff." Could just be that my Google skills are weak.

> 
If you feel KDE is a better project then fine, but don't blame GNOME for stuff like the utter brokenness of the nvidia module.

I don't. In fact I like the fact that Gnome has just worked to be better with xcompmgr turned on. Since no compmgr is stable enough to leave it on all the time, I prefer Gnome+Xcompmgr because I can turn it off at any time. 

The problem (for me) is that I don't see the Gnome goals for eye candy as clearly. I haven't seen as much press on Gnome 3 (or whatever release finally gets some lunimocity love) compared to KDE 4. Now, that my be just my perception (I'd prefer if I was wrong).

Finally, the original poster asked for "Vista like" eye candy. Only KDE is working on effects that are like Vista's effects. I can't say if that good or bad (after playing with both I prefer fading to wobbly windows), but it does seem to be the case.

---

### Post by poofyhairguy on 2005-09-19
[QUOTE=Knome_fan]
xcompgr != Aero
xcompgr != gpu drawing your screen[/QUOTE]

Good point. I must admit that I wish I knew more about Aero. Does anyone have a good article explaining the Vista graphics framework?

---

### Post by drizek on 2005-09-19
read the longhorn/vista reviews on winsupersite.com if you wanna learn all about it.

its not too complicted though.  Before, they had a thing called DCE(Desktop composting engine) which does the xcomp stuff but then they renamed it to DWM, not sure what it stands for. aero is basically just a visual style, much like luna is to xp. avalon is the "presentation engine" which i think is the equivelant of QT/GTK, but im not really sure about taht one so dont quote me on it ;). thats pretty much it.

Edit: KDE 3.5 is coming out some time in october or maybe even early november. not too far off O:) there is a klax livecd with a previous alpha version of it if you want to try it out.

as for the "vista-like" effects. well, neither kde or vista are going to have them. they will both use fading rather than wobbly windows. i was listening to an interview with asiego yesterday and when he was asked about wobbly windows he just said "whats the point?".

---

### Post by kcy29581 on 2005-09-20
about the "why do people want eye-candy, it wastes resources etc...":

Eye-candy on-screen is a nice effect, that **for me personally**, makes my PC feel more "futuristic"! I did name my PC Shadow after all. :wink:

I once had a very similar discussion at work today. I have recently ordered motion detection gloves to play Black & White (1 and 2), and many people say that was just pointless, mouse and keyboards will always be more functional.
About that, I'd say there are a few people out there (myself included) that actually work better when flashy things are plugged in the PC, or when it makes "pretty colours"; I'd say that it makes you feel happier (I know there's a better word...)

@poofyhairguy: I agree with you about Gnome and KDE's future in eye-candy. I can't find a concrete quote from any Gnome developer that they are commited to bringing nice effects in Gnome, as KDE is doing. It is annoying as I left KDE because of the K-this and K-that, and all those bloody icons for EVERYTHING!
Gnome may feel superior for work **now**, but the tables might turn if KDE presents a nice, working and flashy desktop

---

### Post by getaceres on 2005-09-20
[QUOTE=poofyhairguy]Good point. I must admit that I wish I knew more about Aero. Does anyone have a good article explaining the Vista graphics framework?[/QUOTE]
 Just as I see:

Windows: Avalon
Mac OS: Quartz
KDE4: Arthur (from QT)
GNOME: Cairo

Windows: Aero
Mac OS: Aqua
KDE4: Oxygen
GNOME: Clearlooks-Cairo?

---

### Post by poofyhairguy on 2005-09-20
[QUOTE=getaceres]Just as I see:

Windows: Avalon
Mac OS: Quartz
KDE4: Arthur (from QT)
GNOME: Cairo

Windows: Aero
Mac OS: Aqua
KDE4: Oxygen
GNOME: Clearlooks-Cairo?[/QUOTE]

Thank You.

---

### Post by poofyhairguy on 2005-09-20
Aero info:

[http://channel9.msdn.com/Showpost.aspx?postid=114694](http://channel9.msdn.com/Showpost.aspx?postid=114694)

---

### Post by drizek on 2005-09-20
If the k this and k that are the only things keeping you away from kde, then you will be pleased to know that it is being changed.

notice that how plasma, tenor and oxygen dont have k's?

oh and,

Desktop Search:

Windows: WinFS
Mac OS: Spotlight
KDE4: Tenor
GNOME: Beagle

Icons and Wallpapers:

Windows: High-res bitmaps
OSX: High-res bitmaps
KDE4:SVG
Gnome: SVG

Desktop Widgets:

Windows: Sidebar
OSX: Dashboard
KDE4: Plasma
Gnome: None(gdesklets optional)

3D Desktop Acceleration:

Windows: direct3D
OSX: OpenGL
KDE: OpenGL
Gnome: OpenGL

who doesnt fit in?

anyone have any more?

---

### Post by poofyhairguy on 2005-09-21
[QUOTE=drizek]

anyone have any more?[/QUOTE]

(best) Task Switcher:

Vista: Better Alt-Tab
OSX: Expose
KDE: Kompose
Gnome: Skippy?

---

### Post by jzke on 2005-09-23
[QUOTE=poofyhairguy](best) Task Switcher:

Vista: Better Alt-Tab
OSX: Expose
KDE: Kompose
Gnome: Skippy?[/QUOTE]
The better Alt-Tab in Windows Vista has been named 'Flip', and the 3d version is known as Flip 3d...

Also, I believe icons in the final Vista will be (if all goes to plan) in SVG format.

---

