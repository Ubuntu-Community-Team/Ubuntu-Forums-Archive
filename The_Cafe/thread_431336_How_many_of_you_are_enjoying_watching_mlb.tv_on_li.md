---
title: "How many of you are enjoying watching mlb.tv on linux"
date: 2007-05-02
forum: The Cafe
---

### Post by lbyrd33 on 2007-05-02
Over the last 3 years, one of the biggest things that I tried to get to work was watching mlb.tv on linux. I am now on my 2nd season using mplayer and I am having a blast watching the mets on their road to the world series. Next we need to figure out how to get mlb mosaic to work.

---

### Post by Mateo on 2007-05-03
so does it use mplayer in the browser?  the plugin?

---

### Post by lbyrd33 on 2007-05-03
Yeh, it uses in the browser plugin. The biggest problem that I observed was that websites like espn.com and mlb.com use a web browser window that needs both a mpeg player plugin and a flash player plugin. However, the firefox or any browser would be able to load up the flash plugin and then stop, thinking it had already done its job.

---

### Post by JAPrufrock on 2007-05-03
Nope, because my DSL isn't quite fast enough.  However, I do listen to MLB audio.  I needed to install mplayer and flash in order to be able to listen to it.

---

### Post by tomlyn on 2007-05-04
> **lbyrd33 said:**
> Over the last 3 years, one of the biggest things that I tried to get to work was watching mlb.tv on linux. I am now on my 2nd season using mplayer and I am having a blast watching the mets on their road to the world series. Next we need to figure out how to get [COLOR="Red"]mlb mosaic[/COLOR] to work.

Hello,

By "mlb mosaic" do you mean those short free game high-light videos?
Any progress in making them work?

Thanks.

Another Mets fan in Hong Kong :)

---

### Post by lbyrd33 on 2007-05-04
> **tomlyn said:**
> Hello,

By "mlb mosaic" do you mean those short free game high-light videos?
Any progress in making them work?

Thanks.

Another Mets fan in Hong Kong :)

No, mlb mosaic is the program they now offer from mlb.com with subscription where you can have all the games going on at one time and choose which one you want to watch in real time. To watch the highlights or anything else you need to have mplayer installed properly as well as macromedia flash. Let me know if you need some help.

---

### Post by tomlyn on 2007-05-05
> **lbyrd33 said:**
> No, mlb mosaic is the program they now offer from mlb.com with subscription where you can have all the games going on at one time and choose which one you want to watch in real time. To watch the highlights or anything else you need to have mplayer installed properly as well as macromedia flash. Let me know if you need some help.

Thank you lbyrd33,

I do appreciate if you can help!

I am using Feisty, which was upgraded from 6.10, I did not do clean install. There was no problem in upgrading.

I use Synaptic to manage all my packages. I have installed mplayer, mozilla-mplayer, flashplugin-nonfree. Using the Feisty automatic codec installation, I have installed lots of codecs, so that I can listen to mp3, and watch lots of avi files. 

But I still can not watch the MLB highlight video clips. What's missing in my install? 


Thank you.


Following is "about:plugins" result of my firefox. (sorry the format is lost when copy-paste)
--------------------------------------------------------------------------

**[CENTER][SIZE="3"]Installed plug-ins[/SIZE][/CENTER]**
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.


**Windows Media Player Plugin**

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
audio/x-ms-wmv 	Windows Media 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes


**Windows Media Player Plug-in 10 (compatible; Totem)**

    File name: libtotem-gmp-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
video/x-ms-wvx 	Playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes


**Shockwave Flash**

    File name: libflashplayer.so
    Shockwave Flash 9.0 r31

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes


**Totem Web Browser Plugin 2.18.1**

    File name: libtotem-basic-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes


**DivX® Web Player**

    File name: libtotem-mully-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes


**QuickTime Plug-in 7.1.3**

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes


**QuickTime Plug-in 6.0 / 7**

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes


**RealPlayer 9**

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes

[B]
mplayerplug-in 3.31[/B]

    File name: mplayerplug-in.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpegurl 	MPEG url 	m3u 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes


**Java(TM) Plug-in 1.6.0-b105**

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6 	Java 		Yes

---

### Post by lbyrd33 on 2007-05-05
> **tomlyn said:**
> Thank you lbyrd33,

I do appreciate if you can help!

I am using Feisty, which was upgraded from 6.10, I did not do clean install. There was no problem in upgrading.

I use Synaptic to manage all my packages. I have installed mplayer, mozilla-mplayer, flashplugin-nonfree. Using the Feisty automatic codec installation, I have installed lots of codecs, so that I can listen to mp3, and watch lots of avi files. 

But I still can not watch the MLB highlight video clips. What's missing in my install? 


Thank you.

Could you post your /etc/mplayer.conf file. Also, could you describe to me what happens when you open up the highlight browser. Just a blank screen or whatever you observe.

---

### Post by jarvis13 on 2007-05-05
I only watch one team and I get all the televised games anyways.

GO REDLEGS!

---

