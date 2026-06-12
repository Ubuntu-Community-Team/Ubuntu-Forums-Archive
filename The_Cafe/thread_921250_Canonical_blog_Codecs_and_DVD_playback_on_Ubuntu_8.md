---
title: "Canonical blog: Codecs and DVD playback on Ubuntu 8.04 for all users"
date: 2008-09-16
forum: The Cafe
---

### Post by The Keeper on 2008-09-16
[http://blog.canonical.com/?p=37](http://blog.canonical.com/?p=37)
> 
For the first time we are making codecs for media playback and a DVD player, from our partners at Fluendo and Cyberlink, available through the Ubuntu store. We have had relationships with these companies for a while and to date we have offered their products to our hardware partners as pre-install options.

Now though, we are making them available to all users. It is important to us that no matter how you choose to access Ubuntu, pre-installed or as a free download, that you can have a similarly rich experience. The vast majority of our current users will have installed Ubuntu themselves. These users should also be allowed legal DVD and media playback and so we have built a way of letting them do this.

We cannot ship codecs through the distro, as they are not free to redistribute. So we have built a restricted download area that is accessible through the store. Once purchased you can find your software here which will then install in the familiar hassle-free way that Ubuntu users appreciate. A pretty cool feature is that, should you wipe out your machine you can go back to the restricted download area and access your codecs again. Enjoy

Gerry Carr - Marketing Manager, Canonical


What do you think?

The biggest question on my mind at the moment is if I buy Fluendo Complete Playback Pack for example, will it work with Ibex or Jackalope or any of the future releases? It would be excessive if people would have to buy it every six months.

And also about the Cyberlink PowerDVD requirements;
> 
This software is only compatible with systems that have working OpenGL driver support for the graphics hardware. 

Does this mean that you must have proprietary ATI/NVIDIA drivers installed for PowerDVD to work? Or do current open-source drivers provide enough OpenGL functions?

---

### Post by jeyaganesh on 2008-09-16
I think we can use that for any future version. Because most of the multimedia softwares never change for ages in linux.

---

### Post by qazwsx on 2008-09-16
So Canonical starts to support DRM (DVD playback) :(

Codecs are fine but DRM support is not.

BTW I am using libdvdcsss2 (which completely bypases DRM) (GPL)

---

### Post by karellen on 2008-09-16
> **qazwsx said:**
> So Canonical starts to support DRM (DVD playback) :(

Codecs are fine but DRM support is not.

DRM has nothing to do with supporting DVD playback

---

### Post by Lod on 2008-09-16
> **The Keeper said:**
> [http://blog.canonical.com/?p=37](http://blog.canonical.com/?p=37)
The biggest question on my mind at the moment is if I buy Fluendo Complete Playback Pack for example, will it work with Ibex or Jackalope or any of the future releases? It would be excessive if people would have to buy it every six months.I bought it to use in Fedora, I believe I tried it also on Ubuntu and it worked for me, but I'm not sure however.

---

### Post by SupaSonic on 2008-09-16
I wonder if libdvdcss2 will still be available.

---

### Post by SunnyRabbiera on 2008-09-16
> **SupaSonic said:**
> I wonder if libdvdcss2 will still be available.

well it might still be in the medibuntu repositories and the like, I doubt the paid for codec will be forced.

---

### Post by mrgnash on 2008-09-16
A lot of the codecs are 32bits only. Pfft, pass.

---

### Post by qazwsx on 2008-09-16
> **karellen said:**
> DRM has nothing to do with supporting DVD playback
Really? In theory yes but I have never bought single DRM free DVD movie.  So they are not going to apply CSS decryption?

---

### Post by samjh on 2008-09-16
> **qazwsx said:**
> Really? In theory yes but I have never bought single DRM free DVD movie.  So they are not going to apply CSS decryption?

If you don't like DRM support, you shouldn't use libdvdcss either, because it supports DRM.  It doesn't "bypass" DRM, it just uses reverse-engineered code to decrypt CSS encrypted media.

Look... if you want to enjoy DVD movies on Ubuntu, you're going to have to be able to unlock the DRM'ed content, and you can't do that without software written for the task.  You can either get that software illegally (in most developed countries) by using libdvdcss, or legally by purchasing licensed DVD playback software (what Canonical appears to be offering).

Putting your hand up to say you don't like supporting DRM, and then using DRM software (illegally, no less) just smacks of hypocrisy.  So which side of the fence are you on?

Personally, I think it's good that Canonical is giving Linux users the option to play some multimedia content which would otherwise be of dubious legal status.

---

### Post by qazwsx on 2008-09-16
> **samjh said:**
> 
Putting your hand up to say you don't like supporting DRM, and then using DRM software (illegally, no less) just smacks of hypocrisy.  So which side of the fence are you on?

yes, hypocrisy... But according to my moral it is better to use libdvdcss2 than "legal" playback. I usually respect law but DRM bypassing is better than restricted use IMHO :lolflag:

---

### Post by billgoldberg on 2008-09-16
I'll pass.

Why would I pay for something that I can get legally for free?

---

### Post by The Keeper on 2008-09-16
libdvdcss2 and w32codecs are illegal in most western countries. Dunno about others. If your country happens to be one of the few where you can use them legally, then more power to them.

---

### Post by qazwsx on 2008-09-16
> **The Keeper said:**
> libdvdcss2 and w32codecs are illegal in most western countries.

w32codecs are illegal and no one should use them in Linux system. However ffmpeg provides us lots of free and fast quality codecs (decoders+encoders).
I don't have w32codecs installed.

---

### Post by fiddledd on 2008-09-16
I don't know about the legality of DVD playback for each country, and I also don't know how to react to this.

So you will have a link from a menu that takes you to a site to purchase software for DVD playback. Something about this doesn't quite sit right with me.

Maybe it's necessary, but it feels like a change in Ubuntu to me, and I'm not sure if it's a change for the better. 

Is this a one off, or will other functionality require the purchase of third party software?

I know, maybe I'm being paranoid.:)

---

### Post by LinuxFox on 2008-09-16
I think this is great news.  I remember trying to play a DVD when I first got Ubuntu, it didn't work.  When I read about libdvdcss being illegal, I didn't bother with it.

I really like how they plan to make a hassle-free way to re-download the codecs that were purchased.  I've always been paranoid about buying downloads, since I might lose them should something happen to my computer.

It's nice Canonical is giving us a legal option. 8)

---

### Post by Canis familiaris on 2008-09-16
Will I be allowed older codecs? I dont need to buy the codecs since the patent laws are not applicable where I live.

---

### Post by mikewhatever on 2008-09-16
> **fiddledd said:**
> I don't know about the legality of DVD playback for each country, and I also don't know how to react to this.

So you will have a link from a menu that takes you to a site to purchase software for DVD playback. Something about this doesn't quite sit right with me.

Maybe it's necessary, but it feels like a change in Ubuntu to me, and I'm not sure if it's a change for the better. 

Is this a one off, or will other functionality require the purchase of third party software?

I know, maybe I'm being paranoid.:)

Paranoid indeed.
First, lots of people have been asking for this. 
Second, you aren't forced to buy it.

---

### Post by fiddledd on 2008-09-16
> **mikewhatever said:**
> Paranoid indeed.
First, lots of people have been asking for this. 
Second, you aren't forced to buy it.

Yeah, well I'm still going to wear my tin foil hat, just in case.

---

### Post by tikal26 on 2008-09-16
This is good for the widespread adoption of (k)ubuntu. Many people in the US are reluctant to use it since there is no easy qaty to get codecs and dvd playback. I know that ubnutu has a worldwide appeal and I tihnk this is good for some coutries if you live where is not illegal then it doe snot matter to you

---

### Post by BigSilly on 2008-09-16
Not sure how this could be a good thing for Linux adoption in general really. Aren't people going to be confused with the idea of paying for something as obscure as a *codec*? I mean, paying for a DVD suite or whatever would be good. Many do that on Windows anyway. But the idea of codecs could prove confusing for regular users.

Plus, I think I'll wear my tin foil hat too like fiddledd just in case. Not sure what I think of this whole endeavour just yet...

---

### Post by VitaLiNux on 2008-09-16
> **samjh said:**
> If you don't like DRM support, you shouldn't use libdvdcss either, because it supports DRM.  It doesn't "bypass" DRM, it just uses reverse-engineered code to decrypt CSS encrypted media.

Look... if you want to enjoy DVD movies on Ubuntu, you're going to have to be able to unlock the DRM'ed content, and you can't do that without software written for the task.  You can either get that software illegally (in most developed countries) by using libdvdcss, or legally by purchasing licensed DVD playback software (what Canonical appears to be offering).

Putting your hand up to say you don't like supporting DRM, and then using DRM software (illegally, no less) just smacks of hypocrisy.  So which side of the fence are you on?



Personally, I think it's good that Canonical is giving Linux users the option to play some multimedia content which would otherwise be of dubious legal status.
+1 Agree.

---

### Post by Chame_Wizard on 2008-09-16
just use the new VLC

---

### Post by eldragon on 2008-09-16
this seems like one step closer to having legal bluray/hddvd playback on linux, something im not quite sure exists due to the complexity of the copy protection schemes in place.

i feel quite torn in half by this one. i dont know if i want linux to start siding with copyright holders as long as they enforce such restrictive schemes. but on the other hand, it'd be nice to have an easy, legal and free way to do this. 

i still dont fully understand why we need to 'buy' the codecs though.

i'll keep on with watching the dvds on my player for now :D

---

### Post by david_lynch on 2008-09-16
> **The Keeper said:**
> [http://blog.canonical.com/?p=37](http://blog.canonical.com/?p=37)
Does this mean that you must have proprietary ATI/NVIDIA drivers installed for PowerDVD to work? Or do current open-source drivers provide enough OpenGL functions?
You don't need any specific proprietary driver. Linux has had open source OpenGL support for some years. My current laptop and home desktop have intel graphics, and the OpenGL support is included with the standard kernel and xorg drivers. Of course, if you want ATI or Nvidia, then you'll need an appropriate driver for OpenGL support. Some ATI cards work well with the OSS radeon driver, some need the proprietary drivers. For the most part, Nvidia cards need the proprietary nvidia drivers to work well, but there is progress being made on the OSS noveau drivers for nvidia cards.

---

### Post by swoll1980 on 2008-09-16
If you buy a dvd drive the right to use dvd codecs comes with it. I don't see how downloading the codec from the repos is an issue. I allready have cyberlink, and nero for Windows it came with my LG DVD drive. I see no way it would be illegal to use the codecs from the repos.

---

### Post by LaRoza on 2008-09-16
> **BigSilly said:**
> Not sure how this could be a good thing for Linux adoption in general really. Aren't people going to be confused with the idea of paying for something as obscure as a *codec*? I mean, paying for a DVD suite or whatever would be good. Many do that on Windows anyway. But the idea of codecs could prove confusing for regular users.

Plus, I think I'll wear my tin foil hat too like fiddledd just in case. Not sure what I think of this whole endeavour just yet...

Windows has the exact same things to contend with. (Try installing Windows XP, it supports much less than Ubuntu does, and they both can't play DVD's)

---

### Post by swoll1980 on 2008-09-16
> **eldragon said:**
> this seems like one step closer to having legal bluray/hddvd playback on linux, something im not quite sure exists due to the complexity of the copy protection schemes in place.


nero linux works with bluray if I'm not mistaken

---

### Post by Chame_Wizard on 2008-09-16
i hate patents ******,it's crazy.

BSD/GNULinux FTW:guitar:

---

### Post by LaRoza on 2008-09-16
> **swoll1980 said:**
> If you buy a dvd drive the right to use dvd codecs comes with it. I don't see how downloading the codec from the repos is an issue. I allready have cyberlink, and nero for Windows it came with my LG DVD drive. I see no way it would be illegal to use the codecs from the repos.

The issue, if one truly exists, is that the creation of the codecs violated certain "laws" which basically stated "Do not even try to decode things".

This is extremely stupid as if it is coded, it shouldn't be easily decoded (the only thing protecting DVD's is the law, not the encryption. 6th graders cheating on tests have been encryption systems.)

Since the law is the only thing that is an issue, what is the need for encryption? It is not like it is stopping anything and it gets in the way of people who legally obtain the media.

---

### Post by CarpKing on 2008-09-16
> **swoll1980 said:**
> If you buy a dvd drive the right to use dvd codecs comes with it. I don't see how downloading the codec from the repos is an issue. I allready have cyberlink, and nero for Windows it came with my LG DVD drive. I see no way it would be illegal to use the codecs from the repos.

That's a good point.  My DVD drive came with Cyberlink and Nero for Windows.  The same is likely true for most people who build their computers, and I'm sure just about every pre-built computer comes with some way to play DVD's out of the box, included in the price.  Users shouldn't be expected to pay for this functionality when they've already bought it.  

This doesn't really affect me, as I've used VLC for DVD playback since I first got my computer despite the other options available on Windows.  I'm just worried that new users, will be conned into paying unnecessarily or will think "I didn't have to pay for that on Windows!" and give up on Ubuntu.

---

### Post by Daveski on 2008-09-16
> **LaRoza said:**
> Since the law is the only thing that is an issue, what is the need for encryption? It is not like it is stopping anything and it gets in the way of people who legally obtain the media.

Indeed, and this is becoming more and more of an issue. I dislike the idea of using 'technology' to enforce the law (however stupid that law is). All DRM in my opinion has this social flaw, and because the law is being enforced without any intelligence, any form of 'fair use' is immediately prohibited.

As mentioned this approach only inconveniences those who are trying to do the right thing - those who are not (say pirates) are not bothered because as soon as someone breaks the technology (inevitable) they can bypass it and happily get on with their blatant law-breaking.

Companies are now routinely punishing their customers with very little impact on preventing unlawful use of their products or services.

Back on topic though, I would have thought that by purchasing a perfectly legal DVD, you should have already obtained the 'right' (or license) to play back from that media, even if it uses an encryption system. The 'license' should be bought as part of the media, but it is not, presumably in a misguided attempt to control which companies can produce equipment to decode and play that media. The reason for this is to stop a company producing equipment to facilitate the illegal copying of licensable media.

IT IS THE ACT OF COPYING WHICH IS ILLEGAL! Not the production of a copying system. When will we learn?  The thinking seems to be that if the act of copying protected material is illegal, then so should be owning equipment capable of doing so. Twisted.

---

### Post by 71CH on 2008-09-16
I don't get it.  Why do we have to purchase codecs?  Aren't these readily available for free?

---

### Post by LaRoza on 2008-09-16
> **71CH said:**
> I don't get it.  Why do we have to purchase codecs?  Aren't these readily available for free?

Why? Because they charge for them.

The codecs that are free where made by a person without any sort of permission. The ones sold are properly licensed and they charge for them. It is kind of like going into a restaurant and finding the food is reasonably priced, but you have to pay to use their forks and you can't bring your own.

(food == media, non-free fork == non-free codecs, your fork == free codec)

---

### Post by swoll1980 on 2008-09-16
> **CarpKing said:**
>   

This doesn't really affect me, as I've used VLC for DVD playback since I first got my computer despite the other options available on Windows.  I'm just worried that new users, will be conned into paying unnecessarily or will think "I didn't have to pay for that on Windows!" and give up on Ubuntu.

+1 I'm not paying for the codecs twice. I'm using them without remorse, and it will stay that way

---

### Post by Daveski on 2008-09-16
> **71CH said:**
> I don't get it.  Why do we have to purchase codecs?  Aren't these readily available for free?

Free (gratis)  - yes, legal - well maybe not.

VLC FAQ mentions the library it uses to decode DVDs, and that it might not be legal to use this in your country:

> 3.3.	
Is libdvdcss legal?

The use and distribution of the libdvdcss library is controversial in a few countries such as the United States because of a law called the DMCA (Digital Millennium Copyright Act). If you are unsure about the legality of using and distributing this library in your country, please consult your lawyer.

---

### Post by fballem on 2008-09-16
In order to be able to play media, including DVDs, do I need to purchase both the Fluendo Complete Playback Pack and the CyberLink PowerDVD Linux packages?

I think it's a great idea, I just want to make sure that I pickup the right things.

Thanks,

---

### Post by LaRoza on 2008-09-16
> **swoll1980 said:**
> +1 I'm not paying for the codecs twice. I'm using them without remorse, and it will stay that way

+1 The only illegal thing we can do is make them, not use them. We aren't making them.

---

### Post by Daveski on 2008-09-16
> **LaRoza said:**
> +1 The only illegal thing we can do is make them, not use them. We aren't making them.

Distribution might be illegal though, so once you have downloaded it, don't give it to a friend. Presumably this is an issue for Canonical though. This is just the kind of thing that keeps lawyers in business.

---

### Post by Vadi on 2008-09-17
I think this is a great thing.

---

### Post by cor2y on 2008-09-18
Where this could possibly be helpful is with the playback of dvds that are not region 1 coded.
I recently picked up a copy of blade trinity secondhand from a swap meet and i couldn't get the dvd to play fully , midway through the movie it totem would fly up with an error saying the disc was encrypted, tried both mplayer and vlc as well, turns out the disc is not a region 1 disc and apparently theres more disc errors/ new copy protection on dvds outside of region 1, something libdvdcss2 does not handle correctly, while my dvd player (set to region free) and windows xp in virtualbox using cyberlink dvd player were able to play the disc with no problem.
So here i am guessing Cyberlink's program would come in handy at reading a disc like that.

Anyone buy the fluendo gstreamer codecs yet?
What are the limits of usage on that?
For example what about updates when gstreamer gets updated does fluendo give you free lifetime updates?
What about OS/distro usage , am i limited to just say ubuntu 8.04 or can i use it on say Debian Etch if i decide Ubuntu is not for me? 
Obviously the section of the fluendo codec pack i am looking at is the windows media part, how much better is it than the gstreamer opensource decoders for windows media encoded files?

---

### Post by billgoldberg on 2008-09-18
> **The Keeper said:**
> libdvdcss2 and w32codecs are illegal in most western countries. Dunno about others. If your country happens to be one of the few where you can use them legally, then more power to them.

I presume you only need to buy the license for these things once in a lifetime.

Thus anyone who has ever owned a Windows license or PC that came with Windows pre-installed should be able to legally install them.

No?

---

### Post by The Keeper on 2008-09-18
AFAIK only if you've owned a retail version of Windows that came with those codecs. If you've bought OEM version, the license is only limited to the computer it was bought for/with.

On the other hand I'm sure licenses/EULAs doesn't cover using windows codecs on non-Microsoft OS.

---

### Post by BigSilly on 2008-09-18
What kind of price are we talking, and what's the package of codecs you get?

---

### Post by The Keeper on 2008-09-18
Both details can be read from the Ubuntu store.
[https://shop.canonical.com/index.php?cPath=19](https://shop.canonical.com/index.php?cPath=19)

---

### Post by hanzomon4 on 2008-09-18
one would think that buying a DVD drive covered the cost of the codec to view DVDs. The whole system is broken. Software kinda looks like one big con.....

---

### Post by The Keeper on 2008-09-18
Indeed, if you buy a drive with bundled DVD-playback software which happens to be Windows-only, I can't but wonder why it cannot be exchanged for a linux version free-of-charge. Obviously you would then lose the windows version, but at least linux users would be happy with it.

---

### Post by Vadi on 2008-09-18
I hope the media picks this up.

---

