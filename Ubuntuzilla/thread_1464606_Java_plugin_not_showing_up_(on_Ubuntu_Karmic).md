---
title: "Java plugin not showing up (on Ubuntu Karmic)"
date: 2010-04-28
forum: Ubuntuzilla
---

### Post by JakeLawrence on 2010-04-28
After following the instructions on [this SourceForge]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29") page, I'm running into this problem:

```
jacob@jacob-laptop:~$ sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50
update-alternatives: error: alternative path /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so doesn't exist.

```

I had successfully installed the sun-java6-plugin, as shown here:

```
jacob@jacob-laptop:~$ sudo apt-get install sun-java6-plugin
[sudo] password for jacob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gsfonts-x11 odbcinst1debian1 sun-java6-bin sun-java6-jre unixodbc
Suggested packages:
  sun-java6-fonts ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho
  ttf-arphic-uming libmyodbc odbc-postgresql libct1
The following NEW packages will be installed:
  gsfonts-x11 odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin unixodbc
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.2MB of archives.
After this operation, 98.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic/multiverse sun-java6-jre 6-15-1 [6,421kB]
Get:2 http://us.archive.ubuntu.com karmic/main odbcinst1debian1 2.2.11-16ubuntu1 [71.8kB]   
Get:3 http://us.archive.ubuntu.com karmic/main unixodbc 2.2.11-16ubuntu1 [309kB]            
Get:4 http://us.archive.ubuntu.com karmic/multiverse sun-java6-bin 6-15-1 [27.4MB]          
Get:5 http://us.archive.ubuntu.com karmic/main gsfonts-x11 0.21 [10.5kB]                    
Get:6 http://us.archive.ubuntu.com karmic/multiverse sun-java6-plugin 6-15-1 [1,822B]       
Fetched 34.2MB in 2min 24s (236kB/s)                                                        
Preconfiguring packages ...
Selecting previously deselected package sun-java6-jre.
(Reading database ... 136547 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6-15-1_all.deb) ...
Selecting previously deselected package odbcinst1debian1.
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-16ubuntu1_amd64.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.11-16ubuntu1_amd64.deb) ...
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6-15-1_amd64.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package gsfonts-x11.
Unpacking gsfonts-x11 (from .../gsfonts-x11_0.21_all.deb) ...
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-15-1_amd64.deb) ...
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up odbcinst1debian1 (2.2.11-16ubuntu1) ...

Setting up unixodbc (2.2.11-16ubuntu1) ...

Setting up gsfonts-x11 (0.21) ...

Setting up sun-java6-jre (6-15-1) ...

Setting up sun-java6-bin (6-15-1) ...
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/ControlPanel to provide /usr/bin/ControlPanel (ControlPanel) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/java_vm to provide /usr/bin/java_vm (java_vm) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/jcontrol to provide /usr/bin/jcontrol (jcontrol) in auto mode.

Setting up sun-java6-plugin (6-15-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

So what did I do wrong?

Any help is greatly appreciated.

Best,
Jake

---

### Post by garyedwardjohnston on 2010-04-28
not sure why you are making this more complicated than it is just search synaptic for the java files you want installed and install them

i installed java with ubuntu-restricted-extras

---

### Post by nanotube on 2010-04-28
> **JakeLawrence said:**
> After following the instructions on [this SourceForge]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29") page, I'm running into this problem:

```
jacob@jacob-laptop:~$ sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50
update-alternatives: error: alternative path /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so doesn't exist.

```

I had successfully installed the sun-java6-plugin, as shown here:
<snip>
So what did I do wrong?

Any help is greatly appreciated.

Best,
Jake

run the update-alternatives command /after/ you have installed the sun-java6-jre.

---

### Post by JakeLawrence on 2010-04-28
I have no idea why I made things harder either, man! I had downloaded A LOT of 32-bit flash plugins and all sorts of different files. Having just installed the OS, I just did a clean install and started over. All I did to get Youtube videos working was

```
sudo apt-get update
```and then installed the Ubuntu Restricted Extras package.

After nearly 8 hours of finding out how to get flash, it was that freakin' easy. :)

EDIT: Should this method work for both 32-bit and 64-bit architectures?

---

### Post by Objekt on 2010-06-23
I ran into this problem recently, when trying to use USAA Deposit @ Home (thread here: [http://ubuntuforums.org/showthread.php?t=1454931]("http://ubuntuforums.org/showthread.php?t=1454931")).

It's actually a general plugins problem.  When I go to about:plugins, I see only the following:

```
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r42

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Default Plugin

    File: libnullplugin.so
    Version: 1.0.0.15
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
```

There's a TON of stuff missing!  Besides the Java plugin, there are about 20 zillion other plugins that should be showing up in Firefox.  They only show up in Google Chrome (5.0.307.7 beta) and Opera (10.10).  Here's the about:plugins listing from Chrome, for example (Warning: quite long):
```
Installed plug-ins

