---
title: "ipod dilemma"
date: 2007-01-10
forum: The Cafe
---

### Post by Polygon on 2007-01-10
So, my brothers windows installation died (will not boot, something about invalid device... yeah yeah) so im decididng on whether or not to install ubuntu or just reinstall windows

all he really does is surf the internet, watch youtube and play runescape (a java internet browser game so that SHOULD work...) but he also has an ipod...

and im worried that if i install ubuntu he wont be able to play his itunes music protected files (cause he got some itunes giftcards for xmas and had some before) or sync them to his ipod.... 

I know i can just let him use some other music manager besides itunes (like listen or something) but are there any programs (like gtkpod, or maybe gtkpod will do this) that will actually sync his itunes protected music? Or maybe even possibly play it? (i doubt it)

---

### Post by BarfBag on 2007-01-10
There isn't a FairPlay codec available, so he won't be able to listen to them on his PC.  GTKPod might make it possible to put them on the iPod.  It supports .m4p and .acc.  I'm not sure whether or not it will work with DRM, though.

The easiest thing I can think of is this.  Have him create a playlist (in iTunes, of course) with all of his "protected" songs.  Then, burn it to a CD.  This will strip it of it's DRM.  Then, rip the CD in Ubuntu.  There's a tiny loss in quality when you do this, but it's very small.

---

### Post by ner0tic on 2007-01-10
> **BarfBag said:**
> There isn't a FairPlay codec available, so he won't be able to listen to them on his PC.  GTKPod might make it possible to put them on the iPod.  It supports .m4p and .acc.  I'm not sure whether or not it will work with DRM, though.

The easiest thing I can think of is this.  Have him create a playlist (in iTunes, of course) with all of his "protected" songs.  Then, burn it to a CD.  This will strip it of it's DRM.  Then, rip the CD in Ubuntu.  There's a tiny loss in quality when you do this, but it's very small.

you could use amarok to load music onto the ipod.  You may be able to run itunes via wine i haven't tried this i use amarok and it does what i need just fine.

---

### Post by jbus on 2007-01-10
The only solution I have found for this is to copy all your DRM protected files to music cds & rip them in ubuntu or you can install Windows/iTunes using vmware and just start it up when you need it.

Honestly, if Apple would make a Linux version of iTunes or one that runs properly in Wine, it would eliminate the need for many people to use Windows on their PCs.

---

### Post by BarfBag on 2007-01-10
> **ner0tic said:**
> you could use amarok to load music onto the ipod.  You may be able to run itunes via wine i haven't tried this i use amarok and it does what i need just fine.

Wine doesn't run iTunes.  Crossover does, but you have to pay for it.

---

### Post by jbus on 2007-01-10
> **BarfBag said:**
> Wine doesn't run iTunes.  Crossover does, but you have to pay for it.

To my knowledge, Crossover office only runs iTunes version 4. Which makes it useless to most iTunes users because once you upgrade past iTunes version 4 (which almost everyone has) you can't go back... The files purchased with your account won't play with version 4.

---

### Post by dbbolton on 2007-01-10
codeweavers

---

### Post by BarfBag on 2007-01-10
> **jbus said:**
> To my knowledge, Crossover office only runs iTunes version 4. Which makes it useless to most iTunes users because once you upgrade past iTunes version 4 (which almost everyone has) you can't go back... The files purchased with your account won't play with version 4.

Good point.  I forgot about that.

---

### Post by SilverDragon on 2007-01-13
> **jbus said:**
> 
Honestly, if Apple would make a Linux version of iTunes or one that runs properly in Wine, it would eliminate the need for many people to use Windows on their PCs.

I agree :-)

I was wondering, is there a way to transfer your music from your iPod onto Linux? For example, on Windows there is software such as iPodcopy, iPodAgent, xPlay, things like that. Or maybe there's a way around it like there is on Windows, even tho it is a pain to get them onto iTunes like this : [http://www.cnet.com/4520-7899_1-6477981-1.html?tag=nl.e404](http://www.cnet.com/4520-7899_1-6477981-1.html?tag=nl.e404)

