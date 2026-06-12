---
title: "gTorrent: A Bittorrent client for GNOME"
date: 2006-06-14
forum: The Cafe
---

### Post by zachtib on 2006-06-14
I'm starting a new thread to keep thing simpler, and cause I don't want people to glance over anyting of importance.

First off, the most current screenshots are attached to this post, I'll add newer ones as I get farther along in the program.  Right now, gTorrent is a GUI only, it doesn't actually do anything yet, but I've only been coding for a few days, so all that is still to come. ;)

Second, I need some artwork, specifically an icon.  If you want, make an icon in GIMP, or whatever else you use and post it here. You'll receieve full credit for doing so, and get your name in the about dialog.  Scalable icons are nice, otherwise a 64x64 or so png should work fine, and I'll scale it to whatever size i need.   This icon will be for the application menu, and also for gTorrent's system tray icon.

If I get a bunch of good submissions, I'll likely have a runoff here poll-style :)

finally, any input is greatly appreciated, what does the gui need/not need, etc.  what should the program do on top of simply downloading, if anything?

EDIT: doh! forgot the screenies :-x


Update 6/22/2006
gTorrent is now on SourceForge: [http://sourceforge.net/projects/gtktorrent/](http://sourceforge.net/projects/gtktorrent/)
the name gtorrent was already taken =/ gtktorrent is only what it is listed on SF as, the program itself is still gTorrent.

---

### Post by anodizer on 2006-06-14
[QUOTE=zachtib]finally, any input is greatly appreciated, what does the gui need/not need, etc.  what should the program do on top of simply downloading, if anything?[/QUOTE]

Supporting multiple torrents in one instance [unlike bittorrent and bittornado] is a must imo.
Also, the option to control speed and connections.
And something less important: a web interface.
Good luck, having another linux bittorrent client is great.

---

### Post by G Morgan on 2006-06-14
[QUOTE=anodizer]Supporting multiple torrents in one instance [unlike bittorrent and bittornado] is a must imo.
Also, the option to control speed and connections.
And something less important: a web interface.
Good luck, having another linux bittorrent client is great.[/QUOTE]

I'm not sure a web interface is that important. As long as you can chose to open a torrent file directly in gTorrent from firefox then its not as necessary. For me multiple torrents and a tray icon are the obvious ones.

Prehaps a peer list and a measure of the health of the swarm would be nice as well. Long term the ability to set priorities for both torrents and individual files would be a good feature.

---

### Post by XQC on 2006-06-14
Priority settings
There are directory torrents, from which you only want actually one file or you want a file earlier than the others.

---

### Post by zachtib on 2006-06-14
[QUOTE=G Morgan]For me multiple torrents and a tray icon are the obvious ones.[/QUOTE]

Those are the exact two reasons I started this.


thanks all for the feedback, I'll keep posting whenever I have updates

---

### Post by Wallakoala on 2006-06-14
Just one question, what language are you making this in?

---

### Post by etc on 2006-06-14
Please, please, please let it cache the .torrents.  You don't know how many times I chose to open a torrent in freeloader and then later closed it, hoping I could restart it but it couldn't find the torrent that no longer exsists in my browsers temporary files.

---

### Post by zachtib on 2006-06-14
[QUOTE=Wallakoala]Just one question, what language are you making this in?[/QUOTE]

python

[QUOTE=etc]Please, please, please let it cache the .torrents.  You don't know how many times I chose to open a torrent in freeloader and then later closed it, hoping I could restart it but it couldn't find the torrent that no longer exsists in my browsers temporary files.[/QUOTE]

good idea, will do

---

### Post by bionnaki on 2006-06-15
please make this compliant with oink: [http://oink.me.uk/faq.php#stats3](http://oink.me.uk/faq.php#stats3)

---

### Post by siimo on 2006-06-15
I would like to contribute as well if this project is gonna be open source as im a noob programmer and would like to see if i can help or if im totally clueless :confused: 

P.S: i dont know python but i want to learn it - its upto u if you're goig to release the code during development or not, im sure some other peeps might get a look in as well :idea:

---

### Post by gingermark on 2006-06-15
**icon idea**:

One arrow coming down on a "seed" and being dispersed. I did a quick mockup (attached, but I have to leave for work). If folks like the idea then I can continue it, and if it's been done before (doesn't seem like a groundbreaking idea) then I won't bother!

P.S. Don't laugh at the mockup:

---

### Post by GarethMB on 2006-06-15
[QUOTE=zachtib]I'm starting a new thread to keep thing simpler, and cause I don't want people to glance over anyting of importance.

First off, the most current screenshots are attached to this post, I'll add newer ones as I get farther along in the program.  Right now, gTorrent is a GUI only, it doesn't actually do anything yet, but I've only been coding for a few days, so all that is still to come. ;)

Second, I need some artwork, specifically an icon.  If you want, make an icon in GIMP, or whatever else you use and post it here. You'll receieve full credit for doing so, and get your name in the about dialog.  Scalable icons are nice, otherwise a 64x64 or so png should work fine, and I'll scale it to whatever size i need.   This icon will be for the application menu, and also for gTorrent's system tray icon.

If I get a bunch of good submissions, I'll likely have a runoff here poll-style :)

finally, any input is greatly appreciated, what does the gui need/not need, etc.  what should the program do on top of simply downloading, if anything?

EDIT: doh! forgot the screenies :-x[/QUOTE]
It's looking good. Are there any clients that you are trying to emulate in this program?

---

### Post by G Morgan on 2006-06-15
Something I forgot. When you come to setup the library. Pre-allocation of disc space is a god send and is one of the most useful features I've seen anywhere. It was so annoying if you had a HDD with limited space and setup several torrents only for the  machine to complain about a lack of disc space. Allowing a pre-allocation option removes this worry completely.

---

### Post by blkish on 2006-06-15
[QUOTE=gingermark]**icon idea**:

One arrow coming down on a "seed" and being dispersed. I did a quick mockup (attached, but I have to leave for work). If folks like the idea then I can continue it, and if it's been done before (doesn't seem like a groundbreaking idea) then I won't bother!

P.S. Don't laugh at the mockup:[/QUOTE]

i like that (icon)

---

### Post by GarethMB on 2006-06-15
[QUOTE=gingermark]**icon idea**:

One arrow coming down on a "seed" and being dispersed. I did a quick mockup (attached, but I have to leave for work). If folks like the idea then I can continue it, and if it's been done before (doesn't seem like a groundbreaking idea) then I won't bother!

