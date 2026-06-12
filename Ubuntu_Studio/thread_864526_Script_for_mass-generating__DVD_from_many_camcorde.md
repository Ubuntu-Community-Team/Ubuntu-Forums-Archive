---
title: "Script for mass-generating  DVD from many camcorder videos"
date: 2008-07-19
forum: Ubuntu Studio
---

### Post by Lapogne71 on 2008-07-19
I made a small script intended to archive on DVD your many video sequences from camcorder. (Waiting for complete free equivalent solution, mkv with menus when it will be possible !... )

The aim is archiving to DVD with :
- menus with pictures slide-show and soundtrack
- intelligent navigation menus
- readable titles and numbers of DVD / menus
- reusable configuration (from .ini file)
- no tiresome 'handmade' dvd authoring
- complete automated DVD generation

Excerpt of the help of the script :

[I]"** This script allow mass-generating of DVDs (.iso images) from "
"** many video sequences with m2v + ac3 format. "
"** This program is typically intended to save on DVD your movie camera video archives, "
"** beforehand converted to 'MPEG2 (m2v) and A52 (ac3) DVD compatible format'."
"**"
"** For each DVD, the program make one or more menus depending on the number "
"** of video sequences in DVD and on the number of titles allowed per menu. "
"**"
"** Each menu is a slide-show made from a list of pictures, "
"** with a soundtrack taken from a list of audio files "
"**"
"** It's possible to change the font used in menus, "
"** the maximum duration of menus in secondes, the number of titles displayed in one menu "
"**"
"**  For menus navigation creation, the program will need a list of pictures with"
"**  JPEG, BMP or TIFF format, and a list of audio files (WAV, MP3, OGG)."
"**"
"** Please allow enough disk space for destination folder."
"**"
"** Tools to be beforehand installed : "
"**	ffmpeg, sox, aften, dvdauthor, mjpegtools, imagemagick, "
"** 	dvd-slideshow, genisoimage, xine "
"**"
"** Other prerequisites : "
"** 	- sequences names should be not too short neither too long"
"** 	- some pictures and audio tracks for the menus "
"** 	- a font with accents (ex : for french names)"
"** "
"** Precisions on program : "
"** 	- configuration is done with ini file"
"** 	- pictures and audio tracks in menus are choosen randomly "
"** 	- fade-out for audio tracks in menus "
"** 	- intelligent navigation inside and between menus "
"** 	- sequences not included in any DVDs (too big) listed in list_seq_to_redo.txt "
"** 	- DEMO mode allow to test DVDs generation with "
"** 	  only 10 secondes sequences to speed up results "
"** 	- DEV mode allow to keep temporary files "
"** 	- if DEV_MODE and DEMO_MODE = 0 , musics menu can be re-generated "
"** 	  each time to ensure fade-out is made at end of menu "[/I]

Video sequences have to be in MPEG2 ES (elementary streams m2v + ac3). A script dv-to-m2v-ac3
is included to mass-convert your DV files to 'MPEG2 DVD compatible' files.

**(update : v0.04) :**
- minor corrections due to sox and convert (imagemagick) syntax changes
- screenshot et readme included in tar.gz

(update : v0.03) :
- comments inside script are now in english
- configuration with .ini file
- added a script to convert any video file "MPEG2 elementary streams"


Links :
the script : [m2v-ac3-to-dvd_0.04.tar.gz](http://lapogne.free.fr/files/shell/m2v-ac3-to-dvd_0.04.tar.gz)
the font I prefer for the menus : [LEXIA.ttf](http://lapogne.free.fr/files/shell/LEXIA.ttf)

Any help, comments, suggestions, corrections, reviews are welcome ! :)

---

### Post by Lapogne71 on 2009-11-14
just updated the script (minor corrections)

---

