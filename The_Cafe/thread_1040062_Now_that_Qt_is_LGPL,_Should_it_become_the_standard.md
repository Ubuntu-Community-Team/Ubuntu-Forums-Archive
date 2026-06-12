---
title: "Now that Qt is LGPL, Should it become the standard toolkit?"
date: 2009-01-15
forum: The Cafe
---

### Post by mangar on 2009-01-15
Currently, the duality of Gtk/ Qt is a real barrier to entry for Developing for Linux, since it forces the potential developer to peek a side in the "Desktop Environment wars", and thus fracturing the application base of Linux;

Since Qt is to be released as LGPL, ending (imho) the historical significance of Gtk, I believe that it is for the best interest of all the involved parties - Gnome, KDE, Qt Gtk, and the application developers, to transition away from Gtk to Qt, creating a strong foundation of standards from whom the FOSS community can draw.

In short - retire Gtk, standardize on Qt.

---

### Post by ghindo on 2009-01-15
Why is there all this talk about doing away with GTK+?  What's wrong with multiple toolkits?  What makes Qt better than GTK+?

---

### Post by samjh on 2009-01-15
I don't think GTK+ should be retired.  GTK+ is a GUI library.  Qt, on the other hand, is a comprehensive development framework, not just a GUI library.

You've also got the issue of development language.  Qt is C++-centric, while GTK+ is C-centric.  Sure, there are bindings for other languages, but the principal development language can affect choice too.

There is no reason why one library should win over the other.  Even their look-and-feel are compatible, now that theme engines exist to convert the L&F of Qt to GTK+ and vice versa (QGtkStyle will be a part of Qt4.5, so Qt apps will have native L&F on Gnome and other GTK-based desktop environments).

---

### Post by bufsabre666 on 2009-01-15
> **ghindo said:**
> Why is there all this talk about doing away with GTK+?  What's wrong with multiple toolkits?  What makes Qt better than GTK+?

i feel the same, they both serve a purpose. but if they wanted to make qt standard i wouldnt be against it for two reasons: 

1) it seems to be in more active development. (either that or gtk just doesnt like to announce every little update)

2) its always nice to standardize behind something, there are several areas i wish linux would just pick one thing and standardize behind it so that the standard one would get the funnel of development and become great (coughfilesystemscough)

---

### Post by HavocXphere on 2009-01-15
I think there are lots of areas were standardisation would do wonders. But its not going to happen imo. Some ppl won't touch gnome, others won't touch kde. Unless one of the camps gets a massive brainwave, its not going to happen. I guess therein lies the strength (and weakness) of *nix: variety and individualism.

/philosophical ramblings

> **bufsabre666 said:**
> there are several areas i wish linux would just pick one thing and standardize behind it so that the standard one would get the funnel of development and become great (coughfilesystemscough)
Audio

---

### Post by cb951303 on 2009-01-15
> **ghindo said:**
> Why is there all this talk about doing away with GTK+?  What's wrong with multiple toolkits?  What makes Qt better than GTK+?

Linux is surely about choices but there just some areas that needs to be standardized, like a main GUI toolkit. Didn't you ever see an application that you wished it was made with GTK? or vice versa? I know there are tools like QGTKStyle etc... and they work great but it's not just a problem of looks. Having one main toolkit would reduce the efforts, costs and bug hunting a *LOT* more easier. And it would eventually lead to better applications. 

There is nothing wrong with GTK and its a fine toolkit (actually it's more than a toolkit together with glibc). If we would ever need a GUI toolkit standardization, and had to choose between GTK and QT, why not choose QT?

---

### Post by Tibuda on 2009-01-15
The poll is biased towards Qt. Why only who votes for Gtk has to explain?

I'm not really a GUI programmer, but sometimes I write some little tools in wxWidgets because it looks native in both Windows and Gnome (I say Gnome because I never tested how they look in KDE). I like the idea to abstract the native API as wx does.

JOKE: Why not choose MS API as the standard? Everyone should write apps only for Windows and use Wine to run them.

---

### Post by jespdj on 2009-01-15
Just because Qt is becoming LGPL does not mean that GTK+ is obsolete now and should disappear. There's no reason why there should be only one GUI toolkit (and one desktop environment).

GTK+ should just continue to exist.

> **danielrmt said:**
> The poll is biased towards Qt. Why only who votes for Gtk has to explain?
I agree, the way it is worded is biased towards Qt.

Why do you think Qt should become the standard?

---

### Post by Keyper7 on 2009-01-15
> **danielrmt said:**
> The poll is biased towards Qt. Why only who votes for Gtk has to explain?

Because the main reason why Gnome was created and Gtk was popularized as a general-purpose GUI toolkit (instead of being just the GIMP toolkit) is now gone. Gtk has grown up much farther than being just a replacement, but now that Qt became LGPL this kind of questions are only natural. The poll is biased towards Qt because it's the direction that makes sense under the recent news. The OP didn't want to make the old, beaten-to-death "should a toolkit be the standard" poll, it's more like "in the light of recent news, what is your opinion?"

My personal opinion: competition is good. Several people were choosing Gtk mainly because of the licensing issues. Now that this is gone and the KDE4 userbase is growing, I expect many improvements in Gtk in a short time.

---

### Post by mangar on 2009-01-15
I agree as well, that this poll is biased toward Qt..
I've played a little with both toolkits, and Qt, from development POV, is, IMHO, much, much better: lower barrier to entry, better documentation, better API, more complete funtionality, better cross platform support (Gtk runs on other platform, but doesn't play well with the host operating system), larger more active development community, faster rate of evolution, etc.

I fail to see what Gtk does better / different enough to justify its continued existence, Other than two factors - existing application support, and the (now irrelevant) license.

This is not a Gnome Vs. Kde thing - personally, I find Gnome to be more usable than Kde.

---

### Post by jpeddicord on 2009-01-15
> **mangar said:**
> I agree as well, that this poll is biased toward Qt..
I've played a little with both toolkits, and Qt, from development POV, is, IMHO, much, much better: lower barrier to entry, better documentation, better API, more complete funtionality, better cross platform support (Gtk runs on other platform, but doesn't play well with the host operating system), larger more active development community, faster rate of evolution, etc.

I fail to see what Gtk does better / different enough to justify its continued existence, Other than two factors - existing application support, and the (now irrelevant) license.

This is not a Gnome Vs. Kde thing - personally, I find Gnome to be more usable than Kde.

I think it's already been pointed out:
[LIST]
[*]Qt is a whole application toolkit, while GTK+ is a minimalistic GUI toolkit
[*]Qt is C++ based, CTK+ is C (with other bindings)
[/LIST]

Even if it was desired, we can't just switch to another toolkit since many GNOME programs are strictly C and Qt wouldn't play too well without a middleware library.

---

### Post by Ub1476 on 2009-01-15
Well it will be interesting to see what the Gnome devs come up with for Gnome 3. They can either use QT, or write a new API for GTK. I don't see why they shouldn't use QT 4 when GTK 2 is gonna be abandoned anyway.

---

### Post by cb951303 on 2009-01-15
> **jacobmp92 said:**
> I think it's already been pointed out:
[LIST]
[*]Qt is a whole application toolkit, while GTK+ is a minimalistic GUI toolkit
[*]Qt is C++ based, CTK+ is C (with other bindings)
[/LIST]

Even if it was desired, we can't just switch to another toolkit since many GNOME programs are strictly C and Qt wouldn't play too well without a middleware library.

* GTK with glibc/gobject is at least as bloated as QT. There is nothing minimalistic about GTK
* OOP in GUI toolkits is a must have. C++ has native OO abilities whereas C doesn't and that's why GTK uses glibc/gobject (which is a runtime object system implementation) so I believe C++ is an advantage here

GTK3 will break the application compatibility anyway.

---

### Post by MaxIBoy on 2009-01-15
Gtk is worthwhile, simply because it gives developers an alternative toolkit. I prefer not to work with Qt, I like Gtk, and there are many who would agree with me. As far as I'm concerned, that's a more-than-sufficient reason to keep Gtk around.

---

### Post by smartboyathome on 2009-01-15
Ok, so perhaps we should get rid of Gentoo, Fedora, Opensuse, Arch, Linux Mint, and all the other distros, and just make one super distro. Then take away all desktop environments and just make one super desktop environment. Same with Office, same with Web Browser, same with... oh wait, how are we going to keep people from forking? We can't! As long as people use GTK+, it won't die, as someone will develop it and you can't stop that.

---

### Post by Kvark on 2009-01-15
As a Gnome user I'm a bit jealous of how great it seems KDE 4 will be when they've worked out the kinks. Qt and Plasma combined with Gnome's applications and HIG would be sweet. But as a programmer I realize that won't happen.

---

### Post by SomeGuyDude on 2009-01-15
> **smartboyathome said:**
> Ok, so perhaps we should get rid of Gentoo, Fedora, Opensuse, Arch, Linux Mint, and all the other distros, and just make one super distro. Then take away all desktop environments and just make one super desktop environment. Same with Office, same with Web Browser, same with... oh wait, how are we going to keep people from forking? We can't! As long as people use GTK+, it won't die, as someone will develop it and you can't stop that.

QFT

What's this ******** about eliminating alternatives? You know what, if I liked QT, I'd be using QT apps. One big reason I don't use KDE is I am not a fan of QT. I can't put my finger on it, I just don't like it. I have zero QT apps on my machine and that's not changing any time soon. Losing GTK would definitely annoy the hell outta me.

---

### Post by spupy on 2009-01-15
As someone pointed out, GTK won't die while there are people who use it and people who develop it.
On the other hand we must choose between "I don't want to switch development to Qt, I'm lazy and slow to change" and "Winning the battle at the desktop". Developers will certainly be against such standardization, but I think it will ultimately be for the better (if the new standard is well organized.)


Problem is, GTK themes owns Qt themes. :)

---

### Post by super breadfish on 2009-01-15
I honestly don't see the argument. KDE won't explode if you run a GTK+ app on it or vice versa.

Leave the fanboy stuff with little kids with game consoles.

---

### Post by spupy on 2009-01-15
> **super breadfish said:**
> I honestly don't see the argument. KDE won't explode if you run a GTK+ app on it or vice versa.

Leave the fanboy stuff with little kids with game consoles.

The problem is that they don't work together very good -> Desktop isn't consistent -> User is frustrated -> User leaves.

---

### Post by bufsabre666 on 2009-01-15
i am surprised how close this is 17 for, 16 against ATM. i was expecting it to be like 2 to 45

---

### Post by SomeGuyDude on 2009-01-15
> **super breadfish said:**
> I honestly don't see the argument. KDE won't explode if you run a GTK+ app on it or vice versa.

Leave the fanboy stuff with little kids with game consoles.

Unity. Drives me bonkers when I run something that doesn't use my GTK settings.

---

### Post by cb951303 on 2009-01-15
I don't think 'looks' is an argument here. QT is 100% capable of simulating GTK (QGTKStyle) thus it is at least as customizable as GTK.

---

### Post by Slug71 on 2009-01-15
> **bufsabre666 said:**
> i feel the same, they both serve a purpose. but if they wanted to make qt standard i wouldnt be against it for two reasons: 

1) it seems to be in more active development. (either that or gtk just doesnt like to announce every little update)

2) its always nice to standardize behind something, there are several areas i wish linux would just pick one thing and standardize behind it so that the standard one would get the funnel of development and become great (coughfilesystemscough)

Have to agree with number 2) here. Some standardization so that certain things can really excell would be nice. I think we'll start seeing more of this though. Specially when Jaunty gets Packagekit which is already used by Fedora, Super Ubuntu and Foresight Linux and is now Supported by Mandriva and OpenSuse. Hopefully the same will happen when 9.10 gets Plymouth and Login Experience.

As for the Filesystems though, hopefully we'll see that get cleaned up when Btrfs is out.

