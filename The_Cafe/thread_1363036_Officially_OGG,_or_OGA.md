---
title: "Officially OGG, or OGA?"
date: 2009-12-23
forum: The Cafe
---

### Post by kevin11951 on 2009-12-23
Is the official suffix for ogg vorbis (audio) files .ogg or .oga?

---

### Post by Hwæt on 2009-12-23
Did something change? Every Ogg Vorbis file I've seen is .ogg.

---

### Post by LeifAndersen on 2009-12-23
Same here, the only divergence I've heard from .ogg, is .ogv, for ogg theora.

---

### Post by Sef on 2009-12-23
Read [Wikipedia ]("http://en.wikipedia.org/wiki/Ogg")on the difference between .ogg and .oga.

> The term ‘Ogg’ is commonly used to refer to audio file format Ogg Vorbis, that is, Vorbis-encoded audio in the Ogg container. Previously, the .ogg file extension was used for any content distributed within Ogg, but as of 2007, the Xiph.Org Foundation requests that .ogg be used only for Vorbis due to backward compatibility concerns. The Xiph.Org Foundation decided to create a new set of file extensions and media types to describe different types of content such as .oga for audio only files, .ogv for video with or without sound (including Theora), and .ogx for applications.[3]

---

### Post by LeifAndersen on 2009-12-23
ogx for applications?  What kind of applications would you be putting in a media container format!?!

---

### Post by MaxIBoy on 2009-12-24
Gedit.ogx: Open it with VLC, hit play, edit text files with it! Great plan, guys!

Seriously though, maybe it's some kind of no-installation-required software package format?

---

### Post by cascade9 on 2009-12-24
> **Sef said:**
> Read [Wikipedia ]("http://en.wikipedia.org/wiki/Ogg")on the difference between .ogg and .oga.

Or read the xiph.org guidelines that Sefs wikipedia quote is referencing- 

[http://wiki.xiph.org/index.php/MIME_Types_and_File_Extensions](http://wiki.xiph.org/index.php/MIME_Types_and_File_Extensions)

> **  .oga - audio/ogg **

 
[LIST]
[*] Ogg Audio Profile (audio in Ogg container)
[*] Applications supporting .oga, .ogv SHOULD support decoding from muxed Ogg streams
[*] Covers Ogg [FLAC]("http://wiki.xiph.org/FLAC"), [Ghost]("http://wiki.xiph.org/Ghost"), and [OggPCM]("http://wiki.xiph.org/OggPCM")
[*] Although they share the same MIME type, Vorbis and Speex use different file extensions.
[*] SHOULD contain a Skeleton logical bitstream.
[*] Vorbis and Speex may use .oga, but it is not the prefered method of distributing these files because of backwards-compatibility issues.
[/LIST]
 **  .ogg - audio/ogg **

 
[LIST]
[*] Ogg Vorbis I Profile
[*] .ogg applies now for Vorbis I files only
[*] .ogg has more recently also been used for Ogg FLAC and for Theora, too — these uses are deprecated now in favor of .oga and .ogv respectively
[*] has been defined in [RFC 3534]("http://tools.ietf.org/html/rfc3534") [http://www.ietf.org/rfc/rfc3534.txt](http://www.ietf.org/rfc/rfc3534.txt) for application/ogg, so rfc 3534 will be re-defined
[/LIST]
 RATIONALE: .ogg has traditionally been used for Vorbis I files, in particular in HW players, hence it is kept for backwards-compatibility 



.ogg is the offical .xiph naming for ogg vorbis.

---

### Post by 3rdalbum on 2009-12-24
Mozilla still has downloadable videos with a ".ogg" extension; so Gnome puts a music note icon on them.

---

### Post by Ozor Mox on 2009-12-24
Rhythmbox went through a period of ripping my CDs to .oga but I think they are back to .ogg again now.

---

### Post by gnomeuser on 2009-12-24
Perhaps we should file a bug against Ubuntu to bring consistency to the subject. If upstream specifically requests that we use the .ogX extensions then we should review the relevant applications in the repo and ensure that they support these both for import and for playback as well as making it the default.

*edit*

And here we go:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/500145](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/500145)

---

### Post by zekopeko on 2009-12-24
The major problem was that ogg could have video only or audio only or a mix.
So very confusing for users and applications that didn't read the header.
oga and ogv are far better descriptions because you can know just by looking at the extension whats in it.

---

### Post by LeifAndersen on 2009-12-24
Meh, I think extensions are the old way of denoting file types.  Any modern OS should be able to determine the file type, and show you the extension.  With that being said though, I still like extensions, it makes using the terminal much easier.

> **Ozor Mox said:**
> Rhythmbox went through a period of ripping my CDs to .oga but I think they are back to .ogg again now.

He, he.  You make it sound like Linux is sentient.

---

### Post by phrostbyte on 2009-12-24
> **LeifAndersen said:**
> Meh, I think extensions are the old way of denoting file types.  Any modern OS should be able to determine the file type, and show you the extension.  With that being said though, I still like extensions, it makes using the terminal much easier.



He, he.  You make it sound like Linux is sentient.

[http://www.youtube.com/watch?v=AQtu8gm7lJU](http://www.youtube.com/watch?v=AQtu8gm7lJU)

---

