---
title: "Proposed Community Project: gTorrent"
date: 2006-04-27
forum: The Cafe
---

### Post by zachtib on 2006-04-27
(dunno if that name is taken btw)

There was a disscussion about this in the Dapper Forums a few days ago,
but there isn't really a good, full featured torrent client for Gnome.  KDE has KTorrent, and while Azureus will run fine under Gnome, it requires Java, which for some (like me) is a bit of a turn-off.

So, I was wanting to gauge public interest for a community driven project to create a full-featured Bittorrent client for Gnome, with a similar feature set of KTorrent and Azureus, but written in C or C++ (perhaps even C# or Python, I'm not sure) and using GTK+ widgets for better integration with Gnome.  It should resume all current torrents when the program is started, and automatically save completed files to a common location.

I'd certainly be willing to help, but I won't be able to to it alone, as I go to school year round here at Speed School, and I'm also working on a few projects of my own at the moment.

So, what do you think?

---

### Post by ssam on 2006-04-27
add it to [https://wiki.ubuntu.com/GoogleSoC2006](https://wiki.ubuntu.com/GoogleSoC2006) and you might get paid to write it!

---

### Post by Caligula on 2006-04-27
Personally? no.
For me the small box for downloading via bittorent is enough. what more do we need? click and download, isn't that enough?

I like minimalism...

---

### Post by Jason_25 on 2006-04-27
I don't think one is needed either.  gnome-btdownload is great.  If you need the best, then there is azureus.

---

### Post by zachtib on 2006-04-27
[QUOTE=Caligula]Personally? no.
For me the small box for downloading via bittorent is enough. what more do we need? click and download, isn't that enough?

I like minimalism...[/QUOTE]

i currently use bittornado, and while i do like the minimalistyness of it, somethings are a bit annoying.

what id like to accomplish is a client with multiple downloads in a single window, that can resume partial downloads when started, and an ability to minimize to the tray to get it out of the user's way.  I'd still like to keep it (relatively) lightweight. Sort of a halfway point between gnome-bittorent and Ktorrent

btw, uTorrent does a pretty good job of what im aiming at, but is windows only, and not OSS

---

### Post by Rinzwind on 2006-04-27
A gnome torrent client would always be cool to have.

What I would love to see is something that can add a panel to my taskbar with some minimal info.Like it would show something like

"90% complete, 5 min to go" 

or

"90%/10m, 80%/20m, 30%/2h30m"  if I have 3 files.


And if I start a torrent download from commandline under tty1 (or so) gnome shows me how far the files are.

---

### Post by Caligula on 2006-04-27
the clien I like the most is ABC.
It's minimalistic, and still it's got all the important features you mentioned.

But I do just fine with gnome-bittorent... instead of the tray I always throw al lthe rubbish to desktop 4 or something... lol

I didn't know gnoe-bittorent doesn't resume downloads:confused: 

I still don't think we need more... but I guess that's personal preference...

---

### Post by Sheinar on 2006-04-27
It's a nice idea, though almost all of these "community projects" don't get anywhere.

---

### Post by jc87 on 2006-04-27
Personally i would love it , because it would be nice to have a real alternative to azureus for the following reasons :

A) Java is also a turn off for me

B) I hate some of Azureus aspect´s like trying to self update himself ( heck why is that needed at the Gnu/Linux world? heck we have package managers for some reason) and other annoying bugs.

C) Other Gnome torrents software don´t have some features i need.

I´m not a programmer (and i´m always broke) so i can´t contribute directly to the project , but if you need a beta-tester in the future you can count me in!

---

### Post by zachtib on 2006-04-27
[QUOTE=Caligula]I didn't know gnoe-bittorent doesn't resume downloads:confused: [/QUOTE]
i believe it can (i alway replace it with bittornado immediately) but in order to do so, you must open the same .torrent file, and then choose the same download location.

what im talking about is the user clicks Applications >> Internet >> gTorrent
and when it starts up, its will AUTOMATICALLY resume any partial downloads that were running when it ran last, and also start seeding any completed downloads.

I'm this close to going and registering the project on sourceforge, I just want a few people to confirm that they will be willing to help

---