---

### Post by geoken on 2009-01-15
> **smartboyathome said:**
> Ok, so perhaps we should get rid of Gentoo, Fedora, Opensuse, Arch, Linux Mint, and all the other distros, and just make one super distro. Then take away all desktop environments and just make one super desktop environment. Same with Office, same with Web Browser, same with... oh wait, how are we going to keep people from forking? We can't! As long as people use GTK+, it won't die, as someone will develop it and you can't stop that.

We're talking about standardization, not killing.

You guys probably don't notice how lack of standardization hurts you because you obviously have no way of knowing when a developer considers Linux, then scratches that idea because he sees the landscape of api choices like a minefield.

For example, do you guys know that the creator of Braid wanted to make a Linux port. Here is one of the comments he made on his blog post about the matter;

"*It&#8217;s hard to get good communication with Linux users though, because there are a lot of options and no reliable information about them anywhere. (For example you change your mind about which API provides minimal latency in these last two comments. So as a third party who has no experience with either API, am I supposed to believe one conclusion or the other now? **Now multiply that by N thousand pundits and M APIs that play audio. It is a total mess.)***"

As of now it seems like he won't be going through with the project because he feels like the task of choosing suitable API's is greater than the actual porting of the game.

---

### Post by bufsabre666 on 2009-01-15
> **Slug71 said:**
> Have to agree with number 2) here. Some standardization so that certain things can really excell would be nice. I think we'll start seeing more of this though. Specially when Jaunty gets Packagekit which is already used by Fedora, Super Ubuntu and Foresight Linux and is now Supported by Mandriva and OpenSuse. Hopefully the same will happen when 9.10 gets Plymouth and Login Experience.

As for the Filesystems though, hopefully we'll see that get cleaned up when Btrfs is out.

thats pretty much what im aiming for, is univeral package installation, universal file system and universal sound system.

those are the things that definitely need to be combined

qt becoming standard would be nice but its not something that is a must, but if gnome was to do that now would be the time so theres time to transition before gnome3 even has a release schedule

---

### Post by phrostbyte on 2009-01-15
I think the people who keep making posts like this should go ahead and lead this development effort. Because I don't think they realize that going to Qt is basically like throwing away a decade year of progress on Gnome. It's not like there is some switch built into Gnome and a quick recompile does the trick here.

---

### Post by cb951303 on 2009-01-15
> **phrostbyte said:**
> I think the people who keep making posts like this should go ahead and lead this development effort. Because I don't think they realize that going to Qt is basically like throwing away a decade year of progress on Gnome. It's not like there is some switch built into Gnome and a quick recompile does the trick here.

And I think you should read about GNOME 3 and GTK 3
Gnome team already thinks about breaking backward compatibility which means a huge rewrite of lot of things. The question is, while at it, why not use QT4?

+1 for Geoken, very true statement.

---

### Post by mangar on 2009-01-15
I'll drop in another two cents:
1. In software development, Choice is good as long as the parts are interchangeable.

I'll explain:

If choosing a toolkit was purely a development choice, with no visible effect on the end user, than jolly good and all is well, and this whole argument is unnecessary.

