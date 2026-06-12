---
title: "Must have CLI apps compared to GUI alternatives"
date: 2013-02-06
forum: The Cafe
---

### Post by rmcellig on 2013-02-06
What are your top CLI apps that you use that you feel are better and faster than a GUI alternative?

So far, in my early years of using Linux after switching from the Mac, I have found some I feel are so easy to use compared to the GUI alternatives I was using on the Mac side. Here they are:

arecord - I use this to record all of my radio show. Fast and easy!

Imagemagick - This is a new one for me. Less than 20c seconds I converted a folder full of jpgs to one pdf file. Love it!!

sudo apt-get install - I find this so fast at installing apps compared to the GUI solution.

What are your favs? Especially for newbies. As I get more comfortable with the CLI, I'm really starting to realize how powerful it is!!

---

### Post by georgelappies on 2013-02-06
bmon - monitoring bandwidth
htop - excellent process monitor
nethogs - let you know what is using up your bandwidth
fortune - always leaves a smile on the face especially when combined with a random cowsay

---

### Post by tgalati4 on 2013-02-06
free -- Show your RAM and swap
w -- What's happening?
df -h -- Show your disk usage
dmesg | more -- Look for system/hardware problems
netstat -r -- Look at your network routing
sudo smartctl -a /dev/sda -- Look at your harddisk error records.
ruptime -- Show your other machines on the network, also running rwhod.

---

### Post by mamamia88 on 2013-02-06
Clamz- Download music from amazon music store.   Just edit the config file with the directory you want music to be downloaded by default or it will download to whatever the current directory is.   Then you just run clamz pathtofile.amz

---

### Post by nothingspecial on 2013-02-06
weechat because once set up it has more features and is easier to use than any irc client I've tried. Plus you can run it on a server and connect remotely and stuff.

That and anything that does something you do often that you can use with an alias or a function in your .bashrc 

It's fun to try and do everything you normally do without X. Well I find it fun anyway......... >.<

---

### Post by Toz on 2013-02-06
> It's fun to try and do everything you normally do without X. Well I find it fun anyway......... >.<
+1. My favourites are:

- cmus - music player
- screen - screen multiplexer
- links - web browsing
- irssi - irc
- alpine - mail reader

---

### Post by monkeybrain2012 on 2013-02-06
octave. There was a gui called qtoctave but it was buggy and the project has died.

There is a new gui from the developmental version that looks like matlab, but haven't tried it out yet.

---

### Post by nothingspecial on 2013-02-06
> **Toz said:**
> +1. My favourites are:

- cmus - music player
- screen - screen multiplexer
- links - web browsing
- irssi - irc
- alpine - mail reader

Yeah, I'd say instead of screen itself use byobu with which you can switch between screen and tmux and get the best of both multiplexers.

I'd say elinks is better than links.

cmus is great if you want a music player with a library and stuff. I'd rather something like mplayer or cvlc that you can alias/function/script

I'm with you with alpine.

weechat is sooo much better than irssi, try it :)

---

### Post by doorknob60 on 2013-02-06
ffmpeg - better than any of the GUIs that exist to convert videos and such. Just so much more powerful and less buggy.
youtube-dl - best way to download videos from Youtube. Period.
pacman - Arch only, but it's the best package manager I've ever used. Better than Software Center, Synaptic, everything (including apt-get for the record).

---

### Post by GrouchyGaijin on 2013-02-18
Yeah I agree - cmus is quite good.

I also use mutt for email and as mentioned above ffmpeg for video conversion.  Here is a tip I got from the Multimedia forum, run the latest version of ffmpeg (the dev vervion) from a directory via the command line and you can have the version found in the repo installed system wide for things like kden live that require it.

---

### Post by Paqman on 2013-02-18
chown and chmod. Always just found sorting permissions easier in the CLI. I really only use the CLI for maintenance work, so find the preinstalled suite of tools more than adequate.

---

### Post by oldos2er on 2013-02-18
apt-get and apt-cache, use them all the time.

mplayer

htop

nano, when a simple text editor will do the job.

---

### Post by Kov3nant on 2013-02-18
apt-get (always). Never touch the software center.
nano is a nice quick editor for small files, otherwise I use gedit or emacs

Otherwise, when I'm bored, I'll just explore using the terminal. It's good fun.

---

### Post by deadflowr on 2013-02-18
> **Kov3nant said:**
> apt-get (always). Never touch the software center.
nano is a nice quick editor for small files, otherwise I use gedit or emacs

Otherwise, when I'm bored, I'll just explore using the terminal. It's good fun.

I tend to use the software center for the reviews.
It's nice to know if something I want to use is actually working.

For CLI apps, whoami.

No, really, who am I? 

ufw over gufw.

---

### Post by cariboo on 2013-02-18
The one app I always install is mc.

---