P.S. Don't laugh at the mockup:[/QUOTE]
My suggestions for the icon would be:
-replace circle with ubuntu icon.
-make it ubuntu colours. 

A good starting idea though.

---

### Post by XQC on 2006-06-15
>  My suggestions for the icon would be:
-replace circle with ubuntu icon.
-make it ubuntu colours. 
I don't think the author intented to make this app only for Ubuntu.

I like the idea but I think it's hard to realize for small sizes.

---

### Post by CronoDekar on 2006-06-15
As far as features go, what I'd really like to see is an ability to stop seeding the torrent after hitting a certain ratio.  I've got limited monthly bandwidth, so it's not good for me to leave a torrent seeding overnight.  If you could have both default and per-torrent options for that, that'd be awesome.

Hum, other features... DHT would probably be nice, if you could get it to work.  Superseeding definitely.  The ability to individually select certain files you want to download rather than get the whole thing would be nice too.  uPnP support would be good... I think.  (OK so I have no idea what exactly that does, but it sounds useful!)

That's about all I can think of right now.  Good luck with the project!

---

### Post by zachtib on 2006-06-15
thanks for the replys, now to try and answer a few questions

i'm sort of trying to emulate uTorrent, in that its a lightweight yet full featured client.

of course it will be open source, there just isnt much code right now.  once there is something to look at, ill put the source code up fo download

i have no idea what oink is, but ill look into it, and if its something that can be done without a whole lot of effort, i may put it in

to whomever said they didn't know python: neither did I three days ago, but i picked up a copy of Python in a Nutshell, and began to read.  The language is very easy to learn, and as I'm experienced with c and java, wasn't too hard to adjust too

i'd like to include a lot of the features you guys have mentioned, but atm, im just trying to get the program working.  My first goal is to get this client to complete a download, then I'll start working on all the cool stuff :D

---

### Post by moustacheky on 2006-06-15
a verrrry usefull feature would be to give downloading priority to, for example, the first mb of the file. (if that's possible)
that way you don't have to wait to be lucky enough/wait to have the beginning of the file downloaded and you can easily preview an avi and check it's resolution, quality, language, etc. you than can check if its the correct version, and even beter, if it's a fake file or not!

---

### Post by SlugO on 2006-06-15
[QUOTE=zachtib]i have no idea what oink is, but ill look into it, and if its something that can be done without a whole lot of effort, i may put it in[/QUOTE]
Oink.me.uk is an invite only music tracker. They banned BitComet and a few other clients for either putting too much load on their tracker or behaving in nonstandard ways. So just make sure the client behaves nicely ;)

---

### Post by Kimm on 2006-06-15
I tried to design an icon... but I'm far from good at designing, so I decided to just try and show a possible concept for the icon.

[http://www.ubuntuforums.org/gallery/showimage.php?i=2871&c=5](http://www.ubuntuforums.org/gallery/showimage.php?i=2871&c=5)

The idea is described with the image... although I think you'll understand the idea just by looking at it.

---

### Post by arsenic23 on 2006-06-15
If you support DHT, make sure  it's easy to turn off.  Some of the private trackers I use will ban me if I use a client with DHT.

---

### Post by bruce89 on 2006-06-15
[quote=Kimm]I tried to design an icon... but I'm far from good at designing, so I decided to just try and show a possible concept for the icon.

[http://www.ubuntuforums.org/gallery/showimage.php?i=2871&c=5]("http://www.ubuntuforums.org/gallery/showimage.php?i=2871&c=5")

The idea is described with the image... although I think you'll understand the idea just by looking at it.[/quote] 
I thought that E[SIZE=1]p[/SIZE] = mgh, where gravity is concerned?

---

### Post by Kimm on 2006-06-15
Oops... sorry, my bad.

It should be F = mg

Ep = mgh is for potential energy (E = Energy, p = Potential),

I supose I should update the picture...

---

### Post by kpolice on 2006-06-15
About the GUI, a way to choose my own icons for the toolbar. Like downloader for X (d4x) . Sometimes I don't like the icons from my GNOME Icon theme so it woukld be nice to use custom ones.

Also pause and resume buttons on the toolbar. A progressbar showing the completed percentage.

---

### Post by fenton06 on 2006-06-16
Yes, a uTorrent clone would be a good thing, becasue I can';t stand using Azureus...anyway, what i would like is:

Ability to pause, start and stop torrents

DHT - toggle on or off

Be able to search popular torrent sites from the program, and be able to add/remove sites (like utorrent)

I would also like to be able to select what files to download, sometimes I dont want every single file in the torrent

having all the information about the torrent in a frame on the bottom, i.e: tracker details, percent completed, file list...etc (again, like uTorrent)

the ability to resume downloads if the program closes

minimize and close to system tray

no pop ups like Azureus, a dialog box you can close is nice


This is a small list, I would help, but alas, I know no programming.

---

### Post by bruce89 on 2006-06-16
All I need is gnome-btdownload to log how much of a file has been uploaded, so I can tell when I can stop sharing.  I only need it for ubuntu CD's anyway.

---

### Post by Stellaris on 2006-06-17
First and foremost,

I'd like to be able to **download and upload multiple .torrents in one window**, how's that for a start? :D 

Keep up the good work!

---

### Post by hopstah on 2006-06-17
i agree with compatibility with oink - very important to me.

but another feature that i find very useful is the ability to schedule ul / dl caps for different times of the day and different days of the week.  this allows me to free up my house's network during the day while downloading like crazy overnight, without having to actually change anything myself.

thanks, and keep up the good work.

---

### Post by JSchwage on 2006-06-19
Just sprung another suggestion. Might it be a good idea to add the ability to create torrents such as is possible in Azureus? So far I haven't seen this feature in any other Bittorrent clients for Linux yet. I know it's possible to create torrents in via a console application, but it's very confusing to me.

Lovin' the screenshots. Keep up the good work!

---

### Post by zachtib on 2006-06-19
[QUOTE=JSchwage]Just sprung another suggestion. Might it be a good idea to add the ability to create torrents such as is possible in Azureus? So far I haven't seen this feature in any other Bittorrent clients for Linux yet. I know it's possible to create torrents in via a console application, but it's very confusing to me.

Lovin' the screenshots. Keep up the good work![/QUOTE]

most likely i will do this.

I've created a Gnome 'Druid' as is common with many apps.  On running, gTorrent will check for a .gTorrent directory to store the configuration files.  On that note, does anyone know a command in python to return the user's home directory? I can't seem to figure that one out...

I'll post some new screenshots in a few days, when I should have the interface hammered out and will begin working on the torrenting itself.  A note to all you oink users, once I start releasing builds, I wouldn't advise using oink till i get the bugs hammered out, as i don't want to get this client banned right away...

---

### Post by mynimal on 2006-06-19
Really looking forward to this. :) I suggest you use a Tango icon (With permission from the developers of course) like Epiphany does. A perfect icon for it would be the Internet menu category icon.

---

### Post by samir85 on 2006-06-20
I think you don't have to worry about compatibility to 0ink.
As far as I'm concerned, this was about some clients, which had a DHT feature, which didn't respect the private flag of the tracker and thus you could download the torrents via DHT, which 0ink reasonrably wanted to prevent and so they banned the concerned clients (I believe it was about some old versions of Azureus and BitComet).

---

### Post by Maupertus on 2006-06-20
If possible I would love to have the possibility for sharing to automaticly stop after a certain share-percentage has been reached.

I always try to share the torrent at least untill I've reached a 150 to 200 percent share rate and it would be nice if it could remove itself after it had reached that percentage. (Hey, it's not a must, but the less I have to do myself :) )