Unfortunately, this is not the case. There are many incompatibilities between Qt and Gtk application interaction on almost any level (I'm mixing in Gnome and Kde, since those are the FOSS main application platforms): Incompatible HIGs, incompatible look and feel, incompatible soundsystems, incompatible OLE, drag and drop behavior, etc. 

Using Qt and Gtk applications together does not work well.

Some may claim that freedesktop.org is making progress toward unified user experience. Unfortunately, the current rate of progress is extremely slow, without many results (with some highly notable exceptions, such as dbus), and generally speaking will probably never be enough to allow for seamless user interaction with the system.

2. Gtk and Gnome are extremely short on man/woman-power - for an illustration, Nautilus is currently maintained by a single person -  and are currently using those limited resources to refactor the existing libraries and software. Since a large effort and and extensive rewrite are already planed and taking place, why not reduce the overhead of maintaining Gnome and it's applications by using a common, well maintained development platform? It can allow Gnome to focus on its strength, rather than try to rebuild the entire stack.

---

### Post by cardinals_fan on 2009-01-15
> **mangar said:**
> Currently, the duality of Gtk/ Qt is a real barrier to entry for Developing for Linux, since it forces the potential developer to peek a side in the "Desktop Environment wars", and thus fracturing the application base of Linux;

Since Qt is to be released as LGPL, ending (imho) the historical significance of Gtk, I believe that it is for the best interest of all the involved parties - Gnome, KDE, Qt Gtk, and the application developers, to transition away from Gtk to Qt, creating a strong foundation of standards from whom the FOSS community can draw.

In short - retire Gtk, standardize on Qt.
Write your next program in Qt then.  If it is genuinely the better choice, developers will choose it and GTK will die out.  Think of it as survival of the fittest.

---

### Post by Keyper7 on 2009-01-15
> **mangar said:**
> I'll drop in another two cents:
1. In software development, Choice is good as long as the parts are interchangeable.

Summed up my feelings quite well, thank you.

And to emphasize what's already been said: yes, standardization is NOT elimination. Quite the contrary: it's the opportunity of having more choices in the future.

---

### Post by mangar on 2009-01-15
@cardinals_fan
I'm fully intended to use Qt when version 4.5 is release.

Until than, I'm gauging opinion and making an argument.
FWIW I've made the following posts to ubuntu-brainstorm several months ago:

8.2008
[http://brainstorm.ubuntu.com/idea/12292/](http://brainstorm.ubuntu.com/idea/12292/)

6.2008
[http://brainstorm.ubuntu.com/idea/9833/](http://brainstorm.ubuntu.com/idea/9833/)

---

### Post by Slug71 on 2009-01-15
> **bufsabre666 said:**
> thats pretty much what im aiming for, is univeral package installation, universal file system and universal sound system.

those are the things that definitely need to be combined

qt becoming standard would be nice but its not something that is a must, but if gnome was to do that now would be the time so theres time to transition before gnome3 even has a release schedule

Well Packagekit is definitely a start as a frontend to Package installation which is coming soon in Jaunty.
As for sound. That too is coming with Jaunty. This just came in a few days ago.

[https://fedoraproject.org/wiki/Features/VolumeControl](https://fedoraproject.org/wiki/Features/VolumeControl)

Its not perfect yet but its a good start.

I think as far as the backend goes for package installation i think we may see Smart replace APT.

---

### Post by cardinals_fan on 2009-01-15
> **mangar said:**
> @cardinals_fan
I'm fully intended to use Qt when version 4.5 is release.

Good.  I personally feel that Qt 4 is superior to GTK, but these things should be allowed to work themselves out naturally.

---

### Post by phrostbyte on 2009-01-15
> **cb951303 said:**
> And I think you should read about GNOME 3 and GTK 3
Gnome team already thinks about breaking backward compatibility which means a huge rewrite of lot of things. The question is, while at it, why not use QT4?

+1 for Geoken, very true statement.

Go ahead and compare the APIs of GTK+ 2/3 and Qt for me. Thank you.

This is beyond ridiculousness.

---

### Post by geoken on 2009-01-15
> **cardinals_fan said:**
> Write your next program in Qt then.  If it is genuinely the better choice, developers will choose it and GTK will die out.  Think of it as survival of the fittest.

You have a good point, but the problem is that DE's throw a wrench into that plan.

I consider Dolphin to be the best file manager yet I still use Nautilus or Thunar because my DE of choice leaves me pre-disposed to using GTK apps, even in situations where (on technical merits alone) the Qt app is far superior.

---

### Post by cardinals_fan on 2009-01-15
> **geoken said:**
> You have a good point, but the problem is that DE's throw a wrench into that plan.

I consider Dolphin to be the best file manager yet I still use Nautilus or Thunar because my DE of choice leaves me pre-disposed to using GTK apps, even in situations where (on technical merits alone) the Qt app is far superior.
This is why I like to use just a window manager.  The choice of apps is left up to me.

---

### Post by cb951303 on 2009-01-15
> **phrostbyte said:**
> Go ahead and compare the APIs of GTK+ 2/3 and Qt for me. Thank you.

what gtk 3? there is no gtk3. that's the whole point. instead of rewriting a new toolkit why not use qt

---

### Post by phrostbyte on 2009-01-15
> **cb951303 said:**
> what gtk 3? there is no gtk3. that's the whole point. instead of rewriting a new toolkit why not use qt

Qt and GTK+ are vastly different. There is no clear migration path between GTK+ and Qt (unlike GTK+ 2 and GTK+ 3). Porting to GTK+ 3 is far less (if any) work, then porting to Qt, which is even written in a completely different programming language.

---

### Post by cb951303 on 2009-01-15
> **phrostbyte said:**
> Porting to GTK+ 3 is far less (if any) work

and your source is...? 

what's the point of GNOME3/GTK3 if developers are thinking to easily migrate? The whole point is to *break* (third time now, if that's what will make you understand) backward compatibility and in such case porting applications is never easy. It's true that porting them to QT would be harder considering gnome devs are used to GTK but it's nowhere near the extra effort that they will probably make by writing a new toolkit which will do the same job as QT.

---

### Post by phrostbyte on 2009-01-15
> **cb951303 said:**
> and your source is...? 

what's the point of GNOME3/GTK3 if developers are thinking to easily migrate? The whole point is to *break* (third time now, if that's what will make you understand) backward compatibility and in such case porting applications is never easy. It's true that porting them to QT would be harder considering gnome devs are used to GTK but it's nowhere near the extra effort that they will probably make by writing a new toolkit which will do the same job as QT.

Breaking backward compatibility doesn't not mean rewriting the whole API. From my understanding they have no intention to do so with Gnome 3.0, because it really isn't necessary. GTK+ and Qt (all versions) are vastly different in how you interact with them at a core level, and if you can't see that or you are not a programmer I can not help you.

---

### Post by ghindo on 2009-01-15
> **cb951303 said:**
> what gtk 3? there is no gtk3. that's the whole point. instead of rewriting a new toolkit why not use qtNo GTK+ developers are talking about rewriting the whole toolkit; they're talking about breaking ABI in future releases of the toolkit, which is *not* the same as starting from scratch.

---

### Post by ssam on 2009-01-15
> **Keyper7 said:**
> Because the main reason why Gnome was created and Gtk was popularized as a general-purpose GUI toolkit (instead of being just the GIMP toolkit) is now gone. Gtk has grown up much farther than being just a replacement, but now that Qt became LGPL this kind of questions are only natural.


I dont think that is quite right.

Qt has been free enough for gnome to use for many years
[http://en.wikipedia.org/wiki/GNOME#History](http://en.wikipedia.org/wiki/GNOME#History)

LGPL vs GPL only makes a difference if you want to link to a library from a non-free (or non-gpl) application.

i can't imagine GNOME or any of the big GTK apps moving. it would take years to port everything. it has taken years for all the KDE software to move from qt3 to qt4, the move from GTK+ to Qt would be a more difficult task.

the main change will be for closed source Qt apps (Opera, Google Earth, Skype, Adobe Photoshop Album, VirtualBox according to wikipedia). they will no longer have to pay licence fees.

---

### Post by LuisAugusto on 2009-01-15
Yeah, in practice is like that. But the bashing to Qt for not being available on the LPGL were enormous.

Now that Qt is LPGL and the only "relevant" advantage of Gtk has vanished :-)

---

### Post by 2cute4u on 2009-01-15
If there's only one toolkit, why shouldn't it be GTK?

Even though from what Ive heard QT is a better toolkit for the PROGRAMMER, I'm not a programmer, and as a user I can say that GTK apps have a far superior feel.   I hate how clunky and unresponsive QT apps and KDE feel.

---

### Post by LuisAugusto on 2009-01-15
> **2cute4u said:**
> If there's only one toolkit, why shouldn't it be GTK?

Even though from what Ive heard QT is a better toolkit for the PROGRAMMER, I'm not a programmer, and as a user I can say that GTK apps have a far superior feel.   I hate how clunky and unresponsive QT apps and KDE feel.

Because Qt is far better. GTK is far less responsive by the way...

---

### Post by ewaldk on 2009-01-15
When I started to use Linux some years ago, I was a Gnome user and I really liked it. However, I found a KDE program that I used almost daily (I didn't like the Gnome alternatives). That got me interested in KDE and someday I made the switch to KDE - because of one program! Now I do what many others do: only use programs of my DE in order to get a coherent user experience. What a loss that is if you thing about it. A standard toolkit for KDE/Gnome would be incredibly cool. Anyway just dreaming I fear...

I want to say again what someone else already said: This is not a Gnome Vs. Kde thing

---

### Post by mangar on 2009-01-15
@2cute4u
Every difficulty a library (Qt, Gtk, libxml, alsa, whatever) puts in the way of the developer, means that his ability to maintain, enhance, or polish his application is reduced, and that in the end means that you, as an end user, get a less good final product.

On the other hand, I do agree that the Gnome HIG (human interface guidelines) are better than KDE, but the HIG is toolkit agnostic.

---

### Post by LuisAugusto on 2009-01-15
> **mangar said:**
> @2cute4u
Every difficulty a library (Qt, Gtk, libxml, alsa, whatever) puts in the way of the developer, means that his ability to maintain, enhance, or polish his application is reduced, and that in the end means that you, as an end user, get a less good final product.

On the other hand, I do agree that the Gnome HIG (human interface guidelines) are better than KDE, but the HIG is toolkit agnostic.

Exactly, you can use GNOME HIG in Qt applications (or whatever). But as they already said (and they're right) this is about Qt and GTK.

---

### Post by Heinzelotto on 2009-01-15
> **mangar said:**
> Since Qt is to be released as LGPL, ending (imho) the historical significance of Gtk, I believe that it is for the best interest of all the involved parties - Gnome, KDE, Qt Gtk, and the application developers, to transition away from Gtk to Qt, creating a strong foundation of standards from whom the FOSS community can draw.


I think you miss the point that QT has already been released as GPL (not LGPL, which is unimportant for most Linux-developers anyway) for several years now.

---

### Post by OutOfReach on 2009-01-15
> **2cute4u said:**
> If there's only one toolkit, why shouldn't it be GTK?

Even though from what Ive heard QT is a better toolkit for the PROGRAMMER, I'm not a programmer, and as a user I can say that GTK apps have a far superior feel.   I hate how clunky and unresponsive QT apps and KDE feel.

IMO I think Qt's API is a lot easier to understand for the programmer (compared to GTK's).
But I have to disagree with you, I always feel that Qt apps are on par with GTK apps. Do not judge a toolkit by only using it in one or two programs.
I also feel that Qt has much better theme abilities. It looks a lot more elegant with the proper work (KDE's Oxygen theme for example)

---

### Post by 2cute4u on 2009-01-15
> **mangar said:**
> @2cute4u
Every difficulty a library (Qt, Gtk, libxml, alsa, whatever) puts in the way of the developer, means that his ability to maintain, enhance, or polish his application is reduced, and that in the end means that you, as an end user, get a less good final product.

On the other hand, I do agree that the Gnome HIG (human interface guidelines) are better than KDE, but the HIG is toolkit agnostic.
its not just the HIG,  though those are really important. It's the feel of things in motion  dragging windows, pullong down menus, pushing buttons, dragging and dropping objects, moving the mouse. These things have to do with the low level drawing functions of the toolboxes (which I admit I don't understand); they just feel better, smother and more ellegant in GTK apps and gnome than they do in QT apps and KDE.  

If QT were to rewrite the basic object drawing funtions, to draw and animate more like GTK (or better yet the mac toolkit), then I would agree that it would be the better toolkit.  But as long as it draws like a windows wanna-be, I don't want it powering my apps.

---

### Post by mangar on 2009-01-15
@Heinzelotto
The Gpl was seen as a barrier for most companies that depend on propriety bits for living (I think that includes Redhat and Novell).

Qt license was about 3000$ per developer, per year, per platform, and potential users had to choose the license before starting development (either commercial or propriety), which meant that trying to assess Qt for development became a sort of a lock.

This article is old, but I hope it will add some perspective:
[http://www.staikos.net/~staikos/whyqt/](http://www.staikos.net/~staikos/whyqt/)
[http://www.wikivs.com/wiki/Qt_vs_GTK](http://www.wikivs.com/wiki/Qt_vs_GTK)

IMHO, even if Qt didn't have a clean technological advantage, it would have still been the better choice, since it's got very good documentation.


BTW:
From a developer POV, having clear documentation and examples is, at most times, much better than having the source code available.

---

### Post by smartboyathome on 2009-01-15
I feel that GTK is more "desktop agnostic" than QT, if you will. I can theme it easier without installing many GNOME tools, just by using something like gtk-chtheme or lxapprearance. With Qt, you would pretty much have to install at least the KDE tools to theme it.

Also, everyone is acting like GTK shouldn't even be considered unless it is this super superior tool. Qt4 may have advantages, but the reason GTK is coming out with GTK3 is because it is going to meet those. I think that having different toolkits competing will be ultimately better than having one with no competition on the platform. More innovation comes out of competing than out of working together, that is why even in the science community there are several theories for the same concept, which each group of scientists trying to prove theirs is right.

---

### Post by geoken on 2009-01-15
> **2cute4u said:**
> its not just the HIG,  though those are really important. It's the feel of things in motion  dragging windows, pullong down menus, pushing buttons, dragging and dropping objects, moving the mouse. These things have to do with the low level drawing functions of the toolboxes (which I admit I don't understand); they just feel better, smother and more ellegant in GTK apps and gnome than they do in QT apps and KDE.  

If QT were to rewrite the basic object drawing funtions, to draw and animate more like GTK (or better yet the mac toolkit), then I would agree that it would be the better toolkit.  But as long as it draws like a windows wanna-be, I don't want it powering my apps.

Look around KDELook and I think your opinion may change.
[http://www.kde-look.org/content/preview.php?preview=1&id=52721&file1=52721-1.jpg&file2=52721-2.png&file3=52721-3.jpg&name=LightGrey+for+Domino]("http://www.kde-look.org/content/preview.php?preview=1&id=52721&file1=52721-1.jpg&file2=52721-2.png&file3=52721-3.jpg&name=LightGrey+for+Domino")

---

### Post by mangar on 2009-01-15
@2cute4u
I agree that flicker and resize were a problem in Kde 3.5 series.
The flicker problem has been fixed in version 4.4 of Qt:

[http://labs.trolltech.com/blogs/2007/08/09/qt-invaded-by-aliens-the-end-of-all-flicker](http://labs.trolltech.com/blogs/2007/08/09/qt-invaded-by-aliens-the-end-of-all-flicker)

---

### Post by LuisAugusto on 2009-01-15
> **smartboyathome said:**
> I feel that GTK is more "desktop agnostic" than QT, if you will. I can theme it easier without installing many GNOME tools, just by using something like gtk-chtheme or lxapprearance. With Qt, you would pretty much have to install at least the KDE tools to theme it.

You don't need anything of KDE to theme your Qt applications (which is a stupid idea), you just run "qtconfig".

> **smartboyathome said:**
> Also, everyone is acting like GTK shouldn't even be considered unless it is this super superior tool. Qt4 may have advantages, but the reason GTK is coming out with GTK3 is because it is going to meet those.

Qt already met them, and since it has a hell lot more developers (just like KDE does) by when gtk catches, Qt will be even more.

> **2cute4u said:**
> If QT were to rewrite the basic object drawing funtions, to draw and animate more like GTK (or better yet the mac toolkit), then I would agree that it would be the better toolkit.  But as long as it draws like a windows wanna-be, I don't want it powering my apps.

What are you talking about? Qt supports far more animation and mac-like things than Gtk has ever dream off.

---

### Post by pansz on 2009-01-15
I agree that Qt is better maintained and has a better framework.

However, Qt lacks a C binding, while GNU is a community which encourages non-C++ programming. (RMS thinks GNU programs should not use C++ unless absolutely necessary)

For the commercial world there's no doubt Qt will be the de-facto standard of Linux programming, but for the F/OSS world it is very likely that Gtk+ will exist for a much longer time.

---

### Post by LuisAugusto on 2009-01-15
> **pansz said:**
> I agree that Qt is better maintained and has a better framework.

However, Qt lacks a C binding, while GNU is a community which encourages non-C++ programming. (RMS thinks GNU programs should not use C++ unless absolutely necessary)

For the commercial world there's no doubt Qt will be the de-facto standard of Linux programming, but for the F/OSS world it is very likely that Gtk+ will exist for a much longer time.

Richard Stallman will die eventually. And, let's hope people OSS developers and supporters can look a little beyond his little closed perspective.

---

### Post by zekopeko on 2009-01-15
not too bash KDE devs (i think they did THEIR thing with KDE4 excellent) , but i just like GNOME better. The whole philosophy of GNOME apps is similar to Mac OS X. Simple and to the point. On the other hand KDE's still isn't visually pleasing to me. And not to mention that they have to add a bazilion options to the menus. Fortunately they understood that the broader user base doesn't want a graphical option for every little thing in KDE4 and the world is now a little saner. I would just like for GTK to be on the same eyecandy level of Mac OS X which IMO has the most polished GUI toolkit.

And the whole aspect of standardization should be made on the freedesktop.org platform to benefit every desktop environment.

---

### Post by LuisAugusto on 2009-01-15
Then again it isn't about KDE and GNOME... it is about Qt and GTK.

---

### Post by MaxIBoy on 2009-01-15
I think this discussion has gotten a little out of hand.

When dealing with software, need justifies creation, use justifies maintenance, and disuse justifies abandonment. If you don't like a toolkit, don't write programs with it. If you don't like some software because it doesn't use your preferred toolkit, don't use it. Or, I'm sure most software maintainers would be happy to accept a user-submitted patch to add a compile switch for using a different toolkit. If it's not enough of a dealbreaker to make you stop using it, then you have no right to complain.

---

### Post by 2cute4u on 2009-01-16
> **geoken said:**
> Look around KDELook and I think your opinion may change.
 [http://www.kde-look.org/content/preview.php?preview=1&id=52721&file1=52721-1.jpg&file2=52721-2.png&file3=52721-3.jpg&name=LightGrey+for+Domino](http://www.kde-look.org/content/preview.php?preview=1&id=52721&file1=52721-1.jpg&file2=52721-2.png&file3=52721-3.jpg&name=LightGrey+for+Domino)
 
WTF do themes have to do with anything, do you even know the difference between "look" and "feel"?  nothing I'm talking about has to do with anything you can take a screenshot. Imagine if I said "I think that a Camry drives much smoother, and handles corners, much better than an Accord, and you replied, "well look at this picture of an Accord, it looks just like a Camry, so it's just as good"


> **LuisAugusto said:**
> 
What are you talking about? Qt supports far more animation and mac-like things than Gtk has ever dream off.
Far more doesn't mean better, it's not doing more, it's doing it right.  The animations, in KDE are annoying,and they don't work to connect you to the interface.  They are not at all mac like, or gnome like; from the little I know about windows, they are very windows like.

---

### Post by LuisAugusto on 2009-01-16
> **2cute4u said:**
> WTF do themes have to do with anything, do you even know the difference between "look" and "feel"?  nothing I'm talking about has to do with anything you can take a screenshot. Imagine if I said "I think that a Camry drives much smoother, and handles corners, much better than an Accord, and you replied, "well look at this picture of an Accord, it looks just like a Camry, so it's just as good"



Far more doesn't mean better, it's not doing more, it's doing it right.  The animations, in KDE are annoying,and they don't work to connect you to the interface.  They are not at all mac like, or gnome like; from the little I know about windows, they are very windows like.

Qt isn't KDE. And KDE is barely using animations. GTK support many too, but GNOME use none.

---

### Post by techmarks on 2009-01-16
I think it's terrific news that Qt is now LGPL.

Qt is clearly the superior toolkit.

GTK has problems.  For one the terrible integration with OpenGL.  Also the fact that it's based on C is very problematic at times when trying to program in C++.

GTK still will have it's place, but I think the focus of GUI development will begin to favour Qt.

---

### Post by beniwtv on 2009-01-16
So since QT now it LGPL, I thought I'd take a quick look at it. I'm always interested in GUI programming :)

I come from a GTK background, having made many GUIs with it. While I'm no expert, I've come to like how GTK handles things.

So I've tried some easy things which I can do in GTK with QT4 Designer:

First of all, I created a dialog with two buttons on the bottom. So far it looks OK, the dialog and two buttons appear.  I realize I need a bigger window, so I just resize it. But what's that? Whoops... the buttons do not move, and now are in the center of the dialog.

Coming from Windows development using Visual Studio, no surprise to me, QT4 appears to use a fixed layout. So I search for some properties that tell the button box to stay at the bottom right, and I seem to find some, but modifying them seems to do nothing. Weird. 

OK, maybe you have to do that programatically, no surprise either, Windows Forms has limited options there as well. So I decide to see if there are any widgets imitating GTK's automatic layout, and indeed there seem to be, called "GridLayout".

Placing some things into the GridLayout, and resizing it seems to work. Hooray! But it's not as straight forward as GTK where to hover the mouse to place the object.

Moving on to other things, I want a tabbed interface, where each tab represents a document. Naturally, I'd like to place a close button on each tab. So I place a Tab widget, and try to delete the default labels, so that I can place a VerticalLayout with the label and the button. Fail. In QT4 it's not possible, or at least not with QT Designer, so I probably have to code it.

So I move on to my last task: A scroll window. So I place a scroll window and some content in it. However, I can't seem to get the scrollbars to appear. And if I select them to always appear, they  can not be scrolled, even though there is content.

In summary, I can't see why QT4 is superior to GTK from a designer's view, unless I missed big time some options (Again, it was only a quick look).

While I may agree that it's superior form a coding standpoint, e.g. the QT4 source code may be cleaner and much more organized, more effective, you name it, .... it can't see how it's superior to GTK, which is, once you get a grip for the not fixed layout, a godsend to work with.

For me, fixed layout and these other is like going back to Visual Basic 6.0 and Windows Forms *shudder*. 

NOTE: This is _not_ intended as a flame to QT4. Instead, I hope some of the QT4 guys here can comment and enlighten me on how to do things properly in QT4.

Cheers,

---

### Post by deepclutch on 2009-01-16
First - I voted for QT.
--
100% Gnome/GTK+ apps user.But ,I would like to see a better toolkit in the likes of QT4 or..why NOT QT4 itself?Make it as a base for future Gnome -3/4 releases.
Then, if qt vs gtk+ is fought ,you will end up with the core fight C vs Cpp .that is another BIG war:popcorn:

---

### Post by zolookas on 2009-01-16
> **beniwtv said:**
> 
So I've tried some easy things which I can do in GTK with QT4 Designer:

First of all, I created a dialog with two buttons on the bottom. So far it looks OK, the dialog and two buttons appear. I realize I need a bigger window, so I just resize it. But what's that? Whoops... the buttons do not move, and now are in the center of the dialog.

Coming from Windows development using Visual Studio, no surprise to me, QT4 appears to use a fixed layout. So I search for some properties that tell the button box to stay at the bottom right, and I seem to find some, but modifying them seems to do nothing. Weird. 

OK, maybe you have to do that programatically, no surprise either, Windows Forms has limited options there as well. So I decide to see if there are any widgets imitating GTK's automatic layout, and indeed there seem to be, called "GridLayout".

Placing some things into the GridLayout, and resizing it seems to work. Hooray! But it's not as straight forward as GTK where to hover the mouse to place the object.


This is unnecessary there is a "built-in" layout, but it is not activated by default, because user has to choose which one he/she likes. Just add a few items and right click on an empty space, select "Lay out" and select the layout you want, then you will see how it works.

This is probably what you have done:
Pick one of the layouts (for example Grid Layout) and drag them on the dialog.
Now expand it to the window: right click on an empty space in dialog and select "Lay out" and then any layout you want (because you added only one item (Grid Layout)) (for example "Lay Out Vertically").
But you are adding just another layout which takes 100% of space, you can still place other items beyond that layout, so use that only if it is necessary.

I can't comment about the tabs issue, i have used Qt only for one project.

---

### Post by hessiess on 2009-01-16
NO, GTK looks nicer, and is easier to custmise.

---

### Post by funkyou on 2009-01-16
**Hello world in plain GTK:**
```
static void hello( GtkWidget *widget, gpointer data )
{
g_print ("Hello World\n");
}

static gboolean delete_event( GtkWidget *widget, GdkEvent *event, gpointer data )
{
g_print ("delete event occurred\n");

return TRUE;
}

static void destroy( GtkWidget *widget, gpointer data )
{
gtk_main_quit ();
}

int main( int argc,
char *argv[] )
{
GtkWidget *window;
GtkWidget *button;

gtk_init (&argc, &argv);

window = gtk_window_new (GTK_WINDOW_TOPLEVEL);

g_signal_connect (G_OBJECT (window), "delete_event",
G_CALLBACK (delete_event), NULL);

g_signal_connect (G_OBJECT (window), "destroy",
G_CALLBACK (destroy), NULL);

gtk_container_set_border_width (GTK_CONTAINER (window), 10);

button = gtk_button_new_with_label ("Hello World");

g_signal_connect (G_OBJECT (button), "clicked",
G_CALLBACK (hello), NULL);

g_signal_connect_swapped (G_OBJECT (button), "clicked",
G_CALLBACK (gtk_widget_destroy),
G_OBJECT (window));

gtk_container_add (GTK_CONTAINER (window), button);
gtk_widget_show (button);
gtk_widget_show (window);

gtk_main ();

return 0;
}

```


**Hello World in plain Qt:**
```
int main(int argc, char *argv[])
{
QApplication app(argc, argv);

QPushButton hello("Hello world!");
hello.resize(100, 30);

hello.show();
return app.exec();
}
```

Oh, and i know there are various bindings for GTK that enable you to create such stuff in less code, but dont forget that Qt (and of course KDE) has such bindings too ;)

Well... Code less. Create more :)

---

### Post by loell on 2009-01-16
> **funkyou said:**
> **Hello world in plain GTK:**


**Hello World in plain Qt:**
Well... Code less. Create more :)

errhm, the code you presented and compared does not do the same thing. ;)

---

### Post by Tibuda on 2009-01-16
> **loell said:**
> errhm, the code you presented and compared does not do the same thing. ;)

No, they don't.
```
#include <gtk/gtk.h>
int main(int argc, char *argv[] )
{
  gtk_init (&argc, &argv);
  GtkWidget *window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
  GtkWidget *button = gtk_button_new_with_label("Hello World");
  g_signal_connect (G_OBJECT (window), "destroy",
    G_CALLBACK (gtk_main_quit), NULL);
  gtk_container_add (GTK_CONTAINER(window), button);
  gtk_widget_show (button);
  gtk_widget_show (window);
  gtk_main ();
  return 0;
}
```
EDIT: remember this is C not C++

---

### Post by loell on 2009-01-16
yep, that's more like it, without the callback from the button.

---

### Post by beniwtv on 2009-01-16
> **zolookas said:**
> This is unnecessary there is a "built-in" layout, but it is not activated by default, because user has to choose which one he/she likes. Just add a few items and right click on an empty space, select "Lay out" and select the layout you want, then you will see how it works.


Now it's getting interesting. :D

I tried what you suggest - and it seemed to work. Still I think GTK is more straight forward with layouts (try adding a table in Glade and you'll see what I mean).

So I stand corrected on that.

However, I still think QT vs. GTK is a pointless debate, as it seems the two of them handle things different, and thus, can't really compare.

---

### Post by geoken on 2009-01-16
> **2cute4u said:**
> WTF do themes have to do with anything, do you even know the difference between "look" and "feel"?  nothing I'm talking about has to do with anything you can take a screenshot. Imagine if I said "I think that a Camry drives much smoother, and handles corners, much better than an Accord, and you replied, "well look at this picture of an Accord, it looks just like a Camry, so it's just as good"




First of all, you used the word draw several times in the post I was responding to;

*If QT were to rewrite the basic object **drawing** funtions, to **draw** and animate more like GTK (or better yet the mac toolkit), then I would agree that it would be the better toolkit. But as long as it **draws** like a windows wanna-be, I don't want it powering my apps.*

Perhaps your definition of 'draw' is not the programatically accurate definition of draw. If this is the case, then I apologize for the misunderstanding but also ask that, in the future, when you misuse terms don't get bent out of shape and take an insulting tone when people misinterpret your comments based on your misuse of terms.

Secondly, tweaking animations is so trivial as to be a non issue. Most animation functions are able to accept multiple easing equations to change the character of the animation. Basically the animation function/class will be supplied your end properties and time (some may even require the begining properties) and an easing equation. The easing equation is what you would define as the feel. For example, OS X's easing equation on drop down menus starts very slow, but then exponentially ramps up it's speed as the animation progresses. The effect could easily be duplicated with an easing function/curve of InQuint or InExpo.

---

### Post by techmarks on 2009-01-16
In it's current state GTK is at a dead end.

A complete re-design is what is needed.

Is it really worth it at this point?  I'm not sure it is.

---

### Post by jpeddicord on 2009-01-16
> **techmarks said:**
> GTK has problems.  For one the terrible integration with OpenGL.  Also the fact that it's based on C is very problematic at times when trying to program in C++.

Could you back up those statements?

gtkmm is an object-oriented C++ interface to GTK+: [http://www.gtkmm.org/](http://www.gtkmm.org/)
Also, how is using a C library problematic when using C++? It's still compatible, just a different code structure.

I'm curious what you mean by "terrible integration with OpenGL." Do you mean compositing, or embedded OpenGL? If you mean compositing, take a look at the Murrine GTK+ engine which supports per-widget alpha transparency (RGBA).

If you are talking about embedded OpenGL, well, I'm not sure where GTK+ fails in that area either. Take a look at this video, where everything (including the GTK+ widgets) is drawn with OpenGL: [http://www.youtube.com/watch?v=dCAvtaeWwmU](http://www.youtube.com/watch?v=dCAvtaeWwmU)
The Clutter UI library is another OpenGL interface toolkit that integrates well with GTK+ windows and widgets.

I'm just not sure what the problem is with either of those statements. :)

---

### Post by jpeddicord on 2009-01-16
> **beniwtv said:**
> However, I still think QT vs. GTK is a pointless debate, as it seems the two of them handle things different, and thus, can't really compare.

If only the Thanks feature was enabled right now. I wholeheartedly agree.

---

### Post by geoken on 2009-01-16
> **jacobmp92 said:**
> If only the Thanks feature was enabled right now. I wholeheartedly agree.

I disagree. 

If we have 2 things with identical purposes, is it not always a good idea to discuss the need for having 2 things?

---

### Post by cb951303 on 2009-01-16
> **geoken said:**
> I disagree. 

If we have 2 things with identical purposes, is it not always a good idea to discuss the need for having 2 things?

+1

Both GTK and QT are GUI toolkits. The debate is valid.

---

### Post by Tibuda on 2009-01-16
> **geoken said:**
> If we have 2 things with identical purposes, is it not always a good idea to discuss the need for having 2 things?
Remember that Linux and Windows have identical purposes. The "need" to have many (not only two) things with identical purposes is competition.
EDIT: Many religions have the same purposes too. Why do we have them all?

---

### Post by Changturkey on 2009-01-16
> **danielrmt said:**
> Remember that Linux and Windows have identical purposes. The "need" to have many (not only two) things with identical purposes is competition.
EDIT: Many religions have the same purposes too. Why do we have them all?

Linux was and still is more suited to the server, whereas Windows has always been a desktop OS. Religions don't exactly compete with each other either.

---

### Post by zolookas on 2009-01-16
I think it is impossible to have one toolkit like it is impossible to have only one distro, but since both toolkits will be licenced under LGPL now, i would like to see them share features/ideas, talk to each other and have some standarts. As a user, i want GTK+ and Qt applications to have the same functionality under Gnome and KDE (for example: look and feel, file open dialogs, ability to use drag and drop, which sometimes does not work). It would be great. But it seems that (sadly) toolkit developers have no interest in that (Qt will have a GTK style in 4.5, but there is no response from GTK+ developers) and don't see anything happening soon.

---

### Post by geoken on 2009-01-16
> **danielrmt said:**
> Remember that Linux and Windows have identical purposes. The "need" to have many (not only two) things with identical purposes is competition.
EDIT: Many religions have the same purposes too. Why do we have them all?

I never said we need to eliminate them. After a discussion it's very likely that the conclusion will be that both things are needed. It's still perfectly valid to discuss them.

Also, while competition is good, cannibalization is not.

---

### Post by Tibuda on 2009-01-16
> **geoken said:**
> I never said we need to eliminate them. After a discussion it's very likely that the conclusion will be that both things are needed. It's still perfectly valid to discuss them.

Also, while competition is good, cannibalization is not.

Cannibalization?

---

### Post by geoken on 2009-01-16
> **danielrmt said:**
> Cannibalization?

It's a term common in the auto industry. It's commonly used when one manufacturer makes two models that are extremely close to each other in terms of the market segment they satisfy.

The basic idea is that a certain market is finite in size. If you produce two items to address that market there is the chance that your two items will simply subdivide the piece of the pie that your one item would have got. At this point it still hasn't resulted in a net loss, but when you factor in the extra costs wih developing/maintaining a second, similar product you realize that you could have achieved greater gains if you didn't invest time/money into a course of action which did nothing more than subdivide your existing market.



Applying this to the current situation, the question would be;

Does having two toolkits increase the amount of people choosing linux over other platforms or does it merely subdivide the people who have already chosen linux?

---

### Post by 2cute4u on 2009-01-16
> **geoken said:**
> First of all, you used the word draw several times in the post I was responding to;

*If QT were to rewrite the basic object **drawing** funtions, to **draw** and animate more like GTK (or better yet the mac toolkit), then I would agree that it would be the better toolkit. But as long as it **draws** like a windows wanna-be, I don't want it powering my apps.*

Perhaps your definition of 'draw' is not the programatically accurate definition of draw. If this is the case, then I apologize for the misunderstanding but also ask that, in the future, when you misuse terms don't get bent out of shape and take an insulting tone when people misinterpret your comments based on your misuse of terms.

Secondly, tweaking animations is so trivial as to be a non issue. Most animation functions are able to accept multiple easing equations to change the character of the animation. Basically the animation function/class will be supplied your end properties and time (some may even require the begining properties) and an easing equation. The easing equation is what you would define as the feel. For example, OS X's easing equation on drop down menus starts very slow, but then exponentially ramps up it's speed as the animation progresses. The effect could easily be duplicated with an easing function/curve of InQuint or InExpo.

I'm sorry about the tone I took yesterrday,  it's that time of the month for mem and I had a fight with my girlfreind . so I was in a reallybad moood when I replied.  Also I don't thinkI knoiw the right way to describe what I'm talking about, since I'm not a programmer, so i probably did misuse terms.  

If tweaking the animations is trivial, what would it take to do it and get it into QT4? Could a package be created that would make the changes to and installed system, or would it have to be something that is made part of the official codebase and accepted by the QT team?

---

### Post by geoken on 2009-01-16
> **2cute4u said:**
> 
If tweaking the animations is trivial, what would it take to do it and get it into QT4? Could a package be created that would make the changes to and installed system, or would it have to be something that is made part of the official codebase and accepted by the QT team?

The functions are already in Qt. I think your issue is more with the specific functions chosen by KDE. I can't really speak to how they're implemented in KDE itself so I don't know what would be involved with changing them in KDE. 

The only point I was trying to make is that the animation 'feel' that you dislike in KDE is something that was chosen by KDE and independent of the toolkit itself as the animation options within the toolkit are completely configurable.

---

### Post by atraylen on 2009-01-16
I don't think any one toolkit should become standard.  I think that is the grace of the system.  If there are applications that I want to run in QT I install kde and if there are applications that run in GTK I install gnome.  I don't really see the hassle around it?  I think that there could be a little better interoperability.  I think that we are starting to see that these days. I just don't see why would should limit ourselves?  There are advantages to using either toolkit to develop.  Just as there are advantages to using either corresponding desktop environment to accomplish tasks.  One good thing about QT is its ability to run on Windows, hopefully this will only get better with time.  Someone mentioned earlier in this thread that QT was a full blown development tool from what I have seen I have to agree with this.  Couple that with its ability to run on Windows I can see why a developer might want to use this toolkit.  But I do not think that this is grounds enough to limit ourselves to one toolkit.  We should aim for ultimate interoperability.

---

### Post by jsmidt on 2009-01-16
I'm not going to go into all my reasons, it would take too long, but I think standardizing around Qt would be a good move.

However, I do see benefit in Qt and GTK becoming like a 2 party system which in theory would have them compel each other to innovate to compete.  But I'm not convinced GTK innovation can keep up with Qt's anymore.

---

### Post by darkcoder on 2009-01-16
One thing is Qt becoming the distribution (Ubuntu and derivatives) standard toolkit and another is becoming the Gnome's standard toolkit.

As a company, Canonical can reduce expense and provide faster/stable tools if they just concentrate on one toolkit.  No more Kubuntu tools appearing a release or two later.

But Gnome switching to Qt... keep dreaming

---

### Post by mangar on 2009-01-16
@atraylen
Having two toolkits that do not cleanly inter operate is a problem, because it **reduces choice**.

If you choose Gnome, using Qt based applications will give you a lesser user experience than using Gtk based applications.

Choosing Kde, will give you a lesser user experience if you choose Gtk based applications.

I have no problem with Gnome and Kde competing, or with Gtk or Qt competing. On the other hand, I have a serious problem with Qt based applications that do not cleanly integrate with Gnome, and Gtk based applications that do not cleanly integrate with Kde; I'm fully aware that they all work together, but the experience is far from satisfactory.

While freedesktop.org exists to solve the interoperability problem, it is far from being a complete solution, and the rate of standards production does not seem to improve.

---

### Post by bruce89 on 2009-01-16
> **mangar said:**
> I have no problem with Gnome and Kde competing, or with Gtk or Qt competing. On the other hand, I have a serious problem with Qt based applications that do not cleanly integrate with Gnome, and Gtk based applications that do not cleanly integrate with Kde; I'm fully aware that they all work together, but the experience is far from satisfactory.

There is no difference between GNOME vs. KDE than there is over GTK+ over Qt. Think about it.

All this nonsense about ditching GTK+ is therefore as plausible as ditching GNOME.

---

### Post by mangar on 2009-01-16
@bruce89
I think I don't understand your argument:

Do you mean that Gtk is not seperateable from Gnome, and Qt from Kde? If so, a counter argument might be the existence of xfce, Gimp, Last.fm and Skype on Windows and Mac.

If you mean that the desktop standards do not depend on Qt or Gtk, a counter argument would be that since Qt is a full featured framework, it can provide a de-facto standard, and therefore, solve this problem. If this point is wrong, I think it's better to lose a desktop environment and have wider choice of applications.

---

### Post by bruce89 on 2009-01-16
> **mangar said:**
> @bruce89
I think I don't understand your argument:

Do you mean that Gtk is not seperateable from Gnome, and Qt from Kde? If so, a counter argument might be the existence of xfce, Gimp, Last.fm and Skype on Windows and Mac.

Xfce uses GTK+, as does GIMP (on all platforms).

> **mangar said:**
> If you mean that the desktop standards do not depend on Qt or Gtk, a counter argument would be that since Qt is a full featured framework, it can provide a de-facto standard, and therefore, solve this problem. If this point is wrong, I think it's better to lose a desktop environment and have wider choice of applications.

I was really going with the fact that GTK+ is not going to go away, no matter how much you want it to.

---

### Post by mangar on 2009-01-16
@bruce89
Pidgin, Gimp, Xfce in Gtk - it's a fact, No argument here.

As for Gtk going away - it's not about personal preference - I have nothing to gain from, therefore, no reason to want, Gtk disbanding; I just see it as the most logical conclusion from Qt's recent license change, and argue for that point of view.

---

### Post by Vadi on 2009-01-16
Gtk is tailored to Gnome, Qt isn't. I don't see Gtk becoming redundant anytime soon.

Some numbers to think on: apport-gtk is installed on 89% of ubuntu machines. apport-qt is installed on 15% of ubuntu machines.

---

### Post by MaxIBoy on 2009-01-16
+1

There's no reason to abandon Gtk+, it's currently in wider use.


And as I've said before, live and let live.

---

### Post by bruce89 on 2009-01-16
> **mangar said:**
> I just see it as the most logical conclusion from Qt's recent license change, and argue for that point of view.

Why is it the most logical thing to do? Porting massive numbers of programs from one toolkit to another (not including a change of language) wasting thousands of hours for what?

There are some programs that still use Athena (xtide).

I rather like the bit on the Qt Website which once said that "We will never change to LGPL, as the FSF don't recommend it for anything other than special circumstances". Those special circumstances are where there are already lots of libraries that do the same thing. There are a lot of GUI libraries.

---

### Post by samjh on 2009-01-16
> **mangar said:**
> If you choose Gnome, using Qt based applications will give you a lesser user experience than using Gtk based applications.

You're a bit behind the times.

Qt has steadily been adopting Freedesktop.org standards.  In another year or two, Qt apps will be indistinguishable from GTK+ apps on Gnome.  Apps that use Qt 4 and above, are already capable of near-perfect integration with Gnome.  Qt4.5 will include QGtkStyle, so look and feel need no longer be an issue.  With more Freedesktop.org stuff getting into Qt, integration with Gnome will only become easier.

I have no less user experience when using VLC or VirtualBox on Gnome, despite the fact that both are Qt apps.

---

### Post by MaxIBoy on 2009-01-16
I thought VLC was merely *forked* to Qt?

It's annoying that VBox doesn't match my theme, but it's not really a big deal.

---

### Post by LuisAugusto on 2009-01-16
> **MaxIBoy said:**
> I thought VLC was merely *forked* to Qt?

It's annoying that VBox doesn't match my theme, but it's not really a big deal.

It matches mine...

---

### Post by whollycow on 2009-01-17
> **samjh said:**
> I have no less user experience when using VLC or VirtualBox on Gnome, despite the fact that both are Qt apps.

I don't know enough about the underpinnings of either toolkit to have an opinion but I definitely HATE the file->open dialog in VLC.  The main VLC interface looks alright in Gnome, but they've got to do something about the file chooser.

---

### Post by LuisAugusto on 2009-01-17
> **whollycow said:**
> I don't know enough about the underpinnings of either toolkit to have an opinion but I definitely HATE the file->open dialog in VLC.  The main VLC interface looks alright in Gnome, but they've got to do something about the file chooser.

Uhm, yes it looks out of place on GNOME, but it isn't a bad "file choose" dialog itself (gnome dialogs are quite bad).

---

### Post by techmarks on 2009-01-17
> **jacobmp92 said:**
> Could you back up those statements?

gtkmm is an object-oriented C++ interface to GTK+: 

I'm curious what you mean by "terrible integration with OpenGL." 

You'll need to use GTKGLext which is not maintained,and not even an official part of GTK and hasn't been updated in a long time.
It doesn't support the GL_ARB__multisample, and besides just seems to have been abondoned.

I had troubles using some C++ libraries with GTK, without using GTKmm.
(I know I should start using Gtkmm!)

I'm not saying at all the QT is perfect, and certainly GTK has it's own strengths, for example there is the issue of some of the modifications QT has made to the C++ language.

But the point is there isn't anything perfect, GTK+ is not and QT is not.

Certainly the documentation for QT is much better.

Both are good toolkits.  In the end I guess just use the one that helps to accomplish your goals more efficiently.

---

### Post by benmoran on 2009-01-17
I personally love the look and feel of GTK. That said, I do use a lot of QT apps regularly. Some people go on and on about things looking out of place. It can be a minor inconvenience, but it doesn't bother me that much to be honest. I also disagree with the statement that it will scare away users, since ex-Windows users are all well familiar with every application looking different.

I think some things (like audio) definitely should become standard across the board, without a doubt. Things like QT vs GTK are more difficult to argue about... Lets just all be glad we have a choice, and see which path the future takes. Personally i'll use GTK, as I like vanilla C.

---

### Post by samjh on 2009-01-17
....

---

### Post by bruce89 on 2009-01-17
> **LuisAugusto said:**
> Uhm, yes it looks out of place on GNOME, but it isn't a bad "file choose" dialog itself (gnome dialogs are quite bad).

It's a GTK+ standard dialogue, not a GNOME one.

> **techmarks said:**
> You'll need to use GTKGLext which is not maintained,and not even an official part of GTK and hasn't been updated in a long time.
It doesn't support the GL_ARB__multisample, and besides just seems to have been abondoned.

AFAIK, Clutter is supposed to fill this gap.

> **techmarks said:**
> I'm not saying at all the QT is perfect, and certainly GTK has it's own strengths, for example there is the issue of some of the modifications QT has made to the C++ language.

It sometimes feels like GObjectified C is a different language to "normal" C too.

> **techmarks said:**
> Certainly the documentation for QT is much better.

How many people are paid to maintain Qt? How many for GTK+? This may be a good reason.

One damn good argument for GTK+ is GObject-Introspection, which could mean language bindings without (AFAIK) any code at all. GNOME 3.0 is planned to be using a lot of JavaScript, which shows the power of GObject.

---

### Post by LuisAugusto on 2009-01-17
> **bruce89 said:**
> It's a GTK+ standard dialogue, not a GNOME one.

Wrong, is a Qt standard dialog.

> **bruce89 said:**
> It sometimes feels like GObjectified C is a different language to "normal" C too.

Yes, I almost feel that GNOME will end up using C++ one day haha.


> **bruce89 said:**
> How many people are paid to maintain Qt? How many for GTK+? This may be a good reason.

It's completely irrelevant. Qt documentation is better regardless of why.

---

### Post by bruce89 on 2009-01-17
> **LuisAugusto said:**
> Wrong, is a Qt standard dialog.

I was responding to the bit which said the GNOME ones are bad by saying it's a GTK+ one, not a GNOME one.

> **LuisAugusto said:**
> Yes, I almost feel that GNOME will end up using C++ one day haha.

GObject is not quite that bad. Also, it was designed with UIs in mind, and so has things like signals built in.

> **LuisAugusto said:**
> It's completely irrelevant. Qt documentation is better regardless of why.

No it's not. The reason you say Qt has better documentation is because the developers are paid for their work. (Most of) the GTK+ ones on the other hand aren't.

It'd be like West of Scotland being expected to beat Toulouse in the Heineken Cup instead of Glasgow beating them instead. I'm sure West could do if they put their minds to it though.

---

### Post by MaxIBoy on 2009-01-17
I'm going to have to say that good docs are good docs, no matter how many people were or weren't paid to write them.

---

### Post by LuisAugusto on 2009-01-17
> **bruce89 said:**
> I was responding to the bit which said the GNOME ones are bad by saying it's a GTK+ one, not a GNOME one.

I'm lost. VLC is a Qt application and somebody was bitching because it's dialog look out of place. I just said, yes, they do, but GNOME dialogs suck anyway, never intent to speak of gtk itself or any other issue. 

> **bruce89 said:**
> GObject is not quite that bad. Also, it was designed with UIs in mind, and so has things like signals built in.

I'm not against C++ (I like Qt so...), but, what about Vala? Isn't it an object oriented language? Just like C#, Java or C++?

> **bruce89 said:**
> No it's not. The reason you say Qt has better documentation is because the developers are paid for their work. (Most of) the GTK+ ones on the other hand aren't.

It'd be like West of Scotland being expected to beat Toulouse in the Heineken Cup instead of Glasgow beating them instead. I'm sure West could do if they put their minds to it though.

I knew what your point was, yet, It's still irrelevant.

---

### Post by bruce89 on 2009-01-17
> **LuisAugusto said:**
> I'm not against C++ (I like Qt so...), but, what about Vala? Isn't it an object oriented language? Just like C#, Java or C++?

Indeed it is, it's very interesting.

```
public class HelloUbuntu
{
	string name;

	public HelloUbuntu (string name)
	{
		this.name = name;
	}

	public void say_hello ()
	{
		stdout.printf ("Hello, %s! Welcome to Ubuntu\n", this.name);
	}

	public static void main (string[] args)
	{
		var name = new string ();

		stdout.printf ("Hi! What's your name? ");
		stdin.scanf ("%s", name);
		var hello = new HelloUbuntu (name);

		hello.say_hello ();
	}
}
```

The above is about 200 lines of code in GObjectified C.

> **LuisAugusto said:**
> I knew what your point was, yet, It's still irrelevant.

Well, there is always one way to improve the documentation.

---

### Post by cdekter on 2009-01-19
As an application developer myself, I have to say, QT is definitely easier to work with. There are several aspects of GTK that are frustrating and slow down development:

[LIST]
[*]Documentation is in some cases very poor. You spend a lot of time looking for code examples because things are not documented. (This is a BIG one)
[*]Some things simply don't work (drag and drop in the treeview control for example)
[*]Some of the controls are very unsophisticated compared to their QT counterparts (treeview a culprit here again!)
[*]The designers available (e.g. Glade) can't realistically be used for complex user interfaces.
[/LIST]

There is a general feeling with GTK that the development of the toolkit stops as soon as it's "good enough". What happened to innovation and pushing the boundaries? The rate of development on GTK is glacial compared to QT.

Quality applications need a quality foundation. Furthermore, to encourage developers across to Linux, high quality documentation and examples are needed. This has already been mentioned earlier in this thread.

While I don't think that the choice should be removed from developers, realistically slimming down to just one main toolkit would free up a lot of resources for more useful things. Choice is a good thing, but is this not a case of alternatives just for the sake of having choice?

---

### Post by cdekter on 2009-01-19
> **maxiboy said:**
> i'm going to have to say that good docs are good docs, no matter how many people were or weren't paid to write them.

+1

---

### Post by mips on 2009-01-19
> **cdekter said:**
>  The rate of development on GTK is glacial compared to QT.



Be carefull with that statement, apparently with global warming glaciers are moving a lot faster these days :)

---

### Post by handy on 2009-01-19
> **mips said:**
> Be carefull with that statement, apparently with global warming glaciers are moving a lot faster these days :)

I was tempted to report you for breaking the CoC. ***[Edit:]*** ;-)

