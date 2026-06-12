---
title: "Alternatives to mythTV"
date: 2010-01-05
forum: The Cafe
---

### Post by Cdwijs on 2010-01-05
Hi All,

I would like to be able to time-shift and record TV, but I feel MythTV is a bit overkill.

Are there alternatives?

Best regards,
Cedric

---

### Post by lovinglinux on 2010-01-05
There is XBMC, Moovida, Boxee, Freevo and others, although I'm not sure about recording capabilities .

If you intend to watch the recordings only on your machine, without streaming TV/videos and without remote control, then you could try my Firefox extension, [FoxMediaCenter]("http://fmc.isgreat.org"). It can record weekly series automatically and schedule normal recordings. The recordings become available in the Playlist Manager as soon as you start recording, so you can simulate time-shifting behavior.

I wouldn't recommend installing the current available version (3.1) from Mozilla web site, since the database will be reset on the next version (4.0), which 
I will be releasing in a couple of weeks.

 Version 4.0 will be much simpler and efficient. Unfortunately, there are still a couple bugs to be fixed in the xmltv import feature and finish DVB support. Nevertheless, it works perfectly for me.

If you want to try it before the official release, then you can get the alpha 1 version from [here]("https://sourceforge.net/projects/foxmediacenter/files/foxmediacenter-4.0.0a1.xpi/download").

Any feedback will be much appreciated.

---

### Post by laceration on 2010-01-06
When I switched over to Ubuntu a couple of years ago I intended to use Myth, but was very disappointed with it.  I ended up writing a bunch of scripts to control MPlayer.  It turned out so good that I packaged it.  I call it OSTV.  It is very lightweight but still does a lot.  It timeshifts, records, + more and is easy to install. It is by far the best TV program for Linux!  Of course I am biased, but I really believe it.

Check it out, I'll subscibe to this thread if you have any questions or need any help.

---

### Post by lovinglinux on 2010-01-07
> **laceration said:**
> When I switched over to Ubuntu a couple of years ago I intended to use Myth, but was very disappointed with it.  I ended up writing a bunch of scripts to control MPlayer.  It turned out so good that I packaged it.  I call it OSTV.  It is very lightweight but still does a lot.  It timeshifts, records, + more and is easy to install. It is by far the best TV program for Linux!  Of course I am biased, but I really believe it.

Check it out, I'll subscibe to this thread if you have any questions or need any help.

Cool. I wrote my extension for the same reason. MythTV was too powerful for me since I have a crappy analog card and don't need streaming.

---

### Post by laceration on 2010-01-07
Sorry to take this thread on a tangent, but... I am wondering, Lovinglinux if you are worried about investing so much work that is dependent on analog?  Where I live analog does not even exist anymore, I thought it was being phased out.  I am amazed that you have HBO and other premiums in your system.  They are totally locked down/encrypted for me.

---

### Post by lovinglinux on 2010-01-08
> **laceration said:**
> Sorry to take this thread on a tangent, but... I am wondering, Lovinglinux if you are worried about investing so much work that is dependent on analog?  Where I live analog does not even exist anymore, I thought it was being phased out.  I am amazed that you have HBO and other premiums in your system.  They are totally locked down/encrypted for me.

