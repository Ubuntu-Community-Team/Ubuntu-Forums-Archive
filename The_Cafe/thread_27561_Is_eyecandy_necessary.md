---
title: "Is eyecandy necessary?"
date: 2005-04-16
forum: The Cafe
---

### Post by RastaMahata on 2005-04-16
First of all, please forgive my english. I may sound a bit weird, but that's only because I'm from Chile :P

Anyway, I just wanted to start a discussion on this topic. I have always thought that eyecandy always attracts users from other places, saying things like "woah, your desktop looks cool. What are you using?". Then again, the answer is mostly:

"I use a Mac".

Sadly enough, users dont say linux (unless the hack the system somehow, or install some other programs not coming by default with the distro). Leave the option of saying windows last, as windows users may get a pretty desktop, but having to install 20 programs appart running in the tray, eating resources.

The best thing about eyecandy on the mac, is that it uses very few resources. Being based on OpenGL, and using pdf technology, its damn fast to render movements and effects. The Aqua theme looks so good that there are ports for gnome and windows xp. It's such a good system, everybody goes there sometimes for inspiration (well, some people..).

The thing about these effects being used is that they dont slow the system so much. With each MacOS X release, believe it or not, the system gets a speed boost, whatever components you are using. Tiger is faster than panther, no matter if you are running a G4 or a G5. You cant say the same about new windows versions, as each new release needs a totally new computer (Well, except the case of windows 95 - 98).