Java(TM) Plug-in 1.6.0_20

File name: libnpjp2.so
The next generation Java plug-in for Mozilla browsers.
MIME Type	Description	Suffixes	Enabled
application/x-java-vm	Java&#8482; Plug-in		Yes
application/x-java-applet	Java&#8482; Plug-in Applet		Yes
application/x-java-applet;version=1.1	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.1.1	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.1.2	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.1.3	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.2	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.2.1	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.2.2	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.3	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.3.1	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.4	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.4.1	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.4.2	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.5	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.6	Java&#8482; Plug-in		Yes
application/x-java-applet;jpi-version=1.6.0_20	Java&#8482; Plug-in		Yes
application/x-java-bean	Java&#8482; Plug-in JavaBeans		Yes
application/x-java-bean;version=1.1	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.1.1	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.1.2	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.1.3	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.2	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.2.1	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.2.2	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.3	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.3.1	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.4	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.4.1	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.4.2	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.5	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.6	Java&#8482; Plug-in		Yes
application/x-java-bean;jpi-version=1.6.0_20	Java&#8482; Plug-in		Yes
application/x-java-vm-npruntime	Java&#8482; Plug-in		Yes
Java(TM) Plug-in 1.6.0_20

File name: libnpjp2.so
The next generation Java plug-in for Mozilla browsers.
MIME Type	Description	Suffixes	Enabled
application/x-java-vm	Java&#8482; Plug-in		Yes
application/x-java-applet	Java&#8482; Plug-in Applet		Yes
application/x-java-applet;version=1.1	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.1.1	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.1.2	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.1.3	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.2	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.2.1	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.2.2	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.3	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.3.1	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.4	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.4.1	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.4.2	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.5	Java&#8482; Plug-in		Yes
application/x-java-applet;version=1.6	Java&#8482; Plug-in		Yes
application/x-java-applet;jpi-version=1.6.0_20	Java&#8482; Plug-in		Yes
application/x-java-bean	Java&#8482; Plug-in JavaBeans		Yes
application/x-java-bean;version=1.1	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.1.1	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.1.2	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.1.3	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.2	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.2.1	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.2.2	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.3	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.3.1	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.4	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.4.1	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.4.2	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.5	Java&#8482; Plug-in		Yes
application/x-java-bean;version=1.6	Java&#8482; Plug-in		Yes
application/x-java-bean;jpi-version=1.6.0_20	Java&#8482; Plug-in		Yes
application/x-java-vm-npruntime	Java&#8482; Plug-in		Yes
iTunes Application Detector

File name: librhythmbox-itms-detection-plugin.so
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.
MIME Type	Description	Suffixes	Enabled
application/itunes-plugin			Yes
Shockwave Flash

File name: npwrapper.libflashplayer.so
Shockwave Flash 10.0 r42
MIME Type	Description	Suffixes	Enabled
application/x-shockwave-flash	Shockwave Flash	swf	Yes
application/futuresplash	FutureSplash Player	spl	Yes
VLC Multimedia Plugin (compatible Totem 2.28.2)

File name: libtotem-cone-plugin.so
The Totem 2.28.2 plugin handles video and audio streams.
MIME Type	Description	Suffixes	Enabled
application/x-vlc-plugin	VLC Multimedia Plugin		Yes
application/vlc	VLC Multimedia Plugin		Yes
video/x-google-vlc-plugin	VLC Multimedia Plugin		Yes
application/x-ogg	Ogg multimedia file	ogg	Yes
application/ogg	Ogg multimedia file	ogg	Yes
audio/ogg	Ogg Audio	oga	Yes
audio/x-ogg	Ogg Audio	ogg	Yes
video/ogg	Ogg Video	ogv	Yes
video/x-ogg	Ogg Video	ogg	Yes
application/annodex	Annodex exchange format	anx	Yes
audio/annodex	Annodex Audio	axa	Yes
video/annodex	Annodex Video	axv	Yes
video/mpeg	MPEG video	mpg,mpeg,mpe	Yes
audio/wav	WAV audio	wav	Yes
audio/x-wav	WAV audio	wav	Yes
audio/mpeg	MP3 audio	mp3	Yes
application/x-nsv-vp3-mp3	NullSoft video	nsv	Yes
video/flv	Flash video	flv	Yes
application/x-totem-plugin	Totem Multimedia plugin		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

