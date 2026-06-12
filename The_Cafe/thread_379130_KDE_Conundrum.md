---
title: "KDE Conundrum"
date: 2007-03-08
forum: The Cafe
---

### Post by TheMono on 2007-03-08
My desktop looks like rubbish. The reason is, I like GNOME. GNOME works well for what I want. However, I like KDE apps. I think Kaffeine is one of the best media players out. Amarok for music, Ktorrent for downloads, etc...

So, nothing is consistent. I'm running a gnome shell to launch KDE apps. Does anyone else find themselves doing that? And does anyone have any suggestions? It really is so annoying. KDE apps are perfect for my needs, and the GNOME desktop functions exactly like I think a desktop should.

---

### Post by floke on 2007-03-08
Not much of a way around it AFAIK. I like to use K3b, which also stands out.

---

### Post by GeneralZod on 2007-03-08
Try making a list of the things you like about the GNOME desktop shell and what you don't like about the KDE desktop shell.  You *might* be able to get KDE to approximate GNOME.

---

### Post by Orval on 2007-03-08
Yes, I am experiencing the same. However, I have a Murrine Gnome desktop and installed the avialable Murrine-themes I could find for KDE and when using an icon theme that is available for Gnome and KDE, KDE programs look well integrated in Gnome. Could be done with other themes as well, I guess. The trick is to find themes that are available for both desktops.

---

### Post by finferflu on 2007-03-08
I would install KDE and make it look like Gnome (as I have already done ;))

---

### Post by chaosgeisterchen on 2007-03-08
> **finferflu said:**
> I would install KDE and make it look like Gnome (as I have already done ;))

Do you have any HowTo to achieve this?

---

### Post by Adamant1988 on 2007-03-08
Fortunately for you, KDE makes it very easy to add another kicker and move them around so that you're dealing with something that looks an awful lot like Gnome.  I definitely understand where you're coming from with this as I have the same issue, LOVE KDE apps, and Love Gnome.  Prefer the KDE style though, lets me configure more to my liking.  Gnome looks a lot better though.

---

### Post by finferflu on 2007-03-08
As mentioned by Adamant1988, KDE is very flexible, I don't think you need an HOWTO, also you could install Kickoff, which is the KDE SLAB, if you like that style (and it's more practical than the normal K menu, at least for me)...

If you want Kickoff, just add this repository
```
deb http://download.tuxfamily.org/3v1deb/ edgy 3v1n0
```

If you get a message like this:
```
W: GPG error: http://mirror.myISP.net testing Release:
The following signatures couldn&#8217;t be verified
because the public key is not available: NO_PUBKEY [key_id]
W: You may want to run apt-get update to correct these problems
```

just do:
```
gpg &#8211;recv-keys [key_id]
```
where [key_id] is given in the previous message.

and then in a terminal:
```
sudo aptitude install kickoff
```

Hope it helps :)

---

### Post by TheMono on 2007-03-08
Yes, I'm a big fan of the slab style, so knowing that is there for KDE is great.

I have installed Kubuntu-desktop, as I realised that I was using virtually solid KDE apps (and yes, K3b, I forgot to mention that one), but I just couldn't get it to feel right. I couldn't figure out how to theme it properly. Plus it doesn't play quite as nice with my Beryl... Though it certainly is not a deal breaker.

I'm thinking I should switch to KDE and force myself to stay long enough to get used to it.




The things I don't like about KDE though:
couldn't see if you could resize desktop icons
Single click file navigation
Damned Konqueror - has to be the most annoying app in the world. I want my file manager to navigate files. That is all.
The default theme, and the fact I couldn't see how to retheme easily - something like the gnome style would be best - though I did see how to theme the gnome apps to look at home in KDE!

KDE, with a nautilus clone for navigation and drawing the desktop, and an easy way to theme, would be perfect.


It's not that I'm scared of doing things the hard way, it is more that I change my theme often and it isn't worth doing it a hard way every time! Having said that though, I think most of my objections here are going to be just a matter of knowing where to find the right option / setting.

---

### Post by ComplexNumber on 2007-03-08
couldn't see if you could resize desktop icons - **you can, but unlike gnome that allows you to set any size, there are only 2 sizes available in kde. they can be changed in the kde control centre (appearance -> icons).**


Single click file navigation - **that can be changed to double click in kde control centre (ie peripherals -> mouse)**


Damned Konqueror - has to be the most annoying app in the world. I want my file manager to navigate files. That is all. -** i agree. i absolutely hated konqueror with a passion. it must be one of the most major irritations on any desktop environment.  luckily, dolphin will be the default file manager in kde 4, so thats something for many people to look forward to.**


The default theme, and the fact I couldn't see how to retheme easily - something like the gnome style would be best - though I did see how to theme the gnome apps to look at home in KDE! - [B]use the qtcurve or klearlooks style. also install the qt-gtk-engine. theming kde is quite difficult and intricate. when you install the theme manager themes, ensure that you have all the necessary components (ie icons, styles(ie kde equivalent of theme engines), and window decorations.
[/B]

---

### Post by Orval on 2007-03-08
I don't get why people hate konqueror so much. I love it! I use it even under Gnome. Nautilus is much to simplistic for me.

---

### Post by finferflu on 2007-03-08
If you want a faster KDE experience, just uninstall kubuntu-desktop and install kde-core. You will not have as many options as you have now, but you will be able to install them by yourself, so you will not have useless bloat (as in konqueror - you'll have the simple browser, with no particular add-ons).

---

### Post by karellen on 2007-03-08
what is the problem about running native kde applications in gnome? I do that with k3b, ktorrent, quanta plus, konversation...and they look just fine. even more, I like how they look and integrate :)

---

### Post by mips on 2007-03-08
> **ComplexNumber said:**
> couldn't see if you could resize desktop icons - **you can, but unlike gnome that allows you to set any size, there are only 2 sizes available in kde. they can be changed in the kde control centre (appearance ->**

Not true, I currently have 6 sizes for desktop icons, 16, 22, 32,48, 64, 128. I suppose these can be set somewhere in some config file to give you even more options, say 8 to 128.

For themes have a look at kde-look.org as there are quite a few kubuntu themes available.

---

### Post by ComplexNumber on 2007-03-08
> **mips said:**
> Not true, I currently have 6 sizes for desktop icons, 16, 22, 32,48, 64, 128. I suppose these can be set somewhere in some config file to give you even more options, say 8 to 128.

For themes have a look at kde-look.org as there are quite a few kubuntu themes available.
it is true. they look strangely like the set sizes available in all icon themes. have a look in the kde control centre at the size available for desktop, application, etc. i remember there only being 2 (last time i used kde was kde 3.5.5 on PCLinuxOS). the sizes are usually 32 or 64. i think they may be an option for "double size", but thats greyed out on most.

---

### Post by mips on 2007-03-08
> **ComplexNumber said:**
> it is true. they look strangely like the set sizes available in all icon themes. have a look in the kde control centre at the size available for desktop, application, etc. i remember there only being 2 (last time i used kde was kde 3.5.5 on PCLinuxOS). the sizes are usually 32 or 64. i think they may be an option for "double size", but thats greyed out on most.

Never mind. We'll just let people blindly believe it is not possible like you say.

---

### Post by GeneralZod on 2007-03-08
> **mips said:**
> Never mind. We'll just let people blindly believe it is not possible like you say.

How about let's not? :)

[http://etotheipiplusone.com/kde-desktop-icon-sizes.png](http://etotheipiplusone.com/kde-desktop-icon-sizes.png)

ksnapshot has a Snapshot Delay setting which makes taking this kind of "action shot" easy :)

---

### Post by mips on 2007-03-08
> **GeneralZod said:**
> How about let's not? :)