Being the macs the systems setting the standard as far as eyecandy goes (I wont argue other things, as I don't know that much about mac/win/linux specs), and not slowing down the system as each release goes by, Linux graphic enviroment developers should look at this and say "We're doing something wrong".

Yeah, sure, I've read in some gnome blogs that some progress has been done, that OpenGL has been tested, that a new X server is underway, that the enlightment project looks good, etc, etc. But right now, people have in their minds "Linux looks ugly". If people think the system looks ugly, they think the system wont work as they  think. Gnome has done a great job at getting their system look nice, but thats not enough. I think (personal thought) that a good system should look nice and work fast if its meant to be used as a desktop system.

Wobbling windows, fading effects, cool looking shadows, smoke effects, cartoon effects, you name it. Animation always attracts people. Booms and flashes too. If you dont believe me, look the latest "top console games" and tell me if they dont have nice looking effects. This is because gamers are simple. If the game is good, they'll play it. Now, 1337 g4m3rs have the latest and most expensive card in the market and bla bla bla. And you know they'll buy the best looking game in the market, no matter if Unreal 1 is better at gameplay. This is a sign (I think) that users tend to confuse looks with quality.

Most linux users are hardcore fans of the system. Hell, I know a lot using blackbox or others that use less resources, and with a bit of hacking and configuration and RTFM, they get a pretty cool looking system. But mere mortal newbies just want a good looking system out of the box. So they can say "Hey, my windows look better than yours", and get the "Oh! And what OS are you using?" question.

And it is my dream to hear "I'm using linux, and it was easy as installing it".

I don't know what you think about this, but for a start, Dont you think that this should have a bigger priority than other things for the system to be more accepted in the market?

Please, dont flame me, nor my grammar :(

---

### Post by Stormy Eyes on 2005-04-16
I say, "Be patient." With X.org's X11 improving, and the development of E17 and the Cairo libs for GTK, GUI development on Linux is proceeding slowly, but surely. And, speaking as somebody who's used Linux since 1999, I'll tell you this: Linux GUIs have come a hell of a long way.

If you don't believe me, try spending a day with TWM as your window manger. :)

---

### Post by RastaMahata on 2005-04-16
yeah, but each time, they require more resources :( (or at least that has been my experience)

---

### Post by Stormy Eyes on 2005-04-16
[QUOTE=RastaMahata]yeah, but each time, they require more resources :( (or at least that has been my experience)[/QUOTE]

Cairo is supposed to be less resource intensive. [Read this.](http://www.gnome.org/~seth/)

---

### Post by nautilus on 2005-04-16
X.org and the extensions are just beating a dead horse, using 2d acceleration to achieve what should be with slightly more serious methods; opengl.

Metisse is a virtual X server which runs atop normal X, and provides a display which renders everything using OpenGL.  the result is the window transformations are spectacular!

iconifying a window can spin it backwards to the root window, while lowering the opacity (making it transparent).  this isn't some a/eterm transparency hack, it's *real*.  you can watch your .avi move playing right through your web browser by turning transparency on.

it's a neat idea, but suffers many caveats, most of which are due to the lacking support for the initiative.

as for cairo, i haven't seen anything actually come from that project in years, it concerns me to put weight on a project without much to show for itself.

---

### Post by benplaut on 2005-04-16
<rant> IMO, the big move that needs to be made is _away from raster_. For photographs, there is nothing like a raster. They can accurately render texture better than anything out there. For everything else, however, vector graphics can be implimented without any visible change to the user, other than the fact that graduals are more gradual, and pixilation will not occur (even on high-res moniters). For the time being, this is a far away goal. For both KDE and GNOME, vector based is a longterm goal. 

For the time being, the optimum way to go seems to be .PNG format, in which gradual transparencies are possible without removing a precise number of pixels to clear, as is the case with a GIF image.

I am a fan of eye candy, but, I think that high performance and sharp images are a higher priority than cute animations and "usefull" popup boxes that tell you what you [should] already know. </rant>

:)

---

### Post by kiddo on 2005-04-16
> For the time being, the optimum way to go seems to be .PNG format, in which gradual transparencies are possible without removing a precise number of pixels to clear, as is the case with a GIF image. What do you mean, PNG? Did you ever play with inkscape (or open a .svg gnome icon with it for example)? This is simply amazing. I haven't seen anything PNG can do that SVG can't. And it's vector (so you can stretch it as you wish), open, and most of time, lighter in filesize. (Note: this isn't some kind of "did you ever" in a harsh way, it's actually in a question way.. Hmm, I don't understand my own words.. whatever) :)

I'm really really looking forward OpenGL on the desktop. Or video cards that cooperate fully with Xorg. No glitches or smudges or anything. *drools* Any.. predictions when this kind of technology could come around? I mean, I do hope it's not going to take 6 years (longhorn release cycle ;)) to implement somehow... I might die being run over by a [reindeer]("http://www.smokinmka.com/xmas/FUNNY%20Christmas%20-%20Grandma%20Got%20Run%20Over%20By%20A%20Reindeer.mp3") by then!

---

### Post by ubuntu_demon on 2005-04-17
cairo looks promising ... I really like the video's at [http://www.gnome.org/~seth](http://www.gnome.org/~seth)

Does anybody have an idea about what timescale we are talking about ?

---

### Post by baza41 on 2005-04-17
Macs do look good, on screen and off. 

Some eye candy for Linux, while not making it 'work' any better, would help sell it. People are used to the way windows looks, and Linux looks don't compare at the moment. Nicer icons would help,

Baza

---

### Post by benplaut on 2005-04-17
> **kiddo]What do you mean, PNG? Did you ever play with inkscape (or open a .svg gnome icon with it for example)? This is simply amazing. I haven't seen anything PNG can do that SVG can't. And it's vector (so you can stretch it as you wish), open, and most of time, lighter in filesize. (Note: this isn't some kind of "did you ever" in a harsh way, it's actually in a question way.. Hmm, I don't understand my own words.. whatever) :)

I'm really really looking forward OpenGL on the desktop. Or video cards that cooperate fully with Xorg. No glitches or smudges or anything. *drools* Any.. predictions when this kind of technology could come around? I mean, I do hope it's not going to take 6 years (longhorn release cycle  said:**
> reindeer[/url] by then!

That's what i was saying :roll:... except, currently, AFAIK, the technology to put vectors into the everyday desktop environment in extremely limited ](*,). And yes, there is something a .PNG can do that a .SVG can't. It can be viewed in most browsers (except in IE, correctly).
:)

And yes, i have used vectors before... i use them almost daily in my uber-minimal money making :-\"

---