File name: libtotem-gmp-plugin.so
The Totem 2.28.2 plugin handles video and audio streams.
MIME Type	Description	Suffixes	Enabled
application/x-mplayer2	AVI video	avi,wma,wmv	Yes
video/x-ms-asf-plugin	ASF video	asf,wmv	Yes
video/x-msvideo	AVI video	asf,wmv	Yes
video/x-ms-asf	ASF video	asf	Yes
video/x-ms-wmv	Windows Media video	wmv	Yes
video/x-wmv	Windows Media video	wmv	Yes
video/x-ms-wvx	Windows Media video	wmv	Yes
video/x-ms-wm	Windows Media video	wmv	Yes
video/x-ms-wmp	Windows Media video	wmv	Yes
application/x-ms-wms	Windows Media video	wms	Yes
application/x-ms-wmp	Windows Media video	wmp	Yes
application/asx	Microsoft ASX playlist	asx	Yes
audio/x-ms-wma	Windows Media audio	wma	Yes
DivX® Web Player

File name: libtotem-mully-plugin.so
DivX Web Player version 1.4.0.233
MIME Type	Description	Suffixes	Enabled
video/divx	AVI video	divx	Yes
QuickTime Plug-in 7.2.0

File name: libtotem-narrowspace-plugin.so
The Totem 2.28.2 plugin handles video and audio streams.
MIME Type	Description	Suffixes	Enabled
video/quicktime	QuickTime video	mov	Yes
video/mp4	MPEG-4 video	mp4	Yes
image/x-macpaint	MacPaint Bitmap image	pntg	Yes
image/x-quicktime	Macintosh Quickdraw/PICT drawing	pict,pict1,pict2	Yes
video/x-m4v	MPEG-4 video	m4v	Yes
Xine Plugin

