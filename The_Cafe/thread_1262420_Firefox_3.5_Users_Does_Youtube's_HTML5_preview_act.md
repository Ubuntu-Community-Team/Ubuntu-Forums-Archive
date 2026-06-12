---
title: "Firefox 3.5 Users: Does Youtube's HTML5 preview actually work for you?"
date: 2009-09-09
forum: The Cafe
---

### Post by purgatori on 2009-09-09
I tried it, and couldn't get any love. Only by opening the stream directly, through the mplayer plugin, could I actually view the video here: [http://www.youtube.com/html5](http://www.youtube.com/html5)

In Google Chrome, on the other hand, it worked like a charm. Isn't FF3.5 meant to have full HTML5 support? (or at least enough to run embedded video?)

---

### Post by j.bell730 on 2009-09-09
I've tried it a few times, too, it's never worked for me.

---

### Post by orlox on 2009-09-09
Nope, just a black screen...and many black screens on the side on related videos...

---

### Post by Sunflower1970 on 2009-09-09
> **orlox said:**
> Nope, just a black screen...and many black screens on the side on related videos...

Yep, me too. Tried FF 3.6alpha, 3.5.4pre, and Chrome. Nothing but a black screen.

---

### Post by Frak on 2009-09-10
Plays in Chrome on Windows, but that's it. No volume control, fullscreen control, anything.

---

### Post by MasterNetra on 2009-09-10
Black screen on Firefox 3.5.3 too.

---

### Post by murderslastcrow on 2009-09-10
Haha, that's RETARDED, to be completely politically correct about this. I'm sure it'll all be there in Karmic, but it still sounds kinda' odd that Firefox on Linux is lagging behind for some reason. Windows gets seamless HTML5 first? That just sounds wrong. We don't want HTML5 to be like Flash when it's open-source, do we?

Lol, I can't wait until this starts working. Until then, I'm going to be thoroughly bothered.

---

### Post by mcduck on 2009-09-10
> **purgatori said:**
> I tried it, and couldn't get any love. Only by opening the stream directly, through the mplayer plugin, could I actually view the video here: [http://www.youtube.com/html5](http://www.youtube.com/html5)

In Google Chrome, on the other hand, it worked like a charm. Isn't FF3.5 meant to have full HTML5 support? (or at least enough to run embedded video?)

Most likely the problem is in the video codec used by Youtube, since while different browsers now have support for the new video tag, they all support different video formats.

[LIST]
[*]Opera and Firefox only supports Ogg. That's the standard, and only free option.
[*]Chrome supports both Ogg and H.264. (Only Ogg in Chromium)
[*]Apple refuses to support Ogg.
[/LIST]

Since most videos in the normal Youtube use H.264 compression, most likely this site also uses that format.

---

### Post by MaxIBoy on 2009-09-10
Even after going into about:config and enabling HTML5, no it didn't work. Likely due to the codec issue mentioned earlier (as the file was an MP4.)

No biggie. Just right-click and select "view video." Works a treat. You don't even need a flash ripper anymore!

---

### Post by purgatori on 2009-09-10
> **mcduck said:**
> Most likely the problem is in the video codec used by Youtube, since while different browsers now have support for the new video tag, they all support different video formats.

[LIST]
[*]Opera and Firefox only supports Ogg. That's the standard, and only free option.
[*]Chrome supports both Ogg and H.264. (Only Ogg in Chromium)
[*]Apple refuses to support Ogg.
[/LIST]

Since most videos in the normal Youtube use H.264 compression, most likely this site also uses that format.


Ah, that makes sense;  thankyou for the explanation. The that I linked to is most definitely not using ogg -- it is an mp4 file, probably using H.264 as you say.

---

### Post by jrusso2 on 2009-09-10
Strange, I ran it in VLC and in the demo it shows the demo running in Safari.

I didn't know Safari even did HTML 5

---