### Post by poofyhairguy on 2005-04-17
Unfortunately it will be a while before this is across all Linux desktops. The main thing MacOSX has that Linux doesn't is consistant hardware and good video drivers. For OSX eyecandy, only those with newer NVIDIA cards (that can get them to work) will be allowed. Too small of a part of the Linux population to move to fast. Now maybe if ATI and other video card companies will support Linux like OSX, then all can have this candy. Till then, the few with Nvidia cards can do it and OSX still wins the eyecandy war.

---

### Post by TravisNewman on 2005-04-17
Chiming in with a simple answer:
No. It's not necessary.

It's nice for some, but it can impair things as well. OSX would be MUCH nicer if it toned down the eye candy-- there are a lot of people doing intense things on OSX, and they'd appreciate the processor cycles.

Eyecandy is nice, but it shouldn't be default-- if it's a matter of winning Windows users with eye candy, vs creating a better product and keeping the current userbase, I choose the better product.

---

### Post by ubuntu_demon on 2005-04-17
I think it's necessary to have the eyecandy. It's necessary to compete with OS X and avalon. But it's also necessary to be able to turn it off.

---

### Post by TravisNewman on 2005-04-17
Well, I don't care about competing, so that's where I'm coming from ;)

If it's eyecandy that performs a handy function, then fantastic, but if it's JUST eyecandy, not by default, IMO.

---

### Post by HungSquirrel on 2005-04-17
> I'm from Chile
Bienvenidos.

---

### Post by ubuntu_demon on 2005-04-17
[QUOTE=panickedthumb]Well, I don't care about competing, so that's where I'm coming from ;)

If it's eyecandy that performs a handy function, then fantastic, but if it's JUST eyecandy, not by default, IMO.[/QUOTE]
 regarding practical side of cairo :

-hardware rendering instead of software rendering for the eye-candy. So it shouldn't cost much cpu power

-if you have a big screen your icons and fonts do still look good

---

### Post by Brunellus on 2005-04-17
Eyecandy's ok, if you can afford it.  I don't have gobs and gobs of RAM, so I try to minimize my eyecandy...so much so that I've gone to fluxbox instead of gnome, because fluxbox lets me have enough useful eyecandy without slowing me down overmuch.

One of my windows-using friends always comments on how cool my desktop (even the fluxbox one) looks, but he says "yeah, but you had to tweak and fiddle with it to get it that cool.  Mine isn't as cool, but I didn' t have to put in any work."

He has a point.  Those who are advocating an opt-in eyecandy strategy are going to alienate some users who'll just run to the more accomodating arms of microsoft.  (I'm going to ignore apple here, because their hardware is just too damn expensive.  period).

As someone else already said:  OSX can have nifty eyecandy because they don't have to support a lot of hardware requirements, especially with regard to graphics cards.  A Macolyte friend of mine says as much:  he's happy paying extra for Apple hardware because he knows it will work with Apple software.  (lock-in, much?)

It's also worth noting that malware of all stripes proliferates readily when packaged in/as eyecandy for the windows desktop--so people *want* eyecandy to amuse and entertain them, and seldom think about the security implications.  I hate watching my mother's face fall when I tell her *never* to open any forwarded attachments from her friends, because I'm sick of having to clean up after th spyware/adware.  (and no, she won't go Linux, because the whole thing intimidates her too much.  I'll try with a spare laptop soon, though)

---

### Post by ubuntu_demon on 2005-04-17
[QUOTE=Brunellus]Eyecandy's ok, if you can afford it.  I don't have gobs and gobs of RAM, so I try to minimize my eyecandy...so much so that I've gone to fluxbox instead of gnome, because fluxbox lets me have enough useful eyecandy without slowing me down overmuch.

One of my windows-using friends always comments on how cool my desktop (even the fluxbox one) looks, but he says "yeah, but you had to tweak and fiddle with it to get it that cool.  Mine isn't as cool, but I didn' t have to put in any work."

He has a point.  Those who are advocating an opt-in eyecandy strategy are going to alienate some users who'll just run to the more accomodating arms of microsoft.  (I'm going to ignore apple here, because their hardware is just too damn expensive.  period).

