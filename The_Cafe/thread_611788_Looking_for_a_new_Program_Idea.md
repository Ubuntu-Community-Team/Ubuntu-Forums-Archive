---
title: "Looking for a new Program Idea"
date: 2007-11-13
forum: The Cafe
---

### Post by zachtib on 2007-11-13
I'm wanting to get back into programming again, and I'm looking fora fresh idea.  What I'm wanting to do is start developing a new application, not anything huge, but not too small, that will be usable by the community.

So, are there any programs that you've been wanting to see on Linux?  I'm especially interested in hearing from new Linux users as to what applications they miss from their previous OS.

For the record, whatever I wind up doing will most likely be a GTK+ app, using either Python or C#(Mono)

---

### Post by Caffeine_Junky on 2007-11-13
Have you seen this thread, asking about a "[[COLOR="DarkOrange"]_Download Manager_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=610983")"

---

### Post by zachtib on 2007-11-13
> **Caffeine_Junky said:**
> Have you seen this thread, asking about a "[[COLOR="DarkOrange"]_Download Manager_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=610983")"

actually, i just saw that, and it's definitely a possibility, but i want to get some more ideas before I settle down on one.

---

### Post by DoctorMO on 2007-11-13
You could develop the conduit widget which sits in the system tray and allows you to initiate syncing via conduit dbus and also pop up messages when new sync devices are plugged in. would be a big help if you could join in.

---

### Post by urukrama on 2007-11-13
A solid twin-pane file manager in gtk with tabs? The only thing decent around is gnome-commander and tux-commander, but both are miles away from something like krusader or total commander (windows).

Or a pdf creator -- something that allows you to easily create a single pdf file from more than one (image, text, etc.) file. There is nothing like it (both qt or gtk, or anything else).

I have no idea how difficult and/or feasible this is, but since you asked for ideas...

---

### Post by DoctorMO on 2007-11-13
> 
Or a pdf creator -- something that allows you to easily create a single pdf file from more than one (image, text, etc.) file. There is nothing like it (both qt or gtk, or anything else).

I have no idea how difficult and/or feasible this is, but since you asked for ideas...

Actually the pdf idea is quite easy, the pdf spec would be easy to do if you used the inkscape pdf export tool as a base.

---

### Post by CarpKing on 2007-11-13
I just saw this blog today: [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=3763294](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=3763294)

It's about a new and better GPS daemon.  It currently has no GUI whatsoever.  It would be cool to have some sort of GUI manager for GPS using this (not sure if such a thing already exists using other methods).  

Of course, if you don't use GPS, this probably isn't a project you'd be interested in.  I'll be sure to post some ideas for a more general audience if I think of any.

---

### Post by ssam on 2007-11-13
> **DoctorMO said:**
> Actually the pdf idea is quite easy, the pdf spec would be easy to do if you used the inkscape pdf export tool as a base.

inkscape already exports pdf

---

### Post by urukrama on 2007-11-13
> **ssam said:**
> inkscape already exports pdf

Yes, but try creating a single pdf file from 100+ images. It'll take you a lot of time and be very annoying. Adobe Acrobat Professional can do it in a few clicks. Something like that would be great for Linux.

---

### Post by SunnyRabbiera on 2007-11-13
LASER TOAST!
Yes, it CAN be done!!!!

---

### Post by ssam on 2007-11-13
> **urukrama said:**
> Yes, but try creating a single pdf file from 100+ images. It'll take you a lot of time and be very annoying. Adobe Acrobat Professional can do it in a few clicks. Something like that would be great for Linux.

could it be a print pluggin in f-spot (f-spot is GTK and mono). so you select some photos, go to print, make the pretty layout, and then print or print to pdf.

---

### Post by DoctorMO on 2007-11-13
> could it be a print pluggin in f-spot (f-spot is GTK and mono). so you select some photos, go to print, make the pretty layout, and then print or print to pdf.

I'd advise against having anything to do with mono, as a programmer I like to write things in languages I know will still be legal in the coming years.

> inkscape already exports pdf

Inkscape can only export one page of pdf since it only supports a single svg viewport/page. Although having read the pdf module and done work on the pdf support in inkscape you'll be fully aware of that. ;-)

---

### Post by DeadSuperHero on 2007-11-13
Well, might as well shamelessly plug my ideas in here:

