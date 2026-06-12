---
title: "Blu-ray discussion thread"
date: 2009-01-07
forum: The Cafe
---

### Post by 3rdalbum on 2009-01-07
Hi all! I got a Blu-ray drive for my computer the other day and I've been enjoying the higher picture quality of the movies, even though I'm just using my 17 inch computer monitor :-)  It was a slight hassle to get it working on Linux, involving decrypting and dumping the contents to disk and compiling Mplayer from svn. I still don't have really fluent playback but it's pretty good.

My main complaint with Blu-ray is that the picture quality is just SO good, that if bad quality film stock is used for the original recording and the distributor is too cheap to digitally remove the film grain, then the picture quality really suffers. Still that's not a problem with Blu-ray, it's a problem with people.

If anyone wants to raise any topics about Blu-ray, feel free! What movies are best on Blu-ray? What sort of TV or computer monitor are you watching them on? What do you think of the range of titles currently available?

---

### Post by Joeb454 on 2009-01-07
I got a Blu-Ray/HD-DVD combo drive the other day, it's brilliant :) I'm watching on [this monitor]("http://www.ebuyer.com/product/132115/show_product_reviews") and the picture is, as you say, fantastic.

I only have Hancock on Blu-Ray right now, I'm still waiting for the Dark Knight. If you really want to see good picture quality, get an animated film, as it's a digital-digital transfer the picture will be pretty much flawless.

I know the Matrix has awesome picture quality if you like those films :)

---

### Post by Sealbhach on 2009-01-07
Hi,
Did you use this guide here?

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

I have a Blu-Ray drive on my laptop, I used it in Windows a bit but not much. I was thinking of getting it working in Linux but it looks like a bit of hassle. 

