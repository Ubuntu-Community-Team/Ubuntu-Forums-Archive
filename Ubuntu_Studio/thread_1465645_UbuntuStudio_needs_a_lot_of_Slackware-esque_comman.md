---
title: "UbuntuStudio needs a lot of Slackware-esque command line tinkering for use."
date: 2010-04-29
forum: Ubuntu Studio
---

### Post by WrinkledCheese on 2010-04-29
Hey everyone,

I apologize in advance for the long post.

If I Google for 10.04 I can get the torrent or the ISO but there is no download section on ubuntustudio.org.  I was wondering if this is due to stability problems.

Previously I've been using Slackware 64 for my video production, if you want to call my tinkering production.  I had it to the point where it was awesome but I wanted to see if there was something more specific to multimedia production to make my life easier.  So I downloaded the x86 and the AMD 64 ISOs for 9.10 and installed the x86 version on my secondary system so that if it didn't come with Cinelerra and couldn't get Cinelerra installed I would keep using Slackware 64.

Here is a list of issues I have with UbuntuStudio:

[LIST]
[*]H264 not available by default, from my searches in the repository.  libx264 should be suitable for this since it's GPL.  Maybe it's because H264 isn't going to be royalty free beyond 2015.  I hope Google ends up releasing VP8 to the open source community so that it can be the new standard for HTML 5s, and the industry as a whole, video tag.  Only problem I see with this is the hardware acceleration already put into place by companies like nVidia.
[*]Kino sucks.  This is probably because I don't have libx264 installed, but I wanted to get a system that didn't require command line compiling of libraries for my video production.  H264 is quickly becoming the standard with pretty much EVERY video camera coming out writing to at least this spec and possible others.  My camera actually uses H264 encoding with the AVI or MOV containers unless it's in standard definition mode.
[*]ffmpeg require compile from command line to get it to work with libx264, once you get that installed.
[/LIST]
 
In summation, the only difference I find that Ububtu Studio has over Slackware is the use of Jack by default.  Jack is available in extras for Slackware so I don't see this as being an issue.  Slackware doesn't come with many encoders but has all the standard ones and has many decoders.  Essentially I can get a Slackware themed system to be pretty darn close to Ubuntu Studio for multimedia production if I install the base system and then install my extras after the installation is complete, which is pretty much what I have to do with UbuntuStudio.

I don't mean to slam Ubuntu or UbuntuStudio but I thought that a multimedia Linux distribution would bring together the best of both worlds.  Having a niche distribution of multimedia production while also having the benefit of choice, out of the box, that I have become accustomed to with Linux and it's plethora of open source projects.  Now I know that Ubuntu seems to be trying to get Cinelerra into it's repos while trying to keep it legal and licensed, but this seems to be ongoing for quite some time.


Maybe I should create a new thread.  On that note, maybe I should just stop complaining and go back to Slackware.  I would still appreciate it if someone addressed my concerns and questions.

Also, since I wasn't able to find the information I wanted in a few hours over the span of a few days, if someone could point me in a direction of information that gives me the multimedia benefits over standard/average Linux distributions that would also be much appreciated.

I haven't read much documentation aside from release notes and the rare wiki page and Google result, but I have spent about a month playing with UbuntuStudio.  Unfortunately, I was initially amazed with Ubuntu Studio so I reformatted my 64bit system after backing up all of my media and files.  Either way I have to build a system from scratch.

If it comes down to it I will be creating exact steps I follow to get both systems to the point where their multimedia capacity is pretty much the same and where I like it.  Also, I hope people with a lot more information on the subject can point out the differences.

I'm all for trying to get UbuntuStudio where I want it to be but if it's going to be more of a process/hassle than Slackware then why does it have the name Ubuntu at all?  <- Sarcastic Joke

P.S.  Sorry for the sarcasm...not ;) LMFAO

---

### Post by sgx on 2010-04-29
[/QUOTE]

snip

Here is a list of issues I have with UbuntuStudio:

[/QUOTE]

Hi, Ubuntu Studio, and its competitors, are for the convenience of many, not the panacaea of a few, but give the few a good starting place in many cases. Your best linux experience will come from a barebones
installation with only crucial apps, whether compiled, installed by commands, or processed through a package manager. Typically, the distribution that suits your basic needs best, will be replaced or
augmented by alternates from time to time, as competition drives
innovations that are worth the effort of switching, or having multiple computers. Your specific video needs should drive your selections, and the apps created by unpaid volunteer coders often reqire compiling, so that skill may be part of your future, and its not difficult given
the help forums and search-engines at our disposal. For luck, having both an rpm and debian linux, both set up to compile apps as needed, will insure
you access to the widest selection of the newest apps.