---

### Post by zachtib on 2006-06-20
[QUOTE=Maupertus]If possible I would love to have the possibility for sharing to automaticly stop after a certain share-percentage has been reached.

I always try to share the torrent at least untill I've reached a 150 to 200 percent share rate and it would be nice if it could remove itself after it had reached that percentage. (Hey, it's not a must, but the less I have to do myself :) )[/QUOTE]

Well, enough people have requested it, so I think I'm going to add this feature into the program.  Hopefully, I'll have something to show you all soon, but I'm a full time student with less free time than I'd like :(

---

### Post by G Morgan on 2006-06-20
[QUOTE=zachtib]Well, enough people have requested it, so I think I'm going to add this feature into the program.  Hopefully, I'll have something to show you all soon, but I'm a full time student with less free time than I'd like :([/QUOTE]

Lets be fair. On one hand alcohol and general clubing, on the other hand programing ;) .

---

### Post by zachtib on 2006-06-20
[QUOTE=G Morgan]Lets be fair. On one hand alcohol and general clubing, on the other hand programing ;) .[/QUOTE]
ssssshhhhh!  :D

---

### Post by Virogenesis on 2006-06-20
```

<?xml version="1.0" encoding="iso-8859-1"?>
<gTorrent>
	<NavBar>
		<Button id="AddTorrent" img="AddTorrent.svg" />
		<Button id="AddUrl" img="AddUrl.svg" />
		<Button id="CreateTorrent" img="CreateTorrent.svg" />
		<Button id="Remove" img="Remove.svg" />
		<Button id="Start" img="Start.svg" />
		<Button id="Pause" img="Pause.svg" />
		<Button id="Stop" img="Stop.svg" />
		<Button id="MoveUp" img="MoveUp.svg" />
		<Button id="MoveDown" img="MoveDown.svg" />
		<Button id="RssFeed" img="RssFeed.svg" />
		<Button id="Preferences" img="Preferences.svg" />
	</NavBar>
	<SideBar>
		<Button id="All" img="All.svg" />
		<Button id="DownLoading" img="DownLoading.svg" />
		<Button id="Completed" img="Completed.svg" />
		<Button id="Active" img="Active.svg" />
		<Button id="InActive" img="InActive.svg" />
	</SideBar>
</gTorrent>

```
Ermm not sure if that would help but mark a xml file up as a skin so you can change the icons easly.

---

### Post by Virogenesis on 2006-06-20
[http://ubuntuforums.org/gallery/files/6/5/1/8/4/gtorrent.gif](http://ubuntuforums.org/gallery/files/6/5/1/8/4/gtorrent.gif) thats the layout to utorrent pretty much but imagine that built with gtk2 widgets.
libcairo would be ace for using on the graphs, true vector graphics.

---

### Post by ZephyrXero on 2006-06-20
I notice you're calling it "gTorrent: a bitTorrent client for Gnome". I think it would be very nice to use it in XFCE as long as you don't have any Gnome specific dependencies beyond libGlade or something. Hopefully, even though you're target DE is Gnome it will work well in others ;)

---

### Post by zachtib on 2006-06-20
[QUOTE=ZephyrXero]I notice you're calling it "gTorrent: a bitTorrent client for Gnome". I think it would be very nice to use it in XFCE as long as you don't have any Gnome specific dependencies beyond libGlade or something. Hopefully, even though you're target DE is Gnome it will work well in others ;)[/QUOTE]

well, I'm using the Gnome template in glade, I don't know what impact that will have on the matter

---

### Post by Sammi on 2006-06-20
Feature request: Download sceduleing.

The reason that I have been forced to use Azureus is because it has a plugin available, which makes it possible to preconfigure the times when torrents are downloaded and when they are not.

I live in a small place where there are only two ISPs and both only provide semi-flatrate. For the subcription that I pay for, this means that I only get real flatrate at night and only 3 GB of free download per month during the day.

Because of this I need to scedule the torrent program to stop downloads at 8 in the morning at start again at midnight, but as said, I have only found this feature in one torrent app and that's Azureus. 

It would be nice if you included this feature. Then I would definatively choose your program over Azureus.

---

### Post by zachtib on 2006-06-20
[QUOTE=Sammi]Feature request: Download sceduleing.[/QUOTE]

This has also been requested a few times, so it will likely also be included.

But I don't want to get ahead of myself, first things first, I have to get gTorrent to download something before i get started on the fun stuff ;)

---

### Post by zachtib on 2006-06-21
Thought you'd like a new screenshot, look, the tray icon is working :D

---

### Post by st4rdr1ft3r on 2006-06-22
If you want some help I can teach myself python and give you a hand with it. Also could host an svn or cvs repo on my vps if you like?

---

### Post by samir85 on 2006-06-22
[img]http://www.ubuntuforums.org/attachment.php?attachmentid=11597&d=1150927262[/img]


Looks great, keep it up !

btw: a new version of [Transmission](http://transmission.m0k.org) has been released yesterday. I will use this one until Zatchibs client is finished !

---

### Post by zachtib on 2006-06-22
[QUOTE=st4rdr1ft3r]If you want some help I can teach myself python and give you a hand with it. Also could host an svn or cvs repo on my vps if you like?[/QUOTE]

feel free, and if you want to host a cvs repo, just set it up and tell me how to access it.

thanks, 

zach

---

### Post by oscar on 2006-06-22
I just thought of a nice feature that I haven't seen implemented anywhere...though I am not a big bittorrent user. How about having the progress bars viewable from the notification area applet. Sort of like the NetworkManager applet has. I couldn't get my own screenshot of it for some reason but it is shown here:
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

---

### Post by roderikk on 2006-06-22
Wow, this looks like an awesome project. As a full time student myself I can't tell where I can get the time to teach myself Python but once I can I will most certainly help out! I've been searching for ages for a bittorrent client that rivals uTorrent. (Even tried using Wine to run uTorrent :rolleyes: ).

Good luck.

BTW If you ever see the need to (start) a site for this program and need a hand give a shout!

---

### Post by zachtib on 2006-06-22
[QUOTE=roderikk]Wow, this looks like an awesome project. As a full time student myself I can't tell where I can get the time to teach myself Python but once I can I will most certainly help out! I've been searching for ages for a bittorrent client that rivals uTorrent. (Even tried using Wine to run uTorrent :rolleyes: ).

Good luck.

BTW If you ever see the need to (start) a site for this program and need a hand give a shout![/QUOTE]

i was gonna plop it at gtorrent.collegegeek.org, im just worried about it killing my bandwidth, as i host the server at home :confused:

---

### Post by ZephyrXero on 2006-06-22
[QUOTE=zachtib]i was gonna plop it at gtorrent.collegegeek.org, im just worried about it killing my bandwidth, as i host the server at home :confused:[/QUOTE]

Why not just setup a sourceforge site or something? ;)

PS. I think having the progress bars when you mouse over the notification icon would be very cool too :D

---

### Post by st4rdr1ft3r on 2006-06-22
personally i think a notification bubble when you hover over would be better, what if you have 5 torrents on the go, thats a fair amount of space taken up by progress bars in the notification area.

---

### Post by zachtib on 2006-06-22
[QUOTE=ZephyrXero]Why not just setup a sourceforge site or something? ;)

