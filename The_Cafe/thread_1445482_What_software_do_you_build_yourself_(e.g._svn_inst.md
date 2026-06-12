---
title: "What software do you build yourself? (e.g. svn instead of ubuntu package)"
date: 2010-04-02
forum: The Cafe
---

### Post by bryce123 on 2010-04-02
Hi guys,

I was wondering, if you build software from source on ubuntu, and if yes why?

I always build my own mplayer svn version since i often times benefit from new/left out features, that are not provided by the package. I also build irssi, because i like to help testing. 

The rest of the software I use on a daily basis is either a pain to build yourself (firefox) or there are quite recent versions (fluxbox) / extra repositories.

---

### Post by diesch on 2010-04-02
I've compiled Emacs myself as I didn't like all the customizations Ubuntu makes there by default. And as I'm a Python programmer I need to install some Python modules that aren't in the repositories every now and then.

---

### Post by lovinglinux on 2010-04-02
Firefox to improve performance, but I stopped compiling it since I upgraded my CPU from a P4 to a Core 2 Duo.

---

### Post by Irihapeti on 2010-04-02
I've compiled some multimedia packages because I wanted codecs not included in the Ubuntu versions, or because the version in the repositories was too old/buggy.

---

### Post by sandyd on 2010-04-02
kde. I compile it for bug patching reasons. I also compile other apps for bug patching / testing.

---

### Post by bluelamp999 on 2010-04-02
> **lovinglinux said:**
> Firefox to improve performance, but I stopped compiling it since I upgraded my CPU from a P4 to a Core 2 Duo.

For those of us on less than current processors I highly recommend compiling Firefox.

I've used LovingLinux's most excellent instructions - [http://lovinglinux.megabyet.net/?page_id=220#Compiling-Firefox-1](http://lovinglinux.megabyet.net/?page_id=220#Compiling-Firefox-1) - to compile Firefox 3 times now (currently rocking 3.6.3!)

It's definitely a very positive upgrade and puts Firefox on an equal footing with Chrome speed wise (at least on a Pentium M 2GHz.)

Edit: I also compile Transmission to always have the latest version.

---

### Post by donkyhotay on 2010-04-02
I generally only compile games that have out of date packages or I want to modify them myself.

---

### Post by lovinglinux on 2010-04-02
> **bluelamp999 said:**
> For those of us on less than current processors I highly recommend compiling Firefox.

I've used LovingLinux's most excellent instructions - [http://lovinglinux.megabyet.net/?page_id=220#Compiling-Firefox-1](http://lovinglinux.megabyet.net/?page_id=220#Compiling-Firefox-1) - to compile Firefox 3 times now (currently rocking 3.6.3!)

It's definitely a very positive upgrade and puts Firefox on an equal footing with Chrome speed wise (at least on a Pentium M 2GHz.)

Edit: I also compile Transmission to always have the latest version.

Yes, the performance gain on single core processors is great. 

Thanks for your comments about my tutorial.

---

### Post by bluelamp999 on 2010-04-02
> **lovinglinux said:**
> Thanks for your comments about my tutorial.

You are most welcome. You are THE Ubuntu Firefox guru!

---

### Post by andrew.46 on 2010-04-02
Hi,

I always compile the svn MPlayer, svn FFmpeg, git x264 and Transmission. The Ubuntu Repositories are just not able to keep up with the pace of development for these...

Andrew

---

### Post by dragos240 on 2010-04-02
Everything. I use gentoo.

---

### Post by Bachstelze on 2010-04-02
MPlayer, ffmpeg, mkvtoolnix, Python 3, iroffer, and probably a few others I can't remember from the top of my head, I'm not on my Ubuntu machine right now. I also use my own self-compiled x264 packages, so maybe that counts too.

---

### Post by Bachstelze on 2010-04-02
> **dragos240 said:**
> Everything. I use gentoo.

You don't build it yourself, Portage builds it for you. ;)

---

### Post by Dharmachakra on 2010-04-02
A sizable number... anything I can't find in the Fedora or RPM Fusion repositories.

---

### Post by dragos240 on 2010-04-02
> **Bachstelze said:**
> You don't build it yourself, Portage builds it for you. ;)

Make.conf?

---

### Post by andrew.46 on 2010-04-02
Mind you if we are talking *other* distros this is my directory of source code I have compiled under slackware:

```

andrew@skamandros~/source$ ls
Brother_HL-2140  conky		      id3lib	   libnotify	   opencore-amr		 vlc
abcde		 enca		      id3v2	   libtheora	   openoffice.org	 vobcopy
acpica		 faac		      ladspa_sdk   live555	   perl			 w3m
adobe-reader	 faad2		      lame	   lua		   scons		 wxGTK
alsa-lib	 ffmpeg		      leafnode	   mkvtoolnix	   slackware-13-updates  x264
b43-firmware	 ffmpeg2theora	      libass	   mplayer	   slrn			 xfce4-power-manager
b43-fwcutter	 flash-player-plugin  libdvdcss    mplayer-codecs  smplayer		 yasm
bluefish	 gc		      libdvdread   msmtp	   speex
ca_certs	 gecko-mediaplayer    libebml	   mutt		   transmission
cd-discid	 gnome-mplayer	      libmatroska  nero-aac	   vbox_puel


```

Mind you I see a few ringins there, the adobe reader, vbox and Nero-aac are repackaged binaries, abcde is a script and vlc + slackware updates are packages...

Andrew

---

### Post by phrostbyte on 2010-04-02
Too many to count.

Most recent thing was IronPython.

---

