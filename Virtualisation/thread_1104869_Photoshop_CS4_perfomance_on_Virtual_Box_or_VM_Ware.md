---
title: "Photoshop CS4 perfomance on Virtual Box or VM Ware"
date: 2009-03-24
forum: Virtualisation
---

### Post by Draxeiro on 2009-03-24
Hi there,

I am a professional graphic designer looking to make the switch to Ubuntu (currently using XP). But first I would like to find out if it is in fact a realistic proposition.

Now, I know there are Linux-alternatives for quite a few of the applications I am using but for my workflow in conjunction with professional printers, other designers, developers, etc switching to programs like Gimp, Scribus and Inkscape is just not realistic.

I am aware that going the Wine route will not be very fruitful for the software I am using, so I am currently looking into the option of Virtualization.

I use Photoshop CS4 and Illustrator CS4 (among other programs, but these are the most important ones).

So I am very interested in finding out how these programs perform under either Virtual Box or VMware. 

Is there much of a perfomance hit, do these programs function properly and/or are there functionality issues? 

I've heard conflicting stories with regards to CS3 for instance: one says that works like a charm, another says it gets very slow when working on large multi-layered files. I've also found out that Virtual Box contains a bug which causes colour profiling not to work properly in Photoshop.

Add to this the fact that CS4 makes direct use of the video card as opposed to the earlier incarnations that solely went the CPU route. So I am not sure what that means for its functionality and/or speed while virtualizing.

To give you an idea I do regularly work on images that are 50-100Mb, consisting of dozens of layers.

I hope some of you can give me advice if virtualization is indeed a route to take or if I will, realistically, be better off for the time being sticking with XP (until such time when CS4 works flawlessly with Wine for instance).

Speed and performance is key for me. Especially considering the large file-sizes I often have to deal with.

So if you have any experience please let me know :)

Thanks a lot in advance for your advice!

---

### Post by Mistrblank on 2009-03-24
You won't get direct access to your video card and I suspect that will end any further discussion right there.

---

### Post by Draxeiro on 2009-03-24
CS4 will also function without being able to access the video card drivers I believe. So in that respect I am quite curious to find out if somebody has had any hands-on experience. And if so, what that experience was.

---

### Post by kakkapeelo on 2009-05-29
I have CS4 installed on Windows XP SP2 running in virtualbox. It works quite well. You may experience the menus being a bit more sluggish than in a real environment and you wont get OpenGL acceleration.  Make sure you got plenty of memory for your virtual machine though. Otherwise you will get constant errors in Photoshop when trying to do things that are memory intensive. I have also experienced som odd behaviour with certain brushes causing the mouse not register properly somehow in the Photoshop interface and making the brush appear as a black box. You can paint with it as usual but you wont get the brush preview on the actual painting area.   If you want speed, then a real environment is the only soution I'm afraid.

---

### Post by rliegh on 2009-05-29
> **kakkapeelo said:**
> I have CS4 installed on Windows XP SP2 running in virtualbox. It works quite well. You may experience the menus being a bit more sluggish than in a real environment and you wont get OpenGL acceleration.  The non-free version of VirtualBox offers support for OpenGL acceleration, and that might be worth exploring.

---

### Post by kakkapeelo on 2009-05-29
"The non-free version of VirtualBox offers support for OpenGL acceleration, and that might be worth exploring."  True But I have not managed to get it working, even with Adobes "own" registry hacks for forcing opengl and setting the opengl compatibility mode. Dont have any problems with the opengl acceleration in the real envinronment though.

---

### Post by HDave on 2009-05-29
Enough of the theory.  

I use Adobe Lightroom 2.x in VMWare Workstation regularly for RAW photo processing.  If I am correct, Lightroom takes even more CPU cycles than Photoshop.

While VMWare Workstation doesn't provide the guest OS direct access to the video adapter, it also does not use software emulation and I have found the performance acceptable.  I only have a dual-core 2.0Ghz laptop.  If you set up your box as a dual-boot, you should know that VMWare Workstation can boot a VM off a physical partition of a real machine.  That is, you could use VMWare Workstation some of the time and reboot into Windows if you need the extra boost...and you'd be using the same "machine".  (disclosure:  I have not done this.)

I have benchmarked the 2D graphic performance of several (not all) virtualization technologies and found VMWare Workstation to be the best by far.  The tool I used to benchmark can be found [here.]("http://www.passmark.com/")

If I had the latest Quad-Core Xeon 3.3Ghz then I'd probably enjoy it a lot more....   You should download the trial version of Workstation and see how it performs on your box.

You'll also need to think about color management, but that's another thread...

---

