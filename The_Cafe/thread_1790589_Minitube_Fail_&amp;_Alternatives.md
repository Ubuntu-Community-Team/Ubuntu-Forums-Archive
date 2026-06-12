---
title: "Minitube Fail &amp; Alternatives?"
date: 2011-06-25
forum: The Cafe
---

### Post by neu5eeCh on 2011-06-25
So I tried Minitube based on a "praise it to the hilt" article in one of the Linux magazines. Fail. Minitube manages to only play, on average, 5 to 12 seconds of a video whereupon it skips straight to the next video. Wash. Rinse. Repeat. Guess I got what I paid for it.

Anyway... anyone have similar problems or know of some good alternatives? - or is Flash and the browser still the only realistic viewer?

---

### Post by lovinglinux on 2011-06-25
I develop [FlashVideoReplacer]("http://www.webgapps.org/add-ons/flashvideoreplacer"), which replaces YouTube videos on the page, so it plays with a different plugin like gecko-mediaplayer. It can also launch the video in a new tab, new window or standalone external player.

[UMPlayer]("http://www.umplayer.com/") has a YouTube plugin.

There is a new application like Minitube, but I can't find it right now. I think it was featured on OMG Ubuntu.

---

### Post by neu5eeCh on 2011-06-25
Thanks lovinglinux, I'm going to try out some of those other avenues.

---

### Post by Ric_NYC on 2011-06-25
> **VTPoet said:**
> So I tried Minitube based on a "praise it to the hilt" article in one of the Linux magazines. Fail. Minitube manages to only play, on average, 5 to 12 seconds of a video whereupon it skips straight to the next video. Wash. Rinse. Repeat. Guess I got what I paid for it.

Anyway... anyone have similar problems or know of some good alternatives? - or is Flash and the browser still the only realistic viewer?


