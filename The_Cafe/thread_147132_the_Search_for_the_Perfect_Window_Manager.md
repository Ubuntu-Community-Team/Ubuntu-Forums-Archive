---
title: "the Search for the Perfect Window Manager"
date: 2006-03-19
forum: The Cafe
---

### Post by benplaut on 2006-03-19
Sorry for being long-winded :rolleyes: 

Two days ago, i was an Enlightenment DR17 user. I was compiling the latest CVS, and to minimize the risk of breaking things, had uninstalled the old version first. I mucked around a bit in Openbox while it was compiling, and when i got back to E, it felt slow. Sure, the benchmarks say that Enlightenment is faster than openbox, but it didn't have the snappy feal of Openbox.

Yesterday, i went on a safari. I didn't know what it would be, but i had a goal in mind - the perfect lightweight window manager. This window manager has to be pretty. It's got to be fast. It's got to not have a pixel-border around the X button. It's got to work with my choice of panel (pypanel, in this case). It has to be customizable, and relatively easy to do so.

I looked at a few WM in depth, and skimmed over a few more. I'm not going to provide many screenshots, go to their websites if you want.

---
My first stop of the day was perhaps a bit extreme. Let me preface this by saying that Tuomo Valkonen is a damn genious. He thought up a completely new way to manage windows, and it's extremely efficient. It's also extremely comfusing, for the newcomer.

IonWM rm -rf's the stereotypical [IMG]http://i1.tinypic.com/rszq78.png[/IMG] in exchange for the idea that an application either uses your whole screen, or a predivided block of your screen, to which more apps can be seen at once. It's hard to explain, it's worth your while to install Ion3 and try it for yourself.

Ion is definately fast and efficient, the fitt's law compatability is excellent, but it's just too far off of the norm for me. I've been living with [IMG]http://i1.tinypic.com/rszq78.png[/IMG] for way too long.

---
After fleeing from Ion, my next stop was fvwm. The version in the repos was a version or two behind, but i figured that if i liked that version, i could always go back and compile the latest. I selected Fvwm from GDM and logged in.
AAAAAAAAHHHHHHHHHH!!!!!!! This ugly-as-sin WM lasted about five minutes, before i smashed it to pieces with a 20lb virtual sledgehammer. Yes, i know that there are infinate possibilites of customizing Fvwm, but as i looked through there forums, i knew that this wasn't going to be "*customizable, and relatively easy to do so*." Settle down, all you Fvwm fanboys (yes, all 2 of you). I'll give it another chance today. I think i'm going to have nightmares about that horrible horrible *horrible* default config. I'll give them one point for a nice website, anyway.

---
Still dazed with my mentally damaging experience with fvwm (ok, i've made my point, i'll shut up now), i decided to try what is supposed to be one of the more widely used WMs - fluxbox. From what i understand, Fluxbox's goal is to be a more configurable version of blackbox. Not only does it succeed, but it's extremely pretty! Most of the included default themes are pleasent to work with, but pleasent to look at, too!

After mucking around with the menu and keybindings, i made a horrifying discovery. Once I minimized/iconified a window, PyPanel couldn't bring it back up! i would have to go through the workspace menu and individually bring each window back to life. I voiced my complaint in #fluxbox, and a wonderful fellow called _markt said that if i could wait around for an hour or so, he'd make me a patch to fix the issue. The ubuntu community is great for answering questions, but this was one step beyond. Wow! I put away IRC and went on to my next victim while waiting.

---
Openbox. It's another fork of Blackbox, but the goal was to add something that it's parent was sorely missing - EWMH support. This allows you to use any panel, any Expose clone, and a wonderful tool called Wmctrl (it lets you minimize, maximize, close, etc, any window using a command rather than pressing a button. Very useful in scripts). Openbox also got rid of the toolbar, determined to be even lighter than Blackbox. The latest version, the 3.x series, is a complete rewrite, and shares no code from Blackbox.

I read the docu, edited the XML files for keybindings and the menu, and... that was it! It's ultra-fast and relatively comfigurable (rc.xml is your friend), but... that's it! It's just a window manager, nothing more. I was impressed at the simplicity, but i wanted more. That's about when _markt flagged me down with a link to a .diff patch. Perfect timing, Mark. Perfect timing.

---
I uninstalled fluxbox 0.9.14, and checked out 0.9.15 from the SVN repository. I applied the patch with no trouble, and compiled the beast (relative beast, of course). It compiled without a hitch, and i proceded to redo the menu modifications and keybindings that i had stupidly deleted.

Fluxbox was the best i'd found yet. It was pretty, it was fast. It worked with my panel, and the community was great. There was only one problem. Our little buddy [IMG]http://i1.tinypic.com/rszq78.png[/IMG] had a nice little one-pixel border around him. I could get rid of the border, but that left me without a border around a window when not maximized. I was starting to get a bit picky, i know, but it had been a long day, and i was a bit urked that nothing i'd tried yet had the magic borderless button.

