---
title: "The ultimate mplayer config file!!!!!"
date: 2005-10-16
forum: Tutorials
---

### Post by pizzach on 2005-10-16
Mplayer is da bomb.  But with a good config file it's much better.  Take a look at mine and try it!  Keep in mind, if you don't use mplayer from the terminal you don't know what you're emissing.  That and this config is for the terminal version.

To play a movie from the terminal just 
$ mplayer filename

Go to a terminal
(next step is only needed if you have never run mplayer before)
$ mkdir .mplayer 
$ cd .mplayer
$gedit config
Paste in my code and save

Anyone have their own?  

 ~/.mplayer/config

```

#General setup

ao="alsa"	#audio out
mixer-channel="Master"
srate=48000

really-quiet="1" #Very very little console output

vo="xv"	#video out
zoom="1" #Allow sofware scaling if I use x11 for vo
aid="1"	#audio channel
sid="0"	#subtitle set

#Display

double="yes"	#double buffering(recommended for subtitles)
monitoraspect="16:9"	#I'm on a widescreen laptop so keeps 4:3 content from stretching
framedrop="1"	# For slow machines
hardframedrop="0"  #Make sure hard frame drop is off but can turn on easily now

#subtitle code
#Truetype fonts rock! (sudo apt-get msttcorefonts)
font=/usr/share/fonts/truetype/msttcorefonts/impact.ttf

ffactor="10" #black outline
sub-bg-alpha="0" #background color ala closed captions
sub-bg-color="0" #black to white
subfont-text-scale="3.7"	#truetype font scaling
subfont-blur="1" #Slight blur

#This sets the postprocessing into overdrive using all possible spare cpu cycles to make the movie look better
autoq=100
vf=pp=de,hqdn3d


subpos="90"	#By default subtitles are too low
subalign="2"

#always keep mplayer on top
ontop="1"

#turns off xscreen saver...maybe
stop-xscreensaver="yes"

#Some extra stuff I am currently not using....
#Fix A/V sync problems on files with bad MP3 VBR audio
#mc="1"
#autosync="10"
#delay="0.5"

#Updated 11/14/2005

```

In my opinion, if you watch a lot of dubbed/subtitled movies, nothing beats mplayer

---

### Post by ow50 on 2005-10-16
The best part about MPlayer is the superior subtitle rendering. And that needs to be configured.

Here's my ~/.mplayer/config
```
# * Experimental stuff

#======
# Video
#======

# Set video driver.
vo=xv

# Use double-buffering. (Recommended for xv with SUB/OSD usage)
double=yes

#======
# Audio
#======

# Set audio driver.
ao=alsa

# Set mixer channel
mixer-channel=Master

# Ajust volume differences. *
a52drc=1

# Fix A/V sync problems. *
mc=0.2
autosync=30


#==========
# Subtitles
#==========

# VobSubs
#========

# Align subs. (-1: as they want to align themselves)
spualign=-1

# Anti-alias subs. (4: best and slowest)
spuaa=4

# Set language.
slang=fi,fin,en,eng

# Text-based subtitles
#=====================

# Find subtitle files. (1: load all subs containing movie name)
sub-fuzziness=1

# Set font.
font=/home/osmo/.fonts/microsoft/vista/Calibri.ttf

# Set font encoding.
subfont-encoding=unicode

# Set subtitle file encoding.
unicode=yes
utf8=yes

# Resample the font alphamap. (1: narrow black outline)
ffactor=1

# Set subtitle position. (100: as low as possible)
subpos=100

# Set subtitle alignment at its position. (2: bottom)
subalign=2

# Set font size. (2: proportional to movie width)
subfont-autoscale=2

# Set font blur radius. (default: 2)
subfont-blur=2.0

# Set font outline thickness. (default: 2)
subfont-outline=2.0

# Set autoscale coefficient. (default: 5)
subfont-text-scale=4.4

# OSD
#====

# Set autoscale coefficient. (default: 6)
subfont-osd-scale=4.4

#===========
# Appearance
#===========

# Disable screensaver.
stop-xscreensaver=yes

# Position window. (50%:50%: center of screen)
geometry=50%:50%

# Skin
skin=Glider

```