### Post by monkeynut on 2006-04-27
I'd say a uTorrent equivalent for Linux would be an awesome asset, Azureus doesn't play too nice with 256MB of RAM and encryption is becoming important as traffic shaping increases. The uTorrent FAQ is (purposely, no doubt) cagey about a Linux port and it isn't open as was mentioned above.

---

### Post by ssam on 2006-04-27
[QUOTE=Sheinar]It's a nice idea, though almost all of these "community projects" don't get anywhere.[/QUOTE]

*cough* linux

:-)

---

### Post by Kvark on 2006-04-27
Yeah that would be sweet but starting from scratch to make a brand new program that can compete with Azureus sounds like a big project.

How hard would it be to port Ktorrent to GTK? Is the GUI stuff gathered in it's own class so all you have to do is to replace one or a few classes with GTK equivalents or have they spread out Qt stuff all over the program so it's impossible to replace the GUI without reinventing the whole program?

Is there any full featured CLI torrent client that you could just make a GTK frontend to?

---

### Post by zachtib on 2006-04-27
[QUOTE=Kvark]Is there any full featured CLI torrent client that you could just make a GTK frontend to?[/QUOTE]

like bittorrent?

yeah, that may be what winds up happening, i dunno.

i registered the project on sourceforge, so maybe well have a place to put it

---

### Post by htinn on 2006-04-27
Nice idea, but it will be a TON of work.

[http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_software](http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_software)

---

### Post by nedkelly on 2006-05-14
Yes this would be a nice to have a gtorrent like Ktorrent, since the ktorrent in svn starts to look very nice!

But there is a lot of work in makeing a torrent client like this as #15 says and I do not think that one can just "port" the Ktorrent to GTK since Ktorrent uses many things from KDE. If some one has the time and skill to make a gtorrent I think it is a great idea, but I also see the danger that this project would be to big and die

