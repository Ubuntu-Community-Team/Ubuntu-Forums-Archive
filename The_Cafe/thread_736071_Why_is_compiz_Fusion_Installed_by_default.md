---
title: "Why is compiz Fusion Installed by default?"
date: 2008-03-26
forum: The Cafe
---

### Post by MONODA on 2008-03-26
I do not have Compiz Fusion turned on and have not have it turned on for quite some time. The reason for this is because I have realized that it causes almost all the crashes and problems in Ubuntu (and most GNU/Linux distros in general). I remember during Feisty's time Beryl was installed but not turned on by default and there was a warning that it is still in testing. However in Gutsy it is turned on by default and no warning is given to the user that it is still Beta (or maybe alpha). Not only that, but it is turned on by default making a new user think that it will not cause problems. My experience in general with Compiz Fusion is that it causes many crashes and problems. I really hope that in Hardy there will be a warning. I post this because I want to see what other people have been experiencing and I also want to see if people agree that Compiz should not be turned on by default.

---

### Post by macogw on 2008-03-26
Perhaps it's just on your hardware?  It never crashes for me and a lot of other people.  The only thing that crashes my computer is my hard drive (stupid Circuit City replacing bad drives with worse ones)

---

### Post by Raven_Oscar on 2008-03-26
In Hardy Compiz is on by default. No warnings are displayed. At least in beta. But to my mind it works quite stable even on my ATI x1400.

---

### Post by MONODA on 2008-03-26
> Perhaps it's just on your hardware? It never crashes for me and a lot of other people. The only thing that crashes my computer is my hard drive (stupid Circuit City replacing bad drives with worse ones)
Well I have tried compiz on four pcs, two laptops, and two desktops and on every single on of them, I have had a plethora of problems with Compiz... That's weird, I thought most people were having trouble with it too. I have also seen other problems on this forum casued by compiz such as with videos and flash.

---

### Post by fela on 2008-03-26
I agree. I think they shouldn't have it on by default, and also in the appearances preferences compiz fusion tab, say 'WARNING: THIS IS ALPHA SOFTWARE AND EXPECT IT TO BE BUGGY'. right now they're acting like it's at version 1.0, as they both display NO warning AND have it on by default if hardware supports..tut tut. You may call me a hypocrit as i use compiz fusion, but I'm talking generally

It runs fine on lots of people's computers (most in fact, including mine) but on some computers its really buggy (that's why i'm giving this rant)

---

### Post by Mr. Picklesworth on 2008-03-26
Indeed.

Now that we have Metacity's nice little compositor, it would make sense to swap out Compiz for Metacity's compositing_manager by default. Metacity's compositor is still in early days as well, but I for one am finding it extremely stable and quite nice on my computer's battery life. Furthermore, it works practically everywhere I have tried it, including within VirtualBox.

There are fewer usability issues turning on compositing with Metacity, since it is not a change of window manager as Compiz is; all underlying behaviours for switching windows, etc. stay the same. There are also no strange inconsistencies or losses of functionality to speak of.

Perhaps Desktop Effects "safe" setting could do that, while the other crazy looking ones use Compiz...

---

### Post by aroth87 on 2008-03-26
I have Compiz enabled on both my desktop and my personal laptop, as well as my laptop at work. None of them give me any problems. Compiz works fine, doesn't crash at all.

YMMV.

Adam

---

### Post by fela on 2008-03-26
I like compiz myself...never used metacity's compositor.

---

### Post by diablo75 on 2008-03-26
I have installed both Beryl and Compiz Fusion on many PC's (Mostly on nVidia chipsets and in a couple cases some on board intel graphics chipset, one ATI a year ago), and the only one I've ever had a problem with is my own PC (because the video card was overclocked by the manufacturer, which I think is causing it to lockup; it's a BFG GeForce 5600 OC).  No other computer I've installed it on has ever had a problem with Compiz or Beryl.

What happened when you approached the forums with the problems you were having??  Nobody could help you?

---

### Post by Joeb454 on 2008-03-26
How do you enabled metacity's compositor? I'm running Hardy so should have it right? :lolflag:

---

### Post by eragon100 on 2008-03-26
I agree they shouldn' install it by default: I have bout 35 3de games (shooters, strategy, MMORPG, flightsim, etc), both closed- and opensource, and not a single (!) one of them works correctly when compiz is enabled. 

Let's try metacity compositor. Where can i get it and/or how do I activate it?

---

### Post by Joeb454 on 2008-03-26
This is what I'd like to know, because, although I rather like the shift-switcher compiz provides, the only reason I have compiz enabled is for a true transparent terminal, because I much prefer being able to read stuff through the terminal than not :)

---

### Post by diablo75 on 2008-03-26
Compiz doesn't seem to have an affect on my video game frame rates.  I can play Portal on Wine on Compiz, no problem.

---

### Post by Lord Illidan on 2008-03-26
To activate the metacity compositor :

copy and paste that in your terminal 

```
gconftool-2 -s  --type bool  /apps/metacity/general/compositing_manager true
```
EDIT : That will only work if you're using gnome 2.22, so if you're using gutsy default, it will not work.

---

### Post by FuturePilot on 2008-03-26
I've never had a problem with it. It runs just fine for me.

As for why it's installed by default, probably because everyone wants it. If it wasn't you would have a whole group of other people saying why *isn't* it installed by default, Vista and OS X are able to do compositing. You can't please everyone.

---

### Post by Mr. Picklesworth on 2008-03-26
> **Joeb454 said:**
> How do you enabled metacity's compositor? I'm running Hardy so should have it right? :lolflag:

Open the Configuration Editor (gconf-editor). Go to apps/metacity/general (easy way: Edit -> Find -> Type metacity). You will see a key listed on the right called "compositing_manager". Click the box beside that to turn it on.

The changes are fairly subtle. Many gains are simply from GNOME software expecting to have a stable compositor somewhere, so striving to work with it. Indeed, there is "real transparency" for all the fading screen stuff (gksu, for example). Window previews in the application switcher, fancy effects for launchers, drop shadows...
Definitely not as glamorous as Compiz (I miss Expo!), but it's still good.

Compositing in Metacity is new to GNOME 2.22, so only in Hardy. Err, usual disclaimer applies: Don't install the beta on a production machine because of me, no matter how fantastic it is.

---

### Post by Nano Geek on 2008-03-26
It has been a very long time since Compiz has caused any problems on my machine.

I say keep it on by default.

---

### Post by eragon100 on 2008-03-26
I can wait 29 more days till 8.04 comes out, thanx for the info :)

---

### Post by FuturePilot on 2008-03-26
I don't really like Metacity's compositing. It's not as smooth as Compiz and it has no options except for on or off. It also causes a lot of tearing when moving windows around and even in videos.

---

### Post by MONODA on 2008-03-26
Yeah but it shouldnt be turned on by default and there should be a warning. Well I cant use compiz anymore since it broke while  using it a while ago.

---

### Post by sumguy231 on 2008-03-26
I remember back in the day, I used Beryl and it probably crashed every 5 minutes or so. I've been using Compiz Fusion for a couple of months now and I've never seen it crash even once. There are still some integration issues with Compiz like keybindings and such, but they're already being worked on.
I think in the long run switching out Compiz for Metacity with compositing would actually be more of a headache than just 'taming' Compiz a little.

> Yeah but it shouldnt be turned on by default and there should be a warning.
It's generally only turned on by default if it's known to work well on the graphics hardware the system is using, or else it's blacklisted. That's fair enough to me. Maybe Metacity's compositing could be used with a similar configuration to Compiz on systems where Compiz is blacklisted, though.

---

### Post by macogw on 2008-03-26
> **fela said:**
> I agree. I think they shouldn't have it on by default, and also in the appearances preferences compiz fusion tab, say 'WARNING: THIS IS ALPHA SOFTWARE AND EXPECT IT TO BE BUGGY'. right now they're acting like it's at version 1.0, as they both display NO warning AND have it on by default if hardware supports..tut tut. You may call me a hypocrit as i use compiz fusion, but I'm talking generally

It runs fine on lots of people's computers (most in fact, including mine) but on some computers its really buggy (that's why i'm giving this rant)
Beryl was Alpha.  Compiz Fusion is technically Beta :P The thing that crashes the most is Emerald which is no longer supported by the C-F team.

---

### Post by SunnyRabbiera on 2008-03-26
well from the beta of hardy compiz is looking to be quite a bit lighter and stable then it is now, on the live compiz used a very minuscule amount of memory.
Truth be told compiz is quite stable for me, but I see why it can cause issues.
But there is a safe graphics mode available on the installer disk last time I checked.

---

### Post by FuturePilot on 2008-03-26
> **macogw said:**
> Beryl was Alpha.  Compiz Fusion is technically Beta :P The thing that crashes the most is Emerald which is no longer supported by the C-F team.

Emerald is no longer supported?

---

### Post by klange on 2008-03-26
> **macogw said:**
> Beryl was Alpha.  Compiz Fusion is technically Beta :P The thing that crashes the most is Emerald which is no longer supported by the C-F team.
Emerald may not be officially supported anymore, but it has been fixed up a lot. Emerald no longer crashes every 30 seconds. In fact, I haven't had a single Emerald crash in the past few months.

Most of the devs are in agreement that, at this point, Compiz is simply at a "pre-1.0" stage. Though, from what I've heard, we'll be going into some double-digit minor version numbers before bumping it to 1.0.

---

### Post by diablo75 on 2008-03-26
Hey, WindowsSucks.... your signature links are broken.

---

### Post by nutz on 2008-03-26
That is one of the best things about Ubuntu. Compiz is installed and configured by default. All you have to do is turn it on and I like that.

---

### Post by keykero on 2008-03-26
Compiz is the root of all evil.  Along with fglrx.

---

### Post by Fury5000 on 2008-03-26
I had just made the comment below to a new user having problems with a compiz side effect.  I also think it should be OFF by default.  Let them use the OS a bit.. see how it is "supposed to run".. then let them find the "on" switch... note the new problems and realize that the new "quirks" appeared _after_ activating compiz.  This keeps them from blaming everything on Ubuntu itself.

 Re: Dang These oversized windows!
