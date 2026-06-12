---
title: "Ubuntu Package Website"
date: 2005-09-29
forum: The Cafe
---

### Post by philipacamaniac on 2005-09-29
I had this idea about a redesign of packages.ubuntu.com, or possibly just a separate website altogether. Kinda like a web-based frontend for the Ubuntu repositories, but user friendly and fun, like Download.com or Linspire's CNR.
What does everyone think about that idea? Is it something the Ubuntu community could benefit from?

---

### Post by matthew on 2005-09-29
I like the idea. You might take a look at [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") before you go to all the work of designing from scratch. Your implementation looks a lot prettier and would probably have some functionality not in the above site, though.

---

### Post by brentoboy on 2005-09-29
loving it

---

### Post by majikstreet on 2005-09-29
thats hot.

---

### Post by philipacamaniac on 2005-09-29
Okay, good response. I'll contact the [http://packages.ubuntu.com](http://packages.ubuntu.com) to see about using this design. Although, the site is very functional now, especially for developers and advanced users. I think my idea would server better as a separate site (downloads.ubuntu.com?) or as a subsection of the existing site (packages.ubuntu.com/downloads). It will be super-easy to implement in CSS.

---

### Post by Kapre on 2005-09-29
Looks really good!:cool: 

K

---

### Post by Buffalo Soldier on 2005-09-29
i like what i see. the community projects in ubuntu is one of the things i like about this distro.

---

### Post by az on 2005-09-29
[QUOTE=philipacamaniac]Okay, good response. I'll contact the [http://packages.ubuntu.com](http://packages.ubuntu.com) to see about using this design. Although, the site is very functional now, especially for developers and advanced users. I think my idea would server better as a separate site (downloads.ubuntu.com?) or as a subsection of the existing site (packages.ubuntu.com/downloads). It will be super-easy to implement in CSS.[/QUOTE]

Post this on the user's mailing list.  Probably also send an email to Jane Siber from Canonical.  She would give you the right direction as to how to run with this.

The packages.ubuntu.com site is a copy of debian's package site.  It scans the repositories regularly and updates itself.  It saves on processor power by scanning at regular intervals and generating the pages once and caching them.  This is different from the typical contructed-on-demand CMS pages.  I hope this helps.

They (Canonical) love ideas like this, you know.

---

### Post by jdong on 2005-09-29
Excellent idea! Carry forwards -- this is the future of CNR.

I'd love to see a portal built around Ubuntu's main/universe repositories, highlighting special apps, collecting statistics on popular packages, and perhaps even letting users comment about packages and rate them.

---

### Post by poofyhairguy on 2005-09-29
Two things:

1: This is awesome looking.

2. The packages.ubuntu.com site was a community based effort. Yours can be too. Personally though.....I would also try to work with one more party:

[http://klik.atekon.de/ubuntu.php](http://klik.atekon.de/ubuntu.php)

Klik has been trying to make an Ubuntu side for a while. Your idea+ klik could be the ultimate way to install programs (plus would get over the klik site's problem of mixing Debian and Ubuntu sources).

This thing is SOOOOO slick that I bet if you need help you will get it. I will personally say that you can use these boards to recruit help. Please do in fact.

Yet another step on the path of Ubuntu rulling the desktop world!

---

### Post by philipacamaniac on 2005-09-29
Excellent. I'll contact Jane Siber, and then the Klik folks. I can create a working mockup of the frontend, but will probably need help with the CMS backend. 

So possible options on function: 

1. Like packages.ubuntu.com, it provides a download link to the .deb files. You download the deb file and figure out how to install it. Not so hot. 

2. Klik style: packages are debs repackaged as klik cmg packages and can be downloaded and ran instantly. 

3. Somehow become a front-end to apt-get, installing dependencies and so forth. 

4. Actually, the possibility of all 3 sounds rather enticing. A .deb (Download for Manual Installation), a .tar.gz (Download Source), a .cmg (Try it Now With Klik) and some apt-get call (Install).


Ideas for getting it working:

1. Crawling the Ubuntu repositories at regular intervals and creating page caches, much like packages.ubuntu.com. But, I don't want just the .deb file, I want something like serverside-apt to take care of the dependencies and download everything needed when the program is requested.

2. I don't suppose making calls to apt-get from a website is secure.

3 . The existing Klik database could be crawled as well, and links could be added to each application's page. Or Klik packages could be hosted by Canonical, which would be super cool. Perhaps then we would gain support from the community at converting more debs to Klik cmgs.

4. Screenshots and logos might be strange. I could crawl the web and download as many as I can find, and create a script to make them all the same size and format. But there wouldn't be too much automation in this area. When a new application is added to Dapper, for example, I'd have to manually go find a screenshot or make one myself. Then I'd have to grab the logo and make sure it is okay to post it for this purpose. This would be ugly when first setting up the site, but would be easier after the first time. Once all the screenshots and logos are in, updates wouldn't need to be made all that often. And, a script could be written to notify me (or other maintainers) when new packages are available that need screenshots.

---

### Post by poofyhairguy on 2005-09-30
[QUOTE=philipacamaniac]
2. Klik style: packages are debs repackaged as klik cmg packages and can be downloaded and ran instantly. [/QUOTE]

The benefit of this over the old "download debs and install them by hand" is that dependancies can really get bad by hand (RPM Hell).

Plus, Klik is really neat but has lacked a "killer application." You just made one.

---

### Post by UbuWu on 2005-09-30
The add/remove programs program will be very much like this when it is further developed...

---

### Post by jdong on 2005-09-30
Maybe not Klik... Maybe Synaptic will be able to handle this and install the packages via APT upon clicking the link.

---

### Post by az on 2005-09-30
Well, what is happening with the dpkg -i nautilus utility?  Wasn't someone working on getting downloaded debs installable from nautilus?  This sounds like a client for that.

---

### Post by tseliot on 2005-09-30
[QUOTE=azz]Well, what is happening with the dpkg -i nautilus utility?  Wasn't someone working on getting downloaded debs installable from nautilus?  This sounds like a client for that.[/QUOTE]
Do you mean something like this? It is supposed to be in Kubuntu Breezy, please have a look:

[http://www.kde-look.org/content/show.php?content=23981]("http://www.kde-look.org/content/show.php?content=23981")

---

### Post by philipacamaniac on 2005-09-30
[QUOTE=jdong]Maybe not Klik... Maybe Synaptic will be able to handle this and install the packages via APT upon clicking the link.[/QUOTE]

I like the idea of Synaptic/Adept installing the packages when you click the Install link, but I still want to explore Klik as an option. If you haven't heard about it yet, it basically bundles everything needed together into one single image (think Windows exe). It is the easiest way to try out an app without borking your system or installing a bazillion dependencies.

As for dpkg -i, yeah, I've already covered that option in Konqueror, as you can see on kde-look. But that doesn't help you if you downloaded tuxtype and you need libsdl-mixer, libsdl-ttf, etc.

Does anyone know anything about serverside-apt? I can't find much on Google.

---

### Post by poofyhairguy on 2005-09-30
[QUOTE=jdong]Maybe not Klik... Maybe Synaptic will be able to handle this and install the packages via APT upon clicking the link.[/QUOTE]

I thought that was dpkg's area!

---

### Post by tageiru on 2005-09-30
That looks really great!

If I were you I would post it on the ubuntu-art mailing list.

---

### Post by thecrimsonking on 2005-09-30
Great idea, but I would like it better if it didn't look exactly like downloads.com

---

### Post by philipacamaniac on 2005-09-30
[QUOTE=thecrimsonking]Great idea, but I would like it better if it didn't look exactly like downloads.com[/QUOTE]

heh... that was just an example. The point here was function, and the fact that it would somehow look super hot. I'm a decent webdesigner, so I could put something together. Plus, the current design could be tweaked here and there to remove any resemblance to other websites.

Again, emphasis was on a hot-looking, user-friendly download site, not this actual design. This was just a mockup in Photoshop.

---

### Post by aysiu on 2005-09-30
[QUOTE=thecrimsonking]Great idea, but I would like it better if it didn't look exactly like downloads.com[/QUOTE] It doesn't look exactly like download.com. I like the look--it's professional but very Ubuntu (maybe it's just the brown).

---

### Post by TrailerTrash on 2005-09-30
WoW! I love the looks and sounds of all of these ideas......It makes Ubuntu look even more user friendly....And thats a good thing to help get all of the newbies from other distros and even windows. Keep up the good work and lets see some of thses things get rocking!

---

### Post by jdong on 2005-09-30
[QUOTE=poofyhairguy]I thought that was dpkg's area![/QUOTE]

But dpkg cannot evaluate dependencies from APT repositories -- I want Synaptic to turn into a YAST package manager equivalent :)

---

### Post by poofyhairguy on 2005-09-30
[QUOTE=jdong]But dpkg cannot evaluate dependencies from APT repositories -- I want Synaptic to turn into a YAST package manager equivalent :)[/QUOTE]

Can synaptic install deb files currently?

---

### Post by aysiu on 2005-09-30
[QUOTE=poofyhairguy]Can synaptic install deb files currently?[/QUOTE] KPackage can.

---

### Post by UbuWu on 2005-09-30
[QUOTE=poofyhairguy]Can synaptic install deb files currently?[/QUOTE]

No

---

### Post by poofyhairguy on 2005-09-30
Heck, can apt-get get install dep files? Appitude? I would love to know.

---

### Post by manicka on 2005-09-30
[QUOTE=jdong]Maybe not Klik... Maybe Synaptic will be able to handle this and install the packages via APT upon clicking the link.[/QUOTE]
This would be the perfect way to do it.

---

### Post by jdong on 2005-09-30
[QUOTE=poofyhairguy]Heck, can apt-get get install dep files? Appitude? I would love to know.[/QUOTE]

no; some higher level (than apt-get) frontend needs this capability if Dapper's seriously supposed to stand up to Vista and other OSes.

---

### Post by az on 2005-09-30
[QUOTE=jdong]But dpkg cannot evaluate dependencies from APT repositories -- I want Synaptic to turn into a YAST package manager equivalent :)[/QUOTE]

