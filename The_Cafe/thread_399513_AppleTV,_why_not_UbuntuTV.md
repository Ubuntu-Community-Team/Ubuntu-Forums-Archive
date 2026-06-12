---
title: "AppleTV, why not UbuntuTV???"
date: 2007-04-02
forum: The Cafe
---

### Post by amoore on 2007-04-02
AppleTV, why not UbuntuTV??? With all the hubbub about AppleTV lately, it got me thinking about a possible UbuntuTV. Ubuntu would be a perfect host OS for something like a AppleTV variant. 

Before I get started, I'm well aware of MythTV, Freevo, and LinuxMCE and what these do. I have a MythTV Box but damn, it was a real pain in the A** to configure but, I have it all up and running flawlessly. "I would never expect Joe User to get a box like Mythtv going on his own." So, for the Average Joe, we could start UbuntuTV 

AppleTV Just streams A/V Content(MP3, AAC, MOV, MP4,Jpeg,PNG ect) from a PC to an AppleTV. 

UbuntuTV, in theory could do this too, using [[COLOR="RoyalBlue"]Avhai,[/COLOR]]("http://avahi.org/") Avhai is Zero  conf networking tool already packaged in Ubuntu and with [[COLOR="RoyalBlue"]Mt-Daapd, now know as Firefly[/COLOR]]("http://www.fireflymediaserver.org/") also packaged in Ubuntu.

Both Avhai and Mt-Daapd are a breez to setup and could be installed by default to a live CD Thus, UbuntuTV is Born. 

I believe AppleTV uses these similar protocols too.

Now we need a slick user gui like AppleTV. It would be nice if we could get something like Macslow's [COLOR="Blue"][[COLOR="Blue"]Lowfat[/COLOR]]("http://youtube.com/watch?v=GkrM4ymkiDo")[/COLOR] as a user gui to alternate between the different categories: Music, Videos, Podcast,Pictures, CD and DVD. I also believe that capturing album, CD, and DVD art and info could be done with simple scripts from CCDB, IMDB, and Amazon.

The use of a remote control could be implemented by using the LIRC packages in Ubuntu for IR remotes.

Ideally it would be nice if this was a live CD that a user just popped in their machine and installed it with setup screens for the remote, and Xorg configs for TV out.

If there is any interest in starting a UbuntuTV package or UbuntuTV distro feel free to PM me or post on this Thread.

---

### Post by mykalreborn on 2007-04-02
ubuntu tv as in watch actual shows from tv channels on the computer via internet streaming or... ?

---

### Post by amoore on 2007-04-02
Uhmmm, no, but guess that [[COLOR="Blue"]Sopcast[/COLOR]]("http://www.sopcast.org/") could be implemented into the project also, [[COLOR="Blue"]Joost[/COLOR]]("http://www.joost.com/") could be added when a Linux client is available. Sopcast is available for Ubuntu but not in the repos. if you would like to see Sopcast there is a [[COLOR="Blue"]how to on the forums  [/COLOR]]("http://ubuntuforums.org/showthread.php?t=258049&highlight=sopcast") the How to uses a Asian website to get the .debs from but they work good in edgy. There are also a lot of Asian TV channels to pick from

AppleTV just streams content such as avi, mp3, mov, oog,  mp4, pictures, and ect. from one computer to a TV.

Sopcast and Joost are P2P networks that stream live TV.

Good idea on adding P2P live TV

---

### Post by IYY on 2007-04-02
Do you think it's possible to make the final product cost about as much as AppleTV? Would it be a software or hardware+software product?

---

### Post by amoore on 2007-04-02
> **IYY said:**
> Do you think it's possible to make the final product cost about as much as AppleTV? Would it be a software or hardware+software product?


I believe that UbuntuTV should be free, just like all the other (*)Ubunut variants. Also this would be a distro or package that would allow one to install it on a PC and then hook the pc to a TV. Then all of the other PCs in a home could stream content to a TV.

See the [[COLOR="Blue"]AppleTV home[/COLOR]]("http://www.apple.com/appletv/") page for more info on AppleTV 