I also use two python scripts, one for playing a movie with headphones and one for playing with 5.1 speakers. Those scripts handle the routing of the audio channels. Rather difficult to set up but very easy to use afterwards.

Edit 20060305:
Updated config file.

---

### Post by GrammatonCleric on 2005-10-16
I also find that mplayer's keyboard navigation rocks!

**_Mplayer Keyboard Navigation:_**

```


    * <- and -> seeks backward/forward 10 seconds 

    * up and down seeks backward/forward 1 minute 

    * pgup and pgdown seeks backward/forward 10 minutes 

    * < and > backward and forward in playlist 

    * p or spacebar pause / unpause 

    * q or ESC stop playing and quit 

    * / and * or 9 and 0 to decrease/increase volume 

    * m mutes sound 

    * # cycles through available audio tracks 

    * f toggles fullscreen (see also -fs) 

    * T toggles stay-on-top (see also -ontop) 

    * b and j toggles through available subtitles 

[edit]
General Playback Options

Once again, these are only a few of the many options available that most people might be looking for. See the MAN page for more details. Almost all of these descriptions are taken straight from the man.

    * -quiet to display less console output 

    * -v or -verbose to display more console output 

    * -loop <number> loops movie playback <number> times. 0 means forever. 

    * -playlist <filename> plays a filelist. May be required for some streaming video. 

    * -cache <kBytes> sets "how much memory (in kBytes) to use when precaching a file or URL. Especially useful on slow media." 

    * -cache-min <percentage> - "Playback will start when the cache has been filled up to <percentage> of the total." 

    * -channels <number> changes the number of playback channels. See the man for a lengthier explanation on how this one works. 

    *
          o 2 - stereo (default)
          o 4 - surround
          o 6 - full 5.1 

    * -forceidx - "Force index rebuilding. Useful for files with broken index (A/V desync, etc). This will enable seeking in files where seeking was not possible." 

    * -srate <Hz> - "Selects the output sample rate to be used (of course sound cards have limits on this)." 

    * -ss <time> - "Seek to given time position." In other words, starts playback at the specified time index. 

mplayer movie.avi -ss 56

Seeks to 56 seconds: 
 
mplayer movie.avi -ss 01:10:00

seeks to 1 hour 10 minutes:


```

GC

---

### Post by pizzach on 2005-10-17
Hehe. I actually started this thread hoping to be able to read other people's config files and get ideas.  I don't thing there are any other's on the forum and example documentation is hard to find.  Though one more so far is still more than I expected for a "newbie os." :)

That and maybe some other ubuntu users would get brave to try mplayer for what it is really worth.  You don't use mplayer like totem or vlc respectively.  Or like any windows/macinosh movie player respectively.

I didn't have so much luck with these:
a52drc=1
mc=0x
I've found in general mplayer's general settings roughly shoot right.  Or I can use "+" or "-" to align the audio.  It's too bad audio is so complicated.

PLEASE.  IF YOU USE MPLAYER POST YOUR  CONFIG FILE.  Really. :) Right now I'm once again wishing firefox didn't impliment backspace as back life stupid firefoix does. :)  :)   :)

I'm drunk right now.  So don't shoot me for my post please.  :)windows r

---

### Post by pizzach on 2005-10-18
Kinda of sad, but after playing for a while.  I find the best way to way to realign audio is by "-" or "+" when the movie is playing.  I haven't found a movie where after realigning it about 200ms-300ms in either direction.  Other methods seem to only kind of realign the audio.  It's better at some times and not so better at others.  I'm sure I'll figure it out eventually.  :)

---

### Post by sherz on 2005-11-02
Hi,

how can I can say that e.g. the streams in a special folder saved instead in a tmp folder.

I did this changes in a config-file on my first ubuntu installation but I cant remember where.

sherz

---

### Post by sherz on 2005-11-09
[QUOTE=sherz]Hi,

how can I can say that e.g. the streams in a special folder saved instead in a tmp folder.