What about a jazzed-up 
gksudo  gnome-terminal -x dpkg-i $1 && apt-get -f install
?

---

### Post by poofyhairguy on 2005-09-30
[QUOTE=azz]What about a jazzed-up 
gksudo  gnome-terminal -x dpkg-i $1 && apt-get -f install
?[/QUOTE]


Sounds like a Third Party project idea to me!

---

### Post by jensyt on 2005-09-30
Don't mean to advertise or anything, but a while back I was working on a (temporary) solution to the dpkg -i issue. What I came up with was [Debins](http://programmer-art.org/debins).

I haven't worked on it at all since the initial releases because I got no feedback. What it does for now is make a simple repository of the files you want installed in /root/.debinstall/ and then it just updates apt's caches to contain this (without hitting every source... quite smart, actually) and then apt-get installs it. That way you get the power of apt with the ease of something like dpkg -i.

Anyway, enough of the sales pitch. If anyone wants me to continue working on it (as it is really alpha, I suppose) I'd enjoy doing it. And even though I say it's alpha, it should work with most packages you throw at it. Unless they're named with non-standard naming conventions, etc.

Enjoy. :)

---

### Post by jdong on 2005-09-30
Debins is the closest match for what I'm thinking of :)

P.S. Tell users to copy the binaries into **/usr/local/bin**, not /usr/bin -- that's strictly reserved for dpkg-managed files.