### Post by andrew.46 on 2013-02-21
I hope I am the first to mention the great newsreader slrn, going strong since 1994 with a new release at the end of 2012:

Home of the slrn newsreader
[http://slrn.sourceforge.net/](http://slrn.sourceforge.net/)

And who said Usenet was dying :)

---

### Post by angry_johnnie on 2013-02-21
I used to be a commandline junkie :p  

dvtm - console-based tiled window manager
gpm - a terminal mouse pointer
screen - terminal multiplexer
moc - commandline music player
mplayer - media player. will play video on the framebuffer
finch - console-based IM client
links2 - console-based web browser with image support
nano - my favorite text editor
mc - file manager
fbi - console-based image viewer
fbgrab - framebuffer screenshot program
convert - image editor. part of imagemagick
bsdgames - a bunch of console-based games

---

### Post by GrouchyGaijin on 2013-02-22
@angry_johnnie  Dude, that is a serious command line fetish there ;-)

One more for the list of cool cli apps - note.
Note is a cli note taking app that I started using and like.

---

### Post by matt_symes on 2013-02-23
rtorrent and newsbeauter. slrn is great and screen is a winner. 

The only thing i don't do in the terminal is web browsing,

---

### Post by nothingspecial on 2013-02-23
> **matt_symes said:**
> 

The only thing i don't do in the terminal is web browsing,

Amatuer :p

---

### Post by matt_symes on 2013-02-23
> **nothingspecial said:**
> Amatuer :p

LOL. I have elinks installed but i don't use it unless to have no choice.

---

### Post by mJayk on 2013-02-23
> **monkeybrain2012 said:**
> octave. There was a gui called qtoctave but it was buggy and the project has died.

There is a new gui from the developmental version that looks like matlab, but haven't tried it out yet.

Hay do you know the name of the new octave gui? Worth a try

---

### Post by K.Mandla on 2013-02-24
I'm just going to dump *pacman -Q* and trim out the boring stuff.