Also the fact that you need 50GB of temporary disk space is a but much!:(


.

---

### Post by mips on 2009-01-07
There are some movies that were recorded with digital cameras, just don't remember which ones.
[COLOR=Red]Edit:[/COLOR] [http://en.wikipedia.org/wiki/Digital_cinematography#List_of_major_films_shot_in_digital](http://en.wikipedia.org/wiki/Digital_cinematography#List_of_major_films_shot_in_digital)

Film is still a better medium and these days scanned at about 4000 lines of resolution which beats any digital movie camera out there. The quality of the end product relies on the quality of the original film and post processing. You can get a movie from the 60's to look as good as a modern day movie.

---

### Post by Joeb454 on 2009-01-07
> **mips said:**
> There are some movies that were recorded with digital cameras, just don't remember which ones.

Film is still a better medium and these days scanned at about 4000 lines of resolution which beats any digital movie camera out there. The quality of the end product relies on the quality of the original film and post processing. You can get a movie from the 60's to look as good as a modern day movie.

I have to agree. I can't remember which film it was, but it was pretty old (60's maybe early 70's) and had obviously been recorded on film.

A friend of mine has it on HD-DVD, and despite thinking the film was pretty boring, the picture quality was outstanding, far better than any modern day films :) Odd when you think about it initially, but mips described why quite well.

---

### Post by SunnyRabbiera on 2009-01-07
Bah blue ray might offer a better picture, but its a crap format.
Its practically impossible to use on linux, thanks to DRM loving idiots who think linux is the antichrist.
Heck not even DVD is as closed off!
I hope blue ray dies out along with the rest of DRM riddled nonsense.

---

### Post by 3rdalbum on 2009-01-07
Hmm... thanks for the discussion on film. I saw Superman on Blu-ray and it looked shocking. I might take a look at something older still - I notice they're starting to release Elvis movies on Blu-ray, so it could be a good birthday present for a family member :-)

I've seen The Wild and Ice Age 2 on Blu-ray and I agree, you can't beat the 3D animated movies for picture quality.

Sealbahch, it's lucky you didn't see the Doom9 forums - they make it look awfully hard. It's actually pretty simple:

1. Install Java from Synaptic, and the "unstripped" libav codecs if you don't already have them
2. Download "dumpHD" and "aacskeys" from the page
3. Follow the directions on the Mplayer website to compile their svn version. You need lots of -dev libraries from Synaptic, and you need to disable x264 in the ./configure script.
4. The aacskeys README file tells you what files to copy into the "dumpHD" directory, so do that.
5. Run dumpHD.
6. In the resulting STREAM directory, find the biggest m2ts file (it's your movie). Use it in your new Mplayer like so:

```
/usr/local/bin/mplayer -vc ffvc1 00002.m2ts
```

You can switch to full-screen by pressing f, play and pause by pressing spacebar, move the volume up and down by pressing 9 and 0, and change the audio delay by pressing - and +.

Compiling Mplayer is the most difficult part, but if you've compiled anything before it will be familiar enough. I think it's worth it :-)

---

### Post by SunnyRabbiera on 2009-01-07
> **3rdalbum said:**
> Hmm... thanks for the discussion on film. I saw Superman on Blu-ray and it looked shocking. I might take a look at something older still - I notice they're starting to release Elvis movies on Blu-ray, so it could be a good birthday present for a family member :-)

I've seen The Wild and Ice Age 2 on Blu-ray and I agree, you can't beat the 3D animated movies for picture quality.

Sealbahch, it's lucky you didn't see the Doom9 forums - they make it look awfully hard. It's actually pretty simple:

1. Install Java from Synaptic, and the "unstripped" libav codecs if you don't already have them
2. Download "dumpHD" and "aacskeys" from the page
3. Follow the directions on the Mplayer website to compile their svn version. You need lots of -dev libraries from Synaptic, and you need to disable x264 in the ./configure script.
4. The aacskeys README file tells you what files to copy into the "dumpHD" directory, so do that.
5. Run dumpHD.
6. In the resulting STREAM directory, find the biggest m2ts file (it's your movie). Use it in your new Mplayer like so:

```
/usr/local/bin/mplayer -vc ffvc1 00002.m2ts
```

You can switch to full-screen by pressing f, play and pause by pressing spacebar, move the volume up and down by pressing 9 and 0, and change the audio delay by pressing - and +.

Compiling Mplayer is the most difficult part, but if you've compiled anything before it will be familiar enough. I think it's worth it :-)

still why support a bad format even if it has a great picture.
I dont care about the picture personally, I care what the format does for the end user.
I personally boycott blueray until it wisens up

---

### Post by 3rdalbum on 2009-01-07
> **SunnyRabbiera said:**
> Bah blue ray might offer a better picture, but its a crap format.
Its practically impossible to use on linux, thanks to DRM loving idiots who think linux is the antichrist.
Heck not even DVD is as closed off!
I hope blue ray dies out along with the rest of DRM riddled nonsense.

Just as there are legal DVD playback solutions for Linux, there will be legal Blu-ray playback solutions for Linux. Mark my words on that.

Back in 2000, DVD was more closed off - you needed to wait a day to brute-force the CSS key.

Yes I'd rather see Blu-ray without DRM, and I'm strongly against the DRM they are using right now; but it's so easy to get around that I'd rather they kept things the way they are than create a new format with stronger DRM.

---

### Post by uberdonkey5 on 2009-01-07
I've got an AVCHD camcorder and am thinking of getting either a blue ray or HD DVD recorder. Are these compatible in any way, or will one die a death and the other take over as the format?? Which would you advise?

---

### Post by Joeb454 on 2009-01-07
HD-DVD is the dead one. I still have some lying around (hence my purchase of a BD/HD DVD combo drive).

Go for a blu-ray burner if you want to burn HD formats. But the blank discs aren't cheap :(

---

### Post by Sealbhach on 2009-01-07
Yes, Blu-Ray is regarded as having won the war against HD-DVD.


.

---

### Post by Joeb454 on 2009-01-07
> **Sealbhach said:**
> Yes, Blu-Ray is regarded as having won the war against HD-DVD.


.

Given that nobody makes HD-DVD players or publishes films on the format anymore, I'd class it as dead ;)

I have a HD-DVD player for my Xbox, it was *really* cheap when everybody started ditching HD-DVD ;)