[http://www.apple.com/appletv/](http://www.apple.com/appletv/)

[IMG]http://images.apple.com/appletv/images/syncfloorplan_20070109.png[/IMG]

---

### Post by amoore on 2007-04-02
Apple TV is “for people who are yearning for a simple way to show on their big TVs all that stuff trapped on their computers.”
— Walt Mossberg and Katherine Boehret,
    Wall Street Journal

---

### Post by mykalreborn on 2007-04-02
oh i get it. pretty cool. but since my lcd monitor is way better than my small tv, this ain't for me. :D
nice idea though. good luck with the project, if it gets started!

---

### Post by alaaji on 2007-04-04
Good idea.  I hope you can get this going.  By the way, what do you think of [www.orb.com]("http://www.orb.com")?

---

### Post by majoridiot on 2007-04-04
there's is a project called **mythbuntu** in the works that will install mythtv from a live cd, doing
most of the "troublesome" configuration for you... and will also run a remote frontend from the live
disc as well, i believe.  of course the configuration of tuners and program listsings, etc. will still be
needed, but the installation process with be GREATLY simplified.

the project is is very good shape, from reports... so you should expect to see it sometime in the 
coming weeks.

---

### Post by amoore on 2007-04-06
> **alaaji said:**
> Good idea.  I hope you can get this going.  By the way, what do you think of [www.orb.com]("http://www.orb.com")?

Orb looks cool, I've seen it before but, I don't know that much about it. I'm waiting for joost. I'm floating the Idea for ubuntu tv right now.

---

### Post by Shawn Dineley on 2007-04-06
How about using MMS (My Media System) as the GUI.

[http://mms.sunsite.dk/](http://mms.sunsite.dk/)

---

### Post by Brunellus on 2007-04-06
God in Heaven.  **Joe User doesn't set up Apple TV on his own, either**.  The only 'meaningful' interpretation of "UbuntuTV" would be a piece of hardware with Ubuntu + Mythtv preinstalled.

For people who know they have suitable hardware--there's Knoppmyth.

---

### Post by amoore on 2007-05-08
I found a great open source project kinda like AppleTV.  Elisa is an open source media cent aimed at being somewhat easer than Mythtv. The Project is still in beta and is somewhat buggie but it shows real potential. 


**About Elisa**

Elisa is a project to create an open source cross platform media center solution. While our primary development and deployment platform is GNU/Linux and Unix operating systems we also currently support Microsoft Windows and also hope to support MacOSX in the future. Elisa runs on top of the GStreamer multimedia framework and takes full advantage of harware acceleration provided by modern graphic cards by using OpenGL APIs. In addition to personal video recorder functionality (PVR) and Music Jukebox support, Elisa will also interoperate with devices following the DLNA standard like Intel’s ViiV systems.

The core Elisa system is licensed under the GPL version 2. The GPL part of Elisa is also available under a commercial licensing agreement from Fluendo. Elisa core plugins are licensed under the MIT license agreement.

Elisa is developed by Fluendo.

Elisa home page: [http://elisa.fluendo.com/]("http://elisa.fluendo.com/")

First time set up: [https://core.fluendo.com/elisa/trac/wiki/FirstRun]("https://core.fluendo.com/elisa/trac/wiki/FirstRun")

See Elisa in action: [http://elisa.fluendo.com/screenshots/]("http://elisa.fluendo.com/screenshots/")

---

### Post by Mateo on 2007-05-08
I don't get AppleTV.  What does it do that a computer can't already do?  You can hook your computer up directly to the television.  What is the need for AppleTV?

---

### Post by Brunellus on 2007-05-08
> **Mateo said:**
> I don't get AppleTV.  What does it do that a computer can't already do?  You can hook your computer up directly to the television.  What is the need for AppleTV?
it's a set-top box.  from Apple.  that's (slightly) cheaper than getting a miniMac.

---

### Post by Mateo on 2007-05-08
I don't get that though.  What is a "set-top box"?  You mean like a cable box?  Those you have to have or otherwise you can't get the channels.  You can't hook your cable connection (talking about digital cable) directly to the television.  But you can hook up the computer directly to the television.  So again, what does this thing do?

edit:  i guess it just has the graphical interface already  built in?

---

### Post by Redache on 2007-05-08
Basically it's like a Wireless box with a hard drive. It means you don't have to spend the cash on a second computer and you can use it to stream stuff from your PC to your TV without having to have them in the same room.

---

### Post by tehbeermang on 2007-05-22
I looked into using a miniITX board with onboard tv-out to build my own.

After looking into everything, the cost difference is negligible. Might as well buy the AppleTV and employ the hacks.

Except for people like me. I don't have the prescribed "widescreen" tv. I'm back to building an UbuntuTV. :D

---

### Post by a12ctic on 2007-05-22
Buy a used xbox, throw in a cheapy mod chip, install XBMC, buy a cheap wireless gaming adapter, and you have everything you could get with apple tv and a lot more like youtube, a bunch of emulators, xbox games, etc. I know a lot of you are saying "OMG AND SUPPORT MICROSOFT?!" Thats not the case because MS sells the xbox for a loss, they make their money on games.

---

### Post by amoore on 2007-05-23
Well, it's official!!! The Ubuntu media center will be a new Ubuntu distro spin off. The UMC will use Elisa as the application of choice for it's Media center. Check out the Ubuntu Media Center Wiki and the Elisa Homepage. The project has been blessed by Mark Shuttlesworth  SABDFL and the the dev team for Elisa at Fluendo.

Ubuntu Media Center Wiki[URL="https://wiki.ubuntu.com/UbuntuMediaCenterTeam"]
https://wiki.ubuntu.com/UbuntuMediaCenterTeam[/URL]


Elisa Homepage
[http://elisa.fluendo.com/]("http://elisa.fluendo.com/")

A few days ago, the Ubuntu Community Council has blessed the Ubuntu Media Center project with a great enthusiasm. Here are some quotes from the meeting log:

MediaCenter/CocMeeting070515

This is an excerpt of the Ubuntu Community Council meeting, that took place on May, 15th 2007. Only the part about the UMC project are kept.

--> You are now talking on #ubuntu-meeting

<Uzuul> Hi there. I'm Arnaud Quette, from the UMC team ([WWW] [https://wiki.ubuntu.com/UbuntuMediaCenterTeam](https://wiki.ubuntu.com/UbuntuMediaCenterTeam)) ...

<dholbach> next item: Uzuul wants blessing for the [WWW] [https://wiki.ubuntu.com/UbuntuMediaCenterTeam](https://wiki.ubuntu.com/UbuntuMediaCenterTeam)

<Uzuul> I've put the latest status & roadmap here: [WWW] [https://wiki.ubuntu.com/UbuntuMediaCenterTeam/Status20070514](https://wiki.ubuntu.com/UbuntuMediaCenterTeam/Status20070514)

we're on the road to success, federating *all* the players in the field (Debian, Ubuntu, Elisa, LIRC, ...) to work together...

<jsgotangco> that's a healthy spread of team members

<jsgotangco> how do you forsee this project going during gutsy development?

<Uzuul> jsgotangco: well, we will have releasable things. Elisa 0.2 will be out for the Guadec, packages are underway...

<elmo> sorry, but what does federating mean in this context?

<Uzuul> the only point is about the artwork (missing gfx designers) and the achievement of our UI goals. I've no exact idea yet!

<dholbach> looks like you have lots of ideas and a lot of people in the team

    *

      how many people are working on getting the changes you propose into Ubuntu?

<Uzuul> elmo: team members, working together on the same aims...

    *

      dholbach: some 10 peoples really active. but we are quickly growing...

<dudanogueira> Uzuul, i know a very good gfx designer. vdepizzol. he probably will be very interested in design it.

<dholbach> I'm asking because the goals you propose in [WWW] [https://wiki.ubuntu.com/MediaCenter/SoftwareSpecs](https://wiki.ubuntu.com/MediaCenter/SoftwareSpecs) look quite some work

<Uzuul> dholbach: we work a lot upstream, so hiting ubuntu by side effect...

<Uzuul> dholbach: Elisa team already address a lot ;-) Isn't it Kaleo

<Kaleo> About the artwork, we have a graphist in the Elisa team

<Uzuul> dudanogueira: thanks for this. I'll contact him...

<Kaleo> Feature-wise, Elisa is meant to achieve many of the points listed in [WWW] [https://wiki.ubuntu.com/MediaCenter/SoftwareSpecs](https://wiki.ubuntu.com/MediaCenter/SoftwareSpecs) soon

<sabdfl> as i understand it, the initial step is just packaging Elisa, right?

    *

      that in itself would be a very good start

<dudanogueira> Uzuul, he is wright here: [WWW] [http://vdepizzol.wordpress.com/](http://vdepizzol.wordpress.com/)

<jsgotangco> that's how i got it as well

    *

      package Elisa, and have it on Ubuntu as a good platform

<sabdfl> that's fine by me!

<Uzuul> sabdfl: right ! I'm working, as a DD, with Loic Minier, on this point.

<sabdfl> super

<sabdfl> once you have a core piece of software like that in place, you can build a custom derivative easily enough

<Uzuul> sabdfl: but that's just a small beginning. The big things comes then ;-)

<sabdfl> well, let's take one step at a time :-)

<jsgotangco> there's huge interest in having free software in the entertainment hub and having this go along with Ubuntu will definitely create a following

<Uzuul> sabdfl: right, but some things can be done in // without impacting the schedule (like the LIRC improvements) ;-)

<sabdfl> we get a LOT of requests for media centre functionality, so it will be great to be able to point folks at Elisa

    *

      LIRC?

<Seveas> infrared

    *

      remote control things

<jsgotangco> ahh for all-in-one remotes

<mako> sabdfl: absolutely

<Treenaks> (shouldn't lirc be replaced by proper kernel input drivers?)

<dholbach> I'm very happy you're keen on getting this done and are so enthusiastic about it; I'm with sabdfl here: I'd recommend splitting up the long list of goals in tiny tiny tasks, so you can easily track them and get people involved with them

<Uzuul> sabdfl: [WWW] [https://wiki.ubuntu.com/RemoteControls](https://wiki.ubuntu.com/RemoteControls)

<Daviey> Treenaks, being worked on already

<Treenaks> Daviey: \o/

<Uzuul> Daviey: can you contact me back for more info? I have a task underway upstream on that...

<Daviey> Uzuul, pm

<Uzuul> dholbach: the tasks splitting is planned.

<sabdfl> Uzuul: what do you need from us right now?

<Uzuul> sabdfl: an official blessing, and a mailing list.

<sabdfl> +1 from me

<MikeB-> +1 from me, definitely an area Ubuntu should support

<jsgotangco> there's some work to be done, but it seems there is more work being accomplished upstream, so I would give my +1 as well to have something for Ubuntu in the future

<dholbach> +1

<mako> if you really have ~30 members, it seems that this would be overdue

    *

      +1 from me

<sabdfl> elmo?

<dholbach> Uzuul: it'd be nice to hear back from you team every now and then to see how you're progressing (maybe on one of the other mailing lists)

<elmo> +1

<sabdfl> Uzuul: i think you can proceed, elmo will likely chime in with additional comments and questions in due course

<sabdfl> ok

<sabdfl> congrats Uzuul! please keep us posted, and good luck building your team

<jsgotangco> Uzuul: good luck along with the team!

<Kaleo> thank you guys :)

<Uzuul> sabdfl: thanks fellows. I'll keep you informed (any prefered ml?)

<philn> \o/

* kjcole is here

<hku> cool :)

<sabdfl> Uzuul: keep the UWN folks abreast of news that the whole community will be interested in, and perhaps report back here every month or so initially

<sabdfl> dcteam!

<dudanogueira> Uzuul, congrats!

<sabdfl> let's go

* beuno takes nots for the UWN

<beuno> *notes

...

<Uzuul> all: thanks. we'll do the necessary to succeed. see you soon. bye

...

<beuno> Uzuul: get in touch with me for the UWN

...

last edited 2007-05-15 19:51:50 by ArnaudQuette
© 2005 Canonical Ltd. Ubuntu, Kubuntu, Edubuntu and Can

---

### Post by mattdee on 2007-05-23
Well Playstation just announced support for DLNA in the latest firmware update...

Now....if I could figure out how to DLNA-enable my PC...

---

### Post by webdr on 2007-05-24
Seems like a ruckus wireless zoneflex would be cheaper, easier, and more beneficial.
[URL="http://www.ruckuswireless.com/press/releases/20070521b.php"]
http://www.ruckuswireless.com/press/releases/20070521b.php[/URL]

---

### Post by MetalMusicAddict on 2007-05-24
Im very interested in the project but don't think it warrants another derivative. IMO it should be a overlay to Ubuntu.

Id like to know the rational for a new disk.

---

### Post by amoore on 2007-05-29
The rational is that its to hard to set up a media center. Many packages need to be installed and set up correctly such as, codecs, lirc, apps, and ect. A new distro could thin out apps you don't need for a media center like "openoffice.org" and replace this free space for apps that are media center like. You could always install the media center on top of a regular install of Ubuntu but, having everything you need on one disk and configured automatically is a nice touch.

---

### Post by jiminycricket on 2007-05-29
Have you guys seen the news on [digg]("http://digg.com/linux_unix/XBMC_recruiting_developers_for_Linux_port#c6925168")?  XBMC (Xbox Media Center) is coming for Linux, and they have instructions to get it running on Ubuntu.  They're porting it to SDL, so it should work on the AppleTV, Windows, XP, GNU/Linux, etc..

---

### Post by amoore on 2007-05-30
WOW!! Looks great! I wonder how long it will take to port and how easy will it be set up? Easy set up is crucial most media centers suffer from overly difficult  set up. I will say that XBMC looks very promising

---