---

### Post by Changturkey on 2009-01-19
> **handy said:**
> I was tempted to report you for breaking the CoC.

???

---

### Post by Vadi on 2009-01-19
I do agree that Qt is better documented. However, working with both, GTK+ here has the advantage that #gtk+ is actually filled with people who write gtk, unlike #qt. I received much better help in #gtk+ from people who actually write the thing than people who just use it in #qt. This is just my case so far though - and I've been pleased.

DnD works fine in treeview ([lots of tutorials]("http://www.kksou.com/php-gtk2/index.php?option=com_googlesearch_cse&n=30&Itemid=114&cx=partner-pub-5032765168656743%3Aost4rr-en3s&cof=FORID%3A11&ie=ISO-8859-1&q=treeview+drag&hl=en#1125")), I'm not sure what do you mean about that. Glade is great for designing too - while it indeed misses the "signals" feature of the designer, it fills in the gaps by having a usable method for laying out tables and such. You can just punch in a number - instead of trying to move the damned mouse by 1px or keep breaking your layout, arrange, and layout again.

Really though it's more like the personal preference of what do you prefer / are told by your boss to work with (qt is preferred more for cross-platform apps, even though gtk works cross-platform just fine and even without x11 on macs)

---

### Post by Ub1476 on 2009-01-19
This just came up on PlanetGnome:

> Alexander Neundorf from KDE wonders what's up in GNOME land, specifically about Vala and what's up with it. As his blogging system requires me to sing up for an account in kdedevelopers.org and getting approval from someone (even going through OpenID) I decided to answer in my blog.

Alexander GNOME 3.0 and Gtk+ 3.0 are sticking to C. Actually, the core of GNOME won't move away from C, GObject is the core of our technology, we are happy with it. Anyone willing to see GNOME moving away from that will have to hold his hopes.

Now, one of the main points for us using C is that it makes our life easier when we bind our APIs to other platforms, it also allows not only to bind easily, but to make very platform-alike APIs integrated with the STL in the case of C++, being very Pythonic in PyGtk, very .NET-ish in the case of C# and so on...
Our vision is that the core is done in C, and you write your apps on whatever platform you like.

Now, Vala is not really something to replace C, rather than something that allow us to use C and GObject in a much more usable way. The Vala compiler is a C#-like language that translate C#-like objects to C using GObject.

The "write your stuff on whatever platform you like" point has a risk, we end up having leaks on how much can we reuse from what people build on top of their platforms. Most people are not willing to write new widgets on C because GObject despite its wonders, is tedious to write and all the boilerplate involved is quite scary.

This is where Vala comes in. Vala allows you to write stuff in a high level language (actually, Mono/C# stuff is quite easy to port to Vala) and then that stuff you write is core-compilant, meaning it's something that could go to the GNOME libraries and being reused by the whole stack. Not to note that it's actually a very powerful GObject learning tool as you can check what the C output is for the Vala code you write.

Now, Vala is no all wonders, it still needs work on the documentation side, and the APIs are not fully stable (they'll be stable as soon as GObject-Introspection is stable ;-), however, at the moment it already is a great tool for fast prototyping of things that would potentially go in the core and write apps based on already well tested APIs (which is the case for the most common stuff already).

As for the general trend, there's no general trend at the moment, some people are trying Vala and I have not heard anyone in the community being against it, some people are using some brand new JavaScript-GObject bridges using GObject-Introspection (the guys doing 3.0's desktop shell for example).

But there's not such thing as GNOME 3.0 would be in language X. We are happy with C, and we will stick to C so that others can use our stuff and stick to whatever they already use at the same time.

I wonder if this post is making you feel any less confused. :-)

