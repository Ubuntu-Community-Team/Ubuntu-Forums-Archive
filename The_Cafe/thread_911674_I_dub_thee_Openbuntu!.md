---
title: "I dub thee Openbuntu!"
date: 2008-09-05
forum: The Cafe
---

### Post by elmer_42 on 2008-09-05
I was given a computer by a friend of mine because he thought the motherboard was bad. Turns out it wasn't, and it worked perfectly fine once I installed Linux onto it. It's actually a pretty good machine aside from the RAM, and it runs fairly well with what I'm using now. Over the weekend I'm going to be sprucing it up a little bit more, but today I installed of Ubuntu 8.04.1 and Openbox 3.4.7.2.

Anyway, I did a minimal install today, and named this computer marinerII, named after both the first series of space probes to reach Mars and my main rig. after the Xubuntu install was just a little too heavy for this computer. With Openbox, I find it fitting to call it Openbuntu. Anybody have any recommendations for some light apps to use on this machine? When Chrome comes to Linux I'll be testing it out to see just how light it really is, but does anybody know of some light office applications?

**e:**Added *Current State of Openbuntu*
**e:**Added *Current State of MarinerII*
**e:**if an ISO is ever to be made, it will be made soon. As I said, I'm reinstalling Ubuntu right now. Then I will install the programs I like and follow [this]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html") guide. The ISO will be burnt to a CD and an installation will be made to MarinerII. Assuming all goes well, the ISO will be posted to my File Savr account and a link will be posted here.

