---
title: "theora or xvid"
date: 2006-02-14
forum: The Cafe
---

### Post by sup on 2006-02-14
I just happen to have some DVD I would like to back up. I Gathered I can use either dvdrip or thoggen. Thoggen uses theora/ogg, when dvdrip have more possibilities, xvid for example, but is lacking theora. I would for obvious reasons like to use free codecs (and both xvid and theora are free, although the former has some issues, as far as I gathered). Which one should I use? Or are there any other possibilities?

Also, I would then like to role up the whole thing with matroska container (I hope mmg as a part of mkvtoolnix will do all I need for me) - as far as I understand, it is better and more free than OMG - with that in mind, what is better way? Or is there any alternative?

---

### Post by sapo on 2006-02-14
xvid, cause you can play them on some dvdplayers like one made by philips.. and everyone have a xvid codec, no matter in what operating system.

I dont know about quality. but xvid is better if you think about the compatibility

---

### Post by xequence on 2006-02-14
Xvid has always been great for me. You can fit a movie into 700MB and it will be great quality.

---

### Post by Lovechild on 2006-02-14
xvid isn't free - it's patent encumbered.

---

### Post by Lovechild on 2006-02-14
[http://schrodinger.sourceforge.net/](http://schrodinger.sourceforge.net/)

---

### Post by kingsidy on 2006-02-14
like everybody said, xvid. good quality plus it is more widespread

---

### Post by JuanC on 2006-02-16
I think XviD is better for dvdbackups , you can watch on a lot of dvdplayers and use Theora for the rest.

I like so much Theora , i think ubuntu team would focus more in this format , It seems a lack of GUI encoders / editors of this format.

I would like someone make a program like [Avidemux](http://avidemux.sourceforge.net) that can use Theora.

---

### Post by Malphas on 2006-02-16
Best quality and compatibility: x264 video, FAAC audio, MP4 container.  Or if sharing with others or playback on standalones isn't required then x264, Vorbis and Matroska would also be acceptable.  If you want to go the completely free route and don't mind a significant drop in video quality then go with Theora, Vorbis, OGM.

Also, I would forget about Dirac for now.  It has potential but is probably too early in development to be practical right now, the quality isn't up to scratch and it's far less widely supported than the other options.  Another one to look out for is [Snow]("http://forum.doom9.org/showthread.php?s=&threadid=84593&").

---

### Post by pmj on 2006-02-16
I say the best combination is still XviD and MP3 in AVI. Theora is nowhere near as good as XviD quality-wise, and if you go with x264 and Matroska you're going to have trouble playing them in many players.

For example, pretty much none of the anime in x264 and Matroska I have plays in totem-xine on Breezy, and it's often glitchy in VLC. I have to use mplayer for it.

---

### Post by Malphas on 2006-02-16
I've never had any problems using VLC.  It could possibly be the fault of the person doing the encoding rather than the codecs and container.  And AVI is ridiculously archaic.

---

### Post by pmj on 2006-02-16
It is, but it works well enough (and more importantly, it works everywhere) as long as you don't need multiple audio streams and subtitles and stuff like that.

---

### Post by sup on 2006-02-21
> Best quality and compatibility: x264 video, FAAC audio, MP4 container. Or if sharing with others or playback on standalones isn't required then x264, Vorbis and Matroska would also be acceptable. If you want to go the completely free route and don't mind a significant drop in video quality then go with Theora, Vorbis, OGM.
Matroska is not free? 

Anyway, as far as I understand, it stands as follows:
Since compatibility is not such an issue (I am planning on buying some kind of barebone system with linux for playing dvds and like stuff) 
Considering quality x264 is the best, followed with xvid, then divx and Theora at the end, others being in still in experimental phase.
Or is x264 still to immature?

Considering moral issues, theora would be the best, divx the worst and x264 and xvid somewhere between, since they are open source but use some patents.

Containers - is there anything better than Matroska? (Nothing such seems to be out there if we are to believe wikipedia:[http://en.wikipedia.org/wiki/Comparison_of_container_formats]("http://en.wikipedia.org/wiki/Comparison_of_container_formats"))



Software(GUI, not that I would not like command line, but...): for matroska, mkvmerge with gui works fine. 
For ripping, dvd::rip could be used, but for me, DVD Decrypter under Wine works very well. But what can I use for subtitles and converting those ugly .VOB files I get from DVDs to something more usable? Avidemux? VirtualDbuMod (works fine with wine) Kino? Something completely different?

And one thing I am not sure about - are video and audio handled separetly or together?

I find it hard to get some basic info for someone completely new in this area, there are so many possibilities that one just do not know, what try first. Here [http://www.doom9.org]("http://www.doom9.org") seems to be lots of informations, but it is windows-centric...

---

### Post by mcpish on 2006-03-03
I'd like to start using mp4 containers for my video files with x264 video and aac audio.  I know I can encode x264 with mencoder (I've done it a lot of times) and I can encode aac audio with faac, but what programme do I use to merge the audio/video together into an .mp4 container?

---

### Post by SVFUSiON on 2006-03-03
xvid, just because it rocks. \\:D/ .

---

### Post by Malphas on 2006-03-03
[QUOTE=mcpish]I'd like to start using mp4 containers for my video files with x264 video and aac audio.  I know I can encode x264 with mencoder (I've done it a lot of times) and I can encode aac audio with faac, but what programme do I use to merge the audio/video together into an .mp4 container?[/QUOTE]
mkvtoolnix.



Also, because I missed this when it was first posted:

[QUOTE=sup]Matroska is not free?[/QUOTE]
Where did I say that?  Matroska is entirely free to my knowledge.

[QUOTE=sup]Or is x264 still to immature?[/QUOTE]
No, I wouldn't say so at all.

[QUOTE=sup]Containers - is there anything better than Matroska?[/QUOTE]
Not to my knowledge - for your needs anway.  If playback on standalones was a requirement then MP4 might have the advantage.

---

### Post by sup on 2006-03-03
> Quote:
mkvtoolnix.
Wait o moment, you got me confused here, is not mkvtoolnix supposed to produce matroska files? I seems so to me, but I have always used GUI only.

> Where did I say that? Matroska is entirely free to my knowledge.
well, I probably misread you here:

> Best quality and compatibility: x264 video, FAAC audio, MP4 container. Or if sharing with others or playback on standalones isn't required then x264, Vorbis and Matroska would also be acceptable. If you want to go the completely free route and don't mind a significant drop in video quality then go with Theora, Vorbis, OGM.
Since you said that to be completely free, I should go for ogm and not matroska, I deduced Matroska was not free (which suprprised me a lot). Otherwise I do not see reason to use OGM (since it has not been developed for several years now, I was said) 

> No, I wouldn't say so at all.
I see, but avbidemux support for it is not very good, right? They say so on project's page. I do not like command line that much.

> For ripping, dvd::rip could be used, but for me, DVD Decrypter under Wine works very well. But what can I use for subtitles and converting those ugly .VOB files I get from DVDs to something more usable? Avidemux? VirtualDbuMod (works fine with wine) Kino? Something completely different?

And one thing I am not sure about - are video and audio handled separetly or together?

I will just answer my own questions
Avidemux with decrypted files works just fine, and OCR tool in it is the best I have tried so far, but there is no need for it since media players like Mplayer can read vodsub files, co you can attatch them you mkv files using mmg.

And audio and video are handled together.

---

### Post by Malphas on 2006-03-03
[QUOTE=sup]Since you said that to be completely free, I should go for ogm and not matroska, I deduced Matroska was not free (which suprprised me a lot). Otherwise I do not see reason to use OGM (since it has not been developed for several years now, I was said)[/QUOTE]
Ah right, well just to clear everything up what I meant was the best quality you could get (in my opinion) is x264, Vorbis and Matroska, best quality whilst allowing playback on standalones/conforming to some sort of standard would be x264, FAAC and MP4 and the totally free option would be Theora, Vorbis and OGM - of course Theora, Vorbis and MKV would also be totally free (the reason x264, Vorbis and MKV isn't free is because of x264 rather than Matroska), I just never thought of it, and to be honest I don't really see the point.

Of course if I were being more precise, FAAC probably isn't the highest quality codec for AAC, but I was trying to stick to open source alternatives where possible (also, trying to use Nero AAC or whatever might not be viable under Linux).  Another alternative I forgot would be Snow, Vorbis, Matroska; the drawback though is that Snow - although being more mature than Dirac and Tarkin, and offering superior quality to Theora - is still in early development and the authors don't reccommend using it for archival purposes yet.  Could be fun to play around with though.

---

### Post by GreyFox503 on 2006-03-04
[quote=Lovechild]xvid isn't free - it's patent encumbered.[/quote]

Can you link to sources?  I didn't think this was true.

---

### Post by sup on 2006-03-04
> Can you link to sources? I didn't think this was true.
first match to google "xvid patent encumbered" gave me this, I hope statement on xvid developers mailing list is sufficient.

malphas: I understand, thanks for the clarification.

---

### Post by Buffalo Soldier on 2006-04-07
[QUOTE=sup]first match to google "xvid patent encumbered" gave me this, I hope statement on xvid developers mailing list is sufficient.

malphas: I understand, thanks for the clarification.[/QUOTE]

[http://www.xvid.org/modules.php?op=modload&name=FAQ&file=index&myfaq=yes&id_cat=2](http://www.xvid.org/modules.php?op=modload&name=FAQ&file=index&myfaq=yes&id_cat=2)

> I plan to use XviD in my own program and I'm going to modify it. Do I have to distribute my program as "open source" then?

Yes, XviD is released under the GNU GPL license which requires that all derived work from XviD also has to be distributed under the terms of the GNU GPL. A derived work, as defined in the GNU GPL, is a software that links (statically or dynamically) against XviD or includes XviD.

---

### Post by cvmostert on 2006-05-27
This post is editid by me... cvmostert.. 

I am sorry for my behaviour.

I was trying to come up for someone i dont eaven know and about something that has nothing to do with me.

again, sorry and this will not happend again.
c

---

### Post by matthew on 2006-05-27
[quote=cvmostert]Well this is one thread gone sour, thanks to malphas...[/quote]The post previous to yours was a month and a half old...was it really necessary to revive this thread just so you could violate the [forum policy]("http://ubuntuforums.org/index.php?page=policy") on posting by making a personal attack?? Consider yourself warned.

---