---

### Post by Xanatos Craven on 2009-01-19
> I'm lost. VLC is a Qt application and somebody was bitching because it's dialog look out of place. I just said, yes, they do, but GNOME dialogs suck anyway, never intent to speak of gtk itself or any other issue.
Wow, I've seen this complaint on here a lot. I don't understand why somebody doesn't just make their own dialog or something if so many people hate it... this is open-source, isn't it? Wasn't there some software that let you replace GTK file dialogs with KDE ones? Shouldn't replacing the GTK default dialog with a different GTK  dialog be just as possible?

---

### Post by LuisAugusto on 2009-01-19
I use KDE 4.2 and its dialogs are quite good.

GNOME dialogs are damn awful, actually, the Qt dialog of VLC is better XD

---

### Post by Tibuda on 2009-01-19
> **Xanatos Craven said:**
> Wow, I've seen this complaint on here a lot. I don't understand why somebody doesn't just make their own dialog or something if so many people hate it... this is open-source, isn't it? Wasn't there some software that let you replace GTK file dialogs with KDE ones? Shouldn't replacing the GTK default dialog with a different GTK  dialog be just as possible?

I like GTK dialogs, but this is a good idea for both toolkits.

---

### Post by etnlIcarus on 2009-01-20
> **Xanatos Craven said:**
> Wow, I've seen this complaint on here a lot. I don't understand why somebody doesn't just make their own dialog or something if so many people hate it... this is open-source, isn't it? Your response isn't particularly original, either.

