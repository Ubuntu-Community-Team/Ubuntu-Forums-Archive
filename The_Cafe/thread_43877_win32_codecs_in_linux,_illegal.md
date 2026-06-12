---
title: "win32 codecs in linux, illegal?"
date: 2005-06-23
forum: The Cafe
---

### Post by Kimm on 2005-06-23
I'm just woundering about this since there is such a fuzz about the free open source media players. I mean, isnt it the codecs that acctually play a file, so, in that case the program is not in violation of any law since it does not provide the codecs only know how to use them.

And if this is the case (its not illegal), why dont just all apps use win32 codecs if the software patent law makes it into Europe?

Anyway, I supose there are chances of playing your beloved media anyway, Winamp in wine... PowerDVD for Linux LinDVD, even the Windows Media codecs are released for Linux...

---

### Post by Lovechild on 2005-06-23
Patents (since we want the code), License (since they want money), License violation (since the GPL requires a royalty free patent grant).. take your pick

---

### Post by Kimm on 2005-06-23
I dont think I quite understand? is the GPL license the problem? or what exactly do you mean?

---

### Post by Lovechild on 2005-06-23
This is the part of the GPL we are interested in:

> 
7.  If, as a consequence of a court judgment or allegation of patent infringement or for any other reason (not limited to patent issues), conditions are imposed on you (whether by court order, agreement or otherwise) that contradict the conditions of this License, they do not excuse you from the conditions of this License. If you cannot distribute so as to satisfy simultaneously your obligations under this License and any other pertinent obligations, then as a consequence you may not distribute the Program at all. For example, **if a patent license would not permit royalty-free redistribution of the Program by all those who receive copies directly or indirectly through you, then the only way you could satisfy both it and this License would be to refrain entirely from distribution of the Program.**


So if there are patents, and we can't get a royalty-free redistribution grant, then we cannot distribute it under the GPL.

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=Kimm]I dont think I quite understand? is the GPL license the problem? or what exactly do you mean?[/QUOTE]

The license of the codecs are the problem. w32codecs are meant be used only on a legal Window's box....any other use is illegal I think...

---

### Post by skoal on 2005-06-23
illegal? probably...

...but that's 1/2 the fun, ain't it?

\\//_

---

### Post by Kimm on 2005-06-23
well the license problem can easily be dealt with, just release with a different license!

> 
w32codecs are meant be used only on a legal Window's box....any other use is illegal I think...


That sounds strange, but what if I have purchased the codecs shouldnt I be able to use them? does it realy mather what platform its running?

Btw, wount this affect wine aswell? I mean if codecs are only supose to run on win32 then what about win32 apps?

---

### Post by dmb on 2005-06-23
Is there some kind of opensource project working on open source codecs for all of the win32 codecs, like avi, mp3(i know that exists) and the rest of the proprietary crap?

---

### Post by Takis on 2005-06-23
[QUOTE=Kimm]That sounds strange, but what if I have purchased the codecs shouldnt I be able to use them? does it realy mather what platform its running?[/QUOTE]
I'm not a legal guru but they may try and say that doing so consititutes reverse-engineering (or using reverse-engineered versions of) their product.

---

### Post by Kimm on 2005-06-23
dmb, that is the biggest problem, the new codecs violates patent laws.

> 
I'm not a legal guru but they may try and say that doing so consititutes reverse-engineering (or using reverse-engineered versions of) their product.


if I'm using their acctually product, I mean, only using it to decode video/audio I'm not reverseengineering it (as in, not getting the code for it, or trying to reproduce it), I'm just... well I dont know how codecs work but I'm executing it I supose...

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=Kimm]well the license problem can easily be dealt with, just release with a different license![/QUOTE]

The thing about the GPL is that it doesn't allow you to release the programs within a different license.



> That sounds strange, but what if I have purchased the codecs shouldnt I be able to use them? does it realy mather what platform its running?

1. No. We are talking about Microsoft here, they are very anal about that stuff. I bet their EULA says you have to give them your first born if you do this.

2. Even if you could get this right in court...its not what people are doing. In Ubuntu you are not installing YOUR w32codecs. You are installing some elses. The only way that this would work would be if YOU harvested them out of YOUR Windows install YOURSELF!

> 
Btw, wount this affect wine aswell? I mean if codecs are only supose to run on win32 then what about win32 apps?

That is why most major distros won't ship with Wine. To some it is a legal landmine.

---

### Post by Wolki on 2005-06-23
[QUOTE=dmb]Is there some kind of opensource project working on open source codecs for all of the win32 codecs, like avi, mp3(i know that exists) and the rest of the proprietary crap?[/QUOTE]

avi is not a codec, it's a container format that can contain all sorts of codecs (thats why on windows some avis might play and others not). Anyway, there's Open Source versions for lots, probably most of the proprietary codecs (not to sure about the Windows media formats :) but that doesn't really help when you can't distribute them.

---

### Post by sonny on 2005-06-23
[QUOTE=poofyhairguy]That is why most major distros won't ship with Wine. To some it is a legal landmine.[/QUOTE]
And I think M$ is waiting for the time when everyone starts shipping the distro's with wine, so he can take legal actions, cuz it's not the same to confront an IP adress than to do so with someone like mandriva, SuSe, Xandros or perhaps.. canonical??

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=sonny]And I think M$ is waiting for the time when everyone starts shipping the distro's with wine, so he can take legal actions, cuz it's not the same to confront an IP adress than to do so with someone like mandriva, SuSe, Xandros or perhaps.. canonical??[/QUOTE]

Me too...Ubuntu can't risk it...we will be in enough legal controversy when Mono is included with Breezy.

---

### Post by Burgundavia on 2005-06-23
Mono is not a huge issue. If it were, Novell would be in trouble when they shipped Mono in Suse 9.3

As for w32codecs, there are 2 issues here:
1.COPYRIGHT -  The actual files themselves are basically stolen, and violate copyright
2. PATENTS - Even a clean room implementation like ffmpeg breaks patents

