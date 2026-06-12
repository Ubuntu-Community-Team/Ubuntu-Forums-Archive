---
title: "Is there a GOOD video editor for gnu/linux?"
date: 2008-08-16
forum: The Cafe
---

### Post by Somenoob on 2008-08-16
Can handle and convert various video formats/codecs * 
Editing is *simple* *
Not abstruse or complicated in any way *  

That's the criteria that a good video editor should meet. As much as I love OS software, every single linux-based video editor I've used so far has been a piece of crap. Don't recommend Kino, what's so special about it? it often fails at importing and editing is too hard and I don't feel like going trough a long learning curve I just want it to be self-explanatory.  

Are there any good ones out there?

---

### Post by Warpnow on 2008-08-16
MainActor was good but production has stopped on it.

---

### Post by MaxIBoy on 2008-08-16
Kdenlive is terrific, as far as I can tell, but I haven't gotten it to run more than a minute without crashing. I don't think it likes my computer.

---

### Post by Superkoop on 2008-08-16
[ffmpeg]("http://www.linuxjournal.com/video/linux-howto-video-editing-magic-ffmpeg")

Not really that simple, but after you get used to using it, it's not too bad (at least it works for me, where as most programs fail somewhere along the way). For most of the instructions, just run a man ffmpeg.

---

### Post by Somenoob on 2008-08-16
> **Superkoop said:**
> [ffmpeg]("http://www.linuxjournal.com/video/linux-howto-video-editing-magic-ffmpeg")

Not really that simple, but after you get used to using it, it's not too bad (at least it works for me, where as most programs fail somewhere along the way). For most of the instructions, just run a man ffmpeg.

lol, a CLI video editor? i'd rather cut the actual microfilm with scissors.

---