PS. I think having the progress bars when you mouse over the notification icon would be very cool too :D[/QUOTE]

doh I set that up weeks ago... ](*,) 
[http://sourceforge.net/projects/gtktorrent/](http://sourceforge.net/projects/gtktorrent/)

---

### Post by oscar on 2006-06-22
[QUOTE=st4rdr1ft3r]personally i think a notification bubble when you hover over would be better, what if you have 5 torrents on the go, thats a fair amount of space taken up by progress bars in the notification area.[/QUOTE]
I don't think you quite get what I mean. I managed to take a screenshot (had to use scrot instead of gnome-screenshot) to show what I mean. That box appears when you click on the icon. Mouse over is just plain tooltip type text.

---

### Post by zachtib on 2006-06-22
OK, from now on, if there's a feature you want to see, add it to the sourceforge page here: [http://sourceforge.net/projects/gtktorrent/](http://sourceforge.net/projects/gtktorrent/)
feel free to still post here about it, but i want to get all of these ideas in one place

---

### Post by st4rdr1ft3r on 2006-06-22
Ah ok, yea sorry, i got the network things mixed up, theres one that puts the bars in the notification area.

---

### Post by banjobacon on 2006-06-26
[QUOTE=samir85]btw: a new version of [Transmission](http://transmission.m0k.org) has been released yesterday. I will use this one until Zatchibs client is finished ![/QUOTE]

Thanks for linking to Transmission. It's got a great, clean interface. I'll be trying it out for a while.

---

### Post by ericsp on 2006-07-09
Might be a silly question: where is the download page?

---

### Post by JSchwage on 2006-07-24
> **ericsp said:**
> Might be a silly question: where is the download page?It hasn't been released to the public yet as far as I know. Correct me if I'm wrong.

---

### Post by BitTorrentBuddha on 2006-07-24
Keep up the good work man, is there anywhere to donate to the project yet?

---

### Post by Sammi on 2006-07-24
Hope to see a usable/downloadable/installable version soon :KS

You can look forward to it yourself, because if gTorrent has download sceduling and works generally well, then sure I will donate :D

---

### Post by The Noble on 2006-07-24
Looks like it could be an awsome client soon. Right now I'm stuck with ktorrent, which is nice, but my computer feels the blow. Maybe an advanced version and simple version? What you already have looks nice and simple (as it should so far -- looks nice). 

For the short term:
Easy, multiple downloads, quick, fast. Maybe disk allocation. Disc tray is a must too.

Long run:
Skinable? That would be awsome. Maybe plugins as well - Something that the community could help with. 

Quick Q:
Can a pyton be compiled into a .deb file for an install? I don't like having a bunch of folders floating around (like Nexuiz, for example).

Edit: Wow, I was on page 2 when I started writing this. The icon looks amazing as well!

---

### Post by !nkubus on 2006-07-24
Have you looked at libtorrent , it might come handy, it's a well proven bittorrent library. the famous rTorrent is running on it :)

you might be interested :

[http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)

---

### Post by mynimal on 2006-07-25
> **The Noble said:**
> Long run:
Skinable? That would be awsome. Maybe plugins as well - Something that the community could help with.

In my opinion a bittorrent client is something that would be kind of stupid to skin. I think it should just stick to GTK+ and your icon theme.

---

### Post by JoWilly on 2006-07-25
> **mynimal said:**
>  I think it should just stick to GTK+ and your icon theme.

+1

---

### Post by Sammi on 2006-07-25
+1

Think only audio players and IM applications are used by enough silly people to warrant an effort to satisfy their need for strange skins.

Oh and that bittorrent library looks interesting. Especially since it could save programming time and effort :-D

---

### Post by The Noble on 2006-07-26
Wow, I was on windows at the time and forgot about how we can actually skin our entire desktop! ;). Totally did not think there. Scratch that comment.

---

### Post by ~viper~ on 2006-08-02
cool client idea, although i'm moving slowly from gnome to fluxbox (retaining gnome on my system all the while).
i guess the lack of replies means that the hard part is coming: the coding =P.

[quote=The Noble]Wow, I was on windows at the time and forgot about how we can actually skin our entire desktop![/quote]
clearly you haven't examined all the potentials of windows...

---

### Post by BitTorrentBuddha on 2006-08-04
> **~viper~ said:**
> clearly you haven't examined all the potentials of windows...
I believe he meant sans paid party software.

---

### Post by Polygon on 2006-08-04
cool, i will be looking forward to this project. for some reason, the standard ubuntu bittorrent program timessout on some torrent files...

---

### Post by cantormath on 2006-08-04
> **zachtib said:**
> I'm starting a new thread to keep thing simpler, and cause I don't want people to glance over anyting of importance.

First off, the most current screenshots are attached to this post, I'll add newer ones as I get farther along in the program.  Right now, gTorrent is a GUI only, it doesn't actually do anything yet, but I've only been coding for a few days, so all that is still to come. ;)

Second, I need some artwork, specifically an icon.  If you want, make an icon in GIMP, or whatever else you use and post it here. You'll receieve full credit for doing so, and get your name in the about dialog.  Scalable icons are nice, otherwise a 64x64 or so png should work fine, and I'll scale it to whatever size i need.   This icon will be for the application menu, and also for gTorrent's system tray icon.

If I get a bunch of good submissions, I'll likely have a runoff here poll-style :)

finally, any input is greatly appreciated, what does the gui need/not need, etc.  what should the program do on top of simply downloading, if anything?

EDIT: doh! forgot the screenies :-x


Update 6/22/2006
gTorrent is now on SourceForge: [http://sourceforge.net/projects/gtktorrent/](http://sourceforge.net/projects/gtktorrent/)
the name gtorrent was already taken =/ gtktorrent is only what it is listed on SF as, the program itself is still gTorrent.

I like azurues alot

---

### Post by mithras86 on 2006-08-05
What is the status of the project? It seems this is going to be the perfect bittorrent app for Gnome:KS
I'm learning myself python now, so there is a sprank of hope i can participate in the project (although i never programmed before, exept php, so i don't learn that quick ;)).