THEY ARE NOT THE SAME THING, DO NOT CONFUSE THEM.

Sorry, for shouting, but a lot of people make that basic mistake.

Corey

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=Burgundavia]Mono is not a huge issue. If it were, Novell would be in trouble when they shipped Mono in Suse 9.3[/QUOTE]

I hope so. I like mono.

> As for w32codecs, there are 2 issues here:


Both are bad!

---

### Post by tkiesel on 2005-06-24
What would the legal status be of an app that doesn't decode the file, but transcodes it from a proprietary file format to an open one?  In that case, the media isn't being decoded to a viewable format (video/audio/etc.) but rather is being piped from one file directly to another.

I know that there are quality issues with transcoding from one lossy codec to another. (ick!), but if transcoding rather than decoding lets one sidestep legal problems with prop. codec use, that's good news.

much love,
-T

---

### Post by TravisNewman on 2005-06-24
it still has to decode in order to re-encode, so it still has those problems

---

### Post by nocturn on 2005-06-24
[QUOTE=Burgundavia]Mono is not a huge issue. If it were, Novell would be in trouble when they shipped Mono in Suse 9.3

As for w32codecs, there are 2 issues here:
1.COPYRIGHT -  The actual files themselves are basically stolen, and violate copyright
2. PATENTS - Even a clean room implementation like ffmpeg breaks patents

THEY ARE NOT THE SAME THING, DO NOT CONFUSE THEM.

Sorry, for shouting, but a lot of people make that basic mistake.

Corey[/QUOTE]

That is indeed an important difference, because in many parts of the world, only the first one matters.
In Europe, the patents are worthless for now although this might change.

---

### Post by TravisNewman on 2005-06-24
in some parts of the world, neither matters.
How I wish I lived there ;)

---

### Post by oracle2025 on 2005-06-24
If you are legally allowed to use these codecs under windows, you can do so under Linux. Can't think of a reason why not.

And yes, there is a project that tries to reproduce a free version of most availble codecs, it's called ffmpeg.

---

### Post by oracle2025 on 2005-06-24
BTW.

Software patents are not legal yet in Europe, so basically you could consider it a crime to patent software, and therefore everyone who patents his video codecs in Europe could be considered a criminal. ;)

And indeed, that's how I see it, the value of a Movie does not lie in the codec it's encoded, but in the story and production.

Therefore I consider it somehow a crime against the cultural heritage to restict the viewing of a piece of art, in the name of some minor piece of Technologie (a Video-Codec)

---

### Post by poofyhairguy on 2005-06-24
[QUOTE=oracle2025]If you are legally allowed to use these codecs under windows, you can do so under Linux. Can't think of a reason why not.
[/QUOTE]


Because its not YOUR codecs. Its the codecs of whoever ripped them out of his or her XP install and packaged them. YOUR legal codecs are still on yours window's partition (I could be wrong....you could have harvested them yourself).

---

### Post by weekend warrior on 2005-06-24
> Originally Posted by sonny
And I think M$ is waiting for the time when everyone starts shipping the distro's with wine, so he can take legal actions
 
It's *highly* unlikely Gates is going to open a new front in Europe against (for ex.) Kanotix for shpping with Wine, when Redmond already has a gaping open wound from European Court of Justice anti-trust/monopoly proceedings that are far from being resolved and receiving bad press for it. If they attempt to tie Office or other applications to their OS, they'll be slapped with yet another series of fines from ECJ.

