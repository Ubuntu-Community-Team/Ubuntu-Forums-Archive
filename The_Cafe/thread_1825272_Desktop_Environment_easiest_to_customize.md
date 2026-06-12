---
title: "Desktop Environment easiest to customize?"
date: 2011-08-15
forum: The Cafe
---

### Post by 8_Bit on 2011-08-15
What is the most easily customizable Desktop Environment?

I love that **KDE **has a built-in interface in its settings for switching and downloading themes. The customization is super easy.

**Gnome 3 **still requires manually putting files in various root-owned folders, and requires knowledge of CSS. Not easy for the layperson; No built-in theme selector in the settings.

What about the rest of desktop environments? No, don't mention Gnome 2. I only want to talk about projects still being worked on, not dead ones.

I have never tried OpenBox or any of the others. Are they as customizable, or as easy to customize?

(I ask all this because I *love *KDE's customization features, but unfortunately can't use it because the sound never works. I've tried Kubuntu and Fedora KDE and sound just won't work on either, even though sound works fine on regular Ubuntu or Fedora Gnome. So now I need another desktop environment, one that won't make me have to give up the same flexibility and ease of customization I've found in KDE.)

---

### Post by ninjaaron on 2011-08-15
Gnome2 has a fork now called [MATE]("http://matsusoft.com.ar/redmine/projects/mate").

Should be the same for configuration as Gnome2, presumably.  Furthermore, Gnome2 is still the stock DE on the current Debian stable, so it will probably be supported for the next two years at least through that community.

It's not really a question of which DE is the easiest to configure, because the configuration for all of them are usually saved in text files (very often formated as bash commands or XML).  It's more of a question of which DE has the best GUI tools for manipulating those configuration files.  That usually comes down to how long they have been around and how large the user-base is.  Obviously, that puts Gnome2.x and KDE among the best.

LXDE, powered by openbox, has fairly good GUI configuration tools, but they are still not as mature or extensive as those available for KDE and Gnome.  I understand Xfce is also good, but I haven't used it.

In a few years, I'm sure Gnome3 (including Unity) will have a configuration tools with similar capabilities to Gnome2.  I wouldn't be surprised if good tools begin emerging within the next six months, especially with Ubuntu adopting it.

Everyone is criticizing all these next generation DE's, but nobody seems to remember that they are still basically 1.0 software.  Gnome2 wasn't always like it is now at the end of it's life cycle (extremely bloated and configurable).

You think it's bad now, just wait to Wayland comes through and breaks EVERYTHING, and then the system slowly gets rebuilt into one that is vastly superior to X.  That's the reality of using an OS that is more or less a plaything for it's developers:  about the time it gets to be ready for mass adoption, the developers are going to get sick of the limitations in the current system and rewrite it from scratch.

The only way to avoid the problems inherent in this system is for the distributor to fork all the core components of the OS and maintain them independently... in which case you would have Android or OSX.

---

### Post by el_koraco on 2011-08-15
Why, Openbox, of course.

---

### Post by LowSky on 2011-08-15
XFCE is pretty easy to customize.

gnome 3 has gnome-tweak-tool, sure its in its infancy but give it 6-12 months.

---

### Post by whatthefunk on 2011-08-15
LXDE is good.  I love the LXpanel.  However, because its designed to be lightweight, it doesnt have all the features of other DEs.  On thing that annoys me though is that icons are saved all over the place.  If you switch icon themes, it always seems like one or two dont change and then you have to run around all over the place to change them all.

---

### Post by kmsalex on 2011-08-15
psh! dead? i think gnome 2 is quite far from dead, and if i had to pick one i'd say gonme 2. but then i never used kde much, and lxde and xcf both seam similureish to gnome's way of combustibility.

---

### Post by Version Dependency on 2011-08-15
> **el_koraco said:**
> Why, Openbox, of course.

This is probably the best answer.   A default openbox installation includes...nothing...absolutely nothing.  Where you go from there is up to you.  And it's not hard to modify it since openbox isn't trying to force anything on you.

---

### Post by 8_Bit on 2011-08-15
> **ninjaaron said:**
> Gnome2 has a fork now called [MATE]("http://matsusoft.com.ar/redmine/projects/mate").


Woah! Have you read what that page says? 


 		> ***"*****MATE** Desktop Environment, a [SIZE=3]non-intuitive [/SIZE]and [SIZE=3] unattractive [/SIZE]desktop for users, using traditional computing desktop  metaphor. Also known as the **GNOME2 fork***."*

