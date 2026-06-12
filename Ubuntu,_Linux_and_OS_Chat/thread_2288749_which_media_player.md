---
title: "which media player?"
date: 2015-07-29
forum: Ubuntu, Linux and OS Chat
---

### Post by Matrix01 on 2015-07-29
mplayer does not work for my Lubuntu 14.04, and
quick fix from launch pad did not work.
which media player do you prefer, any feed back or suggestions?
there are many choices, and i may not go through every single of them.

---

### Post by TheFu on 2015-07-29
There isn't an easy answer.  See - if you've upgraded the kernel or installed a newer release than the original 14.04.0 - well - the answers are different because the X/Windows libraries are different.

Rather than fight with it, I find it easier to watch media using a Raspberry Pi-2 running OSMC (which is a specialized install of Kodi media center).  At home, any media I have gets put somewhere on the network that the R-pi can playback.

Ok - let's say you just want to watch media on the laptop/netbook/desktop.  I use mplayer by default. Use to use mpv, but it isn't compatible with the newer kernels which pull in newer X11 libraries (I think). Honestly, I haven't tried to get mpv working very hard after the accidental kernel update.  I have had to fight with X11 a few times on 14.04 because the Xlibs and kernels have some undesirable interaction - at least here.

If I'm really into playing lots of media ... like on travel with the netbook and connected the hdmi out to the hotel TV ... then I'll use VLC.  It is easiest to keep track of where playback is in a list of media files when stuck in a hotel in the middle of nowhere on a stormy day.

---

### Post by andrew.46 on 2015-07-29
> **Matrix01 said:**
> mplayer does not work for my Lubuntu 14.04

I am curious to know why MPlayer does not work for you?

---

### Post by Simon_Tomoko on 2015-07-29
I use VLC myself, because it was highly praised by the community.  After I installed it, it has continued to function without issue. There are plenty of options available for both music, video, and internet streams.  I removed the default Dragon Player that came with my KDE, I don't recommend it at all.

---

### Post by monkeybrain20122 on 2015-07-29
> **TheFu said:**
>  Use to use mpv, but it isn't compatible with the newer kernels which pull in newer X11 libraries (I think). Honestly, I haven't tried to get mpv working very hard after the accidental kernel update.  I have had to fight with X11 a few times on 14.04 because the Xlibs and kernels have some undesirable interaction - at least here.


Huh?? I am interested to know which newer kernel and which version of mpv you are talking about. While I have switched to 15.04 I maintain a 14.04 installation in an external drive and running kernel 4.0.x and latest mpv from git master. Never have a problem with libraries. Maybe all you need is an up to date version of mpv.