For reference,  see [this article](http://news.zdnet.co.uk/software/linuxunix/0,39020390,39188944,00.htm)

---

### Post by Kimm on 2005-06-24
> 
(I could be wrong....you could have harvested them yourself).


Thats what I mean, If you harvest them from your windows and for yourself that should be legal. So I'd just be using a piece of software that happens to be able to use win32 codecs (such as mplayer/xine/<whatever>), shouldnt be any different then to be using them in windows.

Ofcourse ripped codecs are illegal, so are they in the windows environment!

But I supose we can still view are video, perhaps not for a little while, but I think a gazillion raging linux users will change their minds of the codec developers to port them to linux and perhaps write players for it. And there is still hope that we might defeat software patents in europe and it can stay the way it is. Perhaps microsoft is digging its own grave by doing what they are doing now.

---

### Post by Lovechild on 2005-06-24
[QUOTE=Burgundavia]Mono is not a huge issue. If it were, Novell would be in trouble when they shipped Mono in Suse 9.3
[/QUOTE]

My Microsoft .NET development insider tells me that basically the current view on Mono is that they will be unable to keep up with the Microsoft implementation in the long run, and they will never brand it an official .NET implementation so they doubt businesses will use it. 

But we have seen Microsoft issues some disturbing messages in the past few days regarding mono, so as sad as I think it is since I like Mono, I'm beginning to think that we need to tread carefully.

---

### Post by Kimm on 2005-06-24
Well, as long as we still have Java it should be quite allright I supose...

What if the acctuall developer wants to release his/her program under a different license, wount that work?

---

### Post by jsimmons on 2005-06-24
[QUOTE=Lovechild]My Microsoft .NET development insider tells me that basically the current view on Mono is that they will be unable to keep up with the Microsoft implementation in the long run, and they will never brand it an official .NET implementation so they doubt businesses will use it. 

But we have seen Microsoft issues some disturbing messages in the past few days regarding mono, so as sad as I think it is since I like Mono, I'm beginning to think that we need to tread carefully.[/QUOTE]

I'm a Windows developer (and have been since Windows 3.0), and I said this back when .NET was .NEW.   Mono will never be able to keep up (Microsoft release new .NET .CRAP every .YEAR), and even if they could keep up, Microsoft would step on their necks if Mono was suddenly  percieved to be a threat to Micropsoft's on-going monopoly.  .NET hasn't improved .ANYTHING from my standpoint, and Mono, IMHO is a waste of otherwise good development time.

---

### Post by TravisNewman on 2005-06-24
.righton

---

### Post by poofyhairguy on 2005-06-24
[QUOTE=jsimmons]  .NET hasn't improved .ANYTHING from my standpoint, and Mono, IMHO is a waste of otherwise good development time.[/QUOTE]

Screw .NET apps and Novell desperately wanted to convert people from .NET. The best part of Mono is that programmers that have experiance in that area can add to Linux as well. Only the companies that want MS's business care about keeing up with .NET.

 I care about Beagle, Muine, Tomboy, etc.

Programs that use mono.

---

### Post by az on 2005-06-24
Am I correct in saying that you can write something in mono and it will run on a .net platform, but you cannot necessarily run a .net program developed in windows in mono on linux?

If that is correct, then the Microsoft company should have no problem with that situation and be able to keep that up for years.

---

### Post by Lovechild on 2005-06-24
[QUOTE=azz]Am I correct in saying that you can write something in mono and it will run on a .net platform, but you cannot necessarily run a .net program developed in windows in mono on linux?

If that is correct, then the Microsoft company should have no problem with that situation and be able to keep that up for years.[/QUOTE]

Well with few modifications a .NET app could run on Windows or Linux - stuff like paths do change a great deal - but it's fairly easy to write portable C# code.

---

### Post by poofyhairguy on 2005-06-24
[QUOTE=azz]Am I correct in saying that you can write something in mono and it will run on a .net platform, but you cannot necessarily run a .net program developed in windows in mono on linux?
[/QUOTE]

Yep. Apparently .NET has some calls to specific things in Windows that C# by itself does not have. Currently some of the mono people (the ones working for novell) are trying to bridge this gap with wine...but we all know how well that works in a professsional setting.

---

### Post by Optimal Aurora on 2005-06-24
So does that with the illegalness also include things like libdvdcss... Just curious...

---

### Post by az on 2005-06-24
[QUOTE=Optimal Aurora]So does that with the illegalness also include things like libdvdcss... Just curious...[/QUOTE]

That's another portion of evility.

There is a patent on dvd encryption meaning that even though you bought the cd and own the content, to decode it without paying for a css decoding licence is patent infringement.  You can get sued for even wearing the C code in which it is written on a T-shirt.

Everybody will just end up using ogg and theora sooner or later anyway....  Who needs any other form of audio/video encoding?

Halo II shipped with ogg as the audio (and video?) codec on the Xbox...  The microsoft company didn't want to have to pay the mp3 encoding royalty so they just used the free implementation...

HAHAHAHA.

---

### Post by skoal on 2005-06-24
[QUOTE=azz]Halo II shipped with ogg as the audio (and video?) codec on the Xbox...  The microsoft company didn't want to have to pay the mp3 encoding royalty so they just used the free implementation...[/QUOTE]
Are you serious??  If not, I don't think Jerry Seinfeld could write better material than that.  I never heard about that and Halo2.  That's like a billionaire picking from the buffet at a homeless shelter's "soup kitchen".   Man, that's good stuff...

\\//_

---

### Post by Wolki on 2005-06-24
> Are you serious?? If not, I don't think Jerry Seinfeld could write better material than that. I never heard about that and Halo2. That's like a billionaire picking from the buffet at a homeless shelter's "soup kitchen". Man, that's good stuff...


[http://wiki.xiph.org/index.php/Games_that_use_Vorbis](http://wiki.xiph.org/index.php/Games_that_use_Vorbis)

Seems to be the other way round, PC and Mac Versions use Vorbis, Xbox not.

Xbox live however seems to use Ogg Speex:

[http://newsvac.newsforge.com/article.pl?sid=05/06/10/142235&tid=22](http://newsvac.newsforge.com/article.pl?sid=05/06/10/142235&tid=22)

---

### Post by az on 2005-06-24
Lugradio, season two, episode 17
[http://lugradio.org/episodes/29](http://lugradio.org/episodes/29)

Interview with Ralph Giles from [http://xiph.org/](http://xiph.org/), a head developer for the ogg codec.

Two million copies of Halo II for X box:

Title: Too orangey for crows
Date: 06 June 2005
Length: 76:35

Show summary: Jono Bacon, Matt Revell, and Ade Bradshaw talk about Linux and whatever else comes along, including:

    * Ralph Giles from the Xiph.Org Foundation talks about Ogg Theora, what Xiph are all about, and Xiph's free codecs being used in commercial environments, like Halo 2 on the XBox, and Speex in XBox Live
    * Jono went to the 6th GUADEC, and talks about how much beer he drank, what the conference was about, how much beer he drank, Gnome's direction, interesting Gnome people (lots of whom listen to LugRadio!), and how much beer he drank
    * Should we ditch Linux and start again from scratch?
    * Emails from all our lovely fans
    * A LugRadio Live update (only 3 weeks to go!) including how Mark Shuttleworth will now be attending and taking part in the Mass Debate

---

### Post by jdong on 2005-06-24
[QUOTE=poofyhairguy]Yep. Apparently .NET has some calls to specific things in Windows that C# by itself does not have. Currently some of the mono people (the ones working for novell) are trying to bridge this gap with wine...but we all know how well that works in a professsional setting.[/QUOTE]
Yep.

1: System.Windows.Forms (SWF), the made-famous-by-VB Windows Form GUI system, drag-and-drop. Mono uses GTK# as a replacement, but is trying to use Wine to emulate SWF support via winelib.

2: Win32.* : Microsoft-specific extensions to the .Net languages... Some are used to manipulate the registry. I don't know what mono has done with these...


Personally, I don't do much .NET programming... I've found my niche with Python.

---

### Post by Goddess_of_Linux on 2005-12-13
I was wondering if w32codecs where illegal here in the USA...

---

### Post by aysiu on 2005-12-13
[http://ubuntuforums.org/showthread.php?t=49536](http://ubuntuforums.org/showthread.php?t=49536)

---

### Post by Lovechild on 2005-12-13
yes they are illegal anywhere, you are violating copyright when using them..

---

### Post by nocturn on 2005-12-13
[QUOTE=Lovechild]yes they are illegal anywhere, you are violating copyright when using them..[/QUOTE]

AFAIK, they are not illegal here...  If they are offered for free download (like Media Player and quicktime), there is no additional restriction on using them in another OS.

EDIT, I'm from Europe, they are illegal in the US

---

### Post by agger on 2005-12-13
[QUOTE=nocturn]AFAIK, they are not illegal here...  If they are offered for free download (like Media Player and quicktime), there is no additional restriction on using them in another OS.

EDIT, I'm from Europe, they are illegal in the US[/QUOTE]

In Europe using them is legal if you obtained them legally.

If you own a Windows XP license, use dual boot and use the w32codecs on the dual boot machine, using the codecs in Ubuntu must be legal too (but IANAL). Distributing them unofficially cannot be, of course.

---

### Post by nocturn on 2005-12-13
[QUOTE=agger]In Europe using them is legal if you obtained them legally.

If you own a Windows XP license, use dual boot and use the w32codecs on the dual boot machine, using the codecs in Ubuntu must be legal too (but IANAL). Distributing them unofficially cannot be, of course.[/QUOTE]

Yes, and if you download Media player or quicktime, run it in wine and copy the DLL's over, it is OK too.

The download of the ZIP's from Mplayer etc are a different matter...

---

### Post by matthewv on 2005-12-13
Anybody know about australia.. legal or illegal there..??? Along with things like libdvdcss2? Just wondering where I stand...:)

---

### Post by BoyOfDestiny on 2005-12-13
[QUOTE=matthewv]Anybody know about australia.. legal or illegal there..??? Along with things like libdvdcss2? Just wondering where I stand...:)[/QUOTE]

As far as I know, Australia "imports" the DMCA... 

Fortunately, I don't use/own anything in wma/wmv...

---

### Post by LinuxSwede on 2005-12-13
[QUOTE=nocturn]Yes, and if you download Media player or quicktime, run it in wine and copy the DLL's over, it is OK too.

The download of the ZIP's from Mplayer etc are a different matter...[/QUOTE]

Actually, it's not illegal to download and use the zips as they are either as long as you don't redistribute them.

Just to be on the safe side i should probably add a "yet" to that though. ;)

---

### Post by Lovechild on 2005-12-13
[QUOTE=agger]In Europe using them is legal if you obtained them legally.

If you own a Windows XP license, use dual boot and use the w32codecs on the dual boot machine, using the codecs in Ubuntu must be legal too (but IANAL). Distributing them unofficially cannot be, of course.[/QUOTE]

It is my understanding that some of the codecs are tied to a certain player by license agreement, such that if you move the files to your Linux partition you are actually violating the license - thus making it illegal. The truth of this today, I am however unsure of - I haven't looked much into this area as I've just elected to avoid the windows formats. I feel that formats such as Ogg Theora currently present me with what I need in terms of video support.

---

### Post by Goddess_of_Linux on 2005-12-13
"That just prime..." -Optimus Primal

Great, so the majority of sites I visit I can't actually view any files (WMV WMA and MOV) without these and if I used them that would make me illegal, Great...

That's strike 1 against linux in general...

---

### Post by Lovechild on 2005-12-13
[QUOTE=Goddess_of_Linux]"That just prime..." -Optimus Primal

Great, so the majority of sites I visit I can't actually view any files (WMV WMA and MOV) without these and if I used them that would make me illegal, Great...

That's strike 1 against linux in general...[/QUOTE]

I would call that strike 1 against stupid laws.. you can't blame the Linux community for things lawyers enforce on us.

---

### Post by Goddess_of_Linux on 2005-12-13
[QUOTE=Lovechild]I would call that strike 1 against stupid laws.. you can't blame the Linux community for things lawyers enforce on us.[/QUOTE]
Instead of trying to make open source formats, or using windows dll files to run these codecs... So body, Hacker or programmer, should have made a linux version of these codecs and let the respective companies share them like they share their programs with Windows and OSX...

---

### Post by Knomefan on 2005-12-13
[QUOTE=Goddess_of_Linux]Instead of trying to make open source formats, or using windows dll files to run these codecs... So body, Hacker or programmer, should have made a linux version of these codecs and let the respective companies share them like they share their programs with Windows and OSX...[/QUOTE]

Ehm, they actually do. Look at ffmpeg for example. With it you can use most formats. The problem however, what ffmpeg are doing might also be legally problematic. 
So as Lovechild said, blame it on stupid laws.

---

### Post by Malphas on 2005-12-13
[QUOTE=Lovechild]yes they are illegal anywhere[/QUOTE]
That's quite a sweeping generalisation.  Are you sure you can back that up with facts?

[QUOTE=Knomefan]Ehm, they actually do. Look at ffmpeg for example. With it you can use most formats. The problem however, what ffmpeg are doing might also be legally problematic. 
So as Lovechild said, blame it on stupid laws.[/QUOTE]
Yes, exactly.  You can't blame this at all on the FOSS community.

---

### Post by Stormy Eyes on 2005-12-13
[QUOTE=Goddess_of_Linux]I was wondering if w32codecs where illegal here in the USA...[/QUOTE]

It probably is, but I don't let that stop me.

---

### Post by poofyhairguy on 2005-12-13
[QUOTE=Goddess_of_Linux]Instead of trying to make open source formats, or using windows dll files to run these codecs... So body, Hacker or programmer, should have made a linux version of these codecs and let the respective companies share them like they share their programs with Windows and OSX...[/QUOTE]

Actually there are open source version of many codecs. But that does not make them legal. Legallity comes from having the rights to use those patents (that the open source programs must use to play these files) and the only legal way to play these things is to get a license.

And its not a strike against Linux, because with Linspire you can get the codecs legally. Linux != Ubuntu.

---

### Post by benplaut on 2005-12-13
if you own a legal copy of windows, and *don't use it*, is it legal?

---

### Post by poofyhairguy on 2005-12-13
[QUOTE=benplaut]if you own a legal copy of windows, and *don't use it*, is it legal?[/QUOTE]

No, I think you must rip your own codecs. We have a guide for that on the forum.

And just for the record- NO USER HAS EVER GOTTEN IN TROUBLE FOR THIS! The creator of Mepis ships it with the codecs, lives in the U.S. and has never seen a jail cell. 

So if you are worried, then never speed or jaywalk again! As a friend of mine once said "its only against the law if you can get caught doing it."

---

### Post by The Warlock on 2005-12-13
[QUOTE=benplaut]if you own a legal copy of windows, and *don't use it*, is it legal?[/QUOTE]
Who knows? Copyright law is so seriously fucked up in the US that odds are, anyone with lots of money could sue you for just about any reason and, if not win, at least drain all your resources with a lengthy court battle or force you to settle out of court for lots of money. 

That said, unless you distribute w32codecs or libdvdcss, nobody cares if you donwload it.

---

### Post by endersshadow on 2005-12-13
Yeah, just install w32codecs.  Fight the system.

Microsoft (and others) offer these codecs up for free on their site via a download (WMP, Quicktime, RealPlayer, etc.).  It's not like their charging for the codecs in the first place.  It's like libdvdcss...I bought the DVD burner, but you're telling me I can't read DVDs legally?  Again, this has nothing to do with Linux and everything to do with copyright laws.  There is such a thing as "fair use" in the US legal system.  As long as you do not use these codecs for commercial purposes, you're within fair use, though don't quote me on that specific legal advice.  But according to my law professor, that is true.  If you're pumping out wmv's and selling them on the net using these codecs, I would suggest you use OGG...

---

### Post by The Warlock on 2005-12-13
[QUOTE=endersshadow]If you're pumping out wmv's and selling them on the net using these codecs, I would suggest you use OGG...[/QUOTE]

Hell, use OGG anyway. I remember someone earlier in the thread saying "Ogg Theora suits all my needs". Well, it would suit mine if, y'know, *anyone actually used it*. As it is, I need codecs for DivX, Xvid, WMV, and Quicktime to view my movies. Ogg Theora is virtually unknown outside of the Linux world. So please, use it if you're making movie files for whatever. Get it out there.

---

### Post by endersshadow on 2005-12-13
[QUOTE=The Warlock]Hell, use OGG anyway. I remember someone earlier in the thread saying "Ogg Theora suits all my needs". Well, it would suit mine if, y'know, *anyone actually used it*. As it is, I need codecs for DivX, Xvid, WMV, and Quicktime to view my movies. Ogg Theora is virtually unknown outside of the Linux world. So please, use it if you're making movie files for whatever. Get it out there.[/QUOTE]

Yeah, I'm in the same boat.  I don't make movies, but if I did, I'd go for OGG.  Hell, let's start up a porn site completely in OGG format...wasn't there a thread about that a while ago?  That was a great idea to generate popularity...heh...

---

### Post by Malphas on 2005-12-13
The problem is that Theora just isn't as good quality as most MPEG-4 Part 2/10 codecs yet.  Anyone that says otherwise is either blinded by zealotism or needs to visit an optician.  The general populace are willing to use open source alternatives when they're superior quality (and to some extent need to have third-party support), that's why XviD is used far more commonly than DivX.

---

### Post by GeneralZod on 2005-12-13
[QUOTE=Malphas]The problem is that Theora just isn't as good quality as most MPEG-4 Part 2/10 codecs yet.  Anyone that says otherwise is either blinded by zealotism or needs to visit an optician.  The general populace are willing to use open source alternatives when they're superior quality (and to some extent need to have third-party support), that's why XviD is used far more commonly than DivX.[/QUOTE]

This is true.  That's why I'm sitting here with every crossable part of my body (well...nearly every one :)) crossed hoping that one day [Dirac](http://dirac.sourceforge.net/faq.html) becomes viable and widely-used.  It has patents, but the BBC state that these are mainly defensive patents and that the codec is intended for use by Free software.

---

### Post by Lovechild on 2005-12-13
[QUOTE=Malphas]The problem is that Theora just isn't as good quality as most MPEG-4 Part 2/10 codecs yet.  Anyone that says otherwise is either blinded by zealotism or needs to visit an optician.  The general populace are willing to use open source alternatives when they're superior quality (and to some extent need to have third-party support), that's why XviD is used far more commonly than DivX.[/QUOTE]

I don't think it's that much worse visually to be honest, I mean there are clear differences but Ogg Theora remains fully functional for many tasks - I use it to backup my TV series (legally bought on DVD), for that it does rather well.

---

### Post by Lovechild on 2005-12-13
[QUOTE=GeneralZod]This is true.  That's why I'm sitting here with every crossable part of my body (well...nearly every one :)) crossed hoping that one day [Dirac](http://dirac.sourceforge.net/faq.html) becomes viable and widely-used.  It has patents, but the BBC state that these are mainly defensive patents and that the codec is intended for use by Free software.[/QUOTE]

Dirac is very interesting as is Snow and the wavelet xiph format I forget the name off.. 

Wavelets are very interesting, I've been studing them for a while now and I'm definately interested in seeing what talented mathmaticians can do with them to create superior video codecs.

---

### Post by GeneralZod on 2005-12-13
[QUOTE=Lovechild]Dirac is very interesting as is Snow and the wavelet xiph format I forget the name off.. 

Wavelets are very interesting, I've been studing them for a while now and I'm definately interested in seeing what talented mathmaticians can do with them to create superior video codecs.[/QUOTE]

I've not studied it, but it does sound promising - their faq states that they already have "much better compression performance" than Theora, which could be interpreted as "compressing faster" but hopefully means "compresses better".  There have been very few announcements made by the project, though (that I can see) so I'm hoping it doesn't just fade away and die like so many other promising projects :(

---

### Post by Malphas on 2005-12-13
In case you didn't know, Dirac will hopefully be included in the next Doom9 shootout, which should be interesting.

[http://forum.doom9.org/showthread.php?t=103120&page=1&pp=20&](http://forum.doom9.org/showthread.php?t=103120&page=1&pp=20&)

[http://sourceforge.net/forum/forum.php?thread_id=1391839&forum_id=353618](http://sourceforge.net/forum/forum.php?thread_id=1391839&forum_id=353618)

Not sure if Theora will be included or not yet, it's a possibility though.

---

### Post by hatefulthreatening on 2005-12-14
[QUOTE=endersshadow]Yeah, just install w32codecs.  Fight the system.

Microsoft (and others) offer these codecs up for free on their site via a download (WMP, Quicktime, RealPlayer, etc.).  It's not like their charging for the codecs in the first place.  It's like libdvdcss...I bought the DVD burner, but you're telling me I can't read DVDs legally?  Again, this has nothing to do with Linux and everything to do with copyright laws.  There is such a thing as "fair use" in the US legal system.  As long as you do not use these codecs for commercial purposes, you're within fair use, though don't quote me on that specific legal advice.  But according to my law professor, that is true.  If you're pumping out wmv's and selling them on the net using these codecs, I would suggest you use OGG...[/QUOTE]

I don't think that's an accurate description of fair use. Using the codecs is illegal in the US.

That situation is entirely different from the libdvdcss conflict. The courts failed us on that count. It was a very legitimate case of reverse engineering and a complete abuse of the DMCA. CSS had nothing to do with copy protection. I say fight that system by using libdvdcss for fair use copying and viewing.

But for the codecs, if you really want to protest, don't use those formats. Don't view the content created for it. Email content creators and tell them that they look very unprofessional and are limiting their exposure by using closed proprietary formats that aren't crossplatform. They are also leaving themselves vulnerable by depending on formats that could be obsoleted by forced "upgrades" at any time by the likes of Microsoft.

---

### Post by Malphas on 2006-01-03
Unfortunately Dirac and Theora weren't up to scratch to even make it through the qualification round of the Doom9 2005 codec test:

[quote=Doom9.org]As far as Theora goes, quality isn't up to the level and neither is rate control. I put this codec through the quality evaluation purely out of curiosity, it would've not been allowed in the main round because of the severe oversize anyway. Also, since the promised DVD backup optimized ffmpeg2theora build never showed up, I ended up using what's available per default and if you have any quarrel with that, direct your objections to the people in #theora on IRC.

Finally, Dirac didn't make it very far I'm afraid. At this point, the codec needs a lot of work to become a competitive solution for DVD backups / archival.[/quote]

[http://www.doom9.org/index.html?/codecs-quali-105-1.htm](http://www.doom9.org/index.html?/codecs-quali-105-1.htm)

---

### Post by GeneralZod on 2006-01-03
[QUOTE=Malphas]Unfortunately Dirac and Theora weren't up to scratch to even make it through the qualification round of the Doom9 2005 codec test:



[http://www.doom9.org/index.html?/codecs-quali-105-1.htm](http://www.doom9.org/index.html?/codecs-quali-105-1.htm)[/QUOTE]

Ouch.  That's disappointing :(

---

### Post by Zotova on 2006-01-03
[QUOTE=hatefulthreatening]But for the codecs, if you really want to protest, don't use those formats. Don't view the content created for it. Email content creators and tell them that they look very unprofessional and are limiting their exposure by using closed proprietary formats that aren't crossplatform. They are also leaving themselves vulnerable by depending on formats that could be obsoleted by forced "upgrades" at any time by the likes of Microsoft.[/QUOTE]

These formats aren't going to go away any time soon. In the mean time as a Linux user, if you want to go the legal way, you can't view 90% of websites which contain video because they use Windows based codecs - how is that a solution? Your just alienating yourself from the rest of the world by taking the stance of not using Windows codecs.

---

### Post by Malphas on 2006-01-03
MPEG-1, 2 and 4, and MP3 are not "Windows based codecs" and it's not illegal to view media using those codecs either; the problem is that any distribution that wants to include them by default would have to pay licensing fees.  Let's not blow the problem out of proportion.

---

### Post by Viper12 on 2006-01-03
This discussion is really a moot point.  All of these codecs are freely available over the internet for anyone to just download.  The ethics of do/do not here are simply laughable. 
 Don't:    Protest, and be unable to view just about anything other than a small % of the web, and feel good about being 'pure'.  

Do:     Be an evil law breaker!  Of course this is about the same as doing 60 mph in a 55mph speed limit area.  Even the police break this one...why?  because 
A.   Its unenforcable, and 
B.   It just plain violates common sense.

A lot of the laws 'invented in the US (my home) are created by people who for some reason or other, have lost all sense of reality.  Other laws are pushed through by those who are out trying to corner markets.  (read:  M$)

At the end of the day:
The end user MUST be the one who decides whether to speed....or not.  

Just as the movie industry tried to fight bittorrent and p2p only to make the problem grow larger, so to these stupid patent and copyright laws regarding software will either adapt or become irrelevent.  (In my opinion, they are ALREADY irrelevent).

An unenforceable law isn't worth the paper its printed on, and in the case of an end user and codecs........that's all the law is...unenforceable.

---

### Post by xequence on 2006-01-03
Honestly people, why does it matter at all? Yes, some things are illegal. Does it mean you will go to jail? No. Does it mean anyone cares if you do it? No. Does it mean its right to make it illegal? No.

Anyone have one of those little books of stupid laws? Like you cant drag a horse through the streets of Toronto on a tuesday. Whatever law forbids whatever were talking about doesent matter whatsoever.

---

### Post by mstlyevil on 2006-01-03
Just because something is illegal does not make it unethical. If every law was enforced in this country (USA) we would all be in prison and have records. Honestly, how are they going to know who installed and who did not install "illegal" codecs. This is like the law in some state that says it is illegal to eat a hamburger on Sunday. How about the law still on the books in california that says a Woman can only drive a car if there is a man running ahead carrying a red lamp and yelling "woman driver". Ubuntu on the other hand has to abide by the codecs law in order to remain a free distro and to keep from having to shell out huge legal fees to fight a lawsuit. This is not their fault and we should really lay off of them because they provide us wiht a great OS for free. "As in speech and beer."

---

### Post by super on 2006-01-03
i know they are illegal in the states. i'm pretty sure they are legal in Canuck-land (not that i care)

what about [vlc?]("http://www.videolan.org/vlc/features.html") does it use the w32codecs also or are they somehow different?

---

### Post by bionnaki on 2006-01-03
I'll install w32 codecs if I want - whether it is "illegal" or "legal" - I am not worried about it anymore than when I download music or when I used keygens on windows.

---

### Post by MaximB on 2006-08-20
why does Win32Codecs are illegal in LINUX
but perfectly legal in WINDOWS ???

---

### Post by KiwiNZ on 2006-08-20
You have actually answered this yourself.They are licenced for Windows.

---

### Post by MaximB on 2006-08-20
> **KiwiNZ said:**
> You have actually answered this yourself.They are licenced for Windows.


ok...so...
can we make "free legal" codecs that will work on linux too
and could run every movie/music format ?

---

### Post by FISHERMAN on 2006-08-20
> **MAXDDARK said:**
> ok...so...
can we make "free legal" codecs that will work on linux too
and could run every movie/**music format** ?

That would take a lot of reverse engineering and time, but in theory it is possible.(though in countries with software patents, like the US, they would still be illegal)

PS. I think I misread your question, I was talking about a possible free decoder for Windows media and not about free formats like Vorbis/Theora.

---

### Post by KiwiNZ on 2006-08-20
There already is for open formats eg Ogg. However for closed formats say DVD you need to pay licence.

---

### Post by MaximB on 2006-08-20
I wasn't talking about open formats like ogg
so - if I own DVD , is it legall to use thouse codecs in linux ?

---

### Post by Terracotta on 2006-08-20
> **MAXDDARK said:**
> I wasn't talking about open formats like ogg
so - if I own DVD , is it legall to use thouse codecs in linux ?
It depends on the country you live in. The mpeg decoding is open I think, but the CSS makes it in some countries illegal to play them without a licence.

---

### Post by KiwiNZ on 2006-08-20
In many countries yes it is illegal. It is illegal in the US where the owner of this Forum resides. Thus we do not permit posts that will infringe those laws and expose the owner of this Forum to litigation.

---

### Post by FISHERMAN on 2006-08-20
> **MAXDDARK said:**
> I wasn't talking about open formats like ogg
so - if I own DVD , is it legall to use thouse codecs in linux ?

TBH, I don't think there are many experts on 
Israeli copyright legislation on these forums.

All I know is that in my country(Belgium) Lame, Xvid, x264,... are legal because we don't have software patents. Libdvdcss is also legal (fair use). But the W32codecs aren't(copyright violation).
In the US all of them are illegal.

---

### Post by MaximB on 2006-08-20
well - in israel
it's all legal
no one will tell you anything about it
but as I turned to linux - I want to be legal

is there anything we can do to make thouse codecs legal in every country ?
**like licence them like MS did ?**
if we all collect the money - we could do it
like we have done with blender3d - we just bought it and made it free for all !

---

### Post by KiwiNZ on 2006-08-20
Talk to the rights owners. Arrange a very large bank overdraft. Hire a team of lawyers, and grow old while you do battle.

---

### Post by tribaal on 2006-08-20
Yeah... it's pretty much a lost cause for the current codecs. But we can still fight the upcoming formats, and try to make our voice heard - make them freely available / open source -

Or you can all move to Switzerland or Sweden :)

- trib'

---

### Post by kinematic on 2006-08-20
> **FISHERMAN said:**
> 
All I know is that in my country(Belgium) Lame, Xvid, x264,... are legal because we don't have software patents. Libdvdcss is also legal (fair use). But the W32codecs aren't(copyright violation).
In the US all of them are illegal.

same thing in the netherlands.
and windows codecs will be legal in a short while too.
realplayer has licensed the codecs as part of a settlement in a case against ms so in a while we can all enjoy wma's and wm'v(and what else they include)without doing something illegal.

---

### Post by RudolfMDLT on 2006-08-20
But in the future most codecs will have a free variant, won't they? The open source response to the mp3 issue was Ogg and to Divx was Xvid. And i don't really think that a company will come after you for wacthing a DVD with an illegal codec, they are after the distrubuters of illegal copied DVD's. 

Just for interest, check out VP3 or xiph: [http://www.vp3.com/vp3/about_vp3.shtml](http://www.vp3.com/vp3/about_vp3.shtml)
[http://www.xiph.org/](http://www.xiph.org/)

Cheers,

---

### Post by MaximB on 2006-08-20
so with thouse free legal open source formats , am I able to play "illegal" formats ?

---

### Post by seshomaru samma on 2006-08-20
> **KiwiNZ said:**
> You have actually answered this yourself.They are licenced for Windows.
I don't understand.What is licenced for Windows , the formats or the codecs?

---

### Post by Sam on 2006-08-20
Microsoft pays the makers of codecs to bundle them in Windows. When you purchase a Windows license, they gain some royalties.

---

### Post by daniel of sarnia on 2006-08-20
RealNetworks to support WMV on Linux

[http://arstechnica.com/news.ars/post/20060816-7524.html](http://arstechnica.com/news.ars/post/20060816-7524.html)

---

### Post by zenwhen on 2006-08-20
> **MAXDDARK said:**
> so with thouse free legal open source formats , am I able to play "illegal" formats ?

People have been trying to get a point across to you, but they have failed so far. I am not saying that as an insult, by the way.

What people have been trying to get across to you is that these support for these "illegal codecs" is not a technical hurdle we have yet to overcome. As you can see, once w32codecs, gstreamer0.10-plugins-ugly,  and libdvdcss are installed, a Linux user can view just about any type of media on their system.

The issue that keeps this functionality from being supported out of the box is that inclusion of this would cause Ubuntu to be illegal to distribute in many countries.

The way around this would be to pay for or obtain a license for each copy of Ubuntu that is downloaded or shipped. First of all, the companies who own the patents have to be willing to license us the technology, then someone has to pay them. Mark Shuttleworth has quite a bankroll, but Ubuntu can never be profitable on support alone if he plans to throw away money like that.

The solution we have now is working great for everyone who is willing to run a configuration script like Automatix or Easy Ubuntu after they install Ubuntu. I understand that this (or the effort of finding the solution) seems to be too much of a hassle for some, and I hope that one day a solution can be found that would allow us to have something like that offered to the end user right after they first boot to the Ubuntu desktop.

Software licenses are tough issue. Switching to free codecs is the best solution, but only if we can bring the mainstream with us.

You cannot play a DVD by default in Ubuntu. This is not the fault of the Ubuntu devs. This is the fault of governments around the world supporting software patents that stifle innovation and destroy consumer choice. Blame them, and blame the people who develop proprietary software.

---

### Post by seshomaru samma on 2006-08-20
zewhen's explanation was very clear
thank you
So who owns the DVD format?
Or MP3?

---

### Post by RudolfMDLT on 2006-08-20
The question of who owns the mp3 has a very complicated answer:

From : [http://www.mp3-converter.com/encoders/index.htm](http://www.mp3-converter.com/encoders/index.htm)
> So What is an MP3 Encoder?

An MP3 encoder is the software using an MP3 Codec (compression/decompression algorithm), to make MP3s.  Most encoders convert wav to mp3 although many can convert other formats such as WMA to MP3.

There are very few unique encoders.  Most software out there uses only about 4 main encoding engines due largely in part by the patents held by Fraunhofer-Gesellschaft and other companies that helped produce the ISO source that MP3 is based on.  Although no one company owns exclusive rights, MP3 software companies must pay a licensing fee to develop their own ISO source encoder which is expensive.  The major encoding engines are LAME (non-ISO source), BladeEnc, Fraunhofer Encoders, and Xing. 

and [http://www.iis.fraunhofer.de/amm/techinf/layer3/](http://www.iis.fraunhofer.de/amm/techinf/layer3/)

> Frequently Answered Questions on MP3

I'd like to license / to buy the Fraunhofer MP3 software.

End Users: Fraunhofer IIS is a research institute. Although MP3 was developed here, we do not sell any MP3 products to end users. MP3 encoders are available from various companies. They are integrated, for example, in Apple iTunes, Windows Media 10, and MusicMatch Jukebox.

Companies: Thomson ([http://www.mp3licensing.com/](http://www.mp3licensing.com/)) is our software and patent licensing partner for MP3. Please direct your enquiry to them. On the web site, you find the current MP3 royalty rates and the contact details of Thomson. 

Bluddy complex, I'll rather stick to the non-ISO versions!

As for the DVD, i'm not pasting everything here. Check out this link: [http://www.allformp3.com/dvd-faqs/61.htm](http://www.allformp3.com/dvd-faqs/61.htm)

Hope this explians it a little!

---

### Post by MaximB on 2006-08-20
zenwhen
I didn't get few things
1.if we develop a free, open source, legal codecs that can run mp3, avi's and other non-free formats
will it be legal then ?

2.if we licence the non-free codecs
do we have to pay per copy of ubuntu, or can we pay them once for all ubuntu's copies ?

I'm not interstead in it for myself
in israel any codec is perfectlly legal.
I'm asking for others.

---

### Post by RudolfMDLT on 2006-08-20
> **MAXDDARK said:**
> zenwhen
I didn't get few things
1.if we develop a free, open source, legal codecs that can run mp3, avi's and other non-free formats
will it be legal then ?


I don't think so... if you developed a free mp3 codec it would still be created using their ideas and stuff, intellectual property, of whom ever "created" mp3's and patented them first. For your codec to play their codec you need to conform to there codec and use algorithms and so on that they had developed, and thus you need to pay them. 

As for payment, they would want a dollar for every person that uses the codec, not just a once off payment. That would mean licensing Ubuntu in order to keep these people satisfied that whom ever uses Ubuntu is at least paying them for the ability to watch DVD's or listen to mp3's using codecs they developed.

EDIT:

So you see the problem, you can't have a free OS and then have people paying for the codecs shipped with it. It's easier to ship it without the codecs and then let the people download illegal codecs and break the law them selves rather than have your OS banned in certain countries

---

### Post by zenwhen on 2006-08-20
> **MAXDDARK said:**
> zenwhen
I didn't get few things
1.if we develop a free, open source, legal codecs that can run mp3, avi's and other non-free formats
will it be legal then ?

2.if we licence the non-free codecs
do we have to pay per copy of ubuntu, or can we pay them once for all ubuntu's copies ?

I'm not interstead in it for myself
in israel any codec is perfectlly legal.
I'm asking for others.

1) We would still be infringing on patents.

2) That is something that would be left up to the patent holders.

---

### Post by prizrak on 2006-08-20
> **FISHERMAN said:**
> That would take a lot of reverse engineering and time, but in theory it is possible.(though in countries with software patents, like the US, they would still be illegal)

PS. I think I misread your question, I was talking about a possible free decoder for Windows media and not about free formats like Vorbis/Theora.

Yes it has taken alot of reverse engineering. The result of it is Gstreamer, they have reverse engineered most of the popular codecs.

---

### Post by MaximB on 2006-08-20
it's a shame...
but if we convert the non-free format into a free format like ogg
then I see no problems ?

---

### Post by zenwhen on 2006-08-20
> **MAXDDARK said:**
> it's a shame...
but if we convert the non-free format into a free format like ogg
then I see no problems ?

We are fine then, but the software used to do it would also infringe. The solution is a social one. The solution is getting people not to put things into proprietary formats to begin with.

---

### Post by meho_r on 2007-08-24
> **zenwhen said:**
> We are fine then, but the software used to do it would also infringe. The solution is a social one. The solution is getting people not to put things into proprietary formats to begin with.

It is said that Linspire (and Freespire) is paying for codecs and other stuff. Does it mean that using them on that OS-es is legal? It seems that it is. Well, then you can spin LiveCD, convert your mp3s in ogg and no one could sue you, right? ;)

---