---
I looked down through the Debian Menu's usefull section for switching WM mid-session, and noticed that there was still one there i hadn't tried. Xfwm. My brain called 'foul!' but my conscience told me to give it a fair try, so i logged into Xfce. After removing the panel and adding pypanel, I started to really like Xfwm. The themes were excellent, it looked really good, the speed was... different. To be frank, there isn't much of a speed difference between various WMs on a relatively modern system like mine, but you can still feal a difference. To log into my custom Xfce session took pretty much the same time as flux. Flux's menus popped up instantly, but Xfce had a miniscule pause before it opened. What was really noticable was the speed that a window was rendered. I use a relatively low resolution screen, and i usually have a few windows open - all maximized. Switching between apps in flux, the window would be blank for a half-moment before it rendered. Xfce was instant.

>>>>>>>><<<<<<<<

I feal a bit like a traitor right now. Not only did i decide on the heaviest WM out of my mix, it's also the only one bundled with graphical config tools. I guess i'm not yet ready for full-on Ratpoison (look it up), but it's a pretty big step, after being a gnome user for over a year, and Enlightenment DR17 for 2 months.

Speed is always nice to have, but it's a comprimise. What do i want? I want metacity themes on Xfwm's wonderful window rendering speed with Fluxbox's menus and E17's Evas module layer underneath.

I still have a few more days before heading off to Maui, and a few days after that before break ends. There are still a few more WMs for me to try:

WindowMaker (or another NextStep clone)
PekWM
IceWM
Possibly Kahakai
Fvwm (My conscience tells me to give it another chance)

Until next time, happy WM hunting!

---

### Post by zenrox on 2006-03-19
very well writen 
and very intutive
and hmmm i might try some of the other wm's thanks to you
/me farts 
/me then runs off to the next world

---

### Post by midwinter on 2006-03-19
Interesting read, thanks.

I've been trying to get off gnome for a while now, I recently installed xfce-svn to see how that was coming along and I think i'll be using that when 4.4 is released.  I should probably try out Openbox though, seems interesting.

---

### Post by benplaut on 2006-03-19
[QUOTE=midwinter]Interesting read, thanks.

I've been trying to get off gnome for a while now, I recently installed xfce-svn to see how that was coming along and I think i'll be using that when 4.4 is released.  I should probably try out Openbox though, seems interesting.[/QUOTE]

you might want to wean yourself onto openbox from Flux... it's a bit extreme, coming directly from gnome.

if you want, here's a screenshoot of the default Openbox configuration (i think the color messed up, the background is supposed to be brown):

---

### Post by midwinter on 2006-03-19
[QUOTE=benplaut]you might want to wean yourself onto openbox from Flux... it's a bit extreme, coming directly from gnome.

if you want, here's a screenshoot of the default Openbox configuration (i think the color messed up, the background is supposed to be brown):[/QUOTE]

Haha.  I have my desktop like that anyway, doesn't everyone? :)

---

### Post by benplaut on 2006-03-20
[QUOTE=midwinter]Haha.  I have my desktop like that anyway, doesn't everyone? :)[/QUOTE]

no ;) 

here's my current Xfwm

---

### Post by Project 318 on 2006-03-20
I've actually been pretty happy with blackbox

---

### Post by benplaut on 2006-03-20
[QUOTE=Project 318]I've actually been pretty happy with blackbox[/QUOTE]

I tried blackbox a week or so ago, and i wasn't impressed, compared to fluxbox. The community was a fraction of flux's, and the speed was very similar.

What i *am* impressed with is the windows port. BBlean and Xoblite (the bb4win family) are, IMO, better than any of the WMs i've found for linux yet. There are hundreds of plugins available, including the wonderfull BBinterface - it puts fvwm to shame in terms of customizability.

I wish someone would port BBlean back to linux :-#

---

### Post by halfvolle melk on 2006-03-20
Wow, just installed E17. It was looking all fancy and then I managed to break it in 2 minutes flat. That must be a record of some kind :mrgreen: Checking back in with my good friend Gnome.

---

### Post by Stormy Eyes on 2006-03-20
If you want to try FVWM again, I have a config you can use.

---

### Post by mostwanted on 2006-03-20
Personally, after trying Compiz out, I can't see myself going back to a non-GL window manager :)

*starts shaking Muine to get the wobbly window effect*

---

### Post by poofyhairguy on 2006-03-20
"The Search for the Perfect Window Manager" ended for me when Compiz was released.

Time to buy that Nvidia card, use my guide and get into 2006!

---

### Post by mstlyevil on 2006-03-20
[QUOTE=poofyhairguy]"The Search for the Perfect Window Manager" ended for me when Compiz was released.

Time to buy that Nvidia card, use my guide and get into 2006![/QUOTE]

Already onboard! :mrgreen: 

Compiz rocks!

---