I'm asking because for anyone with over 1000 songs, it would be a big hassle to burn all those songs to cds, even if you had a cd you can rewrite over and over and over.

---

### Post by nandasunu on 2007-01-13
> **SilverDragon said:**
> I was wondering, is there a way to transfer your music from your iPod onto Linux? 

You can load the ipod in amarok and "copy to your collection" easily from there. if you have drm files, this probably won't help you much tho, works fine for getting your standard mp3s off the ipod and onto your hard drive.

---

### Post by SilverDragon on 2007-01-13
Could I go to Tools > Rescan Collection, for the same effect? 

And where is the music copied to on the hard drive? You can probably change it somehow, but what is the default? File management on Linux seems a bit tricky right now, but of course everything new is weird at first ;-)

---

### Post by Polygon on 2007-01-14
are you talking about how to get itunes drm files to mp3s from the ipod?

The only way to do that is burn em as a regular cd in itunes, and then re-rip them as mp3s.

but to get just all the music on your ipod to your hard drive in linux, follow the instructions a few posts up.

---

### Post by Voxxi on 2007-01-14
> **SilverDragon said:**
> I agree :-)

I was wondering, is there a way to transfer your music from your iPod onto Linux? 

If you have your iPod enabled as a hard-drive you can just copy all the music files off it. They'll have cryptic names like FGHTW.mp3, but you can use EasyTag to rename them all based on the ID3 tags. That's what I did with my iPod.

---

### Post by nandasunu on 2007-01-14
> **SilverDragon said:**
> Could I go to Tools > Rescan Collection, for the same effect? 

no. the rescan is just to update the list of files in your music folders. 

> And where is the music copied to on the hard drive? You can probably change it somehow, but what is the default? File management on Linux seems a bit tricky right now, but of course everything new is weird at first ;-)

The files are copied to your music folder (that you set up the first time you ran amarok). When you copy the files it will give you some options for arranging the files, they are grouped into folders based on the artists name/album. This method is way better than copying the cryptic filename files directly as you don't have to do any renaming.

Basicly to copy your mp3s (non drm) just:

 - open amarok
 - plug in your ipod
 - a popup will appear, asking how to treat the device. in the drop down menu chose "Apple Ipod ...". 
 - in amarok go to the media device tab, click connect (if you get any messages about locks, just click remove)
 - your media files will be visible now, select the ones you want, right click and "Copy Files to Collection"
 - choose your file naming scheme in the popup and hit ok - job done!

You can then find your files and move them to different locations if you want, as long as they are within the scope of your music folder amarok will update the locations of the files, you can also "rescan collection" to have amarok update locations.

For DRM files, burn to cd via itunes (on widows/mac) as said before & rip.

---

### Post by SilverDragon on 2007-01-14
When I click on "Copy Files to Collection", the collection folder says its /media/ipod,(which cannot be changed) which is on the iPod itself?

I could move around the files, but I can't seem to create folders in my media folder? I'm guessing you have to do this in the terminal somehow? The only place I can already make a folder is on the desktop but its not in the scope of where Amarok will scan when I ask it to rescan collection.

---

### Post by nandasunu on 2007-01-15
> **SilverDragon said:**
> When I click on "Copy Files to Collection", the collection folder says its /media/ipod,(which cannot be changed) which is on the iPod itself?

I could move around the files, but I can't seem to create folders in my media folder? I'm guessing you have to do this in the terminal somehow? The only place I can already make a folder is on the desktop but its not in the scope of where Amarok will scan when I ask it to rescan collection.

It sounds like you don't have your collection set up right. 


Make sure you have specified to Amarok where your mp3s are stored by going to - Settings: Configure Amarok: Collection. Navigate to the folder your music is in and click the little box next to it, that and all subfolders will then be scanned for music and you should be able to copy to your collection ok. When you do that the mp3s will be saved in the folder you specified, you can then move them in nautilus/konquerer.

Amarok just looks at any folder you specify on your hard disc when it creates the collection, you can't create folders from within Amarok. The "folders" you see within Amarok are just all the files within the orginal specified folder (on hard disc) organised by artist/album etc (based on the id3 meta tags).

---

### Post by Aetherius on 2007-01-15
DRM:evil:

---