There are many strings about this problem, its just finding the search terms people have called this problem in the past. Some call it "window off center problem" "windows alignment problem" I am surprised anyone is not familiar with this bug as I would call it. I have installed Ubuntu 7.1 on over 70 pc's and never seen one that didnt have this issue right out of the box. The systems I deploy are in a work environment so I turn off the "desktop effects" and this problem immediately goes away. Its a compiz issue. There are some workarounds as a previous poster has described. I do wish the desktop effects were "off" by default on new installs so people could learn the OS and fall in love with it without some of the quirky/buggy things aggravating them from the start. I was curious if this "issue" carried on to 8.04 beta and installed it the other day. Still there.

---

### Post by swoll1980 on 2008-04-06
'cause it's freakin' sweet!!!!

---

### Post by swoll1980 on 2008-04-06
I think the crashing is due to low spec video cards because my lap top that has a intel 845 64mb card crashes all the time but my desktop with 256mb nvidia has never crashed

---

### Post by Tundro Walker on 2008-04-06
Compiz tries to turn on by default, because Windows Aero Glass tries to turn on by default ... they're both "value added" things to enhance the look and feel of the OS.  Like Shuttleworth said, sometimes style IS substance, especially for some folks who are all about superficial look and feel (EG: the type of folks who just buy a car based on how it looks or what color it is).  Compiz happens to kick more butt than Aero, so it's a natural marketing choice to bolster Ubuntu bragging rights.

Now, what I've noticed is that Compiz doesn't seem to always auto turn-on.  If you have older hardware, or can't support it, it will be off by default.  There's no sense in firing up Compiz on an old p2.  Instead of providing a slick-looking interface, it would be a dog-slow system.  So, it's off in order to speed up the interface.

Take all that as you may, it probably doesn't help the fact that you seem to be annoyed by Compiz being on by default since your systems can handle it.  Dude, 5 seconds and you can disable it in the menus.  So really this is a non-issue.

---

### Post by macogw on 2008-04-06
> **swoll1980 said:**
> I think the crashing is due to low spec video cards because my lap top that has a intel 845 64mb card crashes all the time but my desktop with 256mb nvidia has never crashed

The Intel 8xx seem to be kinda yuck.  My mom's 855 is dying so sometimes doesn't talk to the monitor, but that's been going on for years.  Compiz doesn't, from what I recall, crash on it, just go really slow.  My i945 works great.

---

### Post by Fury5000 on 2008-04-06
> **swoll1980 said:**
> I think the crashing is due to low spec video cards because my lap top that has a intel 845 64mb card crashes all the time but my desktop with 256mb nvidia has never crashed

I know this is drifting off topic a little but your point may be the biggest issue.  Low system spec vid cards and pc's.  For many this was a big reason to move to Ubuntu.  To keep that old clunker alive as XP support ends and Vistas demands are too much to ask of the pc.  I guess the question is.. what percentage of the linux community are using high end pc's and vid cards?  I have several laptops and one aging desktop and one newly built uber-gamer pc.  Linux is on all of the machines except the gamer.  I did put ubuntu on the gamer just to see how it ran and quite frankly it ran at the same speeds as the aging desktop.  So to run linux on a super pc seems sorta like a waste of equipment.  My gamer pc was built for games so you know what OS is on it.. XP... the OS the games are being made for.  Whats my point?.. I "think" many that are migrating over to this OS at this time have lower spec equipment and this may be responsible for the surge of problems with things like Compiz.

---

### Post by Mr. Picklesworth on 2008-04-06
Compiz is also just not very good as a window manager. It's nice at the fancy compositing effects, but it has countless problems with all manner of things, such as breaking Fitt's law with docks. It also gives that odd problem with windows becoming stuck on top until I try to move them a couple of times (at which point they inexplicably become free again).

Metacity is less fancy, but it does manage to be a very consistent and reliable window manager, which is a breath of fresh air after a lot of Compiz. Frankly, I see no reason why Compiz's plugins have to be implemented in a way that makes them usable only with Compiz. Now that most popular window managers are coming to support compositing, it would make a lot more sense to develop these plugins as standalone apps that are triggered via existing frameworks. (Implementing and advocating standards where necessary).

For example, Compiz's favourite unique things are window switchers and workspace switchers. There are many fancy window switchers (eg: Expose clones) written as standalone applications, and there is no shame in the concept. Linux handles multiple small applications really, really well and having such a design is no different than having a bunch of plugins in Compiz -- except the system handling said tiny applications in this case is maintained and developed by an enormous community, and is aimed specifically at doing that well.
...I highly doubt Compiz's development community will overshadow the kernel's. If it does, I will pursue a career in baseball.

---

### Post by CarpKing on 2008-04-06
> **FuturePilot said:**
> Emerald is no longer supported?

