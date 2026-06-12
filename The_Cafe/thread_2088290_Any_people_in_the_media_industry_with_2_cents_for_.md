---
title: "Any people in the media industry with 2 cents for Ubuntu Studio and Dream Studio"
date: 2012-11-26
forum: The Cafe
---

### Post by ElBjorno on 2012-11-26
Hey guys, I'm a cameraman and video editor that's been in the industry for just a few months - I jumped in right after completing my Screen and Media course. I've been using Ubuntu Studio for a while now, and wanted to share my thoughts, as well as see if anyone else with relevant experience has any insight.

I did find a similar thread to this _[here]("http://ubuntuforums.org/showthread.php?t=1983652&highlight=studio")_, but rather than resurrect it I thought I'd start a new one.
First off, as much as I would like it to be otherwise, for most applications I have to say that Open Source does not come close to matching commercial software when it comes to multimedia creation. That being said, I have the opportunity to use Adobe Premiere at my work computer, so I'm free to have a good old romp through the open source offerings at home. For my private projects I've never felt like the software I've been using is lacking.
So what does everyone think about _[Ubuntu Studio]("http://ubuntustudio.org/")_ and _[Ubuntu Studio]("http://ubuntustudio.org/) and [Dream Studio](&quot;http://www.dickmacinnis.com/dreamstudio/about-dream-studio/")_? Are they worth it?

For me, I would say no. I'm seriously considering doing a fresh install of Xubuntu and simply installing the lowlatency kernel and whatever other programs I need.
However, my problems with Ubuntu Studio are different to those with Dream Studio. My biggest issue with Ubuntu Studio (but by far not the only one), is that, despite claiming to be an all-rounder for audio, video, photography and graphic design, they lean far too heavily on the audio side. The audio menus are positively bloated with every conceivable mixer, effect, synthesiser, DAW and god knows what else, and much of it is unsupported, ugly, buggy or completely esoteric. However the other areas, particularly video, don't have half the features one would expect. My biggest gripe in that regard is giving videographers just Openshot as a Non-linear video editor. That's like giving a photographer MS paint instead of photoshop or GIMP!

Apart from that the design is uninspired - it just looks like a stock XFCE install. There's no quick links on the desktop to the most important programs like GIMP, Ardour or the video editor, and there's very little in the way of customizing the desktop to the needs of media people. There's more I could say about it, but I'm sure you don't want to be here all day ;)
I haven't tried Dream Studio myself, but I don't see anything there that makes me particularly excited either. I don't think it would take me any longer to install the packages included in this myself, and then I wouldn't be stuck with the sh*tty Unity interface either. At least Ubuntu Studio does that right - XFCE, with its speed, simplicity, elegance and customizability is pretty much perfect for a studio OS.

At least Dream has a better Video Editor though, but not by much. Again, for a long time I really wanted Cinelerra to be good, but as someone that edits videos every day for a living, I came to the professional opinion that it's a piece of crap.
It has a few really good and powerful features, but overall the program is ugly as sin, is clunky and counterintuitive, to the point of unusability in the case of the timeline, it's buggy and unstable as hell, and it barely reads any video formats, and what it outputs can't be read by anything else. While it also has a number of its own issues, the best Non-Linear Video Editor for linux is KDenlive.  I like to use that for 90% of my work, and occasionally use Cinelerra to put effects that KDenlive can't handle.
I'm also puzzled as to why both of these suites have brasero instead of k3b - it's only any good if you want a program that makes coasters.

They both inlcude the lowlatency kernel though, which is good but pretty much goes without saying.
Sorry this turned into a bit of a rant. I'm still curious what others in the industry think. Please, let your opinions be known!

---

### Post by Swagman on 2012-11-26
Wall of text mate.

But.. Try Blender. It has a NLE built in.

LightWorks is also coming to Linux.

---

### Post by mastablasta on 2012-11-26
i am not a pro but ...
 
> **ElBjorno said:**
> First off, as much as I would like it to be otherwise, for most applications I have to say that Open Source does not come close to matching commercial software when it comes to multimedia creation. That being said, I have the opportunity to use Adobe Premiere at my work computer, so I'm free to have a good old romp through the open source offerings at home. For my private projects I've never felt like the software I've been using is lacking.

i don't know about that. adobe has some awesome features but you could probably make the same in Gimp if you wanted to. cause it's source is open :-) maybe there already is a plugin that does it.
 
what puzzles me is while i read this a lot from pro's then i look at blender projects in youtube and i can't understand what they talk about? i mean just look at sintel or big buck bunny. made with opensource. blender as i understand is also used by some big studios.
 
yet this small business studios, who know best, are all tied to Adobe suite only. sorry just can't understand it since i am not in the business.
 
> 
While it also has a number of its own issues, the best Non-Linear Video Editor for linux is KDenlive. I like to use that for 90% of my work, and occasionally use Cinelerra to put effects that KDenlive can't handle.
I'm also puzzled as to why both of these suites have brasero instead of k3b - it's only any good if you want a program that makes coasters.

Problem with kdenlive and k3b is that they are KDE (qt based) applications while XFCE and Gnome are using GKT+ so they simply isntalled native aplications. 
 
well you can always install/add what you want or install mini.iso and only add features you need/want. the distributions are ment as something prepacked. it seems the programmes in them are suitable to some.
 
 
in any case use what works best for you, or join the project and help with testing/ideas/creating content...
 
