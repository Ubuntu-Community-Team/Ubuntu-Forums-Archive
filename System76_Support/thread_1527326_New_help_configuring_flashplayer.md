---
title: "New help configuring flashplayer"
date: 2010-07-09
forum: System76 Support
---

### Post by volkerbradley on 2010-07-09
Just went to [http://www.linuxjournal.com/video](http://www.linuxjournal.com/video) to view some their videos.
Unfortunately, nothing happens when click on the play button.
How can I determine what is causing this behavior?
I am using Firefox 3.6.6 and Flashplayer version 10.1 r53
The following plugins are installed:

```
Shockwave Flash

    File: npwrapper.libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
DjVuLibre-3.5.22

    File: nsdejavu.so
    Version: 
    This is the DjVuLibre-3.5.22 version of the DjVu plugin.
    See DjVuLibre.

MIME Type 	Description 	Suffixes 	Enabled
image/x-djvu 	DjVu File 	djvu,djv 	Yes
image/x.djvu 	DjVu File 		Yes
image/djvu 	DjVu File 		Yes
image/x-dejavu 	DjVu File 		Yes
image/x-iw44 	DjVu File 		Yes
image/vnd.djvu 	DjVu File 		Yes
DivX Browser Plug-In

    File: gecko-mediaplayer-dvx.so
    Version: 
    Gecko Media Player 0.9.9.2

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	DivX Media Format 	divx 	Yes
video/vnd.divx 	DivX Media Format 	divx 	Yes
QuickTime Plug-in 7.6.4

    File: gecko-mediaplayer-qt.so
    Version: 
    Gecko Media Player 0.9.9.2

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
RealPlayer 9

    File: gecko-mediaplayer-rm.so
    Version: 
    Gecko Media Player 0.9.9.2

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
Windows Media Player Plug-in

    File: gecko-mediaplayer-wmp.so
    Version: 
    Gecko Media Player 0.9.9.2

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-asx 	Media Files 	asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
audio/x-ms-wmv 	Windows Media 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
application/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes
mplayerplug-in is now gecko-mediaplayer 0.9.9.2

    File: gecko-mediaplayer.so
    Version: 
    Gecko Media Player 0.9.9.2

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type 	Description 	Suffixes 	Enabled
audio/x-mpegurl 	MPEG Playlist 	m3u 	Yes
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
audio/mp4 	MPEG 4 audio 	mp4 	Yes
audio/x-mp4 	MPEG 4 audio 	mp4 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
video/x-m4v 	MPEG 4 Video 	m4v 	Yes
video/3gpp 	MPEG 4 Video 	mp4,3gp 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpegurl 	MPEG url 	m3u 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg,oga,ogm 	Yes
application/ogg 	Ogg Vorbis Media 	ogg,oga,ogm 	Yes
audio/x-ogg 	Ogg Vorbis Audio 	ogg,oga 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg,oga 	Yes
video/x-ogg 	Ogg Vorbis Video 	ogg,ogm 	Yes
video/ogg 	Ogg Vorbis Video 	ogg,ogm 	Yes
application/x-vlc-plugin 	VLC plug-in 	vlc 	Yes
application/x-google-vlc-plugin 	Google VLC plug-in 		Yes
audio/flac 	FLAC Audio 	flac 	Yes
audio/x-flac 	FLAC Audio 	flac 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/x-flv 	Flash Video 	flv 	Yes
video/flv 	Flash Video 	flv 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
audio/x-matroska 	Matroska Audio 	mka 	Yes
video/x-matroska 	Matroska Video 	mkv 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/x-aiff 	AIFF Audio 	aif 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes
audio/midi 	MIDI Audio 	mid,midi,kar 	Yes
audio/x-scpls 	Shoutcast Playlist 	pls 	Yes
video/x-mng 	Multiple-Image Network Graphics 	mng 	Yes
IcedTea NPR Web Browser Plugin (using IcedTea6 1.8 (6b18-1.8-0ubuntu1))

    File: IcedTeaPlugin.so
    Version: 
    The IcedTea NPR Web Browser Plugin (using IcedTea6 1.8 (6b18-1.8-0ubuntu1)) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.6.0_18 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.6.0_18 	IcedTea 	class,jar 	Yes
VLC Multimedia Plugin (compatible Totem 2.30.2)

    File: libtotem-cone-plugin.so
    Version: 
    The Totem 2.30.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-vlc-plugin 	VLC Multimedia Plugin 		Yes
application/vlc 	VLC Multimedia Plugin 		Yes
video/x-google-vlc-plugin 	VLC Multimedia Plugin 		Yes
application/x-ogg 	Ogg multimedia file 	ogg 	Yes
application/ogg 	Ogg multimedia file 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	Annodex exchange format 	anx 	Yes
audio/annodex 	Annodex Audio 	axa 	Yes
video/annodex 	Annodex Video 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
application/x-totem-plugin 	Totem Multimedia plugin 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File: libtotem-gmp-plugin.so
    Version: 
    The Totem 2.30.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Windows Media video 	wmv 	Yes
video/x-ms-wm 	Windows Media video 	wmv 	Yes
video/x-ms-wmp 	Windows Media video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/x-ms-wmp 	Windows Media video 	wmp 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File: libtotem-mully-plugin.so
    Version: 
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.6.6

    File: libtotem-narrowspace-plugin.so
    Version: 
    The Totem 2.30.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
iTunes Application Detector

    File: librhythmbox-itms-detection-plugin.so
    Version: 
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
Adobe Reader 9.3

    File: npwrapper.nppdf.so
    Version: 
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser. 

MIME Type 	Description 	Suffixes 	Enabled
application/pdf 	Portable Document Format 	pdf 	Yes
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Yes
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Yes
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Yes
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Yes

```
Thanks for looking at this.

---

### Post by thomasaaron on 2010-07-09
Please go to System > Prefs > Appearance > Visual Effects and select "None."

Does that make it work?

---

### Post by volkerbradley on 2010-07-09
Wow.  That was quick.  It works now.
Thank you very much.

---

### Post by garvinrick4 on 2010-07-09
volkerbradley
High light the whole post and then click # sign and will scroll instead of being
so long.

---

### Post by Cavsfan on 2010-07-09
> **thomasaaron said:**
> Please go to System > Prefs > Appearance > Visual Effects and select "None."

Does that make it work?

Yes, but no visual effects? Maybe this will help:

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: "export GDK_NATIVE_WINDOWS=1" before the last line of text
(without the quotes)

Restart browser, turn visual effects back on  and try it again.

I had to do this for any buttons to work on youtube.

I like my visual effects.

---

### Post by zitch on 2010-07-09
And make sure that is entered as the **second-to-last** line, this is what that file looks like for me now:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
[COLOR="Red"]export GDK_NATIVE_WINDOWS=1[/COLOR]
. /usr/lib/nspluginwrapper/noarch/npviewer

```

I kept miss reading "before the last line" and putting the export as the last line... :)  Hopefully, this saves someone else some frustrations...

---

### Post by Cavsfan on 2010-07-10
Is there an echo in here??? :-s

---

### Post by volkerbradley on 2010-07-10
Yes, that works very well.  It's great to keep the visual effects and see shockwave-flash videos.
Thank you

---

### Post by Cavsfan on 2010-07-10
> **volkerbradley said:**
> Yes, that works very well.  It's great to keep the visual effects and see shockwave-flash videos.
Thank you

Glad it helped you! Who wants to give up special effects because of flash?
I have a nice Compiz cube going on and a lot of other things like fire, etc. which I like to show off.
And I can watch 1080p flash in full screen too!

---

### Post by volkerbradley on 2010-07-11
> **garvinrick4 said:**
> volkerbradley
High light the whole post and then click # sign and will scroll instead of being
so long.

I've read these instructions, but for the life of me cannot figure out what you are trying to teach me.
Can you give me an example and give me the instructions step-by-step?

---

### Post by Cavsfan on 2010-07-11
> **volkerbradley said:**
> I've read these instructions, but for the life of me cannot figure out what you are trying to teach me.
Can you give me an example and give me the instructions step-by-step?

```
[COLOR=Blue]He is talking about wrapping CODE around that long string of text in your first post. [/COLOR] 
```[COLOR=Blue]He is talking about wrapping CODE around that long string of text in  your first post. [/COLOR](see this above?)
Edit and highlight the whole section of text about your plugins on your first post and then click on the "#" sign 
at the top of the box. It will wrap CODE around the text that will shorten the amount of space your post takes up. 
You want to do this whenever you are posting a lot of data. It creates a scrollable window that takes up less room 
for the display of a lot of data in a post.

---

### Post by samalex on 2010-07-12
> **Cavsfan said:**
> Yes, but no visual effects? Maybe this will help:

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: "export GDK_NATIVE_WINDOWS=1" before the last line of text
(without the quotes)

Restart browser, turn visual effects back on  and try it again.

I had to do this for any buttons to work on youtube.

I like my visual effects.

I've heard a few people suggesting this change, but what does it do?  I haven't had any major problems with Flash since installing 64-bit 10.04 on my PanP5, but I made this change in npviewer none the less to maybe fix some potential problems.  But what does it do exactly?  Just curious.

Sam

---

### Post by volkerbradley on 2010-07-12
I don't really know what all it does.  In my case, I could watch Flash videos but not Shockwave Flash videos.  When I added this line, the Shockwave-Flash videos started to play and I continue to have the features of compiz.

---

### Post by volkerbradley on 2010-07-12
Thanks to both of you for helping me understand this.  

> **Cavsfan said:**
> ```
[COLOR=Blue]He is talking about wrapping CODE around that long string of text in your first post. [/COLOR] 
```[COLOR=Blue]He is talking about wrapping CODE around that long string of text in  your first post. [/COLOR](see this above?)
Edit and highlight the whole section of text about your plugins on your first post and then click on the "#" sign 
at the top of the box. It will wrap CODE around the text that will shorten the amount of space your post takes up. 
You want to do this whenever you are posting a lot of data. It creates a scrollable window that takes up less room 
for the display of a lot of data in a post.

---

### Post by Cavsfan on 2010-07-12
> **volkerbradley said:**
> Thanks to both of you for helping me  understand this.

You are very welcome!

> **samalex said:**
> I've heard a few people suggesting this change, but what does it do?  I haven't had any major problems with Flash since installing 64-bit 10.04 on my PanP5, but I made this change in npviewer none the less to maybe fix some potential problems.  But what does it do exactly?  Just curious.

Sam

For me, before I made that mod. I could not stop a youtube video nor pause it, 
control the volume, go fullscreen or be able to use any other buttons. After the 
workaround I could.

Here is the bug/workaround as posted by **Spr0k3t**
There are 3 steps, but the 3rd is all I had to do. It worked immediately.
_[http://ubuntuforums.org/showpost.php?p=9380613&postcount=2](http://ubuntuforums.org/showpost.php?p=9380613&postcount=2)_

---