Yikes! That's no way to attract GNOME 2 users to your project. GNOME 2 is anything but unintuitive. Is this project a joke? :confused:



Anyway, it seems like OpenBox with LXDE seems like the right way to go. I'll probably go with that. It's a shame that all the computing power of my machine will go to waste though. Do Awn, Dockie, and all those other bells-and-whistle type of programs work on LXDE? I like speed and customizability, but I also like pretty shiny things too. :)

---

### Post by NightwishFan on 2011-08-15
> **8_Bit said:**
> 
Yikes! That's no way to attract GNOME 2 users to your project. GNOME 2 is anything but unintuitive. Is this project a joke? :confused:
That is probably sarcasm because of the move to Gnome 3 upstream.


> It's a shame that all the computing power of my machine will go to waste though.
In my opinion less is more. Have more to spare for what you want: Using programs and gtd. :)


> Do Awn, Dockie, and all those other bells-and-whistle type of programs work on LXDE? I like speed and customizability, but I also like pretty shiny things too. :)
Most of the docks require compositing. Not sure if Openbox can use compositing as any time I have used it I was not interested in doing so. I have heard of this software "xcompmgr" though I have never tried it.

Basically any software should work under any environment if it is of decent quality and standards.

---

### Post by smellyman on 2011-08-15
> **kmsalex said:**
> psh! dead? i think gnome 2 is quite far from dead, and if i had to pick one i'd say gonme 2. but then i never used kde much, and lxde and xcf both seam similureish to gnome's way of combustibility.
 
It is on life support........

---

### Post by el_koraco on 2011-08-15
> **8_Bit said:**
> It's a shame that all the computing power of my machine will go to waste though. Do Awn, Dockie, and all those other bells-and-whistle type of programs work on LXDE? I like speed and customizability, but I also like pretty shiny things too. :)

Yes, you just need a compositor. The two compositors used with Openbox are xcompmgr and cairo-compmgr. 

The first tends to have nicer compositing results, but it's harder to configure, and it tends to get a little more buggy. The second even has a GUI and stuff.

---

### Post by ninjaaron on 2011-08-15
> **el_koraco said:**
> Yes, you just need a compositor. The two compositors used with Openbox are xcompmgr and cairo-compmgr. 

The first tends to have nicer compositing results, but it's harder to configure, and it tends to get a little more buggy. The second even has a GUI and stuff.

xcompmgr is also no longer in development, I do believe

---

### Post by keithpeter on 2011-08-15
> **ninjaaron said:**
> Everyone is criticizing all these next generation DE's, but nobody seems to remember that they are still basically 1.0 software.  Gnome2 wasn't always like it is now at the end of it's life cycle (extremely bloated and configurable).

You think it's bad now, just wait to Wayland comes through and breaks EVERYTHING, and then the system slowly gets rebuilt into one that is vastly superior to X.  That's the reality of using an OS that is more or less a plaything for it's developers:  about the time it gets to be ready for mass adoption, the developers are going to get sick of the limitations in the current system and rewrite it from scratch.

Hello ninjaaron and all

Yup, the Open Source development model often has a 'bleeding edge', then a 'stable' then a 'legacy' strand. My only problem with the 'new' desktops is the 'stable' strand seems to have got missed out. 

I'd love to try out Unity and Gnome 3 for a month just to see how [my workflow]("http://www.randsinrepose.com/archives/2004/07/21/messy_thinking.html") is accommodated, but alas the GeForce 6150 chipset is blacklisted at present. Hoping it gets sorted soon! I'll be moving sideways to XCFE in Ubuntu with a Debian Squeeze partition for continuity.

The OP asked which was the *easiest* to configure: I'd go for Openbox with Obconf and Obmenu. A little bit of configuration file tweaking perhaps for really ambitious things.

---

### Post by sffvba[e0rt on 2011-08-15
Enlightenment is super customizable...


404

---

### Post by Bazon on 2011-08-15
Being very disappointed from Unity's lack of customization I'm now very pleased with XFCE (Xubuntu)+Compiz on my desktop and LXDE (Lubuntu) on my netbook. 
Each of them offers all the options I want, setting them is easy, System-Settings or right click context menus.

---

### Post by KUU on 2011-08-15
> **ninjaaron said:**
> Gnome2 has a fork now called [MATE]("http://matsusoft.com.ar/redmine/projects/mate").


:) For any kind of success a fork has to have on board a good portion of original developers, KDE3 (Failed) is a prime example, Gnome2 will soon be just a memory.l

---

