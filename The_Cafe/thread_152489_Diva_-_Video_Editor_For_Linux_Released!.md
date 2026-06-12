---
title: "Diva - Video Editor For Linux Released!"
date: 2006-03-30
forum: The Cafe
---

### Post by lotusleaf on 2006-03-30
Finally, Diva is released. Let's hope it receives a lot of testing.

**[Diva**](http://www.diva-project.org/) [color=blue]"is a project to build an easy to use, scalable, open-source video editing software for the Gnome desktop. Our goal is to provide users with a complete and tightly integrated set of tools that can be used to import, edit, enhance and export digital video material. The aim of the project is to chart the unexplored areas of video editing for the open-source platform. "Diva is written in mono on the top of the gstreamer multimedia library. It currently runs only on Linux."[/color]

*Related Links:*
[Diva Author's Page](http://www.mdk.org.pl/)
[Diva @ gnomefiles.org](http://www.gnomefiles.org/app.php?soft_id=1335)

Comments?

---

### Post by curuxz on 2006-03-30
Looks really really good, will install later because I wonder how it compares to Kino and avidemux!

Thanks for letting us know :)

---

### Post by tom-ubuntu on 2006-03-30
Screenshots are looking impressive; great work! Even if I don't use video edition, I am glad to see another really nice and usefull piece of software for the gnome desktop. Keep up the great work!

---

### Post by Arktis on 2006-03-30
Hmmm, looking really nice!  I hope this will get into Dapper +1 as one of the default packages.

---

### Post by awakatanka on 2006-03-30
Nice, thats one of the prg's i still missing on linux hope it can replace my pineacle software.  And i hope it runs also smooth in kde hehe.

Waiting now till someone makes some deb files. So i can test it.

Kino wasn't good enough for me atm.

---

### Post by ssam on 2006-03-30
also see [pitivi]("http://pitivi.sourceforge.net/")

---

### Post by Buffalo Soldier on 2006-03-30
[http://pitivi.sourceforge.net/?go=features](http://pitivi.sourceforge.net/?go=features)> **Pitivi** is meant to be a easy to use non-linear video editor in the same vein as Apple's iMovie. Pitivi will support both reading and writing to any format that is supported by the GStreamer framework, but our primary objective is to encourage more content created in the free Ogg formats by the Xiph Foundation. In this regard you can also use Pitivi as an easy to use tool for just transcoding your movies into Ogg format.

Pitivi is still in early stages of its development, but its core developer Edward Hervey is working almost full time on it as part of his job for Unix and GNU/Linux multimedia experts Fluendo. Current releases should let you transcode from most formats into Ogg and also combine multiple smaller clips into one. 

[http://www.diva-project.org/](http://www.diva-project.org/)> **Diva** is a project to build an easy to use, scalable, open-source video editing software for the Gnome desktop. Our goal is to provide users with a complete and tightly integrated set of tools that can be used to import, edit, enhance and export digital video material. The aim of the project is to chart the unexplored areas of video editing for the open-source platform.

Diva is written in mono on the top of the gstreamer multimedia library. It currently runs only on Linux.

[http://blogs.gnome.org/view/uraeus/2006/03/30/0](http://blogs.gnome.org/view/uraeus/2006/03/30/0)> **Diva and Pitivi**

So why are there two efforts to make a GTK+ non-linear editor using GStreamer instead of one you might ask. Well as usual the answer is disagreement on design and component choices. While Diva and Pitivi are written in C# vs Python that isn't the important divide, although it has some secondary implications in that regard as it makes it a little easier for Novell to integrate Diva with f-spot and Banshee when its done with Mono, while for us integrating Pitivi with Flumotion to do live editing on video streams is easier when both are done in Python. Both are possible of course anyway, but using the same language does makes things easier. But as said these are secondary items.

With Pitivi we sincerely feel that the under laying design is sounder and more flexible and that the path taken with gdv, the library Diva is built upon is suboptimal and much less flexible compared to the direction we have taken with GNonLin, the library/gstreamer plugin that Pitivi is built upon. Michael obviously disagrees which this assessment which is why he wrote GDV in the first place. Time will tell who is right and not.

That said the competition between the two projects is friendly and the redundancy in work is luckily kept to a minimum due to both projects using GStreamer. A lot of the work involved for both projects is of course writing various GStreamer plugins to enable support for various formats and effects and here everything that benefits one benefits the other. Both Edward and Michael is also looking at each others code and applications for ideas and discussing technical problems, so even though there are two codebases on two languages there is a good deal of cross pollination going on.

So no matter what happens the community should have one or two kick *** non-linear editors within a year. Personally I am putting my eggs in the Pitivi basket, but I will be genuinely happy about people contributing to any of the two projects.

I think both project have a lot in common. I hope both project will work openly and share resources.

---

### Post by majikstreet on 2006-03-30
nice.. I'll have to remember all these software choices for when I buy my firewire card :D (which I could do right now because I know that my refund for a video card is approved)

---

### Post by Jonathan Métillon on 2008-02-18
Hi,

What's going on with Diva? :confused: [Official website]("http://diva-project.org/") is 404.

And main developer Michael gave [no news since 2006]("http://www.mdk.org.pl/tags/diva"). He now works for Novell. Maybe they would be interested in helping him continue his project? Diva is a Mono project, and Mono is [SIZE=-1]sponsored/supported [/SIZE]by Novell, so it would make sense.

Edit: I read in a [comment from Michael]("http://www.mdk.org.pl/2008/1/31/changes-of-n/comments/525"): *"No Diva for now, I&#8217;m going to work on graphics and other stuff related to mono and hopefully some desktop/suse. But in future &#8211; who knows?"*

Or maybe Diva efforts could be merged with [PiTiVi]("http://www.pitivi.org/wiki/Main_Page") which looks a bit more alive, with its last release in November 2007?

---

### Post by ssam on 2008-02-18
i think diva is pretty much abandoned.

[http://lwn.net/Articles/265577/](http://lwn.net/Articles/265577/) (scroll halfway down) has an up to date look at what is avaliable currently in open source.

---

### Post by Jonathan Métillon on 2008-02-18
Thank you for the link. I discovered [Open Movie Editor]("http://openmovieeditor.sourceforge.net/HomePage"), which saw a new release this month. So at least, it's an active project!

Hope the main developer will keep up his efforts. Go Richard, Go!

Edit: There's a video of [Richard demonstrating OME]("http://www.youtube.com/watch?v=9ljEb1PdEdM") on YouTube.

---

### Post by altonbr on 2008-03-11
Very sad news.

For the main developers blog on Diva, go here: [http://www.mdk.org.pl/tags/diva](http://www.mdk.org.pl/tags/diva)

Last blog asking for help: [http://www.mdk.org.pl/2006/12/7/state-of-diva](http://www.mdk.org.pl/2006/12/7/state-of-diva)

---

### Post by smartboyathome on 2008-03-11
> **altonbr said:**
> Very sad news.

For the main developers blog on Diva, go here: [http://www.mdk.org.pl/tags/diva](http://www.mdk.org.pl/tags/diva)

Last blog asking for help: [http://www.mdk.org.pl/2006/12/7/state-of-diva](http://www.mdk.org.pl/2006/12/7/state-of-diva)

The source is still available at [this page]("http://svn.diva-project.org/diva/"), so someone could take it and develop it more if they wanted. :)

---

### Post by Jonathan Métillon on 2008-03-25
> **Jonathan Métillon said:**
> Thank you for the link. I discovered [Open Movie Editor]("http://openmovieeditor.sourceforge.net/HomePage"), which saw a new release this month. So at least, it's an active project!

I just installed OME, which is in the Ubuntu repository:
```
openmovieeditor - a simple non-linear video editor
```Then I try to import my video taken with my [Kodak C330]("http://www.kodak.com/eknec/PageQuerier.jhtml?pq-path=7085&pq-locale=en_US&_requestid=3665") which is .MOV file 320 x 240 JPEG still images at 20 fps.

And OME says:
```
Video framerates other than 25 are not supported
```Richard, if you read this thread, is this planed to support other framerates any soon? Or is there an easy way to recode videos to 25 fps?

Thank you.

Edit: there's a support forum at [http://www.openmovieeditor.org/support.html](http://www.openmovieeditor.org/support.html) I will post here.

Edit 2: new thread at OME support forum started at [http://www.openmovieeditor.org/board/viewtopic.php?pid=1564#p1564](http://www.openmovieeditor.org/board/viewtopic.php?pid=1564#p1564)

---

### Post by anubis4d on 2008-04-21
Richard plans to have multiple FPS (I saw a screenshot of the next release with a FPS pull-down selector).

I started a blog about 3D transitions like hollywood FX for linux (based in a batch blender3D render), but now we will make any kind of templates for OME, like SVG titles (the next version has an internal conversion to PNG), or UV distorts.

titles
[IMG]http://www.openmovieeditor.org/images/blue2_title.png[/IMG]

UV distorts (this is a screenshot of a working OME still unreleased)
[IMG]http://propirate.net/oracle/zipfiles/uvmap_screenshot.png[/IMG]

a blendfile which renders (anim button) many PNG sequences into /tmp
[http://gvfx.blogspot.com/2008/04/post-15-open-movie-editor-s-new.html](http://gvfx.blogspot.com/2008/04/post-15-open-movie-editor-s-new.html)
[http://www.freewebs.com/marquitux/OME/distorsionesUV.blend]("http://www.freewebs.com/marquitux/OME/distorsionesUV.blend")

more stuff
[http://gvfx.blogspot.com](http://gvfx.blogspot.com)
Marquitux from Argentina.

---

### Post by Jonathan Métillon on 2008-04-22
> **anubis4d said:**
> Richard plans to have multiple FPS (I saw a screenshot of the next release with a FPS pull-down selector).

Yes, thank you. Oracle2025 answered me at Open Movie Editor board that the current version is not limited to 25 FPS anymore.

I hope the binaries from Ubuntu 8.04 repository will be up to date.

---

### Post by quinnten83 on 2008-04-22
How easy is this to use? It seems complicated!! 
Kinda like (dare I say it) Cinelerra....

---