### Post by phrostbyte on 2009-09-10
> **jrusso2 said:**
> Strange, I ran it in VLC and in the demo it shows the demo running in Safari.

I didn't know Safari even did HTML 5

Actually Safari (WebKit) has excellent standards support. The only major web browser that doesn't support HTML5 video right now in form or another is IE. :)

---

### Post by phrostbyte on 2009-09-10
Firefox 3.5 can only play videos in the Ogg Theora format. Videos on Wikimedia sites (Wikipedia) or the Ubuntu Podcast uses Ogg/HTML5. Ogg Thoera is a completely free codec in the VP* family of codecs (similar to what Flash uses already) and it supports HD video.

Example:

[http://commons.wikimedia.org/wiki/File:Apollo_15_launch.ogg](http://commons.wikimedia.org/wiki/File:Apollo_15_launch.ogg)

This should work on FF3.5 in Ubuntu

---

### Post by purgatori on 2009-09-10
> **phrostbyte said:**
> Actually Safari (WebKit) has excellent standards support. The only major web browser that doesn't support HTML5 video right now in form or another is IE. :)

Does IE even plan on supporting it, I wonder?

And I'm not impressed by Apple's refusal to support ogg, I must say. I kinda wish that Google had decided to go the ogg way with Youtube as well, since using restricted codecs goes a long way to undermining the multiplatform benefits that HTML5 was supposed to deliver.

---

### Post by aldld on 2009-09-10
It doesn't work in Firefox for me either :(

It worked fine when I tested it in Midori (webkit). All I could do, really, was watch the video. I couldn't do anything else.

---

### Post by Starlight on 2009-09-10
It doesn't work on Firefox, but it seems to work well in Chromium. It also doesn't work in Arora.

---

### Post by Ric_NYC on 2009-09-10
It doesn't work in any browser I tried (Chromium, Firefox, Arora, Opera...)

Is it a joke?

---

### Post by matthewbpt on 2009-09-10
Chromium should be able to play it if you also install the chromium-codecs-ffmpeg-nonfree, this one has the h264 as well as the ogg.

---

### Post by purgatori on 2009-09-10
I tried it in Opera 10, and was merely greeted by a message that I needed to view the page in a browser that "supports HTML5"; so no dice there :)

---