### Post by unknownPoster on 2011-08-15
> **KUU said:**
> :) For any kind of success a fork has to have on board a good portion of original developers, KDE3 (Failed) is a prime example, Gnome2 will soon be just a memory.l

It didn't fail. You're just misinformed.

[http://www.trinitydesktop.org/](http://www.trinitydesktop.org/)

KDE3 was forked and has been fairly well maintained.

---

### Post by KUU on 2011-08-15
> **unknownPoster said:**
> It didn't fail. You're just misinformed.

[http://www.trinitydesktop.org/](http://www.trinitydesktop.org/)

KDE3 was forked and has been fairly well maintained.


:) 1 Developer trying to play catch up does'nt count. plus Qt3 is dead. /

---

### Post by unknownPoster on 2011-08-15
> **KUU said:**
> :) 1 Developer trying to play catch up does'nt count.

LOLWUT.

There are 5 named developers.

[http://www.trinitydesktop.org/contributors.php](http://www.trinitydesktop.org/contributors.php)

I guess by your logic Slackware doesn't count since it's run by one guy...

---

### Post by sffvba[e0rt on 2011-08-15
> **unknownPoster said:**
> LOLWUT.

There are 5 named developers.

[http://www.trinitydesktop.org/contributors.php](http://www.trinitydesktop.org/contributors.php)

I guess by your logic Slackware doesn't count since it's run by one guy...


Slightly unrelated but[COLOR=Black] Patrick Volkerding does have a number of trusted people working with him on Slackware... 

OK, carry on...


404
[/COLOR]

---

### Post by unknownPoster on 2011-08-15
> **not found said:**
> Slightly unrelated but[COLOR=Black] Patrick Volkerding does have a number of trusted people working with him on Slackware... 

OK, carry on...


404
[/COLOR]

I know, still doesn't change my point.

Just because a project only has one main developer doesn't mean it's bad or will fail.

---

### Post by KUU on 2011-08-15
> **unknownPoster said:**
> I know, still doesn't change my point.

Just because a project only has one main developer doesn't mean it's bad or will fail.

You have to literally build slack yourself, and drag in lots of things that have been done by a 3rd party that are maintained. trolltech dropped qt3

---

### Post by BrokenKingpin on 2011-08-15
Probably KDE, but I find far to buggy. I use Xfce, and I find it fairly easy to customize (similar to Gnome2).

---

### Post by Lucradia on 2011-08-15
> **ninjaaron said:**
> Gnome2 has a fork now called [MATE]("http://matsusoft.com.ar/redmine/projects/mate").

Times out for me, sadly.

---

### Post by Jesus_Valdez on 2011-08-15
Maybe I'm misunderstanding something, but I don't think that Openbox qualifies as Desktop Enviroment.

Anyway, KDE has GUI with options for everything and you can use different windows managers with Gnome, so I'm gonna say is that they are tied and that is personal taste. I have never really use any other DE.

On an unrelated note, I use adeskbar with Openbox, doesn't have the bells and whistles of the more mainstream docks, but it does its job well.

---

### Post by Lucradia on 2011-08-15
> **Jesus_Valdez said:**
> Maybe I'm misunderstanding something, but I don't think that Openbox qualifies as Desktop Enviroment.

This is correct. Openbox is not a DE, but can act as a Desktop.

---

### Post by ilovelinux33467 on 2011-08-15
If KDE isn't working for you (which IMO is by far the easiest to customize) then XFCE would be my second choice.

---

### Post by NightwishFan on 2011-08-15
> **ilovelinux33467 said:**
> If KDE isn't working for you (which IMO is by far the easiest to customize) then XFCE would be my second choice.
I humbly agree. Gnome 3 isn't yet very customizable (and may never be? time will tell.)

---

### Post by el_koraco on 2011-08-15
> **Jesus_Valdez said:**
> Maybe I'm misunderstanding something, but I don't think that Openbox qualifies as Desktop Enviroment.


Who cares, it blows the other out of the water.

---

### Post by sffvba[e0rt on 2011-08-15
> **NightwishFan said:**
> I humbly agree. Gnome 3 isn't yet very customizable (and may never be? time will tell.)

Gnome 3 will be super customizable if you look at the underlying system... The problem is it seems Gnome doesn't want you to customize it... Therefor you need community written Tweak tools (and I am sure they will continue to become better and better)...

Got to love GNU/Linux :)


404

---

### Post by NightwishFan on 2011-08-15
> **not found said:**
> Gnome 3 will be super customizable if you look at the underlying system... The problem is it seems Gnome doesn't want you to customize it... Therefor you need community written Tweak tools (and I am sure they will continue to become better and better)...

Got to love GNU/Linux :)