File name: xineplugin.so
Xine Plugin version 1.0.2, (c) The Xine Project.
Windows Media Player / RealPlayer / QuickTime compatible.
MIME Type	Description	Suffixes	Enabled
application/annodex	 Annodex media	anx	Yes
application/x-annodex	 Annodex media	anx	Yes
audio/annodex	 Annodex audio	axa	Yes
audio/x-annodex	 Annodex audio	axa	Yes
video/annodex	 Annodex video	axv	Yes
video/x-annodex	 Annodex video	axv	Yes
video/quicktime	 Quicktime animation	mov,qt	Yes
video/x-quicktime	 Quicktime animation	mov,qt	Yes
audio/x-m4a	 MPEG-4 audio	m4a,m4b	Yes
application/x-quicktimeplayer	 Quicktime list	qtl	Yes
video/mp4	 MPEG-4 video	mp4,mpg4	Yes
audio/mp4	 MPEG-4 audio	mp4,mpg4	Yes
audio/x-8svx	 IFF-8SVX Audio	8svx	Yes
audio/8svx	 IFF-8SVX Audio	8svx	Yes
audio/x-16sv	 IFF-16SV Audio	16sv	Yes
audio/168sv	 IFF-16SV Audio	16sv	Yes
image/x-ilbm	 IFF-ILBM Picture	ilbm	Yes
image/ilbm	 IFF-ILBM Picture	ilbm	Yes
video/x-anim	 IFF-ANIM Video	anim	Yes
video/anim	 IFF-ANIM Video	anim	Yes
audio/x-aiff	 AIFF audio	aif,aiff	Yes
audio/aiff	 AIFF audio	aif,aiff	Yes
audio/x-pn-aiff	 AIFF audio	aif,aiff	Yes
audio/x-flac	 FLAC Audio	flac	Yes
audio/flac	 FLAC Audio	flac	Yes
audio/x-realaudio	 RealAudio File	ra	Yes
audio/basic	 ULAW (Sun) audio	snd,au	Yes
audio/x-basic	 ULAW (Sun) audio	snd,au	Yes
audio/x-pn-au	 ULAW (Sun) audio	snd,au	Yes
audio/x-mod	 SoundTracker/NoiseTracker/ProTracker Module	mod	Yes
audio/mod	 SoundTracker/NoiseTracker/ProTracker Module	mod	Yes
audio/it	 ImpulseTracker Module	it	Yes
audio/x-it	 ImpulseTracker Module	it	Yes
audio/x-stm	 ScreamTracker 2 Module	stm	Yes
audio/x-s3m	 ScreamTracker 3 Module	s3m	Yes
audio/s3m	 ScreamTracker 3 Module	s3m	Yes
application/playerpro	 669 Tracker Module	669	Yes
application/adrift	 ADRIFT Module File	amf	Yes
audio/med	 Amiga MED/OctaMED Tracker Module Sound File	med	Yes
audio/x-amf	 ADRIFT Module File	amf	Yes
audio/x-xm	 FastTracker II Audio	xm	Yes
audio/xm	 FastTracker II Audio	xm	Yes
video/x-flic	 Autodesk FLIC files	fli,flc	Yes
audio/x-pn-realaudio	 Real Media file	ra,rm,ram	Yes
audio/x-pn-realaudio-plugin	 Real Media plugin file	rpm	Yes
audio/x-real-audio	 Real Media file	ra,rm,ram	Yes
application/vnd.rn-realmedia	 Real Media file	ra,rm,ram	Yes
video/mkv	 matroska	mkv	Yes
video/x-matroska	 matroska	mkv	Yes
video/x-ms-asf	 ASF stream	asf	Yes
video/x-ms-wmv	 Windows Media Video	wmv	Yes
audio/x-ms-wma	 Windows Media Audio	wma	Yes
application/vnd.ms-asf	 ASF stream	asf	Yes
application/x-mplayer2	 mplayer2	asf,asx,asp	Yes
video/x-ms-asf-plugin	 mms animation	asf,asx,asp	Yes
video/x-ms-wvx	 wmv metafile	wvx	Yes
video/x-ms-wax	 wma metafile	wva	Yes
video/x-flv	 Flash video	flv	Yes
video/flv	 Flash video	flv	Yes
application/x-flash-video	 Flash video	flv	Yes
video/msvideo	 AVI video	avi	Yes
video/x-msvideo	 AVI video	avi	Yes
image/png	 PNG image	png	Yes
image/x-png	 PNG image	png	Yes
video/mng	 MNG animation	mng	Yes
video/x-mng	 MNG animation	mng	Yes
application/ogg	 Ogg Stream	ogx	Yes
application/x-ogg	 Ogg Stream	ogx	Yes
application/x-ogm	 Ogg Stream	ogx	Yes
application/x-ogm-audio	 Ogg Audio	oga	Yes
application/x-ogm-video	 Ogg Video	ogv	Yes
audio/ogg	 Ogg Audio	oga	Yes
audio/x-ogg	 Ogg Audio	oga	Yes
video/ogg	 Ogg Video	ogv	Yes
video/x-ogg	 Ogg Video	ogv	Yes
video/mpeg	 MPEG animation	mpeg,mpg,mpe	Yes
video/x-mpeg	 MPEG animation	mpeg,mpg,mpe	Yes
audio/x-wav	 WAV audio	wav	Yes
audio/wav	 WAV audio	wav	Yes
audio/x-pn-wav	 WAV audio	wav	Yes
audio/x-pn-windows-acm	 WAV audio	wav	Yes
audio/musepack	 Musepack audio	mpc,mp+,mpp	Yes
audio/x-musepack	 Musepack audio	mpc,mp+,mpp	Yes
audio/mpeg2	 MPEG audio	mp2	Yes
audio/x-mpeg2	 MPEG audio	mp2	Yes
audio/mpeg3	 MPEG audio	mp3	Yes
audio/x-mpeg3	 MPEG audio	mp3	Yes
audio/mpeg	 MPEG audio	mpa,abs,mpega	Yes
audio/x-mpeg	 MPEG audio	mpa,abs,mpega	Yes
audio/x-mpegurl	 MPEG audio	mp3	Yes
audio/mpegurl	 MPEG audio	mp3	Yes
audio/mp3	 MPEG audio	mp3	Yes
audio/x-mp3	 MPEG audio	mp3	Yes
audio/x-wavpack	 WavPack audio	wv,wvp	Yes
audio/x-flac	 FLAC Audio	flac	Yes
audio/flac	 FLAC Audioaudio/x-scpls: pls: Winamp playlist	flac	Yes
application/smil	 SMIL playlist	smi,smil	Yes
application/xspf+xml	 XSPF playlist	xspf	Yes
application/x-xine-plugin	 Xine plugin		Yes
```

FWIW, I just upgraded Firefox to version 3.6.4 using Ubuntuzilla, but the problem persists.

What is the deal?  I definitely have the sun-java6-plugin package installed.  I tried the instructions at the Sourceforge Ubuntuzilla page to work around this bug.  Didn't work.  Maybe because I'm running a 64-bit version of Ubuntu 9.10?  I did have to alter the instructions slightly (e.g. change "i386" to "amd64" in one of the commands), but the command completed.  Didn't do anything, however, because I still see only the Flash plugin in Firefox.

I installed ubuntu restricted extras long ago, as you can probably tell from the plugins listing from Chrome.

---

### Post by nanotube on 2010-06-23
> **Objekt said:**
> 
What is the deal?  I definitely have the sun-java6-plugin package installed.  I tried the instructions at the Sourceforge Ubuntuzilla page to work around this bug.  Didn't work.  Maybe because I'm running a 64-bit version of Ubuntu 9.10?  I did have to alter the instructions slightly (e.g. change "i386" to "amd64" in one of the commands), but the command completed.  Clearly, they didn't work.

well, the thing is, as you may have read on the ubuntuzilla site, mozilla only makes 32bit binaries, which are what ubuntuzilla packages. so in order to get the plugins to work, you need 32bit plugins. if you're on 64bit ubuntu, the sun-java5-bin/jre/plugin packages are 64 bit, and won't work on 32bit firefox.

see:
[https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_What_happened_with_Flash_and_all_my_other_plugins.3F](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_What_happened_with_Flash_and_all_my_other_plugins.3F)
for details on getting 32bit java/flash. 

and see also this:
[https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users)
for alternatives to ubuntuzilla, since it really isn't the best for 64bit.

---

### Post by Objekt on 2010-06-24
Tried all that (including the "Java plugin not showing up" instructions); still didn't work.  I even manually created symbolic links to the 32-bit version of the Java plugin.  No dice.

Maybe I should just switch browsers.  I'm reluctant to leave Firefox  because I love all the extensions & add-ons.  Opera et al simply don't have as many available, although they're good browsers too (better than FF in some ways).

I'm also wondering if I shouldn't just start over with 32-bit everything.  Aside from Intel Atom-based netbooks, there's hardly any PC anymore that can't handle 64-bit native code, but certain software seems to be stuck in 32-bit land.  I'd feel silly running a 32-bit OS on my hardware, but it would save some headaches.

Might be time for a new thread, something like ""Java plugin not showing up" instructions don't work"?

---

### Post by nanotube on 2010-06-25
well... i'd suggest then going with another repository, that has a 64bit build of firefox you can use.
maybe the firefox-stable or the mozilla-security ppas...

---

### Post by Objekt on 2010-07-09
I downloaded & unpacked the 64-bit build of Firefox 3.7a6pre.  Got it to run (kudos to the devs for including a shell script).

As you predicted, all my plugins showed up when I went to "about:plugins."

(By the way, that's not supposed to be a smiley face in the middle of the quotes in the line above.  I guess the forum software automatically interprets the sequence of : and then letter "p" as a smiley face.)

I LOL'd @ the new name: "Minefield," with the Firefox globe turned into a bomb with lit fuse.  How apropos for a pre-release build! :D 

So now I have a version of Firefox that is 64-bit, and will work with all my (64-bit) plugins without arcane manipulations, genuflections, and/or blood sacrifice.  That solves the immediate problem.  

I guess I'll have to manually download new 64-bit builds of Firefox as they're released.  I expect the occasional crash and/or add-on incompatibility.  No biggie.  I'm marking my other thread on this topic as "solved."

---

### Post by ratcheer on 2010-07-09
> **Objekt said:**
> Tried all that (including the "Java plugin not showing up" instructions); still didn't work.  I even manually created symbolic links to the 32-bit version of the Java plugin.  No dice.



Which Java plugin are you linking? The documented one is incorrect. You have to link libnpjp2.so, instead. It resides in $JAVA_JOME/lib/i386

Tim

---

### Post by Objekt on 2010-07-09
> **ratcheer said:**
> Which Java plugin are you linking? The documented one is incorrect. You have to link libnpjp2.so, instead. It resides in $JAVA_JOME/lib/i386

Tim

Not sure what you're talking about.  There is no such path as $JAVA_JOME/lib/i386 anywhere on my system.  Typo?

What I do have is, a link (in ~/.mozilla/plugins) to the following: /opt/java/64/jre1.6.0_20/lib/amd64/libnpjp2.so

Which is of course the 64-bit version of the Java plugin.  Which, naturally, won't work with at 32-bit version of Firefox.

I haven't put my 64-bit build of 3.7a6pre through its paces yet, but it at least runs and recognizes all my plugins.

---

### Post by ratcheer on 2010-07-09
Ok, if you don't have JAVA_HOME set, it is just wherever you have Java installed. For example, on my system, it is /usr/java/jre1.6.0_20. On yours, it might be somewhere else.

So, on my system, i have the link set as /usr/lib/firefox/plugins/libnpjp2.so -> /usr/java/jre1.6.0_20/lib/i386/libnpjp2.so

Tim

---