---

### Post by dragoonmac on 2006-08-17
This project looks awesome, I can't wait to try it out.
I saw you were requesting icon submissions, so I whipped this one up in Photo... I mean the GIMP ;) I tried to follow Tango guidelines, what do you think?

---

### Post by gnomeuser on 2006-08-17
I'd love to see Bittorrent integration with [Mathusalem](http://tw.apinc.org/#mathusalem-gets-useful) - this is by far the best way to handle longterm tasks within GNOME.

I've always hated the idea of having seperate downloaders for different protocols.

---

### Post by aeiah on 2006-08-17
i may be repeating what someone else has suggested, because im at work and havent time to read every single post, but i really like some of the features in utorrent (windows only, annoyingly), specifically automatically moving finished files to a different directory upon completion, and the scheduler they have to cap bandwidth to a certain % of the total available from your isp (to allow for updates and other scheduled downloads outside of gtorrent to have priority for a set period of time, like 16:00-17:00 each day for example).

being able to choose which parts of the torrent to download first (or at all) is a must in my opinion. very useful for downloading discographies when you already have one or two of the albums it contains etc.

---

### Post by reda_ea on 2006-08-17
try this one
[http://www.ubuntuforums.org/showthread.php?t=234700](http://www.ubuntuforums.org/showthread.php?t=234700)
maybe you'll like it

---

### Post by krazyd on 2006-08-20
Perhaps the source of the original 'Mainline' BitTorrent client would be worth inspecting. Being Python and Free Software, it may give you a head start in developing the torrent engine behind gtorrent..

[http://www.bittorrent.com/download.html](http://www.bittorrent.com/download.html)

---

### Post by zachtib on 2006-08-20
> **krazyd said:**
> Perhaps the source of the original 'Mainline' BitTorrent client would be worth inspecting. Being Python and Free Software, it may give you a head start in developing the torrent engine behind gtorrent..

[http://www.bittorrent.com/download.html](http://www.bittorrent.com/download.html)

Not a bad idea, and I'll look into it.

Sorry for the lack of replies, but I've been on Summer Vacation for the last month+, and haven't been doing much of anything except for catching up on sleep.

Now that I'm back at school, I plan on starting work back on gTorrent, and I hope to post some downloads on sf.net soon.

Thanks for maintaining an interest, 

Zach

---

### Post by Polygon on 2006-08-20
i really like the icon that you have on the sourceforge page, is that the final version of the icon?

---

### Post by GuitarHero on 2006-08-20
ignore

---

### Post by mynimal on 2006-09-06
I really hope this hasn't died, so far this completely obliterates any other BT app when it comes to GUI. :/

---

### Post by roderikk on 2006-09-07
I also hope that this hasn't died. Was looking forward to it. However, since a week or so I have been using KTorrent 2.0.2 with great pleasure. It has almost all the features that gTorrent promises (except the K in front of it...) ;-). It is the first torrent client I have found that I can put in my sessions as a startup program and automatically starts downloading again, immediately...

---

### Post by mynimal on 2006-09-07
Have you tried Transmission? I'd use KTorrent but unfortunately I don't like to use KDE apps in Gnome. :P Transmission is great now that I modded the source to finally have a window icon.

---

### Post by etc on 2006-09-07
> **mynimal said:**
> Have you tried Transmission? I'd use KTorrent but unfortunately I don't like to use KDE apps in Gnome. :P Transmission is great now that I modded the source to finally have a window icon.

Can you provide us with a patch :) 

The only reason I don't use Transmission too often is because it's banned from certain trackers.

---

### Post by zachtib on 2006-09-07
Well, i'm having trouble with the torrenting itself.  If any experienced python programmers know anything about bittorrent, i can use the help.

---

### Post by TSP on 2006-09-08
> **zachtib said:**
> Well, i'm having trouble with the torrenting itself.  If any experienced python programmers know anything about bittorrent, i can use the help.

Good to te progress i this project :D i don't know phyton but if you need help testing let me know. All the day i try to compile, use and search for new clients, i am still waiting for a good client with a decent equilibrium (options/resourses)

---

### Post by kripkenstein on 2006-09-08
> **zachtib said:**
> Well, i'm having trouble with the torrenting itself.  If any experienced python programmers know anything about bittorrent, i can use the help.

Zachtib,

I just saw this thread now. I have actually been thinking about writing a GNOME bittorrent client myself, and I see that you are already on the way to the same goal :) So, perhaps I can be of help? I know Python well; I think it's a good choice of language.

Now, as for the bittorrent backend. I guess you have already made a choice here, but I don't know how far along you are. So I'll tell you what I concluded after researching this topic. First, writing one's own backend is no simple task. So, let's assume the use of an existing library. There are then three major options here:

1. libtorrent (this was mentioned in the thread earlier). This is in C++, but bindings for Python are simple to write (I could do this). A big advantage is that libtorrent is well-documented. A disadvantage is that libtorrent has less features than options 2&3 (like encryption, DHT, etc.).
2. The 'standard' Bittorrent engine (Bram Cohen's). This is already written in Python, which is good. Also good is that it has a few things missing from libtorrent, like encryption.
3. libktorrent. This is not a standalone library; it is simply the backend of the ktorrent client for KDE. However, it seems that it *could* be used as a standalone. It is written in C++ (but, again, bindings can be made). It has similar features to option 2. A possible advantage is that ktorrent appears to have more development going on than the 'standard' client.

One important suggestion I would make is to abstract the engine from the GUI. This way, you will be able to switch engines if this is useful at some point (which is a good idea if you rely on external code for your engine).

So, let me know if you'd like my assistance on this project. I can be reached at kripkensteiner -at- gmail.

---

### Post by zachtib on 2006-09-08
> **kripkenstein said:**
> Zachtib,

I just saw this thread now. I have actually been thinking about writing a GNOME bittorrent client myself, and I see that you are already on the way to the same goal :) So, perhaps I can be of help? I know Python well; I think it's a good choice of language.

Now, as for the bittorrent backend. I guess you have already made a choice here, but I don't know how far along you are. So I'll tell you what I concluded after researching this topic. First, writing one's own backend is no simple task. So, let's assume the use of an existing library. There are then three major options here:

1. libtorrent (this was mentioned in the thread earlier). This is in C++, but bindings for Python are simple to write (I could do this). A big advantage is that libtorrent is well-documented. A disadvantage is that libtorrent has less features than options 2&3 (like encryption, DHT, etc.).
2. The 'standard' Bittorrent engine (Bram Cohen's). This is already written in Python, which is good. Also good is that it has a few things missing from libtorrent, like encryption.
3. libktorrent. This is not a standalone library; it is simply the backend of the ktorrent client for KDE. However, it seems that it *could* be used as a standalone. It is written in C++ (but, again, bindings can be made). It has similar features to option 2. A possible advantage is that ktorrent appears to have more development going on than the 'standard' client.

One important suggestion I would make is to abstract the engine from the GUI. This way, you will be able to switch engines if this is useful at some point (which is a good idea if you rely on external code for your engine).

So, let me know if you'd like my assistance on this project. I can be reached at kripkensteiner -at- gmail.

this would be a great help.

if you have an aggount, join the sourceforge project.

I haven't started on the backend at all, i just threw a line of text into the screenshot to show what i'd like it to look like.

libtorrent seemed to be the best option, except it was a C++ lib.  and yes, id like to keep the GUI separate from the frontend, Because someday I may redo the interface in wxWidgets or something to allow running on other platforms.

send me an email if you can help

zach at collegegeek dot org

---

### Post by mynimal on 2006-09-09
That screenshot you showed looks like it could use a little more "pizazz". I don't know, it just looks kind of bland having only text there. Maybe add a status icon (Standard 16x16) to the left of the name, and possibly a graphical progressbar for the percentage? If it used the GTK progressbar of the current skin that'd be awesome, but I don't know how possible that would be.

Also, will the sidebar be toggleable?

**Edit: Here's how you add a window icon to Transmission. I don't know how to make a patch but it's all pretty painless.**

[list]
[*] Download the Transmission source
[*] In the gtk directory, open main.c with gedit or whatever
[*] Find this line: "gtk_window_resize(GTK_WINDOW(wind), width, height);"
[*] Below that line, add: "gtk_window_set_icon_name(GTK_WINDOW(wind), "stock_internet");"
[/list]

This will set the window icon to the icon for the "Internet" category for whatever icon theme you use.

---

### Post by nedkelly on 2006-09-09
Hi 

I think that libtorrent has DHT support at least it says so in their feature list [http://www.rasterbar.com/products/libtorrent/features.html]("http://www.rasterbar.com/products/libtorrent/features.html")

---

### Post by stoeptegel on 2006-09-15
Have you desided what peerid style to use already? Azureus style? Example how not to do it IMO: -TR0006 = Transmission 0.6

---

### Post by zachtib on 2006-09-15
> **stoeptegel said:**
> Have you desided what peerid style to use already? Azureus style? Example how not to do it IMO: -TR0006 = Transmission 0.6

well, we're using python wrappers for the libtorrent library

and on that note, it managed to successfully download a torrent ;)

---

### Post by stoeptegel on 2006-09-17
> **zachtib said:**
> well, we're using python wrappers for the libtorrent library

Hmm, i think there are a few other clients out there that use libtorrent while still using their own peerid. There's nothing against that afaik. 
> 
and on that note, it managed to successfully download a torrent ;)

=D>

---

### Post by zachtib on 2006-09-17
> **stoeptegel said:**
> =D>

My thoughts exactly.

I woke up early today, about 1pm, and spent a fair amount of time coding.  The downloading has been incorporated into the GUI, our previous downloads were with a simple, text based client Kripkenstein wrote in python that used his python-libtorrent library.  (for those of you that are wondering, we are using the libtorrent from sourceforge, not rakshasa's)

The GUI download works, and I simultaneously downloaded the Dapper Desktop CD's of Ubuntu, Kubuntu, and Xubuntu earlier today.  The problems we are running into are that resource usage is rather high, but we seem to have isolated that problem, also the code is very ugly, and pretty inefficient.  We'll likely be going over the code to make it cleaner and (hopefully) faster.

I don't know how close we are to posting the first release up for download.  It could be tomorrow, it could be two weeks from now, but we're getting close.

I'll keep you guys updated and post a new thread in the Cafe as soon as we post the first downloads and are ready for testers.

---

### Post by mithras86 on 2006-09-18
Whohoo! \\:D/ This project is going very well. My compliments=D>

I think a lot user are waiting for this application ;) I hope a pre-alpha is soon available!

---

### Post by zachtib on 2006-09-18
> **mithras86 said:**
> Whohoo! \\:D/ This project is going very well. My compliments=D>

I think a lot user are waiting for this application ;) I hope a pre-alpha is soon available!

