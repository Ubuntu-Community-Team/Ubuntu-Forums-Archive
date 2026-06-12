---
title: "What to tweak/remove in Debian/Ubuntu to make 'em fastest/faster"
date: 2008-10-05
forum: The Cafe
---

### Post by Jags_FL on 2008-10-05
I was searching about 'Fastest GNOME Distro' and found many posts (on this & other Linux forums) saying Debian / Ubuntu would be fastest/faster, among GNOME distros, after some tweaks / removing "crap/unwanted stuff". By fastest I mean, quick/improved boot time & highly responsive afterwords.

For a Desktop my usage is pretty basic I guess... Firefox, RSS Reader, Pidgin, GIMP, Open-Office Writer, gedit, VLC Media Player, Brasero, BitTorrent(rarely). Few unwanted things I know already... Evolution, Banshee/Totem, Games etc.


So my questions are:

1, What are those tweaks/settings
2, What are those unwanted packages


Also(unrelated to being fastest), is there such a thing exists / need to be done like tweaking the firewall for max protection or automated/regular cleanup of temp files etc (e.g. CCleaner/Tune-Up Utilities for Windows, not the Firefox cleanup on exit) in Debian/Ubuntu or they have it built-in ? 

Thanks a million in advance, any input is greatly appreciated. -jags


PS: also any comment/suggestion on this thread, please:

[http://ubuntuforums.org/showthread.php?t=938335&goto=firstpost](http://ubuntuforums.org/showthread.php?t=938335&goto=firstpost)

---

### Post by Sealbhach on 2008-10-05
You can remove Tracker, if you feel you don't need to search your computer much.

Also, you could use lighter office software such as Abiword instead of Open Office.

Remove the Orca accessibility stuff, if you're fortunate enough not to need it.

Disable ipv6 in your browser...

there's lots of tweaks out there.

.

---

### Post by init1 on 2008-10-05
Yeah I've researched that too. All the sites I've found say 
1. Remove unnecessary programs
2. Remove some virtual terminals
3. Use light apps
4. Use preload
If you want a faster system, I'd use fluxbox or an other WM instead of Gnome in a minimal install of Debian or Ubuntu. I would also install preload
```

sudo apt-get install preload

```

As for firewall/clean up, I don't think you need to worry about either of those in Linux.

---

### Post by steeleyuk on 2008-10-05
Install the [preload]("apt://preload") package.

> adaptive readahead daemon
preload monitors applications that users run, and by analyzing this
data, predicts what applications users might run, and fetches those
binaries and their dependencies into memory for faster startup times.

Note that installing preload will not make your system boot faster
and that preload is a daemon that runs with root priviledges.

Sorry, init beat me :)

---

### Post by Jags_FL on 2008-10-05
[B]Sealbhach, init1 and steeleyuk


You guys are lightning fasst [/B] :)   

I mean really, even before I can ask "What's Preload, 'steeleyuk' answered it already...  


The reason I prefer GNOME is, I find it simple and very friendly.


A quick Q: How to remove virtual terminals


I would love to hear more so guys please keep your comments/suggestions coming.


- Many thanks for the replies.

---

### Post by steeleyuk on 2008-10-05
[I have no idea whether this will break anything else though.]("http://ubuntuforums.org/showthread.php?t=433167")

---

### Post by Jags_FL on 2008-10-05
Thanks steeleyuk.

I have spared a Desktop just to test/experiment with Debian Unstable and Ubuntu Dailies so even if they break I can just reinstall 'em back.

---

### Post by LaRoza on 2008-10-05
Remove X and anything that requires it.

---

### Post by jimi_hendrix on 2008-10-05
> **laroza said:**
> remove x and anything that requires it.

lol

---

### Post by LaRoza on 2008-10-05
> **jimi_hendrix said:**
> lol

Why?

It it true. I have used CLI only setups before.

---

### Post by kerry_s on 2008-10-05
> **LaRoza said:**
> Why?

It it true. I have used CLI only setups before.

i agree, start from the command line and add only what you need.