### Post by Cresho on 2008-08-16
avidemux.  go to [http://www.getdeb.net/search.php?keywords=avidemux](http://www.getdeb.net/search.php?keywords=avidemux)

download the avidemux and avidemux common.  Do not use qt as this is for kde.

here are my notes to force enable all codecs.  The defaults only give you a few measily ones.

if you want to enable full codec support, in terminal "avidemux" or change the application executable to avidemux. you can verify this by Help->built in support.

what this application does is splice stuff or puts stuff together.

here is my tutorial

[http://forums.steves-digicams.com/forums/view_topic.php?id=594710&forum_id=27](http://forums.steves-digicams.com/forums/view_topic.php?id=594710&forum_id=27)

I use a sanyo HD1000 high definition video cam.

---

### Post by lisati on 2008-08-16
This is why I keep Windows on my desktop. As much as I like Ubuntu, none of the Linux-friendly video editing tools I've checked out has the combination of features that I'm used to and grown to like.

---

### Post by Somenoob on 2008-08-16
> **Cresho said:**
> avidemux.  go to [http://www.getdeb.net/search.php?keywords=avidemux](http://www.getdeb.net/search.php?keywords=avidemux)

download the avidemux and avidemux common.  Do not use qt as this is for kde.

here are my notes to force enable all codecs.  The defaults only give you a few measily ones.

if you want to enable full codec support, in terminal "avidemux" or change the application executable to avidemux. you can verify this by Help->built in support.

what this application does is splice stuff or puts stuff together.

here is my tutorial

[http://forums.steves-digicams.com/forums/view_topic.php?id=594710&forum_id=27](http://forums.steves-digicams.com/forums/view_topic.php?id=594710&forum_id=27)

I use a sanyo HD1000 high definition video cam.

It doesn't run under 64-bit architecture, what's with this lack of support for 64-bit? x86-64 is pretty much the norm now.

---

### Post by Bungo Pony on 2008-08-16
> **Somenoob said:**
> As much as I love OS software, every single linux-based video editor I've used so far has been a piece of crap.

Unfortunately, I have to agree with you. Nero Vision is probably the only reason I have a Windows partition.

Ever try recording from your TV Tuner card in Linux? It's a pain. It would be nice if it worked well with my TV Tuner card period. I can get video, but no audio. I have to run the audio to the audio in on my soundcard, which means unplugging the existing input, and plugging in the audio. It wouldn't be necessary if Linux liked my multi-input onboard audio. Nero in Windows uses it all without a hitch.

The only thing I found that kinda worked with recording from the TV Tuner card is XawTV, which is no longer being developed. That's a damn shame, since it's probably the easiest piece of software to use, and the word 'easy' probably shouldn't be associated with XawTV.

---

### Post by FuturePilot on 2008-08-16
Unfortunately this seems to be an area that Linux is lacking in. The best simple video editor I've found is kdenlive, albeit a bit crashy. What Linux needs is a good **simple** video editor.

---

### Post by TBOL3 on 2008-08-16
I say blender is simple, or the video editer is anyway :).  The only problem is that there are a bunch of other features that will get in your way, if you've never used blender before.

---

### Post by frup on 2008-08-16
Anyone willing to pool together $20 each for a development bounty of video editors?

We could select a few required features, the top 2 or 3 editors (so that the bounty is also worth it for them as they will be closer to completion no doubt)

I hereby announce that I will pledge $20 to the advancement of F/OSS video editing if 50 at least people join me. If you want to join select some features and an app you want improved.

I don't use video editing software but I have tried kino and avidemux, I can't get my panasonic GS27 to behave properly.

---

### Post by beameup on 2008-08-16
Probably one of the better attempts at Linux Video Editing WAS Mainconcept's MainActor. Unfortunately they gave up on it. Some related articles here.

[http://en.wikipedia.org/wiki/MainActor]("http://en.wikipedia.org/wiki/MainActor")

and

[http://dvformat.digitalmedianet.com/articles/viewarticle.jsp?id=32719]("http://dvformat.digitalmedianet.com/articles/viewarticle.jsp?id=32719")

 and

[http://www.madpenguin.org/cms/?m=show&id=8000]("http://www.madpenguin.org/cms/?m=show&id=8000")

---

### Post by Warpnow on 2008-08-16
If you can find a copy of it somewhere *cough*torrent site*cough* mainactor is STILL the best video editor available for linux.

---

### Post by jman623 on 2008-08-16
have you tried any of these yet:

[Open Movie Editor]("http://www.youtube.com/watch?v=9ljEb1PdEdM")

[LiVES]("http://lives.sourceforge.net/")

[Kino]("http://www.kinodv.org/")

---

### Post by FuturePilot on 2008-08-16
> **jman623 said:**
> have you tried any of these yet:

[Open Movie Editor]("http://www.youtube.com/watch?v=9ljEb1PdEdM")

[LiVES]("http://lives.sourceforge.net/")

[Kino]("http://www.kinodv.org/")

Is Open Movie Editor still even an active project?

Lives is overkill and very complicated. The idea here is **simple**

As for Kino did you read the OP's post? 
> Don't recommend Kino, what's so special about it? it often fails at importing and editing is too hard and I don't feel like going trough a long learning curve I just want it to be self-explanatory.

---

### Post by Warpnow on 2008-08-17
Linux doesn't need simple.

Linux needs competent.

The current video editting software are not competent or reasonable for any kind of professional use. You would be losing money, efficiency, and time running them.

It needs to work without crashing. That's really all that matters, as no linux video editor can realistically achieve it for long periods of time.

It also needs to follow the standard idea of a video editor. It needs a timeline and a cutting tool bare minimum. No clip linking or ****. Just stick to what has worked.

---

### Post by fiddledd on 2008-08-17
I've not found any capable/stable video editor or video encoder for Linux, which is one of the reasons I still need Windows. I don't think the situation is going to change any time soon, I'm not sure why though.

---

### Post by Cresho on 2008-08-17
From what I read here, some of you guys need some more expirience.   There are many things you can do in linux.  Just to give some examples, analog tv recording, HDTV recording, HD cam recording.  All can be edited and burned to dvd or stored in a format you like.

---

### Post by lisati on 2008-08-17
> **TBOL3 said:**
> I say blender is simple, or the video editer is anyway :).  The only problem is that there are a bunch of other features that will get in your way, if you've never used blender before.
I once took a look at the Windows version of Blender, it seemed unnecessarily complicated for what I wanted to, and the user interface wasn't exactly intuitive for the new user.

> **Warpnow said:**
> Linux doesn't need simple.

Linux needs competent.

The current video editting software are not competent or reasonable for any kind of professional use. You would be losing money, efficiency, and time running them.

It needs to work without crashing. That's really all that matters, as no linux video editor can realistically achieve it for long periods of time.

It also needs to follow the standard idea of a video editor. It needs a timeline and a cutting tool bare minimum. No clip linking or ****. Just stick to what has worked.
I agree: This is just my opinion, but Windows Movie Maker, which is pretty basic, suits my needs better than some of the Linux offerings I've looked at. For some of the stuff I do, it might only be as a "hobbyist" but I want to do at least a reasonable job of tidying up the footage I shoot for other people. 

Even transferring old VHS tapes to DVD properly can require more effort than just cut-and-paste or pressing the "copy" button on the VCR/DVD-recorder I have and letting it do its stuff. There's the proper menus to do, sometimes colour correction, noise reduction in the sound track, putting the chapter markers in sensible places.....

---

### Post by quinnten83 on 2008-08-17
And yet nobody has even reacted to the post about the $20 pledge, but all seem to complain about the lack of good editing software.

I used kino, and except for the importing and some sound problems, I found it to be very easy and straight forward. I do agree it is not as dependable, but saying that it is not easy, I can't agree with that.

Btw, yes I would be willing to pledge $20 for good simple editing software.
What do you propose?

---

### Post by sstusick on 2008-08-17
I am surprised there is not a Windows Movie Maker clone. WMM is perfect for simple video editing tasks, and it's the only Microsoft software that I find useful. All of the Linux alternatives pale in comparison.

---

### Post by roaldz on 2008-08-17
Why don´t any of you guys mention Cinelerra? It´s very good!

for Hardy:
```
sudo wget http://akirad.cinelerra.org/dists/hardy.list -O /etc/apt/sources.list.d/akirad.list
wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
```


And be shure to try Blender!

---

### Post by quinnten83 on 2008-08-17
> **roaldz said:**
> Why don´t any of you guys mention Cinelerra? It´s very good!

for Hardy:
```
sudo wget http://akirad.cinelerra.org/dists/hardy.list -O /etc/apt/sources.list.d/akirad.list
wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
```


And be shure to try Blender!

Because it had to be simple to use. 
I have tried cinelerra several times and I just can't get the hang of it. I know it is the most powerful video editor in linux, but the interface is complex and you sorta have to understand the terminology.

---

### Post by beameup on 2008-08-17
> **Warpnow said:**
> If you can find a copy of it somewhere *cough*torrent site*cough* mainactor is STILL the best video editor available for linux.


Wow, I actually see it on a *cough*torrent site*cough* :). cough*torrentpond.com*cough*
Will it still work on the latest Ubuntu?

:guitar:

---

### Post by Perfect Storm on 2008-08-17
*cough*Infraction*cough*

---

### Post by Canis familiaris on 2008-08-17
> **Artificial Intelligence said:**
> *cough*Infraction*cough*

Wow! I didn't know about a Linux Video Editor called 'Infraction'. But I did not find it in the repos. Could you provide Links?

EDIT: Oh! A forum infraction. My mistake. LOL

---

### Post by mips on 2008-08-17
> **Artificial Intelligence said:**
> *cough*Infraction*cough*

*cough*Somehow I saw that coming*cough* :)

---

### Post by Perfect Storm on 2008-08-17
> **Anurag_panda said:**
> Wow! I didn't know about a Linux Video Editor called 'Infraction'. But I did not find it in the repos. Could you provide Links?

EDIT: Oh! A forum infraction. My mistake. LOL

Hehehe :KS

---

### Post by ssam on 2008-08-17
> **frup said:**
> Anyone willing to pool together $20 each for a development bounty of video editors?

We could select a few required features, the top 2 or 3 editors (so that the bounty is also worth it for them as they will be closer to completion no doubt)

I hereby announce that I will pledge $20 to the advancement of F/OSS video editing if 50 at least people join me. If you want to join select some features and an app you want improved.

I don't use video editing software but I have tried kino and avidemux, I can't get my panasonic GS27 to behave properly.

bounties are hard to make work.

what might work would be to gather enough money to actually hire a programmer. trouble is not many people would want to deal with all that money, and not many people would trust anyone with all that money.

It might work if you got a company to deal with the money. maybe canonical or fluendo. then everyone gives them the $20, and they hire someone to make the video editor.

---

### Post by daverich on 2008-08-17
there seems to be some action going on with Kdenlive,- personally I think it's got the best chance of become *the* linux video editor.

the svn version I have works pretty well already and they seem to be cracking on with the KDE4 version.

Kind regards

Dave Rich

---

### Post by Daveski on 2008-08-17
> **quinnten83 said:**
> I used kino, and except for the importing and some sound problems, I found it to be very easy and straight forward. I do agree it is not as dependable, but saying that it is not easy, I can't agree with that.

+1. Kino was easy to pick up for me, but as it only really deals with DV you have to be willing to use something like ffmpeg to do some conversions. I have just started to get the hang of Cinelerra and I think this is much better but it is much harder to pick up.

I tried Windows Movie Maker, but I thought it was a bit of a pile - sure if you are cutting together some Windows native videos I guess it would do the trick. I wanted to edit some clips converted to raw uncompressed (and non lossy compressed) video and I could not get playback smooth enough to preview - the same videos on the same machine running Ubuntu and Cinelerra were perfect and easy to manipulate.

The problem here I guess is getting the balance right - something not too difficult that it scares off the average user, but not too simple that it is far to limited.

---

### Post by roaldz on 2008-08-17
> **Daveski said:**
> +1. Kino was easy to pick up for me, but as it only really deals with DV you have to be willing to use something like ffmpeg to do some conversions. I have just started to get the hang of Cinelerra and I think this is much better but it is much harder to pick up.

I tried Windows Movie Maker, but I thought it was a bit of a pile - sure if you are cutting together some Windows native videos I guess it would do the trick. I wanted to edit some clips converted to raw uncompressed (and non lossy compressed) video and I could not get playback smooth enough to preview - the same videos on the same machine running Ubuntu and Cinelerra were perfect and easy to manipulate.

The problem here I guess is getting the balance right - something not too difficult that it scares off the average user, but not too simple that it is far to limited.

The bad part of Cinelerra is the crashes.. You CAN´T fix them... Such a pity.. But Cinelerra´s new version is coming:
[http://lumiera.org/](http://lumiera.org/)

Looks promising:)

---

### Post by oldos2er on 2008-08-17
> **Somenoob said:**
> It doesn't run under 64-bit architecture, what's with this lack of support for 64-bit? x86-64 is pretty much the norm now.

 Yes, it does, you just need to set the 64-bit version at the top of the page. I use "cat" to capture video, and avidemux to edit it.

---

### Post by Bungo Pony on 2008-08-17
I *sorta* got Windows Movie Maker to work in Wine. Unfortunately, it's somewhat unuseable.

---

### Post by Cresho on 2008-08-17
ya, avidemux is a really good cuter, joiner, converter.  if you launch the application from terminal "avidemux", you get teh full bang with avidemux. they even have a tutorial on there forums about fade in and out and also picture slide show.

---

### Post by miggols99 on 2008-08-17
> **MaxIBoy said:**
> Kdenlive is terrific, as far as I can tell, but I haven't gotten it to run more than a minute without crashing. I don't think it likes my computer.
Nope, I get that too. I hope the new KDE 4 version is better...

---

### Post by FJGamer on 2008-08-17
I'm sort of limited to non-KDE programs in Ubuntu, but I have to say that the video tools I've tried can't edit Windows Media formats, not even wma. I tried Open Movie Editor, which looked almost perfect, but it kept failing to load audio on everything, and I never got video preview to work. I did get a couple clips spliced together without audio, but it came out as a 200mb file and had no compression options. Also, PiTiVi looks pretty good, much better than Open Movie Editor, but I have not messed with it enough to have an opinion yet. At the least, audio plays, and it seems to work like Windows Movie Maker.

I keep WinXP as my secondary OS just for the video and editing programs. If Linux could support WM formats and video embeds (without Flash players, unlike YouTube, which works like a charm in Firefox) and give us a really awesome video studio, Windows would probably be forgotten. Well, I'd still play my Steam games in Windows, but hey, Wine will support more of DirectX eventually.

---

### Post by hessiess on 2008-08-17
+1 for Blender, it may not be simple, but it is powerfal. Blender has a nodal compositor that can be used for all cinds of effects/ tweeks, the only limit beeing your imangination ;). Blenders interface is _VERRY_ fast once you get to know it.

programs like Imovie/windows movie maker are far too simple, (IMHO) you cannot do anything good with them. although its not the software that makes art, its the artist using it.

---

### Post by sstusick on 2008-08-17
> **Bungo Pony said:**
> I *sorta* got Windows Movie Maker to work in Wine. Unfortunately, it's somewhat unuseable.I was going to try WMM in wine, but figured it a waste of time.

---

### Post by doorknob60 on 2008-08-17
Yeah, they all suck except Kdenlive, which is too buggy (it screws up my vids last time I tried, mainly with the sync, but it has the most potential).

---

### Post by FJGamer on 2008-08-17
> **hessiess said:**
> +1 for Blender, it may not be simple, but it is powerfal. Blender has a nodal compositor that can be used for all cinds of effects/ tweeks, the only limit beeing your imangination ;). Blenders interface is _VERRY_ fast once you get to know it.
I never considered Blender as a video editor, but I guess it could be used that way. I never even animated a model in Blender, but I love the program. It's actually a lot easier to use than any other 3D suite I ever tried. I've tried hundreds.

Off topic: *I've seen some interesting games being made in Blender using Python, and all these games are platform-independent, meaning all my friends, who refuse to use a Linux OS, can still play my games in Windows.*

---

### Post by magnus0 on 2008-08-17
> **FuturePilot said:**
> Unfortunately this seems to be an area that Linux is lacking in. The best simple video editor I've found is kdenlive, albeit a bit crashy. What Linux needs is a good **simple** video editor.

yes, like windows movie maker:D someone should do linux movie maker:)