In that case I'll even take it a step further. Icon themes have build scripts in which you could also specify sizes you want if you get them from places like kde-look etc.

[http://www.kde-look.org/content/show.php?content=53006](http://www.kde-look.org/content/show.php?content=53006)

---

### Post by Pikestaff on 2007-03-08
Anyone looking for a more Gnome-ish KDE may want to check out this excellent tutorial I found:

[http://www.mutube.com/mu/kubuntu-like-you-ubuntu/](http://www.mutube.com/mu/kubuntu-like-you-ubuntu/)

I used it myself to create a sort of Gnome/KDE hybrid, but you can go much further and make your KDE look nearly identical to Gnome if you want.

---

### Post by TheMono on 2007-03-08
Alright then. I think I'll do it. I'll switch to KDE and force myself to stay there for a while...

---

### Post by DrainBead on 2007-03-08
> **ComplexNumber said:**
> couldn't see if you could resize desktop icons - **you can, but unlike gnome that allows you to set any size, there are only 2 sizes available in kde. they can be changed in the kde control centre (appearance -> icons).** 

No, it means that you are using an icon set sized in two different sized instead of blowing them up and making them look like crap. Use big icon sets, KDE will scale them down without a problem which is the point of SVG.

> Damned Konqueror - has to be the most annoying app in the world. I want my file manager to navigate files. That is all. -** i agree. i absolutely hated konqueror with a passion. it must be one of the most major irritations on any desktop environment.  luckily, dolphin will be the default file manager in kde 4, so thats something for many people to look forward to.**

Apart from being the fastest and least resource craving web browser, it handles media, text, documents, pdf's and  a shatload more things without being anywhere near any of the beasts of resorces that use the extremely slow Gecko engine.

And no, Konqueror will be the default file manager in KDE 4 with dolphin as an alternative (i'm sure this will confuse most GNOME users though "what you have an ALTERNATIVE", personally i'm just waiting for GNOME to restrict theming.


> The default theme, and the fact I couldn't see how to retheme easily - something like the gnome style would be best - though I did see how to theme the gnome apps to look at home in KDE! - [B]use the qtcurve or klearlooks style. also install the qt-gtk-engine. theming kde is quite difficult and intricate. when you install the theme manager themes, ensure that you have all the necessary components (ie icons, styles(ie kde equivalent of theme engines), and window decorations.
[/B]

KDE does a perfect job at theming GTK apps, you really don't know that it's a GTK app, the other way around, well, it simply adds to load times and takes ages to load.

If you use mostly QT apps, use KDE, if you use mostly GTK 2 apps use gnome, if you use mostly GTK 1 apps, upgrade.

---

### Post by kragen on 2007-03-08
To respond to the intial post:

I'm in the same position, I like the gnome desktop, but sometimes I feel like some gtk apps lack features that qt apps have. I've tried things the other way around (running KDE and installing gnome libraries), but it didnt work for me.

I find it really fustrating, both desktop enviroments are very good, if you consider the total hours of development which has gone into each, and then combined them into one, the result would be a far superior desktop enviroment. As it is, just about everything is being developed twice, in slightly different ways each time :(

---

### Post by ComplexNumber on 2007-03-08
> **GeneralZod said:**
> How about let's not? :)

[http://etotheipiplusone.com/kde-desktop-icon-sizes.png](http://etotheipiplusone.com/kde-desktop-icon-sizes.png)

ksnapshot has a Snapshot Delay setting which makes taking this kind of "action shot" easy :)
those icon sizes are not available on any kde distro i've ever used. there are only 2 sizes.
the thing is, kde doesn't support svg properly in the same way that gnome does at this time,  so it can't possibly have that range of icon sizes (unless the user isn't bothered about them looking jagged and really bad to the point of impracticality).




[quote=DrainBead]
Use big icon sets, KDE will scale them down without a problem which is the point of SVG.[/quote]
there's no such thing as a large(or small) icon set. 


[quote=DrainBead]
And no, Konqueror will be the default file manager in KDE 4 with dolphin as an alternative[/quote]
sorry, but you're wrong. the current plan is that dolphin is going to be the default file manager in kde 4. i don't know how many more times this needs to be said. you can either read it  [here]("http://commit-digest.org/issues/2007-02-18/moreinfo/633622/") or from Aseigo himself [here]("http://aseigo.blogspot.com/2007/02/konqueror-not-vanishing-news-at-11.html"). quote:
> The big plan is: dolphin will become the default file manager (kicker buttons and file:/ links bring it up); or a more file-manager-oriented GUI than in kde3. File management in konqueror will remain available, e.g. for people who like to have profiles where it's combined with other things. For code sharing even more, we are considering making a dolphinpart and using that as konqueror's directory view.

---

### Post by TheMono on 2007-03-08
I realise that KDE themes GTK apps to look consistent in KDE - problem is I can't find a KDE look that I like.

I hope to god that they use dolphin by default in KDE4. That's what I'm looking forward to, I almost certainly will switch then. But Konqueror is an absolute behemoth.

In response to "Apart from being the fastest and least resource craving web browser, it handles media, text, documents, pdf's and a shatload more things without being anywhere near any of the beasts of resorces that use the extremely slow Gecko engine."

1 - I don't like it as a web browser, Firefox suits my needs much better (with a few extensions)
2 - I can't imagine why I would want my file browser to handle media, text, documents, pdf's, and a shatload of anything, other than just files. I'd rather have a program that does something properly. I mean, technically, you could browse files in firefox, and with the right plugins handle documents, media, etc. But why would you want to?

---

### Post by TheMono on 2007-03-08
[http://dot.kde.org/1172721427/](http://dot.kde.org/1172721427/)

"Konqueror is not going to disappear for KDE 4, although its user interface may yet see some adjustments as its primary utility will not as the default file manager."

Hallejulah....

---

### Post by maniacmusician on 2007-03-08
I sort of agree with what you're saying, but not completely.

I think there just needs to be an easy way to control what things Konqueror handles. I'm sure there actually are settings in Konqueror's options to control that, but they should be easier to get to. Out of all the KDE apps, Konqueror seems to have the messiest Configure dialog.

But easy options would solve the problem. For example, I don't want Konqueror to handle images, because Gwenview handles that better, but I'd like Konqueror to open PDF's; that integration is nice, because the kpart of KPDF is just as full-featured as if I were opening KPDF itself.

---

### Post by TheMono on 2007-03-08
I can see the place of Konqueror for those who want functionality like the PDF's that you mention before, but as a personal thing, I guess I'm just a big fan of division of labour lol. 

For example, I detest reading PDF's within firefox, I'd much rather use evince.

And you are right. Simple options would solve the problem.

---

### Post by finferflu on 2007-03-08
I still say kde-core is the way to go!

---

### Post by DrainBead on 2007-03-08
> **ComplexNumber said:**
> those icon sizes are not available on any kde distro i've ever used. there are only 2 sizes.
the thing is, kde doesn't support svg properly in the same way that gnome does at this time,  so it can't possibly have that range of icon sizes (unless the user isn't bothered about them looking jagged and really bad to the point of impracticality).

Well, what can i say... you are transferring the faults of Gnome onto KDE, actually it is the other way around and the bigger icon sets are scaled down on KDE while most themes icon sets are blown up on Gnome resulting in pixelated images.


> there's no such thing as a large(or small) icon set. 

OK, now that is just ridiculous.

> sorry, but you're wrong. the current plan is that dolphin is going to be the default file manager in kde 4. i don't know how many more times this needs to be said. you can either read it  [here]("http://commit-digest.org/issues/2007-02-18/moreinfo/633622/") or from Aseigo himself [here]("http://aseigo.blogspot.com/2007/02/konqueror-not-vanishing-news-at-11.html"). quote:

The defalt file manager in KDE 4 is Konqueror, there has been some discussion on it for years and the conclusion of it all is that Konqueror will be the default file manager.

It's the default file manager of KDE 4 now, and by default i mean what will open when you open your file manager, it will not change.

I'm willing to put €1000 on a paypal account and bet it against yours on this, are you up for that? I  could use the funding of this new project i have.

---

### Post by ComplexNumber on 2007-03-08
**DrainBead**
believe what you want to believe then if that makes you happy.

---

### Post by DrainBead on 2007-03-08
> **maniacmusician said:**
> I sort of agree with what you're saying, but not completely.

I think there just needs to be an easy way to control what things Konqueror handles. I'm sure there actually are settings in Konqueror's options to control that, but they should be easier to get to. Out of all the KDE apps, Konqueror seems to have the messiest Configure dialog.

But easy options would solve the problem. For example, I don't want Konqueror to handle images, because Gwenview handles that better, but I'd like Konqueror to open PDF's; that integration is nice, because the kpart of KPDF is just as full-featured as if I were opening KPDF itself.

It's all in the control panel, it handles all of it.

There are five bazillion choices but otoh, once you made them, you can save the configruation and move it to just about any distro or BSD since it will be the same anywhere.

You want to change something in GNOME, good luck editing the registry like Gconf crap.

At least in KDE there is help for every single item and every single item makes sense.

In Gnome, well most things they restrict you from changing and the few things you can change are mosly editable in the registry.

It reminds me a lot of win ME, there is a setting for it, but you have to dig into the registry to find it, and this ia called "usability",

Yeah, you'd think they'd be joking, but they are not kidding at all, it's to "protect the user" obviously the GNOME team took a look at the ME manifesto and never returned to normal.

---

### Post by DrainBead on 2007-03-08
> **ComplexNumber said:**
> **DrainBead**
believe what you want to believe then if that makes you happy.

Same to you, i'm sorry about the challenge, it's just that i've had to keep answering this same post too many times.

Anyway, it was stupid of me and i apologize, no hard feelings?

Time will prove who of us are wrong, in the meantime, i'll stay out of that discussion if you will, deal?

Take care.

---

### Post by TheMono on 2007-03-08
DrainBead, can you point us to something more recent and / or more authoritative than [http://dot.kde.org/1172721427/](http://dot.kde.org/1172721427/) to support that please? I'm curious.

Edit: Sorry, I posted before you closed off the conversation before, but one more post with a reference or something wouldn't hurt... I'm just curious why such mixed messages are coming out of the KDE project.

---

### Post by aysiu on 2007-03-08
Having only skimmed this thread, I don't know for certain if someone's suggested this or not, but maybe you should consider running Gnome but with Kwin as the window manager instead of Metacity.

---

### Post by DrainBead on 2007-03-08
> **TheMono said:**
> DrainBead, can you point us to something more recent and / or more authoritative than [http://dot.kde.org/1172721427/](http://dot.kde.org/1172721427/) to support that please? I'm curious.

Edit: Sorry, I posted before you closed off the conversation before, but one more post with a reference or something wouldn't hurt... I'm just curious why such mixed messages are coming out of the KDE project.

Don't worry about it.

The KDE4 project is kept under lock and key, take anything you hear as something that "could be" there are a lot of discussion going on and a lot of people with a lot of strong feelings about some things. Basically the key is interoperability which excluses Dolphin as a file manager since it doesn't even recognize basic mime types yet and has NO way of making the settings since it's not supported through the default konqueror control panel interface, the chances of it being the default file manager is zero, zilch, nada. There are those who wish for it though but as it is, it's like using firefox as a file manager in Gnome, sure, it works but it sucks.

Dolphin though... i have high hopes for it and in time it could become a default "file browser" but it will never be a replacement for konqueror.

I'll tell you what though, i'll try to organize a round table discussion on some of the subjects but it will be a while until i can get everyone sorted on that kinda thing.

Sounds ok?

---

### Post by DrainBead on 2007-03-08
> **aysiu said:**
> Having only skimmed this thread, I don't know for certain if someone's suggested this or not, but maybe you should consider running Gnome but with Kwin as the window manager instead of Metacity.

Wasn't it poofyhairguy that wrote a guide on how to do that? I've been a lurker for a long time and i kinda remember that, i might be wrong though.

Anyway, with beryl-manager, that is so easy to do, even if you have no intention of ever using beryl, it's a worthwhile install just because you can change window manager on the fly, you can even run KDE with the fluxbox window manager (doesn't make much sense but you can).

---

### Post by aysiu on 2007-03-08
> **DrainBead said:**
> Wasn't it poofyhairguy that wrote a guide on how to do that? I've been a lurker for a long time and i kinda remember that, i might be wrong though.

Anyway, with beryl-manager, that is so easy to do, even if you have no intention of ever using beryl, it's a worthwhile install just because you can change window manager on the fly, you can even run KDE with the fluxbox window manager (doesn't make much sense but you can).
It was indeed Poofyhairyguy who wrote it... way back in November 2004... so I'm not sure if the steps are still the same, but [here's the guide](http://ubuntuforums.org/showthread.php?t=115974).

---

### Post by DrainBead on 2007-03-08
> **aysiu said:**
> It was indeed Poofyhairyguy who wrote it... way back in November 2004... so I'm not sure if the steps are still the same, but [here's the guide](http://ubuntuforums.org/showthread.php?t=115974).

Whoa, time flies.

The steps of that guide will work just fine even now.

Thanks for finding it aysiu. :)

---

### Post by bailout on 2007-03-08
> **ComplexNumber said:**
> those icon sizes are not available on any kde distro i've ever used. **there are only 2 sizes.**


There are actually 8 icon sizes in kubuntu and they don't look pixelated to me ;) But I am sure you will still try to argue that you are right, that there are only 2 sizes and KDE is terrible in evey way :D

---

### Post by DrainBead on 2007-03-09
> **bailout said:**
> There are actually 8 icon sizes in kubuntu and they don't look pixelated to me ;) But I am sure you will still try to argue that you are right, that there are only 2 sizes and KDE is terrible in evey way :D

Well that is only because he hates KDE and lies his **** off about it without even having used it.

In KDE they are the maximized kind and everything from that is scaled down (SVG is KDE's way fo doing it and apparently, since KDE does not need a halffway lib to sharpen the icons, it's tthe best, well,, whoulda thunk it... me?) no icon is pixelated if you don't want a taskbar that filles your screen with two icons on it.

You CAN increase icon sizes by the point if you really like to, it's not implemented in Kubuntu yet but it's in SuSE factory.

Thanks ballout.

---

### Post by bailout on 2007-03-09
To the OP. I think it usually makes sense to use the DE which has most of the apps you prefer. If you prefer gnome/gtk apps use gnome or xfce, if you mostly use kde apps use KDE. Both DEs basically do the same thing ie sit in the background while you use applications. Choosing one over the other because of default colour schemes or toolbar layout would be a bit silly imho.

KDE can certainly be heavily customised to pretty much whatever you want. I have attached a screenshot of my current layout which is quite close to gnome although I have the top panel on autohide. I started with two panels on KDE, then went to one like windows and am now back with two. I had one panel down the side of my screen on my latop as it seemed to suit the widescreen format better. KDE probably takes more effort to customise than gnome but you can probably do more with it.

I am one of those people who loves Konq. My major dislike of Gnome is Nautilus. I think it would be better if they stripped out the web browser side and built it into a seperate khtml browser, I use Opera myself, and the customisation could be made easier. However, as a file browser it is suberb once you get to know it. Tabs in a file browser are incredibably useful. I find it really quick being able to view files in konq rather than opening a seperate app if you just want to view one file. You can turn off that by going to Settings > configure > file associations and then click on the type of file ie 'images' and you can set it to use seperate viewer or embedded. You can set this for individual file types as well.

If you prefer a simplistic windows explorer clone style of file manager like Nautilus then you can get deb packages for Dolphin that work on Kubuntu. Look on the Dolphin site or kde-apps.

ps Try out basket and kdissert for two more great kde apps if you haven't already, and kmymoney, digikam etc etc

For some reason I have actually been thinking of going the other way and trying gnome again or probably xfce.

---

### Post by aysiu on 2007-03-09
> **DrainBead said:**
> Well that is only because he hates KDE and lies his **** off about it without even having used it. That's not entirely true. ComplexNumber is certainly biased against KDE but has also used it. Used it extensively? Not sure. Used it? Definitely.

---

### Post by ComplexNumber on 2007-03-09
> **bailout said:**
> There are actually 8 icon sizes in kubuntu and they don't look pixelated to me ;) But I am sure you will still try to argue that you are right, that there are only 2 sizes and KDE is terrible in evey way :D
can you show a screenshot of what the icons look like on the desktop after you have selected 128, please?
do they look anything like the stretched svg icon shown in the screenshot below? note just how wonderfully smooth it is. 
my last memory of using kde was kde 3.5.5 on PCLinuxOS, and i certainly don't remember there being more than 2 sizes. some of them were 32 and 64, whilst others were 16 and 32. i had to keep all icons small because whenever they went over 64, they all became pixalated.


also, do you know of any  links to any kde svg icon set  that can be used on kde without conversion to png?

---

### Post by FyreBrand on 2007-03-09
> **ComplexNumber said:**
> can you show a screenshot of what the icons look like on the desktop after you have selected 128, please?
do they look anything like the stretched svg icon shown in the screenshot below? note just how wonderfully smooth it is. 
my last memory of using kde was kde 3.5.5 on PCLinuxOS, and i certainly don't remember there being more than 2 sizes. some of them were 32 and 64, whilst others were 16 and 32. i had to keep all icons small because whenever they went over 64, they all became pixalated.


also, do you know of any  links to any kde svg icon set  that can be used on kde without conversion to png?

Here is a screenshot of Konqueror on the desktop at 128.  Note just how wonderfully smooth it is.  Why must you troll every single KDE thread and say negative stuff?  Doesn't it make your day to derail a thread?

Edit:  Added complete screen as requested.
[[IMG]http://img69.imageshack.us/img69/4412/kubuntudesktop128xn4.th.png[/IMG]](http://img69.imageshack.us/my.php?image=kubuntudesktop128xn4.png)

---

### Post by GeneralZod on 2007-03-09
> **ComplexNumber said:**
> can you show a screenshot of what the icons look like on the desktop after you have selected 128, please?


Excuse wallpaper, please:

[http://etotheipiplusone.com/kde-desktop-icon-128.png](http://etotheipiplusone.com/kde-desktop-icon-128.png)

---

### Post by DrainBead on 2007-03-09
> **aysiu said:**
> That's not entirely true. ComplexNumber is certainly biased against KDE but has also used it. Used it extensively? Not sure. Used it? Definitely.

Well that makes him narrow minded

---

### Post by maagimies on 2007-03-09
> **FyreBrand said:**
> Here is a screenshot of Konqueror on the desktop at 128.  Note just how wonderfully smooth it is.  Why must you troll every single KDE thread and say negative stuff?  Doesn't it make your day to derail a thread?And yet KDE with all it's configurability doesn't allow you to pick a single icon and resize it, leaving everything else the same. :KS

---

### Post by mips on 2007-03-09
It is best to ignore ComplexNumber. No matter what you say or what evidence you present he will not believe you and will always claim otherwise.

The sad thing is he is spreading FUD and people that do not know any better would probably believe him seeing his forum position would make him sound all the more believable.

Next time he pipes up about how bad KDE is just reply with "Yes master ComplexNumber, ruler of all that is Gnome. We have strayed from the path of righteousness which is Gnome and been overcome by the darkness which is KDE. We beg your humble forgiveness and seek absolution from our sins"

He will never admit he is wrong, leave him be as you are wasting your time.

---

### Post by bailout on 2007-03-09
> **mips said:**
> It is best to ignore ComplexNumber. No matter what you say or what evidence you present he will not believe you and will always claim otherwise.

The sad thing is he is spreading FUD and people that do not know any better would probably believe him seeing his forum position would make him sound all the more believable.

Next time he pipes up about how bad KDE is just reply with "Yes master ComplexNumber, ruler of all that is Gnome. We have strayed from the path of righteousness which is Gnome and been overcome by the darkness which is KDE. We beg your humble forgiveness and seek absolution from our sins"

He will never admit he is wrong, leave him be as you are wasting your time.

The problem with just ignoring him is that there are many people on here who have come to linux through ubuntu and hence have no direct experience of kde. If the FUD of CN and others isn't challenged then those noobs who might like to try kde are less likely to due to the misinformation that ubuntuforums promote.

I often think that linux would be stronger if there was just one main DE but ever since the creation of gnome we have to accept this split into two camps. I just don't see the nee for the antipathy from zealots like CN. Unfortunately these forums have always condoned this rather than stopping it.

---

### Post by Erunno on 2007-03-09
:popcorn: > **GeneralZod said:**
> Excuse wallpaper, please:

[http://etotheipiplusone.com/kde-desktop-icon-128.png](http://etotheipiplusone.com/kde-desktop-icon-128.png)

This does look suspiciously like Oxygen ;-)

Customizing KDE to look like GNOME might take some time as beside the desktop itself most people coming from GNOME will probably want to adjust icons and toolbars in the applications as well. So better save that .kde profile after being done. Other then that the human icon theme for KDE doesn't match all of KDE's icons so there will probably be icons left from Crystal SVG which might look a little inhomogeneous.

EDIT:

There's a lot of misinformation about KDE it seems. I'm not actually sure where it all started but by now it seems most people just picked up some phrases on the internet and repeat them without concrete evidence. Oh boy, I can't wait until KDE 4.0 is released and all the doomsayers can pick on it because it doesn't implement all promised features yet.

---

### Post by ComplexNumber on 2007-03-09
> **FyreBrand said:**
> Here is a screenshot of Konqueror on the desktop at 128.  Note just how wonderfully smooth it is.  Why must you troll every single KDE thread and say negative stuff?  Doesn't it make your day to derail a thread?
instead of just showing a single icon, can you show the whole desktop(and not a kde 4 mockup)? i wonder why you only showed a single icon instead of posting the whole deskop :confused:.  hmmmm. people want to see what the 128 size icons look like in their proper context.
how about posting a link to ANY kde icon set on kde-look that uses svg's?




** mips,FyreBrand,bailout**
less of the attacks if you don't mind. i don't know what it is about some people such as yourselves who label others as trolls if they dare to mention any of the  negative aspects about their beloved desktop. all 3 of you are well known on these forums for that.

---

### Post by mips on 2007-03-09
> **ComplexNumber said:**
> instead of just showing a single icon, can you show the whole desktop(and not a kde 4 mockup)? i wonder why you only showed a single icon instead of posting the whole deskop :confused:.  hmmmm. people want to see what the 128 size icons look like in their proper context.
how about posting a link to ANY kde icon set on kde-look that uses svg's?

First you argue that you there are only two sizes available. Now you want SVG's. You lost the first argument now you keep moving the goalposts.

SVG Icon Themes:
[http://www.kde-look.org/content/show.php?content=8341](http://www.kde-look.org/content/show.php?content=8341)
[http://www.kde-look.org/content/show.php?content=17362](http://www.kde-look.org/content/show.php?content=17362)
[http://www.kde-look.org/content/show.php?content=32288](http://www.kde-look.org/content/show.php?content=32288)
[http://www.kde-look.org/content/show.php?content=5358](http://www.kde-look.org/content/show.php?content=5358)
[http://www.kde-look.org/content/show.php?content=17158](http://www.kde-look.org/content/show.php?content=17158)

[http://wiki.kdenews.org/tiki-index.php?page=Icon+Guide](http://wiki.kdenews.org/tiki-index.php?page=Icon+Guide)

As you know (or not) many of the KDE Icon themes are svg icon themes and distributed as such. They are however converted into .png pixmaps of different sizes from 16-128

I have also attached four different icon themes that are currently available on my desktop that are of size 128. I left out the panels and rest of the desktop because I don't want to give away the new theme of the beta/rc distro I'm beta testing (some people wont be happy). They look pretty smooth to me.


> **ComplexNumber said:**
> 
** mips,FyreBrand,bailout**
less of the attacks if you don't mind. i don't know what it is about some people such as yourselves who label others as trolls if they dare to mention any of the  negative aspects about their beloved desktop. all 3 of you are well known on these forums for that.

tsk, tsk... Because people question you and refute what you say you call it attacks ? I never called you a troll, I said you were spreading FUD (I can quote you on your two icon sizes if you have forgotten). I'm not exactly a KDE fan boy either and believe people must use what they like. Do you actually have kde installed at the moment ? Well I have KDE, Gnome, Fluxbox, E16 and more, so much for my beloved desktop (people like us?). We should not be silent and let you spread wrong information. If you don't like it then send the infraction points my way, but you won't silence people that tell you 'you are wrong'.

---

### Post by ComplexNumber on 2007-03-09
[B]mips
[/B]i didn't ask for icon themes that merely have svg in the title. i meant actual svg icon themes like those that are available for gnome. > 
As you know (or not) many of the KDE Icon themes are svg icon themes and distributed as such. They are however converted into .png pixmaps of different sizes from 16-128exactly my point. kde can't handle svgs. thats why, on kde, all the particular icons themes use a build script to convert them (using inkscape as a dependency in some cases) to pngs. 
anyway, the person(ie DrainBead)  who originally stated the untruths and inaccurate information about dolphin, kde/gnome icon themes and other kde matters is no longer with us. isn't it funny how none of you labelled him as a troll, yet his posts contain no factually correct information whilst mine do. how odd :rolleyes:. 
case closed. 


and no, i don't have kde installed on this moment i time. i used kde from the late 1990's, but became tired of its quirks and disadvantages. i used it again for a few months recently, but nothing has changed (although i like the actual distro).
if you read what i said, i said  i am not aware of there being more than 2 sizes of icons available. i had virtually every icon theme from kde-look, but there were still only 2 sizes available in the kde control centre.

---

### Post by mips on 2007-03-09
> **ComplexNumber said:**
> [B]mips
[/B]i didn't ask for icon themes that merely have svg in the title. i meant actual svg icon themes like those that are available for gnome. exactly my point. kde can't handle svgs. thats why, on kde, all the particular icons themes use a build script to convert them (using inkscape as a dependency) to pngs. 
anyway, the person(ie DrainBead)  who originally stated the untruths and inaccurate information about dolphin, kde/gnome icon themes and other kde matters is no longer with us. isn't it funny how none of you labelled him as a troll, yet his posts contain no factually correct information whilst mine do. how odd :rolleyes:. 
case closed. 


and no, i don't have kde installed on this moment i time. i used kde from the late 1990's, but became tired of its quirks and disadvantages. i used it again for a few months recently, but nothing has changed (although i like the actual distro).
if you read what i said, i said  i am not aware of there being more than 2 sizes of icons available. i had virtually every icon theme from kde-look, but there were still only 2 sizes available in the kde control centre.

Technically speaking they are svg icon themes. KDE just can use them as svgs at this stage like I said. you did ask for any svg icon theme, " how about posting a link to ANY kde icon set on kde-look that uses svg's" Those icon sets use svg, but kde definately does not. You should have phrased your request better. What you meant and what you said are two different things.

Are you satisfied though that there are more than two sizes for desktop icons and they are smooth in appearance.

I'm very happy to acknowledge that KDE (not kde4) does not support svgs
I'm also happy to acknowledge that there are svg icon themes for KDE.
And I stand by my statement that there are more than two sizes of desktop icons available and that they are smooth in appearance.

As for BrainDead, I don't pay much attention to him. Been observing him for the last2-3 days and could see he was headed for burnt beans in a hurry. Actually considered reporting him but he was doing a pretty good job on his own.

---

### Post by ComplexNumber on 2007-03-09
**mips**
case closed. time to move on.

---

### Post by mips on 2007-03-09
Just like that :rolleyes:

I don't think it is wise to moderate and participate in the same thread for obvious reasons.

---

### Post by FyreBrand on 2007-03-09
> **ComplexNumber said:**
> instead of just showing a single icon, can you show the whole desktop(and not a kde 4 mockup)? i wonder why you only showed a single icon instead of posting the whole deskop :confused:.  hmmmm. people want to see what the 128 size icons look like in their proper context.
how about posting a link to ANY kde icon set on kde-look that uses svg's?




** mips,FyreBrand,bailout**
less of the attacks if you don't mind.** i don't know what it is about some people such as yourselves who label others as trolls if they dare to mention any of the  negative aspects about their beloved desktop**. all 3 of you are well known on these forums for that.It's not about mentioning drawbacks.  It's about changing the subject, derailing the thread, and using the red name tag to moderate your position in a discussion.  It's software that I like to use it's not my beloved anything.  I use XFCE as well.

I  cropped the screenshot to keep the file size down.  Here's a full screenshot.
[[IMG]http://img69.imageshack.us/img69/4412/kubuntudesktop128xn4.th.png[/IMG]](http://img69.imageshack.us/my.php?image=kubuntudesktop128xn4.png)

---

### Post by ComplexNumber on 2007-03-09
**FyreBrand**
its a bit too late for that screenshot now. see my 2nd to last post.

---

### Post by FyreBrand on 2007-03-09
I don't get it?  Why is it too late to look at a screen shot?

---

### Post by TheMono on 2007-03-09
Wow.... I didn't mean to start this lol.

To whoever it was posted a screenshot of their desktop with a black and white photo of seagulls - I love the way your Konqueror looks. I think I could handle using it with all its extra features if it didn't have those tabs down the side, etc, and try and shove the features down my throat lol.

You've given me hope that KDE can look good.... I'll start having a go with this.

---

### Post by maniacmusician on 2007-03-09
> **TheMono said:**
> Wow.... I didn't mean to start this lol.

To whoever it was posted a screenshot of their desktop with a black and white photo of seagulls - I love the way your Konqueror looks. I think I could handle using it with all its extra features if it didn't have those tabs down the side, etc, and try and shove the features down my throat lol.

You've given me hope that KDE can look good.... I'll start having a go with this.
yup, it's all configurable. looking good is just a relative term. For instance, I think that konqueror, with emerald window borders provided by beryl, the tree view down the side, and the universal sidebar, looks great. It gives me quick access to a bunch of features that I actually use.

I like Gnome too, and I use it in a VM sometimes, but I guess I'm just more comfortable with KDE. 

Anyways, if you really want to get the hang of customizing it, then use KControl rather than the "system settings" thing that the Kubuntu people have put in there. You can either start kcontrol via a terminal or the Alt + F2 Dialog, or you can add it's menu to the default KMenu (Right click on a Panel > "Menus" tab > Tick off te "Settings" menu > Hit apply) so that it'll stick all the settings in there.

---

### Post by qalimas on 2007-03-09
To get those tabs off of the left and right, just hit F9 =/

Not complicated.

---

### Post by TheMono on 2007-03-09
That control center is much better. MUCH better.

OK, so I'm writing this now from my Kubunut-desktop. Katapult is great, I'm liking most of KDE, and my GNOME apps still look great in it with the qt engine.

My only problems now are: 
In Konqueror, I can handle it without all the rubbish on the let (ie, hit F9). How can I make that default though, as it reverts back with each new instance?
Secondly, Beryl works oddly. After closing some menu's, it leaves a glow outline of the menu that didn't happen with GNOME... I have to reload Beryl to get them to go, and then they start coming back when I use menus again.

---

### Post by maniacmusician on 2007-03-09
> **TheMono said:**
> That control center is much better. MUCH better.

OK, so I'm writing this now from my Kubunut-desktop. Katapult is great, I'm liking most of KDE, and my GNOME apps still look great in it with the qt engine.

My only problems now are: 
In Konqueror, I can handle it without all the rubbish on the let (ie, hit F9). How can I make that default though, as it reverts back with each new instance?
Secondly, Beryl works oddly. After closing some menu's, it leaves a glow outline of the menu that didn't happen with GNOME... I have to reload Beryl to get them to go, and then they start coming back when I use menus again.
To save that, after hitting F9, go to Settings > Save View Profile "File Management".

As for the beryl thing; I dunno, that's never happened to me. It could just be a beryl setting somewhere in BSM. 

If you can't figure it out, check with the guys in #beryl on freenode. (irc)

edit: and yes, the control center is definitely way better than the System Settings rubbish.

---

### Post by TheMono on 2007-03-09
Will jump on to the Beryl IRC now. And thanks, that change with Konqueror worked a treat. Seems odd behaviour though, but I can see its purpose now.

---

### Post by maniacmusician on 2007-03-09
Yeah, Konqueror is a tricky piece of software. the KDE dev's haven't been able to find the right balance between it's web browsing and file-managing capabilties.

It's actually a pretty good idea for Dolphin to take over, but Dolphin is not ready yet. Though it makes a good file manager, it's way too "simple" at the moment. KDE is really all about functionality, so Dolphin still needs some advanced features. Some of those are being added for KDE4 (like the "tree" view has already been inplemented), and I'm sure they will all be added in time. Basically, Dolphin is going to end up being like Konqueror minus some web browsing capabilities and plus some better file-managing capabilities.

Does anyone know if Dolphin takes advantage of KParts and KIOslaves yet? That'll probably be the final step in getting it ready for KDE4, I suppose.

---

### Post by TheMono on 2007-03-09
OK, to update, now that I am getting in to KDE, I am liking it. I still can't figure out how to theme it properly, but I'm sure that will come. I have no doubt that people will find this odd, but I can't ditch evolution. That is the only Gnome app I'm keeping round at the moment...

Lets see how this all goes.

---

### Post by maniacmusician on 2007-03-09
> **TheMono said:**
> OK, to update, now that I am getting in to KDE, I am liking it. I still can't figure out how to theme it properly, but I'm sure that will come. I have no doubt that people will find this odd, but I can't ditch evolution. That is the only Gnome app I'm keeping round at the moment...

Lets see how this all goes.
You're right, it does sound odd :) Evolution is one of the few Gnome apps that I actually don't like.

As for theming KDE, it is definitely harder than theming Gnome, which is regretful. If you want native KWin themes, you go to KDE-Look.org and download them. Bad part; most of them have to be compiled. It's annoying for sure. I don't have to worry about that anymore (I use Beryl + Emerald), but for people that don't use Beryl, it is a major annoyance.

I'm hoping this gets addressed in KDE4.

---

### Post by GeneralZod on 2007-03-10
> **maniacmusician said:**
> 
Does anyone know if Dolphin takes advantage of KParts and KIOslaves yet? That'll probably be the final step in getting it ready for KDE4, I suppose.

KIOslaves *should* be a definite (even KolourPaint supports KIOslaves!) but KParts is less likely, as it will simply turn into Konqueror again ;)

---

### Post by maniacmusician on 2007-03-10
> **GeneralZod said:**
> KIOslaves *should* be a definite (even KolourPaint supports KIOslaves!) but KParts is less likely, as it will simply turn into Konqueror again ;)
well the reason that Konqueror didn't work well was because it couldn't properly manage both file management and web browsing at the same time; KParts certainly doesn't mean the same thing. 

KParts provide really great functionality...for instance, KPDF makes a brilliant KPart because most of the functionality is right there in the main UI, so there's nothing missing from it's KPart version. I'd be kind of dissapointed if we lost the functionality of KParts; I think it's been one of the most innovative and flexible tools I've seen to date.

---

### Post by bailout on 2007-03-13
> **TheMono said:**
> Wow.... I didn't mean to start this lol.

To whoever it was posted a screenshot of their desktop with a black and white photo of seagulls - I love the way your Konqueror looks. I think I could handle using it with all its extra features if it didn't have those tabs down the side, etc, and try and shove the features down my throat lol.

You've given me hope that KDE can look good.... I'll start having a go with this.

Glad you liked the screenshot and that it has inspired you to keep trying with kde and konq. It sounds as if you are doing nicely sorting it out now but if you have questions about my setup just ask. Iam not an expert on kde or konq by any means but I may type out some of the tips I have picked up for konq if I have time. Being more complex than the explorer/nautilus type of file managers it does take a while to learn how to get the most out of it.

In general when 'theming' kde I think you are better off just altering aspects of the desktop yourself rather than looking for a theme package that does it all for you as I think gnome does it. If you want different colours just change them, set the toolbars/menus as you want them, install an icon set that ou like etc.

Secondly, don't try and mimic gnome exactly. This is no different to someone from windows trying to get linux to look and act the same as windows. KDE isn't gnome so you will have to learn some new things even though you can quite easily mimic much of gnome's layout.

---

### Post by TheMono on 2007-03-13
No, I'm not trying to mimic GNOME exactly, just slightly lol.

I've got KDE working well now, and I'm staying. I installed the Kickoff menu which is far superior to the original K menu. I've put a top panel on each of my monitors with a task list. I've managed to transfer everything from Evolution to Kontact. I'm really happy with how it has turned out. Just a few little tweaks made it so much more usable!

Especially figuring out how to force Konqueror NOT to open ANYTHING other than folders!

---

### Post by maniacmusician on 2007-03-13
> **TheMono said:**
> No, I'm not trying to mimic GNOME exactly, just slightly lol.

I've got KDE working well now, and I'm staying. I installed the Kickoff menu which is far superior to the original K menu. I've put a top panel on each of my monitors with a task list. I've managed to transfer everything from Evolution to Kontact. I'm really happy with how it has turned out. Just a few little tweaks made it so much more usable!

Especially figuring out how to force Konqueror NOT to open ANYTHING other than folders!
and how did you do that? I want to tuck that away for future reference.

It's probably really simple, like going to the File Manager option in KControl or something, but I've never tried. So, how'd you do it?

---

### Post by TheMono on 2007-03-14
For the file type you want (in this case PDF):

Konqueror > Settings > Configure Konqueror

Select the File Associations tab.

Select Applications > PDF from the tree.

Go to the "Embedding" tab.

Select "Show file in seperate viewer" rather than show embedded.

Now Konqueror stays the hell away from my files lol.

---

### Post by maniacmusician on 2007-03-16
> **TheMono said:**
> For the file type you want (in this case PDF):

Konqueror > Settings > Configure Konqueror

Select the File Associations tab.

Select Applications > PDF from the tree.

Go to the "Embedding" tab.

Select "Show file in seperate viewer" rather than show embedded.

Now Konqueror stays the hell away from my files lol.
haha nice.

Also, where'd you get the kickoff menu from? I didn't think Ubuntu had that yet.

---

### Post by mips on 2007-03-16
> **maniacmusician said:**
> haha nice.

Also, where'd you get the kickoff menu from? I didn't think Ubuntu had that yet.

[http://www.ubuntuforums.org/showthread.php?t=280552](http://www.ubuntuforums.org/showthread.php?t=280552)
[http://www.ubuntuforums.org/showthread.php?t=261839](http://www.ubuntuforums.org/showthread.php?t=261839)

---

### Post by maniacmusician on 2007-03-16
> **mips said:**
> [http://www.ubuntuforums.org/showthread.php?t=280552](http://www.ubuntuforums.org/showthread.php?t=280552)
[http://www.ubuntuforums.org/showthread.php?t=261839](http://www.ubuntuforums.org/showthread.php?t=261839)
yeah, found those threads after I posted. It's in trevino's repos apparently but I'm using Feisty. I wonder why the MOTU didn't bother packaging it? It's a pretty sensational package.

---

### Post by FyreBrand on 2007-03-16
> **maniacmusician said:**
> yeah, found those threads after I posted. It's in trevino's repos apparently but I'm using Feisty. I wonder why the MOTU didn't bother packaging it? It's a pretty sensational package.I agree.  When I was taking Sabayon for a test spin that is one graphic feature that really stood out to me.  I like it.

---

### Post by mips on 2007-03-16
> **FyreBrand said:**
> I agree.  When I was taking Sabayon for a test spin that is one graphic feature that really stood out to me.  I like it.

lol, it was the first thing I disabled :)

---

### Post by FyreBrand on 2007-03-16
Haha.  I have a Gentoo friend he said the same thing.  He like Sabayon and thinks it's a good idea.  He said Kickoff is annoying.  He's been using some other type of dock I forgot what it's called.

---

### Post by maniacmusician on 2007-03-16
> **mips said:**
> lol, it was the first thing I disabled :)
I actually just tried it and I have to agree. I don't really like it. I suppose it's useful for some people, but it's not as quick to navigate as the normal KMenu. Not even close. 

But it's still a "sensational" package in the sense that a lot of people want to try it, so I think it should've been packaged for Feisty.

---

### Post by mips on 2007-03-16
> **maniacmusician said:**
> I actually just tried it and I have to agree. I don't really like it. I suppose it's useful for some people, but it's not as quick to navigate as the normal KMenu. Not even close. 


Yeah, pretty but nearly as efficient as the old Kmenu.

I had the same initial eagerness as you to be honest, 5mins into my experience with kickoff i though to myself it's a load of junk and switched back.

---

### Post by maniacmusician on 2007-03-16
> **mips said:**
> Yeah, pretty but nearly as efficient as the old Kmenu.

I had the same initial eagerness as you to be honest, 5mins into my experience with kickoff i though to myself it's a load of junk and switched back.
hey, at least you lasted 5 minutes :)

I'd like some sort of a change to the default KMenu, because I'm sure it can be improved. However, Kickoff was not the improvement I was looking for.

---

### Post by TheMono on 2007-03-16
Kickoff isn't perfect, but is a damn sight better than the normal K menu for me. 

I agree, not seeing it in Feisty is a travesty. But I also agree that it should not be default. It does rather take a little getting used to. Given I was using USP in Gnome, Kickoff felt a lot more natural to me. I love the favourites list, and I love being able to find a program by typing the first couple of letters of its name.

---

### Post by maniacmusician on 2007-03-17
> **TheMono said:**
>  I love the favourites list, and I love being able to find a program by typing the first couple of letters of its name.

The favorites list is just a list of recent documents right? You can add that to the Kmenu if you want it.

As for finding programs, use katapult. Just press Alt + Space, and a dialog comes up. type in a few letters and hit enter to open the program.

I'm not bashing Kickoff, it just slowed me down. I didn't see anything that I wanted that I could get with the KMenu.

---

### Post by TheMono on 2007-03-18
No, by the favourites list I mean how when you open Kickoff it just lists whichever programs you tell it to list as your favourites. Then, if you need any other programs, you just type a couple of letters and it does the same as Katapult does.

Having said that, Alt+Space doesn't work for me.

---

### Post by maniacmusician on 2007-03-18
> **TheMono said:**
> No, by the favourites list I mean how when you open Kickoff it just lists whichever programs you tell it to list as your favourites. Then, if you need any other programs, you just type a couple of letters and it does the same as Katapult does.

Having said that, Alt+Space doesn't work for me.
Ah, favorite programs; yeah Kmenu has those as well. You can have it display the most recently used or the most often used. 

Weird that Katapult is not enabled for you by default; it always has been on my installs. If you want to enable it yourself, it's in Menu > Utilities.

while we're at it, I'd also like to add that you should try out yakuake. It's in the repos. It's a drop-down terminal that's really really useful.

---

### Post by Kingsley on 2007-03-18
I found myself in your shoes about 5 months ago until I made the complete switch to KDE. I admit the default settings on Kubuntu are annoying - single click, military time clock, default konqueror web browser - but once you set things through System Settings and apt-get to your liking, it's all good. In my opinion, customization is the only thing lacking in KDE. I was able to pimp out my panel so much in GNOME but I guess I'm over that now.

---

### Post by TheMono on 2007-03-18
I couldn't agree more, Kingsley. That's the only thing I'm missing now, the ability to mess round with things as much as in Gnome.

And thanks for the Yakuake tip... I'll fire that up now.

---

### Post by cowlip on 2007-03-18
Tilda is another dropdown terminal that's useful as well (gtk though)

---

### Post by TheMono on 2007-03-19
I had used Tilda before, on Gnome, but it never worked for me for some reason. I have to say, Yakuake is a heck of a lot better.

---

### Post by finferflu on 2007-03-19
The only problem with Yakuake is that sloooows your system. I used to be addicted to Yakuake, and it was perfect, then I noticed how slow my KDE was going, tried to close Yakuake and saw a considerable improvement in speed. I had to give it up :(

---

### Post by TheMono on 2007-03-19
Really? I haven't noticed. Having said that, I note you are using Xubuntu, so you are probably quite sensitive to speed lol!

I just got a new machine, (yay Core2!), so I feel like I have power to burn at the moment...

---

### Post by awakatanka on 2007-03-19
> **maniacmusician said:**
> Ah, favorite programs; yeah Kmenu has those as well. You can have it display the most recently used or the most often used. 

.In kickoff you can put youre own fav prg in the list, you can control what prg needs to be in there. In kicker it isn't possible, it only show most used our recently used.

If you organize fav in kickoff a bit it can be faster then kicker.

first thought was also disable it, but after a few tips it can work faster.

---

### Post by mand0 on 2007-03-19
> **karellen said:**
> what is the problem about running native kde applications in gnome? I do that with k3b, ktorrent, quanta plus, konversation...and they look just fine. even more, I like how they look and integrate :)

I tend to do this too. Is it really that much slower to do run native kde applications in gnome? (Honest question)

---

### Post by finferflu on 2007-03-19
> **TheMono said:**
> Really? I haven't noticed. Having said that, I note you are using Xubuntu, so you are probably quite sensitive to speed lol!

I just got a new machine, (yay Core2!), so I feel like I have power to burn at the moment...

Not that my machine is that slow (it's a P4 2.6 GHz), but yes, I'm quite sensitive to speed. I can't stand waiting for more than a couple of seconds for an application to at least turn up, when I start it up. I call that productivity. Xubuntu, apart from being very fast, is amazingly stable, I'm impressed, but I don't want to get off topic ;)

---

### Post by TheMono on 2007-03-20
Don't worry, the topic is wandering a bit anyway lol. I used Xubuntu for a while and like it, but it just didn't grab me like GNOME and now KDE.

mand0, it is basically no slower to run them in GNOME instead of KDE. The problem is you load up a whole lot of extra libraries when you run both GNOME and KDE apps, chewing up more RAM.

Having said that, it is slower to open a KDE app on GNOME, because it has to load up all those libraries first. But your second KDE apps is fairly normal to start.

---

### Post by maniacmusician on 2007-03-20
> **TheMono said:**
> Don't worry, the topic is wandering a bit anyway lol. I used Xubuntu for a while and like it, but it just didn't grab me like GNOME and now KDE.

mand0, it is basically no slower to run them in GNOME instead of KDE. The problem is you load up a whole lot of extra libraries when you run both GNOME and KDE apps, chewing up more RAM.

Having said that, it is slower to open a KDE app on GNOME, because it has to load up all those libraries first. But your second KDE apps is fairly normal to start.
the reason I didn't like XFCE with Ubuntu was because it was basically a GNOME clone, which I thought was ridiculous. Once you set it back to it's original configuration, it's a little easier to use because it feels "right". 

There's also the fact that it doesn't have many options or any peripheral-managing tools to speak of yet.

---

### Post by finferflu on 2007-03-22
> **maniacmusician said:**
> the reason I didn't like XFCE with Ubuntu was because it was basically a GNOME clone, which I thought was ridiculous. Once you set it back to it's original configuration, it's a little easier to use because it feels "right". 

There's also the fact that it doesn't have many options or any peripheral-managing tools to speak of yet.
That's exactly the reason I liked it. I like the tidiness of Gnome (even though I don't particularly enjoy its look and feel), and most of the best supported applications in Ubuntu are for Gnome, and thanks to its Gnome-compatibility I can run them on Xfce with no problems. I guess I could also use the Gnome peripheral-managing tools, even though I haven't needed yet, since everything works automatically. And the best thing is stability, really. If on Gnome an application freezes or locks up, it almost takes down the whole system with neverending loading, and you can't do anything but wait or restart the session. On Xfce instead, if that happens, the application stays isolated and you can still move around, spin the cube (if you have Beryl like me), open other applications, as if nothing happened, and finally run xkill (with CTRL+ALT+ESC) and kill it straight away. Amazing.

---

### Post by maniacmusician on 2007-03-22
> **finferflu said:**
> That's exactly the reason I liked it. I like the tidiness of Gnome (even though I don't particularly enjoy its look and feel), and most of the best supported applications in Ubuntu are for Gnome, and thanks to its Gnome-compatibility I can run them on Xfce with no problems. I guess I could also use the Gnome peripheral-managing tools, even though I haven't needed yet, since everything works automatically. And the best thing is stability, really. If on Gnome an application freezes or locks up, it almost takes down the whole system with neverending loading, and you can't do anything but wait or restart the session. On Xfce instead, if that happens, the application stays isolated and you can still move around, spin the cube (if you have Beryl like me), open other applications, as if nothing happened, and finally run xkill (with CTRL+ALT+ESC) and kill it straight away. Amazing.
yes I agree, Xubuntu is a pretty good system

I still disagree about it's cosmetics though. I think the choice to make it look like GNOME should be left to the **user**. The default should stay true to XFCE, just as Ubuntu and Kubuntu do for GNOME and KDE respectively.

---

### Post by TheMono on 2007-03-23
What do you mean by stay true to XFCE? I'm not familiar with the "standard" XFCE look...

---

### Post by maniacmusician on 2007-03-23
> **TheMono said:**
> What do you mean by stay true to XFCE? I'm not familiar with the "standard" XFCE look...
I guess this is a typical screenshot; [http://www.linuxbog.dk/wm/wm/xfce.png](http://www.linuxbog.dk/wm/wm/xfce.png)  The focus on it is really supposed to be sort of minimalistic, but still robust. So, one panel, with launchers, workspace views, etc. Supposed to use the right-click desktop to launch applications. 

You can priobably find better screenshots if you do a google image search.

---

### Post by TheMono on 2007-03-23
I absolutely love the right click on the desktop to bring up the menu. It's a brilliant idea - on that note, anyone know how to make KDE do this? That would be useful.

---

### Post by maniacmusician on 2007-03-23
yeah there's definitely a way. I'm not at home right now, so I don't remember. I'll get to a Linux computer within a couple of hours and post back.

I have a feeling it's in "Right Click on Desktop > Configure Desktop" In that dialog, there are some right click options, I think, that should give you what you want. I had that for a while, but then I stopped using the menu (used katapult and alt+f2 instead) so I replaced it with more useful functions.

---

### Post by mips on 2007-03-23
> **maniacmusician said:**
> 
I have a feeling it's in "Right Click on Desktop > Configure Desktop" In that dialog, there are some right click options, I think, that should give you what you want.

You are heading in the right direction ;)

Right Click on Desktop  -> Configure Desktop  -> Behaviour -> Mouse Button Actions and pick the action you want from the drop down for the mouse button you prefer. Application menu is one of the drop down options.

---

### Post by maniacmusician on 2007-03-23
:) thanks mips. It's way too hard to remember all that from memory (for me at least). that's a pretty cool feature. I would use it except for the fact that 1) I don't really use menus much and 2) My desktop is always covered with windows.

---

### Post by FyreBrand on 2007-03-23
I'm liking katapult more and more.  It does some really cool things I didn't realize before like call the calculator to evaluate expressions or find bookmarked pages.

I didn't realize the mouse was that configurable.  KDE has an amazing amount of functionality built in.

---

### Post by TheMono on 2007-03-23
Here's a tip: If you install and use the Kickoff menu, then you can't use right click on desktop to bring up the K menu....

Oh well, I can accept that missing this is really more my fault than KDE's lol.

---

### Post by finferflu on 2007-03-24
deleted.

---

### Post by mexlinux on 2007-04-21
> **kragen said:**
> To respond to the intial post:

...sometimes I feel like some gtk apps lack features that qt apps have....

I find it really fustrating, both desktop enviroments are very good, if you consider the total hours of development which has gone into each, and then combined them into one, the result would be a far superior desktop enviroment. As it is, just about everything is being developed twice, in slightly different ways each time :(

I agree, I don't think this may ever happen, but both desktops might unite in some way (I don't know how, since there are now too mature), but you can have a complete configuration options like kde does, but have the defaults as gnome does, and somewhere in kcontrol have an option SHOW ADVANCED OPTION, then you can switch from the "feature lack version" to the "over configurated version".

That will unify and both user bases basic, and advanced will have the same desktop.

---

### Post by igknighted on 2007-04-21
> **mexlinux said:**
> I agree, I don't think this may ever happen, but both desktops might unite in some way (I don't know how, since there are now too mature), but you can have a complete configuration options like kde does, but have the defaults as gnome does, and somewhere in kcontrol have an option SHOW ADVANCED OPTION, then you can switch from the "feature lack version" to the "over configurated version".

That will unify and both user bases basic, and advanced will have the same desktop.

See thats the thing... stuff isn't developed twice.  The gnome guys and KDE guys sit together at conferences and swap notes and help each other, then implement it their own way.  So its a really good, efficient system now.  Not everybody likes all the choice KDE gives them, and not everyone likes the simplified Gnome interface.  Having the option to use either makes Linux better, and as far as "double development" I think that largely this is a myth.

---

