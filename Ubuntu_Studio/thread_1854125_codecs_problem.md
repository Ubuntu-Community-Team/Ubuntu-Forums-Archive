---
title: "codecs problem"
date: 2011-10-03
forum: Ubuntu Studio
---

### Post by Subito Piano on 2011-10-03
Hi!  Trying to play a wmv file, but i get the response that no packages are available with the requested plugins:[INDENT] video/x-asf-unknown decoder
Windows Media Speech decoder
[/INDENT]I need to be able to play WMAS files -- OK, somehow, even though i downloaded them and play mp3s all the time, now it appears i don't have the w32 restricted codecs, so i[INDENT]sudo apt-get install ubuntu-restricted-extras
[/INDENT]and get the following message:[INDENT] The following packages will be REMOVED:
  audacious audacious-plugins dvgrab ffmpeg ffmpeg2theora freemix
  gecko-mediaplayer gem gnome-mplayer gnomebaker gstreamer0.10-ffmpeg kino
  libavcodec52 libavdevice52 libavfilter0 libavformat52 libavifile-0.7c2
  libavutil49 libk3b6-extracodecs libmjpegtools-1.9 libpostproc51
  libquicktime1 libswscale0 libxine1-ffmpeg mencoder mjpegtools mplayer
  transcode ubuntustudio-audio ubuntustudio-video vlc vlc-nox vlc-plugin-pulse
  xjadeo
The following NEW packages will be installed:
  gstreamer0.10-plugins-ugly-multiverse icedtea6-plugin libavcodec-extra-52
  libavutil-extra-49 libfaac0 libmp4v2-0 libopenjpeg2 ubuntu-restricted-extras
[/INDENT]?!?!?!??!?!  This is Ubuntu STUDIO!!!  Why is it trying to strip out all my players -- even MPlayer?!?! -- to install these codecs???? 

OK, i can copy down all the programs it is going to rip out, install the codecs, and see what happens, but methinks there is a better way.  Any ideas?

Toshiba, AMD 64-bit dual core, using Ubuntu Studio (Ubuntu 10.04 LTS) for a year and a half, first time anything like this since installation.

---

### Post by jejeman on 2011-10-03
Install just this package: gstreamer0.10-plugins-ugly-multiverse
and try then.

---

### Post by Subito Piano on 2011-10-03
nix -- no go.  :-s

I note that it complains about "MSS2" files....

---

### Post by WasMeHere on 2011-10-03
> **Subito Piano said:**
> ... OK, somehow, even though i downloaded them and play mp3s all the time, now it appears i don't have the w32 restricted codecs ... Toshiba, AMD 64-bit dual core, using Ubuntu Studio (Ubuntu 10.04 LTS) for a year and a half, first time anything like this since installation.

Do you have 64-bit or 32-bit ubuntu? I'm thinking that you may get problems with w32 codecs in a 64-bit system.

I can play wmv files with mplayer and vlc in 'vanilla' ubuntu 10.04-i686 (32-bit)
mplayer: Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)

---

### Post by Subito Piano on 2011-10-03
yes, 64-bit dual core.   According to [this post]("http://forums.opensuse.org/english/get-technical-help-here/multimedia/461366-win32-codecs-64-bit-system.html"), i shouldn't even need the codecs -- ?!?!?  However, the Win32 codecs only work on 32-bit versions of media players.

---

### Post by WasMeHere on 2011-10-04
You can try Linux Mint without installing. Download an iso file for the DVD version with gnome if you are using Ubuntu with gnome! Then you can make a live DVD or live USB. The advantage with Mint is that the multimedia toolbox works directly with the live system, so that you will know without having to install to your hard disk:
*linuxmint-11-gnome-dvd-32bit*
if your graphics work with Mint. Some people would suggest -64bit if you have a 64 bit system.

A good alternative is to apply the following how-to link to your installed system: [_**[COLOR="Red"]Comprehensive Multimedia & Video Howto[/COLOR]**_]("http://ubuntuforums.org/showthread.php?t=766683")
It may take some time, but the result is very good, you will get a solid multimedia system.

---

### Post by Subito Piano on 2011-10-04
Well, yeah, i've used Mint a lot and recommended it a ton -- i think you hit the problem on the head, it has to do with my 64-bit install, and i am loathe to reinstall my OS to get a 32-bit version (way too customized here on my laptop).  Presently pursuing using a few Windows programs under Wine (VLC, Media Player Classic, whatever) in the MS 32-bit format.  Apparently, it also has to do with this wmv file being really old, from the 90's --

The page you mentioned refers me to the restricted-extras package, which i mentioned trying in my first post...

---

### Post by Subito Piano on 2011-10-04
Somewhat of a solution -- download the Windows version of UMPlayer and ran under WINE -- had to mess with the video (OPTIONS>PREFERENCES) for the right driver.  It's touchy, but it works.  
Hmm....     [IMG]http://i148.photobucket.com/albums/s32/juno-ars/snoozer_likelinux_man.gif[/IMG][IMG]http://mepislovers.org/forums/images/smilies/snoozer_likelinux_man.gif[/IMG][IMG]http://mepislovers.org/forums/images/smilies/snoozer_likelinux_man.gif[/IMG]

---

