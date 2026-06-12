---
title: "Ubuntu Developers API -  your thoughts ?"
date: 2011-01-07
forum: The Cafe
---

### Post by Shpongle on 2011-01-07
I was just thinking  , that canonical should provide an API for developers to fully take advantage of the USC .  I mean it "**seems**" they are just sitting around waiting for people to jump on it. Look at google and apple they developed their stores and framework and they're away. So far the only progress I have seen with the USC seems to be a different interface for apt...sure It may seem more user friendly but synaptic allows more options as your aware. 

I know its easier said than done but I think it would help increase adoption as a development platform.   know google / apple are multi billion dollar companies etc. Im more interested in the idea

What do yous think ?

---

### Post by chriswyatt on 2011-01-07
Don't Google and Apple also basically sit around waiting for developers to submit their applications?  I think it mostly boils down to more demand for paid apps and more people paying for them.

An Ubuntu mobile which bridged the gap between the Ubuntu PC and the mobile phone would be sweet.  Games that you downloaded on the phone could be easily ported for the PC and vice-versa.  Would even be neat that if you bought a game on your phone you could play it on your PC as well.

---

### Post by Shpongle on 2011-01-07
> **chriswyatt said:**
> Don't Google and Apple also basically sit around waiting for developers to submit their applications?  I think it mostly boils down to more demand for paid apps and more people paying for them.

An Ubuntu mobile which bridged the gap between the Ubuntu PC and the mobile phone would be sweet.  Games that you downloaded on the phone could be easily ported for the PC and vice-versa.  Would even be neat that if you bought a game on your phone you could play it on your PC as well.

Yea but google and apple make it easier to develop those said applications. There is ubuntu documentation for getting stuff to work - a lot of which is dated but not really for development. 

Note Im not saying it for me personally . Mainly for those who would not be familiar with porting to the platform

---

### Post by zekopeko on 2011-01-07
> **Shpongle said:**
> I was just thinking  , that canonical should provide an API for developers to fully take advantage of the USC .  I mean it "**seems**" they are just sitting around waiting for people to jump on it. Look at google and apple they developed their stores and framework and they're away. So far the only progress I have seen with the USC seems to be a different interface for apt...sure It may seem more user friendly but synaptic allows more options as your aware. 

I know its easier said than done but I think it would help increase adoption as a development platform.   know google / apple are multi billion dollar companies etc. Im more interested in the idea

What do yous think ?

I completely agree with you. It's not really about USC but the entire "Ubuntu" platform. If you compare Windows' and Apple's web portal for developers you will see a stark difference in quality. They really provide a great experience for developers.

