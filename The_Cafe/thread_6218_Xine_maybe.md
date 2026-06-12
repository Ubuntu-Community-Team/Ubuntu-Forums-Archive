---
title: "Xine maybe?"
date: 2004-11-26
forum: The Cafe
---

### Post by poofyhairguy on 2004-11-26
Well, I've been playing with ubuntu for a week and I finally fixed the largest problem I had with warty- the lack of a video file player. I know why mplayer isn't included, but it sucks because all the deb packages of mplayer I have found don't work well in ubuntu for me. 

I know I can build it from source, but I wanted a debian derivative so that I could reach into that big bag of binary packages and never compile another program again! (aka: gentoo sounds like hell to me personallly)

finally today I found a solution that worked on both my machines- I installed Xine instead. Since there is no livna respitory for ubuntu (yet) to deliver custom mplayer packages, Xine is the next best thing (totem sux for me). Do you guys know why its not considered the big banana (or: Why is mplayer better?)? I don't.

Now when i set up ubuntu for my friends I'll use xine. Thank god for choice, it only mplayer was around I might have been forced to put icky fedora back on. (I really hate compiling)

What is yall's experiance with Xine. Is it the media solution ubuntu users like me- who don't give a rats ass about being legal- have been looking for?

---

### Post by poptones on 2004-11-26
Xine is the "engine" of totem but it's really stripped down. It's a shame you have to install "real xine" just to get access to such basic necessities as subtitles and zooming controls, but oh well. 

If you want to know how they're both different than mplayer, try dumping a dvd stream to your hard drive with xine. Or playing an AVI that's ever so slightly munged in the middle. Mplayer is, in my experience, about the most robust media player for ANY platform. It has the best "real world" coping skills and wlll almost always muddle through media files nothing else will play - which means you can also use it to re-save those broken files so the other players can handle them.

I don't use mplayer much as a general purpose player, but it's a fantastic tool to have on the command line.

---

### Post by Magneto on 2004-11-27
[QUOTE=poofyhairguy]

What is yall's experiance with Xine. Is it the media solution ubuntu users like me- who don't give a rats ass about being legal- have been looking for?[/QUOTE]

lol I like xine and I used it pretty exclusively in slackware including the xine browser plugin but the plugin sucked and now I use gmplayer for dvd's and long movies and xine for some others - Ogle is nice too, its a shame people have forgotten about Ogle

As far as I know there is nothing illegal about any of that- I know some issues against dvd decoding were answered when the mpaa lost that lawsuit - i thought most of this stuff about legality was not being able to redistribute software mainly

---

### Post by adbak on 2004-11-27
To get MPlayer, simply add ```
deb ftp://ftp.nerim.net/debian-marillat/ testing main
``` to your /etc/apt/sources.list.

Update Apt/Synaptic, and install.

---

### Post by poofyhairguy on 2004-11-28
[QUOTE=adbak]To get MPlayer, simply add ```
deb ftp://ftp.nerim.net/debian-marillat/ testing main
``` to your /etc/apt/sources.list.

Update Apt/Synaptic, and install.[/QUOTE]


tried. unstable, stable and testing. No dice. All of them gave me problems on any file.

But xine worked great, better than the fedora's livna mplayer. I was scared of it at first because totem is painful, but it is not!

---

### Post by poofyhairguy on 2004-12-01
Just to update, I've tried every media player I could find in the universe/multiverse+ third party repos, and I have a landslide winner.

gxine (the gnome xine) works better in ubuntu than any other media player. Its only flaw is that it lacks an icon in the menu, otherwise it works perfectly!

I even am using it as an mp3 player, as I believe it does this better than xmms. 


I recommend it highly!

---

### Post by jdodson on 2004-12-01
[QUOTE=Magneto]As far as I know there is nothing illegal about any of that- I know some issues against dvd decoding were answered when the mpaa lost that lawsuit - i thought most of this stuff about legality was not being able to redistribute software mainly[/QUOTE]

right, the law looks upon people differently than a distro. company like caninocal(sp?).  it seems to me to be perfectly legal to own decss and the w32codecs and mplayer on your machine.  or at least i do and hope it is
 :-o

---