I'm coding now.

Well, that and playing with compiz... First time I've ever gotten it working on my laptop (/me curses ATI)

but yeah, right now I'm working on splitting the code into separate files by class (right now its just one big monolithic file) in order to make it easier for multiple people to work on it at once.

---

### Post by mynimal on 2006-09-18
Hahah, it's nice to see some activity in this topic again, especially with good news. :P

I know how you feel with Compiz. I got it installed about 3 days ago and I have been playing with it ever since (I'm a fellow ATI user - Radeon 9600SE :/).

---

### Post by christooss on 2006-09-20
Thanks for this program.

There has been lots of feauture request posted already but I would like to point main one. Release CODE. Why Cause 1. We can help and learn 2. No code avalible is (i think) voilation of GPL. We can stop if project coding is going in wrong direction. It  would be silly if there had to be another rewrite of code in near feauture. I hope this doesn't sound to offensive. Please don't take like that

It would be great if you would set up a page. but that comes after source code. For home page it would be enough a simple CMS like Drupal. You can have many administrators and other stuff.

I don't know how could this be done on sourceforge but I would be really glad if I could help in seting up the page. I think it isn't hard cause there is [http://gtktorrent.sourceforge.net/](http://gtktorrent.sourceforge.net/) which is empty directory.

Again please continue a great work.

---

### Post by zachtib on 2006-09-20
> **christooss said:**
> Release CODE. Why Cause 1. We can help and learn 2. No code avalible is (i think) voilation of GPL.

I'm pretty sure we aren't obligated to release code until the program itself is released.  If you'll notice, there aren't any downloads at all yet.

I want to release gTorrent probably as much as you do, maybe even more.  But there are two or three show-stopping issues that we should be able to hammer out pretty soon.  In fact, Kripken just emailed me a fix for one of them.

It's not that I don't want to release it, it's that we don't want to release something that doesn't feel finished.  Obviously we aren't going to wait for a 1.0 final release before we put it up for download, but right now, there isn't that much there.

Why isn't it out yet? Here's my answer:

We've implemented the torrenting, allowed for multiple torrents in a single window, and allowed the window to hide to the system tray.  These features were the basic premise of the project, so they were the first implemented.

These features, however, introduced a few bugs when the program was run, these bugs are noted on the sourceforge page.

At the moment, we are NOT working on adding new features, just fixing the few bugs that have cropped up.

Once gTorrent can download somewhat reliably, I'll put out a first release, most likely v0.1.0

Or to sum things up graphically, a nice little roadmap:

> 
- v0.0.x - Internal Pre-Alpha branch
[INDENT]- v0.0.1 - Reached
- v0.0.2 - Pending
- v0.0.3 - Towards first public Alpha
- v0.0.99 - Have we fixed everything?[/INDENT]

- v0.x - Public Development Branch
[INDENT]- v0.1.x - Public Alpha branch[/INDENT]
[INDENT][INDENT]- v0.1.0 - First public alpha release - Basic feature set, needs a lot of polish
- v0.1.1	\
- v0.1.2	 } Bugfixes/features towards 0.2.0 release
- v0.1.3	/[/INDENT][/INDENT]
[INDENT]- v0.2.x - Public Alpha branch[/INDENT]
[INDENT][INDENT]    - v0.2.0 - Second alpha release
    - v0.2.1	\
    - v0.2.2	 } Bugfixes/features towards 0.3.0 release
    - v0.2.3 	/[/INDENT][/INDENT]