Or buy a Mac. ;)

---

### Post by WrinkledCheese on 2010-04-30
I've been using Slackware Linux for nearly 10 years, since version 8.1.  I am very familiar with installing via compilation and have even fixed a few issues with config files or source code.  I haven't publish my issues beyond a forum post with my findings and solutions.

My post is merely to address the fact that from what I can tell, UbuntuStudio is designed to be a multimedia system.  I haven't heard of Kino before installing UbuntuStudio.  Over the years, I have come to accept that Ubuntu seems to be an out of the box system.  I am very happy with the limited pre-installed packages that come with UbuntuStudio, mainly for ISO size and download time, as well as reducing clutter automatically.

However, my main concern above was that UbuntuStudio is designed as a multimedia production environment.

> 
Hi, Ubuntu Studio, and its competitors, are for the convenience of many, not the panacaea of a few
So why isn't the packaged ffmpeg available in the repository, and pre-installed, compiled with the industry standard H264 codec?  You don't think it's industry standard.  Look at all the consumer(masses) HD camcorders out there.  From what I've seen in my research - I want to buy one - is that very few have other codecs for HD aside from H264.  Those that do have other codecs, half of them have the option between H264 and some proprietary Microsoft, non-H264, format.  Typically you have 95%+ of the HD camcorders, that I've looked at, with H264 and AAC or MP3 encoding in usually an AVI or MOV container.  For the ones that don't their either offer those as well as the new Microsoft WMV container format which supports HD with an encoder using ASV which is the video encoder in the latest and greatest Microsoft formats.  They also have audio specs defined in their WMV(11?) format.  The only format I was able to find that supports HD is matroska and vorbis/theora.  Both of which were atempts at open sourcing the mainstream video formats but failed, IMO.  That's not to say that they aren't any good, they're just not as good.

Furthermore, the description and reviews of UbuntuStudio that I've found say Ubuntu isn't for the faint of heart computer users and is more aimed at professional multimedia productionists.  I'm no professional, but I do have A LOT of experience with Linux, Slackware more specifically, and I find that the hurdles that I run to in Slackware in regards to video production software are fewer and farer between than the ones I ran into with UbuntuStudio.  I have compiled a version of ffmpeg, but I cannot seem to be able to get it compiled with libx264 enabled, even though it detects it in configuration.  

That being said, Slackware is more of a server oriented distribution and UbuntuStudio is more of a multimedia production distribution with branding from what I think is the easiest Linux distribution to use.

So, aside from using jack(audio benefit only) out of the box, I see absolutely no benefit to UbuntuStudio over any other Linux distribution for multimedia production, consumer or professional.

And as I said before, and I suspect this is where your comment quoted above is aimed, Cinelerra not only has licensing issues, but people don't like it.  At first I didn't like it, but after I got used to the complexity I actually found it quite refreshing from the other ones I've tried:  Kino, AviDemux, and another one I can't recall.

The only problem I have with only theora/vorbis being available is that I had to use ffmpeg on my slackware system to get a viewable video.  Otherwise it would crash during encoding in Cinelerra.  With AVI and H264 and MP3, via libx264 and libmp3lame, I had no problem, once I found out where it was stashed in Microsoft AVI container.

As for buying a Mac?  I run old systems on donated hardware aging 4-8 years old, because I cannot afford new computers, nor most software licenses.

---

### Post by sgx on 2010-05-01
Hi, I have noticed quite a few video apps and codecs that can
line dance and boogie, but don't slowdance when the lights are down.

The devs are spread across the globe, not working as a team in a company with common goals, with their paychecks and jobs on the line. So we are sometimes left with gaps in the software base, that can be effected by patents, day-job nda signatures, licensing fees, local law interpretations, not to mention the skill level and available time/energy of those freely writing code, and assembling distributions and repositories for us to enjoy. 
It sounds like you would be able to get you desired video setup if you
have access to the sourcecode, here is a page with a post towards the bottom that might help:

[http://ubuntuforums.org/archive/index.php/t-1233201.html](http://ubuntuforums.org/archive/index.php/t-1233201.html)

here is a PPA repository that might help:

[https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia](https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia)

it has these apps

Package	Version	Uploaded by
 ffmpeg 	4:0.5.1-1ubuntu1+svn20100327-8~multimediappa3 	Brandon Snider (2010-04-14)
 
 ffmpeg 	4:0.5.1-1ubuntu1+svn20100327-8~lucid~multimediappa2 	Brandon Snider (2010-04-09)
 
 ffmpeg-extra 	4:0.5.1-1ubuntu1+svn20100327-8~multimediappa3 	Brandon Snider (2010-04-14)
 
 ffmpeg-extra 	4:0.5.1-1ubuntu1+svn20100327-8~lucid~multimediappa2 	Brandon Snider (2010-04-09)
 
 gstreamer0.10-ffmpeg 	0.10.10-2~lucid~multimediappa3 	Brandon Snider (2010-04-09)
 
 gstreamer0.10-ffmpeg 	0.10.10-1~multimediappa1 	Brandon Snider (2010-03-27)
 
 libtheora 	1.1.1+dfsg.1-4~nvidiavdpauppa1 	Brandon Snider (2010-02-13)
 
 libva 	0.31.0+latest3-1+sds12~multimediappa1 	Brandon Snider (2010-04-18)
 
 libva 	0.31.0+latest2-1+sds11~multimediappa1 	Brandon Snider (2010-03-24)
 
 libvorbis 	1.2.3-3~nvidiavdpauppa1 	Brandon Snider (2010-02-13)
 
 mplayer 	2:1.0~rc3+svn20100414-0ubuntu1~lucid~multimediappa1 	Brandon Snider (2010-04-18)
 
 mplayer 	2:1.0~rc3+svn20100224-0ubuntu1~multimediappa5 	Brandon Snider (2010-04-17)
 
 vdpau-video 	0.6.9-1~lucid~multimediappa1 	Brandon Snider (2010-04-18)
 
 vdpau-video 	0.6.6-1~multimediappa3 	Brandon Snider (2010-03-26) 
 vlc 	1.1.0-git20100407-1ubuntu1~lucid~multimediappa9 	Brandon Snider (2010-04-11)
 
 vlc 	1.1.0+git20100317-ubuntu1~multimediappa4 	Brandon Snider (2010-03-24)
 
 x264 	1:0.svn20100207-0.0ubuntu1~nvidiavdpauppa1 	Brandon Snider (2010-02-12)
 
 xine-lib-1.2 	1.2.0~hg-0~multimediappa1 	Brandon Snider (2010-03-04)
 
 xine-lib-1.2 	1.1.90hg+20100501+09733f3ff3a8-7ubuntu1 	Brandon Snider (2 hours ago)
 
 xine-ui 	0.99.6~multimediappa1 	Brandon Snider (2010-03-28)

-------------------------------------------------------------------------
.
You might look into other distros, some are made in places that are more conducive to packaging troublesome code. Mint and Mepis and Crunchbang
and AVlinux are possible.

Hope this helps :)

---

### Post by VertexPusher on 2010-05-01
> **WrinkledCheese said:**
> H264 not available by default, from my searches in the repository.
You didn't look hard enough.

[http://packages.ubuntu.com/lucid/libx264-85](http://packages.ubuntu.com/lucid/libx264-85)

> ffmpeg require compile from command line to get it to work with libx264, once you get that installed.
Nope.

[http://packages.ubuntu.com/lucid/libavcodec-extra-52](http://packages.ubuntu.com/lucid/libavcodec-extra-52)
[http://packages.ubuntu.com/lucid/libavdevice-extra-52](http://packages.ubuntu.com/lucid/libavdevice-extra-52)
[http://packages.ubuntu.com/lucid/libavfilter-extra-0](http://packages.ubuntu.com/lucid/libavfilter-extra-0)
[http://packages.ubuntu.com/lucid/libavformat-extra-52](http://packages.ubuntu.com/lucid/libavformat-extra-52)
[http://packages.ubuntu.com/lucid/libavutil-extra-49](http://packages.ubuntu.com/lucid/libavutil-extra-49)
[http://packages.ubuntu.com/lucid/libpostproc-extra-51](http://packages.ubuntu.com/lucid/libpostproc-extra-51)
[http://packages.ubuntu.com/lucid/libswscale-extra-0](http://packages.ubuntu.com/lucid/libswscale-extra-0)

Go to *System-->Administration-->Software Sources* and make sure that all four repository branches (including universe and multiverse) are enabled. Otherwise these packages may not show up in Synaptic.

---