### Post by tomlyn on 2007-05-05
> **lbyrd33 said:**
> Could you post your /etc/mplayer.conf file. Also, could you describe to me what happens when you open up the highlight browser. Just a blank screen or whatever you observe.

I don't have /etc/mplayer.conf, but I have instead /etc/mplayer/mplayer.conf, should I move it up? You can find my /etc/mplayer/mplayer.conf below, it is the standard mplayer.conf file coming with the package.

When I click the video, the player window quickly (less than 0.2 sec) flashed a picture, then turns black. On bottom, it shows "Stopped: 0:00/0:00"

Thanks.

----------------- /etc/mplayer/mplayer.conf ------------------------
#
# MPlayer configuration file
#
# Configuration files are read system-wide from /usr/local/etc/mplayer.conf
# and per user from ~/.mplayer/config, where per-user settings override
# system-wide settings, all of which are overrriden by the command line.
#
# The configuration file settings are the same as the command line
# options without the preceding '-'.
#
# See the CONFIGURATION FILES section in the man page
# for a detailed description of the syntax.


##################
# video settings #
##################

# Specify default video driver (see -vo help for a list).
#vo=xv

# Use SDL video with the aalib subdriver by default.
#vo = sdl:aalib

# FBdev driver:
#
# mode to use (read from fb.modes)
#fbmode = 640x480-120
#
# location of the fb.modes file
#fbmodeconfig = /etc/fb.modes

# Specify your monitor timings for the vesa and fbdev video output drivers.
# See /etc/X11/XF86Config for timings. Be careful; if you specify settings
# that exceed the capabilities of your monitor, you may damage it.
#
# horizontal frequency range (k stands for 1000)
#monitor-hfreq = 31.5k-50k,70k
#
# vertical frequency range
#monitor-vfreq = 50-90
#
# dotclock (or pixelclock) range (m stands for 1000000)
#monitor-dotclock = 30M-300M

# Start in fullscreen mode by default.
#fs=yes

# Change to a different videomode when going fullscreen.
#vm=yes

# Override the autodetected color depth, may need 'vm=yes' as well.
#bpp=0

# Enable software scaling (powerful CPU needed) for video output
# drivers that do not support hardware scaling.
#zoom=yes

# standard monitor size, with square pixels
#monitoraspect=4:3

# Use this for a widescreen monitor, non-square pixels.
#monitoraspect=16:9

# Keep the player window on top of all other windows.
#ontop=yes


##################
# audio settings #
##################

# Specify default audio driver (see -ao help for a list).
ao=alsa,

# Use SDL audio driver with the esd subdriver by default.
#ao = sdl:esd

# Specify the mixer device.
#mixer = /dev/mixer

# Resample the sound to 44100Hz with the lavcresample audio filter.
#af=lavcresample=44100

# Specify default audio codec (see -ac help for a list).
ac=mad,


##################
# other settings #
##################

# Drop frames to preserve audio/video sync.
#framedrop = yes

# Specify your preferred skin here (skins are searched for in
# /usr/local/share/mplayer/skins/<name> and ~/.mplayer/skins/<name>).
#skin = Abyss

# Resample the font alphamap.
# 0     plain white fonts
# 0.75  very narrow black outline (default)
# 1     narrow black outline
# 10    bold black outline
#ffactor = 0.75

# cache settings
#
# Use 8MB input cache by default.
#cache = 8192
#
# Prefill 20% of the cache before starting playback.
#cache-min = 20.0
#
# Prefill 50% of the cache before restarting playback after the cache emptied.
#cache-seek-min = 50

# DVD: Display English subtitles if available.
#slang = en

# DVD: Play English audio tracks if available.
#alang = en


# You can also include other configuration files.
#include = /path/to/the/file/you/want/to/include

---

### Post by Baldy18 on 2007-05-06
hey guys i'm a noob here but I'm loving feisty fawn.  Only problem I'm having is on cubs.mlb.com I'm able to view the short video clips but the window that is there when there is no clip shows nothing.  Initially whe the page loads the upcoming games and starting pictures displays briefly and then disapears also quickly.  Sorry to step on this thread but I felt it was related to the topic.

---

### Post by mrgnash on 2007-05-06
Not me. I think the broadcast of spectator sports is a pox.

---

### Post by igknighted on 2007-05-06
> **lbyrd33 said:**
> I am now on my 2nd season using mplayer and I am having a blast watching the mets on their road to the world series.

HA, you wish! :-P

---

### Post by tomlyn on 2007-05-06
Hi lbyrd33,

I have attached the screen shot of what my MLB video playing window. As has said before, it never get to play the video. 

Thank you very much.

---

### Post by lbyrd33 on 2007-05-06
> **tomlyn said:**
> Hi lbyrd33,

I have attached the screen shot of what my MLB video playing window. As has said before, it never get to play the video. 

Thank you very much.

Ill try to get back to you later today, I am at work and I forgot my laptop.

---

### Post by lbyrd33 on 2007-05-06
> **mrgnash said:**
> Not me. I think the broadcast of spectator sports is a pox.

Why?

---

### Post by lbyrd33 on 2007-05-06
> **igknighted said:**
> HA, you wish! :-P