The plan as I understand it is to replace it with a new window decorator providing the same functionality in a much more elegant and maintainable manner.  More on this [here](http://forum.compiz-fusion.org/showthread.php?t=6324).  To my knowledge, no work has been done on this yet.

---

### Post by bruce89 on 2008-04-06
> Why is compiz Fusion Installed by default?

Ubuntu goes for prettiness, not functionality.

---

### Post by ubuntu-freak on 2008-04-06
Not had one single crash due to CF. My question would be: Why isn't compizconfig-settings-manager installed by default?
 
Nathan

---

### Post by bruce89 on 2008-04-06
> **reassuringlyoffensive said:**
> Why isn't compizconfig-settings-manager installed by default?

Because it's a GUI disaster. Makes KDE look sparse.

---

### Post by ubuntu-freak on 2008-04-06
> **bruce89 said:**
> Because it's a GUI disaster. Makes KDE look sparse.

 
What do you mean? Could do with some better wording and descriptions, obviously, but should still be included by default just because CF is. 
 
Nathan

---

### Post by CarpKing on 2008-04-07
> **reassuringlyoffensive said:**
> What do you mean? Could do with some better wording and descriptions, obviously, but should still be included by default just because CF is. 

For one thing, it's designed around the internal structure of the software, not the apparent functionality of the software.  Instead of options that are logically related being placed together, options are placed in the section relating to the plugin they are provided by.  Instead of switching between two choices for a similar function, you enable one in one plugin and then navigate to a different plugin to disable the other.  It's a mess, and even the C-F team has said that it was intended for developers, not end users.  Simple-CCSM is an attempt to address this, but I don't know if it made it into Hardy and from the early screenshots it looks like it might err too far on the simple side.  This may be what some people need, but it would be nice to also have a tool that would provide most of the functionality of CCSM but arranged in a more intuitive manner.  

The above rant was for general purposes; from a purely Gnome standpoint, CCSM exposes way too many options.  The idea here is that any piece of software should start out configured in such a way that it will satisfy most people, and then have the smallest number of options you can have and still keep most people satisfied.  Whether or not Compiz-Fusion should follow this approach is another debete.

---

### Post by MONODA on 2008-04-07
> Dude, 5 seconds and you can disable it in the menus. So really this is a non-issue.
I know but newcomers do not know the risks of using compiz

---

### Post by phenest on 2008-04-08
> **FuturePilot said:**
> ...You can't please everyone.

You CAN please everyone. It should be optional like any other piece of software. It's not like you wouldn't be able to install it afterwards.

As it has already been mentioned, Metacity now supports compositing, and seeing as that's a part of Ubuntu already, it stands to reason to have that enabled by default. Perhaps to have option in the 'Appearance Preferences' applet to turn it on or off would be good.

I see no reason why CF needs to be installed by default. Or, at the very least, why it should be turned on.

If you want it that badly, then download it. Which is the same for any other software you want to use.

It is quite possible to add CF to a standard Ubuntu iso. Just check my signature.

---

### Post by ubuntu-freak on 2008-04-08
> **phenest said:**
> You CAN please everyone. It should be optional like any other piece of software. It's not like you wouldn't be able to install it afterwards.

As it has already been mentioned, Metacity now supports compositing, and seeing as that's a part of Ubuntu already, it stands to reason to have that enabled by default. Perhaps to have option in the 'Appearance Preferences' applet to turn it on or off would be good.

I see no reason why CF needs to be installed by default. Or, at the very least, why it should be turned on.

If you want it that badly, then download it. Which is the same for any other software you want to use.

It is quite possible to add CF to a standard Ubuntu iso. Just check my signature.

 
Perhaps it was only enabled by default due the hideous Metacity minimize effect. What's the status of that effect in 2.22? I haven't tried Hardy yet.
 
Nathan

---

### Post by HangukMiguk on 2008-04-08
Correct me if I'm wrong, but isn't Compiz disabled by default in legacy machines?

I know (or at least I'm fairly certain) I don't have it running.  And I doubt my machine could handle it.

---

### Post by Helios1276 on 2008-04-08
> **Raven_Oscar said:**
> In Hardy Compiz is on by default. No warnings are displayed. At least in beta. But to my mind it works quite stable even on my ATI x1400.
I've got the x1400 as well, is it the worst card for Ubuntu or what? I have compiz with no crashing but it doesnt like games in it's current incarnation on my comp.

---

### Post by CarpKing on 2008-04-08
> **HangukMiguk said:**
> Correct me if I'm wrong, but isn't Compiz disabled by default in legacy machines?

That is true.

---

### Post by Joeb454 on 2008-04-08
And also by default it is only set to Normal in System>Preferences>Appearances :)

It could be worse, for high-end systems it could be set to Extra (though I don't think it is :)

---

### Post by cardinals_fan on 2008-04-08
Why don't we have an 'Install Compiz Fusion' button under the desktop effects tab, but otherwise not include it?

---

### Post by 23meg on 2008-04-08
> Why is compiz Fusion Installed by default?

Discoverability. Push the "killer app" to people rather than expecting people to pull it. People are resistant to change, and pushing new code makes it mature faster. That fits Ubuntu's mission and mentality.

[QUOTE=phenest]You CAN please everyone. It should be optional like any other piece of software. It's not like you wouldn't be able to install it afterwards.[/QUOTE]

Think of default installation as merely "editor's choice". 

All software is optional, even those installed by default: you can remove them. Nobody is forcing you to use them.

[QUOTE=phenest]As it has already been mentioned, Metacity now supports compositing, and seeing as that's a part of Ubuntu already, it stands to reason to have that enabled by default. Perhaps to have option in the 'Appearance Preferences' applet to turn it on or off would be good.[/QUOTE]

It relies on your card's XRender implementation, and will spend CPU cycles if it's lousy. And it lacks any meaningful configuration and basic functionality expected from a compositor at this time, even as a GNOME component. And it has all the same OpenGL related problems with compositing.

---

### Post by cardinals_fan on 2008-04-08
> **23meg said:**
> 
Think of default installation as merely "editor's choice". 

All software is optional, even those installed by default: you can remove them. Nobody is forcing you to use them.

True, but running upgrades to the next version of Ubuntu with default packages removed has caused problems for me in the past

***prays for rolling release***

---

### Post by acelin on 2008-04-09
People need to learn that you need to get a real video card when using this stuff. Not even Ubuntu can promise perfect neato effects on 90's computers.

---

### Post by buried on 2008-04-09
Because It's a bummer to install using the terminal cause you have to do this and that and blah.

---

### Post by cardinals_fan on 2008-04-09
> **buried said:**
> Because It's a bummer to install using the terminal cause you have to do this and that and blah.
But well-written Compiz packages and the Restricted Drivers Manager make it easy...

---

### Post by buried on 2008-04-09
Exactly as cardinals_fan says, thanks :)

---

### Post by caravel on 2008-04-10
I agree with the anti compiz sentiment.  It should not be installed by default and should require the user to download it through apt-get.  In my humble opinion the default presence of compiz in Ubuntu is badly cheapening the OS's image.

Basically people are looking at Ubuntu as *"the OS to get if you want the fancy desktop cube thingy"*.  They then arrive here and expend their energies trying to get the cube to work and then leave disheartened if they fail to do so, or, if they do get it working, bored once the nolvelty that is compiz has worn off.  To such people ubuntu *is* compiz.

I'm sorry to say it but compiz is nothing more than a gimmick.  Yes it's pretty and awesome for the first 5 minutes and it gives publicity to ubuntu, but not the right kind of publicity and will probably end up backfiring.

---

### Post by hessiess on 2008-04-10
I think ubuntu should stick with making it easy for bginners to convert from windows, instead of emphasising useless graphical fluff that brakes other opengl apps.

---

### Post by eye208 on 2008-04-10
> **acelin said:**
> People need to learn that you need to get a real video card when using this stuff. Not even Ubuntu can promise perfect neato effects on 90's computers.
This is BS.

Show me the video card that makes video overlays (XVideo etc.) work with Compiz. There is none. Software rendering mode (X11) makes all video look as crappy as YouTube. And it's not even configured by default, i.e. new Ubuntu users will end up with a system **unable to display any video**. Given the large number of threads in this forum related to this problem, I'd rather not think about how many newbies ditched Ubuntu right after the first look, thanks to Compiz.

Compiz works for you because you don't use your computer for anything except moving wobbly windows around the screen.

---

### Post by Ozor Mox on 2008-04-10
Personally, I would go for stability over fancy effects, and I have Compiz switched off since it doesn't run well with 3D applications for me. If I could get it to run nicely, I'd have it enabled. People have criticised Ubuntu a lot for putting Compiz in by default, but I don't. If you don't like it, switch it off. It takes but five clicks and you never have to look at it again! Also, I like to believe that the Ubuntu developers know what they're doing. It only enables if the hardware supports it, as mentioned above it can be switched off, and I don't think it makes Ubuntu just about the graphic effects. Ubuntu's aim is to be beginner friendly and cutting edge. For rock solid stability, use the Debian base.

Just my humble input, though having said this I hope that Hardy really goes for the stability of features like Compiz.

---

### Post by eye208 on 2008-04-10
> **Ozor Mox said:**
> If you don't like it, switch it off. It takes but five clicks and you never have to look at it again!
You don't get it.

People don't switch Compiz off because they don't like it. They switch it off **because it doesn't work**.

Linux is not ready for the desktop until distributors realize they need to ship it with working defaults.

Five clicks to make windows wobble is acceptable. Five clicks to fix broken video playback or OpenGL is not.

---

### Post by elmer_42 on 2008-04-10
For what it's worth, my computer has no trouble running Compiz. Compiz has never crashed and Ubuntu has never crashed. I've only had it up for two days, but still. This is with an AMD X2 5000+ BE @ 3 GHz and an XFX 7600GT.

---

### Post by Ozor Mox on 2008-04-10
> You don't get it.

People don't switch Compiz off because they don't like it. They switch it off because it doesn't work.

Do you mean that the user is unable to boot the system or start X with Compiz enabled? In this case yes, that's a problem for them obviously. I was assuming when people say Compiz doesn't work for them, they mean they can't use 3D applications properly, or it keeps crashing, or whatever, in which case it's easy to switch it off from the menus.

> Linux is not ready for the desktop until distributors realize they need to ship it with working defaults.

Five clicks to make windows wobble is acceptable. Five clicks to fix broken video playback or OpenGL is not.

I still maintain that Ubuntu is meant to be relatively cutting edge. It uses Debian unstable repositories doesn't it? For a rock solid distribution that has safe defaults for all computers, there's Debian. I actually wouldn't mind if Compiz was included but not enabled by default, letting users choose to switch it on. I'm just trying to explain why I think they have done this.

---

### Post by caravel on 2008-04-10
> **Ozor Mox said:**
> If you don't like it, switch it off. It takes but five clicks and you never have to look at it again!

This is not the point.  The point is that in it's current state ubuntu *attracts* those that want _compiz_ not ubuntu for what ubuntu is in itself (Linux).  Compiz should not be part of, or a main "selling point" of the OS which seems to be the way they're heading.

---

### Post by Ozor Mox on 2008-04-10
> **caravel said:**
> This is not the point.  The point is that in it's current state ubuntu *attracts* those that want _compiz_ not ubuntu for what ubuntu is in itself (Linux).  Compiz should not be part of, or a main "selling point" of the OS which seems to be the way they're heading.

Out of interest, what gives you this impression? I can't recall the developers ever stating that their main goal is desktop effects. Yes, a few people have got a bit excited over a spinning cube, but I don't think that's the direction Ubuntu is taking is it?

---

### Post by elmer_42 on 2008-04-10
While I don't think that is the direction the Ubuntu developers have decided to go with it, even a quick YouTube search shows how many people are excited about Compiz and would use Compiz in Windows if they could. Many people only try out Ubuntu because they want Compiz.

---

### Post by caravel on 2008-04-10
> **Ozor Mox said:**
> Out of interest, what gives you this impression? I can't recall the developers ever stating that their main goal is desktop effects. Yes, a few people have got a bit excited over a spinning cube, but I don't think that's the direction Ubuntu is taking is it?

And I didn't say it was.  I said that:

*"compiz should not be part of, or a main "selling point" of the OS which seems to be the way they're heading."*

My point is that in previous releases compiz was not installed by default, now it is and the forums are full of people that are here just to have a look at "the cube" and then go back to windows.  I don't have a problem with this in itself but because of this ubuntu loses out.

---

### Post by ubuntu-freak on 2008-04-10
> **caravel said:**
> And I didn't say it was.  I said that:

*"compiz should not be part of, or a main "selling point" of the OS which seems to be the way they're heading."*

My point is that in previous releases compiz was not installed by default, now it is and the forums are full of people that are here just to have a look at "the cube" and then go back to windows.  I don't have a problem with this in itself but because of this ubuntu loses out.

Nothing wrong with them trying out Ubuntu because they're interested in all the effects. Once they try Ubuntu, they see how fast (even with effects enabled), secure, spyware and virus free it is, and that reels them in even further. I was so sick of spyware in Windows, viruses were actually easier to guard against, although scanning for them was very tedious.

Nathan

---

### Post by smartboyathome on 2008-04-10
Aren't effects what made people want to try Vista? Also, if compiz wasn't included by Ubuntu, I wouldn't be here right now. Compiz convinced me to try it out. Debian is stable as a rock, and do you see users using IT more than Ubuntu? No, because they want more up-to-date than stable, and if Ubuntu wants stability, they would base it off of Etch.

---

### Post by eye208 on 2008-04-10
> **Ozor Mox said:**
> I was assuming when people say Compiz doesn't work for them, they mean they can't use 3D applications properly, or it keeps crashing, or whatever, in which case it's easy to switch it off from the menus.
There's no point in arguing with fanboys.

Linux will not be accepted by mainstream users until it comes with working defaults. Period.

You want Ubuntu to fail? OK, go ahead.

---

### Post by Ozor Mox on 2008-04-10
> **eye208 said:**
> There's no point in arguing with fanboys.

Linux will not be accepted by mainstream users until it comes with working defaults. Period.

You want Ubuntu to fail? OK, go ahead.

In what way was anything I've said a fanboy comment? Not only have I said that I don't use Compiz because of problems with my graphics card, but I wouldn't mind if it wasn't there by default!

No I do not want Ubuntu to fail. If I did, I wouldn't have made it my desktop operating system of choice. You are interchanging Ubuntu and Linux though, plenty of Linux distributions come with extremely stable working defaults. One of them I have mentioned, Debian.

---

### Post by Fury5000 on 2008-04-10
Well I have to be totally honest here.  I did load Ubuntu solely for the purpose of seeing the cube that I had seen on youtube by accident.  Never touched Linux before but wanted to.  Compiz was amazing on my super pc but the pc was too overpowered for an OS without the mainstream games and was going to waste.  In the process fell in love with Ubuntu Linux.  Loaded it on a lesser desktop with an old geforce Ti200 and it worked fine for speed of effects but then the little compiz "glitches" were causing so much aggravation and headaches I just switched it off and never looked back.  I now have all my pc's and laptops running ubuntu as a result of wanting "the cube thingie"... I even have tried several other linux distros and keep coming back to ubuntu.  If this was ubuntu's master plan.. it worked.  I do vote for it being OFF at point of install and let the user turn it on with a warning message of possible issues once turned on.  Most new Linux users will start with Ubuntu and they should not be fighting with compiz BS right from the first boot.

---

### Post by eye208 on 2008-04-10
> **smartboyathome said:**
> Aren't effects what made people want to try Vista?
Effects are what made people stick with XP. In case you haven't heard, Vista has been a failure. It doesn't even succeed in the OEM market where it's forced upon customers whether they want it or not.

> Debian is stable as a rock, and do you see users using IT more than Ubuntu? No, because they want more up-to-date than stable
Bullsh*t.

Gentoo is more up-to-date than any other distro. Do you see people using it more than Ubuntu? You must be on crack if you think Ubuntu's success resulted from bleeding-edge instability.

You know what's going to happen if Ubuntu goes experimental? Dell will stop preloading it.

Please mess up some other distro, but not Ubuntu.

---

### Post by caravel on 2008-04-10
> **reassuringlyoffensive said:**
> Nothing wrong with them trying out Ubuntu because they're interested in all the effects.
I agree entirely.  There's also nothing wrong with me trying out ubuntu because I want to install a 3D game and see if I can get it running, or if someone else wants to install it to try something else.  My point is that it should not become *_part of the OS_* or get to the stage where it's even *_assumed to be part of the OS_* as this will mask many of ubuntus other good points.

> **reassuringlyoffensive said:**
> Once they try Ubuntu, they see how fast (even with effects enabled), secure, spyware and virus free it is, and that reels them in even further. I was so sick of spyware in Windows, viruses were actually easier to guard against, although scanning for them was very tedious.

Nathan
True enough, but you forget that the majority either don't get the effects working or that because they came solely for the effects in the first place are not interested in Linux as an OS.  They simply spin the cube around a few times then post their last thread on "how to remove ubuntu".

---

### Post by Ozor Mox on 2008-04-10
eye208, what exactly are you getting at? Users here don't have the direct ability to "mess up" anything. I'm sure Canonical can be trusted to make the right decisions for their distribution. After working so hard to get Dell support, they are hardly going to mess it up with a highly unstable release.

And **no**, just because Compiz doesn't work for you in Gutsy does not make the release a mess.

Gentoo is a very un-newbie friendly distribution. Most people think Ubuntu has a nice mix of cutting-edge features and stability. Obviously there are some who will disagree.

---

### Post by Fury5000 on 2008-04-10
> **caravel said:**
> They simply spin the cube around a few times then post their last thread on "how to remove ubuntu".

That statement is hysterical... yet so true...=D>

---

### Post by eragon100 on 2008-04-10
Compiz is a disaster :mad:

I have tried every free and commercial linux game I have and NOT ONE of them works coorectly (major bugs, unplayable) when compiz was enabled. Google Earth doesn't work correctly if it's switched on, neither does full screen video.
Most of the time, fullscreen video either gives a green screen or no screen :(

The LTS  release it supposed to be stable, people !

---

### Post by caravel on 2008-04-10
> **Fury5000 said:**
> That statement is hysterical... yet so true...=D>

Glad you agree.  I got sick of answering those threads after the 10th one, then thought about linking to my previous threads, then gave up altogether.  There is only so many times you can do the *"insert your windows disc and do fixmbr"* thing before you go into a fit and collapse.

---

### Post by caravel on 2008-04-10
> **eragon100 said:**
> Compiz is a disaster :mad:

I have tried every free and commercial linux game I have and NOT ONE of them works coorectly (major bugs, unplayable) when compiz was enabled. Google Earth doesn't work correctly if it's switched on, neither does full screen video.
Most of the time, fullscreen video either gives a green screen or no screen :(

The LTS  release it supposed to be stable, people !
Sorry to double post.

Someone correct me if I'm wrong, but I'm pretty sure that compiz has to be OFF before other apps can make use of OpenGL?  Either that or compiz will somehow need to automatically disable itself when the 3D app runs.  I wasn't aware that you could have two OpenGL apps running simultaneously and certainly not if one or both of them is a full screen app.

---

### Post by Foster Grant on 2008-04-10
> **23meg said:**
> Push the "killer app" to people rather than expecting people to pull it.

Wait. You're kidding, right? You're not *seriously* defining Compiz as a killer app? Because if you are, your credibility level just dropped through the floor.

A killer app is the embodiment of the law of disruption &#8212; it's an innovative technology that disrupts the status quo. You might call it "technocrack" if you want a buzzword &#8212; it brings people to a platform and keeps them there *by itself*. Nothing about Compiz fits that description.

It's a halo product, and in that it's a marketing tool (*"Hey dude, look at the kewl thing I can do!"*) but nobody's going to be awed by it and over the long term, nobody's going to be using *nix simply so they can watch the cube effect again.

Spreadsheets were killer apps. Web browsers were killer apps. On the Mac, Photoshop and Pagemaker were killer apps. Wordperfect was a killer app. Back in the day (back when Ford was president), BASIC was a killer app. The iPod is a killer app. The original Halo for Xbox was a killer app. On early editions of Windows, MS Office was a killer app. In each of these cases, people adopted them simply because it made something they did easier and more enjoyable.

Compiz is not in that category. It's a toy. People check it out and play with it, but it's not a reason to stay with *nix over time.

For that reason, it should not be loaded by default.

---

### Post by Fury5000 on 2008-04-10
Its more of a killer magnet to ubuntu.  The same people that put 65 lights inside their pc need this desktop bling.  From a support standpoint its a nightmare.  I wonder what the drop in daily post count would be on this forum if compiz was not in there.

---

### Post by CarpKing on 2008-04-10
> **caravel said:**
> Sorry to double post.

Someone correct me if I'm wrong, but I'm pretty sure that compiz has to be OFF before other apps can make use of OpenGL?  Either that or compiz will somehow need to automatically disable itself when the 3D app runs.  I wasn't aware that you could have two OpenGL apps running simultaneously and certainly not if one or both of them is a full screen app.

No, Compiz does not have to be turned off to run OpenGL programs.  They just aren't redirected, which can cause problems ranging from the OpenGL-rendered content staying in place while you move the window until you let go, all the way to problems rendering things.  These problems will be fixed when DRI2 is implemented in all the drivers (currently a buggy version is in really new versions of the Intel drivers).  You may have been thinking of XGL, which didn't allow other uses of OpenGL but is no longer necessary for anyone.  

Incidentally, Compiz doesn't prevent Xv playback either.  On ATI and I think Intel, if you move the window the movie will stay behind and then snap into place when you let the window go.  Transforming the window (opacity, wobbling, etc) will make it go solid-colored, but it should go back when it returns to normal.  I seem to recall that Nvidea has a workaround that allows Xv to be redirected, but in any case DRI2 will fix it.  

Xv had problems in Feisty (didn't work at all in Totem and VLC, troublesome in other players), but Gutsy seemed to fix it, at least for me (older low-end ATI card).

---

### Post by klange on 2008-04-10
> **CarpKing said:**
> No, Compiz does not have to be turned off to run OpenGL programs.  They just aren't redirected, which can cause problems ranging from the OpenGL-rendered content staying in place while you move the window until you let go, all the way to problems rendering things.  These problems will be fixed when DRI2 is implemented in all the drivers (currently a buggy version is in really new versions of the Intel drivers).  You may have been thinking of XGL, which didn't allow other uses of OpenGL but is no longer necessary for anyone.  

Incidentally, Compiz doesn't prevent Xv playback either.  On ATI and I think Intel, if you move the window the movie will stay behind and then snap into place when you let the window go.  Transforming the window (opacity, wobbling, etc) will make it go solid-colored, but it should go back when it returns to normal.  I seem to recall that Nvidea has a workaround that allows Xv to be redirected, but in any case DRI2 will fix it.  

Xv had problems in Feisty (didn't work at all in Totem and VLC, troublesome in other players), but Gutsy seemed to fix it, at least for me (older low-end ATI card).
Redirected Xv was already fixed if you're willing to use MPlayer with a patch. And XGL does allow other OpenGL apps (AiGLX is still better). DRI2 will of course fix everything - just need to wait for the glaring bugs to be fixed up (it's very sensitive to pixmap changes, it crashes immediately on even the slightest bit of iffyness).

Speaking of support, VIA embedded users rejoice, VIA's throwing themselves onto the open source drivers for their cards, and we should be getting the proper OpenGL bits to run Compiz (we'll wait and see what problems it may deliver, but hopefully it'll be just as smooth as 'intel' and 'radeon')

> BASIC was a killer app.
That would be the wrong definition of killer. BASIC killed in a literal manner.

> Compiz is a disaster

I have tried every free and commercial linux game I have and NOT ONE of them works coorectly (major bugs, unplayable) when compiz was enabled. Google Earth doesn't work correctly if it's switched on, neither does full screen video.
Most of the time, fullscreen video either gives a green screen or no screen

The LTS release it supposed to be stable, people ! 
That's not Compiz, that's the current DRI framework, and it not only "will be fixed" it HAS been - just needs to filter around. I can personally attest to such programs as Blender and Google Earth working perfectly (until DRI2's unpatched holes bring the entire X server down...)

> I wasn't aware that you could have two OpenGL apps running simultaneously and certainly not if one or both of them is a full screen app.
You can have as many OpenGL apps as you want - until you run out of graphics memory (or in the case of software rendering, regular RAM). The only dilemma with Compiz is that they aren't redirected, and since some apps do some weird drawing things, they just don't work. Best example is the little mesa test app - glxdemo - which renders one frame whenever the window is moved or resized. It appears entirely black on Compiz because it is rendered over. Works fine under DRI2.



This is the most retarded thread I've ever posted in - and I am a member of more forums than I can count. If you don't like the effects, don't use them. Don't bitch. Don't complain. We don't care that you don't like our cube. If you can't use them, don't bitch or complain either, it's not our fault there's some bug in the driver or some other random problem. Tell us what's happening, we'll help you through it if you can, but sure as **** don't complain - because when you complain, we stop caring. If you can't appreciate the fact that it exists in the first place, we probably don't want you to have it. If it works and you use it, good for you.

And lastly, and this is more of just a recent thing: For the love of Torvalds, stop complaining about GL and Xv, we've never been the people to complain to - it has **always** been the sole responsibility of those writing the drivers. And you shouldn't even complain to them - be happy you get accelerated graphics in the first place as most the developers don't get paid a dime for their work. Now more than ever is when you should stop complaining to anyone in general because *we now have a working solution that has been implemented*. Sit and wait, DRI2 will come to you soon enough and all your prayers will be answered. Even the most conservative of distros are considering the possibility of having a composting manager enabled by default because of DRI2.

And a side note: People seem to complain more about problems with Compiz than they do about other issues. I've seen thread after thread about how Compiz sucks, but you know how often I see threads about laptop power management problems - something that is more prominent of an issue than your compositor not working? Once in a blue moon. And when I do, it's usually a sentence or two - "ACPI isn't working on my laptop, fix it!", but when someone has a problem with Compiz they always seem to just rush in and pump out this massive rant about how compositing sucks and they either can't use it at all or it doesn't work with anything they use.

That's enough from me for today, I'm off to advocate the "Desktop Sphere"...

---

### Post by Fury5000 on 2008-04-10
> **WindowsSucks said:**
> 
This is the most retarded thread I've ever posted in - and I am member of more forums than I can count. If you don't like the effects, don't use them. Don't bitch. Don't complain. We don't care that you don't like our cube. If you can't use them, don't bitch or complain either, it's not our fault there's some bug in the driver or some other random problem. Tell us what's happening, we'll help you through it if you can, but sure as **** don't complain - because when you complain, we stop caring. If you can't appreciate the fact that it exists in the first place, we probably don't want you to have it. If it works and you use it, good for you.
.

I really dont think this is about not liking the cube or the effects or anything of the sort.  Its about what the string is titled.  Why is compiz installed or running as the "default" behavior.  Compiz is an amazing piece of eye candy and I love to show it to people but I turn it off for day to day computing.  The compiz problems I refer to in other strings are not driver related.

---

### Post by eye208 on 2008-04-11
> **Ozor Mox said:**
> And **no**, just because Compiz doesn't work for you in Gutsy does not make the release a mess.
Which part of **Compiz broke Xvideo for everyone** didn't you understand?

Please stop staring at wobbly windows and desktop cubes for a while and take a look at the support forums instead. Gutsy's video playback capability is seriously messed up because by default all the media players refuse to work properly if Compiz is on. And no, the connection between broken Xvideo and desktop effects is NOT obvious to new users. Some people take the time to bring up the topic here. Others just ditch Ubuntu after the first look because video playback has been considered an essential feature of desktop operating systems since Windows 98.

---

### Post by X_CheshireCat_x on 2008-04-11
i love the pictures i see of the cube but it seems to crash my laptop (ati radeon mobility x1400) :( think its a driver issue though. more important things to solve than compiz fusion. ;)

---

### Post by Ozor Mox on 2008-04-11
> **eye208 said:**
> Which part of **Compiz broke Xvideo for everyone** didn't you understand?

Please stop staring at wobbly windows and desktop cubes for a while and take a look at the support forums instead. Gutsy's video playback capability is seriously messed up because by default all the media players refuse to work properly if Compiz is on. And no, the connection between broken Xvideo and desktop effects is NOT obvious to new users. Some people take the time to bring up the topic here. Others just ditch Ubuntu after the first look because video playback has been considered an essential feature of desktop operating systems since Windows 98.

Telling me to stop staring at wobbly windows and desktop cubes is pretty moronic of you since I've already said a thousand times **I do not use or have Compiz enabled due to problems with my hardware**, so how about you stop making me out to be someone who gets all hot over a damn spinning cube, yeah?

YES I know it breaks some things, I could not get 3D applications working with it. I do remember having black screens with video playback as well. I used to disabled it for these things, and then re-enabled it when I had finished. Now I just tend to not bother. I agree these things may put of a newbie, but it still just requires a quick search on the forums and a few clicks to disable the effects. No, I don't think they should have to do this, but there are far more tricky problems they may have such as wireless and standby/hibernate, that makes this little problem disappear pretty quick.

Now I'll try once more. I am not arguing that Compiz should be in by default. I do not love Compiz. Eye candy is nice, but I will always choose stability over it. What I am trying to do is explain why I think it is in Ubuntu by default...after all isn't that the title of this thread? I think the developers want to make it cutting edge and attractive to Windows users (see bug #1), while still making it as stable as possible. There have been a few problems with the change to Compiz as the window manager yes, but I trust in the developers to work these problems out and continue to take Ubuntu in the right direction.

---

### Post by klange on 2008-04-11
> **eye208 said:**
> Which part of **Compiz broke Xvideo for everyone** didn't you understand?

Please stop staring at wobbly windows and desktop cubes for a while and take a look at the support forums instead. Gutsy's video playback capability is seriously messed up because by default all the media players refuse to work properly if Compiz is on. And no, the connection between broken Xvideo and desktop effects is NOT obvious to new users. Some people take the time to bring up the topic here. Others just ditch Ubuntu after the first look because video playback has been considered an essential feature of desktop operating systems since Windows 98.

Compiz didn't break it, it was broken from the start in the sense that Xv is an overlay mode and renders directly, just like OpenGL apps. And since when was it truly broken? Xv has always worked for me. In fact, half the time I never notice that I keep forgetting to set my desktop to Xshm because it works perfectly until I rotate the cube or move a window.

And lastly, it's been fixed. And not even with DRI2. There are patches for MPlayer that makes it uses transformed Xv - it's still hardware accelerated video, but it's redirected (just like what DRI2 does).

The next person to say anything about OpenGL and Xv is saying that they want me to leave this forum.

---

### Post by eye208 on 2008-04-11
> **WindowsSucks said:**
> And lastly, it's been fixed.
If it is fixed in Hardy, that's fine. I don't have any issues with Compiz itself, but I strongly believe that operating systems should be shipped with working defaults, especially if they are targeted at the mainstream.

However, in case it is not fixed and Compiz is still on by default, I will encourage all the people affected by it to PM you directly. ;)

---

### Post by klange on 2008-04-11
> **eye208 said:**
> If it is fixed in Hardy, that's fine. I don't have any issues with Compiz itself, but I strongly believe that operating systems should be shipped with working defaults, especially if they are targeted at the mainstream.

However, in case it is not fixed and Compiz is still on by default, I will encourage all the people affected by it to PM you directly. ;)
The patches aren't in Hardy yet, to my knowledge, but I'll help persuade them to add them (not that it really matters when they do, as mplayer doesn't come pre-installed, so it's not like adding them before release effects anything. I'm not sure if there are patches available for Totem). I guess we should really just wait until Ibex, as by then DRI2 should be standard in Xorg. Not sure if it'll make it into Hardy - definitely not before, probably not after.

---

### Post by phenest on 2008-04-11
This thread has been turned into a discussion on how to fix Compiz rather than discuss whether it should be in Ubuntu or not. I always thought that linux was about choice. Does Canonical follow this belief? If so, then everyone needs to have the choice as to whether Compiz should indeed actually be installed by default. To provide this choice is simple: remove it. Then if people want it, they can install it. You don't NEED Compiz. No one does. Ubuntu works fine without. Packages such as these should not be installed by default.

---

### Post by klange on 2008-04-11
> **phenest said:**
> You don't NEED Compiz. No one does.
I do ;)

For Hardy, I really have no opinion either way, as, yes, there are problems that are solved simply by removing it. However, once the problems are "permanently solved" with DRI2 and other various improvements, I think Compiz should regain its "pre-installed" status.

On a relevant side note: For all of the (two) machines I use Compiz on, it actually does improve performance - particularly because one of the machines isn't capable of doing everything with simple software output of standard windows - it needs an accelerated framework just to paint Firefox.

---

### Post by caravel on 2008-04-11
> **phenest said:**
> This thread has been turned into a discussion on how to fix Compiz rather than discuss whether it should be in Ubuntu or not. I always thought that linux was about choice. Does Canonical follow this belief? If so, then everyone needs to have the choice as to whether Compiz should indeed actually be installed by default. To provide this choice is simple: remove it. Then if people want it, they can install it. You don't NEED Compiz. No one does. Ubuntu works fine without. Packages such as these should not be installed by default.

Well said **phenest**, personally I don't care if compiz works or not.  That is not the issue I have with it.  Compiz could be the most stable and perfect piece of coding on the planet and I still wouldn't want it installed as default.  Have it available through apt-get and make it easier to set up and install by all means, but people shouldn't have to *uninstall* it.  Ubuntu should not become a medium for bringing compiz to the masses, it should remain an OS in it's own right.

I'm done with this thread anyway.  Keep it civil.

):P

---

### Post by FuturePilot on 2008-04-11
> **phenest said:**
> You don't NEED Compiz. No one does. Ubuntu works fine without.

Must.....have.....Compiz

:lolflag:

I love compositing :)

---

### Post by NightwishFan on 2008-04-11
If I really do not want it installed I would just do a minimal install.

---

### Post by phenest on 2008-04-12
> **WindowsSucks said:**
> I do ;)

No you don't. You WANT it. That's different.

> **WindowsSucks said:**
> ...there are problems that are solved simply by removing it. However, once the problems are "permanently solved" with DRI2 and other various improvements, I think Compiz should regain its "pre-installed" status.

The argument for having Compiz removed is not because of bugs. It's because it doesn't need to be part of the main installation. Ubuntu doesn't need Compiz in order to be a great OS. It can be that without Compiz, and in fact, it IS a great OS without Compiz.

> **WindowsSucks said:**
> On a relevant side note: For all of the (two) machines I use Compiz on, it actually does improve performance - particularly because one of the machines isn't capable of doing everything with simple software output of standard windows - it needs an accelerated framework just to paint Firefox.

If it helps performance, then you can always install it afterwards. But I think you are part of the minority with that.

It's as if the only thing impressive about Ubuntu is Compiz. Ubuntu IS impressive without the need for eye-candy.

This needs to be taken up with the devs to discuss this properly.

---

### Post by K.Mandla on 2008-04-12
Funny. A year ago the masses were frothing at the mouth to have it turned on by default.

By the way, if you really want to get the ear of the developers you should be making your case on Launchpad. 

And another thing ... keep it civil. ;)