You can looks at [Matthew Paul Thomas' talk]("http://www.youtube.com/watch?v=GT5fUcMUfYg") on how to get great apps on Ubuntu. It's really informative.

---

### Post by Shpongle on 2011-01-07
Cool I will thanks, Its just that lately especially being close to finishing my degree Im starting to think about how I can contribute back and I can do it without an API but having no solid reference slows you down a hell of a lot and If google turns up empty your hoping someone knows how to do or can suggest how to go about whatever it is your trying to do.

---

### Post by earthpigg on 2011-01-07
Wouldn't this be as simple as saying "Hey developers, use Java or Mono and GTK"??

---

### Post by jerenept on 2011-01-07
> **earthpigg said:**
> Wouldn't this be as simple as saying "Hey developers, use Java or Mono and GTK"??

Mono or Java seems to be the best options. Most developers would be already familiar with .NET/Java programming.

---

### Post by Shpongle on 2011-01-07
See zekopeko's link it explains it better than I could.

---

### Post by zekopeko on 2011-01-07
> **earthpigg said:**
> Wouldn't this be as simple as saying "Hey developers, use Java or Mono and GTK"??

No. You have to provide platform integration, code examples, documentation for API interfaces etc. Packaging really needs to become a super simply procedure: fill a form (author, license etc.) and click "Make an Ubuntu package". The language is simply icing on the cake and should be irrelevant for the most part (assuming it's properly supported).

The process of getting apps into Ubuntu repos needs to get super easy. IMO the current model of not updating desktop apps should be abandoned. We should have a core OS and an app layer. I shouldn't upgrade my entire OS just to get the new version of Tomboy, neither should I have to install PPAs that overwrite system libraries and potentially brake older apps that depend on them.

I think that they seriously need to make Monodevelop the official IDE and invest some time into improving its Python, Javascript and Vala/C support.

---

### Post by juancarlospaco on 2011-01-07
> **jerenept said:**
> Mono or Java seems to be the best options. 

No.

---

### Post by zekopeko on 2011-01-07
> **juancarlospaco said:**
> No.

Actually it's yes. Mono even more so since it's cross platform and would allow for people to have their Ubuntu apps on Windows and Mac.

---

### Post by rg4w on 2011-01-07
> **zekopeko said:**
> No. You have to provide platform integration, code examples, documentation for API interfaces etc. Packaging really needs to become a super simply procedure: fill a form (author, license etc.) and click "Make an Ubuntu package". The language is simply icing on the cake and should be irrelevant for the most part (assuming it's properly supported).

The process of getting apps into Ubuntu repos needs to get super easy.
I can't say "Amen!" loud enough.

I was really glad zekopeko posted the link to the Matthew Paul Thomas video - I was about to dig it up when I saw this thread.

If I were Mr. Shuttleworth I'd pick some of the devs who work on the USC and I'd give them a choice:  they can either be strapped into a chair with eyelids clipped open a la Clockwork Orange and be made to watch the Thomas video for three weeks straight over and over in a mind-bending loop, or spend that three weeks building the best GUI deb packager the world has ever seen. :)

Once that's underway I'd find some volunteers to work on the approval process, and I'd make it so easy for devs to get apps into the hands of Ubuntu fans they'll feel stupid if they don't.

For all the great things going on with the OS itself that I'm very grateful for, I'd love to see 2011 become The Year of the Ubuntu App, where one the key focal points becomes identifying and resolving any hurdles that stand between developers and a million great new apps.

---

### Post by sudoer541 on 2011-01-07
Why dont you guys contact Canonical and tell them to improve their API? 
They will appreciate the feedback from existing Ubuntu users. :)

---

### Post by zekopeko on 2011-01-08
> **sudoer541 said:**
> Why dont you guys contact Canonical and tell them to improve their API? 
They will appreciate the feedback from existing Ubuntu users. :)

The closest thing that Ubuntu has to an API is Quickly which is a purely Python framework, Launchpad and the Ayatana project.

---

### Post by JDShu on 2011-01-08
> **zekopeko said:**
> No. You have to provide platform integration, code examples, documentation for API interfaces etc. Packaging really needs to become a super simply procedure: fill a form (author, license etc.) and click "Make an Ubuntu package". The language is simply icing on the cake and should be irrelevant for the most part (assuming it's properly supported).


This would be awesome. You think its possible? I find DPMS prohibitively hard to use.

---

### Post by zekopeko on 2011-01-08
> **JDShu said:**
> This would be awesome. You think its possible? I find DPMS prohibitively hard to use.

I have no idea since the only debs I ever did was with checkinstall. I'm just expressing my opinion after examining developer feedback. 

If developers have to ask other people to package their software for Ubuntu then something is very wrong. That step should be trivial. The hardest part should be actually producing a high quality application not packaging it.

---

### Post by JDShu on 2011-01-08
> **zekopeko said:**
> I have no idea since the only debs I ever did was with checkinstall. I'm just expressing my opinion after examining developer feedback. 

If developers have to ask other people to package their software for Ubuntu then something is very wrong. That step should be trivial. The hardest part should be actually producing a high quality application not packaging it.

I agree, I just wonder if the Linux ecosystem is just too interwoven with the dynamically linked libraries etc. to do it. But I suppose more intelligent people than I will figure it out :)

---

### Post by Mr. Picklesworth on 2011-01-08
> **rg4w said:**
> I can't say "Amen!" loud enough.

I was really glad zekopeko posted the link to the Matthew Paul Thomas video - I was about to dig it up when I saw this thread.

If I were Mr. Shuttleworth I'd pick some of the devs who work on the USC and I'd give them a choice:  they can either be strapped into a chair with eyelids clipped open a la Clockwork Orange and be made to watch the Thomas video for three weeks straight over and over in a mind-bending loop, or spend that three weeks building the best GUI deb packager the world has ever seen. :)

Once that's underway I'd find some volunteers to work on the approval process, and I'd make it so easy for devs to get apps into the hands of Ubuntu fans they'll feel stupid if they don't.

For all the great things going on with the OS itself that I'm very grateful for, I'd love to see 2011 become The Year of the Ubuntu App, where one the key focal points becomes identifying and resolving any hurdles that stand between developers and a million great new apps.