Project Siren (an online "music store" where all the music is free, and the client would play .ogg files, and also be cross-platform. Think iTunes but FOSS): [http://ubuntuforums.org/showthread.php?t=577954](http://ubuntuforums.org/showthread.php?t=577954)

Project Centrifuge (an easy game installer/library/steam-like client for Linux users): [http://ubuntuforums.org/showthread.php?t=465260&highlight=Centrifuge](http://ubuntuforums.org/showthread.php?t=465260&highlight=Centrifuge)

Linux school apps: [http://ubuntuforums.org/showthread.php?t=609272&highlight=Linux+school+apps](http://ubuntuforums.org/showthread.php?t=609272&highlight=Linux+school+apps)

Those are a few major projects I'd like to do, except I don't know how to code (I blame not sticking with any particular programming language.)

EDIT: Also, you could help develop the Gimmie bar: [http://www.beatniksoftware.com/gimmie/Main_Page](http://www.beatniksoftware.com/gimmie/Main_Page)

---

### Post by zachtib on 2007-11-13
> **Mr. Psychopath said:**
> Project Siren (an online "music store" where all the music is free, and the client would play .ogg files, and also be cross-platform. Think iTunes but FOSS): [http://ubuntuforums.org/showthread.php?t=577954](http://ubuntuforums.org/showthread.php?t=577954)


that's a cool idea, and i'd be willing to consider it, but where does the content come from?  find some artists that would be willing to host their work, and find someplace to host it, and then it might be possible.  I wouldn't mind helping with the actual coding, though.

This is the kind of cool idea that i'm interested in.  Keep the ideas coming, guys, I'll probably be picking something to work on in a few days to a week.  I got my last project from listening to what the community wanted, and it worked out well.

---

### Post by DeadSuperHero on 2007-11-13
> **zachtib said:**
> that's a cool idea, and i'd be willing to consider it, but where does the content come from?  find some artists that would be willing to host their work, and find someplace to host it, and then it might be possible.  I wouldn't mind helping with the actual coding, though.


Yeah, I'd basically ask independant artists. As for hosting, well, I figure starting small might be a good thing. I'd start out simply with webspace, eventually I'd buy a dedicated Linux server, and all would be well.

---

### Post by Kymus on 2007-11-13
Unless it already exists somewhere else...

[LIST=1]
[*]A system restorer that's solid (I'm not impressed with Time Vault yet)
[*]I dunno if it's necessary in Linux as much as it is in Windoze, but a system diagnostic program similar to Norton System Works, etc... Though at the same time posting errors to the forum helps one understand how to fix them manually than to rely on a program to fix everything. This is a double edged sword for me.
[*]A program similar to (but possibly with a little more flexibility than) Convert X to DVD. I know Linux has a number of similar programs, but I've seen none so far that have a clean GUI and perform better than it. Given, it works better under WINE than it does in Windoze, but I'd still really like to see a Linux based open-source type of program.
[/LIST]

Everything else I use in Ubuntu is way better than the Windoze alternative and thus, is not necessary :-D

---

### Post by Polygon on 2007-11-13
just curious, are you still working on deluge? or have you moved on?

some things i have written down:

a simple gtk program or maybe a conduit plugin that allows you to upload pictures to an imageshack/photobucket account

i second in maybe like writing a whole new backup program, or expanding on things like sbackup to become maybe a automatic system restore thing like windows/mac os x has

---

### Post by Scruffynerf on 2007-11-13
My votes:

1) A good twin pane file manager. Or contribute to the Nautilus codebase

2) A good download manager that's independent from a web browser with a gui.

3) A good FTP client

4) A good WSYWIG web page creator

5) A Terminal emulator that has true transparency - something like Tilda, but has true transparency. If it could be forked to the background also like conky can be. I would consider this fantastic.

6) File recovery software that can recover from a delete operation in ext3.

cheers

---

### Post by bobbybobington on 2007-11-14
1. An easy to use video editing app is still missing in linux. Something everyday people could figure out. With multimedia so common and important today it's vital. It doesn't have to be able to use every format ever made, just decide on one format, and make the app solid.

---

### Post by yatt on 2007-11-14
> **zachtib said:**
> I'm wanting to get back into programming again, and I'm looking fora fresh idea.  What I'm wanting to do is start developing a new application, not anything huge, but not too small, that will be usable by the community.

So, are there any programs that you've been wanting to see on Linux?  I'm especially interested in hearing from new Linux users as to what applications they miss from their previous OS.