---

### Post by TBOL3 on 2008-08-17
I love blender as well.  But I found one problem, it can't import film from a camcorder (which is what I'm trying to do right now), [smacking my head into the wall].  Oh well, I guess kino does work, but only really for importing...

---

### Post by nerd0795 on 2008-08-17
[http://lives.sourceforge.net/](http://lives.sourceforge.net/)
LiVES I heard about...  never tried it though.  Going to soon.

---

### Post by DeadSuperHero on 2008-08-17
I think there needs to really be two definitive video editors for Linux.

-One for simple editing. Kind of like Movie Maker or iMovie. It could have some simple effects, some nifty developer plugins, and would be usable for someone who doesn't really need to edit every single frame of a movie.

-The other would need to be a film powerhouse. I'm thinking something comparable to Sony Vegas 8. (My brother has it, absolutely fantastic once you get the hang of it.). It's great for the more experienced people who want to edit professional movies, and it's also nice for some people who just want to make short skits.

The ones that I really see promise in are KDEnlive and LiVES.

---

### Post by TBOL3 on 2008-08-17
KDE and GNOME anyone?  But ya, I agree, the problem is that all of them are too buggy at the moment.

---

### Post by Warpnow on 2008-08-17
Sony Vegas is not a film powerhouse. :-p

Try Adobe Premiere, Avid, or Final Cut Pro to see a film powerhouse.

---

### Post by init1 on 2008-08-17
> **Somenoob said:**
>  As much as I love OS software, every single linux-based video editor I've used so far has been a piece of crap.

Yep, I've come to that conclusion too. Avidemux is the best, but it's not all that great.

---

### Post by Daveski on 2008-08-18
> **FJGamer said:**
> I'm sort of limited to non-KDE programs in Ubuntu, but I have to say that the video tools I've tried can't edit Windows Media formats, not even wma.

Why are you limited to non-KDE? You can happily run KDE programs in Ubuntu (Gnome) but it will install any required KDE libraries without issue.

Most Windows formats will be encoded with Microsoft proprietary codecs - you can install codec packs for Ubuntu if the codecs are free (as in beer).

---

### Post by mips on 2008-08-18
> **Daveski said:**
> Why are you limited to non-KDE? You can happily run KDE programs in Ubuntu (Gnome) but it will install any required KDE libraries without issue.


I suspect it is mostly a personal issue. Some people flatly refuse to use anything kde, they would rather use a less capable Gnome application.

---

### Post by Perfect Storm on 2008-08-18
> **mips said:**
> I suspect it is mostly a personal issue. Some people flatly refuse to use anything kde, they would rather use a less capable Gnome application.

That would be me :popcorn:

---

### Post by sstusick on 2008-08-19
> **Mr. Psychopath said:**
> I think there needs to really be two definitive video editors for Linux.

-One for simple editing. Kind of like Movie Maker or iMovie. It could have some simple effects, some nifty developer plugins, and would be usable for someone who doesn't really need to edit every single frame of a movie.

-The other would need to be a film powerhouse. I'm thinking something comparable to Sony Vegas 8. (My brother has it, absolutely fantastic once you get the hang of it.). It's great for the more experienced people who want to edit professional movies, and it's also nice for some people who just want to make short skits.

The ones that I really see promise in are KDEnlive and LiVES.
I agree.

---

### Post by jespdj on 2008-08-19
> **Somenoob said:**
> It doesn't run under 64-bit architecture, what's with this lack of support for 64-bit? x86-64 is pretty much the norm now.
Avidemux does run on 64-bit and it is available in the Ubuntu repository, so you can just install it with Synaptic. No need to manually download and install a .deb file.

---

### Post by hessiess on 2008-08-19
> I love blender as well. But I found one problem, it can't import film from a camcorder (which is what I'm trying to do right now), [smacking my head into the wall]. Oh well, I guess kino does work, but only really for importing...