[=====Current State of Openbuntu=====]
[LIST]
[*]Used [this guide]("http://psychocats.net/ubuntu/minimal") for a minimum install
[*]Used [Urukrama's guide]("http://urukrama.wordpress.com/openbox-guide/") to compile Openbox
[*]Using AbiWord, Gnumeric, Kazehakase, urxvt (with tabs like [Urukrama's]("http://ubuntuforums.org/showpost.php?p=5718353&postcount=159")), rtorrent, Thunar, irssi, and nano
[*]Looking at nubuntu, fluxbuntu, and other light distros to find more light apps
[*]Will make an install disk with the light apps I can find for future use on any **real** junker boxes I find
[/LIST]
[=====Current State of MarinerII=====]
[LIST]
[*]Specs: 2.53GHz Celeron D, 80GB HD, CD-RW drive, 256MB RAM
[*]Found some RAM I had lying around; sadly it was DDR2
[*]Salvaged 512MB RAM & cheapo nVidia GPU (7300GT?); not sure RAM is same type as existing, may only end up with 512MB RAM rather than 768MB
[/LIST]

---

### Post by zmjjmz on 2008-09-05
Abiword and Gnumeric are pretty light, but if you go all the way you can install siag and pw.

---

### Post by perlluver on 2008-09-05
> **elmer_42 said:**
> I was given a computer by a friend of mine because he thought the motherboard was bad. Turns out it wasn't, and it worked perfectly fine once I installed Linux onto it. It's not amazing or fast by any standard (is there a way to check the CPU speed, RAM, etc?), but it runs fairly well with what I'm using now. Over the weekend I'm going to be sprucing it up a little bit more, but today I installed of Ubuntu 8.04.1 and Openbox 3.4.7.2. Right now I'm using Firefox, but I'm going to look into Dillo and Epiphany more as time passes.

Anyway, I did a minimal install today after the Xubuntu install was just a little too heavy for this computer. With Openbox, I find it fitting to call it Openbuntu. Anybody have any recommendations for some light apps to use on this machine? When Chrome comes to Linux I'll be testing it out to see just how light it really is, but does anybody know of some light office applications?

Abiword is a pretty light word processor.  You can run in a terminal, lspci, to find out some of the stuff in it.  For example motherboard, and what not.  As for memory, maybe top, will show how much it has.

---

### Post by dizee on 2008-09-05
for light office apps, you should have a look at abiword (word processing) and gnumeric (spreadsheets).

---

### Post by elmer_42 on 2008-09-05
```
sudo apt-get install abiword gnumeric
```
I use AbiWord a lot on my main machine, because it is much lighter than OpenOffice, and I used Gnumeric a year or so ago when I got a **real** junker (700MHz yay). Thanks for reminding me about Gnumeric!

And now I am a happy man. Any other suggestions for a good light app or a way to check my system stats would be greatly appreciated.

I know it has 256MB of RAM because that's what it said on the stick last night when I opened it up just to look around, but I'm really wondering what CPU it has. It says "Celeron D" on the front, and has the old "Intel Inside" thing with the blue circle and whatnot, but that's the extent of my knowledge.

---

### Post by dizee on 2008-09-05
well, you can get cpu info by typing 
```
cat /proc/cpuinfo
```
into a terminal.

---

### Post by elmer_42 on 2008-09-05
Thanks, dizee. Apparently it's 2.53GHz. Pretty good, no?

---

### Post by dizee on 2008-09-05
yeah. depends on the cpu type of course (probably an early P4 (?) which is not a great processor) but should do everything the average user needs with ease.

---

### Post by elmer_42 on 2008-09-05
It's got this sticker on the front:
[IMG]http://www.physorg.com/newman/gfx/news/2004/IntelCeleronD.jpg[/IMG]

Nothing too good, but will work for what this is. I may end up buying another HD and making this a FreeNAS box.

---

### Post by dizee on 2008-09-05
right, you said that already and i forgot, sorry.

so yeah, a celeron 2.5 ghz... not great, but still, it should be more than usable.

---

### Post by teet on 2008-09-05
Buy a stick of 512 mb of RAM off ebay and you'll be in business (should probably be able to get it for < $15 with shipping).  You could run full ubuntu with ease and not mess with all that "light crap".  Also, you might want to consider upgrading your video card if possible...could make a world of difference.

BTW, I'm running a Celeron D 3.06 ghz, 1 gb ram, 256 mb AGP 8x Nvidia video card.  It was a super cheap machine when I built it a couple years ago but still serves me very well.

-teet

---

### Post by teet on 2008-09-05
double post

---

### Post by gletob on 2008-09-06
Wow the celeron D is in my desktop and thanks to you making me think about it wikipedia lists it as 64 bit and my gentoo 64 cd works so I never would have known.  BTW mines a 2.93 Ghz with 512 ram and intel 865 graphics and it works great with compiz on.

---

### Post by Canis familiaris on 2008-09-06
Opera would a very good browser in this configuration. It is reasonably light and has lots of features. However the fact that it is closed-source will not make it cut-it
for an Open Source DIstribution. :(

---

### Post by myusername on 2008-09-06
this is my list of good light weight apps (however i just use my browser for email but i have heard good things about sylpheed-claws)

leafpad - text editor
Kazehakase - web browser
xfce4-terminal - terminal emulator
quod libet music player
totem-xine - video player
sylpheed-claws - mail app
abiword and gnumeric - office apps

---

### Post by meborc on 2008-09-06
you might be interested in checking out [crunchbang linux]("http://crunchbang.org/projects/linux/"), which is ubuntu+openbox

to find light programs, see what fluxbuntu, nubuntu, xubuntu etc are using... they have already done the job of selecting the lightest of the light

---

### Post by billgoldberg on 2008-09-06
> **Anurag_panda said:**
> Opera would a very good browser in this configuration. It is reasonably light and has lots of features. However the fact that it is closed-source will not make it cut-it
for an Open Source DIstribution. :(

Opera isn't light weight by any definition off the word.

---

### Post by K.Mandla on 2008-09-06
And I have to say it: A 2.53Ghz machine is by no means slow.

But aside from that, if you really want to trim the excess from your system, may I humbly offer [this]("http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/") as a suggestion. 

Beyond that there are plenty of lighter software titles that will make your system seem faster. A lot of the speed of a machine can be won back by lightening the load on the post-installation side ... which is to say, picking lightweight but effective applications makes a bigger difference than tweaking one minor setting somewhere in Ubuntu's core. 

Just some ideas, anyway. ;)

---

### Post by elmer_42 on 2008-09-06
Crunchbang. Huh. Interesting. Anyway, I think this machine will be faster once I get some RAM for it. I have a whole gigabyte or RAM lying around somewhere, but I can't remember if it's DDR (which will work) or DDR2 (which will not). If and when I can find it, I'm sure there will be no problem running almost anything. However, out of pure curiosity I want to see how far I can take this. I may even go past the joke of it being a "distribution" and make an install CD with all the packages, just so I can use a single CD to setup any **real** junk boxes I get.

Thanks go to meborc and myusername for suggesting a place to find good light apps and suggesting a few good light apps. I'd test them out right now, but I'm getting ready to work and the machine is off.

---

### Post by snowpine on 2008-09-06
Definitely check out Crunchbang. It is Ubuntu 8.04 Minimal Install + Openbox + Apps + a very well configured interface. It runs like a dream on 256mb using the full-featured apps we all know and love like Firefox and Openoffice. There's also a "Lite" version available if you prefer to choose your own suite of applications. Why reinvent the wheel? :)

I am also a big fan of Fluxbuntu for those who prefer lightweight apps. It comes with Claws, Kazekahase, Rox-Filer, Xmms, etc.

What I did when I was testing this stuff out is to install Virtualbox on my desktop (which has plenty of ram), then create different virtual machines with 64, 96, 128, 256mb of ram. You will learn a lot by trying different distros on these virtual machines, and your experiments will be quicker since you won't be dealing with slow read/write times on ancient hard drives and CD-Roms. 

Good luck!

---

### Post by Canis familiaris on 2008-09-06
> **billgoldberg said:**
> Opera isn't light weight by any definition off the word.

It is. ;)
Use it to believe it.

---

### Post by myusername on 2008-09-06
o...and pcmanfm for filemanager 
it's very lightweight and can set background images and has icon support for your desktop
have a look here   [http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)  (the new version isnt in the repos)

---

### Post by myusername on 2008-09-06
> **Anurag_panda said:**
> It is. ;)
Use it to believe it.

no it's only lightweight compared to firefox (but only a little)
use a real lightweight browser like the one i suggested and you'll see what the true meaning of lightweight is

---

### Post by dizee on 2008-09-06
opera isn't light in terms of the ram usage it reports but it is actually really snappy on modest machines. it does well for me on a pentium II with 92 MB of ram, particularly if you turn off "turbo mode" in the options.

---

### Post by Anzan on 2008-09-06
Crunchbang is very good. I recommend it as well.

---

### Post by Bart_D on 2008-09-06
Opera feels really fast for me on both Windows and also did so on Ubuntu Fiesty.  No complaints there.

---

### Post by Dr Small on 2008-09-06
Are you making a new distro called Openbuntu or meerly asking for what you should put on your machine? I've been looking for a Openbox distro (by default) and Openbuntu sounds apeasing :)

---

### Post by Pro-reason on 2008-09-06
For *really* light word-processing, use [LaTeX]("http://en.wikipedia.org/wiki/LaTeX") in gedit.

---

### Post by Canis familiaris on 2008-09-06
> **myusername said:**
> no it's only lightweight compared to firefox (but only a little)
use a real lightweight browser like the one i suggested and you'll see what the true meaning of lightweight is

Maybe Yes. But Opera has the best features per requirements value as compared to any other browser.
So maybe not lightweight but has the best ratio of features per unit requirement.

---

### Post by myusername on 2008-09-06
now thats a true statement ^^

---

### Post by chucky chuckaluck on 2008-09-06
cplay is lighter than quodlibet and runs in a terminal

why not just use xterm, or urxvt, instead of xfce-terminal?

the graphical version of links2 might be what you need and you can use firefox, or whatever, for the few things that don't work in it.

nano is going to be lighter than leafpad, but not by much.

mc for file management, or thunar.

feh for an image viewer

---

### Post by myusername on 2008-09-06
i like xfce-terminal cause it supports tabs

---

### Post by chucky chuckaluck on 2008-09-06
> **myusername said:**
> i like xfce-terminal cause it supports tabs

mrxvt does as well and is lighter. or, screen is an option, too.

---

### Post by myusername on 2008-09-06
i did not realize that

---

### Post by chucky chuckaluck on 2008-09-06
> **myusername said:**
> i did not realize that

yup, and you can probably find all the .Xdefaults options you want.

---

### Post by myusername on 2008-09-07
cool thanks

---

### Post by chucky chuckaluck on 2008-09-07
> **myusername said:**
> cool thanks

my pleasure.

---

### Post by elmer_42 on 2008-09-07
> **Dr Small said:**
> Are you making a new distro called Openbuntu or meerly asking for what you should put on your machine? I've been looking for a Openbox distro (by default) and Openbuntu sounds apeasing :)
Actually, it was more of a joke that it was a distro, but I'm thinking about making an install disk, so I can use it whenever I run into a low-power machine. However, I may ditch this idea and just download [Crunchbang]("http://crunchbang.org/projects/linux/"), which seems like the same thing. I do like the idea of having a custom install disk, made specially with the apps I like. Does anybody have a good guide on adding packages to a minimal install disk?

Regarding terminals, I'm currently using *urxvt -pe tabbed* as explained by Urukrama [here]("http://ubuntuforums.org/showpost.php?p=5718353&postcount=159").

Thanks go to chucky chuckaluck, not only for having a happier avatar, but for the app suggestions.

---

### Post by hugmenot on 2008-09-07
Google Chrome is a multi-process browser. This means it will use much more memory than a single-process browser like Firefox or Opera.

---

### Post by Bart_D on 2008-09-07
BINGO!  Well said.....

If you're looking for speed, this will be a major obstacle.  I doubt I will ever use Google Chrome.

---

### Post by urukrama on 2008-09-07
> **myusername said:**
> i like xfce-terminal cause it supports tabs

urxvt does too, and in a much nicer way than mrxvt. You'll need the following line in your Xdefaults:

```
URxvt.perl-ext-common:	default,tabbed
```

You can create a new tab with the keyboard by pressing Shift+Down and move through the tabs with Shift+Left/Right.

If you're interested, these are my full urxvt settings:

```
URxvt*font:		xft:DejaVu Sans Mono:size=7:VL Gothic:size=7:antialias=true:hinting=true
URxvt*boldFont: 	xft:DejaVu Sans Mono:size=7:VL Gothic:size=7:antialias=true:bold:hinting=true
URxvt*background:	#08090A
URxvt*foreground:	#4b555e
URxvt*color0:		#08090A
URxvt*color1:		#4b555e
URxvt*color2:		#08090A
URxvt*color3:		#08090A
URxvt*fading:    	10
URxvt*tintColor: 	#FCFCFC
URxvt*shading:    	100
URxvt*inheritPixmap: 	False
URxvt*cursorBlink:      False
URxvt*cutchars:		`'",;@&*=|?()<>[]{}

URxvt*scrollstyle:	plain
URxvt*mouseWheelScrollPage:	False
URxvt*jumpScroll:       False
URxvt*skipScroll:       False
URxvt*scrollBar: 	False
URxvt*scrollTtyOutput:      False
URxvt*secondaryScroll:	  False

URxvt.perl-ext-common:	default,tabbed
URxvt.tabbed.tabbar-fg:         1
URxvt.tabbed.tabbar-bg:         3
URxvt.tabbed.tab-fg:            2
URxvt.tabbed.tab-bg:            1

URxvt*urlLauncher:	opera
URxvt*saveLines::       32767
```

Attached is a screenshot of what the tabs look like. The colours are adjustable (see the Xdefaults settings above).

The only downside to urxvt is that I still have to figure out if I can scroll up and down with my scroll wheel in urxvt.

EDIT: Just saw elmer already mentioned this. Oh well...

---

### Post by chucky chuckaluck on 2008-09-07
> **elmer_42 said:**
> Thanks go to chucky chuckaluck, not only for having a happier avatar, but for the app suggestions.

people told me i should smile more.

---

### Post by elmer_42 on 2008-09-07
> **urukrama said:**
> EDIT: Just saw elmer already mentioned this. Oh well...
Can't to have it mirrored over here, though. Thanks!
> **chucky chuckaluck said:**
> people told me i should smile more.
And I'm glad you do. :)

I'll be doing some things on it over the week, and I'll see how the various apps you guys suggested. Thanks again!

---

### Post by urukrama on 2008-09-08
The [latest Debian Package of the Day blog post]("http://debaday.debian.net/2008/09/07/mrxvt-fast-light-multitabbed-terminal-emulator/") is about mrxvt. It turns out its tabs can look good. You might be interested in it.

---

### Post by johnraff on 2008-09-08
Just a quick mention for [Ubuntulite]("http://ubuntulite.tuxfamily.org/?q=node/5"),
another lightweight system with Openbox (the [LXDE]("http://lxde.org/") package in fact) on Ubuntu. Whether you prefer that or Crunchbang would be a matter of taste I suppose.

---

### Post by Bart_D on 2008-09-08
So what's the status of Openbuntu?

---

### Post by elmer_42 on 2008-09-08
I've used MarinerII a bit today, and I got urxvt configured nicely and with tabs. I'm using nano or (once I [FONT="Courier New"]vimtutor[/FONT]) vim for text editing. I'll be researching and testing cplay, mpd, and mplayer to see which one I want to use. If I need to run a torrent, rtorrent's my choice (I use it occasionally on my main box). I'm checking out Claws, but I think I'll just end up using GMail through Kazehakase.

Right now I'm in the "find what light apps I like" phase, once that's done I'll start Googling how to add packages to a Hardy Minimal Install Disk, and once I do that I'll add the apps I like to a Hardy Minimal Install Disk. If you guys want I'll upload the ISO, but I figure Crunchbang or Ubuntulite would probably be a better way to go, since they are more established. The only use for Openbuntu, really, is for me to have a personalized install disk tailored especially to my needs.

**e:**Oh, I also updated the first post.

---

### Post by dirtylobster on 2008-09-09
zomg crunchbang is so awesome. Installing it on all my computers as we speak. :)

---

### Post by elmer_42 on 2008-09-09
Yeah, I figured people would like Crunchbang better than a shoddily-assembled minimal install disk with added packages.

---

### Post by Bart_D on 2008-09-09
It's ABOUT TIME we had a Ubuntu mini CD + an already setup openbox configuration available at our disposal.  It really helps the newbies(such as myself) who have had trouble with Urukama's Openbox Guide.

---

### Post by snowpine on 2008-09-09
> **Bart_D said:**
> It's ABOUT TIME we had a Ubuntu mini CD + an already setup openbox configuration available at our disposal.  It really helps the newbies(such as myself) who have had trouble with Urukama's Openbox Guide.

Bart, have you checked out LXDE? It's a preconfigured Openbox+various panels and menus that's designed to be really easy to install over a variety of distros (including Ubuntu).

For a total newbie, I would still recommend Crunchbang as an intro to Openbox. One nice thing about Openbox is that everything is stored in a few text files, so you could, for example, copy your /.config/openbox files from an Ubuntu Openbox build to a Debian Openbox build (or any other distro).

---

### Post by snowpine on 2008-09-09
> **elmer_42 said:**
> Yeah, I figured people would like Crunchbang better than a shoddily-assembled minimal install disk with added packages.

Elmer, don't sell yourself short--sometimes it is really fun to "reinvent the wheel" and I bet you learned a lot doing it. I personally learned a lot about lightweight applications by following this thread. Thank you!

---

### Post by elmer_42 on 2008-09-09
> **snowpine said:**
> sometimes it is really fun to "reinvent the wheel"
This is truth, it was a lot of fun. That's another reason I did/am doing it, for fun.
> **snowpine said:**
> I personally learned a lot about lightweight applications by following this thread.
So did I :lol:
> **Bart_D said:**
> It's ABOUT TIME we had a Ubuntu mini CD + an already setup openbox configuration
Don't get too far ahead of yourself, I haven't found a way to add packages to a Mini disk yet. If you need something like that, though, look into Crunchbang and LXDE.

---

### Post by Bart_D on 2008-09-09
> **snowpine said:**
> Bart, have you checked out LXDE? It's a preconfigured Openbox+various panels and menus that's designed to be really easy to install over a variety of distros (including Ubuntu)....

Briefly....but I prefer Openbox.

---

### Post by elmer_42 on 2008-09-09
On [this]("http://lxde.org/about.html") LXDE page, it says that Openbox is included. I don't quite understand why you say that you prefer Openbox when it is, in fact, included in LXDE.

---

### Post by urukrama on 2008-09-09
> **elmer_42 said:**
> On [this]("http://lxde.org/about.html") LXDE page, it says that Openbox is included. I don't quite understand why you say that you prefer Openbox when it is, in fact, included in LXDE.

I prefer plain Openbox, because I don't have any need for all the extras that LXDE comes with.

---

### Post by elmer_42 on 2008-09-09
> **urukrama said:**
> I prefer plain Openbox, because I don't have any need for all the extras that LXDE comes with.
Well that makes sense. Thanks for giving an explanation.

---

### Post by Bart_D on 2008-09-11
> **elmer_42 said:**
> On [this]("http://lxde.org/about.html") LXDE page, it says that Openbox is included. I don't quite understand why you say that you prefer Openbox when it is, in fact, included in LXDE.

I'm just more used to the "pure/plain" openbox look now.

What is the advantage of LXDE (I mean relative to Openbox)?

---

### Post by snowpine on 2008-09-11
> **Bart_D said:**
> I'm just more used to the "pure/plain" openbox look now.

What is the advantage of LXDE (I mean relative to Openbox)?

Personally, I prefer an ultra-minimal Openbox with no panels or anything... just a plain screen (with a nice wallpaper) that I can right-click to get a menu, plus key combos I can press for my favorite apps. I used Crunchbang as my starting point, then did away with all of the panels and launchers. 

LXDE uses Openbox as its windows manager and adds a taskbar, panel, lower-left-corner menu, network monitors, volume control, etc. to create a complete "desktop environment." I would recommend it for someone who's used to, say, Windows or KDE.

Both approaches are perfectly valid, it's just a matter of opinion and personal preference.

---

### Post by elmer_42 on 2008-09-14
Well, I found a box that was fairly nice, but it won't even boot into a LiveCD. Instead of just throwing it away, I took some parts out of it and put them into MarinerII. I'm reinstalling Ubuntu right now, so I don't actually know if the RAM and GPU I put in it are supported, but I sure hope they do.

Also, if an ISO is ever to be made, it will be made soon. As I said, I'm reinstalling Ubuntu right now. Then I will install the following:
[LIST]
[*]AbiWord (Office)
[*]GnuMeric (Office)
[*]Kazehakase (Web browser)
[*]urxvt (Terminal)
[*]rTorrent (Torrent client)
[*]Thunar (File manager)
[*]irssi (IRC client)
[*]nano (Text editor)
[*]cplay (Music player)
[*]feh (Image viewer)
[*]Sylpheed-Claws (Mail client)
[*]Finch (IM client)
[*]PyPanel (Panel)
[/LIST]
Once those are installed, I will follow [this]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html") guide and create an ISO. That will promptly be burnt to a CD, and an attempt at the first install will be made. Assuming all goes well, I will upload it to my File Savr account and link it to you all. I'm hoping everything works out!

---

### Post by Bart_D on 2008-09-14
That's a damn good list!!!  If I was creating a LIVE-CD(Ha Ha Ha!!!) the only 3 apps that I would have chosen NOT to go with, from your list, would be: 
rTorrent - I don't download copious amounts of stuff
Sylpheed Claws (Mail client) - I don't do email on the Ubuntu/Linux/SIR-BREAKS-A-LOT Box.
irssi - is this necessary?

Does feh do wallpaper changing?

---

### Post by elmer_42 on 2008-09-15
Yes, feh can set your wallpaper. This is covered in Urukrama's Openbox Guide. I use torrents occasionally (if I find something good on Jamendo), and irssi *is* a necessary app for me, I like the near-instant response to questions in IRC. I only included a mail application in case I ever needed one, I normally will just use a web browser to access GMail or whatever email service I am using at the time.

---