### Post by madjr on 2009-09-10
dailymotion
[http://blog.dailymotion.com/2009/05/27/watch-videowithout-flash/](http://blog.dailymotion.com/2009/05/27/watch-videowithout-flash/)

---

### Post by pwnst*r on 2009-09-10
worked in safari and chrome under windwows.

did not work in ff, IE, or Opera under windows.

didn't work with either Opera or FF under linux, but i don't have chrome installed.

---

### Post by karenyyng on 2010-03-29
[https://addons.mozilla.org/en-US/firefox/addon/83149](https://addons.mozilla.org/en-US/firefox/addon/83149) 
after installing this add-on (together with the firefox mplayer plugin installed) i can view some of the videos in youtube in html5 format.

However youtube videos seem to load more slowly with html5 and the mplayer plugin. I would not recommend using html5 to view youtube videos.

---

### Post by dreamsburnred on 2010-03-29
Youtube HTML5/Vimeo HTML5 will **ONLY** work in chrome/safari at the current time. The HTML5 video they offer is not true HTML5 Video in the sense it uses Apple's H.264 decoder. Firefox/IE/Opera can't pay for licensing and as such do not have the codec.

Chrome frame on IE will work though.

.OGG HTML5 Video is not supported on either site but is supported in Firefox/Chrome.

---

### Post by Crunchy the Headcrab on 2010-03-29
> **dreamsburnred said:**
> Youtube HTML5/Vimeo HTML5 will **ONLY** work in chrome/safari at the current time. The HTML5 video they offer is not true HTML5 Video in the sense it uses Apple's H.264 decoder. Firefox/IE/Opera can't pay for licensing and as such do not have the codec.

Chrome frame on IE will work though.

.OGG HTML5 Video is not supported on either site but is supported in Firefox/Chrome.
How does using H.264 make youtube "not true html5 video"?  I thought that was the problem with HTML5 video in the first place--that it didn't specify a standard format!

---

### Post by dreamsburnred on 2010-03-29
> **Crunchy the Headcrab said:**
> How does using H.264 make youtube "not true html5 video"?  I thought that was the problem with HTML5 video in the first place--that it didn't specify a standard format!

Ya no specified format makes it a problem.

Now CBS/New York Times are using HTML5 for iPad...with guess...H.264.

Would be nice though if sites other then mozzila supported .ogv html5 as well eventually H.264 will not be free to use :(.

---

### Post by Frak on 2010-03-29
> **dreamsburnred said:**
> Youtube HTML5/Vimeo HTML5 will **ONLY** work in chrome/safari at the current time. The HTML5 video they offer is not true HTML5 Video in the sense it uses Apple's H.264 decoder. Firefox/IE/Opera can't pay for licensing and as such do not have the codec.

Chrome frame on IE will work though.

.OGG HTML5 Video is not supported on either site but is supported in Firefox/Chrome.
1. It would be very costly for YouTube to provide ogg versions.
2. Mozilla and Opera can pay for H.264 licensing. Mozilla doesn't do it for "freedom" and Opera is cheap.
3. YouTube fully complies with the HTML5 spec. The W3C is a format-agnostic consortium. H.264 is just as valid as ogg.

---

### Post by dreamsburnred on 2010-03-29
> **Frak said:**
> 1. It would be very costly for YouTube to provide ogg versions.
2. Mozilla and Opera can pay for H.264 licensing. Mozilla doesn't do it for "freedom" and Opera is cheap.
3. YouTube fully complies with the HTML5 spec. The W3C is a format-agnostic consortium. H.264 is just as valid as ogg.

1. In storage and formatting times yes but YouTube is owned by Google...

2. A H.264 license is $5,000,000 and its almost the same for any company who wants to provide videos with the same decoder.

3. Didn't say they didn't comply.

---

### Post by Psumi on 2010-03-29
> **karenyyng said:**
> [https://addons.mozilla.org/en-US/firefox/addon/83149](https://addons.mozilla.org/en-US/firefox/addon/83149) 
after installing this add-on (together with the firefox mplayer plugin installed) i can view some of the videos in youtube in html5 format.

However youtube videos seem to load more slowly with html5 and the mplayer plugin. I would not recommend using html5 to view youtube videos.

Will it work with totem or gstreamer-based players such as parole? If no, I won't bother.

---

### Post by Tibuda on 2010-03-29
> **Psumi said:**
> Will it work with totem or gstreamer-based players such as parole? If no, I won't bother.

I suppose so. And VLC too. Why don't you try it?

---

### Post by Frak on 2010-03-29
> **dreamsburnred said:**
> 2. A H.264 license is $5,000,000 and its almost the same for any company who wants to provide videos with the same decoder.

$5,000,000 is chump change for Mozilla.

---

### Post by Psumi on 2010-03-29
> **danielrmt said:**
> I suppose so. And VLC too. Why don't you try it?

It works with totem :D

Also, it takes like... 20% less CPU!

[http://www.youtube.com/watch?v=Q-73zYoUsd4](http://www.youtube.com/watch?v=Q-73zYoUsd4) << HTML5 Markup Video

---

### Post by dreamsburnred on 2010-03-29
> **Frak said:**
> $5,000,000 is chump change for Mozilla.

It's a foundation not a corporation.

---

### Post by Frak on 2010-03-29
> **dreamsburnred said:**
> It's a foundation not a corporation.
Wrong, it's both.

---

### Post by Ian dewhurst on 2010-03-30
Edit my bad doesn't work either remember to disable flash.

---