personaly I use dvgrab to capture frm a camcorder, deinterlace and convert to PNG sequance/WAV with ffmpeg, then edit that with blender. The min problem with blender as a video editor is it dousent handle interlaceing verry well.

---

### Post by Wolki on 2008-08-19
> **Warpnow said:**
> Linux doesn't need simple.

Linux needs competent.

The current video editting software are not competent or reasonable for any kind of professional use. You would be losing money, efficiency, and time running them.

Considering that many major movie studios use Linux in their pipeline, this seems like an odd statement.

See for example [http://www.linuxmovies.org/](http://www.linuxmovies.org/) and [http://www.linuxmovies.org/software.html](http://www.linuxmovies.org/software.html)

Of course, the software used there is not free (and usually very expensive). I'd definitely consider "major motion pictures" professional use though :)

---

### Post by Warpnow on 2008-08-19
> **Wolki said:**
> Considering that many major movie studios use Linux in their pipeline, this seems like an odd statement.

See for example [http://www.linuxmovies.org/](http://www.linuxmovies.org/) and [http://www.linuxmovies.org/software.html](http://www.linuxmovies.org/software.html)

Of course, the software used there is not free (and usually very expensive). I'd definitely consider "major motion pictures" professional use though :)


Professional studios use various Autodesk programs in professional movies,.

Autodesk designs 3d graphics and CGI machines, not video editors

In addition, these are NOT LINUX PROGRAMS in the sense that we know them.

They are proprietary, or at least most of them. They only run on Autodesk workstations.

---

### Post by 50words on 2008-08-19
This is my chief gripe about GNU/Linux, as well. While PiTiVi and Kdenlive are promising, neither work on either of my computers.

All I want is something that will allow me to splice videos, add slideshows, and add soundtracks and captions.

This is a deal-breaker for a lot of people these days.

---

### Post by Thievrey Corporation on 2008-08-24
Hello all,

just to share with you my experience: I have been going around Ubuntu  8.04 with the Live CD for few months now. Could go wireless finally, could have communication with my Mac, was impressed by the way Ubuntu looks, and the softwares you cant get...
I was very ready to take the big dive, but not possible for the moment: the only thing that makes me stay with Windows is Adobe Premiere. All Linux softwares I've tried for video editing are crashing too often ...

Really too bad ...

---

### Post by suri.mahendra on 2008-09-06
Have you tried liVES?  you can get it from [http://www.getdeb.net](http://www.getdeb.net)  You will need to register to download.  I just started playing around with this and it seems straight forward.

Getdeb supports Debian and Ubuntu and will install software with a couple mouse clicks.  Also be aware of the 32 bit/64 bit variants.  Make sure you download the appropriate bit variant, else you will get a nasty-gram from the package manager.

Cheers

---

### Post by zmjjmz on 2008-09-06
I've tried LiVES, and I couldn't figure it out.
Guys, instead of collecting bounty for a _new_ program, just donate to KDEnlive or wait for it to mature more. Open Movie Editor also looks promising, though I can't say that I've made any videos with it yet.

---

### Post by grigio on 2008-10-08
I'm a Gnome user, but Kdenlive is the ONLY usable and quite working Video Editor for Linux right now

---

### Post by daverich on 2008-10-08
> **grigio said:**
> I'm a Gnome user, but Kdenlive is the ONLY usable and quite working Video Editor for Linux right now

not true.

Open movie editor is pretty stable especially compared to Kdenlive...

Kind regards

Dave Rich

---

### Post by UbuWu on 2008-10-09
Pitivi just announced that a fulltime developer is being hired to speed up development, so hopefully it will improve a lot in the near future.

---

### Post by ssam on 2008-10-09
> **UbuWu said:**
> Pitivi just announced that a fulltime developer is being hired to speed up development, so hopefully it will improve a lot in the near future.

wow. where did you hear that?

====update
[http://blogs.gnome.org/uraeus/2008/10/09/supporting-pitivi/](http://blogs.gnome.org/uraeus/2008/10/09/supporting-pitivi/)
:-)

---

### Post by grigio on 2008-10-11
This is a very good news for gnome users

---

### Post by Ubuntiac on 2008-12-15
> **daverich said:**
> Open movie editor is pretty stable especially compared to Kdenlive

I'd suggest trying Kdenlive again since it was almost entirely rewritten to use KDE$ libs instead of KDE3 (it still works just fine on Gnome).

The previous Ubuntu versions were an SVN snapshot over a year old not meant for public use. 0.7 (and especially in a couple of weeks 0.7.1) are much more stable, faster and with a number of new features.

Best of all, it's clean and very easy to use.

There are instructions in the ubuntu community wiki on getting the latest version through the builder wizard, a GUI app that builds 0.7.1 from source for you.

---

### Post by LuisAugusto on 2009-01-17
> **Somenoob said:**
> lol, a CLI video editor? i'd rather cut the actual microfilm with scissors.

Hahahahaha

> **lisati said:**
> I once took a look at the Windows version of Blender, it seemed unnecessarily complicated for what I wanted to, and the user interface wasn't exactly intuitive for the new user.

Blender isn't a video editor, even though it's a hell lot better than most Linux video editors at the task XD (the SVE is quite good).

---

### Post by hessiess on 2009-01-17
> **LuisAugusto said:**
> Hahahahaha



Blender isn't a video editor, even if it's a hell lot better than most Linux video editors at the task XD (the SVE is quite good).

Blender isn't just a video editor, but it has one;) and a nodal compositor which can do prittymuch anything effects-wise if you put your mind to it;)

The interface is designed to be fast, not easy to learn and it achieves this with flying colours:), considering that GUI tends to = waste vast amounts of time navigating menus.

---

### Post by LuisAugusto on 2009-01-17
> **hessiess said:**
> Blender isn't just a video editor, but it has one;) and a nodal compositor which can do prittymuch anything effects-wise if you put your mind to it;)

I know, and I actually like Blender interface, specially what is coming for 2.5 :popcorn:

---

### Post by TBOL3 on 2009-01-17
Agreed, blender is amazing.  Sure, it's not the most simple thing in the world, but if you are going to be making more then the occasional family travel log (the one and only thing the new iMovie is good for), then take some time and learn blender.  It's really powerful.

---

### Post by UbuWu on 2009-01-18
Kdenlive 0.7.1 (available in Jaunty) is pretty impressive compared to prior versions although it still crashes from time to time.

---

### Post by LuisAugusto on 2009-01-23
It never ceases  to amaze me the lack of a decent video editor XD.

I've been trying to use KDenlive but I can't use it for more than 5 minutes without a crash, and 90% of the time it results in a completely lose of everything I did.

Cinelerra has a horrible UI, but it's powerful and doesn't crash that often :/

Seems like I will keep using Blender XD XD XD 

(It's amazing how a crappy application like Windows Movie Maker kicks most Linux video editor as****)

---

### Post by LuisAugusto on 2009-01-26
> **LuisAugusto said:**
> It never ceases  to amaze me the lack of a decent video editor XD.

I've been trying to use KDenlive but I can't use it for more than 5 minutes without a crash, and 90% of the time it results in a completely lose of everything I did.

Cinelerra has a horrible UI, but it's powerful and doesn't crash that often :/

Seems like I will keep using Blender XD XD XD 

(It's amazing how a crappy application like Windows Movie Maker kicks most Linux video editor as****)

Ok, seems like I will eat my words, after updating KDE KDenlive works well, it some time crash, but it's amazingly acceptable, and it has a good interface (which is a first for video editors on Linux).

---

### Post by cotcot on 2009-01-26
I do not fully understand all the 'linux sucks for video editing' like comments. Kdenlive does not crash on my computer. (Am i the only one ?)
However I prefer blender VSE (it is a part of the 3D graphics blender program).

---

### Post by LuisAugusto on 2009-01-26
> **cotcot said:**
> I do not fully understand all the 'linux sucks for video editing' like comments. Kdenlive does not crash on my computer. (Am i the only one ?)
However I prefer blender VSE (it is a part of the 3D graphics blender program).

Well, I just said I ate my words, KDenlive is good, and as I said, Blender VSE is too (but the interface is pretty confusing and completely unintuitive, but it's good once you get used too).

On the other hand, that's for amateur video editing, there isn't anything like Final Cut Pro for Linux.

---

### Post by zmjjmz on 2009-01-26
> **LuisAugusto said:**
> Well, I just said I ate my words, KDenlive is good, and as I said, Blender VSE is too (but the interface is pretty confusing and completely unintuitive, but it's good once you get used too).

On the other hand, that's for amateur video editing, there isn't anything like Final Cut Pro for Linux.

Actually there is :P
Blender, Maya, and Shake are some good examples.

I have yet to try KDEnlive again, maybe I'll look at it when I get Jaunty.

---

### Post by LuisAugusto on 2009-01-26
> **zmjjmz said:**
> Actually there is :P
Blender, Maya, and Shake are some good examples.

I have yet to try KDEnlive again, maybe I'll look at it when I get Jaunty.

Maya and Blender aren't professional video editors, even if they have video editing capabilities.

---

### Post by forrestcupp on 2009-01-26
> **LuisAugusto said:**
> 
Cinelerra has a horrible UI, but it's powerful and doesn't crash that often :/

I think Cinelerra has a great UI.  I wish they'd get it all into one window, though.  But the UI is set up to utilize all of the advanced features.

Where Cinelerra lacks is in file format support.  Other than that, it's one of the best NLE's I've seen.  I wish I could run it in Windows.

---

### Post by LuisAugusto on 2009-01-26
> **forrestcupp said:**
> I think Cinelerra has a great UI.  I wish they'd get it all into one window, though.  But the UI is set up to utilize all of the advanced features.

Where Cinelerra lacks is in file format support.  Other than that, it's one of the best NLE's I've seen.  I wish I could run it in Windows.

Well, I don't like it, but the application itself is powerful. I'm particularly interested on Lumiera (made by some of Cinelerra devs who left it on good terms, they're coding an advance video editor with a good UI), Saya-VE seems like a good idea too (and it use Qt)

---

### Post by geoken on 2009-01-26
> **forrestcupp said:**
> 

Where Cinelerra lacks is in file format support.  Other than that, it's one of the best NLE's I've seen.  I wish I could run it in Windows.

Why, what does it do that movie maker can't? The whole time I was using it I was cursing the fact that Movie Maker wouldn't run in a VM.

---

### Post by forrestcupp on 2009-01-26
> **geoken said:**
> Why, what does it do that movie maker can't? The whole time I was using it I was cursing the fact that Movie Maker wouldn't run in a VM.

Are you talking about Windows Movie Maker?  If so, the list of things Cinelerra can do that MM can't is too long to post here.  Cinelerra is like a professional editor.  You can pretty much do anything you can imagine with it.  

Movie Maker is extremely simple.  It's useful for splicing clips and throwing them together, but it's pretty lacking in features to do more advanced things.  But if all you want to do is simple editing of home videos, Cinelerra isn't necessarily the best choice.  It's more for complex projects.

---

### Post by forrestcupp on 2009-01-26
> **LuisAugusto said:**
> I'm particularly interested on Lumiera (made by some of Cinelerra devs who left it on good terms, they're coding an advance video editor with a good UI)

From what I've seen, I think it will be a very long time before Lumiera is usable.  I hope it lives up to the hype.

---

### Post by polytropos on 2009-01-26
Just tried using Kdenlive and, as predicted by many here, it crashed on me.  My needs are pretty specific, so maybe someone has a suggestion for something that meets them: I need to import a long .avi file and then chop it into segments.  Is there anything that works well for that?

---

### Post by Perfect Storm on 2009-01-27
> **polytropos said:**
> Just tried using Kdenlive and, as predicted by many here, it crashed on me.  My needs are pretty specific, so maybe someone has a suggestion for something that meets them: I need to import a long .avi file and then chop it into segments.  Is there anything that works well for that?

Did you get the latest SVN version of Kdenlive?

---

### Post by Daveski on 2009-01-29
> **polytropos said:**
> I need to import a long .avi file and then chop it into segments.  Is there anything that works well for that?

Avidemux?
Or ffmpeg if you don't mind living without a GUI.

---

### Post by gletob on 2009-01-29
If a mod could take care of this I double posted by acidents

---

### Post by gletob on 2009-01-29
I used PiTiVi a little while ago with some wmv and mpg files.

[http://www.pitivi.org/wiki/Overview](http://www.pitivi.org/wiki/Overview)

---

### Post by waloleles on 2009-02-08
[screenshot](http://www.pipapo.org/pipawiki/Lumiera/GuiBrainstorming?action=AttachFile&do=get&target=screenshot090124-resources.jpg)

this is lumiera, a screenshot taken on january, what's your oppinion?

---

### Post by chris200x9 on 2009-02-08
> **waloleles said:**
> 

this is lumiera, a screenshot taken on january, what's your oppinion?

Looks like imovie 06, I'm sure it's MUCH more powerful but I'm just saying that's what the layout reminds me of, which is actually a good thing I never had to read anything about imovie it was just so simple. It looks like lumiera will be very simple yet very powerful, I'm looking forward to trying it. By the way how well does it run now

---

### Post by waloleles on 2009-02-08
there is the link to to then Lumiera GUI Brainstorm:

[URL="http://www.pipapo.org/pipawiki/Lumiera/GuiBrainstorming"]
http://www.pipapo.org/pipawiki/Lumiera/GuiBrainstorming[/URL]

and here the link to install lumiera on ubuntu using git.

[http://www.pipapo.org/pipawiki/Lumiera/NewbiesTutorials]("http://www.pipapo.org/pipawiki/Lumiera/NewbiesTutorials")

now lumiera is too unstable. but im waitint to the firsts betas to try it on my fedora 10 with kde4.2 :D

---

### Post by dragos240 on 2009-02-08
> **MaxIBoy said:**
> Kdenlive is terrific, as far as I can tell, but I haven't gotten it to run more than a minute without crashing. I don't think it likes my computer.
Well, what is making it crash, i use it all the time, is your computer slow? Do you have very little space on your computer? I ran into a bunch of problems after i used my space up, the gnome panels kept disapearing, no application ran, and i had to partition it, the first symptoms of this are that more programs crash than usual, some programs won't even start, and some sound and connecting issues, if your using wubi, meaning you installed ubuntu from windows, then thats probibly what is causing it, when i used it, it bugged everything. Try looking into some partitioning stuff, and kdenlive is probibly the best video editor for linux, but if you want 3D then blender is your man, i hope this helps :p.

Sinserelly,
Dragos240

---

### Post by kiddo on 2009-02-09
I updated the wikipedia page on PiTiVi recently (but the screenshot is still *very* outdated, I can't upload a new one).

Development is speeding up on PiTiVi lately, due to the fact that 3 developers are now on Collabora's paychecks to work on it (Edward, Brandon, Alessandro), and that's not counting volunteers.

I am watching PiTiVi's git master branch. Thumbnails and waveform have been merged recently. Still no multiple tracks or stuff like that, but it can be used for primitive editing (ordering clips, splitting, trimming, rendering). I filed roughly 27% of PiTiVi's currenty bug reports myself. They need all the help they can get. Anyone with Python knowledge (or who wants to learn) could/should try getting involved and fix things.

They intend to get something usable this spring (I'm not holding my breath; I held it for years), but if they do achieve those goals, as a "reward", I will edit a movie entirely with PiTiVi as a feature benchmark and demonstration of its capabilities. My movie requirements are on a wiki page, it's called [2009: A Workspace Odyssey]("http://www.pitivi.org/wiki/2009:_A_Workspace_Odyssey").

If they achieve this goal, that's it, they won.

---

### Post by 50words on 2009-02-10
> **kiddo said:**
> Development is speeding up on PiTiVi lately...

This is great to hear. PiTiVi has always been a promising project, and I would love to see it become really usable.

---

### Post by waloleles on 2009-03-31
anyone knows anymore about lumiera?

---

### Post by Ms_Angel_D on 2009-03-31
> **Artificial Intelligence said:**
> Did you get the latest SVN version of Kdenlive?

How do you get the latest version?

---

### Post by Perfect Storm on 2009-03-31
> **MetalHellsAngel said:**
> How do you get the latest version?

[http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/builder-wizard](http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/builder-wizard)

---

### Post by Ms_Angel_D on 2009-03-31
> **Artificial Intelligence said:**
> [http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/builder-wizard](http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/builder-wizard)

Thank you :)

---

### Post by LuisAugusto on 2009-03-31
> **waloleles said:**
> anyone knows anymore about lumiera?

Here: 
[http://en.wikiants.org/Lumiera](http://en.wikiants.org/Lumiera)

The official website is way too outdated ;-)

---

### Post by kiddo on 2009-03-31
Update on PiTiVi: it now has multiple tracks and stuff like that, but still lacks proper mixing of those tracks (that will come eventually). It's getting closer and closer to being able to edit the movie I was talking about earlier.

PiTiVi's development lately is quite promising. I'll be giving [a presentation]("http://create.freedesktop.org/wiki/PiTiVi") at [Libre Graphics Meeting 2009]("http://www.libregraphicsmeeting.org/2009/") about PiTiVi, its history, current developments, and most likely a demonstration.

---

### Post by dragos240 on 2009-03-31
Kdenlive is as good as it gets. The reason it crashes is because it lacks Dr. Konqi, this is not included in the new versions of KDE, meaning that if you had an older KDE version, it should work better. Anyways, It should get better, my video editor named "KINK" for now, will try to focus on a free linux clone of Sony vegas. Although It's still in the planning and designing stage, a few more years or so and I'll be able to release a beta. Right now, nothing has been done, again, kdenlive is the best for linux natively.

---

### Post by kiddo on 2009-04-01
> **dragos240 said:**
> Anyways, It should get better, my video editor named "KINK" for now, will try to focus on a free linux clone of Sony vegas. Although It's still in the planning and designing stage, a few more years or so and I'll be able to release a beta.
Oh no, not *yet* another video editor project? Why not just contribute to either PiTiVi or KDEnlive? Both are currently the only ones standing a chance. Speaking as an ex Vegas user myself (personally, I'm trying to shape/advise PiTiVi's design so that it can have some of the best ideas of Vegas, wherever possible)

---

### Post by FuturePilot on 2009-04-01
> **kiddo said:**
> Update on PiTiVi: it now has multiple tracks and stuff like that, but still lacks proper mixing of those tracks (that will come eventually). It's getting closer and closer to being able to edit the movie I was talking about earlier.

PiTiVi's development lately is quite promising. I'll be giving [a presentation]("http://create.freedesktop.org/wiki/PiTiVi") at [Libre Graphics Meeting 2009]("http://www.libregraphicsmeeting.org/2009/") about PiTiVi, its history, current developments, and most likely a demonstration.

I agree. PiTiVi is really starting to look like a decent editor. Its development has recently come to life all of a sudden which I think has something to do with the project being sponsored by someone if I remember correctly. So I'm going to keep my eye on PiTiVi, it looks promising.

---

### Post by SomeGuyDude on 2009-04-02
So what's the word? There an equivalent of Movie Maker?

I'm no professional editor myself, I just need something that can splice and dice tracks easily, overlay audio, give me some fun transitions, etc. Avidemux is tragically lacking and some of the others like KDen and Cinelerra are a wee bit too complex for me.

---

### Post by Perfect Storm on 2009-04-02
Kdenlive is pretty easy. I'm no shark with such app and I manage to put this together; [http://www.youtube.com/watch?v=thAJJn8QTrg](http://www.youtube.com/watch?v=thAJJn8QTrg) (HD version recommended).

---

### Post by mister_k81 on 2009-04-02
> **FuturePilot said:**
> So I'm going to keep my eye on PiTiVi, it looks promising.

Same here, I'm keeping an eye on the progress of this one and Lumiera. 

So far, none of the current Linux video editors have really satisfied me... Some are either unstable, or lack features, or are too over complicated (like Cinelerra). Kdenlive is pretty good though - probably one of the better ones available for Linux. But even then, I find that it still has some quirks that kinda annoy me.

---

### Post by Twitch6000 on 2009-04-02
Well it took me awhile to find a video editor(editors in this case) to suit my needs.

When it all came down to it though kdenlive replaced Windows Movie Maker for me.

I admit though it does have some quirks/bugs. Not as much as it use to though lol..

The main problem I get with it know is a random lock up problem after importing files.

Then I also use cineralla for anything kden cannot do.

---

### Post by SomeGuyDude on 2009-04-02
Came pretty close to Kden but really didn't want to install a thousand KDE libraries. Ah well.

---

### Post by Twitch6000 on 2009-04-02
> **SomeGuyDude said:**
> Came pretty close to Kden but really didn't want to install a thousand KDE libraries. Ah well.

Kdenlive only installs the basic kde files just so you know :).

So if you have VLC installed it shouldn't install anything else :],but the needed kdenlive files.

---

### Post by LuisAugusto on 2009-04-02
> **SomeGuyDude said:**
> Came pretty close to Kden but really didn't want to install a thousand KDE libraries. Ah well.

This is non-sense. And it's created by the stupid idea that more libraries will make your system slower. You'll need more RAM and HD, a stupidly small difference. That's all. Only "pseudo" experts think it matters and should be avoided.

---

