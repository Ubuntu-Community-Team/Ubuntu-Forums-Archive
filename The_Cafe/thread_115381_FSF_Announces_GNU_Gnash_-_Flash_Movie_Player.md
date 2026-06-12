---
title: "FSF Announces GNU Gnash - Flash Movie Player"
date: 2006-01-10
forum: The Cafe
---

### Post by mips on 2006-01-10
[http://www.fsf.org/news/gnash.html](http://www.fsf.org/news/gnash.html)

---

### Post by stoffe on 2006-01-10
Just saw that, excellent!

---

### Post by maruchan on 2006-01-10
I have a question. It says it uses OpenGL. Does this mean that we're even more reliant upon graphics chipset makers to support Linux now? I mean, the way I read that is "now if you want to use this Flash player with any speed, there's no way you can still use that slow 'nv' driver." To say nothing of ATI's dismal support record.

I love what OpenGL offers, of course, but I just want to make sure I'm understanding this correctly.

---

### Post by BWF89 on 2006-01-10
When the first stable version of it is released distros will finially have Flash support out of the box!

---

### Post by JimmyJazz on 2006-01-10
I have been waiting for this for years.  Dreams really do come true.

---

### Post by kaamos on 2006-01-10
> alaisi@ubuntu:~/gnash-0.7$ gnash
gnash: error while loading shared libraries: libbase.so.0: cannot open shared object file: No such file or directory

:(

EDIT: Fixed with
```
sudo ln -s /usr/local/lib/gnash/libbase.so.0.0.0 /usr/local/lib/libbase.so.0
sudo ln -s /usr/local/lib/gnash/libgeometry.so.0.0.0 /usr/local/lib/libgeometry.so.0
sudo ln -s /usr/local/lib/gnash/libserver.so.0.0.0 /usr/local/lib/libserver.so.0
```
:)

---

### Post by jc87 on 2006-01-10
By the way , besides out of the box flash  , what are the other advantages this will bring? i&#180;m just curious because i have no idea.

P.S. Go FSF , Get Busy :)

---

### Post by BWF89 on 2006-01-10
I just thought of something. How is it that were allowed to create a player that will play Flash movies and have it be 100% legal and under the GPL but we can't  (legally) include a media player with a distro that will play MPEG and WMV videos?

---

### Post by Maupertus on 2006-01-10
I just hope I can properly use it on my x64 box.

---

### Post by Lovechild on 2006-01-10
Yet again that FSF displays that it cannot pick a suitable license to save it's life, the viral nature of the GPL is simply not suitable for this kind of operation - what happens when your flash movie wants to hook up to something that allows it to play music (say mp3s).. well then that is required to be gpl'ed as well and following that you'll be in violation of several nice patents.

LGPL would be much saner for a project like this, hopefully they'll see the err of their ways, if they don't the users will suffer.

---

### Post by cylon359 on 2006-01-10
You miss the point of the GPL.

---