---

### Post by markthecarp on 2008-04-12
My nickel:

Include compiz with an install but do not enable. Offer the user the opportunity to enable.

Hardware Report:
Toshiba 1415-S173
Celeron 1.8 ghz
386 Mb ram
GeForce4 420 Go on board video
16 Mb shared video ram
running Hardy via dist-upgrades beginning with Fiesty
Compiz/Fusion works remarkably well.

I'm not good, just lucky.

-mark

---

### Post by klange on 2008-04-12
> **markthecarp said:**
> Hardware Report:
Toshiba 1415-S173
Celeron 1.8 ghz
386 Mb ram
GeForce4 420 Go on board video
**16 Mb shared video ram**
running Hardy via dist-upgrades beginning with Fiesty
Compiz/Fusion works remarkably well.

Thank you for posting that, someone was asking on our forums about hardware requirements, which are really hard to judge - we had people going at "64mb", then someone docked it to 32 with some old first-gen Radeons.

---

### Post by phenest on 2008-04-12
> **K.Mandla said:**
> Funny. A year ago the masses were frothing at the mouth to have it turned on by default.

I guess they're bored of it now.

> **K.Mandla said:**
> By the way, if you really want to get the ear of the developers you should be making your case on Launchpad. 

Consider it done.

> **K.Mandla said:**
> And another thing ... keep it civil. ;)