### Post by gespertino on 2009-07-03
It's not unrealistic to expect to work with free software for design. I do it daily and once you find an adequate workflow it's not that hard.
There are several caveats though. But it's matter of finding some workarounds.
I use Inkscape, gimp and Scribus and I can send my design work to a print shop as CMYK PDF or TIFF, and never had problems.
Obviously, you can't match the convenience of a fully integrated suite like adobe's with separate free applications (and some of them under development) but you can work without much hassle.

Anyway, if you want to run the actual Adobe applications, the best you can do is running them virtualized.They were designed for the Windows environment, so you should run them on Windows if you want the best performance.
Virtualbox is great. The 3D part is pretty experimental yet but if you could work without 3D acceleration before Adobe CS3, it won't be a big problem if it doesn't work.
Apart of the 3D acceleration, the rest of the system works really good, and the performance penalty running a virtualized Windows guest on a modern machine is minimum.
I recommend you to install windows and the adobe apps ONLY on the virtualized guest, and don't connect the guest to the net (use shared folders for your files). De-activate the visual enhancements of your XP installation (theme, animation, etc.) and you'll get a really fast working environment, without viruses.
Use your Ubuntu for the rest, and you'll be fine.

HTH,

Gez.

---

### Post by steveneddy on 2009-07-03
For my two cents, maybe a Mac would be better if you are wanting to get away from Window so bad.

You could run XP in Virtualbox on top of Ubuntu.

You will still run into performance issues.

---

### Post by king0lag on 2009-07-29
Hello,

I am looking to do the same thing and I was wondering if you have made the switch yet? I myself have a Dual 2.8GHz Processor but only 2GB of RAM. I tried to make the switch over a year ago and couldn't handle getting Adobe Suite in Wine (this was before I knew about virtualization). Anyway if you did, please let us know of your results :)

---

### Post by fjgaude on 2009-07-30
I've been using VMware free server under Ubuntu for about three years. Though I don't use Photoshop anymore my other graphic programs work fine with my system. Notice my signature. Do have 4GB of fast RAM. Video speed is not an issue... just about as fast as native with the Windows apps.

---

### Post by amadeobellotti on 2009-07-30
I recently installed an old version of xp on my ubuntu laptop trough virtual box just so I could run Photoshop cs4, and it works great. I don't deal with huge files just some photography (2gb files). It works out really well. 

I bought a tablet from buy.com for like 20 bucks and im gonna try to get it to work with virtualbox. (if anyone has any suggestions please send them this way)

Also I have a total of 2 gigs of ram on my laptop. Photoshop runs great with .75 gigs of ram and .25 gigs of video memory. it works great. The only issue is that if your windows cd is old its gonna take forever to bootup and install all the updates (I had a cd with SP1 on it and it took me 4 hours to install).

Thats my 2 cents on the subject. Good Luck and great choice switching to Ubuntu.

---

### Post by jocampo on 2009-07-30
> **Draxeiro said:**
> switching to programs like Gimp, Scribus and Inkscape is just not realistic.

I do not want to debate :-) though this is a free world and a this is an UBUNTU forum, lol ... but, why switching from Photoshop to Gimp is not realistic, can you provide facts, please?

I can't tell about the other two, but GIMP has nothing to envy to Photoshop and you can do almost everything (I've used both) The fact that GIMP is free and you have a community that can provide free support, are strong reasons.