404

Yes. I am hoping that this is the case. Well to be frank I really do mind I will use/like Gnome 3 anyway.. However if the tweak tools, themes, and extensions end up working ok Gnome 3 will be very awesome.

---

### Post by WinterMadness on 2011-08-15
kde in my opinion. gnome is far, far more difficult than kde is in this department.

---

### Post by Jesus_Valdez on 2011-08-15
> **el_koraco said:**
> Who cares, it blows the other out of the water.
It matters because you start comparing apples with oranges if you don't make the distinction.

---

### Post by ilovelinux33467 on 2011-08-15
> **WinterMadness said:**
> kde in my opinion. gnome is far, far more difficult than kde is in this department.

Agreed

---

### Post by ScionicSpectre on 2011-08-15
I'd say KDE. As you mentioned, it has an extensive automatic framework for downloading and switching all kinds of customizations- desktop themes, window borders, color schemes, modifying every aspect of the window manager's layout and size, dozens of plasmoids, etc. The great thing is that, on top of being so fully customizable, there are things you can do with plasmoids that you just can't do with applets in XFCE or GNOME 2. There's just a lot more possibility available to you in KDE- anything you want, you can create... except for GNOME 3.

So yeah, I'd say KDE. Remember to get qtgraphicssystem and change the rendering to raster so the desktop runs smoothly- for some reason this isn't default in Ubuntu (probably because from a technical perspective it shouldn't be better than native, although it definitely is).

Also, GNOME 2 is dead in that no one's going to develop it, and the guy who's working on MATE, bless his heart, doesn't have unlimited time on his hands for changing GNOME 2, and GNOME 2 doesn't really have a lot that needs changing. However, he is thinking of porting it to GTK 3 or using the new gnome-panel available in GNOME 3. I personally think people would be better off porting their applets to the cleaned up gnome-panel in GNOME 3 and using Fallback mode, since there are many improvements in the panel and metacity due to the port to GTK 3, among other features.

I think people on Ubuntu can't really see GNOME development as clearly as people using other distributions, since it's such a mixed bag of components and default settings. Hopefully 11.10 will fix this and give people a better chance to see for themselves the possibilities.

P.S. [https://live.gnome.org/GnomeShell/SweetTooth](https://live.gnome.org/GnomeShell/SweetTooth)

---

### Post by 8_Bit on 2011-08-16
> **ScionicSpectre said:**
> 
P.S. [https://live.gnome.org/GnomeShell/SweetTooth](https://live.gnome.org/GnomeShell/SweetTooth)

That's very encouraging. Good to know they haven't completely ignored all the (very warranted) complaints about "dumbing down the system" and removing customization features.

I look forward to the day when I can recommend a Gnome 3 distro to a friend, and not have to try to explain why you can't do something as simple as change your theme with it out-of-the-box, even though Windows can.

Anyway, referring to my original post in the thread, I tried all sorts of other OpenBox/LXDE distros today and encountered so many problems. Got fed up and went with Lubuntu. It's very nice. I noticed it lets you change the colors and whatnot of the theme directly within the settings, that's great. I have to admit that it practically feels criminal installing a compositor + dock on this thing. It's so smooth and clean as is. :P

I was disappointed that there doesn't seem to be a process viewer though? Maybe I missed it. (Any third-party ones you can recommend?)

---

### Post by ScionicSpectre on 2011-08-16
If you want a modern experience that's a lot like KDE 3 or XP's layout and feature set, LXDE is a fantastic option, and very, very light. I love their utilities- the last time I tried Lubuntu, I had gnome-system-monitor installed. Not sure if this is the case, anymore.

Also, there are extensive GNOME 3 extensions available for theme switching in the shell and adding a taskbar/dock permanently, along with a way to manage the notification area without having weird blending issues on the bottom panel. So you can very much have a GNOME 2 experience without Fallback mode. I will admit, however, that Gnome Tweak Tool doesn't have quite the inviting/simple interface for appearance customization as was provided by default in GNOME 2. I think it would make sense to bring it back in a much more simplified way than it was available in GNOME 2, although it may take a while for them to include it (namely because there aren't so many GNOME 3 themes out there at the moment- a dozen or so isn't enough for them to consider it as a serious feature).

But yeah, if you like customization as in KDE but you feel like KDE is too heavy, E17 is a great alternative- the only real issue with it is that there aren't many themes that match existing GTK themes.

---