For the record, whatever I wind up doing will most likely be a GTK+ app, using either Python or C#(Mono)Something I have just started thinking about. An application that would serve as a gui installer for ATI graphics cards. I know there is Restricted Driver Manager that will install the repo packages, but sometimes (ie now) the current driver is a complete overhaul of what is in the repos. If you have Nvidia or Intel, this would be irrelevant for you (AFAIK, you have to kill X to use the Nvidia installer). Basically, the app would serve as a wrapper for the command line installer. Build the find the latest version on ATI's website, download it, use it to create packages, install the packages, build/install the kernel module, and do any distro specific steps when necessary (blacklist fglrx in restricted modules).

This would take some significant community effort to make it work on more than a few distros, but could be something that could be made to work on any distro with only a few lines of coded needed to make the thing work.

---

### Post by yatt on 2007-11-14
> **Mr. Psychopath said:**
> Well, might as well shamelessly plug my ideas in here:

Project Siren (an online "music store" where all the music is free, and the client would play .ogg files, and also be cross-platform. Think iTunes but FOSS): [http://ubuntuforums.org/showthread.php?t=577954](http://ubuntuforums.org/showthread.php?t=577954)Sounds like Magnatune. Amarok can access Magnitune. Why not try to write the appropriate modules for Exaile/Rhythmbox/Banshee.

---

### Post by adam.tropics on 2007-11-14
> **Kymus said:**
> ...[LIST=1]
[*]A system restorer that's solid...[/LIST] 
+1

---

### Post by zachtib on 2007-11-14
> **Polygon said:**
> just curious, are you still working on deluge? or have you moved on?

I've basically moved on at this point.  I'd been busy with school, so markybob and andar had taken over.  I started work on 0.5.1 and they finished it up.  Every release since has been their work.  This is why I'm now looking for a small project to tinker on in my free time, and hopefully I can spawn another useful application.

---

### Post by TeaSwigger on 2007-11-14
As a writer, I found the old and now long abandoned freeware KeyNote a godsend in Windows. I used it more than any other prog. It's a simple enough concept; pretty much a hierarchical notes manager, it offers a tree of pages (in old .rtf format btw) which you can expand, collapse, drag 'n' drop etc in any configuration, as a number of native Linux apps like Tuxcards or GJots does, along with a full plate of features like spellcheck, highlighting, macros, internal cross linking, some optional basic password protection, formatting and such. Unlike its many Windows rivals, however, it has tabs. It's an obvious feature today (though not so widely used in KeyNote's time, to its further credit). The odd thing is, especially considering how extensive the list of essentially similar Linux apps is, the Linux apps not only offer less features, but none offer anything more than a single tree per document. 

The tabs may seem like a minor enough point, but deceptively so. I'll explain. Each tree has its own tab, thus massively expanding the useful hierarchy: you have a node, which itself may be expanded by adding sibling or child nodes to any depth, attatched to a freely configurable tree, and you can have any number of trees, each its own tab. You can move any node to any place within the whole hierarchy, including other trees. You could arrange it as a related series of books (trees), each with distinct parts, chapters and pages. In one document then, you can easily organize and develop the most extensive and involved literary project, including all its finished, working draft, and project notation and development forms. Bim bang and boom.

Here in WINE on Linux, KeyNote - very quick and rock stable in Windows 2kpro - is slow and a tad buggy, with a number of features (including spell checking) unfortunately not supported. So slow in fact it takes longer to load in WINE than any Linux app including a loaded-up cold-start of GIMP. Of course it doesn't help that it's rtf based, or that KeyNote hasn't been maintained in four or five years.

NoteCase has proven to be the best native Linux hierarchical notes manager in feel for me. It's actively developed and aside from a nasty problem with an earlier version, seems pretty solid. It's light and fast and works cross-platform. But only one tree, no spell check among its relatively limited features, and lacking a certain refinement - for instance text extends all the way to the last pixel of a given document window, adding to the overall feel that it really is more suited for short note taking than the epic projects one could contrive more comfortably in KeyNote.

So if you made it this far ;)... If you think it may be of insterest, I'd be glad to try and help. I'm no programmer, but would have the eye of the target user when it comes to development and testing.

---

### Post by delfick on 2007-11-14
definitely linux version of fineprint :D
(except better of course :p)

[http://ubuntuforums.org/showthread.php?t=585147](http://ubuntuforums.org/showthread.php?t=585147)

:D

(one of the reasons I still use windows, as fineprint is really helpful for printing all my lecture notes without wasting lots of ink and paper)

---

### Post by ssam on 2007-11-14
> **yatt said:**
> Sounds like Magnatune. Amarok can access Magnitune. Why not try to write the appropriate modules for Exaile/Rhythmbox/Banshee.

rhythbox also does magnatune (and jamendo). you just need to enable the plugin (or have a new version with the plugin on by default)

---

### Post by Polygon on 2007-11-14
> **zachtib said:**
> I've basically moved on at this point.  I'd been busy with school, so markybob and andar had taken over.  I started work on 0.5.1 and they finished it up.  Every release since has been their work.  This is why I'm now looking for a small project to tinker on in my free time, and hopefully I can spawn another useful application.

oh well....you did spawn a successful bittorrent client, one that at least has a chance of replacing that horrible ubuntu default bittorent client :D

---

### Post by rjcsc on 2007-11-14
A GTK version of k3b (or a improvement to Brasero/Gnomebaker).. with the capabilities to rip, burn, convert between codecs...

---

### Post by aysiu on 2007-11-14
> **zachtib said:**
> I'm wanting to get back into programming again, and I'm looking fora fresh idea.  What I'm wanting to do is start developing a new application, not anything huge, but not too small, that will be usable by the community.

So, are there any programs that you've been wanting to see on Linux?  I'm especially interested in hearing from new Linux users as to what applications they miss from their previous OS.

For the record, whatever I wind up doing will most likely be a GTK+ app, using either Python or C#(Mono)
Does it have to be a program directly for Linux?

I think something that would be useful would be *apt-get* for Windows for those Ubuntu users who do not have an internet connection in Ubuntu. That way they have an easy way to get all the dependencies and then just bring them over to the Ubuntu partition and ```
sudo dpkg -i *.deb
```

---

### Post by zachtib on 2007-11-14
> **aysiu said:**
> Does it have to be a program directly for Linux?

I think something that would be useful would be *apt-get* for Windows for those Ubuntu users who do not have an internet connection in Ubuntu. That way they have an easy way to get all the dependencies and then just bring them over to the Ubuntu partition and ```
sudo dpkg -i *.deb
```

well, that would be possible, any probably pretty easy in python. i'll consider it

---

### Post by maluka on 2007-11-14
what about something that does what Delicious Library does.

---

### Post by zachtib on 2007-11-14
i'm bumping this up, because i want to hear from more people.

also, @ aysiu:
i just realized a problem... how would the script know what packages the user already has installed?  i'm sure there are still ways to make this work, but that does present an issue.  there's no reason for it to pull down tons of deps if they aren't needed

---

### Post by zachtib on 2007-11-14
> **maluka said:**
> what about something that does what Delicious Library does.

guess i didn't need the bump....

what exactly is delicious library?

---

### Post by aysiu on 2007-11-14
> **zachtib said:**
> 
also, @ aysiu:
i just realized a problem... how would the script know what packages the user already has installed?  i'm sure there are still ways to make this work, but that does present an issue.  there's no reason for it to pull down tons of deps if they aren't needed I think the script would have to ask the user if Ubuntu, Kubuntu, or Xubuntu is installed. If the user doesn't know, the script should assume Ubuntu. It's definitely possible that it may pull down a few redundant dependencies, but for the user without working internet in Ubuntu, an extra minute or two downloading won't matter when compared to tracking down the missing dependencies one by one manually.

---

### Post by zachtib on 2007-11-14
> **aysiu said:**
> I think the script would have to ask the user if Ubuntu, Kubuntu, or Xubuntu is installed. If the user doesn't know, the script should assume Ubuntu. It's definitely possible that it may pull down a few redundant dependencies, but for the user without working internet in Ubuntu, an extra minute or two downloading won't matter when compared to tracking down the missing dependencies one by one manually.

this is true... i'm also thinking that in the interface, it could show a checklist of all the required packages and the user could select/deselect them at will

---

### Post by p_quarles on 2007-11-14
> **zachtib said:**
> this is true... i'm also thinking that in the interface, it could show a checklist of all the required packages and the user could select/deselect them at will
Would it be possible to implement something like the package listing cache that APT uses, but in the script? My thinking is that you could make redundancy a one-time issue by keeping track of what's already been fetched. 

(but I'm very much a python beginner, so I don't know how/if that would work)

---

### Post by yatt on 2007-11-14
> **aysiu said:**
> I think the script would have to ask the user if Ubuntu, Kubuntu, or Xubuntu is installed. If the user doesn't know, the script should assume Ubuntu. It's definitely possible that it may pull down a few redundant dependencies, but for the user without working internet in Ubuntu, an extra minute or two downloading won't matter when compared to tracking down the missing dependencies one by one manually.It should also make a nice install script so that the user doesn't just try to install the alphabetically first package available, and have Gdebi attempt to fetch its dependencies via apt...

---

### Post by delfick on 2007-11-14
+1 to dependency download for windows :D

(though /me still wants linux alternative to fineprint :D)

---

### Post by frup on 2007-11-14
> **aysiu said:**
> I think the script would have to ask the user if Ubuntu, Kubuntu, or Xubuntu is installed. If the user doesn't know, the script should assume Ubuntu. It's definitely possible that it may pull down a few redundant dependencies, but for the user without working internet in Ubuntu, an extra minute or two downloading won't matter when compared to tracking down the missing dependencies one by one manually.

A small screenshot of the default look of each DE would also help eliminate confusion.

---

### Post by zachtib on 2007-11-14
i've just put up a post on collegegeek.org abou this...


anyways, there are some great ideas in here... and the dependency grabber seems like it could be a real help to new users

keep em coming, guys

---

### Post by Frak on 2007-11-14
Definitely a PDF editor as close to the simplicity that Adobe puts in their Pro edition.

---

### Post by tdrusk on 2007-11-14
This shouldn't be THAT complicated...

[http://www.shareapic.net/](http://www.shareapic.net/)
has an uploader that I can only use in Windows. It just doesn't work with Wine. Well if you could get it to work with Wine I would love it, but could you make an uploader for Linux?

---

### Post by Frak on 2007-11-14
> **tdrusk said:**
> This shouldn't be THAT complicated...

[http://www.shareapic.net/](http://www.shareapic.net/)
has an uploader that I can only use in Windows. It just doesn't work with Wine. Well if you could get it to work with Wine I would love it, but could you make an uploader for Linux?
Have you tried Photobucket instead, it's what I use and runs fine with Firefox or Opera in Linux.

---

### Post by rjcsc on 2007-11-15
> **Scruffynerf said:**
> My votes:

4) A good WSYWIG web page creator

cheers

+1 vote for this

---

### Post by BradwJensen on 2007-11-15
> **Mr. Psychopath said:**
> Well, might as well shamelessly plug my ideas in here:

Project Siren (an online "music store" where all the music is free, and the client would play .ogg files, and also be cross-platform. Think iTunes but FOSS): [http://ubuntuforums.org/showthread.php?t=577954](http://ubuntuforums.org/showthread.php?t=577954)


I would super love that too.. Really, music should be free in my beliefs.

The only things one should pay for music wise are Concerts and for the possible internet cost to have the songs available for people to get for free (the download service).  The later could be supported by a Donation link.

But we should also have a flac version of the free store like thing, too.

---

### Post by BradwJensen on 2007-11-15
Also, maybe you could help out the Pidgin team with the Audio/Video Chat feature... So it can FINALLY get finished!!

---

### Post by kpkeerthi on 2007-11-15
> **BradwJensen said:**
> Also, maybe you could help out the Pidgin team with the Audio/Video Chat feature... So it can FINALLY get finished!!

+1

---

### Post by raptros-v76 on 2007-11-15
for an idea in a different direction, do a study of some field of algorithms. for instance, i have a project lined up in which i am going to write maze solving algorithms, in python. it will generate mazes that can be solved, and then solve them.  an idea for you might be a gridworld style program, that could even help people learn python (ie, they write a class and use the grid world framework.)

---

### Post by snickers295 on 2007-11-15
i am developing a linux system and i am in need of a program kinda like Xandros Network so i can let people download from one site without using a browser.

---

### Post by Tundro Walker on 2007-11-17
When I'm trying to get back into programming, it usually takes a "proof-of-concept" program or just some totally stupid, silly or off-the-wall type program idea to get me motivated.

So, here's the one I've been thinking about lately (which I'm posting more so folks can tell me if it's already been done, and perhaps where to get it at).

(drum roll, please)

A little gnome applet that shows you the progress of your current Folding@Home work.  It'd basically read in the unitinfo.txt stats occasionally, and either show the % complete, or a small vertical progress bar that started small/red and turned green the more it filled up.

Extra ideas for this would be mousing over the progress meter/applet, or maybe clicking on it (like the weather applet) to bring up more detailed stats, like...

* name of project being worked

* start and end/due dates for the work

* calculate how many days (from today) you have left to complete the work (IE: End Date - Today = Days Left)

* calculate the avg% work done per day (Today - Start Date = Days Worked so far, divided into the % complete so far)

* with those calculations (days left, and avg% worked per day so far) be able to estimate if the user will be able to finish the work on time, and red-light them if the project is at risk of not completing.  (EG: if they've only done 1% work per day for 60 days, making it 60% complete, and there's only 30 days left to finish, which would add another 30% work completed at 1% / day, totalling 90%, we can predict the user won't finish on time.  With that knowledge, we could make the progress meter color red instead of green to signify the project is in jeopardy.  This might motivate the user to leave their computer on a bit more to make up some time.)

* Being able to click a button or something on it to run the FAH* console in --configonly mode to set up parameters would also be cool.


Like I said, a completely trivial programming task, but one small and easy enough for one person to screw with for a couple days without having to commit to a huge project.

---

### Post by Nolander on 2007-11-17
+1 on the window repo dependencies thingy sounds good.

Nolander

---

### Post by erfahren on 2007-11-17
a couple of small apps I'd like:

a clipboard utility that has more features than Glipper (like a permanent storage section)
like: [CLCL](http://www.snapfiles.com/get/clcl.html),  [Clipboard Help & Spell](http://www.snapfiles.com/get/clipboardhelp.html), or [YankeClipper](http://www.intelexual.com/products/YC3/)

a browser independent bookmark checking utility (for duplicates, dead links) like [AM-Deadlink](http://www.aignes.com/deadlink.htm) (that'll work with Opera's opera6.adr bookmark format).

---

### Post by tdrusk on 2007-11-17
> **Frak said:**
> Have you tried Photobucket instead, it's what I use and runs fine with Firefox or Opera in Linux.

I can't make money with photobucket.

Shareapic is has unlimited everything.

---

### Post by Bruce M. on 2007-11-17
As a new user to Linux, Ubuntu is my first and only distro.  I'd like to toss something into the pot here.

A little GUI utility that will help ID files you have downloaded.

For example:

catfish
A file search tool that support several different engines

It doesn't show up in the Menus as: Catfish
 ... but as File Search ... or Search (can't recall which)
Or mybe it's the "panel app" one.  I just don't know.

Or "joe" - a terminal program ... looked all over for that, until I asked a Question {Where's Joe}  and someone told me it was a terminal program.

  Like I said, :confused:ing to new Linux users.
  Download:
  "foobar" and find it in the Menus as: Chocolate.
  "foobar2" - it's a Terminal program:  crcr  (Crispy Crunch) :)
  "foobar3" - a panel app called: Oh Henry

  So a little GUI thingy that people put in **the name of the program they downloaded:**

Name:  Catfish
Location: Applications>Accessories>File Search

Name:  foobar
Location: Panel App: Chocolate

Name:  foobar2
Location: Terminal Program:  crcr

Name:  foobar3
Location: System>Preferences>Oh Henry

OK, that's my $0.02 worth, now I have to go and buy a chocolate bar.

Why oh why did I use those as examples?   :lolflag:

---

### Post by Scruffynerf on 2007-11-19
Ok, how about a GUI application that allows for tweaking of themes in metacity/gnome/whatever without having to manually edit .xml files or similar? You may be able to include some code from thewidgetfactory's wierd little application.

---

### Post by Crashmaxx on 2007-11-19
> **erfahren said:**
> a couple of small apps I'd like:

a clipboard utility that has more features than Glipper (like a permanent storage section)
like: [CLCL](http://www.snapfiles.com/get/clcl.html),  [Clipboard Help & Spell](http://www.snapfiles.com/get/clipboardhelp.html), or [YankeClipper](http://www.intelexual.com/products/YC3/)

a browser independent bookmark checking utility (for duplicates, dead links) like [AM-Deadlink](http://www.aignes.com/deadlink.htm) (that'll work with Opera's opera6.adr bookmark format).

+1

I was just thinking we really need a clipboard for Gnome. Klipper is decent, but really for KDE. Though Glipper looks good and I'm trying it now.

---

### Post by natedawg on 2007-11-19
> Or a pdf creator -- something that allows you to easily create a single pdf file from more than one (image, text, etc.) file. There is nothing like it (both qt or gtk, or anything else).

I have no idea how difficult and/or feasible this is, but since you asked for ideas... 



II think it would be great to have a good PDF editor...

A simple  native gnome app thats cross platform (portable on windows would be good too). 
Along with editing PDF files it would be able to split up PDF pages into separate files and combine separate PDF files into one. Also other features like converting images to PDF or vise versa would rock.

---

### Post by Lorin Ricker on 2007-12-30
> I'm wanting to get back into programming again, and I'm looking fora fresh idea. What I'm wanting to do is start developing a new application, not anything huge, but not too small, that will be usable by the community.

So, are there any programs that you've been wanting to see on Linux? I'm especially interested in hearing from new Linux users as to what applications they miss from their previous OS.

[http://ubuntuforums.org/showthread.php?t=611788&highlight=fineprint](http://ubuntuforums.org/showthread.php?t=611788&highlight=fineprint)

[http://snipurl.com/1w5j7](http://snipurl.com/1w5j7)

Hope I'm not too late to the party -- I'm just a couple of weeks into Ubuntu, with a SAAHA commitment to burn all bridges to Windows.  However, there are two utility-applications that I'd kill-or-die to see available in the Linux community:

[1] (Mentioned numerous times elsewhere this forum, as my research shows) -- [FinePrint]("http://www.FinePrint.com").

FinePrint is an essential applet in any OS (available Windoze only) -- its primary benefits are: a) print previewing, with an eye towards paper saving (multi-up printing; ability to delete unwanted pages, such as widow-lines/blank pages/trailing junk from webpages); b) versatile portrait-to-landscape; c) watermarks; d) complete versatility for duplex/two-sided printing.; and much more.

[2] An as-you-type Text AutoCompleter, such as [AceText]("http://www.acetext.com") and/or [Texter]("http://lifehacker.com/software/texter/lifehacker-code-texter-windows-238306.php") (both are again Windoze only).

Texter is the more primitive of the two, simple-to-use and effective for what it does:  it expands a "userword", typically followed by (triggered by) a <tab>, with pre-defined text -- for example, **myphone<tab>** would be instantly replaced by **(303)555-1212**, if that's how I'd defined my userword "myphone".

AceText is a bit more ambitious, providing a GUI in front of a more extensive user database full of user-defined "blocks fo text" -- these can be parameterized with things like %name% or %subject%, so text expansions can be "personalized" by on-the-fly user entries to prompting generated by first-occurrence of any unique parameter.  Invoking a text-replacement is a bit more clumsy with AceText (compared to Texter), but given its extensive functionality, it's an OK tradeoff.

Note: each of these (in Windows) sits in the System Tray and "listens" for its trigger, and then expands/replaces text in whatever the user's current/active window is -- usually a text editing window, such as an email Compose Message, a text editor, or a text box in Firefox (like I'm using now).  Text-expansion happense at the current cursor edit-point position, and the cursor ends up at the end of the replacement text, ready to go/continue.  Works seamlessly.

Ideally, we'd have a blend of the best of both AceText and Texter available for Linux.

I suppose you'd have to use these applets for a while (in Windoze!) to get a sense of how usefully essential they can become.  I know that the tendency in the *nix community is to string together a few "simple components" (pipes) to build ad-hoc functionality, but I'd imagine that such a pipe wouldn't work as seamlessly or fit into the overall desktop environment as well as custom-built applets would.

FinePrint and an AceText/Texter composite go to the top of my want-list to make Ubuntu's absolute conquest over Windoze complete!  Thanks for asking -- I'm available to answer questions or consult on this, if I can help.

---

### Post by airtonix on 2008-01-02
a gui for sqlite that basically replaces filemaker pro.

oh and it must run on mac, dozer and linux

---

### Post by chrismine on 2008-01-02
> Or a pdf creator -- something that allows you to easily create a single pdf file from more than one (image, text, etc.) file. There is nothing like it (both qt or gtk, or anything else).

I second this - CUPS/PDF lacks feature's like giving your own name and location to save.

---

### Post by jobsonandrew on 2008-01-02
A while back I made a program that sits running on my server.. it checks the computer's external IP address (using [www.whatismyip.org](www.whatismyip.org)) and saves it to a file.. every 15 mins it does it again, and if the ip has changed, it records it in the file (overwriting the original) and emails me with the new IP..

I have since moved house and my dad occasionally turns the server on, so it keeps me updated with its IP via email so i can still get on VNC etc.. I wrote it because my dad didnt like the idea of a static IP address.. the only problem is, its written in Java, and the VM takes up a fair amount of memory for something so simple.. (the advantage is it works on windows as well as ubuntu).

its great when i find ive got a new email from my program.. it just runs and runs for months :)

maybe this idea could be made much more efficient with something like Python.. I was going to write it in C++ but I'd have to learn a LOT about C++ before I could do it

---

### Post by M$LOL on 2008-01-02
An idea I got from one of the threads, an app that displays a terminal window on your desktop and for everything you do in the GUI, it displayes a commandline equivalent for it.

I'd definitely use it.

---

### Post by bruce89 on 2008-01-02
> **jobsonandrew said:**
> maybe this idea could be made much more efficient with something like Python.

[Don't be so sure]("http://shootout.alioth.debian.org/debian/benchmark.php?test=all&lang=python&lang2=java").

---

### Post by jobsonandrew on 2008-01-02
Yes! *punches air*
im tired of people saying Java sucks, especially when i spent most of my time at uni learning how to use it

Pythons dont even have legs.. how can they outrun anything? :P

---

### Post by popch on 2008-01-02
> **jobsonandrew said:**
> Yes! *punches air*
im tired of people saying Java sucks, especially when i spent most of my time at uni learning how to use it

Pythons dont even have legs.. how can they outrun anything? :P

Java has even less legs. And Pythons can outslither Java any time of the day.

Still, learning (and even using) Java can have its uses. Who wants a house or a bridge to outrun anything?

---

### Post by stoodleysnow on 2008-01-02
Something that actually takes a computer with Intel ICH8 HDAudio, a Philips chipset Dazzle PCI TV card (analogue) and is able to use both at the same time without clashing.:mad::(

---

### Post by Crashmaxx on 2008-01-02
Don't know if the OP is still looking for ideas. Anyway, it may not be too exciting, but Linux really needs a GUI to setup extra mouse buttons. Still having to go into xorg.conf and possible still needing imwheel is really a joke to get something as simple as back/forward buttons to work.

Wouldn't need to be too much, just a window that lets you pick how many buttons, click each one to confirm what button is what, and let you pick a common action, combo of keyboard and mouse clicks, or custom command. Some more low level stuff here, but not too big a program and shouldn't be hard for the person that made deluge.

If the OP doesn't do this though, I'm going to try it before too long. Difference is, I'm still learning C so it will certainly be a challenge for me. If I can do it at all.

---

### Post by Xzallion on 2008-01-02
On the topic of the Windows apt-get downloader, someone said that it wouldn't know what packages were already installed.

It's not the most elegant solution but maybe make two programs, the windows downloader, and a linux analyzer/installer?  The linux apt-get analyzer would check what packages are installed and write them to a text file or something.  Then the user could carry the text file into windows with any removable media or if its just the windows partition on the same computer they could just copy it over.  Anyways, the Windows downloader would download what it needs using the text file from the analyzer, and package all the downloads into something like a zip file.  Then instead of the user having to run the command to install the debs, they just click on the linux installer and open the zipped file of the downloaded debs.

Should the user not have run the analyzer, the windows downloader could have the user select what OS is installed (Ubuntu, Kubuntu, Xubuntu, GoUbuntu, Debian etc) and download what would be needed from a new distro install.  There would be some redundancy but it would save them having to switch back to the machine and then go back to windows.

Anyways, good luck selecting a project, and rock on man.:guitar:

---

### Post by McTek on 2008-01-11
What I miss is Clipmate for windows. I would like to see Glipper beefed  up with some of Clipmates apps.

---

### Post by billgoldberg on 2008-01-11
How about helping out TimeVault to use 3d (compiz fusion) to match/overclass osx leopard!

It's just something I would like to see.

---

### Post by DUDE_2000 on 2008-01-11
a small program that can view everything.
You want to open an ics file, but don't want to install sunbird?
use the everything viewer!
You need to look at a xls file?
use the everything viewer!

it would nned to be plugin based though.

---

### Post by obdata on 2008-01-21
> **airtonix said:**
> a gui for sqlite that basically replaces filemaker pro.

oh and it must run on mac, dozer and linux

Yes, that would be very good!!!:lol: We use Filemaker 8.5 heavily and have it integrated with Quickbooks Premier via a plugin. I think there would be a surprising number of people that would put something like this to very good use.

PS. It would be most important for it to work on Linux, since there aren't many comparable applications for Linux yet.

---