> **danielrmt said:**
> I like GTK dialogsThis. File picker =/= file manager. GTK+ file pickers certainly have their limitations (to be unoriginal myself: how 'bout a thumbnail view?) but I maintain that file pickers should not replicate 99% of the average file manager's functionality, nor should it be almost indistinguishable from the genuine product; it's bloody confusing.



As for the original topic, while I would never have said this during the Qt3 days, I've been much more comfortable with Qt4 apps and Qt4 certainly has it's advantages over GTK+: I wouldn't be vehemently opposed to standarisation upon Qt4. 

My only concern is I run a relatively antiquated PC and Qt4 apps tend to be more sluggish than their Gtk+ counterparts. Running the full KDE 4.x slows my system to a crawl (so much for 4 being lighter than 3, as some proponents claimed), even with a lot of the graphical load being lifted by accelerated compositing. I wonder if, lets say, Xfce moved to Qt4: how much more is my system going to suffer for it?

---

### Post by geoken on 2009-01-20
> **etnlIcarus said:**
>  but I maintain that file pickers should not replicate 99% of the average file manager's functionality, nor should it be almost indistinguishable from the genuine product; it's bloody confusing.


Why not?

Most of us use our file managers to organize our files and make specific organizational decisions based on the strengths and weaknesses of those file managers. 

For example, going with the thumbnail point you brought up, my project folders usually have image assets in them with very non-descript names. When I have 15 or less image assets they'll usually be named img01.jpeg and so on. It just makes the process of batch resizing easier and since my file manager shows me thumbnails there's no need to spend the time renaming. This is an example of my file organization method reflecting the strengths of my file manager which will obviously be impacted by a less capable file picker.

---

### Post by CarpKing on 2009-01-20
GTK filechooser does show thumbnails now; you just have to click a file before you see it at a useful size.  A more traditional thumbnail view would be welcome, though.

---

### Post by CraigPaleo on 2009-01-20
> **CarpKing said:**
> GTK filechooser does show thumbnails now; you just have to click a file before you see it at a useful size.  A more traditional thumbnail view would be welcome, though.

It does but when you click on the file to see the thumbnail, the name of the file you are saving (if you're downloading or saving a file) changes to the one you've clicked. So you have to go back and change the name or replace the file you last clicked. 

It'd be great if it showed the thumbnail when single clicking and then gave you the option to replace the file by double clicking.

---

### Post by bfc on 2009-01-20
Maybe this is a start....

[http://www.computerworld.com.au/article/273605/move_over_gnome_ubuntu_mobile_looks_qt_other_desktop_environments]("http://www.computerworld.com.au/article/273605/move_over_gnome_ubuntu_mobile_looks_qt_other_desktop_environments")

---

### Post by Vadi on 2009-01-20
It's not a start, because the guy said they'll look at Qt since now it is possible. It's very reasonable to consider your every option - but defintiely doesn't mean that you'll use it.

---

### Post by etnlIcarus on 2009-01-20
> **geoken said:**
> Why not?You explained why, yourself:

> **geoken said:**
> Most of us use our file managers to organize our files and make specific organizational decisions based on the strengths and weaknesses of those file managers.

You don't do that with a file picker. A file picker's main goal is to "pick" a file, not organise large or even small numbers of files. A file *manager* is the wrong metaphor to use for something that is meant to allow you to navigate down a directory tree quickly with a minimum of fuss. The GTK+ file picker does this very well - I can do what I need to do faster with the GTK+ picker than I can with it's Windows/KDE equivalents in a default configuration (switching to the details view mode helps).

---

### Post by LuisAugusto on 2009-01-20
> **etnlIcarus said:**
> You don't do that with a file picker. A file picker's main goal is to "pick" a file, not organise large or even small numbers of files. A file *manager* is the wrong metaphor to use for something that is meant to allow you to navigate down a directory tree quickly with a minimum of fuss. The GTK+ file picker does this very well - I can do what I need to do faster with the GTK+ picker than I can with it's Windows/KDE equivalents in a default configuration (switching to the details view mode helps).

Suure.......

[[IMG]http://img255.imageshack.us/img255/3054/dialog1mu9.th.png[/IMG]](http://img255.imageshack.us/img255/3054/dialog1mu9.png)

Just in case you're a fan of detail views:

[[IMG]http://img177.imageshack.us/img177/6663/dialog2lr8.th.png[/IMG]](http://img177.imageshack.us/img177/6663/dialog2lr8.png)

I like GNOME, but their file picker sucks, it wastes more space, offers less, and looks like crap (and let's not even mention how it behaves when you're trying to find an image...).

---

### Post by etnlIcarus on 2009-01-21
> **LuisAugusto said:**
> Suure.......

[[IMG]http://img255.imageshack.us/img255/3054/dialog1mu9.th.png[/IMG]](http://img255.imageshack.us/img255/3054/dialog1mu9.png)

Just in case you're a fan of detail views:

[[IMG]http://img177.imageshack.us/img177/6663/dialog2lr8.th.png[/IMG]](http://img177.imageshack.us/img177/6663/dialog2lr8.png)I'm not sure what point you're making. Care to elaborate?

> I like GNOME, but their file picker sucks, it wastes more space, offers less, and looks like crap (and let's not even mention how it behaves when you're trying to find an image...).Agreed, it has problems.

---

### Post by LuisAugusto on 2009-01-21
> **etnlIcarus said:**
> Agreed, it has problems.

Exactly those I mentioned later, perhaps I should have put those first instead of the screenshots.

Just by looking at them, it's obvious for me how wrong the gnome dialog is, less functionality in more space, even with less in more space, it still looks a lot more cluttered. It's ugly as hell too.

If you're looking for images, you're pretty much screwed up, since you have to click on every file to preview it, and... (I dunno if it's a gnome dialog per se) the approach The GIMP uses is extremely lame, buggy, ugly, cluttered, slower, etc.

---

### Post by bruce89 on 2009-01-21
I find that saying GTK+ should be dropped because of its filechooser rather odd.

Perhaps someone can implement a new dialogue that implements the GtkFileChooser interface, then you can stop moaning.

Anyway, this entire argument is blind to the technical practicalities of such a venture.

---

### Post by LuisAugusto on 2009-01-21
> **bruce89 said:**
> ***I find that saying GTK+ should be dropped because of its filechooser rather odd.***

Perhaps someone can implement a new dialogue that implements the GtkFileChooser interface, then you can stop moaning.

Anyway, this entire argument is blind to the technical practicalities of such a venture.

I never said that... >.>  

...And I don't recall anybody saying it.

---

### Post by bruce89 on 2009-01-21
> **LuisAugusto said:**
> I never said that... >.>  

...And I don't recall anybody saying it.

I was trying to bring this thread back to the original purpose.

But seriously, there's nothing stopping someone implementing a "proper" file dialogue. Even a simple subclass of GtkFileChooserDialog would do.

---

### Post by LuisAugusto on 2009-01-21
> **bruce89 said:**
> I was trying to bring this thread back to the original purpose.

But seriously, there's nothing stopping someone implementing a "proper" file dialogue. Even a simple subclass of GtkFileChooserDialog would do.

Yeah ;-)

Anyway, the "implement yourself" answer was an excuse before, and still is XD.

-------------

Back to the issue. Ubuntu Notebook remix deciding to "think" about going Qt just because of the change from LPGL to GPL is very odd, and proves how developers bashed Qt without a reason (why is it being considered now that is LPGL, and wasn't while being GPL? It's a non-sense for open source developers, unless the GPL isn't a free license anymore)

I don't want GTK to vanish, but I do think Qt is going to be use a lot more now, and that's a good thing, since it's outstanding.

---

### Post by bruce89 on 2009-01-21
> **LuisAugusto said:**
> Anyway, the "implement yourself" answer was an excuse before, and still is XD.

I thought the whole point of FOSS was ability to do be able to do things yourself.

> **LuisAugusto said:**
> Back to the issue. Ubuntu Notebook remix deciding to "think" about going Qt just because of the change from LPGL to GPL is very odd, and proves how developers bashed Qt without a reason (why is it being considered now that is LPGL, and wasn't while being GPL? It's a non-sense for open source developers, unless the GPL isn't a free license anymore)

GPL prohibits commercial use, all derived work has to be GPL as well. Qt has a thing which allowed developers to use some non-GPL licences as well, but they had to be Free.

The LGPL doesn't have restrictions on what licences derived works can use.

The Ubuntu Netbook people are worried that no-one is using it, Intel for instance. No amount of wasting time like this will help them.

---

### Post by LuisAugusto on 2009-01-21
> **bruce89 said:**
> I thought the whole point of FOSS was ability to do be able to do things yourself.

Not everybody wants, or cares enough, nor they have to know how to do it.GNOME dialogs lame design isn't my fault, and it isn't the fault of everybody who complained about it either.

It's GNOME devs fault, if they want to hide it by excusing themselves, that's their problem too.

> **bruce89 said:**
> GPL prohibits commercial use, all derived work has to be GPL as well. Qt has a thing which allowed developers to use some non-GPL licences as well, but they had to be Free.

The LGPL doesn't have restrictions on what licences derived works can use.

The Ubuntu Netbook people are worried that no-one is using it, Intel for instance. No amount of wasting time like this will help them.

Ok, you're wrong. The GPL DOESN'T PROHIBIT COMMERCIAL USE. It has to remain free, which is irrelevant for an open source developer, since, he will develop an... open source application, only those who want to use the library for closed source are affected. I do think releasing Qt as LPGL it's a good marketing strategy, specially, since I don't have anything against closed source.

But bare in mind, that FOSS community attitude towards Qt being GPL was hypocrite at best.

---

### Post by bruce89 on 2009-01-21
> **LuisAugusto said:**
> Not everybody wants, or cares enough, nor they have to know how to do it.GNOME dialogs lame design isn't my fault, and it isn't the fault of everybody who complained about it either.

It's GNOME devs fault, if they want to hide it by excusing themselves, that's their problem too.

I assure you that they designed them (which other dialogues are no good?) this way for a good reason. I don't know what, but there's no need to blame people for having principles.

Any suggestions are welcome (AFAIK no-one's ever actually proposed a change, as they say it would be rejected).

---

### Post by LuisAugusto on 2009-01-21
> **bruce89 said:**
> I assure you that they designed them (which other dialogues are no good?) this way for a good reason. I don't know what, but there's no need to blame people for having principles.

Any suggestions are welcome (AFAIK no-one's ever actually proposed a change, as they say it would be rejected).

I assure Microsoft made Windows ME that way for a good reason... Come on, those cheap arguments aren't gonna work with me XD.

They could have done it with the best intention, but the reality, is that they suck. Their intentions are completely irrelevant.

Oh, and for suggestions, they just have to look around to find them. Vista dialogs, KDE dialogs, Qt dialogs, etc.

---

### Post by bruce89 on 2009-01-21
> **LuisAugusto said:**
> I assure Microsoft made Windows ME that way for a good reason... Come on, those cheap arguments aren't gonna work with me XD.

They could have done it with the best intention, but the reality, is that they suck. Their intentions are completely irrelevant.

Nothing stops people from filing a bug. Here's one - [http://bugzilla.gnome.org/show_bug.cgi?id=325150](http://bugzilla.gnome.org/show_bug.cgi?id=325150)

Anyway, this is completely off-course.

---

### Post by etnlIcarus on 2009-01-21
> **LuisAugusto said:**
> Just by looking at them, it's obvious for me how wrong the gnome dialog is, less functionality in more space, even with less in more space, it still looks a lot more cluttered. It's ugly as hell too.I guess we're going to have to chalk this one up to perceptive differences.

I agree that the gtk+ dialogue has a bit of wasted space, thoroughly disagree with your, "cluttered", assessment, though. Don't really care that it's ugly but then again, I don't consider the other file picker to be particularly glamorous looking, either; there are tools we're talking about, not the cornerstone of desktop style (this coming from someone who admittedly wastes a lot of time in the desktop screenshot thread).

Really, though, this is all a tangent of a tangent. I didn't mean to get into a broad critique, I simply think that managers/pickers should remain distinct from one other and, as a matter of personal experience, I said that I do get confused by pickers which look and behave like managers.

FTR, though, if I ever got off my butt and continued teaching myself how to code, I would totally create my dream file picker:

[img]http://img93.imageshack.us/img93/6866/dreamfilepickerjo9.png[/img]

Yes, I made that with mspaint. Is it my fault it has no *nix FOSS equivalent?

Edit: Come to think of it, I probably could have fired up Glade and created a mockup just as quickly. >.>

---

### Post by MaxIBoy on 2009-01-21
What about xpaint? (Ouch. Sorry, MS.)

---

### Post by LuisAugusto on 2009-01-21
> **etnlIcarus said:**
> I guess we're going to have to chalk this one up to perceptive differences.

I agree that the gtk+ dialogue has a bit of wasted space, thoroughly disagree with your, "cluttered", assessment, though. Don't really care that it's ugly but then again, I don't consider the other file picker to be particularly glamorous looking, either; there are tools we're talking about, not the cornerstone of desktop style (this coming from someone who admittedly wastes a lot of time in the desktop screenshot thread).

Really, though, this is all a tangent of a tangent. I didn't mean to get into a broad critique, I simply think that managers/pickers should remain distinct from one other and, as a matter of personal experience, I said that I do get confused by pickers which look and behave like managers.

FTR, though, if I ever got off my butt and continued teaching myself how to code, I would totally create my dream file picker:

[img]http://img93.imageshack.us/img93/6866/dreamfilepickerjo9.png[/img]

Yes, I made that with mspaint. Is it my fault it has no *nix FOSS equivalent?

Ehem, it's more cluttered. Just by the fact that's is showing unnecessary scrollbars ;-)

KDE dialog behaves well in the same amount of space, if you want to change the view mode, you can, on the fly, if you want to look for pictures without spending centuries clicking on every file, you click on thumbnails, and increase the zoom, etc. It's a better designed dialog.

And your dialog (with all respect) is broken by design, we have less vertical space, so we should try to use it less, since we will run out of it pretty fast, using horizontal space is 90% of the times a better approach (yours is too similar to the GIMP dialog, which is the worst).

-----------

Hey! What about Kolourpaint! XD

------------

> **bruce89 said:**
> Nothing stops people from filing a bug. Here's one - [http://bugzilla.gnome.org/show_bug.cgi?id=325150](http://bugzilla.gnome.org/show_bug.cgi?id=325150)

Anyway, this is completely off-course.

Nope, but stop trying to make it look as it was the users fault.

---

### Post by etnlIcarus on 2009-01-21
> And your dialog (with all respect) is broken by design, we have less vertical space, so we should try to use it less, since we will run out of it pretty fast, using horizontal space is 90% of the times a better approach (yours is too similar to the GIMP dialog, which is the worst).To be fair, I only put places there 'cause the kids seem to love it and having it as a sidebar wastes a lot of space since I don't use it, therefore, there's a lot of empty space where custom 'shortcuts' should be.

The important thing to note is my design doesn't have a screwy visual hierarchy; the file operations tools are well defined from the rest of the interface, sitting atop to properly represent the fact that they're a controlling and significant element.

---

### Post by bruce89 on 2009-01-21
> **LuisAugusto said:**
> Nope, but stop trying to make it look as it was the users fault.

There is no fault here.

The problem here is that it's impossible to please everyone. Buttons for renaming and moving files would make the thing too cluttered, but context menu options for them would be reasonable (probably only for renaming).

It's also quite complex to actually do, as the file chooser is implemented in a very abstract way (the dialogue contains a widget which implements an interface), and because of the past backend plugins (gnome-vfs for instance).

---

### Post by LuisAugusto on 2009-01-21
> **bruce89 said:**
> There is no fault here.

Yeah, the GNOME dialog is perfect (watches my unicorn smile)

> **bruce89 said:**
> The problem here is that it's impossible to please everyone. Buttons for renaming and moving files would make the thing too cluttered, but context menu options for them would be reasonable (probably only for renaming).

It's also quite complex to actually do, as the file chooser is implemented in a very abstract way (the dialogue contains a widget which implements an interface), and because of the past backend plugins (gnome-vfs for instance).

Their problem, I'm just pointing out how bad the design is. I dunno how KDE devs resolved to put all those features there without cluttering the interface... And renaming and deleting files don't clutter anything, since they're usually accessed by right clicking or with the keyboard. 

> **etnlIcarus said:**
> To be fair, I only put places there 'cause the kids seem to love it and having it as a sidebar wastes a lot of space since I don't use it, therefore, there's a lot of empty space where custom 'shortcuts' should be.

Actually, it will waste more space vertically, unless you make your dialog wider.

> **etnlIcarus said:**
> The important thing to note is my design doesn't have a screwy visual hierarchy; the file operations tools are well defined from the rest of the interface, sitting atop to properly represent the fact that they're a controlling and significant element.

Which is the same thing that most dialogs do, if you actually see the KDE dialog does have this hierarchy (File path on top, folders down). File name is well placed down there, since is the last thing you will be doing (is a visual movement, you'll go from top to bottom after browsing with the file path and then the folders themselves).

---

### Post by etnlIcarus on 2009-01-21
> File name is well placed down there, since is the last thing you will be doing It's only the last thing you will be doing because it's, "down there". Nice circular logic.

> (is a visual movement, you'll go from top to bottom after browsing with the file path and then the folders themselves).Just curious, got any other examples of this in a task-context? 

And the Qt/windows file pickers do not define their separate tasks well but I'm guessing you don't dispute that since, well, you didn't dispute that.

---

### Post by LuisAugusto on 2009-01-21
> **etnlIcarus said:**
> It's only the last thing you will be doing because it's, "down there". Nice circular logic.

Just curious, got any other examples of this in a task-context? 

And the Qt/windows file pickers do not define their separate tasks well but I'm guessing you don't dispute that since, well, you didn't dispute that.

No, I'll make a draw in Paint too XD:

[IMG]http://img443.imageshack.us/img443/86/dialogiu4.jpg[/IMG]

---

### Post by etnlIcarus on 2009-01-21
Mouse movement doesn't increase, you merely go in the opposite direction after picking a file (which isn't a linear movement anyway). Besides that, I don't consider that a real problem. Outside of The GIMP or using Mac OS, I've never felt that I've had to move the mouse too much.

As for point 2, that's not really a criticism. You're simply returning to a dominant controlling element. You know that it's a dominant controlling element because it sits above the other elements. Tutoring, I don't know how many times people have either forgotten to *name their files* or once finding their file, have rolled their eyes around the screen looking for the equivalent of the, "Next", button.

---

### Post by LuisAugusto on 2009-01-21
It does increase:

[IMG]http://img530.imageshack.us/img530/2994/dialogjv2.jpg[/IMG]

---

### Post by etnlIcarus on 2009-01-21
Your diagrams aren't really helping much. The difference (if we ignore that the browsing portion of our task in the middle is a complex mouse task, not a linear motion as you're suggesting) is we have a U-shaped or V-shaped mouse movement, rather than a straight diagonal line movement. There's no reason the mouse has to travel further*.


*if we really want to get into a semantic argument, U or V-shaped motion of same distance to \-shaped motion halves the total amount of *area* the mouse has to cover.

Anyway, this is getting more than a little ridiculous. Call it a day and agree to disagree?

---

### Post by LuisAugusto on 2009-01-22
That the point, you're misunderstanding the browsing part, it isn't complex, in the rarest case scenario, the user will select the first file. In most scenarios he will scroll the list, which means he will go down. You'll never go up, that's the point.

---

### Post by etnlIcarus on 2009-01-22
...do you keep every file on your computer in your $HOME directory?

And even if I accept that browsing consists only of 'scrolling a list' (I don't, in case you can't detect sarcasm), my point remains intact. *Distance* is not the same thing as *direction*.

---

### Post by LuisAugusto on 2009-01-22
Do you have 10 files per folder? Because my music folder has a hell lot of files unsorted, same with my pictures folder.

The browsing, specially in your approach, it's just a scroll list, unless it's among the first 3 itmes on the list (which is by pure logic, very unlikely), you're just increasing the amount of space the mouse will move by. If you aren't willing to accept such a simple fact, it's beyond me.

---

### Post by smartboyathome on 2009-01-22
> **LuisAugusto said:**
> Do you have 10 files per folder? Because my music folder has a hell lot of files unsorted, same with my pictures folder.

The browsing, specially in your approach, it's just a scroll list, unless it's among the first 3 itmes on the list (which is by pure logic, very unlikely), you're just increasing the amount of space the mouse will move by. If you aren't willing to accept such a simple fact, it's beyond me.

I usually just click anywhere in the file picker and start typing the name of the file. It automatically goes to it. Problem solved. ;)

---

### Post by LuisAugusto on 2009-01-22
> **smartboyathome said:**
> I usually just click anywhere in the file picker and start typing the name of the file. It automatically goes to it. Problem solved. ;)

Then I guess you do have everything on your home folder, otherwise, it doesn't work that way.

---

### Post by etnlIcarus on 2009-01-22
> **LuisAugusto said:**
> Do you have 10 files per folder? Because my music folder has a hell lot of files unsorted, same with my pictures folder.

The browsing, specially in your approach, it's just a scroll list, unless it's among the first 3 itmes on the list (which is by pure logic, very unlikely), you're just increasing the amount of space the mouse will move by. If you aren't willing to accept such a simple fact, it's beyond me.At this point, I think you're just being intentionally silly; confusing different points just to see how much patience I have. That or you don't actually use the computer much, or have a lot of data.
> **smartboyathome said:**
> I usually just click anywhere in the file picker and start typing the name of the file. It automatically goes to it. Problem solved. ;)
I do the same thing with half the apps I use. Shame other OSes haven't really cottoned on to the idea.

---

### Post by smartboyathome on 2009-01-22
> **LuisAugusto said:**
> Then I guess you do have everything on your home folder, otherwise, it doesn't work that way.

No, I navigate to the folder I want (I usually use the path editor), and then do what I said above.

---

### Post by mcduck on 2009-01-22
I'm still waiting to see a pretty Qt theme..

So answer is no, it shouldn't be any more standard toolkit than it is now. I'm very happy with current situation, people being able to choose between two available toolkits. I don't see any reason why this choice should be removed. If you like Qt better use KDE, if you like Gtk then use Gnome. Or mix them as you like.

---

### Post by LuisAugusto on 2009-01-22
> **smartboyathome said:**
> No, I navigate to the folder I want (I usually use the path editor), and then do what I said above.

Oh, I see, I use the GNOME dialog that way too XD.

------------

Bespin and Oxygen are very good looking on my eyes (just like Dust is gorgeous too).

---

