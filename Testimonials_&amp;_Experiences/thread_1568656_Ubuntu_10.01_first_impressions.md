---
title: "Ubuntu 10.01 first impressions"
date: 2010-09-05
forum: Testimonials &amp; Experiences
---

### Post by jkxx on 2010-09-05
Posting this mainly as a 'at a first glance' impression of the upcoming 10.10 and how it differs from what I saw in 10.04, along with a few bugs I've noticed. Feel free to move this to a different topic if this isn't the best place for it.

-jk

So upon seeing the beta release announcement I immediately downloaded the 64 bit ISO and installed it for a test drive. Until recently I also had an install of 10.04 on the same drive which I had used for a while since that became available in April. Here's what I found:

Install: Install went smoothly and without any problems. The only 'problem' at this stage is that some text is cut off in the new installer.

Post-install: I was greeted with an OS that boots very fast, at least as quickly as 10.04 and is ready to use nearly instantly. The default theme looks very slick with the exception of the buttons being on the left side of windows - that was a one minute fix though.

At this point I noticed 2 problems, one of which was present in the 10.04 default install as well. (See[ http://www.youtube.com/watch?v=gFN8fxycy3k]("http://www.youtube.com/watch?v=gFN8fxycy3k") for Tim of OSGUI encountering some of the same issues)

By default the compiz refresh rate is halved relative to what the refresh rate slider is set to. I set mine to 75 Hz which resulted an actual refresh of 37.5 Hz and noticeably laggy desktop performance when moving windows around and the like. The fix was to go into CompizConfig and set the refresh rate to 150 Hz which resulted in a 75 Hz actual and smooth desktop performance. The desktop does seem MUCH more responsive after this change.

The first time one opens RhythmBox and adds some songs, a pop up appears stating more codecs are needed to play some of the media. Clicking ok to install said codecs will result in an error. The codecs install just fine manually through synaptic though.

After working out the above two issues, using the desktop was pretty much problem-free from that point. I could set up my IM accounts through epiphany, mail with evolution, and make various changes to the desktop, all of which worked this time.

I did eventually burn a data cd and try a nintendo DS emulator (desmume) which is when I ran into more problems.

The cd burning itself worked and the CD had the proper data burned to it in the end. However, I had to install KDE and go into it to see the data on the disc. In Gnome I kept seeing a 'blank cd' and was asked to burn data to it each time. This was a CD-R so attempting to burn more data would've failed anyway, but I was not able to figure out how to 'reset' Gnome's disk cache so it sees the new contents of said CD.

I use desmume on windows and FreeBSD and it works well in both so I installed it and fired it up in Ubuntu. Unfortunately, both the graphics and sound output were corrupted, indicating there are problems with the related libs. I had installed other emus such as gens, fceux, and zsnes which all had similar issues on ubuntu even though they all work in other OS'es. I'll probably play with those more to try and find the culprit.

Finally, this time around I was able to redirect audio output to my headphones without much issue through pavucontrol. Ubuntu seems to have a similar audio control panel integrated into Gnome, but it unfortunately does not work. I ended up with no sound using that panel even though sound worked when adjusted with pavucontrol.

That's about it for now. Upcoming OS looks good overall, though there are a few defaults that should be changed and a few potential problems involving audio and video output, most of which I've been seeing since 10.04 or earlier. Here's hoping some of these get fixed with this new version!

As well, I hope this review helps those involved with fixing bugs at least somewhat.

---

