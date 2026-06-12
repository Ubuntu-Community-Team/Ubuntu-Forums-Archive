---
title: "Media Set Server Up Advice"
date: 2010-08-10
forum: Server Platforms
---

### Post by kentish on 2010-08-10
Hello 

I was wondering if anyone could point me in the right direction for the following project. I would like stream media from my server to the front room.

Currently I have a Ubuntu Server running PS3 Media Server which works a treat but the front end is essential a file list and doesn't really tell you anything about the film or episode your about to watch. I would like to a have a new menu system on the TV which pull content from the web ie cover art, imdb info ect about the program your about to watch.

I am aware that MythTV has the ablitity to watch media files but it seems to be more focused toward recording chanels etc and I don't need that functionality. So haven't looked at that in detail. I suspect that I would need to swap from the PS3 to a miniPC.

Most of the stuff I have seen on the web is windows based there doesn't seem to be a lot for linux - maybe I am looking in the wrong place.

Any suggestions would be welcome.


Thank You

---

### Post by gobbledigook on 2010-08-10
you could run a cable for the audio and video from your server to your TV? you could then run [**_XBMC_**]("http://xbmc.org/") on the server (although for ease of use i would install the desktop and auto login, with xbmc to start in full screen mode) this is my set-up 'cause i'm poor !!

or if you are able to buy dedicated hardware like a [**_nettop_**]("http://en.wikipedia.org/wiki/Nettop") check out the [**_XBMC forums_**]("http://forum.xbmc.org") for more info on setup etc... you would just point it toward your server (ie samba share) and it turns the file list into something nice :) organise how you want, it can automatically scan and download fan-art and plot/cast descriptions for you :)

---

### Post by snek on 2010-08-10
I actually use a very old P4 3Ghz machine I had left over as my mediacenter. Coupled with quite a beefy nVidia 8800GT it plays 1080p without problems. It runs Windows 7 with the CoreAVC codec and has a DTS encoding soundcard which can upmix stereo to 5.1 DTS over a fibre cable. Why Windows 7 you might ask? For one the sound upmixing doesn't work under Linux, and Windows 7 has options to make the fonts nice & big so they are readable on a TV, whereas XP can't do that.

Once in a while I check XBMC to see if upmixing has evolved and if hardware acceleration of video decoding has improved, but with my weird hardware it isn't working too well for HD.

Now, my server is a cheap low-power AMD Athlon II (45W) system with a bunch of drives running Ubuntu Lucid and sharing all the files using Samba.

I also have a PS3 and even my Samsung LCD TV supports streaming over LAN, but it just doesn't compare to having a stand-alone HTPC. Most of the solutions for the PS3/TV do realtime transcoding, which causes pretty nasty quality loss, something I don't find acceptable.

A nettop would be a good option too I guess, I've seen some very well rated mediaplayers for around 140 euros which play everything you can throw at them over LAN. Not bad, if I didn't have old hardware laying around I would probably get one of them (also to save power, cuz a P4 + 8800GT probably uses 150W+)

---

### Post by kentish on 2010-08-10
Hi gobbledigook

Thanks for that.

The nettop look nice and compact as I already have a network point next to the TV. Using samba share would be cool as I already have that set up for the windows PC upstairs. 

I will have a read. 

Mark

---

### Post by kentish on 2010-08-10
Hi Snek 

At the moment I have ripped only TV series so not really been bothered with the quality aspect but as HDD space is become cheap it certainly looks like an option to rip my DVD's / BluRay and I would want these in the best quality.

I've found the PS3 Media Stream to cope with most things but every now and then I run in to problems and end up watching it on the PC, so the Nettop idea is starting to become every interesting.

Notice some of the nettop have a SSD drive, so that would be nice and quiet.

---

### Post by snek on 2010-08-10
You can get Compact-Flash->SATA converters on the cheap btw.. Like $20-$30.
They are not as fast as SSD's and not as reliable, but for under $50 you can have a totally silent HDD for a HTPC. Slap in a cheap mobo with onboard nvidia chipset and you're done.
Total cost should be under the price of a mediaplayer I think.

Somehow I always prefer building things myself than buying a pre-made system.
I need my freedom of installation choices, plus these mediaplayers have slow menu's.
A friend has a new Popcorn Hour, and it's kinda nice, but I really don't like the menu.

Personally I don't mind the noise too much, my Marantz amp and Wharfedale speakers overpower it quite nicely :D

---

### Post by kentish on 2010-08-10
Yeah I agree I hate the noise of the playstation on full blast or the older xbox 360 that I had, so a completely silent HTPC, would be cool.

I've had a quick look at my local computer supplier in the UK, and I can get a barebones pc for about £90 (144 USD) and that's with out looking too hard it only needs a HDD drive, which can be nice and small hence cheap.

I also agree I prefer building (and breaking) my own stuff, it feel more satisfying than buying a off the shelf product.

---

### Post by kentish on 2010-08-11
Thanks to gobbledigook for the link to the XBMC, it just what I was looking for.

Cheers

:popcorn:

---

### Post by snek on 2010-08-12
Indeed, just share your files with samba and add it as Video location in XBMC.
Works just fine.. I tried it on my HTPC as well, but it's too slow for XBMC..
Somehow Linux has problems playing HD files on that machine eventhough Windows manages (after lots of tweaking)..

---

