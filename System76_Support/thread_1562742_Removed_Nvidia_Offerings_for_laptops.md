---
title: "Removed Nvidia Offerings for laptops?"
date: 2010-08-28
forum: System76 Support
---

### Post by Caedis on 2010-08-28
I'm a big supporter of System 76 and have been saving to buy a new Pangolin or Serval laptop. I may have missed the boat, but I seem to remember that Nvidia has generally more reliable drivers for Ubuntu in general. Has this become the opposite? I'm only seeing ATi offerings from System 76's website now.

Even still, all my computers use Nvidia graphics for the sake of simplicity. I can barely keep track of Nvidia's crazy naming schemes much less ATi's. I don't know, call me a fan boy, but I just don't have the time to mess with having even more issues I have to fix when a new Ubuntu release comes out. And if I have to watch two separate graphics platforms for bugs and other idiosyncrasies I may just go back to building my own barebone laptops rather than supporting System 76. At least then I can use the platforms I'm accustomed to, Intel/AMD and Nvidia. (Yeah, I know AMD = ATi... it was a sad day for me when they bought ATi)

I guess I'm just a bit put off that I've been saving for so long only to find my preferred platform discontinued.

---

### Post by Dies on 2010-08-28
See [http://zareason.com/shop/Strata-Pro-15.html](http://zareason.com/shop/Strata-Pro-15.html) for a possible alternative

---

### Post by Caedis on 2010-08-28
> **Dies said:**
> See [http://zareason.com/shop/Strata-Pro-15.html](http://zareason.com/shop/Strata-Pro-15.html) for a possible alternative

Thanks! I'll defiantly take it under advisement. Hopefully I can get a response on the issue from a System 76 rep, or at least something about the issue from the community.

---

### Post by paulbary on 2010-08-28
I held the same opinion and all my Linux boxes over the years had Nvidia video. I recently got a Dell XPS Studio with an AMD chip and ATI card ... the video is flawless with the auto installed ATI driver on Lucid 64 ... so for what it's worth, ATI seems to be fine.

Paul

---

### Post by 3Miro on 2010-08-29
I guess people have different experience, but I have been using Nvidia for years and never had trouble under Linux. A few months ago I got an ATI video card and hell broke loose.

I used the card for some time and had to go back to NVIDIA (and spend more money). Then the NVIDIA card dies and I had to RMA it, while waiting I started using the ATI again and here is my experience with ATI and different distros.

Under Ubuntu 9.04, 10.04 and XUbuntu 10.04, the default open source ATI driver works better than Catalyst (for regular desktop use) and neither one of them can play wine games. Kubuntu 10.10 Alpha 3 cannot detect the card to install a proper driver (only some generic one), Arch Linux doesn't even have official support for Catalyst and openSusa failed boot after installing Catalyst. Basically anything KDE will not work properly.

Now I have fallen back to 32-bit XFCE Arch while the RMA process gets me a new NVIDIA. The ATI card works great under Windows, so it is not defective and the entire rest of the system works great under Linux with an NVIDIA.

I was surprised that System 76 stated to offer ATI on most of the laptops. Being System76 I am sure they have worked around the different issues, but I feel very uneasy about it. Has anyone tried wine games on an ATI Pangolin (and something that requires 3D graphics, like Sims 3, Starcraft 2, WoW ...)

---

### Post by satsujinka on 2010-08-29
I've not had any trouble whatsoever with ATI cards. though the only one I have experience with is a Mobility Radeon HD 5650. Fedora, OpenSUSE, Ubuntu all worked just fine with both the open source and Catalyst drivers and my prefered DE is KDE too. Mind you, the opensource driver doesn't support much of anything yet, due to the 5xxx series being new, but it is useable. Also while I didn't use wine, Penumbra ran just fine with the Catalyst drivers.

---

### Post by zaphod777 on 2010-08-30
I think the support for the older ATI cards are not as good but it seams the newer ones are a bit better. I couldn't get my old rasion 9800 to work I just got a black screen. But with the news that ATI is releasing open source drivers they are looking better in my book.

---

### Post by isantop on 2010-09-01
Previously, our Serval was our Nvidia system, with the GTX 285M option. We sold out of those cards, and are currently in the middle of upgrading the card to GTX 480Ms. Those should be available in a few weeks.

We're also thinking about putting out a new version of the Pangolin with Nvidia graphics. If it does, it'll be coming out sometime in October or November.

---

### Post by 3Miro on 2010-09-01
> **isantop said:**
> Previously, our Serval was our Nvidia system, with the GTX 285M option. We sold out of those cards, and are currently in the middle of upgrading the card to GTX 480Ms. Those should be available in a few weeks.

We're also thinking about putting out a new version of the Pangolin with Nvidia graphics. If it does, it'll be coming out sometime in October or November.

Great news.

FYI: currently there is a discrepancy on the system76.com Serval page. At the top, it lists ATI or NVIDIA graphics, however, only ATI is available for selection AND it is right next to an NVIDIA logo. This may cause some confusion, especially for someone who doesn't read very carefully.

---

### Post by satsujinka on 2010-09-02
> **isantop said:**
> Previously, our Serval was our Nvidia system, with the GTX 285M option. We sold out of those cards, and are currently in the middle of upgrading the card to GTX 480Ms. Those should be available in a few weeks.

We're also thinking about putting out a new version of the Pangolin with Nvidia graphics. If it does, it'll be coming out sometime in October or November.

At the very least I would prefer if you didn't go back to Nvidia on the Pangolin. But I only feel this way due to Nvidia no longer even bothering to provide an open source driver. That and with optimus they are completely abandoning linux.

A more natural upgrade to the Pangolin might be Clevo's B5125, as it's basically the same thing only with a 5470 (the 5xxx generation version of the gpu in the current Pangolin.)

---

### Post by zaphod777 on 2010-09-02
Aslong as the driver works well I don't mind if it is nVidia or ATI although it seams like ATI is putting a good effort towrds linux now that the released some open source drivers they will really help for support in the future.

I just wish that the Pangolin had USB 3.0

---

### Post by 3Miro on 2010-09-02
Who is releasing the FOSS ATI drivers? I  thought those are entirely community based. Catalyst is the driver made by ATI and it is closed source proprietary one.

The lack of FOSS Nvidia driver comes from the fact that Nvidia has always had good support for Linux and there was no need for special community effort towards that. While I applaud the ATI efforts to improve their Linux support (well AMD actually, ATI mostly ignored Linux), Nvidia definitely has a better track record.

---

### Post by zaphod777 on 2010-09-02
[http://news.slashdot.org/story/10/08/20/234248/Open-Source-2D-3D-Drivers-For-ATI-Radeon-HD-5000-Series?from=rss](http://news.slashdot.org/story/10/08/20/234248/Open-Source-2D-3D-Drivers-For-ATI-Radeon-HD-5000-Series?from=rss)

---

### Post by 3Miro on 2010-09-02
> **zaphod777 said:**
> [http://news.slashdot.org/story/10/08/20/234248/Open-Source-2D-3D-Drivers-For-ATI-Radeon-HD-5000-Series?from=rss](http://news.slashdot.org/story/10/08/20/234248/Open-Source-2D-3D-Drivers-For-ATI-Radeon-HD-5000-Series?from=rss)

Damn it, I only have Radeon 4850 .... 

A FOSS driver directly from ATI definitely changes the game.

---

### Post by zaphod777 on 2010-09-02
The Pangolin Performance has a Radeon HD 4570 so I'm not sure if I will wait for a newer model that has USB 3.0 and an ATI Radeon 5000 series or nVidia or not. Depending on how my job interview goes I may just go for it.

---

### Post by isantop on 2010-09-02
Actually, there are rumors of optimus support in Maverick.

---

### Post by IAmWhatWasDavidBowman on 2010-09-02
> **zaphod777 said:**
> The Pangolin Performance has a Radeon HD 4570 so I'm not sure if I will wait for a newer model that has USB 3.0 and an ATI Radeon 5000 series or nVidia or not.

D'oh. This is always the way. I just got my Panp7 a month ago, and while I love it, it would be that the 5xxx series drivers get released and not 4xxx.

Oh well. Weighing in on how the ATI card performs in Lucid 64:
[LIST]
[*]I have no significant problems with my video playback or with Compiz Fusion
[*]I can get 3D stuff to run smoothly
[*]WINE (no surprises here with an ATI card) does not like playing well with StarCraft II. I had to install Windows 7 to an external eSata drive to play it.
[*]I don't do a lot of gaming on my computers, so this isn't a major problem for me, but I think that Nvidia might have been a better choice for the Panp7 overall.
[*]Either way, I'm pretty much satisfied.
[/LIST]

Does anyone know if the Panp7 has a user-replaceable graphics card, or is it integrated into the mobo?

---

### Post by satsujinka on 2010-09-02
> **isantop said:**
> Actually, there are rumors of optimus support in Maverick.

Considering that X11 would have to be totally rewritten to support optimus, I would be highly skeptical of any such rumors.
That said, the kernel that Maverick will come with will support hybrid graphics (Intel/ATI and ATI/ATI combos.) The same interface can also be used to turn off an optimus nvidia gpu so that it doesn't drain power. It cannot however, switch to a nvidia gpu. If you want more information I would suggest following this blog:
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

Update: I can confirm that at the very least Kubuntu Maverick comes with vgaswitcheroo active. So Intel/ATI and ATI/ATI combos of gpus will work just fine. Though I should probably mention that vgaswitcheroo requires kernel modesetting, which means it has no support for proprietary drivers.

---

### Post by zaphod777 on 2010-09-02
> **IAmWhatWasDavidBowman said:**
> D'oh. This is always the way. I just got my Panp7 a month ago, and while I love it, it would be that the 5xxx series drivers get released and not 4xxx.

Oh well. Weighing in on how the ATI card performs in Lucid 64:
[LIST]
[*]I have no significant problems with my video playback or with Compiz Fusion
[*]I can get 3D stuff to run smoothly
[*]WINE (no surprises here with an ATI card) does not like playing well with StarCraft II. I had to install Windows 7 to an external eSata drive to play it.
[*]I don't do a lot of gaming on my computers, so this isn't a major problem for me, but I think that Nvidia might have been a better choice for the Panp7 overall.
[*]Either way, I'm pretty much satisfied.
[/LIST]

Does anyone know if the Panp7 has a user-replaceable graphics card, or is it integrated into the mobo?

which CPU did you get? I am debating the Core i7 or the Core i5.

The only heavy lifting I do is encoding videos from time to time which takes for ever on my Centrino duo.

---

### Post by IAmWhatWasDavidBowman on 2010-09-07
> **zaphod777 said:**
> which CPU did you get? I am debating the Core i7 or the Core i5.

The only heavy lifting I do is encoding videos from time to time which takes for ever on my Centrino duo.

I got the i7, and I'm glad I did. I do a lot of multi-tasking, and I can definitely notice the difference between this and my old dual-core laptop. It's very snappy! I've been encoding a lot of my DVD's for use on my external drive, and it can encode an episode of a TV show in about 10 minutes on Handbrake (1000 kbps quality / Turbo first pass, 2 passes, etc). This is a gigabyte VOB source down to about a 180 meg file. Not bad in my opinion.

My laptop is a desktop replacement, so this is another reason that I got the upgraded processor: faster memory was available on the i7. I also got the 7200 rpm drive (why have all that power and then let the hard drive be a bottleneck?). The battery life leaves something to be desired, but I knew that going in, and like I said this is a desktop replacement, so I'm never far from a power source. I don't use this outside a lot either, so I can usually get about an hour and a half of battery life when I need it. One thing that hasn't been talked a lot about in these forums is this nifty feature on the Panp7: the "quiet mode" button on the top of the keyboard. It limits the processor speed. Combine this with turning the screen brightness down and you'll get better battery life.

Overall, I'm very VERY satisfied with my Panp7. I would definitely recommend getting one. If you don't need one immediately, however, I might wait until System76 redesigns it later this year so that you can get an Nvidia card. The ATI card in this one is sufficient for my needs as I don't do much gaming, but WINE doesn't play very well with most ATI cards for 3D stuff, and this one is no exception. StarCraft II was a no-go for me, and I tried for days to get it to work. I can get to the title screen, but as soon as I try to launch it, it dies. I installed Windows on an eSATA external hard drive I've got and it plays fine on there.

If you get a Panp7 anytime soon, will you please help me with some research I've been doing on USB 2.0 speed in Lucid 64? I started a thread in these forums about it.

Cheers mate!

---

### Post by zaphod777 on 2010-09-07
> **IAmWhatWasDavidBowman said:**
> 
If you get a Panp7 anytime soon, will you please help me with some research I've been doing on USB 2.0 speed in Lucid 64? I started a thread in these forums about it.

Cheers mate!

Just when I thought I had figured I would go with the Core i5 maybe I will go with the Core i7.

I'm not sure about the USB issue I have never had that problem. What file system are you using on the USB HDD?

---

### Post by betrunkenaffe on 2010-09-07
> **zaphod777 said:**
> Just when I thought I had figured I would go with the Core i5 maybe I will go with the Core i7.

I'm not sure about the USB issue I have never had that problem. What file system are you using on the USB HDD?

Regarding the cpu power of i7, it's a quad core processor (physical). He was comparing to a dual core processor, hence, will definitely see alot of improvement.

---

### Post by isantop on 2010-09-07
Not to mention the i7 has hyperthreading, which gives each core two threads. Most older dual-core CPUs don't have that.

---

### Post by IAmWhatWasDavidBowman on 2010-09-07
@zaphod777 - It seems to be a 64-bit kernel issue with linux. File system or device doesn't seem to matter. It's something that has affected many linux users over several years, but probably not enough of a percentage for the kernel developers to have been able to nail it down. My thread is here: [http://ubuntuforums.org/showthread.php?t=1549304](http://ubuntuforums.org/showthread.php?t=1549304)

A couple other Panp7 owners I messaged on these forums said that they've seen the same issue. Don't let that deter you from buying a Panp7 though: it's not System76's fault as it's not a hardware issue (works fine under Windows), and hopefully it will get fixed eventually. It's not a deal-breaker for me as I use the eSATA connection for most of my file transfers anyway.

And yes, I'd spring for the i7. It costs a little bit more, but it's well worth it. Well, for me it was anyway.

---

### Post by jars_u on 2010-09-21
> **isantop said:**
> ...are currently in the middle of upgrading the card to GTX 480Ms.

I see the Serval's were updated in the last day or two with:

"Nvidia GeForce GTX 460M Graphics with 1.5GB GDDR5 Video Memory"  

as the standard/default option now.

Do you anticipate that either Serval's or Pangolin's will have the i5-580's as an option?

---