I did this changes in a config-file on my first ubuntu installation but I cant remember where.

sherz[/QUOTE]


No Ideas ?

---

### Post by Caboto on 2005-11-09
If your using the MPlayer Plug-In do the following steps.

1. Fire up a Terminal and type (or paste):
```
sudo gedit /etc/mplayerplug-in.conf
```
2. Add the following lines at the end:
```
download=1
dload-dir=$HOME/downloads/trailer
keep-download=1
```
Replace *$HOME/downloads/trailer* with a folder of your choice. For the whole thing to work, this folder needs to exists. So go ahead and create it first.

---

### Post by sherz on 2005-11-11
[QUOTE=Caboto]If your using the MPlayer Plug-In do the following steps.

1. Fire up a Terminal and type (or paste):
```
sudo gedit /etc/mplayerplug-in.conf
```
2. Add the following lines at the end:
```
download=1
dload-dir=$HOME/downloads/trailer
keep-download=1
```
Replace *$HOME/downloads/trailer* with a folder of your choice. For the whole thing to work, this folder needs to exists. So go ahead and create it first.[/QUOTE]

Yeah thanks exactly !!

Stephan

---

### Post by sup on 2006-03-04
would ther ebe any way to make mplayer load all subtitle files that are in the same folder as the movie itself?

from command line, it is possible to use 
```
mplayer movie_name.mkv -subfile "*.srt"
```
but when I try to add something like subfile=*.srt to .mplayer/config, it gives this then:
```
Playing Elephant.avi.
File not found: '~/*.srt'
Failed to open ~/*.srt
Cannot open subtitle stream: ~/*.srt


Exiting... (End of file)
```
any ideas?

---

### Post by ow50 on 2006-03-04
[QUOTE=sup]would ther ebe any way to make mplayer load all subtitle files that are in the same folder as the movie itself?[/QUOTE]
From the man pages
```
       -sub-fuzziness <mode>
              Adjust matching fuzziness when searching for subtitles:
                 0    exact match
                 1    Load all subs containing movie name.
                 2    Load all subs in the current directory.
```
So for your config file, add line
```
sub-fuzziness=2
```

---

### Post by sup on 2006-03-05
nice, thanks, I checked the documentation on mplayer homepage but did not look into the manpages (they are far too large...)

---

### Post by Gandalf on 2006-03-05
Anyone knows how to make **g**mplayer have one and only one instance at a time? i mean whne i play clips, I always have to close the current mplayer, Double click on the next clip and adjust manually again the windows size and make it on top, it's kinda annoying, i like totem because in gconf i can make it on top at launch, also when i hide the controls and adjust it it will always stay the same for all files... i like mplayer options but i dislike the way double clicking a file act :s

Thx

---

### Post by sup on 2006-03-05
I do not know if this helps you, but when you start both gmplayer and mplayer, you can rise a playlist by pressing "p", there you could queu up songs you want to play, then?

---

### Post by ow50 on 2006-03-05
[QUOTE=Gandalf]Anyone knows how to make **g**mplayer have one and only one instance at a time? i mean whne i play clips, I always have to close the current mplayer, Double click on the next clip and adjust manually again the windows size and make it on top, it's kinda annoying,[/QUOTE]
I don't think single-instance is possible. You can take a look at MPlayer's -ontop, -zoom, -vf scale and -geometry options. I'm sure something should accomplish your needs. I only use geometry=50%:50% myself, so I'm not familiar with the rest. There's alot of options for scaling and zooming and such, I don't which would work best.

---

### Post by st0necol on 2006-03-16
Is there any lines to be added for proxy support ? I use mplayerplug-in in firefox but it doesn't plays the movie...and doesn't read the proxy settings of firefox.

---

### Post by sYs^ on 2006-03-17
Hi!

how can i change the subtitles font size in gmplayer?

```
Warning unknown option subfont-autoscale at line 11
Warning unknown option subfont-text-scale at line 12
Warning unknown option subfont-encoding at line 14
```

these setting didn't work :\

