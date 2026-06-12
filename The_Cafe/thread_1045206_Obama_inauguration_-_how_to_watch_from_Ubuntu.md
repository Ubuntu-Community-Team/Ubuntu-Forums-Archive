---
title: "Obama inauguration - how to watch from Ubuntu"
date: 2009-01-20
forum: The Cafe
---

### Post by directhex on 2009-01-20
Some of you may have heard by now that the live streaming for the Obama inauguration will be provided using Microsoft Silverlight technology. "Woe is us!" cried out the Ubuntu masses. "Death to Obama!" cried the anti-Novell fanatics. However, there is some good news to share.

In direct response to the needs of Linux users (and PowerPC Mac users), Microsoft engineers (teamed up with some of Novell's Mono engineers) spent all last night re-architecting the Obama inauguration video player using Silverlight 1.0. See: [http://on10.net/blogs/benwagg/The-Obama-Inauguration-coming-to-Linux-and-PowerPC-Macs-Plus-compression-details/](http://on10.net/blogs/benwagg/The-Obama-Inauguration-coming-to-Linux-and-PowerPC-Macs-Plus-compression-details/) and also [http://tirania.org/blog/archive/2009/Jan-20.html](http://tirania.org/blog/archive/2009/Jan-20.html)

Why does this matter? Well, because SL1.0 is fully supported by the newly released Moonlight 1.0 Free Software plugin, meaning Ubuntu users are equally capable of viewing the streaming media as anyone else, despite the lack of SL2.0 support in current Moonlight releases.

So, what do you need to do? Well, you need Moonlight 1.0. Due to delays in the Debian NEW queue, it isn't yet in any official repositories, so you can either install the official Firefox .xpi file yourself (which will prompt you to install a binary codec pack from Microsoft to view video files), or use my PPA to install the latest version of Moonlight directly as an Ubuntu package (which uses FFmpeg to avoid the need for MS binary codecs). The packages on the PPA are the same packages which will be available in Jaunty - Moonlight is my package - so assume the same quality standards have been applied to the package as with any official repository.

[size=4]**Official plugin location: [http://go-mono.com/moonlight/](http://go-mono.com/moonlight/)**[/size]

[size=4]**Packages for Intrepid: deb [http://ppa.launchpad.net/directhex/ubuntu](http://ppa.launchpad.net/directhex/ubuntu) intrepid main**[/size]
(package name in aptitude/synaptic is 'moonlight-plugin-mozilla')

[size=4]**Packages for Jaunty: deb [http://ppa.launchpad.net/directhex/ubuntu](http://ppa.launchpad.net/directhex/ubuntu) jaunty main**[/size]
(package name in aptitude/synaptic is 'moonlight-plugin-mozilla')

[size=4]**Official streaming video location: [http://www.pic2009.org/page/content/linuxplayer](http://www.pic2009.org/page/content/linuxplayer)**[/size]

[size=4]**Test your Moonlight install: [http://silverlight.net/samples/1.0/Sprawl/default.html](http://silverlight.net/samples/1.0/Sprawl/default.html)**[/size]

[img]http://primates.ximian.com/~miguel/pictures/moon-obama.png[/img]

Digg this to let more people know: [http://digg.com/linux_unix/Obama_inauguration_how_to_watch_from_Ubuntu](http://digg.com/linux_unix/Obama_inauguration_how_to_watch_from_Ubuntu)

---

### Post by iKonaK on 2009-01-20
i found [this]("http://www.cnn.com/video/fb/facebook.html?stream=stream1") flash straming :)
one of many...

---

### Post by directhex on 2009-01-20
> **iKonaK said:**
> i found [this]("http://www.cnn.com/video/fb/facebook.html?stream=stream1") flash straming :)
one of many...

Streaming with adverts using a proprietary plugin

Kickass

---

### Post by iKonaK on 2009-01-20
> **directhex said:**
> Streaming with adverts using a proprietary plugin

Kickass
true, true, but easier.... many of us have the awful "proprietary" plugin you mentioned, already installed ....for watching meaningless videos on youtube.com

---

### Post by kevin11951 on 2009-01-20
[http://hulu.com](http://hulu.com) is going to have non stop coverage of it using flash.

---

### Post by gn2 on 2009-01-20
> **kevin11951 said:**
> [http://hulu.com](http://hulu.com) is going to have non stop coverage of it using flash.

No use if you're outside the US.

Best bet is just to wait till it's on YouTube.

---

### Post by mc4100 on 2009-01-20
> **gn2 said:**
> No use if you're outside the US.
Hulu's stream is working fine here in the UK ;)

---

### Post by directhex on 2009-01-20
Clicking the suggested URLs worked once. Subsequently, I see the "grey box" which anyone running an AMD64 system is all too familiar with (caused by the Flash plugin crashing, and NSPluginWrapper not restarting it).

I really fail to see why the crashy proprietary plugin is the solution it seems everyone wants to use

---

### Post by linux_nc on 2009-01-20
thanks for the link

---

### Post by iKonaK on 2009-01-20
> **gn2 said:**
> No use if you're outside the US.

Best bet is just to wait till it's on YouTube.
put "http://feeds.feedburner.com/Teckh" in liferea, the last feed has *embeded the stream and you can watch from outside too :)
EDIT: it's foxnews streamed, by the way :)

---

### Post by Sorivenul on 2009-01-20
> **directhex said:**
> I really fail to see why the crashy proprietary plugin is the solution it seems everyone wants to use
I don't see what difference it makes what plugin somebody uses, as long as it works for them. If Moonlight works for you, great; if Flash works for somebody else, great; if Gnash or swfdec work for somebody else; great.

I'm sure many appreciate the post, though. Cheers.

---

### Post by p_quarles on 2009-01-20
> **mc4100 said:**
> Hulu's stream is working fine here in the UK ;)
Apparently this stream is available outside the US (without a proxy), according to a few reports I've heard. 

directhex: I don't think anyone really likes Flash, but people are also skeptical about new and untested protocols that don't necessarily promise to be any better/different. To me, that's a legitimate hesitance that has nothing to do with other arguments about Novell/the End-of-the-World. :)

In any event, thanks to the MS and Mono folks who worked hard on getting this running at the last minute.

---

### Post by Mr. Picklesworth on 2009-01-20
If it wasn't Silverlight, this would be done with Flash... and I should not need to remind you guys that that would be a lot worse. (Where Moonlight, on the other hand, is a delightfully native piece of software that "just works", written by a group that actually knows what they are doing and is far less of a reverse-engineered hack than Gnash or Swfdec).

Of course, we all know that the art of "just embedding a video and letting the web browser handle the rest on its own" is long forgotten.

---

### Post by directhex on 2009-01-20
> **p_quarles said:**
> In any event, thanks to the MS and Mono folks who worked hard on getting this running at the last minute.

And just to clarify, it's working great here, on AMD64 Intrepid, with no proprietary anything - pure Moonlight w/ FFmpeg codecs

---

### Post by sdowney717 on 2009-01-20
Thanks, those debs work just fine. I simply added the line into my software sources and then using synaptic installed the packages. You will get a few warnings about a key and that they are not authorized.

---

### Post by eragon100 on 2009-01-20
Microsoft, THANK YOU!!

I can't believe it, microsoft engineers, working all nights to create a player version specially for linux!! :) :)

It indeed works without any problems on 64-bit intrepid, and the plugin installed with a single mouseclick. The official microsoft silverlight place now refers to the linux download!

KUDOS TO MICROSOFT.

ALL HAIL!! :) :popcorn: :KS

---

### Post by sdowney717 on 2009-01-20
[http://blog.atrexis.com/index.cfm/2008/8/6/Test-Silverlight-Streaming](http://blog.atrexis.com/index.cfm/2008/8/6/Test-Silverlight-Streaming)

This works, but other silverlight sites wont. Is this because they require silverlight 2.0?

---

### Post by eragon100 on 2009-01-20
> **sdowney717 said:**
> [http://blog.atrexis.com/index.cfm/2008/8/6/Test-Silverlight-Streaming](http://blog.atrexis.com/index.cfm/2008/8/6/Test-Silverlight-Streaming)

This works, but other silverlight sites wont. Is this because they require silverlight 2.0?

Yes, but microsoft and novell engineers are working on that too :wink:

So they should work soon, too.

MS writes some of the code for 2.0 support themselves, but more importantly, they provide and ALL SPECS AND TEST DEMOS to the mono developers free of charge.

Anyway, see my post above to see what I think of microsoft rewriting obama player for us: HALLELUJAH! All hail Ballmer! (Or whoever decided to do this).

---

### Post by Chame_Wizard on 2009-01-20
[http://wonkette.com/405541/live-inauguration-video-for-those-stuck-in-offices]("http://wonkette.com/405541/live-inauguration-video-for-those-stuck-in-offices")
:popcorn:

---

### Post by eragon100 on 2009-01-20
Watch it on the official page please. They are probably monitoring the amounts of linux vs windows users. If there are enough linux users that watch on the official stream, they will realise it's importtant to keep supporting linux in the future. Otherwise, this official support might just be a one time occasion.

So, please, watch it here: [http://www.pic2009.org/page/content/linuxplayer](http://www.pic2009.org/page/content/linuxplayer)      (after you installed MS silverlight/moonlight offcourse :wink: )

---

### Post by gn2 on 2009-01-20
> **mc4100 said:**
> Hulu's stream is working fine here in the UK ;)

They must have made an exception for this stream, because normally Hulu won't play outside the US.

I'm watching it on the BBC.

---

### Post by -jay- on 2009-01-20
thanks for the links am watching it now

---

### Post by gjoellee on 2009-01-20
This is a flash stream: [http://www.vgtv.no/?id=20750](http://www.vgtv.no/?id=20750)

(it is on right now!)

---

### Post by zolookas on 2009-01-20
> **gn2 said:**
> They must have made an exception for this stream, because normally Hulu won't play outside the US.

I'm watching it on the BBC.
Yes, it appears to be an exception.

---

### Post by Technoviking on 2009-01-20
The Silverlight/Moonlight site was lagging for me, had to switch to [http://cnn.com/live](http://cnn.com/live)

---

### Post by eragon100 on 2009-01-20
> **Technoviking said:**
> The Silverlight/Moonlight site was lagging for me, had to switch to [http://cnn.com/live](http://cnn.com/live)

Worked fine for me, rendering at 55 fps :KS

---

### Post by klange on 2009-01-20
Ended up watching the Oath on a 2" Sony TV in a car going 60 in a 25. Watched the speech on my 52" Sharp, though. So much for Moonlight...

---

### Post by jrusso2 on 2009-01-20
> **sdowney717 said:**
> [http://blog.atrexis.com/index.cfm/2008/8/6/Test-Silverlight-Streaming](http://blog.atrexis.com/index.cfm/2008/8/6/Test-Silverlight-Streaming)

This works, but other silverlight sites wont. Is this because they require silverlight 2.0?

Yes I can't get any of them to work. It downloaded some microsoft codecs and I restarted and none of those links seem to work.

Thanks Microsoft

Of course it the CNN page uses flash and works fine.

---

### Post by PartisanEntity on 2009-01-20
Strange, I could have sworn I posted here 2 mins ago :)

I watched it on [www.livestation.com](www.livestation.com) which is pretty good and runs nicely on mac, windows and linux.

---

### Post by Fabbritzio on 2009-01-20
Thanks for the links.. watched live on the internet.. over 1.000.000 people where there.

---

### Post by alternatealias on 2009-01-20
DirectHex: Thanks for the links/packages, I was about to do a fresh svn checkout before I saw this thread earlier.

The plugin worked beautifully.

---

### Post by Deamos on 2009-01-20
You can watch Via VLC using CNN's HTTP Stream.

Go to VLC
Choose Open Network
Paste the Following in to the location: [http://a466.l3760651364.c37606.g.lm.akamaistream.net/D/466/37606/v0001/reflector:51364](http://a466.l3760651364.c37606.g.lm.akamaistream.net/D/466/37606/v0001/reflector:51364)

Enjoy the coverage and happy Inauguration Day!

---

### Post by tubezninja on 2009-01-20
Funny, I spent the whole morning today getting our networks ready to support the[ Internet2 multicast stream of the inauguration]("https://mail.internet2.edu/wws/arc/i2-news/2009-01/msg00001.html") (which does support OS X, Windows and Linux).  Once that was done, I just went to the TV and turned on CNN. :)

Sometimes, the older tech is still the best way to see these things.

---

### Post by eragon100 on 2009-01-20
[QUOTE=scaredpoet;6586280](which does support OS X, Windows and Linux).  QUOTE]

How much longer is it gonna take before people realize that the silverlight version was linux compatible as Microsoft had a group of engineers working on it the entire night yesterday. They rewrote the whole player using silverlight 1.0, so there was both a Windows and a Linux version on the site, both by Microsoft. Why do people still say that other sites are compatible with linux too?

---

### Post by sefs on 2009-01-20
I cannot get this to work, and I've installed the 3 debs.

I am in firefox 3.1 beta 2 downloaded from the FF website and installed in /opt/firefox

How do I get this to work.

When I visit the page with the stream in the first post, all i get is a grapich to install siverlight

Thanks.

---

### Post by directhex on 2009-01-20
> **sefs said:**
> I cannot get this to work, and I've installed the 3 debs.

I am in firefox 3.1 beta 2 downloaded from the FF website and installed in /opt/firefox

How do I get this to work.

When I visit the page with the stream in the first post, all i get is a grapich to install siverlight

Thanks.

If you're not using a packaged browser, then I can't integrate into it now can I? That's one of the prices for ignoring apt.

ln -s /usr/lib/moon/plugin/libmoonloader.so /opt/firefox/plugins/

There's your fix.

---

### Post by sefs on 2009-01-20
> **directhex said:**
> If you're not using a packaged browser, then I can't integrate into it now can I? That's one of the prices for ignoring apt.

ln -s /usr/lib/moon/plugin/libmoonloader.so /opt/firefox/plugins/

There's your fix.

That was the first thing i did.  But when it didnt work I just tried installing the mozilla plugin deb which didnt work either.


P.S.  your ppa repo is giving me this

```

W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED8B789323DC003A

```

---

### Post by directhex on 2009-01-20
> **sefs said:**
> ```

W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED8B789323DC003A

```

Launchpad issue, nothing to do with me

---

