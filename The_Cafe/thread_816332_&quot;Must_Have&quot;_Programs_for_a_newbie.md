---
title: "&quot;Must Have&quot; Programs for a newbie"
date: 2008-06-02
forum: The Cafe
---

### Post by KingTermite on 2008-06-02
Please help us newbie's out and help us with a comprehensive list of "must have" apps that aren't installed by default. Whether they are apps in the repositories (and not installed by default) or must be attained elsewhere.

Don't hold anything back..even programs you think "everybody" knows about may not be known about by a newbie. As an example, I'd say something like "wine". A newbie may not know about wine, so don't hold back because you think everybody knows about it.

So, if you please, in this format.

app name
brief description
where you can get it


Example:
Wine
Allows you to install/use some windows applications
Available in repositories (newest version at [http://www.winehq.org/](http://www.winehq.org/))
------------------------------------------------

---

### Post by Fire_Chief on 2008-06-02
Could you specify which version of Ubuntu you want to compare against for whether the app is pre-installed or not? It does change a little bit between Gutsy and Hardy.

Thanks!

---

### Post by KingTermite on 2008-06-02
> **Fire_Chief said:**
> Could you specify which version of Ubuntu you want to compare against for whether the app is pre-installed or not? It does change a little bit between Gutsy and Hardy.

Thanks!

Oh....didn't think of that. I was meaning it to be a more general thread (for many newbies), so maybe if you know some its worth mentioning that's installed in one version and not the other.

I'm using the most recent Ubuntu, 8.04.

---

### Post by Fire_Chief on 2008-06-02
Brasero
Disc burning application (CD/DVD/other)
Gutsy: Available in repositories (latest on site [http://www.gnome.org/projects/brasero/]("http://www.gnome.org/projects/brasero/"))
Hardy: Installed by default


Deluge 
Bittorrent Client
Gusty: Available in repositories (latest on site [http://deluge-torrent.org/]("http://deluge-torrent.org/"))
Hardy: Available in repositories (have not tried Transmission bittorrent client on Hardy (preinstalled))

---

### Post by cardinals_fan on 2008-06-02
Opera
Fast and powerful web browser
Get the stable version [here]("http://www.opera.com/download/index.dml?platform=linux"), the new beta (which is strongly recommended) [here]("http://www.opera.com/download/index.dml?platform=linux&ver=9.50b2")

Conky
Monitoring tool for your desktop
In the repos, read [this huge thread]("http://ubuntuforums.org/showthread.php?t=281865") for tips

Qalculate
An extraordinarily powerful calculator
In the repos, use the [gtk version]("http://packages.ubuntu.com/hardy/qalculate-gtk") if running GNOME

Koffice
A great office suite
If you're running KDE, or have disk space to burn, it's in the repos

dwm
OK, it might not be for the total newbies (unless they're willing to climb a vertical learning curve).  But this tiling wm is unbelievably fast and powerful
Download the source from [here]("http://www.suckless.org/wiki/dwm/").  There's no point to a package, because all configuration is done through the source code.

---

### Post by KingTermite on 2008-06-02
> **cardinals_fan said:**
> Conky
Monitoring tool for your desktop
In the repos, read [this huge thread]("http://ubuntuforums.org/showthread.php?t=281865") for tips

Qalculate
An extraordinarily powerful calculator
In the repos, use the [gtk version]("http://packages.ubuntu.com/hardy/qalculate-gtk") if running GNOME

dwm
OK, it might not be for the total newbies (unless they're willing to climb a vertical learning curve).  But this tiling wm is unbelievably fast and powerful
Download the source from [here]("http://www.suckless.org/wiki/dwm/").  There's no point to a package, because all configuration is done through the source code.

Some I'm not familiar with, thanks. Qalculate looks worth a look-see for sure. dwm doesn't sound very nice to me. As a developer myself, I consider it bad coding to have to tweak source code and recompile just to change settings.

---

### Post by aktiwers on 2008-06-02
Preload:
```
sudo apt-get install preload
```

As I understand how it works " It learns what programs you use must, and preload them for better performance". Once installed, it does the rest for you.

---

### Post by SomeGuyDude on 2008-06-02
Deluge - bitTorrent client numero uno

Conky - system monitor

Wine - run your favorite windows programs

CompizConfig-Settings-Manager - need this to customize the eye-candy effects.

The "build-essential" package - for software installation sometime down the road

flashplugin-nonfree - obviously, to show flash in web pages.

---

### Post by cardinals_fan on 2008-06-02
> **KingTermite said:**
> dwm doesn't sound very nice to me. As a developer myself, I consider it bad coding to have to tweak source code and recompile just to change settings.
But it keeps things very simple and FAST.  It doesn't process any input data at startup, and there's no special config-file syntax to learn.  It compiles obscenely quickly anyway.

---

### Post by mmb1 on 2008-06-02
"Must Have" is subjective to the user's needs, but here's my list

gtkpod:  ipod management
Mirage:  image viewer
thunar:  file manager
vlc:     cross-platform video player.

---

### Post by KingTermite on 2008-06-02
> **cardinals_fan said:**
> But it keeps things very simple and FAST.  It doesn't process any input data at startup, and there's no special config-file syntax to learn.  It compiles obscenely quickly anyway.
How long would it take to parse a quick text file at startup? And it's only once...it's not like it would have to access the file every time it opened a window or something. The running speed would be no different, just a "slightly" slower (1 ms tops) startup speed. Just bad programming style, IMO.

---

### Post by KingTermite on 2008-06-02
> **SomeGuyDude said:**
> Deluge

Conky

Wine

CompizConfig-Settings-Manager

The "build-essential" package

flashplugin-nonfree

Can you explain please?

What's Conky?
What's CompizConfig?

This is a newbie thread....so as I mentioned, don't assume everybody knows what they are. The others *I* happen to know, but others may not.

---

### Post by swoll1980 on 2008-06-02
Sun's Virtual Box: Allows you to run virtual machines(OS that runs like an application) like Windows XP inside of a Linux environment. Can't live with out it! You can also use it to do cool things like check out the Ubuntu development in really early alpha without having to install to a partition

---

### Post by cardinals_fan on 2008-06-02
> **KingTermite said:**
> How long would it take to parse a quick text file at startup? And it's only once...it's not like it would have to access the file every time it opened a window or something. The running speed would be no different, just a "slightly" slower (1 ms tops) startup speed. Just bad programming style, IMO.
To each their own.  Dwm does **exactly** what I want it to and nothing else.

---

### Post by SomeGuyDude on 2008-06-02
> **KingTermite said:**
> Can you explain please?

What's Conky?
What's CompizConfig?

This is a newbie thread....so as I mentioned, don't assume everybody knows what they are. The others *I* happen to know, but others may not.

My bad. I'll edit the post.

---

### Post by swoll1980 on 2008-06-02
I will add Exaile to. Best GTK music player around

---

### Post by KingTermite on 2008-06-03
I've heard people talk about Virtual Box and other talk about VMWare (which I've used on Windows).

Are they basically the same thing and if so are there any major advantages of one over the other?

> **swoll1980 said:**
> Sun's Virtual Box: Allows you to run virtual machines(OS that runs like an application) like Windows XP inside of a Linux environment. Can't live with out it! You can also use it to do cool things like check out the Ubuntu development in really early alpha without having to install to a partition

---

### Post by SomeGuyDude on 2008-06-03
> **swoll1980 said:**
> I will add Exaile to. Best GTK music player around

DEFINITELY the best replacement for iTunes junkies (I still maintain that amaroK is too bloated).

---

### Post by billgoldberg on 2008-06-03
> **KingTermite said:**
> Please help us newbie's out and help us with a comprehensive list of "must have" apps that aren't installed by default. Whether they are apps in the repositories (and not installed by default) or must be attained elsewhere.

Don't hold anything back..even programs you think "everybody" knows about may not be known about by a newbie. As an example, I'd say something like "wine". A newbie may not know about wine, so don't hold back because you think everybody knows about it.

So, if you please, in this format.

app name
brief description
where you can get it


Example:
Wine
Allows you to install/use some windows applications
Available in repositories (newest version at [http://www.winehq.org/](http://www.winehq.org/))
------------------------------------------------

Either from the ubuntu or medibuntu reop:

vlc media player
p7zip-full / adds rar, zip, 7z, ... support to archive manager
compiz fusion manager
exaile /decent music player
adobe reader
frostwire /free limewire pro spinoff
emesene /IM client for msn
"ubuntu-restricted-extras" /install flash, mp3 support, ...
"non-free-codecs" /some win32 codecs, divx, ...
"libdvdcss" /dvd support
"sun-java6-jre"/ java (remove "open-java" first
firefox totem plugin /use it to watch windows media files online, ...

thats about it I think

oh and:

pytube media converter

it's not in the repo's, check my signature for it.

---

### Post by billgoldberg on 2008-06-03
> **cardinals_fan said:**
> Opera
Fast and powerful web browser
Get the stable version [here]("http://www.opera.com/download/index.dml?platform=linux"), the new beta (which is strongly recommended) [here]("http://www.opera.com/download/index.dml?platform=linux&ver=9.50b2")

Conky
Monitoring tool for your desktop
In the repos, read [this huge thread]("http://ubuntuforums.org/showthread.php?t=281865") for tips

Qalculate
An extraordinarily powerful calculator
In the repos, use the [gtk version]("http://packages.ubuntu.com/hardy/qalculate-gtk") if running GNOME

Koffice
A great office suite
If you're running KDE, or have disk space to burn, it's in the repos

dwm
OK, it might not be for the total newbies (unless they're willing to climb a vertical learning curve).  But this tiling wm is unbelievably fast and powerful
Download the source from [here]("http://www.suckless.org/wiki/dwm/").  There's no point to a package, because all configuration is done through the source code.

those aren't "must have" programs by a long shot.

Suggesting difficult to use programs like conky to new users -> no
koffice on gnome? -> no
tiling wm's -> no no no no
and a calculator -> again no

---

### Post by KingTermite on 2008-06-03
> **billgoldberg said:**
> Either from the ubuntu or medibuntu reop:

vlc media player
p7zip-full / adds rar, zip, 7z, ... support to archive manager
**compiz fusion manager**
exaile /decent music player
adobe reader
frostwire /free limewire pro spinoff
emesene /IM client for msn
"ubuntu-restricted-extras" /install flash, mp3 support, ...
"non-free-codecs" /some win32 codecs, divx, ...
"libdvdcss" /dvd support
"sun-java6-jre"/ java (remove "open-java" first
firefox totem plugin /use it to watch windows media files online, ...

thats about it I think

oh and:

pytube media converter

it's not in the repo's, check my signature for it.

What is Compiz? I see lots of threads about it. I get the impression its just some fancy desktop effects or something.

Anyway...nice list, I'll need to start capturing this stuff down. ;)

---

### Post by swoll1980 on 2008-06-03
> **KingTermite said:**
> I've heard people talk about Virtual Box and other talk about VMWare (which I've used on Windows).

Are they basically the same thing and if so are there any major advantages of one over the other?

imo virtualbox is at least 2x better than vmware. From my experiences I would say it loads faster, runs faster, and is just more polished over all.
I've also seen various benchmark test that confirm this (although I'm sure theres others that don't) Running a vm in windows is so slow you will be amazed at the difference once you run one under Linux.

---

### Post by klange on 2008-06-03
> **KingTermite said:**
> What is Compiz? I see lots of threads about it. I get the impression its just some fancy desktop effects or something.

Anyway...nice list, I'll need to start capturing this stuff down. ;)
*cries a little inside*

Anyone who has ever used Linux in the past year and doesn't know what [Compiz](http://www.compiz-fusion.org/) is needs to pay more attention. And it's way more than just fancy effects, I couldn't live with a normal window manager after having used Compiz for the past year.

---

### Post by KingTermite on 2008-06-03
> **swoll1980 said:**
> imo virtualbox is at least 2x better than vmware. From my experiences I would say it loads faster, runs faster, and is just more polished over all.
I've also seen various benchmark test that confirm this (although I'm sure theres others that don't) Running a vm in windows is so slow you will be amazed at the difference once you run one under Linux.

I'll need to give it a look then.

I've used VMWare on Windows as I've said. I've had mixed results with it. First time I played with it, it worked great (albeit slow....which was to be expected). Second time I tried it, I couldn't get it to work. Worked with support engineer through about 10+ emails and still never had any success.

---

### Post by RiceMonster on 2008-06-03
I agree with compiz. I don't use it anymore because while I think it's cool, it gets tiring, it messes with my fullscreen apps, and it uses up too much resources. However, for newbies, it's pretty much the coolest thing around and it's a great way of showing your linux box to windows users.

Also,
ubuntu-restricted-extras - That will get all the codecs working.

---

### Post by karellen on 2008-06-03
audacious/amarok/exaile/banshee - for audio files
vlc media player - for videos
deluge/ktorrent - for torrent downloading
openoffice/abiword (if all you do is write) - for office stuff
pidgin/digsby - for instant messaging

---

### Post by cardinals_fan on 2008-06-03
> **billgoldberg said:**
> those aren't "must have" programs by a long shot.

Suggesting difficult to use programs like conky to new users -> no
koffice on gnome? -> no
tiling wm's -> no no no no
and a calculator -> again no
I specifically say that dwm is probably **not** for new users.  I probably shouldn't have put it on there, but oh well.  

Not everyone on these forums uses GNOME, and I find Koffice to be **much** better than OpenOffice.

I challenge the belief that new users can't handle editing a text file.  I started messing around with Conky during my first week with Linux, and it has always been an excellent experience.  Writeups such as [yours]("http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/") make the process easier for beginners.

If you actually try Qalculate, you'll see that it is much more than a calculator.  It can handle everything from ```
2+2
``` to```
integrate(x*sq(x*exp(4*y)*z))+exp(sqrt(y*diff(x ,x ,1)))
``` to listing elements off the periodic table.

With that out of the way, I have another couple apps for the list:

**RealPlayer**
Everyone has their favorite media players, but I really like Real.  The new Linux version has Windows Media support and works well.
Get it at [http://www.real.com/linux](http://www.real.com/linux)

**NoScript**
If you use Firefox, this extension is a must-have.  It enhances security and blocks junk.
Available [here](https://addons.mozilla.org/en-US/firefox/addon/722)
  > Note: If you use Opera (which I recommend) the userscript [here]("http://files.myopera.com/shoust/files/noscriptunblockmode.js") provides much of NoScript's functionality.  The script is discussed [here]("http://my.opera.com/community/forums/topic.dml?id=205858").

**Adblock Plus**
This Firefox extension does just what its name suggests - block ads.  And it does its job well.
Get it [here]("https://addons.mozilla.org/en-US/firefox/addon/1865").
> Opera users: don't feel left out!  The tips [here]("http://www.pcreview.co.uk/forums/thread-3436568.php") add the same functionality to Opera.

I know that browser extensions aren't apps in and of themselves, but since most people these days spend so much time in their web browser, they can make a huge difference.

---

### Post by chucky chuckaluck on 2008-06-03
newbs need idiot proof apps while they're learning. k3b and amarok, while not gnome apps, are pretty idiot proof and have less little oddball quirks than their gnome counterparts (and imltho, they're better too). or, they could try something like cplay, a terminal app that is similar to mpd but without the occasionally nightmarish configurations. vlc is a good choice as it is more likely a newb coming from windows might have used it before. and, firefox and thunderbird are even more likely to have been used by someone more familiar with windows. xmms, and it's similarity to winamp, for the same reason.

---

### Post by KingTermite on 2008-06-03
> **cardinals_fan said:**
> I challenge the belief that new users can't handle editing a text file.  I started messing around with Conky during my first week with Linux, and it has always been an excellent experience.  Writeups such as [yours]("http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/") make the process easier for beginners.

I would completely agree and ask people not to hold back on a program because its not a "beginner level" program. Feel free to mention it is not, but that's not reason not to suggest it.

I'm a prime example of a newbie to Linux, but have been bopping around in the technical side of computers for nearly 20 years. I can muddle through even much of the technical things for Linux. 

My main liability right now is just not having the experience to know what "great apps" exist (hence this thread) and my knowledge of the available commands are still somewhat lacking.

But I can edit a config file to change something...or even likely change code and recompile if necessary. I am a software developer with a bachelor and masters degree in Computer Engineering. So....realize that newbie doesn't mean computer newbie who's only experience is AOL.

---

### Post by KingTermite on 2008-06-03
> **chucky chuckaluck said:**
> newbs need idiot proof apps while they're learning.I respectfully disagree (see my previous post).

I realize some newbie's aren't that tech savvy and need that, but that's an assumption that doesn't hold true for all Linux newbie's.

I personally have enjoyed the few times something didn't quite work right for me....it gave me the opportunity to learn how to fix it and usually taught me some new command line tools.

---

### Post by smartboyathome on 2008-06-03
> **chucky chuckaluck said:**
> xmms, and it's similarity to winamp, for the same reason.

XMMS is not developed anymore, so it should not be recommended anymore. Instead, new users should try Audacious or one of the numerous XMMS2 frontends.

---

### Post by aktiwers on 2008-06-03
> **smartboyathome said:**
> XMMS is not developed anymore, so it should not be recommended anymore. Instead, new users should try Audacious or one of the numerous XMMS2 frontends.

XMMS is still more light IMO. 
Though on Hardy you would need to install from source.

---

### Post by Tomatz on 2008-06-03
> **cardinals_fan said:**
> Opera
Fast and powerful web browser
Get the stable version [here]("http://www.opera.com/download/index.dml?platform=linux"), the new beta (which is strongly recommended) [here]("http://www.opera.com/download/index.dml?platform=linux&ver=9.50b2")

Conky
Monitoring tool for your desktop
In the repos, read [this huge thread]("http://ubuntuforums.org/showthread.php?t=281865") for tips

Qalculate
An extraordinarily powerful calculator
In the repos, use the [gtk version]("http://packages.ubuntu.com/hardy/qalculate-gtk") if running GNOME

Koffice
A great office suite
If you're running KDE, or have disk space to burn, it's in the repos

dwm
OK, it might not be for the total newbies (unless they're willing to climb a vertical learning curve).  But this tiling wm is unbelievably fast and powerful
Download the source from [here]("http://www.suckless.org/wiki/dwm/").  There's no point to a package, because all configuration is done through the source code.


DWM?

Are you a fan of the movie "war games"?

:lolflag:

---

### Post by Tomatz on 2008-06-03
**Songbird** is a nice media player.

Get it [HERE]("http://www.getdeb.net/") (along with some other nice apps)

---

### Post by amingv on 2008-06-03
```
sudo apt-get install checkinstall
```
This application will make packages installed from source known to the package manager and you can also use it to make debs. Trust me, it will save you sooo many headaches. (Just change "sudo make install" for "sudo checkinstall" as the last step.)

```
sudo apt-get install alien
```
This one helps you when you need to install a package from a distro with a different package manager (Slackware's tgz, Red Hat's rpm, etc) that it's not otherwise available for Ubuntu/Debian.

---

### Post by Matthew Wiebelhaus on 2008-06-03
If you need a easy 2d Modeling program for linux you can you QCad or SagCad I use them both and they are great. <Pretty much if you do engineering.

---

### Post by gameryoshi600 on 2008-06-03
app name: K3b
brief description: burns CDs and DVDs, rips dvds and cds
where you can get it: [http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/](http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/)
read that guide it will teach you how to get media (medibuntu) repo also teachs how to install other cool apps that i recommend

---

### Post by Tomatz on 2008-06-03
> **KingTermite said:**
> What is Compiz? I see lots of threads about it. I get the impression its just some fancy desktop effects or something.

Anyway...nice list, I'll need to start capturing this stuff down. ;)

Shortly after you installed your system if you enabled restricted drivers for your (newish) gpu, chances are compiz is enabled.

In a terminal type:

```
sudo apt-get install compizconfig-settings-manager

```

Then go to ***System, preferences, advanced desktop effect settings*** to enable your "cube" etc and have a tinker ;)

Here is a video:

[http://www.youtube.com/watch?v=_ImW0-MgR8I](http://www.youtube.com/watch?v=_ImW0-MgR8I)

---

### Post by KingTermite on 2008-06-03
> **Matthew Wiebelhaus said:**
> If you need a easy 2d Modeling program for linux you can you QCad or SagCad I use them both and they are great. <Pretty much if you do engineering.

You mean mechanical engineering. I do engineering, but not modeling. I'm a software engineer. :p

---

### Post by cardinals_fan on 2008-06-03
> **Tomatz said:**
> DWM?

Are you a fan of the movie "war games"?

:lolflag:
DWM (all caps) refers to Microsoft's Desktop Window Manager.  dwm (no caps) refers to the dynamic window manager, related to wmii.  It's an awesome tiling wm.  See [http://www.suckless.org/wiki/dwm/](http://www.suckless.org/wiki/dwm/)

---

### Post by wootah on 2008-06-03
**Amarok**:
Great music player (Usually used in KDE, but works with GNOME after installing all of the libraries/dependencies that Synaptic handles anyways:)) Available in the repos.

**OpenSSH **(openssh-client, openssh-server):
Secure remote login. It would be a great read for new users in to learning the console and how to remotely use their Linux machine (terminal based). Available in the repos.

**bmon**:
Console based bandwidth monitor. Great little app :)

**filezilla**:
Open Source FTP client available for pretty much all major platforms. Available in the repos.

**firestarter**:
GUI based utility for configuring your firewall. This would provide a good intro into learning about iptables. Available in the repos.

**vlc**:
Multi format video/music player with the capabilities for skinning (oOoOOo shinnnnnnyyyyy) and media streaming. Available in the repos.

**kopete**:
Multi protocol messaging client (for KDE, works in GNOME too). Available in the repos.

**azureus**:
A bit-torrent client based in Java (So you will need the Sun JRE (Java Runtime Environment) installed as well). Available in the repos.

**easytag**:
MP3 IDE3 tagging software (change the mp3 information such as artist, track number, etc). Available in the repos.

**htop**:
Is a scrollable, colour coded, terminal based process viewer (similar to top) with many additional features. Available in the repos.

**gkrellm**:
A GUI based, highly configurable system monitor (similar to conky, but less configurable and not text based). Available in the repos.

**frostwire**:
A Java based p2p network client. I don't think this one is available in the repos? You can download the latest version for Ubuntu from [www.frostwire.com]("http://ubuntuforums.org/www.frostwire.com")

Obviously, not all of these programs are noobie designed or even noobie friendly, but they do present some interesting topics that may strike some curiosity into their users :)

---

### Post by gn2 on 2008-06-03
One that hasn't been mentioned yet is digiKam which is an excellent photo managing and editing application.

I don't like KDE, but I do like the K apps, fortunately they work perfectly in Ubuntu and Xubuntu. K3b and Amarok are both outstanding.

---

### Post by wootah on 2008-06-04
> **gn2 said:**
> One that hasn't been mentioned yet is digiKam which is an excellent photo managing and editing application.

I don't like KDE, but I do like the K apps, fortunately they work perfectly in Ubuntu and Xubuntu. K3b and Amarok are both outstanding.

Yes, K3b is an excellent program--I just wish it didn't look so 2001 :(

---

### Post by karellen on 2008-06-04
> **wootah said:**
> Yes, K3b is an excellent program--I just wish it didn't look so 2001 :(

K3b doesn't look that bad, it nicely integrated into KDE application style

---

### Post by SomeGuyDude on 2008-06-04
> **billgoldberg said:**
> Either from the ubuntu or medibuntu reop:

vlc media player
p7zip-full / adds rar, zip, 7z, ... support to archive manager
compiz fusion manager
exaile /decent music player
adobe reader
frostwire /free limewire pro spinoff
emesene /IM client for msn
"ubuntu-restricted-extras" /install flash, mp3 support, ...
"non-free-codecs" /some win32 codecs, divx, ...
"libdvdcss" /dvd support
"sun-java6-jre"/ java (remove "open-java" first
firefox totem plugin /use it to watch windows media files online, ...

thats about it I think

oh and:

pytube media converter

it's not in the repo's, check my signature for it.

I just installed a few of these, particularly the last five. AWESOME stuff, thank ya.

EDIT: "non-free-codecs" doesn't exist and I can't seem to find libdvdcss either.

---

### Post by jariku on 2008-06-04
> **SomeGuyDude said:**
> "non-free-codecs" doesn't exist and I can't seem to find libdvdcss either.

As billgoldberg wrote, they're part of the medibuntu repo.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by klange on 2008-06-04
> **billgoldberg said:**
> "sun-java6-jre"/ java (remove "open-java" first

*Why?*
OpenJDK is entirely feature complete and has been for a few months. Hell, if you read the FAQs you'll find that it's actually replacing most of the standard commercial Java libraries. Tell me, why would you suggest replacing it? And much less with Java 6?

---

### Post by wootah on 2008-06-04
> **WindowsSucks said:**
> *Why?*
OpenJDK is entirely feature complete and has been for a few months. Hell, if you read the FAQs you'll find that it's actually replacing most of the standard commercial Java libraries. Tell me, why would you suggest replacing it? And much less with Java 6?

:O What's this OpenJDK you speak of?

---

### Post by klange on 2008-06-04
> **wootah said:**
> :O What's this OpenJDK you speak of?

OpenJDK is Sun's effort to release an entire Java runtime under GPL - and they succeeded. There was a news article a few weeks back about the last set of libraries that needed to be rewritten. I don't know if the OpenJDK community or Sun finished them yet, but they were relatively unimportant parts regardless. OpenJDK is the default Java environment installed by Ubuntu. If you had Java on a previous install and upgraded, it was replaced with OpenJDK. The commercial ones are still available from the repos, but what's the point? The only benefit is you can get commercial support from Sun - whoopty fricken' do. The OpenJDK libraries are not only morally better, I've seen nothing but highly improved performance from them (and AWT apps actually look better since the switch! Plus they don't spew X errors any more).

[More literature.](http://openjdk.java.net/)

---

### Post by nick_h on 2008-06-04
**xchat-gnome**
IRC client
In the repositories

---

### Post by wootah on 2008-06-05
> **WindowsSucks said:**
> OpenJDK is Sun's effort to release an entire Java runtime under GPL - and they succeeded. There was a news article a few weeks back about the last set of libraries that needed to be rewritten. I don't know if the OpenJDK community or Sun finished them yet, but they were relatively unimportant parts regardless. OpenJDK is the default Java environment installed by Ubuntu. If you had Java on a previous install and upgraded, it was replaced with OpenJDK. The commercial ones are still available from the repos, but what's the point? The only benefit is you can get commercial support from Sun - whoopty fricken' do. The OpenJDK libraries are not only morally better, I've seen nothing but highly improved performance from them (and AWT apps actually look better since the switch! Plus they don't spew X errors any more).

[More literature.]("http://openjdk.java.net/")

Wow thanks for the insight! I had no clue about this :) Very useful indeed!

---

### Post by danbuter on 2008-06-05
My list:

build-essential - useful for installing some packages and essential if you program C or C++
libdvdcss2 - if you actually want to watch a DVD movie
flashplugin-nonfree - to watch flash movies
chkrootkit - protect your system
msttcorefonts or ttf-liberation - for decent fonts
Abiword 2.6.3 - smaller word program
Gnumeric - smaller spreadsheet program
gedit-plugins - extra stuff for gedit/text editor

Also:
DELETE 
tracker
Open Office
Evolution

---

### Post by woztron on 2008-06-06
> **chucky chuckaluck said:**
> newbs need idiot proof apps while they're learning. 

How many linux n00bs are considered computer n00bs?  By far the majority are those who know enough to reinstall an operating system and are making a choice.  

A computer n00b wouldn't realise there is a choice other than what came on their box.  They need bullet-proof.

The average linux n00b can handle detailed CLI instructions (maybe not vi but nano is easy enough).  I'm still a n00b and managed to install ubuntu server and configure it as a lamp server through an ssh terminal, and i have no computer training, just my windows tinkering.

---

### Post by Lord Xeb on 2008-06-06
So far I have found the following rather helpful:

gnome-lokkit: A small, lite program which asks you about 10 questions and sets up a firewall based on those questions (far easier than firestarter, but not as powerful or customizable, but it gets the job done)

Where: In the repos, just search for lokkit or gnome-lokkit


AWN: A Mac-like docking station (you now what I am talking about) which can be customized to your style.

AWN Manager: Allows you to manage AWN

Where: repos


KolourPaint: A graphics modifier (like MS Paint, just on *nix)

Where: repos


Ubuntu Tweak: Allows you to tweak and modify different areas of Ubuntu. Rather dandy to say the least

Where: ubuntu-tweak.com


GIMP: A graphics program for modifying pictures and things. Kind of like Photoshop, but more a little more harder to use and but just fiddle with it and you will get the hang of it in no time.

Where: repos


bsc: A program that is able to display two locations at once for easy copying and moving of files. (rather handy)

Where: repos


Start-up Manager: Like the name implies, allows you to manage start-up items. 

Where: repos




All of these I have found handy and use them from time-to-time and most are easy to use and idiot proof (except maybe start-up manager).

---

### Post by Bigtime_Scrub on 2008-06-06
Having all the codecs and non free plugins is a must for any user new or not. Media won't work without it so it is essential.

To me, amaroK is a must. I've found gtkpod acts up and is not realiable. I hate having to reload my iPod everytime gtkpod decides to goof up. amaroK may be bloated but it works. 

VLC - It is the best video player I've found in linux.

I would also recommend the K enviorment over Gnome for new users. For one reason and one reason only. When you hover the mouse cursor over something it gives a brief description of what the thing you are pointing at does. Gnome does not have this and neither does Xfce (even though I use and love xfce). It also comes with amaroK!

---

### Post by metalhead8816 on 2008-06-06
I would definitely second these:

DELUGE

XCHAT

Limewire

All are great at downloading programs.

---

### Post by Tomatz on 2008-06-06
> **metalhead8816 said:**
> I would definitely second these:

DELUGE

XCHAT

Limewire

All are great at downloading programs.

Frostwire is better. Its just like limewire pro but free ;)

[http://www.frostwire.com/](http://www.frostwire.com/)

---

### Post by jalvarez53 on 2008-06-06
> **mmb1 said:**
> "Must Have" is subjective to the user's needs, but here's my list

gtkpod:  ipod management
Mirage:  image viewer
thunar:  file manager
vlc:     cross-platform video player.

I had to have vlc on windows but haven't found a need for it yet in 8.04

---

### Post by billgoldberg on 2008-06-06
> **Bigtime_Scrub said:**
> Having all the codecs and non free plugins is a must for any user new or not. Media won't work without it so it is essential.

To me, amaroK is a must. I've found gtkpod acts up and is not realiable. I hate having to reload my iPod everytime gtkpod decides to goof up. amaroK may be bloated but it works. 

VLC - It is the best video player I've found in linux.

I would also recommend the K enviorment over Gnome for new users. For one reason and one reason only. When you hover the mouse cursor over something it gives a brief description of what the thing you are pointing at does. Gnome does not have this and neither does Xfce (even though I use and love xfce). It also comes with amaroK!

What are you talking about?

Gnome does have that. I just checked to make sure.

Amarok is **seriously** over rated.

I prefer bmpx, exaile or even rhytmbox on gnome. On kde it comes out better.

---

### Post by billgoldberg on 2008-06-06
> **Tomatz said:**
> Frostwire is better. Its just like limewire pro but free ;)

[http://www.frostwire.com/](http://www.frostwire.com/)

Add nicotine plus to that list.

---

### Post by bufsabre666 on 2008-06-06
> **billgoldberg said:**
> Amarok is **seriously** over rated.

I prefer bmpx, exaile or even rhytmbox on gnome. On kde it comes out better.

atleast im not the only one who thinks so, although i prefer banshee

---

### Post by JurB on 2008-06-06
"And now for something completely different": [Glipper]("http://glipper.sourceforge.net/")
A super handy clipboard manager applet, can't live without it.

---

### Post by pt123 on 2008-06-06
Sometime back Amarok used to be so far ahead of the music players/organisers on Linux, but now the others have reduced the gap. 

Zim Desktop Wiki is a great tool for a beginner you can organise your Linux notes as you learn. 

I wish there was something like that in Windows (@work).

---

### Post by graabein on 2008-06-06
**Quod Libet** and **Ex Falso** for playing music and tagging music files. Very nice album list view and plugins for getting cover art easily. 

[Awn]("https://launchpad.net/awn") launcher menu for some extra bling.

**Deluge** for BitTorrent. 

**VLC** for videos.

Check out **Inkscape** for drawing and vector graphics. Nice program.

---

### Post by wootah on 2008-06-06
Personally, I would like something a little more light weight than azureus, but still provides similar features.

What are most the popular/best BitTorrent clients for Linux? I still really love uTorrent and have used nothing but that on Windows, but I just don't think it's worth it to use it through Wine. It may be easy to setup through Wine and *blah blah blah*, but there has to be something that is exactly as good/perhaps better to use natively fpr Linux and is fast (startup/running) like uTorrent.

---

### Post by DM was on fire! on 2008-06-06
wootah - A lot of people use KTorrent. ^^

Programs that are needed:

- Murrina theme engine
- Clearlooks theme engine
- Compiz Fusion/Beryl
- WINE. WINE. WINE. **WINE!**
- XMMS 
- MPlayer
- RealPlayer 10
- Tango Icon Generator
- gFTP
- Epiphany

Too lazy to link.
Google them.

---

### Post by cardinals_fan on 2008-06-06
> **DM was on fire! said:**
> wootah - A lot of people use KTorrent. ^^

Programs that are needed:

- Murrina theme engine
- Clearlooks theme engine
- Compiz Fusion/Beryl
- WINE. WINE. WINE. **WINE!**
- XMMS 
- MPlayer
- R**ealPlayer 10**
- Tango Icon Generator
- gFTP
- Epiphany

Too lazy to link.
Google them.
Use RealPlayer 11.  It has Windows Media support.

---

### Post by KingTermite on 2008-06-06
A number of you have suggested RealPlayer. Is that really good? I stopped using it in Windows years ago because it had turned in to such bloatware and was very spammy.

Is it not so in Linux?

---

### Post by wootah on 2008-06-06
> **KingTermite said:**
> A number of you have suggested RealPlayer. Is that really good? I stopped using it in Windows years ago because it had turned in to such bloatware and was very spammy.

Is it not so in Linux?

Exact same reason for me too :(

---

### Post by cardinals_fan on 2008-06-06
> **KingTermite said:**
> A number of you have suggested RealPlayer. Is that really good? I stopped using it in Windows years ago because it had turned in to such bloatware and was very spammy.

Is it not so in Linux?
It's better in Linux.  It also neatly avoids the bad, ugly, vicious, sadistic, etc. codec packages.

---

### Post by Tomatz on 2008-06-06
> **KingTermite said:**
> A number of you have suggested RealPlayer. Is that really good? I stopped using it in Windows years ago because it had turned in to such bloatware and was very spammy.

Is it not so in Linux?

Real player 10 linux isn't, Its really light.

I havent tested 11 so i couldn't say.

---

### Post by KingTermite on 2008-06-06
> **Tomatz said:**
> Real player 10 linux isn't, Its really light.

I havent tested 11 so i couldn't say.
Good to know....thanks for the clarification.

---

### Post by Tomatz on 2008-06-06
> **KingTermite said:**
> Good to know....thanks for the clarification.

np :)

---

### Post by Christmas on 2008-06-06
You can also try [this]("http://vivapinkfloyd.blogspot.com/2008/05/10-linux-applications.html") list. Some of them are included by default though. For Kubuntu users, I've done [this one]("http://vivapinkfloyd.blogspot.com/2008/05/19-essential-kde-applications-review.html").

---

### Post by klepto on 2008-10-03
basKet note pad/Much like OneNote for Linux
Smplayer/great mplayer gui with a great interface
mozilla-mplayer/firefox & mozilla mplayer interface for playing videos on webpages, works great!!
Sabnzbd+/great web gui for downloading nzbs and accessing newsgroups

---