Try this: [B]YouTube HTML5 Video Player
[/B]
[http://www.youtube.com/html5](http://www.youtube.com/html5)


Select : "Join the HTML5 Trial"

---

### Post by beew on 2011-06-25
> **VTPoet said:**
> So I tried Minitube based on a "praise it to the hilt" article in one of the Linux magazines. Fail. Minitube manages to only play, on average, 5 to 12 seconds of a video whereupon it skips straight to the next video. Wash. Rinse. Repeat. Guess I got what I paid for it.

Anyway... anyone have similar problems or know of some good alternatives? - or is Flash and the browser still the only realistic viewer?

Which version of Minitube do you use? The one in Natty's repo is 1.3, it is so old and broken that it is not funny. Version 1.3 suffered the problem you described, but it has been fixed in release 1.4 back in , oh Feb(?) and 1.4X has been available for Maverick through at least 3 PPAs since then. I can't believe that they still put 1.3 in the repo of a new Ubuntu release. 

You can get the up to date version from the webupd8 ppa. [https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")

BTW, I like both LovingLinux's flashvideoreplacer and minitube. The FVR gives you the same (actually better) experience as watching Youtube "normally" so you would be able to choose from the list, read comments etc. Minitube is really smooth though especially if you have an older machine, since it doesn't require Firefox at all and FF can use quite a bit of cpu during streaming.

---

### Post by Ric_NYC on 2011-06-25
VLC plays Youtube videos very well (Media> Open Network Stream > paste video URL or "Open location from clipboard").

---

### Post by el_koraco on 2011-06-25
There's a ppa for the latest release of Minutube, which fixed some bugs. Aa, I see beew posted it.

---

### Post by beew on 2011-06-25
> **Ric_NYC said:**
> VLC plays Youtube videos very well (Media> Open Network Stream > paste video URL or "Open location from clipboard").

That sounds rather clumsy. You start VLC, go to the youtube  url, then you copy the url, at that point Youtube would be playing already, you then put the url in VLC and close the FF tab (where the video is already playing) and play in VLC. It is not what I would call elegant.

---

### Post by Ric_NYC on 2011-06-25
> **beew said:**
> That sounds rather clumsy. You start VLC, go to the youtube  url, then you copy the url, at that point Youtube would be playing already, you then put the url in VLC and close the FF tab (where the video is already playing) and play in VLC. It is not what I would call elegant.


If you compare the quality of the video playback, it is worth it.

---

### Post by beew on 2011-06-25
> **Ric_NYC said:**
> If you compare the quality of the video playback, it is worth it.

You get excellent quality from both minitube and Lovinglinux's Flashvideoreplacer (which is actually embedded mplayer) if you choose the resolution properly.  IMO FVR  offers the most seamless experience and gives a lot of control,--it also works on a few other sitesl. Minitube is smooth and fast as it doesn't need a browser (then there is also Umplayer which has a youtube function, it is also good) All these solutions are more elegant than using VLC IMO.

---

### Post by Copper Bezel on 2011-06-25
I'm using Chrome with my YouTube account on the HTML5 trial and this launcher,

```
google-chrome --app=http://www.youtube.com
```

which for Unity or DockBarX makes YouTube its own little app. I, too, was very disappointed with Minitube, and this is a much better alternative. The HTML5 player doesn't have all of the features of the Flash player yet, but it's very nice; one perk is that the "full screen" button has been replaced with an "expand" button so that the video simply fills the window, precisely as it does in Minitube, so that it actually looks like a decent little video player app. It also seems smoother, of course.

---

### Post by lovinglinux on 2011-06-25
> **Copper Bezel said:**
> I'm using Chrome with my YouTube account on the HTML5 trial and this launcher,

```
google-chrome --app=http://www.youtube.com
```

which for Unity or DockBarX makes YouTube its own little app. I, too, was very disappointed with Minitube, and this is a much better alternative. The HTML5 player doesn't have all of the features of the Flash player yet, but it's very nice; one perk is that the "full screen" button has been replaced with an "expand" button so that the video simply fills the window, precisely as it does in Minitube, so that it actually looks like a decent little video player app. It also seems smoother, of course.

HTML5 is the future, but still uses more CPU than playing with mplayer plugin or external players.

BTW, with FlashVideoReplacer you don't need to join the html5 trial program. Just select that you prefer HTML5 in the extension preferences and it will check if any video has a HTML5 version and then redirect. This way you have the best of both worlds, HTML5 when available and mplayer playback when only flash is available.

---

### Post by beew on 2011-06-25
> **Copper Bezel said:**
>  I, too, was very disappointed with Minitube, and this is a much better alternative. The HTML5 player doesn't have all of the features of the Flash player yet, but it's very nice; one perk is that the "full screen" button has been replaced with an "expand" button so that the video simply fills the window, precisely as it does in Minitube, so that it actually looks like a decent little video player app. It also seems smoother, of course.

First minitube doesn't use flash, secondly I think you are using an old and  broken version of minitube from Ubuntu's repo like OP. I have learned not to install any media player from Ubuntu's official repo since it is almost always crippled or broken or outdated, in other words, almost always sucks.

---

### Post by neu5eeCh on 2011-06-25
> **beew said:**
> Which version of Minitube do you use? The one in Natty's repo is 1.3, it is so old and broken that it is not funny. Version 1.3 suffered the problem you described, but it has been fixed in release 1.4 back in , oh Feb(?) and 1.4X has been available for Maverick through at least 3 PPAs since then. I can't believe that they still put 1.3 in the repo of a new Ubuntu release. 

Thanks beew. I just installed the PPA and problem solved. **Note to self:** Always check for PPAs when apps don't work.


> **beew said:**
> ...Minitube is really smooth though especially if you have an older machine, since it doesn't require Firefox at all and FF can use quite a bit of cpu during streaming.

I read that Minitube successfully uses hardware acceleration in Linux... one of the reasons I wanted to try it.

---

### Post by Copper Bezel on 2011-06-25
[QUOTE=beew]First minitube doesn't use flash, secondly I think you are using an old and broken version of minitube from Ubuntu's repo like OP. I have learned not to install any media player from Ubuntu's official repo since it is almost always crippled or broken or outdated, in other words, almost always sucks.[/QUOTE]
First I didn't say anything about Minitube using Flash, secondly there are a *number* of issues that make Minitube less than useful to me, *none* of which I bothered to mention, as I'm just taking it as an assumption that Minitube isn't worth bothering with.

Let me try again for clarity. = ) This is what I was attempting to express: *YouTube's HTML5 player will make external YouTube apps irrelevant*. I am intrigued by ll's suggestion for the interim, however; I just wish it didn't depend on using Firefox.

One last Edit: VT Poet's problem I actually never experienced. If a video played, it played fine and well. My biggest irritation with Minitube was the godawful search and lack of functioning playlist support.

---

### Post by beew on 2011-06-25
> **Copper Bezel said:**
> If a video played, it played fine and well. My biggest irritation with Minitube was the godawful search and lack of functioning playlist support.

Then try umplayer.

EDITED: I agree with Lovinglinux, html5 may be the way to go in the future but at the moment it is still experimental and it still uses a lot more cpu than the flashvideoreplacer or an external player like minitube. Also, many youtube videos have html5 versions but only for lower resolutions (so you can use flash or use an external player or flashvideoreplacer to play 1080p but the html5 version is only up to 720p or 480P)

---

### Post by neu5eeCh on 2011-06-25
> **lovinglinux said:**
> I develop [FlashVideoReplacer]("http://www.webgapps.org/add-ons/flashvideoreplacer"), which replaces YouTube videos on the page, so it plays with a different plugin like gecko-mediaplayer. It can also launch the video in a new tab, new window or standalone external player.

I've already been upgraded to FF5. Does FlashVideoReplacer work with 5?

---

### Post by lovinglinux on 2011-06-25
> **VTPoet said:**
> I've already been upgraded to FF5. Does FlashVideoReplacer work with 5?

Yes, it works with FF 3.5, 3.6, 4, 5, 6 and 7.

---

### Post by ScionicSpectre on 2011-06-26
The issues you were having with Minitube are the specific ones Flavio fixed in the latest release. Unfortunately, Minitube is not updated during the released period, so you'll have to use a PPA if you're on Ubuntu. It has some nice features.

So far as hardware acceleration goes, Minitube will use whatever codecs you have on board for .mp4 videos. So probably Gstreamer for most of you (so it has as much video acceleration as any other native video player).

For people who like a stripped-down, TV-like interface with dynamic playlists like Minitube, and like to be able to download the videos they watch with a single click, Minitube will still be useful despite the HTML5 player.

Otherwise, yeah, who cares? Why bother?

---