and i didn't find any options about this in the GUI

thanks...


Edit: Problem resolved, copied some other sized fonts to /usr/local/share/mplayer/font

---

### Post by pizzach on 2006-03-20
[QUOTE=sup]nice, thanks, I checked the documentation on mplayer homepage but did not look into the manpages (they are far too large...)[/QUOTE]


The key is to search for the important word.  When in the terminal you type "/" to start a search then just press enter.  To flip through them you use n or enter.  I don't remember.  Capital N goes in the oposite direction.

On days I lose all of my informatino on my computer I am thankful for having started this thread and keeping the config file up to date.  This case would be where I jsut got a new computer to replace my stolen one.  Don't wanna build that big thing again...

---

### Post by ow50 on 2006-03-20
For those who find browsing the huge mplayer man pages at terminal to be difficult, remember that there's a multitude of ways to read man pages. In addition to the terminal, you can read man pages as HTML online, use Yelp (which is slow), copy the man page to a text file or use some text editor plugin. I use a man page plugin for Vim myself, which makes reading and searching man pages a lot nicer.

Here's a screenshot of vim7 (from CVS) reading the mplayer man page.
[[IMG]http://img47.imageshack.us/img47/444/manmplayer5gz.th.png[/IMG]](http://img47.imageshack.us/my.php?image=manmplayer5gz.png)

---

### Post by Gandalf on 2007-03-16
> **Gandalf said:**
> Anyone knows how to make **g**mplayer have one and only one instance at a time? i mean whne i play clips, I always have to close the current mplayer, Double click on the next clip and adjust manually again the windows size and make it on top, it's kinda annoying, i like totem because in gconf i can make it on top at launch, also when i hide the controls and adjust it it will always stay the same for all files... i like mplayer options but i dislike the way double clicking a file act :s

Thx
Just to answer myself, I found the solution long ago...
[http://wael.nasreddine.com/files/configs/home/wael/bin/player](http://wael.nasreddine.com/files/configs/home/wael/bin/player) a wrapper for mplayer that takes care of that (not gmplayer though, I don't use gmplayer)

---

### Post by panch0 on 2007-03-16
There are also several frontends, some of them make sure only one MPlayer is running at a time. I know KPlayer does, because that is what I use for all my multimedia needs. KPlayer is a KDE program. As for an MPlayer config file, I don't have any! I configure everything through KPlayer. For things it doesn't yet support directly, there is Additional Command Line Parameters box.

---

### Post by kpkeerthi on 2007-03-16
Should I only run mplayer from command line to get it use the custom config file?

---

### Post by bedake on 2007-04-01
When using mplayer and while watching an mkv video, there are certain subtitles that are supposed to appear on the top of the screen parallel to subs on the bottom half of the screen, these are intended as an 'editor/translators' note, but mplayer displays them both on the bottom half making it a bit hard to read.

Is there any way to display the editor's note on the top part of the screen like they are supposed to be?

---

### Post by joebu23 on 2007-04-02
i need some help writing a config file for mplayer.  I would like mplayer to play specific files in specific displays.  I have two video cards and would like 1 clip, video1.mp4 to run in one set of monitors and video2.mp4 to run in the second two monitors.

any ideas, suggestions?

---

### Post by VuDu on 2007-04-09
subfont-encoding="unicode"
unicode="yes"


using this, I'm still not able to get mplayer to display my portuguese .srt's as it should.

não me lembro -> n_me lembro
vai matá-lo -> vai mat_o

and so on...

any help??

---

### Post by jocko on 2007-04-09
A few lines I use when I want to see a movie on my tv:

```
geometry=0%:0%
xy=1024
vf=expand=0:-100:50:50

```The first line will make sure the video window always opens in the upper left corner of the monitor.
The second line will resize the video to 1024 pixels wide, but keep the aspect ratio.
I clone my desktop (1600x1200) to my TV (1024x768), which results in the TV only showing part of my desktop.
This way the width of the video will always fit perfectly to the TV.
The third line will add 100 black lines, 50 above and 50 below, to fill up the rest of the TV
(if 100 is too much or too little, remember the numbers need to add up. e.g. 0:-150:75:75 or 0:-75:38:37. Too much will force part of the video window to go offscreen, which sometimes cause mplayer to freeze or stutter).

---

### Post by blueboy4 on 2007-08-25
> **jocko said:**
> A few lines I use when I want to see a movie on my tv:

```
geometry=0%:0%
xy=1024
vf=expand=0:-100:50:50

```The first line will make sure the video window always opens in the upper left corner of the monitor.
The second line will resize the video to 1024 pixels wide, but keep the aspect ratio.
I clone my desktop (1600x1200) to my TV (1024x768), which results in the TV only showing part of my desktop.
This way the width of the video will always fit perfectly to the TV.
The third line will add 100 black lines, 50 above and 50 below, to fill up the rest of the TV
(if 100 is too much or too little, remember the numbers need to add up. e.g. 0:-150:75:75 or 0:-75:38:37. Too much will force part of the video window to go offscreen, which sometimes cause mplayer to freeze or stutter).

I don't like black lines in my movie. I like it full screen like you see on tv. How do you do it then? What would be the calculations for that?

---

### Post by Jose Catre-Vandis on 2007-08-25
my config file is quite short but includes:

```
vop=pp=0x20077
cache=8192
```

used mainly for watching dvb tv and movies (avi)

another good post processing line is:
```
vop=pp=lb
```

---

### Post by blueboy4 on 2007-08-25
I found out what the scale is. I looked in Media Player Classic v6.4 by Gabest and it says that full screen video for tv mode is 16:9. That's what I use in that program. So my question is can Mplayer do 16:9? If so, how would you set it up in the config or can you do it in the settings of the program itself? :confused:

---

### Post by last1 on 2007-08-27
> **blueboy4 said:**
> I found out what the scale is. I looked in Media Player Classic v6.4 by Gabest and it says that full screen video for tv mode is 16:9. That's what I use in that program. So my question is can Mplayer do 16:9? If so, how would you set it up in the config or can you do it in the settings of the program itself? :confused:


In the config file, located at ~/.mplayer/config you should add the line 
monitoraspect="16:9"

---

### Post by blueboy4 on 2007-08-30
> **last1 said:**
> In the config file, located at ~/.mplayer/config you should add the line 
monitoraspect="16:9"

Thanks. But that area seems to be showing empty. Is there a way to create a default one then edit it later? :confused:

---

### Post by blueboy4 on 2007-08-30
Maybe I should rephrase my question since no one seems to understand what I am trying to say here. I want to make a widescreen movie, NTSC somehow in Mplayer. I've tried changing the aspect ratio, zooming, etc. Everything only resizes the Mplayer window but doesn't alter the movie size in anyway. It still has black around the movie. I want to get rid of all the black around the movie so it's all picture. Does anyone know how to do this or is it even possible to do? :confused:

---

### Post by blueboy4 on 2007-08-30
I made an example to show you what I mean:

[IMG]http://i93.photobucket.com/albums/l67/blueboy4/BlissWidescreen.png[/IMG]
**Widescreen**
[IMG]http://i93.photobucket.com/albums/l67/blueboy4/BlissNtsc.png[/IMG]
**NTSC**

---

### Post by jocko on 2007-08-30
Try adding this to your config. It will stretch all movies to a 4:3 aspect ratio:
```
aspect=4:3
```
Not that I see the point of stretching a 16:9 movie to 4:3... everything will be... stretched... But, you asked for it!:)

---

### Post by blueboy4 on 2007-08-30
> **jocko said:**
> Try adding this to your config. It will stretch all movies to a 4:3 aspect ratio:
```
aspect=4:3
```
Not that I see the point of stretching a 16:9 movie to 4:3... everything will be... stretched... But, you asked for it!:)