for us non-pros's the tools seems ot be fine. though for some reason i can't get kdenlive to encode.

---

### Post by Bucky Ball on 2012-11-26
@ ElBjorno: Please format your post, i.e. paragraphs! That is a barely readable block of text and most will just move on ...

To my knowledge the bigger production houses create effects and apps in Linux, when appropriate, to suit their purposes rather than using any particular 'off the shelf' app. 'Appropriate' would be when an effect they want is not available OTS. This creates a unique effect which sets them apart from other effects departments. I know for a fact this is the case with Rising Sun Pictures and have been told of the same situation with other companies ...

---

### Post by ElBjorno on 2012-11-26
Sorry about the wall of text - always been my problem, writing more than I have to! :P
But you're right about Blender - it's very much commercial quality. However, it's also a massively steep learning curve, especially if all you want to do is straight up video editing. I'm also not convinced for that side it has all the features and usability of dedicated non-linear editors, but I've yet been able to penetrate it to find out.

Also, I figured that K3b and KDenlive being KDE applications had something to do with their not being included - but seriously, that just sounds a bit lazy to me. Maybe I'm naive and don't know what it takes to make a distro, but I figure if adding qt support is what it takes to get the best packages for your distribution, then why not do it? I didn't have any problem installing them myself.

As for adobe, they make a whole lot more than just Photoshop. While GIMP is getting close to Photoshop in many areas, there's still nothing that matches their Video editor, Premiere.
And while I would like to see lightworks for linux, I'm not holding my breath.

Also, I know I can just install packages after the fact (as I've done with half the stuff I use!), but why make a studio distribution at all in that case? That's why I said I'm thinking of switching to straight up Xubuntu. Fact is, Ubuntu Studio is just too bloated.
I have also thought of joining the project. Maybe I should look into that again...

PS, don't think I'm trying to disparage Open Source software. The rate it's catching up to commercial software (and in some cases overtaken) I wouldn't be surprised if there was something to truly rival the likes of Lightworks and Premiere in the next five to ten years. It just needs enough backing and interest.

(This may have become a bit long again, sorry!)

---

### Post by ElBjorno on 2012-11-26
> **Bucky Ball said:**
> @ ElBjorno: Please format your post, i.e. paragraphs! That is a barely readable block of text and most will just move on ...
Yeah, I should know better than that :oops:. Fixed it though :)

> To my knowledge the bigger production houses create effects and apps in Linux, when appropriate, to suit their purposes rather than using any particular 'off the shelf' app. 'Appropriate' would be when an effect they want is not available OTS. This creates a unique effect which sets them apart from other effects departments. I know for a fact this is the case with Rising Sun Pictures and have been told of the same situation with other companies ...

Hmmm... that sounds interesting. I haven't heard of that. Though I don't suppose they release them to the public as open source, do they?

---

### Post by mastablasta on 2012-11-26
[LEFT]> **ElBjorno said:**
> Also, I figured that K3b and KDenlive being KDE applications had something to do with their not being included - but seriously, that just sounds a bit lazy to me. Maybe I'm naive and don't know what it takes to make a distro, but I figure if adding qt support is what it takes to get the best packages for your distribution, then why not do it? I didn't have any problem installing them myself.

because for once having even a small KDE app needs you to also get in all the qt packages with it. that increases the image size. that is one point. i installed skrooge n windows (KDE for win porject). skrooge is about 12MB big. well it  pulled over 250 MB dependencies along with it. :P
the other is that the different applicaitons might not look as good or might not have a good desktop integraton. for example Chrome/Chromium browser looks ridiculous in KDE, but Firefox looks fine.
 
so i guess it has a lot to do with looks. once i figured out that most featurefull applications are qt based i switched to KDE.
 
> 
Also, I know I can just install packages after the fact (as I've done with half the stuff I use!), but why make a studio distribution at all in that case? That's why I said I'm thinking of switching to straight up Xubuntu. Fact is, Ubuntu Studio is just too bloated.
I have also thought of joining the project. Maybe I should look into that again...

i have no idea why they make them. i think they make them just because they can make them :-)
 
the specialist distros so far that made sense to me were some server/NAS, router/firewall and security & hacking distros. i mean to make it easier to use them for end user. the rest is mostly just variation of same thing. if Ubuntu studio doesn't seem good to pro's then perhaps they are are at it the wrong way. i mean they selected wrong applications.
 
you can easilly make you own distribution.[/LEFT]

---

### Post by Bucky Ball on 2012-11-27
> **ElBjorno said:**
> Hmmm... that sounds interesting. I haven't heard of that. Though I don't suppose they release them to the public as open source, do they?

Nope. That's gold ... priceless. But give it twenty years and the effect will be old hat ... maybe! ;)

Interesting talking point though; an effect isn't really developed with open-source software, but with a computer language. Anyone can code up a machine, so yea, that code only belongs to the person that wrote it. Up to them how they go about 'owning' it. If they want to make it 'open' it is up to them.

I guess when a company pays a person or a team to code up an effect, then the 'effect' belongs to the company through licensing, perhaps, legalities and other restrictions ... hmmm.

Check out Rising Sun's site and you'll see what I mean re 'homegrown' or I suppose open-source FX ... they get a lot of work because they come up with original stuff:

[http://www.rsp.com.au/news.htm](http://www.rsp.com.au/news.htm)

(sorry, thinking out loud ;))

---