As someone else already said:  OSX can have nifty eyecandy because they don't have to support a lot of hardware requirements, especially with regard to graphics cards.  A Macolyte friend of mine says as much:  he's happy paying extra for Apple hardware because he knows it will work with Apple software.  (lock-in, much?)

It's also worth noting that malware of all stripes proliferates readily when packaged in/as eyecandy for the windows desktop--so people *want* eyecandy to amuse and entertain them, and seldom think about the security implications.  I hate watching my mother's face fall when I tell her *never* to open any forwarded attachments from her friends, because I'm sick of having to clean up after th spyware/adware.  (and no, she won't go Linux, because the whole thing intimidates her too much.  I'll try with a spare laptop soon, though)[/QUOTE]
 true!
gnome+cairo+nice and functonal eyecandy should be default.

---

### Post by somuchfortheafter on 2005-04-17
[QUOTE=demon666_nl]true!
gnome+cairo+nice and functonal eyecandy should be default.[/QUOTE]
 yea well i have 512mb of ram on all my systems but my oldest pc with a 128 on it, so on the old i do not run the eyecandy but on others i load it full of all the eyecandy that i can, well because it looks cool to me lol. so linux just needs to be easily flexable, so i dont have to lets say compile gkdesklets from scratch and install 50 devs to get it to work out of the box.

---

### Post by TravisNewman on 2005-04-17
Yes, I agree with that. :)

---

### Post by nautilus on 2005-04-17
Yep, I turn my eyecandy to the max.  It makes working on the computer feel nicer.  Fung Shooey for my desktop.  I also like to impress people with my elegant and futuristic desktop.  I don't care if they're almost useless, as long as they're not impractical.  Useful is a bonus yeah, but for instance, the new tooltip swiss-cheese fader in KDE 3.4 is completely useless, but still cool.  Or the semi-transparency feature on the amaroK OSD.  It's fine, because it's not really expensive at all, all things considered.  (That, and they only use resources momentarily)

---

### Post by Stormy Eyes on 2005-04-17
[QUOTE=Brunellus]Those who are advocating an opt-in eyecandy strategy are going to alienate some users who'll just run to the more accomodating arms of microsoft.[/QUOTE]

Let them run, then. I don't agree with the emphasis on eye candy. Yes, it's nice and it's fun, but it's not the meat 'n potatoes of computing. Focusing on eye candy at the expense of a rock-solid OS and rock-solid applications is counter-productive. I think the appropriate order of priorities is this:

1. Make it reliable.
2. Make it fast.
3. Make it attractive.

---

### Post by TravisNewman on 2005-04-17
well, I'd put #1 as "Make it functional"

Not trying to be sarcastic here, but you could make a reliable, fast, and attractive maze game for an OS, but that doesn't do any good. Functionality is the most important thing.

The only way eye candy should be default is if its functional and doesn't take away from reliability, and doesn't take TOO much away from speed.

But yes, I agree Stormy-- let them run.

---

### Post by Brunellus on 2005-04-17
I'm not advocating eyecandy at the expense of stability or useability.  I do however appreciate that eyecandy is a good way to get people in the door.  While their eyes are bugged-out and they're drooling over the neatness of your desktop, you can explain to them the technical superiority of your platform.  Hey, it works for Apple.

Positive:  at least Ubuntu and Linux in general gives me the choice.  I can turn stuff on or off pretty much at will, and end up with the desktop that both looks decent and runs well.

---

### Post by nautilus on 2005-04-17
I don't want them in the door.  Let them stick to WinMacOS :)

Okay, it may be mean to say, but if "they" know about Linux and the alternatives (and if "they" use computers to any significant capacity) and they don't migrate for whatever reason, let them stick to what they have.

Personally, Linux, Ubuntu, KDE, they all do what I want/need/wish, so at this point eye-candy is about all I can ask for.

Wow, satisfied... That's so new, I can't believe I just realized.

---