---

### Post by waapwoop1 on 2009-01-07
> **Joeb454 said:**
> I got a Blu-Ray/HD-DVD combo drive the other day, it's brilliant :) I'm watching on [this monitor]("http://www.ebuyer.com/product/132115/show_product_reviews") and the picture is, as you say, fantastic.

I only have Hancock on Blu-Ray right now, I'm still waiting for the Dark Knight. If you really want to see good picture quality, get an animated film, as it's a digital-digital transfer the picture will be pretty much flawless.

I know the Matrix has awesome picture quality if you like those films :)


That monitor won't display Full HD

---

### Post by renzi on 2009-01-07
I am about to dive into MythBuntu with an extra system to see how that project has progressed - has anyone used that platform and scripted a more user-friendly blu-ray "backup" & playback interface?  

I have "backed-up" my blu-ray movies using anyDVD (windows) and have been able to script a seamless playback of the *.m2ts files using PowerDVD thru Meedio, but I am longing to get off all MS platforms... With all the power, control, and flexibility, I assume Linux would be the best way to *work* with DRM.

Great thread - thanks all for the info :-)

---

### Post by I-75 on 2009-01-07
> **SunnyRabbiera said:**
> Bah blue ray might offer a better picture, but its a crap format.
Its practically impossible to use on linux, thanks to DRM loving idiots who think linux is the antichrist.
Heck not even DVD is as closed off!
I hope blue ray dies out along with the rest of DRM riddled nonsense.

 I agree

DVD is a better choice. More movies available. Movies cost less than Blu-ray. Also the upconvert DVD players look great, its like getting a HD picture for a small cost. 

HH Gregg here in the Midwest is selling a Toshiba upconvert 1080 player and its also a DVD recorder for $89. You can't beat the price. 

There are many fine free programs like "Devede" which work great in converting most video formats into a burnable ISO. Lets see Blu-ray do the same. 

My opinion DVD is a universal, affordable, and very workable format and (IMO) DVD has done to video what MP3 did to audio. In addition to DVD,  I still use that old, ancient, old fashioned, relic, technology from three decades ago...the VCR.

---

### Post by KiwiNZ on 2009-01-07
I have a 65" Plasma and Blu Ray looks absolutely stunning. I dont even care that the Disc's are zoned it worth it to finally see DVD as it should be.

And as for HD TV , stunning

As for DRM , bah it does not affect my viewing at all . Its a non issue

---

### Post by yabbadabbadont on 2009-01-07
> **KiwiNZ said:**
> As for DRM , bah it does not affect my viewing at all . Its a non issue

Right up until the keys in your hardware player get revoked for some reason and then any new titles you buy will refuse to play on it...  ;)

---

### Post by KiwiNZ on 2009-01-07
> **yabbadabbadont said:**
> Right up until the keys in your hardware player get revoked for some reason and then any new titles you buy will refuse to play on it...  ;)

odds on that happening ummmmm 0.00000000000000000001% approx

---

### Post by yabbadabbadont on 2009-01-07
> **KiwiNZ said:**
> odds on that happening ummmmm 0.00000000000000000001% approx

I seem to recall reading about it already having happened...  but maybe it was the keys for a software player and not a hardware one.

---

### Post by Skripka on 2009-01-07
> **3rdalbum said:**
> Just as there are legal DVD playback solutions for Linux, there will be legal Blu-ray playback solutions for Linux. Mark my words on that.

Back in 2000, DVD was more closed off - you needed to wait a day to brute-force the CSS key.

Yes I'd rather see Blu-ray without DRM, and I'm strongly against the DRM they are using right now; but it's so easy to get around that I'd rather they kept things the way they are than create a new format with stronger DRM.

I'll believe it when I see it.