[LIST]
[*][**beets**]("http://beets.radbox.org/"): for managing music information
[*][**binclock**]("http://www.ngolde.de/binclock.html"): a binary clock, useful for a screensaver
[*][**bsd-games**]("ftp://ftp.ibiblio.org/pub/Linux/games/"): worms and rain are good for screensavers too
[*][**charm**]("http://ljcharm.sourceforge.net/t_why.shtml"): python-based blog client that will mesh with Wordpress.com, usually
[*][**clockywock**]("http://www.soomka.com/"): console clock and screensaver
[*][**cmatrix**]("http://www.asty.org/cmatrix/"): Matrix-esque screensaver
[*][**crawl**]("http://crawl.develz.org/wordpress/"): usually I just ssh into the dev server, but occasionally I play offline
[*][**cursetheweather**]("http://opensource.hld.ca/trac.cgi/wiki/CurseTheWeather"): pulls weather data, useful once or twice a day
[*][**elinks**]("http://elinks.or.cz/"): my favorite text-based browser, can manage (but not display) images, etc.
[*][**fbgrab**]("http://hem.bredband.net/gmogmo/fbgrab/"): framebuffer screenshot tool
[*][**fbv**]("http://s-tech.elsat.net.pl/fbv/"): framebuffer image viewer; hook this into elinks for good clean fun
[*][**figlet**]("http://www.figlet.org/"): funky text tool; again, for screensavers
[*][**glances**]("https://github.com/nicolargo/glances"): quite possibly a better system monitor than htop
[*][**gnupg**]("http://www.gnupg.org/"): encryption is my life
[*][**hnb**]("http://hnb.sourceforge.net/"): hierarchical notebook; good for making lists in general
[*][**htop**]("http://htop.sourceforge.net/"): for the most part, better than top
[*][**ical2rem**]("http://jalcorn.net/weblog/archives/899-iCal-to-Remind-script.html"): converts ical (think: Google Calendar) to remind format (think: wyrd)
[*][**iptraf-ng**]("https://fedorahosted.org/iptraf-ng/"): finest network monitor in the history of humanity
[*][**irssi**]("http://www.irssi.org/"): chat client. I don't chat much, so this is okay. weechat is probably better
[*][**libcaca**]("http://caca.zoy.org/wiki/libcaca"): img2txt converts a standard image into chunky text; good party game :roll:
[*][**mc**]("http://www.midnight-commander.org/"): if you must use a file manager, use this one. can do ftp too
[*][**moc**]("http://moc.daper.net/"): music player. cmus on slow-slow-slow machines, opencubicplayer on fast-fast-fast machines
[*][**most**]("http://www.jedsoft.org/most/index.html"): my fave-rave pager
[*][**ncdu**]("http://dev.yorhel.nl/ncdu"): graphical representation of drive space used. Indispenable
[*][**ncmatrix**]("http://webpages.charter.net/tux/ncmatrix/index.htm"): cmatrix, looped through your network connection
[*][**ncurses-life**]("http://csiuo.com/drupal/content/ncurses-life"): screensaver, of course
[*][**ntp**]("http://www.ntp.org/"): on slow machines or machines with weak internal clocks, this will keep your ticker in line
[*][**openssh**]("http://www.openssh.org/portable.html"): for scp, mostly
[*][**re-alpine**]("http://sourceforge.net/projects/re-alpine/"): alpine the mail client. Not the best, but not the worst either
[*][**remind**]("http://www.roaringpenguin.com/penguin/open_source_remind.php"): calendar and appointment tool, quite possibly more detailed than can be understood by mere mortals
[*][**renameutils**]("http://www.nongnu.org/renameutils/"): qmv is a godsend
[*][**rsync**]("http://samba.anu.edu.au/rsync/"): only the greatest sync utility ever
[*][**sc**]("http://packages.ubuntu.com/dapper/sc"): a primitive but intuitive spreadsheet
[*][**surfraw**]("http://surfraw.alioth.debian.org/"): looped into elinks, and the CLI becomes a Web search tool
[*][**tamsyn-font**]("http://www.fial.com/~scott/tamsyn-font"): I flip-flop between this and terminus
[*][**tbclock**]("http://tamentis.com/projects/tbclock/"): another binary clock, this one better
[*][**terminus-font**]("http://sourceforge.net/projects/terminus-font/"): I flip-flop between this and tamsyn
[*][**tmux**]("http://tmux.sourceforge.net/"): a little better than gnu-screen. A little ...
[*][**tty-clock**]("http://github.com/xorg62/tty-clock"): terminal clock display, in digits, for a screensaver
[*][**ttyload**]("http://web.archive.org/web/20101115171456/http://www.daveltd.com/src/util/ttyload/"): system load monitor; screensaver
[*][**vim**]("http://www.vim.org/"): mostly for [**vimwiki**]("http://code.google.com/p/vimwiki/") and [**NERD_tree**]("https://github.com/scrooloose/nerdtree")
[*][**vitetris**]("http://www.victornils.net/tetris/"): tetris game
[*][**vms-empire**]("http://www.catb.org/~esr/vms-empire/"): text-based strategic conquest; think Risk but different
[*][**vtclock**]("http://webonastick.com/vtclock"): terminal clock; screensaver
[*][**wavemon**]("http://eden-feed.erg.abdn.ac.uk/wavemon/"): wireless information tool; coolest thing ever
[*][**wicd**]("http://wicd.sourceforge.net/"): curses-based network manager
[*][**wyrd**]("http://pessimization.com/software/wyrd/"): frontend to remind and despite some oddball dependencies, quite useful
[*][**yaourt**]("http://archlinux.fr/yaourt-en"): pacman after too much caffeine; Arch Linux only, of course
[/LIST]
I think that does it. There are a few others, but they are obscure and not things I regularly use. :)

---

### Post by tartalo on 2013-02-24
No one mentioned cp, mv and rm yet?

I have had no problem since I moved to Dolphin, but when I used Nautilus it would sometimes freeze in the middle of an operation, and the command line always saved the day. The command line is also faster.

Also:
dd if=/path/to/livecd.iso of=/dev/mypendrive && sync

is much much more reliable that the USB Creator.

---

### Post by nothingspecial on 2013-02-24
> **andrew.46 said:**
> I hope I am the first to mention the great newsreader slrn, going strong since 1994 with a new release at the end of 2012:

Home of the slrn newsreader
[http://slrn.sourceforge.net/](http://slrn.sourceforge.net/)

And who said Usenet was dying :)

> **K.Mandla said:**
> I'm just going to dump *pacman -Q* and trim out the boring stuff.