Well, I live in Brazil :( We still have some years ahead with analog TV. The digital broadcasting started last year and will only be available in major cities by 2011. I guess I will have to wait until 2013 to get it here in my town. Anyway, I have a DTH satellite subscription, because free-to-air here is pure crap.

But since I don't know much about digital broadcasting, I wonder if you are referring to the TV recorder or because you think such an extension will become obsolete?

---

### Post by laceration on 2010-01-08
> Well, I live in Brazil
That explains it.  I assumed from the screenshots with USA channels, that you were from the USA.

Digital TV is interesting.  On the one hand the picture + sound is great, especially High Definition.  On the other hand it enables the money-grubbing drm-laden propriety Media Conglomerates to have extensive control.

The way I see it, there are are 2 tiers.  There is the traditional free over the air, which includes PBS, our Public channel and the networks that have been around since the beginning of television.  Then there are the cable and satellite providers, whose content is only available from with their "magic" boxes.  These boxes decrypt the signals and sheeple pay outrageous fees for this, $100 per month is not uncommon.  What you have in Brazil, where you could just patch the signal into your computer and do whatever you want with it (this is also the circumstances that MythTV was originally developed for) is now limited to the free tier for us in the US.  That people are using Open Source Myth with ir blasters on the locked down boxes with propriety content without a hint of irony tell me there is something amiss with that project.

TV is a vast wasteland, but there are some gems sprinkled amongst the rubbish.  Free Over the Air TV in the US is where you will find most of those gems.  OTA supplemented with some bittorrent and Web Video is what OSTV does and makes for satisfactory TV viewing.

I think your extension is interesting + unique.  I am not referring to it specifically.  You might have to adapt it in the years ahead!

---

### Post by lovinglinux on 2010-01-08
> **laceration said:**
> Digital TV is interesting.  On the one hand the picture + sound is great, especially High Definition.  On the other hand it enables the money-grubbing drm-laden propriety Media Conglomerates to have extensive control.

The way I see it, there are are 2 tiers.  There is the traditional free over the air, which includes PBS, our Public channel and the networks that have been around since the beginning of television.  Then there are the cable and satellite providers, whose content is only available from with their "magic" boxes.  These boxes decrypt the signals and sheeple pay outrageous fees for this, $100 per month is not uncommon.  What you have in Brazil, where you could just patch the signal into your computer and do whatever you want with it (this is also the circumstances that MythTV was originally developed for) is now limited to the free tier for us in the US.  That people are using Open Source Myth with ir blasters on the locked down boxes with propriety content without a hint of irony tell me there is something amiss with that project.

TV is a vast wasteland, but there are some gems sprinkled amongst the rubbish.  Free Over the Air TV in the US is where you will find most of those gems.  OTA supplemented with some bittorrent and Web Video is what OSTV does and makes for satisfactory TV viewing.

So basically you can only record OTA is that correct? I presume the DRM and the HDMI implementations do not allow to record from cable/satellite boxes. I read somewhere that Sky was shipping setup boxes only with HDMI (no A/V out), in an attempt to prevent unauthorized distribution of content.

> **laceration said:**
> I think your extension is interesting + unique.  I am not referring to it specifically.  You might have to adapt it in the years ahead!

Thanks. I have created it for my personal use, but decided to share it. Since then I'm trying balance my needs with what other users might want. Not an easy task to make it feature rich and simple at the same time. In the last couple of days I have already changed a lot of things. 

Anyway, the primary feature of the extension is the EPG, but it does not require a TV card. For instance I use it to keep records of downloaded episodes from the major local network web site, which I subscribe. The channel is actually OTA, but the reception here sucks and the satellite provider does not offer it in my location. So I have to pay an extra for downloads.

The extension will still be very useful for me, even without being able to record. In fact I haven't been doing much recordings lately. There are so many re-runs of movies and series, that I don't even bother to record them.

BTW, HD content subscription packages here start at U$ 115,00 up to U$ 180,00. I'm currently paying U$40,00 for a basic package (23 digital channels, but not HD). I was paying some extra for HBO, but decided to cancel it last month, since there weren't many quality movies I haven't watched.

---

### Post by laceration on 2010-01-10
> So basically you can only record OTA is that correct? I presume the DRM and the HDMI implementations do not allow to record from cable/satellite boxes. I read somewhere that Sky was shipping setup boxes only with HDMI (no A/V out), in an attempt to prevent unauthorized distribution of content.
Yes.  Cable too, does have an unencrypted tier that roughly parallels OTA.  I, like you, do not live in a big city and get this because my OTA reception is lacking.  Even though people are paying for the boxes and the content, the idea of the whole scheme is to make it proprietary.  I'm sure the DRM is not perfectly implemented and there are workarounds.  These cable/satellite boxes consist of a tuner, (optional)hard drives for dvr functionality + encryption.  Breaking this out and patching it into a computer *again* with a tuner/video in to be recorded to a hard drive is absurd, unless you are doing something worthwhile like making the content available with bittorrent.  If you really need to buy scores of channels of reality show, infomercial crap you might as well run from their box too.

OSTV doesn't have EPG capabilities.  I am working on a solution to this.  One idea is to make it browser based.  OSTV is pretty much remote control, full screen app. It will take a lot of hacking to make a browser work in that context.

---

