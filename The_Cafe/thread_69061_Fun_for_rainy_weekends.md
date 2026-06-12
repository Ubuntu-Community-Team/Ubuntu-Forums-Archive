---
title: "Fun for rainy weekends"
date: 2005-09-25
forum: The Cafe
---

### Post by mtron on 2005-09-25
We had here a very rainy weekend, so i had loads of time to play around with my ubuntu. So i want to present you some pieces of software i discovered:

1. LiVES: [http://www.xs4all.nl/~salsaman/lives/](http://www.xs4all.nl/~salsaman/lives/)
it's a video editing tool and a must for everybody with a DVB card. till now, there were no good apps for cutting recorded dvb mpg2 streams, like we get them from sattelite in europe. Cinerella to hard to use, and Kino refuses to work with them. I looked at Lives already some months ago, but the current version 0.95pre5 is now really usable and amazingly easy to use, import, editing, some filters and loads of export finctions. The latest version compiles and installs flawlessly on an hoary system. 

get the tar.gz here: [http://www.xs4all.nl/~salsaman/lives/downloads.html](http://www.xs4all.nl/~salsaman/lives/downloads.html)

2. DupeMusicMatch [http://www.gnomefiles.org/app.php?soft_id=1090](http://www.gnomefiles.org/app.php?soft_id=1090)
Is a very handy python script that searches your music libary for duplicated files (works really good, on filename and filesize, ect). If you record with streamtuner & streamripper, it happens sometimes that you get the same track twice, so here is the solution.

Just unpack the archive and run the python script 

het it here: [http://sourceforge.net/project/showfiles.php?group_id=148450&package_id=163719](http://sourceforge.net/project/showfiles.php?group_id=148450&package_id=163719)

3. SoundConverter [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)

Based on Gstreamer, this gtk2 app reads anything the GStreamer library can read, and writes WAV, FLAC, MP3, and Ogg Vorbis files. Written in python with glade the surrent version 0.8.0 is already very good. Maybe i'll try to hack it using mplayer and lame for converting apples mp4 (aac) to mp3. Till now, you can use my script for this (see attachment, needs mplayer & lame).

get it here: [http://developer.berlios.de/project/showfiles.php?group_id=3213](http://developer.berlios.de/project/showfiles.php?group_id=3213)  

4. Skype-rec

It's a small script for recording conversations with the proprietary skype VoIP software, and converting them to MP3. The first working solution i found for Skype. It records in and out voice and muxes them togeter afterwards. I use the static skype binary with qt compiled-in and symlinked the binary to /usr/bin. Grab the tool, unpack it in $HOME/skype-rec and run make, then you must adjust the path to the libskype-rec  libary created by make in the skpe-rec perl script. 

e.g: my $SKYPEREC = "/home/michael/work/skype-rec-kraken/libskype-rec.so"; 

close skype, and when you open it by running the perl script (i created a launcher for it with the command executed in a terminal /home/michael/work/skype-rec/./skype-rec)  ./skype-rec it will open skype and record the next conversation. After you close skype the script will convert the wav recording to mp3 and put it in the $HOME/skype-rec directory. very handy tool! 

get it here: [http://z0g.org/stuff/skype-rec-kraken.tar.bz2](http://z0g.org/stuff/skype-rec-kraken.tar.bz2)

Please bring up some other nice tools! It's still raining  :-? 

Cheers mtron

---