### Post by Bug on 2005-04-17
I'm using OS X on my other primary machine and although I'm planning on moving from Windows to Ubuntu, OS X will still be used quite often. I just left a job in which I used OS X exclusivley, and I have extensive experience in OS X in all it's forms from Rhapsody to the builds of Tiger. So I like to think I have a pretty good perspective on OS X vs Ubuntu (Or linux in general). 

First of all, you can turn off alot of the OS X eyecandy features, from drop shadows to 3d effects. It's all in plist files (xml), just do a google search. However, I leave it on because it really does make a difference in usability to me. The drop shadows add an element of depth to the desktop that I miss in ubuntu, and the PDF rendering features are fantastic because ALL the apps that use the core services take advantage of them (which is just about all the OS X apps).  Most of the graphics can be edited, and if you look in the developer documentation you'll see many cool features and effects have not been enabled yet (but some apps already take advantage of them). And don't get me started on the features of Tiger's Core  Imaging and Graphics systems! But this isn't a post about OS X.

It's about Ubuntu, and the thing hurting Ubuntu was mentioned in a previous post in this thead; The drivers. ATI needs to get their drivers into a noobie usable state, it's really a crapshoot if they work or not. Nvidia seems to be doing a better job.

Without the driver support, there can be no eyecandy. I bought a $300 ATI card that now will either do compositing or 3d acceleration. Thats just silly. Once we get the drivers, it seems like the other pieces are already being worked on. I'm sure you know how hard it is to debug display issues when your using bad GFXCard drivers... 

And the future really is going to be full of all this eyecandy even if you personally don't want it. OS X had it, Microsoft is working hard at it, and Linux sorta has it.

One last thing, Ubuntu seems to 'get it' in respect to what I think is the perfect distro. One disk, most needed stuff installed by default, regular releases, good defaults, and above all an easy software distribution system. Most distros have a couple of these features, but Ubuntu seems to be the first one to reach a critical mass of these. And that's the reason I'm using Linux now, 'it just works (most of the time)'. The combination of OS X and Ubuntu in my office just fits together perfectly, with the cross compatibility (standards, not binaries!) making me much more productive. 

So- Backt to the point - Do we need eye candy?

Yes - It's the future of Desktops reguardless, we linux users should have the choice of using it, even if we don't want to. That's what Linux is all about isn't it? Choice and Flexibility.. And it's FREE!

Adam

---

### Post by Brunellus on 2005-04-17
[QUOTE=nautilus]I don't want them in the door.  Let them stick to WinMacOS :)

Okay, it may be mean to say, but if "they" know about Linux and the alternatives (and if "they" use computers to any significant capacity) and they don't migrate for whatever reason, let them stick to what they have.

Personally, Linux, Ubuntu, KDE, they all do what I want/need/wish, so at this point eye-candy is about all I can ask for.

Wow, satisfied... That's so new, I can't believe I just realized.[/QUOTE]

I want them in the door, because I want my friends and family to adopt MY operating system of choice.  :-P 

and, nautilus, uh...nice eyecandy avatar.   :-P

---

### Post by TravisNewman on 2005-04-18
Why should they have to? It's their choice to make too :)
Though I do know how frustrating it is to service Win PCs. ;)

---

### Post by somuchfortheafter on 2005-04-18
what is so bad about repairing windows based pc's is that let's say there is an error, ok you know that but unless it is a post error code or a virus or software error or maybe a hardware problem your pretty much screwed at software based stuff. i swear those error info pages they send to microsoft are encrypted to see if people are pirating software. Also in linux you can read the error code google it and whala your fixed 93% of the time.

---

### Post by Stormy Eyes on 2005-04-18
[QUOTE=Brunellus]I want them in the door, because I want my friends and family to adopt MY operating system of choice.  :-P [/QUOTE]

I take a rather BOFH approach to "persuading" my family to use Linux: I refuse to help them with *any* windows problems. I tell them that I don't use Windows at home, and while I use it at work I call the admin when something goes wrong. (the latter is a lie; I know enough to do my own troubleshooting most of the time, and rarely bother the admin.) If they ask me to build a computer for them and don't *provide* a legitimate copy of Windows, they get Linux and lessons on how to use it.

