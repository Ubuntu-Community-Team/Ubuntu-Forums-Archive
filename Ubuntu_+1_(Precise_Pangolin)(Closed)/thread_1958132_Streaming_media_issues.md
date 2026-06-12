---
title: "Streaming media issues"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by -Robert- on 2012-04-13
I've installed the beta version of Ubuntu 12.04. Now I'm trying to complete multimedia support, but streaming media won't work as before (10.04). I'm only using the totem-mozilla plugin and I've installed ubuntu-restricted-extras, w32codecs and non-free-codecs (the usual stuff). Whenever I open an audio stream, the totem-mozilla player displays visual effects which can't be disabled and no buttons are visible. Sometimes I have to click the stream button a couple of times before it even starts playing.

Examples: [Ubuntu 10.04]("http://i40.tinypic.com/2zpi5ab.png") and [Ubuntu 12.04]("http://i39.tinypic.com/51o8l1.png")

Is this a known issue with the version of totem/totem-mozilla in 12.04? 
Here are some test streams: [http://www.england.fm/](http://www.england.fm/) (liquidfm for example) or [http://nederland.fm/](http://nederland.fm/) (WildFM or GigantFM)

I've also asked this question in the Dutch Ubuntu forums, but one person says it works, and one says it doesn't. Could someone please test this? If other people are experiencing the same problems then at least I know it is not a local problem.

---

### Post by lovinglinux on 2012-04-13
Try to disable or remove all Totem and VLC plugins and install gecko-mediaplayer. It works for me here.

---

### Post by -Robert- on 2012-04-13
gecko-mediaplayer indeed works. 
You said it works for you, did you try it with gecko-mediaplayer or with totem-mozilla?

---

### Post by lovinglinux on 2012-04-13
> **-Robert- said:**
> gecko-mediaplayer indeed works. 
You said it works for you, did you try it with gecko-mediaplayer or with totem-mozilla?

I tried with gecko. I don't have Totem or VLC installed. It also worked with mozplugger.

---

### Post by -Robert- on 2012-04-13
Thanks, lovinglinux.

I guess I'm not going to keep totem-mozilla for the moment and just use gecko. But if there are people who know a possible solution to the totem problem, I would love to hear it.

---

### Post by Frogs Hair on 2012-04-13
I have streams from various stations on the provided page working in FF Nightly and Opera . I have the Gstreamer good, bad, and ugly plug-ins  installed which are part of the ubuntu-restricted-extras package. I did have to enable scripts for both browsers.

---

### Post by -Robert- on 2012-04-13
> **Frogs Hair said:**
> I have streams from various stations on the provided page working in FF Nightly and Opera . I have the Gstreamer good, bad, and ugly plug-ins  installed which are part of the ubuntu-restricted-extras package. I did have to enable scripts for both browsers.
Thanks for the reply.

The gstreamers are installed (I installed ubuntu-restricted-extras) and scripts are enabled. Most streams on those pages work because they are in flash. Only certain streams that require a plugin don't work with totem-mozilla, or they only work after I try several times. Are you only using the totem-mozilla plugin and does it work without those visual effects, in other words can you see the control buttons (like in the 10.04 example)?

Would it be possible to post a screenshot from one of the streams I previously mentioned?

---

### Post by Frogs Hair on 2012-04-13
I did get a request for an html/decoder plug-in from Opera , but that was caused by the script blocking extension. It said that python 2.7 required an html decoder and no plug-in was found . I have not checked synaptic for such a plug-in yet. Below are the plug-ins displayed in Firefox . I using Nightly though which is 14.a1.

DivX Weplayer
iTunes Application detector
Quick Time
Flash
VLC Multimedia Pligin
Windows Media Player 10 Compatible Totem

---

### Post by Frogs Hair on 2012-04-13
Here is Wild and Liquid

---

### Post by -Robert- on 2012-04-13
You've got exactly the same problem as I do ([I marked it on your LiquidFM screenshot]("http://i43.tinypic.com/k3k7c9.jpg")). Totem doesn't show it's controls but shows some visual effects which you can't disable. Because of that the streams are probably so crappy. This is how it looks in 10.04: [http://i40.tinypic.com/2cwlfeb.png](http://i40.tinypic.com/2cwlfeb.png)

The other screenshots are using flash because they are played from the website of the radio stations themselves and not from england.fm / nederland.fm . If you click only once on the WildFM button at nederland.fm or the TranceFM button at england.fm you get the same result as with LiquidFM.

---

### Post by Frogs Hair on 2012-04-13
> **-Robert- said:**
> You've got exactly the same problem as I do ([I marked it on your LiquidFM screenshot]("http://i43.tinypic.com/k3k7c9.jpg")). Totem doesn't show it's controls but shows some visual effects which you can't disable. Because of that the streams are probably so crappy. This is how it looks in 10.04: [http://i40.tinypic.com/2cwlfeb.png](http://i40.tinypic.com/2cwlfeb.png)

The other screenshots are using flash because they are played from the website of the radio stations themselves and not from england.fm / nederland.fm . If you click only once on the WildFM button at nederland.fm or the TranceFM button at england.fm you get the same result as with LiquidFM.

I'm not familiar with what I should be seeing . I was able to listen to both stations . I seem to have been missing some of the features in the radio player . I think that may have been because of no script.

Here's Liquid @ full screen.

---

### Post by mc4man on 2012-04-13
The totem-mozilla plugin isn't working so well atm, so see what you do.
Sometimes nothing happens, otherwise it plays with no controls. Why, no idea.
(totem in 12.04 is an older version, not the 3.4, is that an issue don't know.

Even playing the stream directly in totem works sometimes, sometimes not. (if I open it in vlc or an old version of totem-xine I keep around it opens promptly
Ex,
totem [http://icecast.databoss.nl:8000/wildfm.mp3](http://icecast.databoss.nl:8000/wildfm.mp3)

Same thing on the english site.

Overall gecko-mediaplayer is the better choice atm or play directly in players

---

### Post by -Robert- on 2012-04-13
I'm going to stick with gecko-mediaplayer, at least it works normally.
The Totem browser plugin is useless for playing audio streams. Since you guys are experiencing the same problem, I know it's not a problem with my configuration.

Frogs Hair and mc4man, thanks for the replies.

---

