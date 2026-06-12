---
title: "Theora , good alternative open source or not?"
date: 2005-10-18
forum: The Cafe
---

### Post by JuanC on 2005-10-18
Hi to all,

I saw that [Theora](http://www.theora.org) is the open source container , video codec and for audio codec uses ogg , so is free license and open source.

But i didn't show any clips or movies encode in [Theora](http://www.theora.org) , no streaming videos (i know that Theora support streaming) , no good encode tool (all i saw are command line without gui) , ...

Is Theora a good alternative open source or an obsolete project?

I also didn't saw any partner or company that support Theora project.

---

### Post by Kimm on 2005-10-18
Usualy when you download a video clip from a site that supports Open Source (like GNU) it will be encoded in Theora. Its not an absolete project and its an excelent format... so I suggest you use that, no patents or copyrights to worry about anyway, and anyone can play it. As far as I know comprimation is good.

---

### Post by Lovechild on 2005-10-18
Ogg is the container, Theora is the video codec and Vorbis is the audio codec - and I believe the rule my world!

---

### Post by az on 2005-10-18
I think any gui that supports Gstreamer codecs can use Theora.

---

### Post by JuanC on 2005-10-19
[QUOTE=azz]I think any gui that supports Gstreamer codecs can use Theora.[/QUOTE]

I don't know any one.

It would be cool if ubuntu project create or support a Theora Video Converter (with GUI) application , that you can input avi , mpg , .. files and an easy way in this application you can choose the bitrate for audio and video or you can choose the final size of the file and then this application make the Theora file you want.

---

### Post by asimon on 2005-10-19
I remember downloading a couple of theora videos of some talks (I think from Mark Shuttleworth and other Ubuntu developers). Neither totem nor mplayer were able to skip forward/backward. I could only watch them like a stream. Is this a general defect of theora or was it just those specific videos?

---

### Post by Malphas on 2005-10-19
Alternatively you could use a Matroska container, XviD video stream and Vorbis for audio.

---

### Post by Lovechild on 2005-10-19
[QUOTE=Malphas]Alternatively you could use a Matroska container, XviD video stream and Vorbis for audio.[/QUOTE]

XViD is patent encumbered as it is an MPEG4 implementation, sorry

---

### Post by Lovechild on 2005-10-19
[QUOTE=asimon]I remember downloading a couple of theora videos of some talks (I think from Mark Shuttleworth and other Ubuntu developers). Neither totem nor mplayer were able to skip forward/backward. I could only watch them like a stream. Is this a general defect of theora or was it just those specific videos?[/QUOTE]

This is likely to be an issue with Theora which was fixed recently, Schaller blogged about it a while ago, or a gstreamer AV sync error (which will be fixed when GStreamer 0.9/0.10 is deployed)

---

### Post by Malphas on 2005-10-19
[QUOTE=Lovechild]XViD is patent encumbered as it is an MPEG4 implementation, sorry[/QUOTE]
That is correct.  However, XviD itself is open source and MPEG-4 is basically just a set of standards, not quite as free as Theora but hardly WMV either.  It does have the advantage of being better quality though.

---

### Post by GeneralZod on 2005-10-19
The BBC's "Dirac" project may end up being another one to watch:

[http://dirac.sourceforge.net/index.html](http://dirac.sourceforge.net/index.html)

---

### Post by Lovechild on 2005-10-19
[QUOTE=Malphas]That is correct.  However, XviD itself is open source and MPEG-4 is basically just a set of standards, not quite as free as Theora but hardly WMV either.  It does have the advantage of being better quality though.[/QUOTE]

You are still not able to use either legally

---

### Post by az on 2005-10-19
[http://www.pitivi.org/](http://www.pitivi.org/)
[http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3) (I think)

I know there are a few others...

---

### Post by The Warlock on 2005-10-19
[QUOTE=Lovechild]You are still not able to use either legally[/QUOTE]

Well, this really hasn't been actually tested.

---

### Post by Lovechild on 2005-10-19
[QUOTE=The Warlock]Well, this really hasn't been actually tested.[/QUOTE]

I don't need testing to know that violating the patents in either format is illegal in places that aknowledge software patents.

Just stop debating this - you cannot make a case for the legality of violating patents when you have to factor in that on this issue we have to aim for the lowest common denominator.

Was this about technical merit, XViD would certainly be a contender as it's an excellent format, sadly it's not.

---

### Post by poptones on 2005-10-19
*I don't need testing to know that violating the patents in either format is illegal in places that aknowledge software patents.*

The MPEGLA explicitly states that the first 50,000 units are "free." It may be a violation of IP law for a company to distribute the working technology without paying royalties, but there is absolutely nothing "illegal" about individuals making use of it. Not technically, and not literally - The license is written so as to apply only to larger entities. You're not even bound by the content use part of the license until you have over 50,000 subscribers to your (for example) video blog.

---

### Post by JuanC on 2005-10-19
I found an ogg theora videos in :
[http://commons.wikimedia.org/wiki/Category:Video](http://commons.wikimedia.org/wiki/Category:Video)

[QUOTE=asimon]I remember downloading a couple of theora videos of some talks (I think from Mark Shuttleworth and other Ubuntu developers). Neither totem nor mplayer were able to skip forward/backward. I could only watch them like a stream. Is this a general defect of theora or was it just those specific videos?[/QUOTE]

Have you try VLC to view this video?

I use VLC and works skip forward/backward.

> XViD is patent encumbered as it is an MPEG4 implementation, sorry

I also like the idea of Theora , Open Source and Free-patent video codec for all uses.

> [http://www.pitivi.org/](http://www.pitivi.org/)
 [http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)

Too complicated for me , i like one similar to Avidemux or more easy ...

---

### Post by asimon on 2005-10-19
[QUOTE=JuanC]Have you try VLC to view this video?

I use VLC and works skip forward/backward.
[/QUOTE]
No, I never used VLC, but I'll try it. Anyway I no longer have those theora videos around. Those were just some talks which I deleted after I've watched them. But as Lovechild wrote, could have been some bugs which may already be fixed.

---

### Post by JuanC on 2005-10-25
Any Theora Editor GUI that makes easy Cut Frames in ogg , Paste Frames ogg , Mux ogg , Demux ogg , ... ?

---

### Post by Lovechild on 2005-10-25
[QUOTE=JuanC]Any Theora Editor GUI that makes easy Cut Frames in ogg , Paste Frames ogg , Mux ogg , Demux ogg , ... ?[/QUOTE]


Like pitivi or diva?

---

### Post by JuanC on 2005-10-25
[QUOTE=Lovechild]Like pitivi or diva?[/QUOTE]

I find this for diva : [http://diva.mdk.org.pl/](http://diva.mdk.org.pl/) , looks good but this is an early software and i don't see any mention to ogg Theora.

For ptivi : [http://www.pitivi.org/](http://www.pitivi.org/) , I also don't find any mention to ogg Theora.

---

### Post by MetalMusicAddict on 2005-10-25
Does Theora support Hi-Def resolutions? I was wondering if they are working on anything like DivX6. A DVD like video file.

Open-Source DVD. That would be cool to see. I dont see why it wouldnt be possible if the hardware support was there. There are tons of players that do DivX/XviD.

---