The only person who's griped is my paternal grandmother, and she's a worthless harpy who's ignored me most of my life unless she wants something from me or my father. She didn't even reply to the invitation to my wedding, so to Chaos with her.

---

### Post by Stormy Eyes on 2005-04-18
[QUOTE=Bug]ATI needs to get their drivers into a noobie usable state, it's really a crapshoot if they work or not. Nvidia seems to be doing a better job.[/QUOTE]

It's true that ATI's poor driver support isn't good for Linux, but end users have to take a certain amount of responsibility. I think it's the user's responsibility to know what kind of gear he's got and google to make sure his gear is compatible. If you know you've got an ATI card (Big computer makers like Dell usually mention this), how hard can it be to google "Linux ATI driver" and see that ATI's Linux drivers are utter *crap*?

---

### Post by TravisNewman on 2005-04-18
[QUOTE=Stormy Eyes]It's true that ATI's poor driver support isn't good for Linux, but end users have to take a certain amount of responsibility. I think it's the user's responsibility to know what kind of gear he's got and google to make sure his gear is compatible. If you know you've got an ATI card (Big computer makers like Dell usually mention this), how hard can it be to google "Linux ATI driver" and see that ATI's Linux drivers are utter *crap*?[/QUOTE]
 Well that doesn't work if you have that dell and then get interested in Linux.

---

### Post by Sam on 2005-04-19
[QUOTE=panickedthumb]Well that doesn't work if you have that dell and then get interested in Linux.[/QUOTE]
Or if you bought an ATI card on the old times using windows... :?

---

### Post by Stormy Eyes on 2005-04-19
[QUOTE=panickedthumb]Well that doesn't work if you have that dell and then get interested in Linux.[/QUOTE]

In which case you get yourself a $50 nVidia card from TigerDirect, replace the ATI card, and move on.

---

### Post by fng on 2005-04-19
[QUOTE=Stormy Eyes]In which case you get yourself a $50 nVidia card from TigerDirect, replace the ATI card, and move on.[/QUOTE]

I've payed $300+ for my ati card back in the windows days.  Im not going buy another graphics card.

---

### Post by Stormy Eyes on 2005-04-19
[QUOTE=fng]I've payed $300+ for my ati card back in the windows days.  Im not going buy another graphics card.[/QUOTE]

$300? Lemme guess: you're a heavy duty gamer, right? I can understand why you'd be reluctant to switch.

---

### Post by poofyhairguy on 2005-04-19
[QUOTE=fng]I've payed $300+ for my ati card back in the windows days.  Im not going buy another graphics card.[/QUOTE]


I did too. And let me tell you- that $50 Nvidia card will work better than that $300 ATI card in Linux. I know because last week I bought the $50 card to replace my big, bad ATI card.

But if you are into games, you are probably better off dual booting. If you don't game on the Linux side, all an Nvidia card adds is pretty fading and shadowing techiniques.

The ATI thing turned me off to Linux at first, till I admitted that it wasn't Linux's fault. Its ATIs.

Push come to shove, cards have kinda stagnated recently- you might still get a good price for your ATI card on ebay!

---

### Post by jdodson on 2005-04-19
to address the eyecandy issue.  i agree with panikedthumb.

functionality and usability over eyecandy.

i tried to composite extension for xorg.  it was cool, however it was still a bit buggy.  i also dropped a few hundred FPS on glxgears.  wherein that is not a huge deal, i like to push my games to the max.  perhaps you can switch off composite when you play a game automagically, anyways.  in the end it was not really worth the buggy to get the cool composite(and i admit it is cool).  all the wobbly windows stuff looks cool too, however it is not building a more user friendly desktop, it is building a funner desktop.

i think it should be options you can enable, i dont think all the 3D spinning widgets and desktop-glam should be the default.

---

### Post by TravisNewman on 2005-04-19
Right on jdodson-- you said it like I was trying to say it!

---

### Post by ubuntu_demon on 2005-04-19
[QUOTE=jdodson]to address the eyecandy issue.  i agree with panikedthumb.