MPT *is* one of the Software Centre developers ;)
I don't think it's really Software Centre's problem. It could do a better job (in particular by killing off a lot of cruft associated with apt repositories), and that's always changing, but what we're worried about here is the process of creating packages and pushing them to Extras (which isn't really a process yet). That is another project's problem, and it is improving!

developer.ubuntu.com is on the way to being more useful. However, so far it is still focused on Brand New Stuff You [S]Get[/S] Need to Learn! I don't think the process is our problem. We don't always need people building new apps, from scratch, with brand new frameworks and languages. We need people feeling confident that their existing tools and knowledge will work to get their existing products working nicely on Ubuntu.

Besides that, helping people push to the Extras repository won't help the fact that the vast majority of apps with Linux releases are distributed in incredibly awful ways. (Push *what*?). For example, the majority of games in the Humble Bundle have one Linux package: an executable .run file that dumps files all over the system. It's getting better (the more recent bundle had *two* Debian packages), but it really needs more love. Why are developers more confident working with these horrible install scripts than building simple Debian and RPM packages? How can we help them?

Once all those developers are happy making Deb packages and distributing on their own websites, maybe it will be easy for them to submit those same packages to the Extras repository.
Until then, let's think about the real problem.

---

### Post by zekopeko on 2011-01-08
> **Mr. Picklesworth said:**
> developer.ubuntu.com is on the way to being more useful. However, so far it is still focused on Brand New Stuff You [S]Get[/S] Need to Learn! I don't think the process is our problem. We don't always need people building new apps, from scratch, with brand new frameworks and languages. We need people feeling confident that their existing tools and knowledge will work to get their existing products working nicely on Ubuntu.

developer.ubuntu.com looks like a nice start. But I hope it becomes much, much more. My point was that as Ubuntu has default apps it ships so it should have a default developer platform. Apple has XCode and all the Core* frameworks, Microsoft has Visual Studio and Win32/.NET APIs. What is the equivalent in Ubuntu?

> Besides that, helping people push to the Extras repository won't help the fact that the vast majority of apps with Linux releases are distributed in incredibly awful ways. (Push *what*?). For example, the majority of games in the Humble Bundle have one Linux package: an executable .run file that dumps files all over the system. It's getting better (the more recent bundle had *two* Debian packages), but it really needs more love. Why are developers more confident working with these horrible install scripts than building simple Debian and RPM packages? How can we help them?

They are doing it because the "simple Debian and RPM packages" apparently aren't so simple. Don't you find it ridiculous that people can write entire games (and port them) for Linux but can't provide debs? Why isn't this as simple as running an app, pointing it to a directory, marking what version of Ubuntu they are targeting and simply clicking "Make an Ubuntu package"? And it should work on all major distros.

> Once all those developers are happy making Deb packages and distributing on their own websites, maybe it will be easy for them to submit those same packages to the Extras repository.
Until then, let's think about the real problem.

Well obviously the packaging is the hard part then.

---

### Post by zekopeko on 2011-01-08
> **JDShu said:**
> I agree, I just wonder if the Linux ecosystem is just too interwoven with the dynamically linked libraries etc. to do it. But I suppose more intelligent people than I will figure it out :)

I think that the main problem is the ridiculous "no feature" updates after release. We have this amazing repository system with auto-updates but you can't update applications expect for bugfixes and security fixes (if they are supported at all). I would expect the apps to be supported by the app developers and not the OS vendor aka Ubuntu.

Apple basically made a better repository system (for end users) then what existed on Linux distros for the past decade with their Mac App Store.

---

### Post by jeffathehutt on 2011-01-08
> Apple has XCode and all the Core* frameworks, Microsoft has Visual Studio and Win32/.NET APIs. What is the equivalent in Ubuntu?

Ubuntu uses Gnome, so the API would basically be the same as Gnome/gtk, which is well documented and accessible.

> They are doing it because the "simple Debian and RPM packages" apparently aren't so simple. Don't you find it ridiculous that people can write entire games (and port them) for Linux but can't provide debs? Why isn't this as simple as running an app, pointing it to a directory, marking what version of Ubuntu they are targeting and simply clicking "Make an Ubuntu package"? And it should work on all major distros.

But not all major distros use .deb packages.  There are software developers, and there are distribution developers.  Software developers write code, and that is all they should do.  Packaging their program isn't their responsibility.  They provide the source, which the distribution developers then package up for their distribution.  Since it would be silly to expect every application developer to use every distribution out there, they choose instead to hand the source out for others to package for their specific distribution.