Basically, the sole point of our little internal branch (0.0.x) is to ensure to ourselves that we know what we're doing, once the code is released, all development will be public.  Like I've said, we're getting really close.

But now I feel like I'm rambling, and I have to go to class soon, so I'm signing off

---

### Post by christooss on 2006-09-20
OK thanks for the anwser. Its my mistake that I haven't tried to download. If I would I would know that there is no download avalible. And of course tjat is not voilation of GPL

Sorry for this mistake. it wont happen again. Shit this hapens to me to many times. :(

And again thanks for the effort. And I hope I will have the knowlengement for helping this project

Again sorry for mistake. And thanks for clearing up things.

---

### Post by zachtib on 2006-09-20
> **christooss said:**
> OK thanks for the anwser. Its my mistake that I haven't tried to download. If I would I would know that there is no download avalible. And of course tjat is not voilation of GPL

Sorry for this mistake. it wont happen again. Shit this hapens to me to many times. :(

And again thanks for the effort. And I hope I will have the knowlengement for helping this project

Again sorry for mistake. And thanks for clearing up things.

no problem, and no offense taken

the community's eagerness for this program is what's keeping me working on it

---

### Post by Krakatos on 2006-09-24
Well, I must say I am extremely interested in this project. I switched to Linux not so long ago, and I must say I love Ubuntu, but some applications leave a little to be desired. And one of them is a bittorrent client...

I mean, as of now we have:
Azureus.. very good but honestly soo heavy
Ktorrent: good but.. doesn't work THAT well under gnome...
Bittorrent and such: too few features

That is why I have my hopes up :) I read that you have in mind utorrent. That's good, utorrent is a very good client... if you manage to do something like that for gnome.. I (and many more people) will be grateful :)

Just a small suggestion you most likely already considered (but it never hurts to repeat it..), you should probably try to gain visibility once the basic program works. That way, you can get other people to help you develop it. And who knows, maybe gTorrent will one day be the default gnome bittorrent client :)

---

### Post by zachtib on 2006-09-24
> **Krakatos said:**
> Just a small suggestion you most likely already considered (but it never hurts to repeat it..), you should probably try to gain visibility once the basic program works. That way, you can get other people to help you develop it. And who knows, maybe gTorrent will one day be the default gnome bittorrent client :)

I was going to try to knock out the last few bugs this weekend, but I live in Kentucky (go to school in Louisville, home is in Lexington), and you may have heard about the weather here this weekend.  Flooding, tornados, thunderstorms, etc.  My house was out of power for a good chunk of the weekend, so I was unable to work on the client.  But I have hopes for a first alpha release soon.

---

### Post by Krakatos on 2006-09-24
Well, I waited since I installed Ubuntu (and that means that all the users more experienced than me waited a LOT more :p ) so it's not like there's this much hurry. As long as you keep working on it, it's all fine. 

Once the program is out and it starts to spread.. then it will also acquire momentum on its own, provided it is made so that more than one person can develop it at the same time. Those kind of things inevitably grow on their own :)

---

### Post by zachtib on 2006-09-24
there's actually two of us working on it right now.  the program is split into several files to allow for this

---

### Post by mithras86 on 2006-09-26
Why don't you use SF.net anymore? I see you are hosting your project now at [Google]("http://code.google.com/p/deluge-torrent/"). Also changed the name to Deluge.
Note that I think it's still a great project, but why these changes?