functionality and usability over eyecandy.

i tried to composite extension for xorg.  it was cool, however it was still a bit buggy.  i also dropped a few hundred FPS on glxgears.  wherein that is not a huge deal, i like to push my games to the max.  perhaps you can switch off composite when you play a game automagically, anyways.  in the end it was not really worth the buggy to get the cool composite(and i admit it is cool).  all the wobbly windows stuff looks cool too, however it is not building a more user friendly desktop, it is building a funner desktop.

i think it should be options you can enable, i dont think all the 3D spinning widgets and desktop-glam should be the default.[/QUOTE]
 true.... stability/usability is the most important

but ubuntu should IMO have a big focus on getting cairo in as soon as possible. I think this will be the most important goal after all the current breezy goals are met.

---

### Post by poofyhairguy on 2005-04-19
[QUOTE=jdodson]
i think it should be options you can enable, i dont think all the 3D spinning widgets and desktop-glam should be the default.[/QUOTE]


If for no other reason that the fact that not everyone has the greatest/latest/most compatible equipment.

---

### Post by Bug on 2005-04-20
[QUOTE=poofyhairguy]If for no other reason that the fact that not everyone has the greatest/latest/most compatible equipment.[/QUOTE]
 I bought my ATI card when I was using my Windows box as a game machine. After spending >$250 on it, I really dont want to get another card just for the 'candy'. But I do miss it (I use OS X 50% of the time).

Adam

---

### Post by TravisNewman on 2005-04-20
[QUOTE=Bug]I bought my ATI card when I was using my Windows box as a game machine. After spending >$250 on it, I really dont want to get another card just for the 'candy'. But I do miss it (I use OS X 50% of the time).

Adam[/QUOTE]
 You can always get an old geforce4 pci for pretty cheap-- it'll give you some nice eye candy.

---

### Post by poofyhairguy on 2005-04-20
[QUOTE=panickedthumb]You can always get an old geforce4 pci for pretty cheap-- it'll give you some nice eye candy.[/QUOTE]


For the price, nothing beats a 5200fx in the eye candy department...

---

### Post by nautilus on 2005-04-20
Well, I don't have any Win32 systems, or OSX systems, just a Syllable workstation, and my Ubuntubox.

Between the two, I use my Ubuntu box for gaming ;)

As I see it, every new 'worthwhile' game already runs native in Linux or on my Playstation2, and for the older ones I have Snes9x.

All that Win32 stuff can stay in it's realm, and whoever uses it can enjoy.

In the end, I can't much compare my desktop/system with any other OS, and frankly one doesn't need to.  We all have the choice to run TWM, or to run Metisse+KDE+SuperKaramba+TwinView.  This is the beauty of Linux+Ubuntu :D

So, again, in my situation, I have the badass hardware and resources to do the candy, and I like the candy, such as Ms Lohan.

Even if it's off by default, I might become slightly disgruntled should the candy disappear from the universe repository... Grr!

---

### Post by latrine on 2005-06-28
I am a pretty straight forward user... I use office aplications and graphics/webdevelopment tools... 

I like windows for the games and programs... but I need an ocasional theme that goes away with the default looks
I like ubuntu because it works, it is secure, it is light, blah blha blah...

If I could, I would buy a Mac OS X because 

1- I could use the relative secureness of a Unix based system (I would know that it is there, but would not value it) just like ubuntu
2- I could use almost the same programs as in windows world
3- I would have a kick ass looking Operating System, that isn't somewhat stranded on 2d raster world

Belive me... I don't work with security in  mind... I just like the fuzzy feeling of knowing that it is there in Ubuntu...but... I work looking into a monitor the entire day... If I can make it more beautiffull  in a simple way, without going to the comand line (something I abandoned in win 3.1 world cos someone told me it was the natural usability evolution, and I agreed)... believe me, I will do it... me and 100% of other straight forward users...

Unfortunatly I have  a house, wife, kid and cat to support... so i am "stuck" in Open source world, in windows (that came with the computer- NVU, Inkscape, OO, GImp) and in ubuntu for working in safety... I am glad there is the Ubuntu way... But I would be gladder if it was eggxactly as Mac OS X is...