All the current ways of getting BD discs to play (on Linux) are hacks and illegal according to US law (DMCA).  And there is NO future plan to even let VLC be able to play them-as Sony wants a deathgrip on the decryption.

Hell, last I knew you cannot even fast forward through all the spam they throw on those discs, thanks to the on board DRM on the discs.

Heck the BD encryption has changed at least 4 times since it was released--what does that tell you?  My rule of thumb-is if VLC cannot play it, then it is an idiotic format.  What do ya know-RealPlayer formats are in that catagory, as are Blu-Ray.

---

### Post by Polygon on 2009-01-08
VLC 1.0.0-git can play real player formats. :o)

---

### Post by 3rdalbum on 2009-01-09
> **Skripka said:**
> I'll believe it when I see it.

All the current ways of getting BD discs to play (on Linux) are hacks and illegal according to US law (DMCA).  And there is NO future plan to even let VLC be able to play them-as Sony wants a deathgrip on the decryption.

When DVD was this young, it was the same situation.

> Hell, last I knew you cannot even fast forward through all the spam they throw on those discs, thanks to the on board DRM on the discs.

Also present on DVDs.

> Heck the BD encryption has changed at least 4 times since it was released--what does that tell you?

BD encryption has not changed. A couple of software player keys have been revoked, but updates are available and no hardware players have been affected.

In fact, I think if the hackers want to get BD decryption forever, they should find the player key for a popular hardware player. The AACS people wouldn't revoke a key for a hardware player - it would be instant disaster!

I'll wisely shut my mouth in the issue about "upscaling" and "upsampling" DVD players, except to say that I'd recommend purchasing a Blu-ray player if you have a full-HD TV or computer monitor. They're less than the price that DVD players were when they hit mainstream.

Free Blu-ray conversion and burning software for Linux will come, but be patient; remember, DVD authoring on Linux is still patchy!

---

### Post by drascus on 2009-01-09
I will never get a blue ray player. It's main purpose is to provide a platform for introducing tighter DRM onto media. it allows manufacuteres to change keys as the decryption problems are solved making it harder to decrypt. For instance the fact that you can watch your blue ray with Ubuntu is totally illegal and they would fine you and throw you in jail if they could. Why would I give money to people who would want to throw me in jail because I wanted to watch a movie I paid for? on the quality end. I mean it's just an image. your are limited to the resolution of your eye. the quality of blu-ray for sure is over hyped. It is not worth the money or the special equipment. if you are really going to watch blu-ray videos I would say find some way to do it without giving money to the producers of blu-ray. My mission of course is to get blu-ray to fail.

---

### Post by uberdonkey5 on 2009-01-09
Must admit my sentiments are the same, its about time DVD, blueray and CD producers stopped trying to artificially manipulate the market (regional disks and the like). Russia and China seemed to have managed to rip-off pretty much everything, we just have to wait :D Maybe the future is illegal downloading of blue-ray quality films because we can't play them on ubuntu.

I find the 'don't pirate DVD' adverts extremely hypocrytical. Maybe someone should make a spoof add about encryption and the fact that half the time we can't play things we pay for.

PS. I am waiting patiently for linux to catch up with HD and blue-ray. Despite lots of fiddling around with various packages, it is much much easier just to buy Pinnacle or similar for HD video editing, huff (but thankfully thats all I use windows for)

---

### Post by Skripka on 2009-01-09
> **3rdalbum said:**
> When DVD was this young, it was the same situation.



Also present on DVDs.



BD encryption has not changed. A couple of software player keys have been revoked, but updates are available and no hardware players have been affected.

In fact, I think if the hackers want to get BD decryption forever, they should find the player key for a popular hardware player. The AACS people wouldn't revoke a key for a hardware player - it would be instant disaster!

I'll wisely shut my mouth in the issue about "upscaling" and "upsampling" DVD players, except to say that I'd recommend purchasing a Blu-ray player if you have a full-HD TV or computer monitor. They're less than the price that DVD players were when they hit mainstream.