[LIST]
[*][**beets**]("http://beets.radbox.org/"): for managing music information
[*][**binclock**]("http://www.ngolde.de/binclock.html"): a binary clock, useful for a screensaver
[*][**bsd-games**]("ftp://ftp.ibiblio.org/pub/Linux/games/"): worms and rain are good for screensavers too
[*][**charm**]("http://ljcharm.sourceforge.net/t_why.shtml"): python-based blog client that will mesh with Wordpress.com, usually
[*][**clockywock**]("http://www.soomka.com/"): console clock and screensaver
[*][**cmatrix**]("http://www.asty.org/cmatrix/"): Matrix-esque screensaver
[*][**crawl**]("http://crawl.develz.org/wordpress/"): usually I just ssh into the dev server, but occasionally I play offline
[*][**cursetheweather**]("http://opensource.hld.ca/trac.cgi/wiki/CurseTheWeather"): pulls weather data, useful once or twice a day
[*][**elinks**]("http://elinks.or.cz/"): my favorite text-based browser, can manage (but not display) images, etc.
[*][**fbgrab**]("http://hem.bredband.net/gmogmo/fbgrab/"): framebuffer screenshot tool
[*][**fbv**]("http://s-tech.elsat.net.pl/fbv/"): framebuffer image viewer; hook this into elinks for good clean fun
[*][**figlet**]("http://www.figlet.org/"): funky text tool; again, for screensavers
[*][**glances**]("https://github.com/nicolargo/glances"): quite possibly a better system monitor than htop
[*][**gnupg**]("http://www.gnupg.org/"): encryption is my life
[*][**hnb**]("http://hnb.sourceforge.net/"): hierarchical notebook; good for making lists in general
[*][**htop**]("http://htop.sourceforge.net/"): for the most part, better than top
[*][**ical2rem**]("http://jalcorn.net/weblog/archives/899-iCal-to-Remind-script.html"): converts ical (think: Google Calendar) to remind format (think: wyrd)
[*][**iptraf-ng**]("https://fedorahosted.org/iptraf-ng/"): finest network monitor in the history of humanity
[*][**irssi**]("http://www.irssi.org/"): chat client. I don't chat much, so this is okay. weechat is probably better
[*][**libcaca**]("http://caca.zoy.org/wiki/libcaca"): img2txt converts a standard image into chunky text; good party game :roll:
[*][**mc**]("http://www.midnight-commander.org/"): if you must use a file manager, use this one. can do ftp too
[*][**moc**]("http://moc.daper.net/"): music player. cmus on slow-slow-slow machines, opencubicplayer on fast-fast-fast machines
[*][**most**]("http://www.jedsoft.org/most/index.html"): my fave-rave pager
[*][**ncdu**]("http://dev.yorhel.nl/ncdu"): graphical representation of drive space used. Indispenable
[*][**ncmatrix**]("http://webpages.charter.net/tux/ncmatrix/index.htm"): cmatrix, looped through your network connection
[*][**ncurses-life**]("http://csiuo.com/drupal/content/ncurses-life"): screensaver, of course
[*][**ntp**]("http://www.ntp.org/"): on slow machines or machines with weak internal clocks, this will keep your ticker in line
[*][**openssh**]("http://www.openssh.org/portable.html"): for scp, mostly
[*][**re-alpine**]("http://sourceforge.net/projects/re-alpine/"): alpine the mail client. Not the best, but not the worst either
[*][**remind**]("http://www.roaringpenguin.com/penguin/open_source_remind.php"): calendar and appointment tool, quite possibly more detailed than can be understood by mere mortals
[*][**renameutils**]("http://www.nongnu.org/renameutils/"): qmv is a godsend
[*][**rsync**]("http://samba.anu.edu.au/rsync/"): only the greatest sync utility ever
[*][**sc**]("http://packages.ubuntu.com/dapper/sc"): a primitive but intuitive spreadsheet
[*][**surfraw**]("http://surfraw.alioth.debian.org/"): looped into elinks, and the CLI becomes a Web search tool
[*][**tamsyn-font**]("http://www.fial.com/~scott/tamsyn-font"): I flip-flop between this and terminus
[*][**tbclock**]("http://tamentis.com/projects/tbclock/"): another binary clock, this one better
[*][**terminus-font**]("http://sourceforge.net/projects/terminus-font/"): I flip-flop between this and tamsyn
[*][**tmux**]("http://tmux.sourceforge.net/"): a little better than gnu-screen. A little ...
[*][**tty-clock**]("http://github.com/xorg62/tty-clock"): terminal clock display, in digits, for a screensaver
[*][**ttyload**]("http://web.archive.org/web/20101115171456/http://www.daveltd.com/src/util/ttyload/"): system load monitor; screensaver
[*][**vim**]("http://www.vim.org/"): mostly for [**vimwiki**]("http://code.google.com/p/vimwiki/") and [**NERD_tree**]("https://github.com/scrooloose/nerdtree")
[*][**vitetris**]("http://www.victornils.net/tetris/"): tetris game
[*][**vms-empire**]("http://www.catb.org/~esr/vms-empire/"): text-based strategic conquest; think Risk but different
[*][**vtclock**]("http://webonastick.com/vtclock"): terminal clock; screensaver
[*][**wavemon**]("http://eden-feed.erg.abdn.ac.uk/wavemon/"): wireless information tool; coolest thing ever
[*][**wicd**]("http://wicd.sourceforge.net/"): curses-based network manager
[*][**wyrd**]("http://pessimization.com/software/wyrd/"): frontend to remind and despite some oddball dependencies, quite useful
[*][**yaourt**]("http://archlinux.fr/yaourt-en"): pacman after too much caffeine; Arch Linux only, of course
[/LIST]
I think that does it. There are a few others, but they are obscure and not things I regularly use. :)


FWIW I learned everything I know about cli applications from these 2 guys.

---