It is like comparing the minority report interface that tom cruise uses to the SSH and command line trinity uses in Matrix... baby... I prefer trinity, but I was baffled by Tom using that "future looking" GUI!

---

### Post by UbuWu on 2005-06-28
[QUOTE=latrine]
It is like comparing the minority report interface that tom cruise uses to the SSH and command line trinity uses in Matrix... baby... I prefer trinity, but I was baffled by Tom using that "future looking" GUI![/QUOTE]

And even nmap, which trinity uses, has nice frontend's for it  :razz:

---

### Post by TristanMike on 2005-06-28
[QUOTE=poofyhairguy]For the price, nothing beats a 5200fx in the eye candy department...[/QUOTE]
I have this card, how do I get this so called eye candy, be easy on me please
System Asus A7n8X Deluxe Motherboard/Athelon 2200+XP/2x512MB RAM/GeForceFX5200 128MB/Soundblaster Live Value/80GB Hard Drive
Thanx
TristanMike

---

### Post by Iuliux on 2005-08-02
[QUOTE=panickedthumb]You can always get an old geforce4 pci for pretty cheap-- it'll give you some nice eye candy.[/QUOTE]
wtf boys...installing an ati card on ubuntu/kubuntu is VERY easy.

---

### Post by BWF89 on 2005-08-02
I hate eyecandy. I used an Mac OSX display at a local CompUSA and my first impression was "Wow this looks really cool". My next impression after clicking on some things was "This really sucks! It's like KDE only 5x worse".

When I get Linux (I'm probably going to run it on my Playstation 3's hard drive if I don't get my own PC first) I'm probably going to run GNOME. Heck I might even run CDE (Common Desktop Enviroment) to give my box that old fashioned Unix system feel.

---

### Post by Kvark on 2005-08-02
Is eyecandy neccessary... yes, well maybe we don't need opengl effects today. But the default ubuntu theme (without extra tweaks) must beat windows xp (without extra hacks) at least. Which it does by far IMO. And vista when it comes out. ...why must it beat windows? Because windows sets the bar for average. And OSes are like girls, an uglier-then-average girl might have a great personality, be trustable and all that. But when the boys see you with her they only see the looks and comment on that you 'couldn't get anything better' then big-nose-Betty.

---

### Post by Stormy Eyes on 2005-08-02
[QUOTE=Kvark]But when the boys see you with her they only see the looks and comment on that you 'couldn't get anything better' then big-nose-Betty.[/QUOTE]

And that's why we should bring back duelling. :) Of course, I get your point. I just couldn't resist a joke along the way.

---

### Post by poofyhairguy on 2005-08-02
[QUOTE=Kvark]Is eyecandy neccessary... yes, well maybe we don't need opengl effects today. But the default ubuntu theme (without extra tweaks) must beat windows xp (without extra hacks) at least. Which it does by far IMO. And vista when it comes out. ...why must it beat windows? [/QUOTE]

Don't know why. I know we can't at first though. Why? Drivers. Thats the truth. If all Linux users had Nvidia cards then Linux eye candy would be great and stable. Drivers for the other cards (what most people have) suck. 

There is the truth.

---

### Post by NoTiG on 2005-08-02
Isn't the point that desktop acceleration is both eyecandy and usability? Did you not read the OS X users post about how each release of mac OS is fast? With desktop acceleration , the resources to handle eyecandy would be chump change. And there is no way you will be *Forced* to use eyecandy so i dont see what you all are complaining about.

---

### Post by poofyhairguy on 2005-08-02
[QUOTE=NoTiG]Isn't the point that desktop acceleration is both eyecandy and usability? Did you not read the OS X users post about how each release of mac OS is fast? With desktop acceleration , the resources to handle eyecandy would be chump change. [/QUOTE]

Only Macs with their magic trick (aka a closed box like a game console) can make an accereated desktop seem easy. If everyone had Nvidia cards we would be there too.

---