Your braves are looking pretty good this year and I cant do any trash talking since they are winning the season series against the mets so far....so far!

---

### Post by darweth on 2007-05-06
Big time Mets fan here!  ;)  Though I prefer watching AL baseball in general, where I root for the Red Sox.  Also have a soft spot for the Athletics and Twins.  Got tickets to Oakland vs NY @ Shea June 22nd baby!

I watch most Mets games + many select AL games.  Pretty much ignore the rest of the NL.

---

### Post by Kingsley on 2007-05-06
Is that stuff free?

---

### Post by darweth on 2007-05-06
> **Kingsley said:**
> Is that stuff free?

No.

---

### Post by tomlyn on 2007-05-07
> **lbyrd33 said:**
> Ill try to get back to you later today, I am at work and I forgot my laptop.

Hi lbyrd33,

Thank you very much for your time and willingness.

I have been making progress, although still can not solved the problem yet.

I found this website
[http://zerlinna.blogweb.de/archives/73-Watching-Video-streams-mms-and-rtsp-protocol.html]("http://zerlinna.blogweb.de/archives/73-Watching-Video-streams-mms-and-rtsp-protocol.html")
and followed the instruction.

What I did was: 
(1) add into firefox config: 
 network.protocol-handler.app.mms = /usr/bin/mplayer
 network.protocol-handler.external.mms = true
(2) I have been able to find out that previously it is totem that was trying to open mms stream. I have uninstalled totem-plugin.
(3) set "debug=2" in /etc/mplayerplug-in.conf

Now when I click on the video, mplayerplug-in gets called, and in subsequence, the following messages are flashed. (I could not get the first message, since it is too fast)
(1)
(2) buffering mms://  ...
(3) connected
(4) buffering mmst:// ...
(5) connecting ...
(6) buffering http:// ...
(7) stopped

There is no any video or sound during this process, and the final screen is attached in this post.

Again, I have pretty much very standard Feisty installation. 

I appreciate anyone who could help me. Thank you for considering this problem.

---

### Post by tomlyn on 2007-05-07
Ahha, SILLY me, I got it working now! :-P

The only thing I need to do from my last post is to click the "play" button. :oops:

Thank you lbyrd33, without your encouraging, I would not even want to dive into this. Now I don't need to carry my windows laptop to work any more :-$

---

### Post by lbyrd33 on 2007-05-08
> **tomlyn said:**
> Ahha, SILLY me, I got it working now! :-P

The only thing I need to do from my last post is to click the "play" button. :oops:

Thank you lbyrd33, without your encouraging, I would not even want to dive into this. Now I don't need to carry my windows laptop to work any more :-$

Congratulations. If you are having any problems getting to go to full screen you can add this line to your mplayerplug-in.conf file:

zoom=yes

Also, if you still want to have totem installed but you will not need since you have mplayer working is to add the following line to your mplayerplug-in.conf file:

noembed=1

This will give mplayer preference to open up over totem. Im pretty sure these variables are right as I am not at my computer right now but you can go check them on the forums because that is where I figured everything out.

---

### Post by lbyrd33 on 2007-05-10
I guess most linux users dont like baseball! I guess this could be a generalization.

---

### Post by trippinnik on 2007-05-13
Has anyone had any luck playing archive games?  I am living out here in Japan and the blackout everything.  I am able to view live clips, but the archives always play the intro over and over and over... it's killing me.  I was up until   4 am listening to the mets get destroyed last night.. ugh.. anyway has anyone had any luck with this?  So far I have had the best luck using totem-xine plugin, but also vlc.  Mplayer didn't seem to work too well.

---

### Post by lbyrd33 on 2007-05-14
Ive been able to play the archived games, and I noticed that they play that intro thing for like 30 or so minutes. Unlike using windows, I have never been able to fastforward to a different part of any media in my web browser using linux.

---

### Post by olinbg on 2007-05-15
> **lbyrd33 said:**
> Ive been able to play the archived games, and I noticed that they play that intro thing for like 30 or so minutes. Unlike using windows, I have never been able to fastforward to a different part of any media in my web browser using linux.
This seems like a problem that could be fixed.  Anyone have any more insight into why you can't skip around in streaming media on linux vs. windows?

---

### Post by gregalynch on 2007-05-16
I have the exact same problem with the site.  Go cubs.

---

### Post by gregalynch on 2007-05-16
> **JAPrufrock said:**
> Nope, because my DSL isn't quite fast enough.  However, I do listen to MLB audio.  I needed to install mplayer and flash in order to be able to listen to it.

Prufrock, what plugin are you using to listen to gameday audio?  I just signed up yesterday and I can't get it to play (I'm currently using the mplayer plugin for firefox)?  

Also, great screenname.  'I have heard the mermaids singing, each to each, but I do not think they will sing for me.'

---

### Post by synonymous on 2007-05-16
I have had good success using 'MediaPlayerConnectivity' as an add-on along with VLC. VLC  will allow you to seek through archived streams. I posted my method on google last night. Firefox crashes at times while navigating and selecting media however.

Watching Cubs/Mets right now, this kiks ***, now I'm totally unproductive.

---