### Post by jobezone on 2006-01-10
[QUOTE=Lovechild]Yet again that FSF displays that it cannot pick a suitable license to save it's life, the viral nature of the GPL is simply not suitable for this kind of operation - what happens when your flash movie wants to hook up to something that allows it to play music (say mp3s).. well then that is required to be gpl'ed as well and following that you'll be in violation of several nice patents.
[/QUOTE]
I had a beautifull response which was wasted since I was not logged in:/ So let me just go to the point: it already supports mp3 (or it still has to be added, but will support it once it's done). And patents issues are totally unrelated to licenses. Any software, whichever license it uses, can "violate" software patents (in the countries where they are legal).

---

### Post by Kvark on 2006-01-11
[QUOTE=Lovechild]Yet again that FSF displays that it cannot pick a suitable license to save it's life, the viral nature of the GPL is simply not suitable for this kind of operation - what happens when your flash movie wants to hook up to something that allows it to play music (say mp3s).. well then that is required to be gpl'ed as well and following that you'll be in violation of several nice patents.

LGPL would be much saner for a project like this, hopefully they'll see the err of their ways, if they don't the users will suffer.[/QUOTE]
I couldn't find anything in the GPL that says GPLed programs are not allowed to comunicate with propriarity programs. Besides, the Lame mp3 encoder is GPLed so it wouldn't be a problem in this case.

But yeah the mp3 format is patented even if the encoder software is GPLed. I bet there are patent problems with the flash format too even if there is a GPLed player. This Gnash thing won't be entirely free unless it uses a free format like SVG to store the animated vector graphics but I guess the whole point of this is to use the flash format.

---

### Post by Breepee on 2006-01-11
It only mentions .swf, which is IIRC the shockwave format and pretty much not in use anymore. .fla is flash and support of that is far more crucial I think?

---

### Post by BoyOfDestiny on 2006-01-11
[QUOTE=Breepee]It only mentions .swf, which is IIRC the shockwave format and pretty much not in use anymore. .fla is flash and support of that is far more crucial I think?[/QUOTE]

SWF stand for Shockwave Flash.

From macromedia's flash player page

[http://www.macromedia.com/software/flashplayer/productinfo/faq/#item-3-3](http://www.macromedia.com/software/flashplayer/productinfo/faq/#item-3-3)
What is the Macromedia Flash File Format (SWF) Specification?

    This specification includes a set of tools for developers to write Macromedia Flash files, documentation of the Macromedia Flash file format (SWF), and code to write SWF files. Learn more about how to license and download the specification.

fla's aren't flash ([http://en.wikipedia.org/wiki/Macromedia_Flash](http://en.wikipedia.org/wiki/Macromedia_Flash))
'.fla files contain source material for the Flash application. Flash authoring software can edit FLA files and compile them into .swf files. Proprietary to Macromedia, the FLA format in no sense counts as "open".'

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-01-11
Unfortunately lovechild is right, the liscencing is a problem.

Just as a reminder, Ubuntu does not and can not ship with mp3 playback by default and the new liscenced gstreamer mp3 plugin can not be used with gpl'd applications, like rhythmbox or now gnash.

Some further info:
> GNU Flash
Frederic Crozat pointed me to a news article about GNU Flash today. My opinion is that GNU Flash is a mostly useless project due to its licensing. Flash today isn't just playing Flash animations, it also includes audio through mp3 support and 2-3 video codecs non of them free. Which means a GPL flash library will never be usefull is large parts of the world. People should instead get involved in Swfdec which is LGPL and already made to integrate with GStreamer. If GNU thinks flash support is important they should offer it under a license that doesn't make half their users wait 5 years before they can legally use it. Or if they wanted something to compete with Flash and which is free they should join up with librsvg and help improve it to become a Flash killer. Combining SVG with SMIL should create something very similar to Flash in capabilities. 
[http://blogs.gnome.org/view/uraeus/2006/01/10/0](http://blogs.gnome.org/view/uraeus/2006/01/10/0)

> Lets talk SWF. A lot of people seem to be mentioning Gnash today. Some seem to think it's a giant step for FSF. I think it's really funny. It's really funny (or sad - it depends how you look at it) how a giant win for FSF is taking a wonderful Public Domain project and basically just releasing it under GNU GPL.

So Christian, GNU Flash and Gnash at least were technically two different projects. GNU Flash is (was?) technically GPLFLash2 which is LGPL licensed (how confusing can you get, eh?), while Gnash is using a relicensed Public Domain SWF decoding library making the whole thing GPL. gameswf has been put in the Public Domain so assigning copyrights to FSF and relicensing everything without making any substantial changes is completely legal. In my opinion morally it's not the most wonderful thing one could do though. 
[http://www.kdedevelopers.org/node/1736](http://www.kdedevelopers.org/node/1736)

---

### Post by Lovechild on 2006-01-11
I am right, as per the gpl requirement of RANT-royalty free patent redistribution license - this demand would virally apply to everything GNASH links to including the mp3 support library - thus causing the problem since that requirement isn't forfilled for that library.

That being said there are several Flash reimplementations out there, swfdec, gpl flash2 and now GNASH - what I wonder is why are we reimplementing it so many times, and why hasn't anyone thought up an open replacement for flash all together - Flash is the horror that haunts the net and it's a somewhat closed standard, we really do need an open standard replacement.

---

### Post by jobezone on 2006-01-11
As far as I understand, no media player, be it GPL or not, be it based on gstreamer or xine, can by default play patented codecs like mp3, unless their creators have been given permission by the patent holder to use it.

Proprietary software developers are usually in an advantageous position to have the have the money and status to get this permission, but Fluendo has managed to do this, and will (or has already?) release a MIT licensed mp3 codec with permissions for distributions to include it by default without royalties.
Fluendo people say it can be released as a plugin and part of the LGPLed gstreamer, but that problems may arise as far as GPLed programs.
EDIT:Fluendo's mp3 : [http://www.fluendo.com/resources/fluendo_mp3.php](http://www.fluendo.com/resources/fluendo_mp3.php)

Nevertheless, I think that since alternatives exist, and they're even better than mp3, and ogg support in many portable players already exist, there is little reason to keep hanging on to it.

As far as gnash, or other GPL flash players, I see no trouble in having to install mp3 support afterwards, like it's already the case with media players in Ubuntu and other distributions.EDIT:Patents are bad for all, either free or proprietary software developers. Greater things would arise if, for example, future pushes for software patents in the EU are stopped, pushes for software patents reform in the US are made, and unpantented alternatives to all of these are used (and created when none exists, like a full authoring program+format for animation and easy applications on the web, like shockwave and flash).

This is my opinion, and I'm no gnu/linux developer, so...

Last EDIT:Yep, it seems the GPL has a clause that the software it is licensing cannot contain parts which have patents (or patent royalties?), which explains why the support of mp3, etc., is taken out or not put in by distributions carrying GPL media players.

---

### Post by mips on 2006-01-11
[QUOTE=BWF89]I just thought of something. How is it that were allowed to create a player that will play Flash movies and have it be 100% legal and under the GPL but we can't  (legally) include a media player with a distro that will play MPEG and WMV videos?[/QUOTE]

With great difficulty.

One method involves reverse engineering. You would have two teams, A&B, working on the project.

Team A reverse engineers the code, from the code they write up a specification. The specification document is checked by Patent & intellectual property right lawyers to ensure nothing in that document contains anything that infringes on the original patent.

Team B takes the specification and writes new code based on the document produced by team A. This ensures team B uses no know code or patent technology to write the new code.

Basically called a clean room design or chinese wall.

This was the method used to write the new broadcom wireless drivers.

[http://en.wikipedia.org/wiki/Clean_room_design](http://en.wikipedia.org/wiki/Clean_room_design)

---

### Post by Ubuntu_User on 2006-01-12
[QUOTE=maruchan]I have a question. It says it uses OpenGL. Does this mean that we're even more reliant upon graphics chipset makers to support Linux now? I mean, the way I read that is "now if you want to use this Flash player with any speed, there's no way you can still use that slow 'nv' driver." To say nothing of ATI's dismal support record.

I love what OpenGL offers, of course, but I just want to make sure I'm understanding this correctly.[/QUOTE]
Using OpenGL doesn't mean that you have to have a 3D accelerated graphics cards. There are software OpenGL implementation that will play nicely even if you don't even have a 3D accelerated graphics card.

---

### Post by Zotova on 2006-01-12
Anyone know if it will have support for flash 8?

---

### Post by mips on 2006-01-13
Mentions v7 compliance.

---

### Post by dabear on 2006-01-13
Could anybody who got it to compile provide a deb ("checkinstall")? Just wanna try it out..

---

### Post by frühstück on 2006-01-31
> Or if they wanted something to compete with Flash and which is free they should join up with librsvg and help improve it to become a Flash killer. Combining SVG with SMIL should create something very similar to Flash in capabilities.

[http://blogs.gnome.org/view/uraeus/2006/01/10/0](http://blogs.gnome.org/view/uraeus/2006/01/10/0)


Why would anyone want to compete with Flash?

Flash was first, Flash wins \\:D/

---