I tried 4:3 it still was widescreen. I found an option in Kaffeine where I use "Vertical Zoom In" and you can adjust it from 100% and up. I set it to 130% in it and it covered the whole screen perfectly.

---

### Post by pt123 on 2007-08-31
Is it possible to get the subtitle fonts to be in a yellow color, like in xine & totem?

Yellow subtitles are much easier to read.

---

### Post by pt123 on 2007-09-02
bump anyone?

---

### Post by n.aggel on 2007-09-03
> **pt123 said:**
> Is it possible to get the subtitle fonts to be in a yellow color, like in xine & totem?

Yellow subtitles are much easier to read.

yes , try this OSD/SUBTITLE option

```
 -***-color <value>
              Sets the color for text subtitles.  The color format is RRGGBBAA.
```

hope i helped!

PS:: where asterisks are insert word a.s.s without the dots!

PS2:: for more details check the man pages, they are super complete!

---

### Post by n.aggel on 2007-09-03
yellow rgb code::

```
 255 255 0 	ffff00	yellow
```

plus link with other codes [http://www.pitt.edu/~nisg/cis/web/cgi/rgb.html]("http://www.pitt.edu/~nisg/cis/web/cgi/rgb.html")

---

### Post by pt123 on 2007-09-04
Thanks but it is not working, most likely because of the color format
when i type

a$$-color=255 255 0

It gave me this error

extra characters on line 36: 255 0



a$$-color=2552550

no error but still in white

a$$-color=ffff00
no error but still in white

In the man pages it says The color format is RRGGBBAA.
as usual without a bloody example.

It looks like they are referring to hexadecimal

a$$-color=#ffff00
I get this error
Option ***-color needs a parameter at line 36


Is there a call to reset the config file.  Even when I comment out certain lines in the config file they are still coming out in the video.

I think the gui.conf overides the "config" file.

Anyway this is a bloody mess.  

I will stick with Totem, there has to be a reason why it is the default player.

---

### Post by n.aggel on 2007-09-06
sorry, i can't really help you brcause i haven't used this option myself....

from your post though it seems tha you must provide an alpha setting {RRGGBBAA}..maybe this creates all the problems....

i have some problems with mplayer myself (mainly with gui version)...but it is way suoerior than totem {IMHO}.....

---

### Post by philipho on 2007-09-11
Hi i have a question regarding playback,

During playback, when i press "f" for fullscreen, my video only occupies a small portion of the screen while the expanded border is black, how do i cause it to fill up the whole screen? 

Thanks for the help!

---

### Post by n.aggel on 2007-09-14
> **philipho said:**
> Hi i have a question regarding playback,

During playback, when i press "f" for fullscreen, my video only occupies a small portion of the screen while the expanded border is black, how do i cause it to fill up the whole screen? 

Thanks for the help!
the same thing happens to me, if run mplayer from the gui interface...if i run it from console , full sizing the image works like it should....

any ideas?

---

### Post by taisao on 2007-09-16
> **pt123 said:**
> Thanks but it is not working, most likely because of the color format
when i type

a$$-color=255 255 0

It gave me this error

extra characters on line 36: 255 0



a$$-color=2552550

no error but still in white

a$$-color=ffff00
no error but still in white

In the man pages it says The color format is RRGGBBAA.
as usual without a bloody example.

It looks like they are referring to hexadecimal

a$$-color=#ffff00
I get this error
Option ***-color needs a parameter at line 36


Is there a call to reset the config file.  Even when I comment out certain lines in the config file they are still coming out in the video.

I think the gui.conf overides the "config" file.

Anyway this is a bloody mess.  

I will stick with Totem, there has to be a reason why it is the default player.

You can use -***-color like this:
```
-***-color=ffff00ff
``` (that's how it works in when running mplayer from terminal with options)

---

### Post by bharani on 2007-09-18
hello,
             I have a problem with my mplayer...like whenever I am trying the equalizer while listening to mp3...particulariy the bass(left) part..it makes a horrible sound...would some body give a fix for this...help si most aprreciated

Bunny.

---

### Post by yoda-sama on 2007-10-11
it is amazing that an ultimate mplayer config file would leave out SSA/*** subtitle rendering support, which I believe is:

ass=1

Note that you will have to use a subversion build or one of the Mplayer 1.0 release candidates (or above, depending on when you're reading this) to support it.

---

### Post by Marinodimare on 2007-10-21
> **n.aggel said:**
> the same thing happens to me, if run mplayer from the gui interface...if i run it from console , full sizing the image works like it should....

any ideas?

Go to [FONT="Lucida Console"]/etc/mplayer[/FONT] in you terminal, then type [FONT="Lucida Console"]sudo nano mplayer.conf[/FONT], and uncomment the line [FONT="Lucida Console"]#zoom=yes[/FONT]

This should solve the problem, it did for me.

---

### Post by Marinodimare on 2007-10-21
Hi, does anyone know how to edit mouse commands? I'd like to toggle fullscreen mode by double-clicking the video window. Any ideas?

---

### Post by taisao on 2007-10-21
> **Marinodimare said:**
> Hi, does anyone know how to edit mouse commands? I'd like to toggle fullscreen mode by double-clicking the video window. Any ideas?

use SMplayer - [http://smplayer.sourceforge.net/en/linux/index.php](http://smplayer.sourceforge.net/en/linux/index.php)
> SMPlayer intends to be a complete front-end for MPlayer

---

### Post by Marinodimare on 2007-10-21
Related to another topic I posted - about Kaffeine giving crappy video output - smplayer gives crappy video output too, while mplayer videos look great. I don't how this can be - but it is. Sorry

---

### Post by rvm4000 on 2007-10-21
> **Marinodimare said:**
> smplayer gives crappy video output too, while mplayer videos look great. I don't how this can be - but it is. Sorry

What does "crappy" mean? Video-Audio sync problems? Bad quality image?

---

### Post by Marinodimare on 2007-10-22
Sorry - should heve been more specific. The problem is that the picture is 'blocky', or pixelized. It is most apparent when playing old Simpsons episodes which are not-so-good TV rips, but in high-quality movies the problem also occurs. In MPlayer the edges may be somewhat blurry (due to the kow quality rip), but they are smooth. In Kaffeine the edges are really pixelized. 

On another topic - is it possible to let Kaffeine use the MPlayer engine?

---

### Post by rvm4000 on 2007-10-22
Probably you're using in smplayer a different video output driver than mplayer. In preferences->general you can change it.

Or maybe you have postprocessing activated in mplayer (config file) but not in smplayer.

---

### Post by natrik on 2008-12-12
> **pizzach said:**
> Mplayer is da bomb.  But with a good config file it's much better.  Take a look at mine and try it!  Keep in mind, if you don't use mplayer from the terminal you don't know what you're emissing.  That and this config is for the terminal version.

... nothing beats mplayer

The gui version of mplayer "gmplayer" also uses options found in the ~/.mplayer/config file.  Some of the options you list in the config are also in the gui preferences, but cannot be set as explicitly as the config file allows.  

For example, the postprocessing option in gmplayer's "Preferences" screen is insufficient to set those options you mention (and thank you for bringing hqdn3d to my attention!).  Therefore I enable postprocessing in the gui and specify the options in the ~/.mplayer/config file.  If postprocessing is disabled (gui > Preferences > Misc) then no postprocessing will take effect, even when set explicitly in the config file or on the command line.  I'm sure this applies to other options as well.

One note though, your line "autoq" before the "vf=..." line would seem to have no effect.  The manpage states:  "You have to use &#8722;vf [s]pp without parameters in order for this to work."

-- Nate

EDIT: Oh yeah!  This hqdn3d is sweet!  It gets rid of the flicker which I know now is aggravated by the gui's postprocessing settings which I WAS using without understanding.  (gmplayer > preferences > Misc > postprocessing -- any level. )  It also seems to help the deblocking filter a bit.  Wow, this way is so much better.  Also, you can get interesting results with very high values of hqdn3d, for example hqdn3d=200:200:200 ... only useful for understanding what it does to the video, or maybe for creating effects.  I find **vf="hqdn3d=2:2:3,pp=ac"** provides me with nice results for reasonable quality anime encodes, smoothing "enough" while keeping detail intact.  Default is hqdn3d=4:3:6 if no options are specified.  That's lum:chrom:time.  And "pp=ac" is "high quality pp filter combination (ha:a:128:7,va:a,dr:a)" in the manpage.  The manpage btw, is your friend.  It requires patience though.

---

### Post by DeusEx on 2008-12-15
cheers mate! I edited the settings to fit my system:

(by the way this seems to work really wel in combination with compiz desktop effects enabled)

```

#General setup

really-quiet="1" #Very very little console output

zoom="1" #Allow sofware scaling if I use x11 for vo

#Display

double="yes"	#double buffering(recommended for subtitles)
framedrop="1"	# For slow machines
hardframedrop="0"  #Make sure hard frame drop is off but can turn on easily now

#subtitle code
#Truetype fonts rock! (sudo apt-get msttcorefonts)
font=/usr/share/fonts/truetype/msttcorefonts/impact.ttf

ffactor="10" #black outline
sub-bg-alpha="0" #background color ala closed captions
sub-bg-color="0" #black to white
subfont-text-scale="1.7"	#truetype font scaling
subfont-blur="1" #Slight blur

#This sets the postprocessing into overdrive using all possible spare cpu cycles to make the movie look better
autoq=100
vf=pp=de,hqdn3d


subpos="90"	#By default subtitles are too low
subalign="2"

#always keep mplayer on top
ontop="1"

#turns off xscreen saver...maybe
stop-xscreensaver="yes"

```

---

### Post by IgnorantGuru on 2008-12-20
Thanks for the good ideas here.  I agree mplayer is very capable from the command line and using the keyboard controls.

I wrote a script that does a bunch of things with mplayer including allowing resume and turning off the KDE screensaver.  When I play a file I like it to resume right where I last played it - just as if I put a VCR tape on the shelf.  You can check it out here...
[http://ubuntuforums.org/showthread.php?t=805369](http://ubuntuforums.org/showthread.php?t=805369)

---

### Post by Northern Man on 2009-01-27
I have a small tweak to this config, that may or may not help some people.  After implementing this config, along with digital audio (SPDIF) I spent  days chasing down an intermittent momentary pause in the audio track, while the video appears to keep running.  You could describe it as a stutter.  It would just occur at random intervals during playback, of various types of content.  During playback CPU would stay low, usually in the 30% range.

I found that setting hardframedrop to a 1 resolved the issue

hardframedrop="1"  #Make sure hard frame drop is off but can turn on easily now

---

### Post by cycle_mycle on 2009-04-22
Is there any way to get the EQ settings to stay the way I like them? I don't understand why MPlayer doesn't do that by default...

Maybe I should post on "Absolute Beginners" but...

---

### Post by abumaia on 2010-04-16
I watch primarily mkv's, most of which are dual-audio with multiple subtitles.  Not every mkv is set up the same, however.  Most of the mkv's have two sets of "slang eng" subtitles, rendering the slang setting impotent.  In one directory I need to display the sid 1 subtitles, while in another directory it's the sid 0 subtitles I need.  I see in the man pages that per-directory config files are possible, but I haven't yet been able to get it to work.

In my /etc/mplayer/mplayer.conf file, I have this:
> slang = eng,en
alang = jpn,ja,eng,en
use-filedir-conf = yesIn one of my mkv directories, I have another mplayer.conf file with just "sid=1".

However, when I play one of the mkv's in that directory, the subtitle setting isn't followed correctly.  What have I set up wrong?  How can I get per-directory configurations to work?

---

### Post by firekage on 2012-07-11
Hi.

I have one question regarding smplayer. I placed in ~/.mplayer/config this:

```
vo="vdpau" #video out
```

but it still uses xv. Could you tell me why it runs on xv despite the fact that i placed this above into mplayer config file? Why choosed settings in smplayer done by gui are more important than those placed by terminal in config file?

Because of this, with new driver (everything with binary driver and ppa doesen't work, causes to log off) my Ubuntu 11.10 and 12.04 logs off when using all players to watch movies.

Can you help me?

---