> I think that the main problem is the ridiculous "no feature" updates after release. We have this amazing repository system with auto-updates but you can't update applications expect for bugfixes and security fixes (if they are supported at all).

That was an Ubuntu decision, not an application developer one.  Ubuntu chooses to update sparingly to provide a more stable system for the majority of users.  Rolling release distributions on the other hand update as soon as new versions of the programs are released.  So it sounds like your real point here is against Ubuntu, not the developers.  If you want to have up to date software faster, perhaps a rolling release distribution would be more appropriate for you. :)

---

### Post by JDShu on 2011-01-09
> **jeffathehutt said:**
> 
That was an Ubuntu decision, not an application developer one.  Ubuntu chooses to update sparingly to provide a more stable system for the majority of users.  Rolling release distributions on the other hand update as soon as new versions of the programs are released.  So it sounds like your real point here is against Ubuntu, not the developers.  If you want to have up to date software faster, perhaps a rolling release distribution would be more appropriate for you. :)

I think the issue is that rolling releases tend to upgrade core system files which can break compatibility with user applications. I personally do not want to deal with making sure everything is working nicely together. On the other hand, if the responsibility for making an upgraded app work for Ubuntu can be moved from the Ubuntu teams to the app developer, then end users would be able to get the latest versions of the software as long as the developer wants them to.

---

### Post by Mr. Picklesworth on 2011-01-09
> **jeffathehutt said:**
> Ubuntu uses Gnome, so the API would basically be the same as Gnome/gtk, which is well documented and accessible.

It isn't really that simple; we have lots of different components wrapped under completely different projects. They have some things in common like GObject and Cairo, but are typically quite distinct. Against the Win32 and Core* APIs, we really have something more like Gtk / Cairo / libnotify / Canberra / GStreamer.
They talk to each other, but it is daunting at first.

---

### Post by zekopeko on 2011-01-09
> **jeffathehutt said:**
> Ubuntu uses Gnome, so the API would basically be the same as Gnome/gtk, which is well documented and accessible.

But the documentation is pretty scattered. I would like Ubuntu to gather all of this documentation under developer.ubuntu.com. Well not all of it but at least something that is considered official and recommended by the project. A minimum that developers can look at and know what is recommended to use for specific situations. You want to draw 2D stuff? Use Cairo. Want some snazzy interface? Use Clutter. Want sound to work? Use Pulseaudio.


> But not all major distros use .deb packages.  There are software developers, and there are distribution developers.  Software developers write code, and that is all they should do.  Packaging their program isn't their responsibility.  They provide the source, which the distribution developers then package up for their distribution.  Since it would be silly to expect every application developer to use every distribution out there, they choose instead to hand the source out for others to package for their specific distribution.

This is completely ridiculous. Software developers should package their own software. It isn't feasible in the long run if you manage to attract developers to your side. Imagine if Apple would have to package and integrate 300 000 apps on iOS or Google in the Android Marketplace.

> That was an Ubuntu decision, not an application developer one.  Ubuntu chooses to update sparingly to provide a more stable system for the majority of users.  Rolling release distributions on the other hand update as soon as new versions of the programs are released.  So it sounds like your real point here is against Ubuntu, not the developers.  If you want to have up to date software faster, perhaps a rolling release distribution would be more appropriate for you. :)

Well my entire rant was about Ubuntu. The software developers and end users are the victims here. I would really like if Ubuntu had a rolling release like model for applications.

---

### Post by zekopeko on 2011-01-09
> **Mr. Picklesworth said:**
> It isn't really that simple; we have lots of different components wrapped under completely different projects. They have some things in common like GObject and Cairo, but are typically quite distinct. Against the Win32 and Core* APIs, we really have something more like Gtk / Cairo / libnotify / Canberra / GStreamer.
They talk to each other, but it is daunting at first.

Wouldn't it be nice if a developer could simply install Ubuntu and click on an apt-url link which would install an IDE and everything one needs to start developing on Ubuntu?

---

### Post by Shpongle on 2011-01-11
> **zekopeko said:**
> Wouldn't it be nice if a developer could simply install Ubuntu and click on an apt-url link which would install an IDE and everything one needs to start developing on Ubuntu?

This  ^. They could write a development plugin for an existing IDE , like google did with ADT for eclipse.

---