[http://mpv.io/installation/](http://mpv.io/installation/)

---

### Post by mc4man on 2015-07-30
> **andrew.46 said:**
> I am curious to know why MPlayer does not work for you?
I'd guess the OP may have been using mplayer-gui which has been [quite broken]("https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1218510") in Ubuntu/Debian for some time. 
(never was much use anyway but that's an opinion...

As far as mpv & kernel upgrades - nothing there, i'd suspect TheFu runs a non standard install that is nothing like the OP

---

### Post by shantiq on 2015-07-30
[FONT=book antiqua]for music  >>>   [cantata]("http://ubuntuforums.org/showthread.php?t=2287569")    plays ALL formats; has thorough info on tracks plays cue files zips etc ...
for video two best ones >>>  [mpv]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests")   or [/FONT][kodi]("http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux")[FONT=book antiqua]  ;   both extremely stable

mpv

```
sudo add-apt-repository ppa:mc3man/mpv-test
sudo apt-get update ; sudo apt-get install mpv
```

kodi

[/FONT]```
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update ; sudo apt-get install kodi
```[FONT=book antiqua]
[/FONT]

---

### Post by SeijiSensei on 2015-07-30
I use SMPlayer as a GUI front-end to either mplayer or mpv.  I use the version in Doug McMahon's repository:
```

sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get smplayer mpv

```
I'm also curious why mplayer doesn't work for you.  Have you run mplayer from the command prompt with:
```
mplayer /path/to/file
```
If it fails, you'll get an error message.

That repository is for 14.04.

---

### Post by Matrix01 on 2015-07-30
here's output;

taro@taro-HP-Mini-110-3000:~$ mplayer/Taylor Swift - Bad Blood ft. Kendrick Lamar - YouTube [720p].mp4
bash: mplayer/Taylor: No such file or directory
taro@taro-HP-Mini-110-3000:~$ 











> **SeijiSensei said:**
> I use SMPlayer as a GUI front-end to either mplayer or mpv.  I use the version in Doug McMahon's repository:
```

sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get smplayer mpv

```
I'm also curious why mplayer doesn't work for you.  Have you run mplayer from the command prompt with:
```
mplayer /path/to/file
```
If it fails, you'll get an error message.

That repository is for 14.04.

---

### Post by TheFu on 2015-07-30
> **monkeybrain20122 said:**
> Huh?? I am interested to know which newer kernel and which version of mpv you are talking about. While I have switched to 15.04 I maintain a 14.04 installation in an external drive and running kernel 4.0.x and latest mpv from git master. Never have a problem with libraries. Maybe all you need is an up to date version of mpv.

[http://mpv.io/installation/](http://mpv.io/installation/)

For general purpose systems, I will not installed software outside the package management system. Basically, it wasn't worth my effort to solve any issue with mpv on the machine if **aptitude install** didn't provide a working version.  Looked at the caveats for the 14.04 PPA - didn't like many of those just for a media player. [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) 

Got the backported kernel from ?15.04? (via hw compatibility updates) and it broke X/Windows. I was only slightly interested to solve a touchpad driver issue, but not at the expense of X/Windows. Got X/Windows working and the touchpad, but mpv didn't like the new Xlibs. No other programs noticed that I've seen. Don't remember why - it has been about a month.  Currently running 3.16.0-44-generic on the 14.04 system.

Just did an *aptitude install mpv* which wanted to pull in a bunch of dependencies that I remember broke X11 last time. Cntl-c out. Not worth the hassle today.  I'll look at it in 16.04 - around June.

---

### Post by Bucky Ball on 2015-07-30
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request. 

```
which media player do you prefer, any feed back or suggestions?
```

If you want support for getting an audio player working, see the third link in my signature then post a thread with a title describing what you want support with in the appropriate area. Good luck.

---

### Post by Geoffrey_Arndt on 2015-07-30
Matrix,   for any command, the first step is to insure your command is input correctly.   Re-read Sensei's post re mplayer and try again.  (need a space between app and path).

---

### Post by SeijiSensei on 2015-07-30
> **Geoffrey_Arndt said:**
> Matrix,   for any command, the first step is to insure your command is input correctly.   Re-read Sensei's post re mplayer and try again.  (need a space between app and path).
Yes.  The shell uses the space as the basic delimiter between fields in a command.  The command
```
mplayer /path/to/some/file
```
runs the mplayer program with "file".  Once you get the hang of using the shell, these kinds of things will come naturally.

---

### Post by TheFu on 2015-07-30
> **Matrix01 said:**
> here's output;

taro@taro-HP-Mini-110-3000:~$ mplayer/Taylor Swift - Bad Blood ft. Kendrick Lamar - YouTube [720p].mp4
bash: mplayer/Taylor: No such file or directory
taro@taro-HP-Mini-110-3000:~$

That command shouldn't work for a number of reasons. I'm assuming it isn't a typo.
* The correct path (complete or relative) to the file **must** be specified.
* The filename has spaces and other _special characters_ in it, so that must be quoted.

I suspect the correct command would be something like:
```
$ mplayer "~/Downloads/Taylor Swift - Bad Blood ft. Kendrick Lamar - YouTube [720p].mp4"
```
with the quotes. Of course, the exact location on your system is unknown to me.

If you are new to Unix systems, then it may be best to stay inside the GUI to avoid learning about files and directory paths. **smplayer** might be a better choice at least until your Linux-fu gets stronger.

OTOH, if you want to learn this stuff- [http://linuxcommand.org/](http://linuxcommand.org/) has a free PDF book which is useful with carefully directed teaching. Skills are built on each other, so start at the beginning and work through it.  

There are shorter, less complete, options for learning this stuff. Sometimes you just need the exact knowledge - not a book:  [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) gets to the point about directories and filenames quickly.

I apologize if it was just a typo.

---

### Post by monkeybrain20122 on 2015-07-30
> **TheFu said:**
> For general purpose systems, I will not installed software outside the package management system. Basically, it wasn't worth my effort to solve any issue with mpv on the machine if **aptitude install** didn't provide a working version.  Looked at the caveats for the 14.04 PPA - didn't like many of those just for a media player. [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) 

Got the backported kernel from ?15.04? (via hw compatibility updates) and it broke X/Windows. I was only slightly interested to solve a touchpad driver issue, but not at the expense of X/Windows. Got X/Windows working and the touchpad, but mpv didn't like the new Xlibs. No other programs noticed that I've seen. Don't remember why - it has been about a month.  Currently running 3.16.0-44-generic on the 14.04 system.

Just did an *aptitude install mpv* which wanted to pull in a bunch of dependencies that I remember broke X11 last time. Cntl-c out. Not worth the hassle today.  I'll look at it in 16.04 - around June.


Well to each his own, but based on your descriptions your problem is caused by backported kernel **within** the package management system rather than ppas. Personally I have never had any problem using packages outside the repo. It is a lot easier to upgrade packages this way to get the bug fixes/enhancement upstream  than to fight with known broken packages from the official repo, just my two cents.

---

### Post by SeijiSensei on 2015-07-30
I'm picky about the PPAs, but I trust Doug McMahon.  He's a frequent contributor here as well as mc4man.  I also routinely use Oracle's PPA for Virtualbox, the Mozilla PPA for Firefox and Thunderbird, and the [Pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") PPA.

---

### Post by monkeybrain20122 on 2015-07-30
> **SeijiSensei said:**
> I'm picky about the PPAs, but I trust Doug McMahon.  He's a frequent contributor here as well as mc4man.  I also routinely use Oracle's PPA for Virtualbox, the Mozilla PPA for Firefox and Thunderbird, and the [Pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") PPA.

+1 re mc4man, he has helped me out on various occasions on this forum. I definitely can trust him on the quality of his packages which often fix things that are broken in the official repo (e.g audacity in 15.04 is unusable because it is compiled against the wrong version of wxwidgets, Doug's package fixes that) I will also add rvm's ppa to the list for Smplayer and Smtube (Smtube in the repo is broken completely due to it being very out of date and doesn't keep up with google's changes, Smplayer from repo is also too old to work with mpv,-- and mpv in repo is too old to work with new versions of Smplayer) 

In general I find Ubuntu's stock offering for multimedia stuffs underwhelming, they are often old/crippled or even completely broken. I have been compiling vlc and mpv for quite sometimes (against ffmpeg instead of avconv) For a while vdpau support is missing for vlc in all Ubuntu builds for some reasons even though it has been available since Ubuntu 13.04 (?) or 13.10 (Haven't checked mc4man's build though since compiling is quite easy once got all the dependencies)

Other  ppas I use  are  LO and marutter's R ppa (just install the base packages and the rest from R itself) LO's ppa is maintained by the same packaging team of  LO for  Ubuntu and R's ppa is very trusted because Michael is the person who maintains the Debian packages for CRAN (I think they were actually taken from the ppa) If you don't trust these you can't trust the official repo.

---

### Post by night_sky2 on 2015-07-30
VLC hands down for me.

---

### Post by night_sky2 on 2015-07-30
> **Simon_Tomoko said:**
> I use VLC myself, because it was highly praised by the community.  After I installed it, it has continued to function without issue. There are plenty of options available for both music, video, and internet streams.  I removed the default Dragon Player that came with my KDE, I don't recommend it at all.
And VLC is shipped with it's own media codecs. So no need to install any restricted extras if you plan to use it as your main video player.

---

### Post by vasa1 on 2015-07-30
> **monkeybrain20122 said:**
> +1 re mc4man, he has helped me out on various occasions on this forum. ...
Ditto here!

---

### Post by shantiq on 2015-07-30
Matrix  you need a gap here


```
taro@taro-HP-Mini-110-3000:~$ mplayer/Taylor Swift - Bad Blood ft. Kendrick Lamar - YouTube [720p].mp4
bash: mplayer/Taylor: No such file or directory
taro@taro-HP-Mini-110-3000:~$
```


this needs to be

```
mplayer  "Taylor Swift - Bad Blood ft. Kendrick Lamar - YouTube [720p].mp4"
```


** you need speech marks if you have space in your file names;  **
also this command needs to be in the folder where the file is
Is it in your home folder?
if it is in your Music folder for example you will need to do this; if your Videos folder "cd Videos"

```
cd Music ; mplayer  "Taylor Swift - Bad Blood ft. Kendrick Lamar - YouTube [720p].mp4"
```


and see what message comes up


Best luck   shan

---

### Post by Matrix01 on 2015-07-30
FIY
this link says mplayer has bug;

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1218510](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1218510)

---

### Post by monkeybrain20122 on 2015-07-30
> **Matrix01 said:**
> FIY
this link says mplayer has bug;

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1218510](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1218510)

The bug is related to the gui. Since you use the command it doesn't have anything to do with your problem (which, as others have pointed out you have omitted a space and perhaps a pair of quotations)

In any case I am surprised that anyone is actually using mplayer's gui, most people would use either Smplayer or gnome-mplayer (or maybe a few others for different DE like dragon player(?)) for gui frontend instead of mplayer-gui.

---

### Post by mc4man on 2015-07-30
If having issue getting /path/to/file correct then open a terminal. Type in mplayer then hit the spacebar to move cursor & create a space.. In your file manager open folder containing video, drag & drop it on to the terminal. Click in terminal to return focus, press enter on keyboard.

Re: vlc - in general I think it's ok though with unity I've gotten tired of the scaling issues when one open & then closes vlc with a vid at or bigger then monitor's vertical size. Not really vlc's problem but nothing Ubuntu's going to fix..

---

### Post by TheFu on 2015-07-30
I always just use tab-completion for file/directories.  Typing 2-3 characters, then {tab} is much easier AND it fills in the correct name with any required escapes. 
Confused? [https://www.debian-administration.org/article/316/An_introduction_to_bash_completion_part_1](https://www.debian-administration.org/article/316/An_introduction_to_bash_completion_part_1) explains.

If you are typing the whole thing, you are doing it wrong.  Learn a little bit more about the shell and shortcuts to save 90% of your time there.

---

### Post by monkeybrain20122 on 2015-07-31
> **TheFu said:**
> I always just use tab-completion for file/directories.  Typing 2-3 characters, then {tab} is much easier AND it fills in the correct name with any required escapes. 
Confused? [https://www.debian-administration.org/article/316/An_introduction_to_bash_completion_part_1](https://www.debian-administration.org/article/316/An_introduction_to_bash_completion_part_1) explains.

If you are typing the whole thing, you are doing it wrong.  Learn a little bit more about the shell and shortcuts to save 90% of your time there.

I would just do ls and then cut and paste from terminal, easy and won't mistype. e.g 

cd Videos
ls
then copy whatever and paste after mplayer and a space, add quotations if needed.

I personally prefer a gui or just right clicking the video.

---

### Post by shantiq on 2015-07-31
Matrix I do not know how used you are to a terminal for playing media; but here is a breakdown 
[if you already **know all this** just ignore might be of use to others ]

1.  Go to the right folder to find your files
Most folks keep their music in Music and videos in Videos
so cd [change directory] to there

ie     ```
cd Videos
```

[[IMG]http://s29.postimg.org/77f8fvb43/image.png[/IMG]]("http://postimg.org/image/77f8fvb43/")

2. Then enter name of your player  :  mplayer ; mpv; vlc ; cvlc ; nvlc ; any other ...

3. Then and that is the tricky bit if you are not a usual terminal user;   you need to use "" marks if your filename has gaps in it
otherwise you will get this message or similar

```
MPlayer2 2.0-701-gd4c5b7f-2ubuntu2 (C) 2000-2012 MPlayer Team
Cannot open file '/home/shantiq/.mplayer/input.conf': **No such file or directory**
Failed to open /home/shantiq/.mplayer/input.conf.
```

see above image

Then reenter with "" marks and all good


3. ***  There is an easier way:***

Enter first 2 or 3 letters of you filename you wish to play [make sure there are no other files in folder with similar if there is enter one more letter until it it unique]   then hit Tab Bar   and it will fill in the rest with backslashes \

see image below:

[[IMG]http://s29.postimg.org/qnzy2e683/image.png[/IMG]]("http://postimg.org/image/qnzy2e683/")

---

### Post by vasa1 on 2015-07-31
> **SeijiSensei said:**
> I use SMPlayer as a GUI front-end to either mplayer or mpv.  I use the version in Doug McMahon's repository:
```

sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get smplayer mpv

```
...
After reading this, I installed SMPlayer. But when I look in my *.xsessions-errors*, I see entries like this:```
BrowserWindow::adjustLocation: "http://www.tonvid.com/" 
BrowserWindow::adjustLocation: "http://www.tonvid.com/search.php" 
```And then I came across this:[http://sourceforge.net/p/smplayer/bugs/695/](http://sourceforge.net/p/smplayer/bugs/695/)

My version of SMPlayer:
```
04:25 PM ~ $ acpol smplayer
smplayer:
  Installed: 14.9.0.7042-1~trusty1
  Candidate: 14.9.0.7042-1~trusty1
  Version table:
 *** 14.9.0.7042-1~trusty1 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     0.8.6-2 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
04:25 PM ~ $ 
```

---

### Post by SeijiSensei on 2015-07-31
> **vasa1 said:**
> After reading this, I installed SMPlayer. But when I look in my *.xsessions-errors*, I see entries like this:```
BrowserWindow::adjustLocation: "http://www.tonvid.com/" 
BrowserWindow::adjustLocation: "http://www.tonvid.com/search.php" 
```And then I came across this:[http://sourceforge.net/p/smplayer/bugs/695/](http://sourceforge.net/p/smplayer/bugs/695/)
That bug refers to **smtube**, a companion program designed to play YouTube videos.  When I launch smplayer from the command prompt, I don't see any references to tonvid.com.  Running smtube generates the same "BrowserWindow" error you report.

---

### Post by vasa1 on 2015-07-31
And this is what the smtube GUI looks like for me. I haven't customized or changed any settings:

---

### Post by mc4man on 2015-07-31
> **vasa1 said:**
> After reading this, I installed SMPlayer. But when I look in my *.xsessions-errors*, I see entries like this:```
BrowserWindow::adjustLocation: "http://www.tonvid.com/" 
BrowserWindow::adjustLocation: "http://www.tonvid.com/search.php" 
```And then I came across this:[http://sourceforge.net/p/smplayer/bugs/695/](http://sourceforge.net/p/smplayer/bugs/695/)


It is nothing to concern about, while a ubuntu session doesn't use .xsession.errors anymore it has always been a dump for info, not necessarily 'errors'

run smtube from a terminal & give it a search term  to see - -
ex.

> $ smtube tricks
Translations path: "/usr/share/smtube/translations" 
MyCookieJar::load 
MyCookieJar::load: 3 cookies loaded 
BrowserWindow::loadConfig 
Players::load 
Players::availablePlayers: 0 : "/usr/bin/smplayer" 
Players::availablePlayers: 1 : "/usr/bin/smplayer" 
Players::availablePlayers: 2 : "/usr/bin/mplayer" 
Players::availablePlayers: 3 : "/usr/bin/vlc" 
Players::availablePlayers: 5 : "/usr/bin/totem" 
Players::availablePlayers: 6 : "/usr/bin/gnome-mplayer" 
Players::availablePlayers: 7 : "/usr/bin/mpv" 
Players::availablePlayers: 8 : "/usr/bin/mpv" 
ytcode_file: "/home/doug/.config/smplayer/yt.js" 
BrowserWindow::adjustLocation: "http://www.tonvid.com/search.php?q=tricks" 

---

### Post by monkeybrain20122 on 2015-07-31
Smutube is actually a web app, tonvid.com is its url.

---

### Post by vasa1 on 2015-07-31
> **mc4man said:**
> It is nothing to concern about, ...

> **monkeybrain20122 said:**
> Smtube is actually a web app, tonvid.com is its url.
Thanks!

tonvid.com is set up by the dev of smplayer and the terms of use are clearly laid out on the site.

---