### Post by fuscia on 2006-03-20
i just started using gnome with openbox as a wm (thanks to stormy eyes' 'how-to'). it's quite fast with scrollable workspaces. i use mostly fast, light apps (dillo, sylpheed-claws, rxvt), so the whole thing works well, plus, i get all the benefit of using the desktop environment.

---

### Post by super on 2006-03-20
i say take stormy up on his offer, or get some other fvwm configs at [guistyles.com]("http://www.guistyles.com/?page_id=9")

fvwm is THE window manager. and i will suffer no arguments to the contrary. :mrgreen:

---

### Post by mstlyevil on 2006-03-20
[QUOTE=super]i say take stormy up on his offer, or get some other fvwm configs at [guistyles.com]("http://www.guistyles.com/?page_id=9")

fvwm is THE window manager. and i will suffer no arguments to the contrary. :mrgreen:[/QUOTE]

Oh no you didn't go there. Compiz is THE windows manager. So you must now suffer away. :twisted:

---

### Post by super on 2006-03-20
[QUOTE=mstlyevil]Oh no you didn't go there. Compiz is THE windows manager. So you must now suffer away. :twisted:[/QUOTE]
okay, yeah. i would say compiz is THE window manager of the future.
still a little green tho, and no theming engine.

btw, for poofy, mstlyevil and the other compiz-ers.

[here is a hack to get you different window decorations]("http://members.chello.hu/linux/other.html"). instructions on how to do it are on that page. but as i don't use xgl+compiz i really haven't checked it out.

and he is using ubuntu.

here is the homepage [http://members.chello.hu/linux/]("http://members.chello.hu/linux/")

---

### Post by ThomasAdam on 2006-03-20
[QUOTE=super]i say take stormy up on his offer, or get some other fvwm configs at [guistyles.com]("http://www.guistyles.com/?page_id=9")
[/quote]

Or you could just read the [fvwm forums](http://fvwm.lair.be) which has a much larger subset of people's configurations.

Thomas Adam.

---

### Post by benplaut on 2006-03-20
ok, one at a time :P

@halfvolle melk: That's nothing... in my initial attempts using Shadoi's repo, the splashscreen made it segfault :P

@Stormy Eyes and Super: yah... i've been working on it all morning. Still doesn't look as good as a vanilla flux, but it can look that good... i'm sure of it :D

@all of you compizers: I've got an old ATI card, and won't be upgrading for a long time. Not until i get a desktop, anyway. My main goal in this was to find the balance between fast, feature-full, and good looking, but the main concern was speed.

There's no way compiz+gnome is as fast as Xfwm or Flux + pypanel...

---

### Post by ThomasAdam on 2006-03-25
[QUOTE=benplaut]There are hundreds of plugins available, including the wonderfull BBinterface - it puts fvwm to shame in terms of customizability.[/quote]

You should put that to the test.  :P  Something tells me two are not even comparable.

-- Thomas Adam

---

### Post by benplaut on 2006-03-30
[QUOTE=ThomasAdam]You should put that to the test.  :P  Something tells me two are not even comparable.

-- Thomas Adam[/QUOTE]

ok, that deserves a little "limitations apply, read on below"

there are hundreds of plugins requiring *minimal configuration*

roll-you-own WM is not for everyone :cool: 


As a little update, i've decided to stick with Flux - it's fast, efficient, has a great community, and the themes are easy to make. here's the obligatory screenie:

[http://www.lynucs.org/index.php?screen_id=1280656084420f00f7bbe2&p=screen](http://www.lynucs.org/index.php?screen_id=1280656084420f00f7bbe2&p=screen)

---

### Post by ThomasAdam on 2006-04-17
[QUOTE=benplaut]ok, that deserves a little "limitations apply, read on below"

there are hundreds of plugins requiring *minimal configuration*

roll-you-own WM is not for everyone :cool:[/quote]

Ah, I see.  That's completely different to your original statement.  I'm glad you've found something you (for the moment) are tolerant of.

-- Thomas Adam

---

### Post by dbw on 2006-11-13
T'would be great if someone with experience in several of these would add to the [wikipedia article]("http://en.wikipedia.org/wiki/X_window_manager") about window managers.  It seems fairly anemic in many ways.

---

### Post by shining on 2006-11-13
> **benplaut said:**
> 
After fleeing from Ion, my next stop was fvwm. The version in the repos was a version or two behind, but i figured that if i liked that version, i could always go back and compile the latest. I selected Fvwm from GDM and logged in.
AAAAAAAAHHHHHHHHHH!!!!!!! This ugly-as-sin WM lasted about five minutes, before i smashed it to pieces with a 20lb virtual sledgehammer. Yes, i know that there are infinate possibilites of customizing Fvwm, but as i looked through there forums, i knew that this wasn't going to be "*customizable, and relatively easy to do so*." Settle down, all you Fvwm fanboys (yes, all 2 of you). I'll give it another chance today. I think i'm going to have nightmares about that horrible horrible *horrible* default config. I'll give them one point for a nice website, anyway.


Well, I still think fvwm may be the perfect window manager for you, if you care about wm, and want things a certain way, because fvwm is the most configurable and powerful of them. The ugly default settings is a known problem, and has scared more than one :)
The fact that it's configurable and powerful comes with a downside though, it takes some times to build your perfect config for your perfect wm. That is, looking at config files from other users, reading manual pages and other documentation, and experimenting.
If you have time and motivation for that, go for it, it's worth it. Otherwise, forget it.

---

