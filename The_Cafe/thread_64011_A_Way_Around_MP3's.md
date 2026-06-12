---
title: "A Way Around MP3's"
date: 2005-09-09
forum: The Cafe
---

### Post by drizek on 2005-09-09
I installed breezy and lame is not in the repositories. so i remembered once i heard someone talking about running foobar2000 in wine under linux and it working very well, so i decided to try it out. It works great, the sound quality is excellent, and foobar itself is a great little app.

but i dont think it is entirely opensource [http://www.foobar2000.org/license.html](http://www.foobar2000.org/license.html)

the lack of mp3 support in ubuntu is a pretty big deal for a lot of people. so while foobar under wine is not perfect, and its not pure opensource, i think it would be a good "stopgap" solution to people wanting to play mp3's out of the box.

---

### Post by macgyver2 on 2005-09-09
[QUOTE=drizek]the lack of mp3 support in ubuntu is a pretty big deal for a lot of people. so while foobar under wine is not perfect, and its not pure opensource, i think it would be a good "stopgap" solution to people wanting to play mp3's out of the box.[/QUOTE]
If I understand the intent of Mr. Shuttleworth and the rest of his development team, it's 100% free/libre or it's no go for inclusion in the main repos and the default install...no 'pretty close' or anything like that.  Also, if you have to run it under wine it's not gonna be OOB anyway...I guess I'm just not grasping where you're going with this one...

---

### Post by Kvark on 2005-09-09
There is legal issues around the mp3 format and many other media codecs that prevents Ubuntu from including them out of the box. So that program wouldn't be a solution for those who want mp3 support out of the box since it can't be included out of the box due to those legal issues.

The only solution is to use another file format for music, like ogg that has better compression or flac that is lossless.



BTW, a way to play MP3s without wine is...
1. [http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories)
2. [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)
3. Install and try the different media players that can be found in synaptic to see which one you like best.

---

### Post by poofyhairguy on 2005-09-09
[QUOTE=drizek]
the lack of mp3 support in ubuntu is a pretty big deal for a lot of people. so while foobar under wine is not perfect, and its not pure opensource, i think it would be a good "stopgap" solution to people wanting to play mp3's out of the box.[/QUOTE]

If your distro does not pay (free distros can't) there is only one way to have a legal MP3 player in Linux - the Real Player (Real paid the license fee for us all). But because that part is not open source it will not be included in the default Ubuntu.

Thanks for you idea, and please note that you don't have to emulate Windows programs to play MP3s in Ubuntu.

---

### Post by xequence on 2005-09-09
I tried to play iTunes in crossover office... It installed good, though took along time. It was really slow to load and do anything and it didnt play any sound. My XP partition doesent have a sound driver so I cant use iTunes on it... I woudent ever buy music from itunes, just ive head the player is good. Ill just stick to rythmbox ;)

---

### Post by Adrenal on 2005-09-09
[QUOTE=xequence]I tried to play iTunes in crossover office... It installed good, though took along time. It was really slow to load and do anything and it didnt play any sound. My XP partition doesent have a sound driver so I cant use iTunes on it... I woudent ever buy music from itunes, just ive head the player is good. Ill just stick to rythmbox ;)[/QUOTE]
 Just install mp32ogg
You can convert your music to ogg vorbis, which is a free (as in free beer *and* free speech) codec

---

### Post by drogoh on 2005-09-09
[QUOTE=Adrenal]Just install mp32ogg
You can convert your music to ogg vorbis, which is a free (as in free beer *and* free speech) codec[/QUOTE]

Good advice but transcoding from one lossy format to another is going to put artifacts in your music.  You'd be better off encoding from WAV or the original album if you have access to it.  Else, I'd say compile programs on your own with MP3 support (if one is so inclined and feels comfortable to do so (yes, I know it's messy but transcoded MP3s are too :p)).

---

### Post by drizek on 2005-09-09
[QUOTE=poofyhairguy]If your distro does not pay (free distros can't) there is only one way to have a legal MP3 player in Linux - the Real Player (Real paid the license fee for us all). But because that part is not open source it will not be included in the default Ubuntu.

Thanks for you idea, and please note that you don't have to emulate Windows programs to play MP3s in Ubuntu.[/QUOTE]

i know that. i only tried it because one of the backports mirrors was down(or i made a typo in my sources.list) so i couldnt install codecs. 

and amarok/rhythymbox > itunes anyway. dont lose any sleep over it. youre better off without it.

---

### Post by xequence on 2005-09-09
> Just install mp32ogg
You can convert your music to ogg vorbis, which is a free (as in free beer and free speech) codec

As the person said under you, one lossy to another lossy is very lossy ;)

> Good advice but transcoding from one lossy format to another is going to put artifacts in your music. You'd be better off encoding from WAV or the original album if you have access to it. Else, I'd say compile programs on your own with MP3 support (if one is so inclined and feels comfortable to do so (yes, I know it's messy but transcoded MP3s are too :p)). 

And I am not going to do much ripping. I dont use CDs, and I dont have access to the originals :P And only mp3 works in my mp3 player... (And atrac3, but who is ever going to use that? Stupid sony ;))

I only wanted itunes because people said it is really good for organizing and playing music.

---

### Post by az on 2005-09-09
[QUOTE=drizek]I installed breezy and lame is not in the repositories.

...

so while foobar under wine is not perfect, and its not pure opensource, i think it would be a good "stopgap" solution [/QUOTE]


Lame is in multiverse.  It is LGPL free libre open source software.  The software is free, but the format has restrctions on it in many countries.


[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=lame](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=lame)


You may also install gstreamer-plugins and gstreamer ffmpeg and have mp3 and mp4(mpeg) support through gstreamer as well.

[http://packages.ubuntu.com/hoary/libs/gstreamer0.8-ffmpeg](http://packages.ubuntu.com/hoary/libs/gstreamer0.8-ffmpeg)

---

### Post by NoTiG on 2005-09-09
since there is an mp3 to ogg... and it compresses the file twice.. which results in a loss of quality.. is there an mp3 to flac, that doesnt lose quality ?

---

### Post by Adrenal on 2005-09-09
[QUOTE=NoTiG]since there is an mp3 to ogg... and it compresses the file twice.. which results in a loss of quality.. is there an mp3 to flac, that doesnt lose quality ?[/QUOTE]
 gnormalize converts to wav first, then ogg

---

### Post by Galoot on 2005-09-09
[QUOTE=Adrenal]gnormalize converts to wav first, then ogg[/QUOTE]
That's still adding lossy to lossy, though, like copying a CD to tape (analogous to ripping to MP3), then copying that to CD-R (analogous to MP3 -> WAV) then to a different tape (analogous to WAV -> OGG).

---

### Post by drogoh on 2005-09-09
[QUOTE=NoTiG]since there is an mp3 to ogg... and it compresses the file twice.. which results in a loss of quality.. is there an mp3 to flac, that doesnt lose quality ?[/QUOTE]

There is no way to "not lose quality" when transcoding one format to another.  The only thing you'll gain by transcoding MP3 to FLAC is that your disk space usage in df will go up.  I still think the end user would be better off deviating and manually adding in MP3 support if they have needs or desires for it, my $0.02 anyway.


Say it with me (everybody!):  "Transcoding is bad."

---

### Post by UbuWu on 2005-09-10
[QUOTE=NoTiG]since there is an mp3 to ogg... and it compresses the file twice.. which results in a loss of quality.. is there an mp3 to flac, that doesnt lose quality ?[/QUOTE]

mp3 to flac will neither lose or gain quality, but it will take more disk space.

---