About the alpha: I have not tested it yet, I'll do as soon I'm home again (when i'm back from school)

---

### Post by c0nfidencal on 2006-09-26
w00t

---

### Post by kripkenstein on 2006-09-26
> **mithras86 said:**
> Why don't you use SF.net anymore? I see you are hosting your project now at [Google]("http://code.google.com/p/deluge-torrent/"). Also changed the name to Deluge.
Note that I think it's still a great project, but why these changes?


The [other thread]("http://www.ubuntuforums.org/showthread.php?t=265119") explains some of this. Basically the name gTorrent was (1) taken in the past, and (2) seems to imply the app is gnome-only (but it isn't, it just uses gtk+). As for Google instead of SF, the Google hosting seems to have a nice clean minimalistic interface, and works well for now. I don't think we have anything against SF, it's a great site.

---

### Post by Krakatos on 2006-09-27
> **kripkenstein said:**
> The [other thread]("http://www.ubuntuforums.org/showthread.php?t=265119")  As for Google instead of SF, the Google hosting seems to have a nice clean minimalistic interface, and works well for now. I don't think we have anything against SF, it's a great site.

Well, I must say I disagree a little. The point here is that honestly, sourceforge offers visibility once you start to have a little activity. And visibility means more interested peoples, more coders, more users, more everything. You CAN do it with other means of course, but please as you start to hit "stable" releases later on, consider a way to get visibility- It's really important, so that this does not become just another niche project.

Just my suggestion of course

---

### Post by Choad on 2006-10-28
this is exactly what the linux desktop needs (well, the gtk using linux desktop crowd)

where's the source? i wanna take a peek see if theres anything i could improove (doubt there will be, but u know im interested anyway... im trying to learn py-GTK atm)

edit: found... post #1 surprisingly enuff lol

edit2: oh... no i havent. is the source code not available?

---

### Post by CarpKing on 2006-10-28
> **Choad said:**
> this is exactly what the linux desktop needs (well, the gtk using linux desktop crowd)

where's the source? i wanna take a peek see if theres anything i could improove (doubt there will be, but u know im interested anyway... im trying to learn py-GTK atm)

edit: found... post #1 surprisingly enuff lol

edit2: oh... no i havent. is the source code not available?

This project has been renamed Deluge and now has its own subforum!
[http://www.ubuntuforums.org/forumdisplay.php?f=172](http://www.ubuntuforums.org/forumdisplay.php?f=172)

---

### Post by Choad on 2006-10-28
thanks

---

### Post by ashmew2 on 2006-11-18
Please add a new feature , i dot think any torrent client has ever had this feature , but still i think it would be better if u add this feature :
Support for Multiple torrents downloading one after the other.
For example , putting them in a line from top to bottom and as soon as torrent 1 finishes downloading and reaches a desired UL/DL ratio , the second torrent starts downloading. cuz downloading small files is a pain in the a$$.THanks

---

### Post by roderikk on 2006-11-18
> **ashmew2 said:**
> Please add a new feature , i dot think any torrent client has ever had this feature , but still i think it would be better if u add this feature :
Support for Multiple torrents downloading one after the other.
For example , putting them in a line from top to bottom and as soon as torrent 1 finishes downloading and reaches a desired UL/DL ratio , the second torrent starts downloading. cuz downloading small files is a pain in the a$$.THanks

There is a seperate subforum for Deluge (what used to be gTorrent). You can post your requests there.

---

### Post by anaconda on 2006-11-18
> **XQC said:**
> Priority settings
There are directory torrents, from which you only want actually one file or you want a file earlier than the others.

Yep. this is a must! I often want just 1 smaller file from 8-20GB download file

---

### Post by kripkenstein on 2006-11-18
> **anaconda said:**
> I often want just 1 smaller file from 8-20GB download file

Most clients allow this: Azureus, utorrent, also Deluge (a.k.a. gTorrent).

---

### Post by Valehru on 2007-02-25
Probably a stupid question, but is there a pluggin or a setting that needs to be enabled to minimize the application to the notification tray?  I can't seem to find it.  This functionality is a must in my opinion as I often don't want my torrent window to be on any of my desktops.  

I think that this functionality is already available in ktorrent at the moment.

EDIT:  Never mind, found out how to do it. Click on the icon with the right mouse button. That should toogle the application from appearing/disappearing.

---

### Post by reets on 2007-05-04
This can now be found @ [http://deluge-torrent.org/](http://deluge-torrent.org/)

---

### Post by econobeing on 2007-06-06
i love the program :D good job on it.

---

### Post by mech7 on 2007-06-06
It needs to work exactly the same as uTorrent then i am happy :D So open torrent i can check on and off files.. When i open a torrent from my browser this app opens, so that i don't have to save it first to my hdd and then open it.. That is to much trouble.

Now with the lists of torrents when i click it i want to go to the file.. and when i delete it, it should not delete the downloaded files. 

Also when i have deleted the files after it has completed the program should never redownload them again, but recognizes that i allready downloaded them before.

These are some of the issues that exists with Deluge and are frikking annoying 0_o

---

### Post by maniacmusician on 2007-06-06
you should probably post about them in the Deluge subforum where the developers will actually see you your comments.

---

### Post by mech7 on 2007-06-07
you mean the closed one ;)

---

### Post by NJN on 2007-06-07
How about the new one: [http://forum.deluge-torrent.org/](http://forum.deluge-torrent.org/)

---

### Post by Guardian-Mage on 2007-10-12
Try and make it look like uTorrent for Windows, uTorrent is awesome,

good job, I was going to start making a GUI torrent client for linux since I couldn't find any for GNOME but you beat me to it.:)

---

### Post by Polygon on 2007-10-12
go join the deluge team, if you can code then im sure you can find something to hack away on :D

---

### Post by graabein on 2007-10-12
> **Guardian-Mage said:**
> Try and make it look like uTorrent for Windows, uTorrent is awesome,

I agree! I've been using Windows XP for many months and been impressed by [uTorrent]("http://www.utorrent.com/"). Very nice program. That and [foobar2000]("http://www.foobar2000.org/") should be cross-platformed or written natively for GNU/Linux.

---

### Post by misse- on 2007-10-21
I didn't read all the posts, but I searched this thread for the word "queue" .. And nothing, so I want to suggest that you build support for just queueing in the client, something that I haven't seen in any linux client so far.

---

### Post by Polygon on 2007-10-21
post this on the main deluge website forums

[www.deluge-torrent.org](www.deluge-torrent.org)

---

### Post by zachtib on 2007-10-24
why are people still posting in this thread?

---