with debian use the net installer, uncheck everything at package selection.

with ubuntu use the alternate installer, select install a command line system.

once you have the base you can make it anything you want. a custom install is the best way to get the most speed.

---

### Post by smartboyathome on 2008-10-05
> **LaRoza said:**
> Why?

It it true. I have used CLI only setups before.

So have I, though these forums can be hard to browse from lynx sometimes. :(

---

### Post by oldos2er on 2008-10-05
"A quick Q: How to remove virtual terminals"

 If you're running such a low-end system that you need to start counting the number of ttys loaded, I'd consider a distro far lighter than Ubuntu, e.g. Arch or Slax. The ttys use a very small amount of RAM.

 Google is your friend in looking up Tips & Tricks on slimming down Ubuntu. And if you haven't already, look at this forum's Tutorials and Tips section.

---

### Post by xArv3nx on 2008-10-05
> **LaRoza said:**
> Why?

It it true. I have used CLI only setups before.
That's the kind of stupidity that kills mass adoption for Linux.

---

### Post by crimesaucer on 2008-10-05
remove gnome
install xfce4


> **Jags_FL said:**
> ".....For a Desktop my usage is pretty basic I guess... Firefox, RSS Reader, Pidgin, GIMP, Open-Office Writer, gedit, VLC Media Player, Brasero, BitTorrent(rarely). Few unwanted things I know already... Evolution, Banshee/Totem, Games etc.....


This already sounds like xfce4, no games, using brassero instead of nautilus, Thunderbird and Firefox instead of Epiphany and Evolution..... add deluge and a very fast Thunar and Mousepad, along with Abiword, use slim instead of gdm.... then you have a very light and fast distro.


Don't get me wrong, I like gnome, but I find Thunar is faster to use than Nautilus, it loads faster, plus it is easier to navigate in, and the Thunar custom actions are pretty cool and simple to use..... almost easier than Nautilus scripts.


I also like gedit, but it loads so much slower than mousepad..... I basically use mousepad if I just need to do a quick edit because it loads lightning fast, but I use gedit if I plan on actually working on something for a while becasue I like the find/replace better.


As for gdm, it is much slower than slim, but slim doesn't have the gui features like gdm does..... slim is basically just a log-in window with a customizable background that loads super quick and can even use your wallpaper for a seamless transition from the log-in window to your desktop wallpaper.

---

### Post by mkrahmeh on 2008-10-05
i got ubuntu installed on my machine, then the KDE installed afterwards, 
i noticed a lot of apps being duplicated, cant find an efficient method for removing these duplicates, assuming it has to be done manually, and i hate the chain reaction of install/remove of the system..

can this affect the system's performance ? of course these duplicated apps are not loaded to the memory all the time..

---

### Post by sertse on 2008-10-05
For what it's worth, (and probably straying from the OP..) CLI only setups doesn't always have to be intimidating. For example try INX ([http://inx.maincontent.net/](http://inx.maincontent.net/)) It's CLI only distro, that is menu driven and user friendly with the aim of teaching more about using the console and how most things you use a computer for can be done from the console. Net, Media etc

By back to the topic, it always found Kmandla's guide to be useful. Covers mosts things. [http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/](http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/)

---

### Post by cardinals_fan on 2008-10-05
> **xArv3nx said:**
> That's the kind of stupidity that kills mass adoption for Linux.
Why?  And how is it stupidity?

---

### Post by Scruffynerf on 2008-10-05
There's a list of things that can speed up a system listed at the Ultimate Edition's HOWTO pages, specifically:
[http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html](http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html)

Note: In the latter parts of the HOWTO, some of the options may break systems, so be careful.

---

### Post by Jags_FL on 2008-10-06
Many, many thanks to all of you. I really appreciated your inputs.

Though I still have to implement few more suggestions, so far I've applied following tweaks (mostly from this link: [http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html](http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html) )  and boot time has improved from 47 to 38 sec and most importantly Intrepid feels faster/responsive than before (and still this one is my experimental desktop with P4 2.5GHz/2GB so I'm sure the results would be alott better on XPS 420 with Intel Q9550/4GB) :



(1) Installed boot chart: sudo apt-get install bootchart

(2) Services Disabled:

(a)System>>Administration>>Services
1, Bluetooth device management
2, Computer activity logger (klogd)
3, Computer activity logger (sysklogd)
4, Hotkeys management (hotkey-setup)
5, Multicast DNS service discovery (avahi-daemon)
6, Power management (acpid)
7, Power management (apmd)

(b) System>>Administration>>Boot-up Manager
1, CUPS
2, rsync
3, laptop mode

(c) sysv-rc-conf
(after installing: sudo apt-get install -y  --force-yes sysv-rc-conf)

Disabled (for runlevel 3,4,5) :
acpid  
apmd 
avahi-dae$ 
bluetooth 
hotkey-se$ 
klogd 

(3) Softwares removed:

1, Evolution
2, totem
3, Rhythmbox

(4) Programs removed from startup:

System>>Preferences>>Sessions
1, Bluetooth Manager 
2, power manager
3, Print Que Applet
4, visual assistance

(5) Tweak for Filesystem EXT3:
added to grub:
defoptions=quiet splash rootflags=data=writeback
altoptions=(recovery mode) single rootflags=data=writeback

updated grub: sudo update-grub

sudo gedit /etc/fstab
Modified Ubuntu fstab enry to: relatime,errors=remount-ro,data=writeback,noatime

sudo tune2fs -o journal_data_writeback /dev/sdb1 

(6) swappiness: sudo gedit /etc/sysctl.conf
added a line: vm.swappiness=0 

(7) Concurrent Booting (this may not have any effect unless the processor is dual core)

sudo gedit /etc/init.d/rc
find : CONCURRENCY=none
changed it to CONCURRENCY=shell

(8 ) Edit GRUB while booting first time and add "profile" at the end of kernel options to improve subsequent boots.

*****

Haven't installed preload, neither have I disabled virtual terminals so far.

---

### Post by K.Mandla on 2008-10-06
> **steeleyuk said:**
> [I have no idea whether this will break anything else though.]("http://ubuntuforums.org/showthread.php?t=433167")
It won't. It's safe for day-to-day setups. 
> **LaRoza said:**
> Why?

It it true. I have used CLI only setups before.
Me too. And they're incredibly fast, and incredibly flexible.
> **smartboyathome said:**
> So have I, though these forums can be hard to browse from lynx sometimes. :(
Try elinks. I use that sometimes because I get tired of all the frills that the pages need just to show a string of thread replies. And it has a "tabbed" interface and a download manager and a bunch of other stuff too.
> **xArv3nx said:**
> That's the kind of stupidity that kills mass adoption for Linux.
Hogwash. The only thing that kills mass adoption of Linux is freedom of choice. And when that is gone, and the command line with it, I and a lot of other people will move on to something else that lets us do what we want with our computers, the way we want. So get past it. The command line isn't killing the spread of Linux. It's the ability to say, "I want to use the command line." 
> **Jags_FL said:**
> Many, many thanks to all of you. I really appreciated your inputs.

Though I still have to implement few more suggestions, so far I've applied following tweaks ...
Haven't installed preload, neither have I disabled virtual terminals so far.
Try readahead too, but remember that after all these tweaks, what's holding your system back is the engorged Gnome desktop (I'm assuming you're using Gnome, if I read your other posts right). 

No joke, that machine will open up as soon as you can bear to get rid of all that bloat. I have a 550Mhz Celeron that boots in a third of the time it's taking yours, and I have all the same style software ... just none of it linked to a heavyweight desktop environment.

Please, I humbly encourage you to take a look at my blog if you want some ideas about *truly* speeding up that machine.

---

### Post by Jags_FL on 2008-10-06
hi  K.Mandla

Many thanks for the reply. In fact, I was reading your Blog while you posted the reply. ( 'sertse' posted this link to your blog earlier: [http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/](http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/) )

From this link, [http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=2](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=2) (via your blog), I tried that 

```
hdparm -c3 -m16 /dev/hdb
```

but I got this error:

:::::
root@ubuntu# hdparm -c3 -m16 /dev/sdb

/dev/sdb:

setting 32-bit IO_support flag to 3
HDIO_SET_32BIT failed: Invalid argument
setting multcount to 16
HDIO_SET_MULTCOUNT failed: Inappropriate ioctl for device
HDIO_GET_MULTCOUNT failed: Inappropriate ioctl for device
IO_support  = 0 (default)
:::::

Anyway, I'm still going through your **'How_to_set_up_Hardy_for_speed' guide** and going to install Readahead and Preload.

Thanks again. - jags

---

### Post by Jags_FL on 2008-10-06
I just installed Preload but Readahead was already there (in Synaptic)... I guess Intrepid installs Readahead by default.

---

### Post by K.Mandla on 2008-10-06
It probably installs it in a full Gnome installation; I should have remembered that before I suggested it. A command-line installation doesn't include it.

Also, let me know if hdparm does anything for you. I've never gotten any kind of speed increase out of it, but I haven't tested it with any and every piece of hardware out there. I don't think anyone can. ;)

---

### Post by Jags_FL on 2008-10-06
Regarding hdparm

as I stated in my [post# 22]("http://ubuntuforums.org/showpost.php?p=5915662&postcount=22"), I wasn't able to do anything with it. I was getting this error:

:::::
root@ubuntu# hdparm -c3 -m16 /dev/sdb

/dev/sdb:

setting 32-bit IO_support flag to 3
HDIO_SET_32BIT failed: Invalid argument
setting multcount to 16
HDIO_SET_MULTCOUNT failed: Inappropriate ioctl for device
HDIO_GET_MULTCOUNT failed: Inappropriate ioctl for device
IO_support = 0 (default)
:::::

---

### Post by K.Mandla on 2008-10-06
I'm afraid I don't have any tips to offer on that front. I've gotten more or less the same degree of nothing out of it. :|

Omigosh! You're signed in as root! :shock: Blasphemer! :biggrin:

---

### Post by kerry_s on 2008-10-07
> **Jags_FL said:**
> Regarding hdparm

as I stated in my [post# 22]("http://ubuntuforums.org/showpost.php?p=5915662&postcount=22"), I wasn't able to do anything with it. I was getting this error:

:::::
root@ubuntu# hdparm -c3 -m16 /dev/sdb

/dev/sdb:

setting 32-bit IO_support flag to 3
HDIO_SET_32BIT failed: Invalid argument
setting multcount to 16
HDIO_SET_MULTCOUNT failed: Inappropriate ioctl for device
HDIO_GET_MULTCOUNT failed: Inappropriate ioctl for device
IO_support = 0 (default)
:::::


hdparm is no good in ubuntu cause they made the switch to scsi drivers for drives. i wouldn't worry about hd speed tweaks in ubuntu, the auto setup is pretty accurate.

---

### Post by cleverselfreferentialname on 2008-10-07
> **K.Mandla said:**
> 
Omigosh! You're signed in as root! :shock: Blasphemer! :biggrin:

Heh, maybe he just sudo -i'd for a second. ;)

[QUOTE=K.Mandla][QUOTE=xArv3nx]
That's the kind of stupidity that kills mass adoption for Linux.[/QUOTE]
Hogwash. The only thing that kills mass adoption of Linux is freedom of choice. And when that is gone, and the command line with it, I and a lot of other people will move on to something else that lets us do what we want with our computers, the way we want. So get past it. The command line isn't killing the spread of Linux. It's the ability to say, "I want to use the command line."[/QUOTE]

Hear, hear!

---

### Post by Jags_FL on 2008-10-07
Thanks for the info 'kerry_s'

---

### Post by Exsecrabilus on 2008-10-07
sudo apt-get remove ubuntu

---

### Post by LaRoza on 2008-10-07
> **xArv3nx said:**
> That's the kind of stupidity that kills mass adoption for Linux.

What? Since when do personal setups kill mass adoption for Linux and why is mass adoption a goal?

Please mind your accusations and language...

---

### Post by mkrahmeh on 2008-10-07
> **xArv3nx said:**
> That's the kind of stupidity that kills mass adoption for Linux.

command line control of the system is what really drew into linux..especially yakuake, it blew my mind :guitar:

---

### Post by Sam Lars on 2008-10-15
Thanks for all the useful info and links here, you could really spend all your time tweaking things with Linux...
I did [a post]("http://ubuntuforums.org/showthread.php?t=820804") a list of softwares that I found to be not very useful, and also some that I did find to be useful.
I might want to update that some based on this and other things I've come across since then...

---

### Post by init1 on 2008-10-15
> **xArv3nx said:**
> That's the kind of stupidity that kills mass adoption for Linux.
Actually, I switched to Linux because of the command line.

---

### Post by sokopok on 2008-10-15
About a year and a half ago I was running an Ubuntu system on a 66MHz 48MB RAM laptop while travelling. Worked like a peach. Installed a commandline system, no tweaks, then added KDE for the PIM suite. I was even using Gimp for minor photo editing (patience needed here ;)), started directly from the console with "startx gimp" (or something similar, bad memory). KMail, and Kopete for communication.
I'd like to hear your reply, Bill! Cheers for Ubuntu!

---

### Post by jgrabham on 2008-10-15
Use Arch - one of the fastest distros around (not to set up of course, but to boot and use it definatly is)

---

### Post by .jeger on 2008-10-15
> **jgrabham said:**
> Use Arch - one of the fastest distros around (not to set up of course, but to boot and use it definatly is)

I tried Arch, but mucked something up while doing the installation. I'll come back to it when I've had some more experience with simpler installs.

---

### Post by sokopok on 2008-10-15
My all time fastest (and definitely most fun) system was a [LFS]("http://www.linuxfromscratch.org/") system. Just about everything compiled specificly for my archirecture, highly optimized. Not for console-fobes though. But this isn't the place to discuss this. Just spreading the word... Great way to get acquinted with the guts of a Linux based system.

---

### Post by Jags_FL on 2008-10-15
@ Sam Lars

Thanks for providing the link : [http://ubuntuforums.org/showthread.php?t=820804](http://ubuntuforums.org/showthread.php?t=820804)

I'm gonna apply removals on my Oct-15 daily installation later tonight.


@ jgrabham

After reading Arch being one of the fastest distro, I tried but couldn't install Arch. I don't remember exactly now, but I was getting some kind 'Pacman' errors while installing GNOME.

---

### Post by Jags_FL on 2008-10-19
@ Sam Lars

After going through your detailed [**removal list**]("http://ubuntuforums.org/showthread.php?t=820804") I wonder what else gets installed by default which most users may not need... like these packages:

- splix : Driver for samsung laser printers
- min12xxw : Driver for KonicaMinolta PagePro

And not including those packages would free up some space on Desktop/Live CD for 1084 KB OpenOffice.org Math, whose absence causes 'Data Corruption':

[**Launchpad Bug# 223476**]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/223476") , [comment# 7]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/223476/comments/7") , [comment# 8]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/223476/comments/8")  


Also I couldn't help but notice that, even after selecting English-US as language/locale/keyboard-origin/keyboard-layout at the start of an installation, these packages get installed by default:

ttf :
ttf-arabeyes         : Arabic fonts
ttf-arphic-uming     : Chinese TTF Mingti style
ttf-indic-fonts-core : Indian language fonts
ttf-kochi-gothic     : Gothic Japanese TTF
ttf-kochi-mincho     : Mincho Japanese TTF
ttf-lao              : TTF for Laon language
ttf-thai-tlwg        : Thai TTF
ttf-unfonts-core     : Korean TTF

OpenOffice.org :
openoffice.org-help-en-gb
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-za
openoffice.org-thesaurus-en-au

myspell-en-au
myspell-en-gb
myspell-en-za

Thunderbird-locale-en-gb

---

### Post by Malkovich on 2008-11-12
If you want the fastest distro, use only command line, meaning, like they already said, remove Xorg

---

### Post by Jags_FL on 2008-11-12
@ Malkovich

Thanks for the reply but my quest is for fastest GNOME distro as CLI is not an option for me.

After removing the packages I don't need (a long list includes Tracker search, Bluetooth & CUPS packages), and setting visual effects to none (even though Compiz works just fine on this PC), Ubuntu 8.10 'feels' lot faster and more responsive. Though I'm not sure whether these removals have any correlation with Ubuntu being feel faster.

---

### Post by tipalm on 2008-11-14
Well it is kind of silly to run a "personal computer" from CLI if a windows based GUI is available. 

I am referring to surfing the web, watching videos, listening to music, animation, graphics, etc. I am presuming most people would be using Ubuntu in a "personal home computer" situation.

Personally, I am impressed with the size of your geekpeen ; ]

As far as keeping the masses away I'd would disagree.

---

### Post by handy on 2008-11-14
> **.jeger said:**
> I tried Arch, but mucked something up while doing the installation. I'll come back to it when I've had some more experience with simpler installs.

> **Jags_FL said:**
> 
After reading Arch being one of the fastest distro, I tried but couldn't install Arch. I don't remember exactly now, but I was getting some kind 'Pacman' errors while installing GNOME.

If you follow the Arch [***_Beginners Guide_***]("http://wiki.archlinux.org/index.php/Beginners_Guide") to the letter you really shouldn't have any problems.

---

### Post by voteforpedro36 on 2008-11-14
> **tipalm said:**
> Well it is kind of silly to run a "personal computer" from CLI if a windows based GUI is available. 

I am referring to surfing the web, watching videos, listening to music, animation, graphics, etc. I am presuming most people would be using Ubuntu in a "personal home computer" situation.

Personally, I am impressed with the size of your geekpeen ; ]

As far as keeping the masses away I'd would disagree.

You can do all those things (well, maybe not animation/graphics, but you can view them) in CLI.

/me is talking from XFCE (though I have went from Flux to Openbox to Awesome to X doesn't work/running ncmpc in a tty for a couple days to here on Arch)

---

### Post by dizee on 2008-11-14
it's better to build from the bottom up if you really want speed. the debian net install is great for this and actually pretty easy if you are even vaguely familiar with the basics of the cli. arch is another option, i haven't tried it myself yet but by all accounts it's easier than you'd think and the documentation for it is excellent.

if you really wanted to be a speed freak you could try using xvesa instead of xorg, though i think it is no longer actively maintained. that shouldn't be necessary though. the main bottlenecks are the login manager and the window manager. if you've a heavy DE of course it'll be slow. openbox and pypanel on the other hand will fly (or even xfce, though that's not quite as light ;) ).

dillo is very lightweight as a web browser but doesn't support frames. kazehakase is light and full-featured, and opera also seems to do well surprisingly enough.

though not debian-based the customised kernel in puppy boots extremely quickly, so maybe that distro'd be worth a look, i'd certainly reccommend it.

if you are insistent on gnome, a new arch or debian netinstall would be the fastest i'd say.

---

### Post by Jags_FL on 2008-11-15
tipalm, handy, voteforpedro36 & dizee

guys thanks a lott for your replies...

Ok I'm gonna try to install Arch again and though I have successfully tried Debian net install somehow I come back to Ubuntu in a day or two... I always keep Ubuntu installed on the biggest partition anyway.

Regarding Firefox: to speed up the net surfing to the extreme, I have banned some 50 advert sites (Doubleclick, Atwola, Atdmt to name a few) in my router's hardware firewall, now if I don't use 'NoScript' (which is available with Firefox only; also have to mark those 50 sites as 'Untrusted' in NoScript) or use any other browser (irrespective of OS) the web page will keep looking for advert sites untill it times out and will then open the rest of the page. With combination of banning worst advert sites + NoScript + FiOS, most web pages opens like they are stored locally :)

---