Free Blu-ray conversion and burning software for Linux will come, but be patient; remember, DVD authoring on Linux is still patchy!



My.  Where to begin.

Firstly, apart from the US federal warnings-I can skip through previews ad nauseum fine on DVD.  From what I've read-one cannot on BD.

I'd start with reading this-[which shows for starters how the keys are different for different movies.]("http://forum.doom9.org/showthread.php?t=120988")  The software player then authenticates the hardware etc etc.  These keys also vary by region, of course-and also different versions of movies have different keys.

There have been several iterations of the BD+ encryption released.  This was noted by the Doom9 devs-as they had early success getting moves decoded--[but suddenly things stopped working]("http://forum.doom9.org/showthread.php?t=123111") (Lots of interesting reading...problems start occuring page4-5) Not only have they changed BD+ encryption they have also altered the memory key block (MKB) repeatedly...as a matter of fact-currently they are using MKBv9.x.x.x that is how busy they have been.

If Sony has their way there will not be any Blu-Ray FOSS players-and they seem quite determined to get their way...they also have all the code, and laws (in the US anyway) to get what they want.  And even trying to generate such FOSS players is illegal in the US under DMCA.

---

### Post by Bachstelze on 2009-01-09
> **Skripka said:**
> My rule of thumb-is if VLC cannot play it, then it is an idiotic format.

Sorry to shatter your little dreams, but if VLC can play so few formats, it's because it is an idiotic player, designed in an idiotic way, nothing else.

And for those who say the quality of HD material is over hyped, I can only give you one recommendation: go see an eye doctor, quick.

---

### Post by Skripka on 2009-01-09
> **HymnToLife said:**
> Sorry to shatter your little dreams, but if VLC can play so few formats, it's because it is an idiotic player, designed in an idiotic way, nothing else.

Well when the only thing it won't play are RealPlayer (according to the projects features page) and BD-I like my humble opine better, you of course are free to your humble opine. ;)

---

### Post by Bachstelze on 2009-01-09
> **Skripka said:**
> Well when the only thing it won't play are RealPlayer (according to the projects features page)

ORLY?

Hints: Lagarith, SSA. Those are open source formats, too, and of course playable in any decent player (in Linux, that means MPlayer).

[http://en.wikipedia.org/wiki/Lagarith](http://en.wikipedia.org/wiki/Lagarith)
[http://en.wikipedia.org/wiki/SubStation_Alpha](http://en.wikipedia.org/wiki/SubStation_Alpha)

---

### Post by Polygon on 2009-01-10
if a player doesnt play very VERY obscure video formats that 99% of people would never find in the wild then then it doesn't automatically make something a crappy 'idiotic' player. it just means your mad that your random anime shows encoded in some obscure format can't play on vlc. for the rest of the non-anime watching world, its perfectly fine. im sure its on their 'todo' list somewhere, but since those formats are SO OBSCURE (the fact that you had to link to a wikipedia topic about them demonstrates this) that its probably a very low priority.

but lets get back on topic!

sony cant change the format too much or else older bluray players will not be able to play newer movies, which would piss off A LOT of people.

---

### Post by Bachstelze on 2009-01-10
> **Polygon said:**
> im sure its on their 'todo' list somewhere, but since those formats are SO OBSCURE (the fact that you had to link to a wikipedia topic about them demonstrates this) that its probably a very low priority.

You seem to think the fact that few people use those formats compared to others makes them obscure and not worthy of attention, so let me ask you something: do you know why so few professional applications or games are available on Linux, or why hardware support is still far from perfect? Let me tell you, because the companies who make them think exactly the same way as you do, and since Linux is used by so few people compared to Windows, they consider it SO OBSCURE that is is a very low priority for them.

Life tip: Treat others as you would like to be treated yourself. "If you want to know what a man's like, take a good look at how he treats his inferiors, not his equals." (J.K. Rowling, *Harry Potter and the Goblet of Fire*)

---