---

### Post by manicka on 2005-09-30
[QUOTE=jensyt]Don't mean to advertise or anything, but a while back I was working on a (temporary) solution to the dpkg -i issue. What I came up with was [Debins](http://programmer-art.org/debins).

I haven't worked on it at all since the initial releases because I got no feedback. What it does for now is make a simple repository of the files you want installed in /root/.debinstall/ and then it just updates apt's caches to contain this (without hitting every source... quite smart, actually) and then apt-get installs it. That way you get the power of apt with the ease of something like dpkg -i.

Anyway, enough of the sales pitch. If anyone wants me to continue working on it (as it is really alpha, I suppose) I'd enjoy doing it. And even though I say it's alpha, it should work with most packages you throw at it. Unless they're named with non-standard naming conventions, etc.

Enjoy. :)[/QUOTE]
This looks very promising and seems to work well in it's current state. 

The program itself is simple and effective. I'd encourage you to keep developing it :D

---

### Post by gflores on 2005-09-30
That looks awesome and very Ubuntu-like! There are a lot of great ideas here. I'm going to check out Debins when I get a chance. Linux brainstorming is fun. :)

---

### Post by UbuWu on 2005-09-30
[QUOTE=jensyt]If anyone wants me to continue working on it (as it is really alpha, I suppose) I'd enjoy doing it. [/QUOTE]

Yes! It is great and I used it a lot, and for an alpha release it is very good!

(also have a look at gdeb and debinstaller, maybe you can use some of their source code..?)

---

### Post by UbuWu on 2005-09-30
I think if you develop it further it will have a great chance to be included in Ubuntu by default (just like smeg)! ;)

---

### Post by jensyt on 2005-09-30
Thanks for the feedback, everyone. As of this point, I'll probably review the source code tomorrow and start hacking again (weekend hack fest).

Also, I'll update the page, thanks.

---

### Post by Emerzen on 2005-09-30
Great idea...I'm waiting to bookmark it.

---

### Post by Burgundavia on 2005-09-30
For dapper, launchpad.net is going to provide this functionality in Ubuntu. You will be able to click to install an application. It will only install out of Ubuntu repos and use the standard methods of installing, it is just a web trigger.

Corey

---