I respect your opinion and current situation but probably you should give GIMP a try. I did the same to UBUNTU (I'm MCSA and MS-SQL dba for a big company) and don't regret the change. Of course, can't do the same on my job but my laptop is free of viruses and got plenty of free software to play with

---

### Post by king0lag on 2009-07-31
I'm not the OP, and I'm not looking to start a flamewar either but anytime I see these kinds of topics pick up I usually quote this post from [http://is.gd/1W8dD](http://is.gd/1W8dD)

> At the risk of not sounding pro-linux enough, I'll throw in my two cents here

I can think of a number of reasons - although my experience with the Gimp is limited, so if I am wrong on some points, by all means set me straight.

The main one, for me, is the learning curve. I have been using Photoshop since 2.0 - it's a VERY deep application capabilities-wise, which comes at a price in learning to work with it productively and efficiently. When you invest that kind of time and experience, moving to something that is as different as the Gimp UI-wise is a challenge.

Another is file exchanging - if you are working with a team of grpahic artists, often you pass around the native Photoshop file, with layers and such intact. AFAIK, the gimp uses a different format, so this would be tough.

Then there is the now fairly nice intergation with Illustrator, which allows passing files (or just paths and such) between the two apps. Although Gimp is a reasonable bitmap alternative to Photoshop in many cases, I have yet to find anything aprocahing Illustrator on Linux - let alone with the integration with Gimp to match.

If you are talking about print work, is handling color matching and all of the related issues therein. This one issue is why, until fairly recently, Photoshop wasn't just enough, but Photoshop on MacOS was virtually necessary. Linux and the Gimp (again, AFAIK) don't have the depth and breadth of tools that work with apps like Photoshop and Illustrator to assure that what you see on the screen will resemble the output you see at the end of the production cycle.

Along these lines, there is the huge number of Photoshop-specific plug-ins available. Some are just eye-candy, but many are important tools for a production print environment.

I do hope Adobe ports thier graphics tools over, but the core of thier business is still the professional graphic arts community (you know, the ones who actually pay the $900 a licsense for each app), and there are still too many holes in the Linux tool kit for there to be too much adoption of it in a production environment.

Let's be honest, the terrible time many people seem to have getting thier font situation sorted in X may seem like a nuisance for the average user just wanting thier desktop to look pretty, but it is a show stopper for people trying to crank out magazines and flyers and so forth. WYSIWYG is not an option, it's a requirement to do business.

The Gimp is actually fairly impressive, but until it can play nice with the rest of the pieces of the larger graphics production puzzle, Photoshop (on another platform, really) is still indespensible.

I am a commercial graphic artist, it's how I make my bread and butter. I've used GIMP and I've it has it's perks but when I am working with a team I just need to live in the industry standard workflow. I love Ubuntu, but I need to make sure I keep my productivity up and my downtime to a minimum. :)

Basically it comes down to the point that if I told a client, a co-worker, or a print shop they needed to try GIMP, I would never have a job again.

For the record I'm going to attempt to make the switch back this weekend! So here goes...

---

### Post by HungryMan on 2009-08-06
To counter that guy's argument:

Learning curve - true, changing applications is a PITA. If you use something other than a decent X Window Manager (which OS X or Windows has), the interface is really horrible. Everything wants to be on top of the image, or switching windows is clunky.

File exchange - iirc, GIMP has been able to read and write PSD files for a while already.

File exchanging - nothing to say about this.

Color Matching - I admit it, color modes other than RGB and indexed haven't really "sunk-in" with GIMP. Krita does though, but that's a different story.

Photoshop vs Gimp has been always a fanboy argument. Photoshop isn't an industry standard, it's a de-facto standard.

And to anyone else who wants to know about virtualizing photoshop, Dreamworks Animation uses Red Hat as their OS, GNOME as their DE and VMWare to run Photoshop. Iirc, they didn't change this when they made Shrek.

---

### Post by alex.rayu on 2009-08-06
Adobe CS4 runs well in a VirtualBox. The processor will warm more though. If it's not a laptop, you will not notice.

---

### Post by king0lag on 2009-08-07
Well today I made the switchover on my machine and everything is working perfectly on the specs I listed above so it can be done :)

> **HungryMan said:**
> File exchange - iirc, GIMP has been able to read and write PSD files for a while already.

As of today's date it does not function with any of my CS4 files, it flattens them without warning. :(

---

### Post by sototallycarl on 2009-10-29
> **king0lag said:**
> Well today I made the switchover on my machine and everything is working perfectly on the specs I listed above so it can be done :)



As of today's date it does not function with any of my CS4 files, it flattens them without warning. :(

This is because its PSD 6 or 7 spec, whichever was last 'open.' Layer styles, smart filters, folders, smart objects, layer comps all gone and probably GIMPs default action is to flatten foreign PSD elements/files. This is the number one reason i can't rid myself of photoshop and the simple fact GIMP doesn't do layer folders. at least krita does this...

Otherwise, I have run the entire CS4 in both VMWare and VirtualBox and I can say for sure the VB wins performance wise. I personally go for unity or seamless mode which takes a bit of a hit, but I would say performance is generally acceptable. I tried out After Effects too (eeek!) and I did a little render test OS X native VS XP in VB on top Ubuntu and the results were real bad. 45 minute render compared to 4 minutes native.

edit: Just set up a new install. VMWare 7, Windows 7 and CS4. I have to say if you have the time and money to put into this set up, do it! Try the trials first of course, but its seriously fast enough to work with (even in unity with compiz). Best way to test it is grab some files you work on normal on a Mac or PC and try it out. For me, it works better than I could expect. I thought 7 would drag compared to XP, but clearly I was wrong.

---

### Post by Kenny Danger on 2011-01-18
> **HungryMan said:**
> Photoshop vs Gimp has been always a fanboy argument. Photoshop isn't an industry standard, it's a de-facto standard.

It has nothing to do with being a fanboy, CMYK is print industry standard. If you are working with video or whatever then great but if you are expected to work in a print production environment then you need to be able to output to press.

:popcorn:

---

