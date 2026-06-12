---
title: "recomendation for video editing program"
date: 2009-12-07
forum: Ubuntu Studio
---

### Post by ppitme on 2009-12-07
Hi people. Have just resently tride out ubuntu, realy like the sistim. How ever i want a vidio editing program for ubuntu, something like adobe premier elemens, cuz me and friends are making a movi. Any sujestions? i dont care if its hard, i will just get a manual. (sorry for the speling)

---

### Post by BenAshton24 on 2009-12-07
OpenShot [http://www.openshotvideo.com/](http://www.openshotvideo.com/)

---

### Post by alwayshere on 2009-12-07
kino

---

### Post by ppitme on 2009-12-07
> **BenAshton24 said:**
> OpenShot [http://www.openshotvideo.com/](http://www.openshotvideo.com/)
is ther a manual or something somewere. cant seem to find one....

---

### Post by lovinglinux on 2009-12-07
OpenShot, Kino, Pitivi, Cinelerra, Kdenlive...

See [http://linuxappfinder.com/multimedia/videoeditors](http://linuxappfinder.com/multimedia/videoeditors)

---

### Post by RedRat on 2009-12-08
As you can see there are recommended software available, check the individual web sites to see if documentation is also available. Some documentation is pretty sketchy so you will have to work through it. i am not aware of any books on the programs mentioned written by a professional writer and published, a weak point of the open source movement.

---

### Post by createsean on 2010-01-31
I'm new to ubuntu and am giving openshot a try. I installed lives but wasn't impressed. 

Any other recommendations? I'm coming from windows and am very comfortable editing video in Adobe Premiere Pro - one thing is I need to be able to edit avchd files from my camcorder -file extensino .m2ts

---

### Post by alegallo on 2010-01-31
cinelerra is great, at least for me

Powerful, complete, a professional piece of software, well, maybe not so easy to learn, but great for me ;)

---

### Post by cotcot on 2010-01-31
What features do you want ? 

High level are cinelerra and blender (VSE). (IPO curves; keyframing; multitrack; effects; corrections ...)
Low level is Kino (easy, solid, single track). (fine to get clips together with some transitions;putting an audio track on it and add titles)
Others are somewhere in between. (effects ; multitrack; effects; corrections ...)

---

### Post by RedRat on 2010-01-31
Has anyone tried running Adobe Premier Elements under Wine?

As to best software, if you are a beginner, you will find documentation sparse for many of the recommended programs here. If you are coming from Elements, then Kino is the closest.

---

### Post by LuridCinema on 2010-01-31
I'd say that Cinelerra is the most powerful hands down ( waiting patiently for Lumiera )  and Openshot has additional features .  Kino and Pitivi can easily encode and convert most anything you drop into it. Add ffmpeg and you have a very powerful set of video tools. My suggestion would be use all 4 NLEs and augment w/ ffmpeg.

Blender is mostly for 3D and will do basic NLE functions, however it is pwerful when it comes to 3D animation. for 2D animation, Synfig is another free tool .

Id say look at what is it you are wanting to do and choose from all the above is my 2 penneth worth

---

### Post by createsean on 2010-02-01
Just saw this article on [Ars Technica about 2 video editors]("http://arstechnica.com/open-source/guides/2010/01/video-editing-in-linux-a-look-at-pitivi-and-kdenlive.ars?utm_source=rss&utm_medium=rss&utm_campaign=rss") for linux.

---

### Post by RedRat on 2010-02-01
> **createsean said:**
> Just saw this article on [Ars Technica about 2 video editors]("http://arstechnica.com/open-source/guides/2010/01/video-editing-in-linux-a-look-at-pitivi-and-kdenlive.ars?utm_source=rss&utm_medium=rss&utm_campaign=rss") for linux.

I have played with both of these and it pretty much sums up my experiences with both programs. You can use DVgrab to get your video off your camcorder, it comes off in .m2t format, I believe it is mpeg-2, and then can be edited in whatever program you chose. Right now, I would think that Kino shows some promise.

---

### Post by SoFl W on 2010-02-01
I started using this:
[http://www.kdenlive.org/](http://www.kdenlive.org/)

---

### Post by cotcot on 2010-02-01
> **LuridCinema said:**
> 
Blender is mostly for 3D and will do basic NLE functions, however it is pwerful when it comes to 3D animation. for 2D animation

Do not know from which blender version you talk. Anyway the actual version (2.49) of blender has a very powerful NLE : compositing power; keyframing on a lot of features; node editor; effects; picture in picture; ... .

After trying out Kino, Kdenlive, Cinelerra, Avidemux, Pitivi (earlier versions), Lives I selected first Cinelerra and finally switched to blender as NLE because of its many possibilities and good rendering (rendering was a problem with cinelerra, for the rest I love this editor as well). I recently checked pitivi and openshot but did not found (yet) the tools I need and have with cinelerra and blender.

Only later I started discovering blender for 3D. The possibility to intergrate 3D stuff in video editing is great.

---

### Post by createsean on 2010-02-01
I put together a quick video with kdenlive using .m2ts files and had no problem other than it hangs periodically.

I looked at the blender site, but it looks to me like it's primarily a 3d program and not a movie editor - I definitely would use it if it does key frames and HD video

---

### Post by LuridCinema on 2010-02-02
Although I have been a little off on Blender, It does do Hi-Def and keyframes. Id still say Cinelerra is more powerful in straight video production as the interface once learned has a better workflow and I feel I could do more and do it quicker in Cinelerra as it looks much more suited for production  In My Opinion. HOWEVER find what works for you we all have diffent needs, levels of experience and since most of these NLE's can be a little buggy. Go with what works on your computer


"The possibility to intergrate 3D stuff in video editing is great."   <<< Powerful if you know how to use it for sure as the FX possibilities are endless. I'm seeing how much I can do w/ Synfig ( 2D ) and it sure looks like fun and powerful

---

### Post by gordintoronto on 2010-02-02
> **createsean said:**
> I'm new to ubuntu and am giving openshot a try. I installed lives but wasn't impressed. 

Any other recommendations? I'm coming from windows and am very comfortable editing video in Adobe Premiere Pro - one thing is I need to be able to edit avchd files from my camcorder -file extensino .m2ts

I use Video Converter to create .mpg files, then edit them with Cinelerra.  I'm delighted with the results.  (Sometimes I create DVDs, sometimes I post on youtube.)

---

### Post by savaan on 2010-02-25
I'm having an issue installing any of these. I already have Kdenlive, but not pleased with some of the features. Could be the learning curve, but I need something quickly to edit with. Anyway, I'm getting this when I try to install anything: 

```
W: GPG error: http://downloads.sourceforge.net all Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
```

---

### Post by wkulecz on 2010-02-26
I'll give you the answer you don't want to hear.

Time is money.  If you are at all serious about editing video (especially high definition) buy a PC or a Mac and get'er done.

Video editing on Linux is about like it was on Windows in 2000 -- you can make it "work" if you dick around with it enough, and have near infinte time to search and find solutions to problems.

I put together a cheap quad core system from parts on sale at Frys, got Windows 7 home premium OEM and Sony Vegas Video Pro, and have a tool that works, not a project.  Its all the box is used for.

--wally.

---

### Post by misterbk on 2010-02-27
As far as using Blender for video editing, I was under the impression Blender's video powers were more focused on a compositing workflow?

As in, you can use Adobe AfterEffects to edit video...  But the process will be slow, painful, and lacking essential workflow features because it is -really- meant for stacking many layers of effects on top of a single video shot, not joining multiple shots side by side on one or two layers.

Am I wrong?  Has Blender integrated an actual editing workflow, not compositing workflow?  (Whenever I pick up Blender I find it difficult to navigate and locate features, and it goes back on the shelf.  Because what wkulecz says is sadly true.)

---

### Post by cotcot on 2010-02-27
> **createsean said:**
>  one thing is I need to be able to edit avchd files from my camcorder -file extensino .m2ts

I convert my .m2ts files to mpeg and use the mpeg file in the video editor.
Kdenlive however can edit .m2ts. I have tested this but it gave choppy video (a frame rate issue). 
I convert from command line with mencoder but you might check out Handbrake to convert.

---