but if someone would start the project then this properly a good place to start [http://www.bittorrent.org/developer.html](http://www.bittorrent.org/developer.html) :)

---

### Post by BitTorrentBuddha on 2006-05-22
I am desperately in need of a new client, azureus doesn't play nice with dapper...

---

### Post by arsenic23 on 2006-05-22
If someone goes and starts another torrent client project I wish they'd run the interface something like torrentstorm, which used to be produced for windows.

Aside:
Most torrent programs are either too complicated, too ugly, or too simple ( three bears syndrome, I supose ).  I know I still haven't been able to turn that annouying [COLOR="DarkRed"]DHT[/COLOR] off in my copy of azureus, and some of the groups I belong too will ban me if I use a client with it.

---

### Post by G Morgan on 2006-05-22
If you could create something as fantastic as uTorrent it would be well worth the effort. As far as I'm concerned uTorrent is the only reason to use XP other than Games now. It truely is fantastic and borderlines on magic in comparison to the huge bloat that is Az.

6MB footprint with all the actually useful features. Yes please.

Anyway I'm willing to help test and help out in any way that I can but I'd say that coding is beyond my level of ability at the moment.

---

### Post by st4rdr1ft3r on 2006-05-23
I'd be willing to help out if your going to be writing it in c#.

---

### Post by samir85 on 2006-05-23
I think, that it may be more wise to constribute to an existing project than to start a new one. So far there are a few clients, which could become really god with some further developement:
[list]
[*][Freeloader](http://www.ruinedsoft.com/freeloader/) : Really neat GUI and integrates very well into gnome. Unfortunately, developement has stopped a year ago. It lacks some important features(e. g. it doesn't save torrents from the last session)
[*][Transmission](http://transmission.m0k.org/) : Also a very nice looking bt client and it also it under active developement. Anyway, it's still in an early developement stage and thus it's still unmature. For example some trackers have banned this client, because it doesn't ban peers who send corrupt data.
[*][rtorrent](http://libtorrent.rakshasa.no/) : A command line bt client. This project already exists some time and is still being developed further. Thus it is very stable. The auther also provides a bittorent libary of this torrent. So maybe you can develope a GUI for it ?
[/list]

---

### Post by onesojourner on 2006-05-23
I vote no. there are plenty of options for torrents as it is. there so many other things that need lots of help. I think the tallent could be used better elsewhere.

---

### Post by graabein on 2006-05-23
[QUOTE=onesojourner]I vote no. there are plenty of options for torrents as it is. there so many other things that need lots of help. I think the tallent could be used better elsewhere.[/QUOTE]
...like where? Give some examples please.

---

### Post by disabled_20220313 on 2006-05-23
[QUOTE=samir85]I think, that it may be more wise to constribute to an existing project than to start a new one. So far there are a few clients, which could become really god with some further developement:
[list]
[*][Freeloader](http://www.ruinedsoft.com/freeloader/) : Really neat GUI and integrates very well into gnome. Unfortunately, developement has stopped a year ago. It lacks some important features(e. g. it doesn't save torrents from the last session)
[*][Transmission](http://transmission.m0k.org/) : Also a very nice looking bt client and it also it under active developement. Anyway, it's still in an early developement stage and thus it's still unmature. For example some trackers have banned this client, because it doesn't ban peers who send corrupt data.
[*][rtorrent](http://libtorrent.rakshasa.no/) : A command line bt client. This project already exists some time and is still being developed further. Thus it is very stable. The auther also provides a bittorent libary of this torrent. So maybe you can develope a GUI for it ?
[/list][/QUOTE]

I agree. 

This would be a great example of opensource at its best, Standing on the shoulders of giants comes to mind, and would save you the work.

---

### Post by st4rdr1ft3r on 2006-05-23
[QUOTE=samir85]I think, that it may be more wise to constribute to an existing project than to start a new one. So far there are a few clients, which could become really god with some further developement:
[list]
[*][Freeloader](http://www.ruinedsoft.com/freeloader/) : Really neat GUI and integrates very well into gnome. Unfortunately, developement has stopped a year ago. It lacks some important features(e. g. it doesn't save torrents from the last session)
[*][Transmission](http://transmission.m0k.org/) : Also a very nice looking bt client and it also it under active developement. Anyway, it's still in an early developement stage and thus it's still unmature. For example some trackers have banned this client, because it doesn't ban peers who send corrupt data.
[*][rtorrent](http://libtorrent.rakshasa.no/) : A command line bt client. This project already exists some time and is still being developed further. Thus it is very stable. The auther also provides a bittorent libary of this torrent. So maybe you can develope a GUI for it ?
[/list][/QUOTE]

Personally I would say build on rtorrent, but thats just my opinion. anyone else?

---

### Post by INMCM on 2006-05-23
How about Rufus? [http://rufus.sourceforge.net/](http://rufus.sourceforge.net/)

It's already pretty mature, coded in wxpython, and has Linux source code available. I've seen a thread on here about getting it working on Breezy, perhapes some code clean ups and some patches and it could be a nice client.

---

### Post by G Morgan on 2006-05-23
Preferably I would think the aim would be for efficiency. There are plenty of clients written in intepreted languages and the whole point uTorrent has been such a huge success so quickly is the fact its written with efficiency in mind in C++ (though Az is far more inefficient in XP for some reason).

I do think that such an equivalent is missing in Linux. This could quickly degenerate into my language is better than yours though. Also the end result will be 5 Torrent clients rather than one ;) .

---

### Post by samir85 on 2006-05-23
[QUOTE=INMCM]How about Rufus? [http://rufus.sourceforge.net/](http://rufus.sourceforge.net/)

It's already pretty mature, coded in wxpython, and has Linux source code available. I've seen a thread on here about getting it working on Breezy, perhapes some code clean ups and some patches and it could be a nice client.[/QUOTE]

Indeed, right now Im gathering data about Rufus and it makes quite a good impression . I already used g3torrent a year back when I was Gentoo user as bt client and Rufus builds on g3torrent ...

Unfortunately, the only source in the internet where I can download debian packages of Rufus is down at the moment.

Maybe someone here could provide a package ?
I'd really appreciate that ...

---

### Post by stoeptegel on 2006-05-23
[QUOTE=samir85]Indeed, right now Im gathering data about Rufus and it makes quite a good impression . I already used g3torrent a year back when I was Gentoo user as bt client and Rufus builds on g3torrent ...

Unfortunately, the only source in the internet where I can download debian packages of Rufus is down at the moment.

Maybe someone here could provide a package ?
I'd really appreciate that ...[/QUOTE]

I put the deb file that strikeforce made, on a micfo account of mine half a year ago [here](http://www.luxz.net/ubuntudebs/) (without source though because i dunno if i coppied it correct at that time)

Personally i lost track of rufus at that time because i got notice of a client in development that made very nice progress and had very friendly devs (still are). This client was ktorrent.

PS. The package was clean at that time, but there's nothing to compare it with.

---

### Post by samir85 on 2006-05-23
[QUOTE=stoeptegel]I put the deb file that strikeforce made, on a micfo account of mine half a year ago [here](http://www.luxz.net/ubuntudebs/) (without source though because i dunno if i coppied it correct at that time)

Personally i lost track of rufus at that time because i got notice of a client in development that made very nice progress and had very friendly devs (still are). This client was ktorrent.

PS. The package was clean at that time, but there's nothing to compare it with.[/QUOTE]

Hey,

thanks for the quick reply.
Anyway, the version provided at the link is very outdated.

Of course, I understand that you're using ktorrent.
If I had a kde environment, I woud use ktorrent too. ;)
It is a really awesome client !

---

### Post by richbarna on 2006-05-23
I personally find Gnome slower than KDE and a bit outdated in appearance, so I am kind of biased against gnome software.
This is just my personal opinion (don't flame me)
If anyone can produce a gnome torrent that resembles Utorrent in any way shape or form, the same size, download and run, with the same speed, direct from the Dapper repositories, I will download it tomorrow. Hell, I would even pay for it !!
I use ktorrent and aMule, and I am happy with them both.
If there is something faster and easier to set up, please let me know.
(by the way I have tried it with Wine) It sucks !!

---

### Post by 0b1ivion on 2006-05-24
rTorrent+libtorrent is quite as efficient as utorrent on windows, which both written in C. I'd like to see a gui for gnome for this client although rtorrent at present using ncurse gui in console and plays quite nicely. The only thing falls behind the modern clients is DHT, peer exchange, protocol encryption features. But anything other than that it's a decent and efficient client.
btw, the newer version of rtorrent+libtorrent requires an updated library (curl or something, can't remember exactly) which is not available on ubuntu. Is there any chance that the library to be updated?

---

### Post by st4rdr1ft3r on 2006-05-30
Is this going any further?

Discussion seem to have stopped.

---

### Post by pulp on 2006-05-30
The recent beta of the official BitTorrent client should fit the needs of the majority, i think.

---

### Post by RAV TUX on 2006-05-30
doesn't this already exist?

I went to the Gnome files:
[http://www.gnomefiles.org/index.php]("http://www.gnomefiles.org/index.php")

did a search for torrent:

and I got this list:

[FONT=Arial][SIZE=2][COLOR=#000000][Anatomic P2P (GUI Client)]("http://www.gnomefiles.org/app.php?soft_id=950")[/COLOR][/SIZE][/FONT] - [FONT=Verdana, Arial][SIZE=1][COLOR=#000000]Anatomic P2P is a BitTorrent Client written in GTK with an extension enabling decentralisation[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=#000000]
[IMG]http://www.gnomefiles.org/images/bullet.gif[/IMG] [BitTorrent]("http://www.gnomefiles.org/app.php?soft_id=1211")[/COLOR][/SIZE][/FONT] - [FONT=Verdana, Arial][SIZE=1][COLOR=#000000]BitTorrent is a tool for copying files from one machine to another.[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=#000000]
[IMG]http://www.gnomefiles.org/images/bullet.gif[/IMG] [Gnome BitTorrent Downloader]("http://www.gnomefiles.org/app.php?soft_id=154")[/COLOR][/SIZE][/FONT] - [FONT=Verdana, Arial][SIZE=1][COLOR=#000000]A simple "mime-sink" BitTorrent client designed to integrate with the GNOME desktop. Currently just a GUI on top of the official BitTorrent Python backend.[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=#000000]
[IMG]http://www.gnomefiles.org/images/bullet.gif[/IMG] [GTorrentViewer]("http://www.gnomefiles.org/app.php?soft_id=528")[/COLOR][/SIZE][/FONT] - [FONT=Verdana, Arial][SIZE=1][COLOR=#000000]It is a GTK2-based viewer and editor for BitTorrent meta files.[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=#000000]
[IMG]http://www.gnomefiles.org/images/bullet.gif[/IMG] [PenguinTV]("http://www.gnomefiles.org/app.php?soft_id=1035")[/COLOR][/SIZE][/FONT] - [FONT=Verdana, Arial][SIZE=1][COLOR=#000000]PenguinTV is an RSS reader that supports enclosed media files for podcasts and video blogs.[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=#000000]
[IMG]http://www.gnomefiles.org/images/bullet.gif[/IMG] [TorrentParse GTK]("http://www.gnomefiles.org/app.php?soft_id=659")[/COLOR][/SIZE][/FONT] - [FONT=Verdana, Arial][SIZE=1][COLOR=#000000]TorrentParse GTK Parses BitTorrent Torrent files and extracts useful information from them.



Does none of the above fit?
[/COLOR][/SIZE][/FONT]

---

### Post by nedkelly on 2006-06-04
This sounds very good I am really looking forward for this piece of software

I think that you maybe be able to get some help from the ktorrent forum (and maybe the developers if you are lucky)

---

### Post by SHodges on 2006-06-04
I'd love to see a decent Torrent program for Linux.  So far, from what I've seen on Ubuntu, my only choices are standard bit torrent and bit tornado, which are prehistoric in terms of features, or azureus, which I've had nothing but problems with on both Breezy AND Dapper, performance issues, deciding not to start issues, giving me error messages that are just incorrect, randomly closing, etc.  I'd like to see a uTorrent or Bit Comet clone for linux created.

---

### Post by stoeptegel on 2006-06-04
[QUOTE=SHodges]... or Bit Comet clone for linux created.[/QUOTE]

Lets keep the comet with the idiots please. This client is doing all what bittorrent shouldn't be about... :rolleyes:

---

### Post by jobezone on 2006-06-04
[QUOTE=Sheinar]It's a nice idea, though almost all of these "community projects" don't get anywhere.[/QUOTE]
Yeah, there was that guy which called his OS by his name... What was it, Lunix?

---

### Post by Sheinar on 2006-06-04
[QUOTE=jobezone]Yeah, there was that guy which called his OS by his name... What was it, Lunix?[/QUOTE]
No shit. I did say most, not all.

---

### Post by thero on 2006-06-04
I think it should be something like utorrent.  Similar in footprint to that and same functionality.

---

### Post by SHodges on 2006-06-05
[QUOTE=stoeptegel]Lets keep the comet with the idiots please. This client is doing all what bittorrent shouldn't be about... :rolleyes:[/QUOTE]
"Be about"?  Are you guys ******* kidding me?  Here's a clue: **IT'S ******* SOFTWARE GUYS!  IT'S NOT "ABOUT" ANYTHING, IT'S NOT A MOVEMENT, IT'S NOT A REVOLUTION, IT'S THERE TO DO A SIMPLE TASK ON A COMPUTER WITHOUT CRASHING!**  

Jesus Christ, some of you people take this open source file sharing no DRM yadda yadda crap way, *way* too seriously. :rolleyes:

---

### Post by stoeptegel on 2006-06-05
[QUOTE=SHodges]"Be about"?  Are you guys ******* kidding me?  Here's a clue: **IT'S ******* SOFTWARE GUYS!  IT'S NOT "ABOUT" ANYTHING, IT'S NOT A MOVEMENT, IT'S NOT A REVOLUTION, IT'S THERE TO DO A SIMPLE TASK ON A COMPUTER WITHOUT CRASHING!**  

Jesus Christ, some of you people take this open source file sharing no DRM yadda yadda crap way, *way* too seriously. :rolleyes:[/QUOTE]


I wasn't referring to that.

Bitcomet is for idiots because of the attitude, because of the way it tries to get the fastest download. It let other peers suffer while doing it's thing, the health of the swarm goes down because of this tripping client.

Feel free to ignore me.

---

### Post by DFreeze on 2006-06-08
I’d like a decent torrent program for Gnome. I’ve also tripped over Java issues too many times to ever consider Azureus again. I’ve found a .deb once of Rufus 0.6.9, which offers a lot of functionality in a small package (.deb is around 250kB). But it’s not there yet. If something better is created, I’d team up immediately. But if you decide to e.g. help out the Rufus guys and make that the uTorrent like app (which it already resembles), I’d be all for it as well.

…and SHodges, please keep your temper (at least in your choice of words). You’re right, it’s not a revolution, it’s not that important it needs exclamations of that magnitude ;)

---

### Post by JSchwage on 2006-06-12
I'd really like to see this project happen, especially if it turns out as good or better than uTorrent on Windows. I'm a big Bittorrent user, and the lack of a good "non-java" GUI Bittorrent client sort of turned me off. I'd use Azureus if it wasn't such a resource hog. So for the moment I'm stuck with the default Gnome Bittorrent client provided in Dapper. I've tried console-based clients, but they can get quite confusing at times for me.

So if anyone can pull off a uTorrent-like client for Linux which is readily available for Debian-based distros, I'd be very happy. Sadly, I currently do not have enough experience to help with coding such a client. BUt maybe in a few years. ;)

---

### Post by zachtib on 2006-06-13
Well, I've started the coding process, I've decided to write this program in Python, because of the ease of creating gtk guis.  So far, I'm working on the interface, and I'll start implementing the torrenting part soon.  I'll post again when I have a somewhat working program for people to try out.

---

### Post by jdong on 2006-06-13
[QUOTE=SHodges]"Be about"?  Are you guys ******* kidding me?  Here's a clue: **IT'S ******* SOFTWARE GUYS!  IT'S NOT "ABOUT" ANYTHING, IT'S NOT A MOVEMENT, IT'S NOT A REVOLUTION, IT'S THERE TO DO A SIMPLE TASK ON A COMPUTER WITHOUT CRASHING!**  

Jesus Christ, some of you people take this open source file sharing no DRM yadda yadda crap way, *way* too seriously. :rolleyes:[/QUOTE]

Calm down :)

I think he was referring to the infamous bitcomet algorithms that sucks a swarm DRY just so that the one user can get godly download speeds while everyone else gets reduced down to dial-up speeds...

---

### Post by samir85 on 2006-06-13
[QUOTE=zachtib]Well, I've started the coding process, I've decided to write this program in Python, because of the ease of creating gtk guis.  So far, I'm working on the interface, and I'll start implementing the torrenting part soon.  I'll post again when I have a somewhat working program for people to try out.[/QUOTE]

Yey, Zachtib, I love you !!! :D

btw: post some screenshots when the interface makes progress ...

---

### Post by zachtib on 2006-06-13
[QUOTE=samir85]Yey, Zachtib, I love you !!! :D

btw: post some screenshots when the interface makes progress ...[/QUOTE]

will do

---

### Post by sheilnaik on 2006-06-13
uTorrent, kTorrent, and now gTorrent?  #-o

---

### Post by graabein on 2006-06-13
Yes, why not try to find a name for the client? Or maybe that can wait until it approaches a beta version. :-#

---

### Post by JSchwage on 2006-06-13
[QUOTE=graabein]Yes, why not try to find a name for the client? Or maybe that can wait until it approaches a beta version. :-#[/QUOTE]
Personally, I like the name gTorrent. It reflects that it's native desktop environment is GNOME. ;)

---

### Post by zachtib on 2006-06-14
[QUOTE=samir85]Yey, Zachtib, I love you !!! :D

btw: post some screenshots when the interface makes progress ...[/QUOTE]

here's the first couple of shots of the interface, keep in mind that this is no where near complete or final, and I'm also open to suggestions

its being designed with glade, then written with python using libglade

EDIT:  I'll also need an icon, for the application itself, and the system tray icon, if any aspiring artists are reading this, come up with an icon and post it here if you don't mind me using it.  You'll receieve full credit for doing so, and get your name in the about dialog

---

### Post by opensourcerocks on 2006-06-14
The official bit torrent client is all I need. It is just plain simple to use and I like Simple.

---

### Post by zachtib on 2006-06-14
[QUOTE=opensourcerocks]The official bit torrent client is all I need. It is just plain simple to use and I like Simple.[/QUOTE]

thats what im using at the moment(4.9 beta), but im making this to be a little better integrated with gnome, and adding a minimize to tray function that I think the official client is sorely lacking

---

### Post by stanna on 2006-06-15
if i was able to leave downloads/uploads running all the time i would have no problem with using the default gnome-btdownload client. but seeing as i have limited bandwidth on a shared connection its not an option. so a client with a schedule and the option of a web interface ( using my headless linux server ) would be ideal. so i support this project, simply because i havnt got around to having a look at kde for a long time, dont have the time to be honest. either way it would be great to  have the option of either gtorrent or ktorrent. regardless of your favourite wm. go for gold mate and bring us another alternative :)

---

### Post by st4rdr1ft3r on 2006-06-15
Are you starting on scratch or have you decided to use one of the already started projects?

---

### Post by zachtib on 2006-06-15
[QUOTE=st4rdr1ft3r]Are you starting on scratch or have you decided to use one of the already started projects?[/QUOTE]

ive started a new thread for this app here:

[http://ubuntuforums.org/showthread.php?t=196786](http://ubuntuforums.org/showthread.php?t=196786)

and i'm starting from scratch

---

### Post by SlugO on 2006-06-15
The best example of how a BitTorrent client **should** be done is [uTorrent]("http://www.utorrent.com/"). It's extremely small, efficient, full featured and fast. If you're gonna program the client then use that as an example, not Azureus.

Btw, it's about damn time to make one in my opinion. Did someone assume that Gnome users don't use BitTorrent..?

---

### Post by bionnaki on 2006-06-15
linux clients suck. really there are few options. thanks for doing gtorrent.

but please, make your client compatible with oink. most of the linux clients are banned from this tracker.

---

### Post by Gonzakpo on 2006-07-06
I don't like the idea!!!! Why just only for GNOME? Why not develope an stand alone client (using GTK+ of course)!!!? 

I don't like programs aimed to KDE or GNOME. They are very "selfish". 

If you wanna develope something, make it compatible for almost all desktop (GNOME, XFCE. FLUXBOX) and forget about the QT libs and KDE. 

XFCE rocks!

---

### Post by lapsey on 2006-07-06
i agree with the previous post.

i'd much rather see a standalone backend developed, independantly of graphical environments. Something with all the features of utorrent.

Anything else is hugely wasteful.



in fact, why don't we all use torrentflux? not only does this work for servers but for the individual. Perhaps someone out there can tell us how to get it running on ubuntu?

[http://www.torrentflux.com/](http://www.torrentflux.com/)

---

### Post by reacocard on 2006-07-06
i'd love to see something like this. i currently use bittornado, but something like utorrent would be much better. lightweight is good!

---

### Post by Gonzakpo on 2006-07-06
oh! I forgot to mention! It HAS TO be lightweight!! Because for "highweigh" client we alredy have azureus!

You should try rtorrent! ...I'm hoping anyone to build a deb package of the latest version.

---

### Post by BoHu on 2006-09-21
Why start from scratch? Why not take the FreeLoader source code and then go from there? If you could get FreeLoader to resume feeding torrent files after a restart, it would be darn near the perfect gnome-torrent manager.

---

### Post by mynimal on 2006-09-23
> **BoHu said:**
> Why start from scratch? Why not take the FreeLoader source code and then go from there? If you could get FreeLoader to resume feeding torrent files after a restart, it would be darn near the perfect gnome-torrent manager.

Freeloader is a perfect client once you hack the icons (:P), the only problem is that you can't resume after you close it. That ruins it for a lot of us.

But I don't think this should be based off it, I think we'd be better off just having our own thing rather than spinning off of another project.

Pardon if there are any typos in this post, the designers of the site aren't giving us white-on-black skin users much support. I'm stuck with white text on a light background.

---

### Post by kripkenstein on 2006-09-23
> **BoHu said:**
> Why start from scratch? Why not take the FreeLoader source code and then go from there? If you could get FreeLoader to resume feeding torrent files after a restart, it would be darn near the perfect gnome-torrent manager.

Freeloader relies on the 'official' ('mainline') bittorrent client for its backend. This is somewhat of a problem, since the Debian&Ubuntu repos only have an outdated version of the official client. The reason for this is that the license was changed at some point to one that conflicts with Debian's software guidelines.

(Actually the license is still open-source, and fairly reasonable, in most respects. But, it falls short of Debian guidelines.)

The outdated official client is lacking in several useful features (I can't remember exactly which right now, but I think protocol encryption, DHT, stuff like that). This makes Freeloader perhaps not the best option for starting a new bittorrent client.

---