Ok. Own up. Who's not  being civil? :roll:

---

### Post by Fury5000 on 2008-04-12
> **K.Mandla said:**
> Funny. A year ago the masses were frothing at the mouth to have it turned on by default.

The masses might have thought once it was made part of the default package and ON by default more of the "issues" with compiz would have been taken care of as a matter of priority.  

> **markthecarp said:**
> My nickel:
Include compiz with an install but do not enable. Offer the user the opportunity to enable.

Thats all "I" feel is necessary from a support standpoint.  I just want the "new" user to have a smooth experience installing the OS before pushing the "what hell happened?" button

---

### Post by cardinals_fan on 2008-04-12
> **phenest said:**
> 
Consider it done.

Where?  I'd love to help advocate...

As for Compiz, here's my solution: create a Compiz metapackage that includes the important extras, ccsm, etc.  Then add a button in the 'Desktop Effects' tab of Appearance Settings to install Compiz with one click.  Easy for everyone, but not forced on anyone.

---

### Post by 23meg on 2008-04-12
> **Foster Grant]Wait. You're kidding, right? You're not seriously defining Compiz as a killer app?[/QUOTE]

The use of quotation marks should mark my skepticism of the term "killer app", or so I hoped. I'm not serious about any single app being *the* killer app that will "make people switch", but I know that many others are.

[QUOTE=Foster Grant]Spreadsheets were killer apps. Web browsers were killer apps. On the Mac, Photoshop and Pagemaker were killer apps. Wordperfect was a killer app. Back in the day (back when Ford was president), BASIC was a killer app. The iPod is a killer app. The original Halo for Xbox was a killer app. On early editions of Windows, MS Office was a killer app. In each of these cases, people adopted them simply because it made something they did easier and more enjoyable.

Compiz is not in that category. It's a toy.[/QUOTE]

If you think Compiz and the underlying technologies it's helping push to people are all about "eye candy", you are, like the majority of people speculating about Compiz in web forums, underinformed on what you're talking about. That assumption has been rebutted many times. Here are a few cases in which I've addressed it:

[http://ubuntuforums.org/showpost.php?p=1127262&postcount=26](http://ubuntuforums.org/showpost.php?p=1127262&postcount=26)
[http://ubuntuforums.org/showpost.php?p=1664686&postcount=39](http://ubuntuforums.org/showpost.php?p=1664686&postcount=39)
[http://ubuntuforums.org/showpost.php?p=1017603&postcount=2](http://ubuntuforums.org/showpost.php?p=1017603&postcount=2)

The prospect of a composited desktop where windowing operations, 2D transforms, drawing and animation are handled by the 3D hardware in your video card (which happens to be most of what you paid for) that's [sitting idle all the time]("http://jonsmirl.googlepages.com/graphics.html") in which you're not playing games, staring at a 3D screensaver or working with Blender **is** a "killer app" by your definition. 

Sure, it's possible to move windows around and transform them in non-accelerated, non-composited X. But it's painful. It hogs your CPU, causes tearing and all sorts of unprofessional looking artifacts. Mac OSX (thanks to Quartz) and Windows Vista (thanks to Aero) users have overcome this dark stage of computer graphics, but barebones X users are still suffering under it. They shouldn't be. Without proper acceleration, X and the toolkits running on top of it are a decade behind their proprietary rivals, and compositing plus accelerated 2D is *the* way to go on the modern desktop. Your windows shouldn't be minimized under the escort of a hundred stuttering black squares said:**
> I always thought that linux was about choice. Does Canonical follow this belief? If so, then everyone needs to have the choice as to whether Compiz should indeed actually be installed by default. To provide this choice is simple: remove it.

Whenever someone floats the "Linux is about choice" cliché, I get the smell of a bad argument, and I'm rarely wrong:

Putting forward "choice" as an argument in a discussion of defaults is *non sequitur*. 

As a user, you don't choose defaults; someone else has chosen them for you, and you use them, or change them where they don't suit you. They're not meant to suit everyone (or anyone, for that matter) 100% well, but are meant to be *mostly fine* for the majority of the audience, and easy to change for the rest.

Ubuntu doesn't offer you package selection at install time, but ships a single set of defaults that you can easily tweak and change later. This is done to keep the installation simple, and remove the burden of superfluous choice for the uninitiated user who doesn't (have to) know about all the bells and whistles that make up the OS. 

How does having the GNOME panel installed by default violate your right of choice to use the GNOME panel, or another panel, or no panel at all? Now substitute the GNOME panel with Compiz, or any other default installed app. How? How would you be any more (or less) free to choose a specific window manager if Ubuntu shipped with no window manager at all (which would be the most neutral configuration by your logic)? 

Defaults do not deny you the right to choose. They free people who couldn't care less about choosing, or are unable to choose specific applications for specific purposes from the burden of choice.

[QUOTE=eye208]
People don't switch Compiz off because they don't like it. They switch it off because it doesn't work.[/QUOTE]

Now **this** is what ideally shouldn't happen. Compiz is disabled on hardware with which it's known not to work. This is called blacklisting. Ideally, the blacklist should include every piece of hardware that's known to be severely problematic with it. 

If Compiz tries to run on your hardware, but can't, or severely cripples your experience, then your hardware should be blacklisted, so that the experience of unsuspecting new users who have it isn't ruined.

If you have hardware on which you believe Compiz shouldn't be enabled by default, file a bug report and indicate its model (output of "lshw -class display" and "glxinfo" would be useful).

[QUOTE=K.Mandla]By the way, if you really want to get the ear of the developers you should be making your case on Launchpad. [/QUOTE]

No, this is a discussion of policy, so it should go to the [ubuntu-devel-discuss mailing list]("https://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss"). Not that it hasn't many times in the past; [doing]("http://www.mail-archive.com/ubuntu-devel-discuss@lists.ubuntu.com/info.html") [a search]("http://dir.gmane.org/gmane.linux.ubuntu.devel.discuss") for the old discussions would be a good idea.

---

### Post by phenest on 2008-04-12
> **cardinals_fan said:**
> Where?  I'd love to help advocate....

[Question #29617]("https://answers.launchpad.net/ubuntu/+question/29617")
You may not totally agree with what I've put, but that doesn't matter. Just add what you feel like.

> **23meg said:**
> Whenever someone floats the "Linux is about choice" cliché, I get the smell of a bad argument, and I'm rarely wrong:

Talking about "choice" in a discussion of defaults is *non sequitur*.

That doesn't make it irrelevant. Don't toss aside what people are saying just because you don't agree.

It IS about choice. And it's about freedom of choice. Remember 'Freedom'? It's mentioned on the Ubuntu Home page.

As the end user, I say defaults IS about choice. The end users choice. The end users freedom of choice.

EDIT:
BTW 23meg, I hope you're not involved in any decision making, because you're last post makes it sound as 'if it doesn't work properly then it's your fault and it's up to you to sort it out'. Have you thought about working for MS?

---

### Post by 23meg on 2008-04-12
[QUOTE=phenest]Question #29617
You may not totally agree with what I've put, but that doesn't matter. Just add what you feel like.[/QUOTE]

The support tracker is meant to be used for support requests, and is populated by users, in the same way the support forums on this site are used. Discussions regarding policy are out of its scope.

[QUOTE=phenest]That doesn't make it irrelevant. Don't toss aside what people are saying just because you don't agree.[/QUOTE]

I didn't do that. I presented arguments against what I didn't agree with.

[QUOTE=phenest]It IS about choice.[/QUOTE]

And why? Because you say so? Where's your argument as to why it is?

[QUOTE=phenest]And it's about freedom of choice. Remember 'Freedom'? It's mentioned on the Ubuntu Home page.[/QUOTE]

Which of the freedoms listed at [http://www.ubuntu.com/community/ubuntustory/philosophy](http://www.ubuntu.com/community/ubuntustory/philosophy) is violated by the default installation of any application?

[quote=phenest]As the end user, I say defaults IS about choice. The end users choice. The end users freedom of choice.[/QUOTE]

You're entitled to say whatever you like. Just don't expect others to engage in a discussion with you if you just toss around unsubstantiated opinion and weasel words, because discussions are had with arguments.

[QUOTE=phenest]EDIT:
BTW 23meg, I hope you're not involved in any decision making, because you're last post makes it sound as 'if it doesn't work properly then it's your fault and it's up to you to sort it out'. Have you thought about working for MS?[/QUOTE]

I'm sorry that it sounds that way to you; that's entirely your interpretation and I certainly didn't mean it that way, and in an effort to keep this civil, I'll ignore your loaded question.

---

### Post by ubuntu-freak on 2008-04-12
> **phenest said:**
> [Question #29617]("https://answers.launchpad.net/ubuntu/+question/29617")
You may not totally agree with what I've put, but that doesn't matter. Just add what you feel like.



That doesn't make it irrelevant. Don't toss aside what people are saying just because you don't agree.

It IS about choice. And it's about freedom of choice. Remember 'Freedom'? It's mentioned on the Ubuntu Home page.

As the end user, I say defaults IS about choice. The end users choice. The end users freedom of choice.

 
The devs decided it should be default, and most people are happy with that. The GPU is supposed to handle what's displayed anyway, not the number crunching CPU which has plenty of other things to do.
 
Nathan

---

### Post by phenest on 2008-04-12
Jeez! You're like talking to a brick wall, 23meg. I hope someone else here can help put you in your place. You are very self opinionated.

Don't bother answering me, 'cos I'm off to find some one who listens.

---

### Post by klange on 2008-04-12
> **phenest said:**
> Jeez! You're like talking to a brick wall, 23meg. I hope someone else here can help put you in your place. You are very self opinionated.

Don't bother answering me, 'cos I'm off to find some one who listens.
No, he presented clear, concise facts to disprove your points and you refuse to accept them in anyway. You don't even provide a counter-point. *You're* the brick wall in this conversation.

> **phenest said:**
> No you don't. You WANT it. That's different.

You clearly have no idea who am I, I am a *Compiz-Fusion Developer*. I *do* need it. You clearly did not understand my humorous response.

---

### Post by cardinals_fan on 2008-04-12
> **reassuringlyoffensive said:**
> The devs decided it should be default, and most people are happy with that. The GPU is supposed to handle what's displayed anyway, not the number crunching CPU which has plenty of other things to do.
 
Nathan
I personally believe that an OS should include only the most basic components and allow the user to choose their apps.  This is not and never has been the philosophy of Ubuntu, and if the devs wish to include Compiz, that is their choice.

---

### Post by 23meg on 2008-04-12
> **phenest said:**
> Jeez! You're like talking to a brick wall, 23meg. I hope someone else here can help put you in your place. You are very self opinionated.

Don't bother answering me, 'cos I'm off to find some one who listens.

I spent twenty minutes of my life typing up a post to address your points, which means I listened. And you didn't respond to any of mine. 

Anyway, thanks for reminding me once more that trying to have a serious, factual discussion on the Ubuntu forums is a waste of time.

---

### Post by Foster Grant on 2008-04-12
> **23meg said:**
> 
If you think Compiz and the underlying technologies it's helping push to people are all about "eye candy", you are, like the majority of people speculating about Compiz in web forums, underinformed on what you're talking about.

Let me put this very bluntly: You do not talk down to me. Or anyone. Ever. Period. Just because this is an anonymous web forum, that doesn't mean you have the right to be rude when somebody disagrees with you.

> That assumption has been rebutted many times. Here are a few cases in which I've addressed it:

[http://ubuntuforums.org/showpost.php?p=1127262&postcount=26](http://ubuntuforums.org/showpost.php?p=1127262&postcount=26)
[http://ubuntuforums.org/showpost.php?p=1664686&postcount=39](http://ubuntuforums.org/showpost.php?p=1664686&postcount=39)
[http://ubuntuforums.org/showpost.php?p=1017603&postcount=2](http://ubuntuforums.org/showpost.php?p=1017603&postcount=2)

I see nothing that rebuts my point of view.

> The prospect of a composited desktop where windowing operations, 2D transforms, drawing and animation are handled by the 3D hardware in your video card (which happens to be most of what you paid for) that's [sitting idle all the time]("http://jonsmirl.googlepages.com/graphics.html") in which you're not playing games, staring at a 3D screensaver or working with Blender **is** a "killer app" by your definition. 

No, it's not. It's nice that it's possible, but most end users can and will live without it for two reasons: many end users don't have 3D hardware (hello, Intel graphics!) or don't use the hardware they do have and don't care if they use it or not.

A killer app, by itself, draws people to a platform and, by itself, keeps them there.

> Without proper acceleration, X and the toolkits running on top of it are a decade behind their proprietary rivals, and compositing plus accelerated 2D is *the* way to go on the modern desktop.

This is your opinion, not fact, and should be interpreted as such.

> Your windows shouldn't be minimized under the escort of a hundred stuttering black squares; they should be minimized with a smooth zoom animation.

Waste of graphic processor cycles. Why should there be animation *at all*? Hide the window and have done with it.

> It shouldn't take one painful second for the contents of the screen to be refreshed with visible artifacts every time you switch workspaces; it should happen with a smooth sliding effect, with all drawing done off-screen. If you have a counter argument against this, I'd like to hear it.

Waste of graphic processor cycles. Why waste time with a sliding effect when I can hit {Ctrl}-{Alt}-{->} and instantly be looking at my GIMP/CinePaint workspace?

---

### Post by cardinals_fan on 2008-04-12
> **Foster Grant said:**
> 
Waste of graphic processor cycles. Why should there be animation *at all*? Hide the window and have done with it.
> **Foster Grant said:**
> 
Waste of graphic processor cycles. Why waste time with a sliding effect when I can hit {Ctrl}-{Alt}-{->} and instantly be looking at my GIMP/CinePaint workspace?
Well said.  My argument against Compiz is that I want things done NOW.  Animations slow me down.

---

### Post by klange on 2008-04-12
> **Foster Grant said:**
> Wow! Set phasers on "unwarranted condescension."

Let me put this very bluntly: You do not talk down to me. Or anyone. Ever. Period. Just because this is an anonymous web forum, that doesn't mean you have the right to be rude when somebody disagrees with you.
He's not. "Uniformed" isn't a condescending term, it's very neutral. If you think Compiz is all about eye candy, you're wrong - you're missing key information about it and are therefore uninformed.

> 
I see nothing that rebuts my point of view.

He's rebutting your view that Compiz is a toy. It's definitely not just a toy - it adds serious functionality to the X server.

> 
No, it's not. It's nice that it's possible, but most end users can and will live without it for two reasons: many end users don't have 3D hardware (**hello, Intel graphics!**) or don't use the hardware they do have and don't care if they use it or not.
Absolutely no comment. I don't want to be *condescending*.

> A killer app, by itself, draws people to a platform and, by itself, keeps them there.

You have no idea how many people I've heard of that switched to a Linux distro simply because of Beryl.

> This is your opinion, not fact, and should be interpreted as such.
No, it's a proven fact. Graphical elements rendered by the CPU are "10 years behind". Period. That's not an opinion.


> 
Waste of graphic processor cycles. Why should there be animation *at all*? Hide the window and have done with it.

Waste of graphics processor cycles? The GPU isn't doing ANYTHING else at the time! Most people find animations - especially those where the window gets sucked/dragged/something else into a dock or panel - add to the natural feel of a desktop. Especially new computer users who can't grasp the idea of minimizing when they click a button and *poof*, where'd the window go?


> 
Waste of graphic processor cycles. Why waste time with a sliding effect when I can hit {Ctrl}-{Alt}-{->} and instantly be looking at my GIMP/CinePaint workspace?
Same exact comment as above. Cube and Wall help people visualize workspaces in ways the regular, non-composited system never could.

---

### Post by smartboyathome on 2008-04-12
> **Foster Grant said:**
> No, it's not. It's nice that it's possible, but most end users can and will live without it for two reasons: many end users don't have 3D hardware (hello, Intel graphics!) or don't use the hardware they do have and don't care if they use it or not.

A killer app, by itself, draws people to a platform and, by itself, keeps them there.

My intel 945 was able to use Compiz (although slowly) and my Intel x3100 runs it great on hardy.


> **Foster Grant said:**
> This is your opinion, not fact, and should be interpreted as such.

Its true. Macs and Windows now both have compositing, if Ubuntu does not, then it will be like using Windows 2000 (yes, even XP has some compositing!).


> **Foster Grant said:**
> Waste of graphic processor cycles. Why should there be animation *at all*? Hide the window and have done with it.

Because it makes the end user experience that much more enjoyable. I know that I like it when I use wobbly windows. I think compiz DOES provide a better end user experience when it works.


> **Foster Grant said:**
> Waste of graphic processor cycles. Why waste time with a sliding effect when I can hit {Ctrl}-{Alt}-{->} and instantly be looking at my GIMP/CinePaint workspace?

*You* don't have to, but both the desktop wall and the cube makes the concept of virtual desktops clearer to new users. A lot of them do get attracted by the graphics, and stay because of everything else. If Ubuntu looked like win 98, but was rock stable, would you see many users using it? Nope, it is partly because people are attracted by compiz that it is enabled.

---

### Post by NightwishFan on 2008-04-12
I like Compiz. Especially the water based plugins. I also agree that things should be done immediately, which is why I set effects to none if I do anything that involves a deadline. In my free time I like to wobble a few windows around while I am having a conversation, it at least makes use of my hardware. If Windows is allowed to have "aero" and Mac to have "aqua" then we should get "Compiz-Fusion". (Much better name in my opinion)

---

### Post by ubuntu-freak on 2008-04-12
CF is disabled on legacy hardware by default and enabled on non-blacklisted hardware. This is Ubuntu, not Xubuntu, so why waste time arguing about it? You're in the minority if you want it disabled by default - why should you overrule the rest of us? The devs saw how popular Beryl/CF was, saw the benifits and future benifits and so wanted to intergrate it into Ubuntu. Simple as that.
 
Nathan

---

### Post by cardinals_fan on 2008-04-12
Despite the fact that many forum members have used computers since before I was born, I still feel old-fashioned :)

The whole idea of a 'Desktop' always seemed strange to me.  After all, your desktop is really just a directory, so why is it special?  The same argument applies to animations.  The windows don't 'go' anywhere - they don't exist!  It's all one big visualization anyway, so I prefer it to be blazing fast.

As for visualizing workspaces, I like the Openbox solution.  A helpful menu lists your desktops and the windows open on each of them.  I attached a screenshot for those who haven't used it.

@reassuringlyoffensive: I don't want to keep arguing this point - I have already recognized that Ubuntu's goals are aligned with Compiz, and I just want to show an alternative with this post.  I'm probably leaving this now-irrelavent thread unless I can think of anything important to say.

---

### Post by danbuter on 2008-04-12
In Hardy, Compiz caused weird things to happen with Firefox 3. Once I turned it off, a few of my issues went away.

---

### Post by ubuntu-freak on 2008-04-12
> **cardinals_fan said:**
> 
@reassuringlyoffensive: I don't want to keep arguing this point - I have already recognized that Ubuntu's goals are aligned with Compiz, and I just want to show an alternative with this post.  I'm probably leaving this now-irrelavent thread unless I can think of anything important to say.

 
I didn't realise we were arguing!:-)
 
I was just responding to whoever can't understand why desktop acceleration is enabled by default on modern hardware in Ubuntu. 
 
Nathan

---

### Post by klange on 2008-04-13
> **danbuter said:**
> In Hardy, Compiz caused weird things to happen with Firefox 3. Once I turned it off, a few of my issues went away.

Such as? Maybe we can help.

---

### Post by Vadi on 2008-04-13
Imo, Compiz is what's doing the majority of the attraction to Linux.

'freedom'? Uh? A minority is seeking freedom. Free software? Essentials are already avialable on Windows. Fancy effects? Not quite. And yes, the initial impression does wear off - with the user already accustomed to linux.

Just my opinion, continue your very useful arguing more... (get out into the real world and try to convince average computer users to get linux, too, without compiz)

---

### Post by Foster Grant on 2008-04-13
[quote=23meg]compositing plus accelerated 2D is *the* way to go on the modern desktop[/quote]

@Windowssucks: I repeat myself: This statement is opinion, not fact, and should be interpreted as such. Just because one person stands at the top of a hill and announces, "This is the way things must be!" does that mean the rest of us have to kowtow to him? No. It is 23meg's personal opinion that accelerated 2D is the way to go. That does not make it a fact.

And *tu amigo* certainly _was_ being rude. As a rude person myself (ask anyone who sits down at my computer without asking me first), I know rudeness when I see it.

And neither he nor you have presented anything that rebuts my point of view. I have an ATI video laptop card with a lot of horsepower to it (my computer came with Vista, and I've seen its compositing features), but all that bling is just a waste of processor cycles if it slows down the process of people using their hardware.

There are no more "new computer users" who need help "visualizing workspaces." Not on this platform, not in this century. Nobody's coming into Linux blind. Think about it: In 2008, how many new Linux users have never used a computer before? None. They're coming over from some version of Windows and already have the "desktop," "folder" and "minimize/maximize" concepts figured out. Now they have to figure out the Linux file system and hierarchy, which is very different from FAT/NTFS. Throw in a bunch of sliding windows, spinning cubes, &c. and you may very well be throwing them into the deep end of the pool.

Honestly, some of you Compiz people remind me of the original GIMP development team. This should *not* be construed as a compliment.

(Side note: Since when do geeks and hackers talk like a bunch of marketing types? "Visualizing workspaces" ... gods save us from buzzword-quoting marketers with Powerpoint or OO.org Impress presentations.)

---

### Post by cardinals_fan on 2008-04-13
@Foster Grant: I agree with you about Compiz, but unfortunately, most people don't.  They love the eyecandy, regardless of its bloat.  And Ubuntu caters to the masses.  Simple as that.

Argh... I thought I was gonna stay away from this thread :)

---

### Post by CarpKing on 2008-04-13
> **Foster Grant said:**
> I repeat myself: This statement is opinion, not fact, and should be interpreted as such. Just because one person stands at the top of a hill and announces, "This is the way things must be!" does that mean the rest of us have to kowtow to him? No. It is 23meg's personal opinion that accelerated 2D is the way to go. That does not make it a fact.

I could have said "Windowed display systems are the way to go" in the 1980s and it would have been just a "personal opinion" as well.

---

### Post by ubuntu-freak on 2008-04-13
Desktop acceleration isn't about "eye candy" unless you change the default setup (advanced, custom with CCSM) and make it about "eye candy".
 
Also, having it enabled by default on the most popular distro aids the developement of desktop acceleration.
 
Nathan

---

### Post by vexorian on 2008-04-13
Compiz itself is quite stable.

The problem is that half the apps are not ready for it. Specially Java. Not to mention things like firefox. It is totally a bad idea to include it by default until this changes.

---

### Post by red_Marvin on 2008-04-13
> **Foster Grant said:**
> @Windowssucks: I repeat myself: This statement is opinion, not fact, and should be interpreted as such.

The point is that desktop acceleration goes beyond eycandy, it moves some of the desktop graphics routines from the cpu, to the gpu with
the result that the cpu can do other things with those extra cycles, like make your programs go faster. The alternative would be that the cpu does all
the work, and the gpu does nothing *while still consuming power*. It's not like it's turned off or something.

While anything exept mathematical truth can be argued to be just opinion. I think that "increased efficiency is the way to go" is close enough to the truth that it can be spoken as such.

---

### Post by Foster Grant on 2008-04-13
> **CarpKing said:**
> I could have said "Windowed display systems are the way to go" in the 1980s and it would have been just a "personal opinion" as well.

Tremendous difference. Macintosh System 5 was vastly easier and more intuitive than anything on any platform before it (and indeed, a good number of things that followed it — looking squarely at early editions of MWM and Windows versions 1, 2 and 3.x here), and that was due specifically to the GUI. Of course, the lack of a terminal interface was a mark against it.

Sliding desktops and rippling window edges don't make the underlying hardware easier to use, they just use more of the underlying hardware.

---

### Post by Foster Grant on 2008-04-13
> **red_Marvin said:**
> The point is that desktop acceleration goes beyond eycandy, it moves some of the desktop graphics routines from the cpu, to the gpu with
the result that the cpu can do other things with those extra cycles, like make your programs go faster. The alternative would be that the cpu does all
the work, and the gpu does nothing *while still consuming power*. It's not like it's turned off or something.

While anything exept mathematical truth can be argued to be just opinion. I think that "increased efficiency is the way to go" is close enough to the truth that it can be spoken as such.

So what percentage of *your* CPU time is actually spent drawing the operating environment?

As vexorian noted, Compiz makes things break. Useful things like Java and Firefox; there's also the black-window bug on Nvidia chipsets . If one can't use a needed application package because the fancy 3D display manager breaks apps, then is one really working with increased efficiency?

---

### Post by Vadi on 2008-04-13
Here's an idea: Ubuntu is Linux for human beings.

Okay? Stop being so selfish and try to turn it into something that's not for human beings.

Why am I saying this? Go on youtube.com, and search for "linux". You'll realize what human beings care about, which'll show up as the first video.

---

### Post by vexorian on 2008-04-13
The question would be: do human beings deserve to be given something that's surely going to make their lives harder?

As an example, there's certain site, community and contest stuff that requires people to run a Java program.  But then, since Java has issues supporting compiz it will slow down terribly. The users generally won't guess compiz is causing the issues, they will think that overall Ubuntu is a subpar OS.



The first result for Linux in youtube is a woman in a bikini?  That's what humans want...

---

### Post by red_Marvin on 2008-04-13
> **Foster Grant said:**
> So what percentage of *your* CPU time is actually spent drawing the operating environment?
Actually, enough to make the music sometimes skip a beat when I'm switching workspaces. And my computer should not be considered old from anyone's except a gamer's perspective.

---

### Post by graabein on 2008-04-13
Compiz Fusion runs flawlessly for most users and eye candy is on top of many peoples wanted list. I think you're in the minority on this and you can just turn the thing off.

---

### Post by Vadi on 2008-04-13
I simply don't understand - aren't there enough distros out there that don't offer compiz installed by default?

Is it that hard to uninstall?

I'm not sure why, but Java functions the same with/without compiz here. The first thing I get for a search if "WINDOWS VISTA AERO VS LINUX UBUNTU BERYL". Compiz is also why the majority of my friends were wow-ed and got Ubuntu - not because software is free speech / beer (they pirate/buy it and if it doesn't work, get something else), not because of stability (they got used to instability), but because compiz looked way nicer than aero, and has several very useful plugins for their work.

Has there been usability testing done on compiz? Or are all of these arguments just based assumptions of how people "think" compiz will spoil their experience?

Edit: Loud minority, I'm suspecting. Like Ubuntu for the ease that it offers, yet no, things are too easy and should be harder!

---

### Post by cardinals_fan on 2008-04-13
> **Vadi said:**
> I simply don't understand - aren't there enough distros out there that don't offer compiz installed by default?

Is it that hard to uninstall?

I can't believe I'm back again ;)

There are lots of distros without Compiz, and I currently use one (Zenwalk).  This is the point I was trying to make earlier - Ubuntu targets the market that wants desktop effects.

As for uninstalling Compiz, it is not difficult *at first*.  However, strange things tend to happen when Ubuntu updates without a default package...

---

### Post by Vadi on 2008-04-13
Exactly. I'm not sure why are people thinking that changing Ubuntu's target market is such a great idea.

---

### Post by Foster Grant on 2008-04-13
> **Vadi said:**
> Exactly. I'm not sure why are people thinking that changing Ubuntu's target market is such a great idea.

I rather thought Ubuntu's target market was everybody, not just PFYs.

---

### Post by Vadi on 2008-04-13
And you aren't trying to slim it down in a particular direction?

Yes, it is for everybody. Normal users get what they want, experienced ones can tweak ubuntu to how they want. Requesting that the tweaks be in by default is in fact, cutting down on the normal users.

---

### Post by Foster Grant on 2008-04-13
> **Vadi said:**
> And you aren't trying to slim it down in a particular direction?

Yes, it is for everybody. Normal users get what they want, experienced ones can tweak ubuntu to how they want. Requesting that the tweaks be in by default is in fact, cutting down on the normal users.

Do you consider a beta compositer that is buggy and not part of the default GNOME/K3.5.x installs to be "normal" or a "tweak"?

[size=1]EDIT: From further reading, it appears the compiz team does not consider the current release to be beta. I come from a time when anything numbered 0.*X* was beta software, and not for public release. That also includes Ubuntu Tweak, which I recommended on another thread. I consider Tweak to be much closer to true beta version than Compiz.[/size]

---

### Post by Vadi on 2008-04-13
...

Yeah, I understand your views now, and have no wishes to argue anymore. Bye.

(simply because down the road, it's the same type of "go compile it yourself, it's easy" and "linux isn't for you then if you can't do *x*". Views like that make their best effort to make Linux not usable by normal humans - yet then they whine and complain about the lack of commercial support for Linux, after they've shot themselves in the foot. Attitude expressed in your post very closely matches that of many "elite" Linux users)

---

### Post by bobbybobington on 2008-04-13
Answer: Because it is awesome.

---

