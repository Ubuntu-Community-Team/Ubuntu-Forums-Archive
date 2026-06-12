---
title: "Looking out for a streaming video guru"
date: 2007-02-17
forum: The Cafe
---

### Post by Bloch on 2007-02-17
Playing streaming video - in particular for the BBC site [http://news.bbc.co.uk/](http://news.bbc.co.uk/) or RTE news  [http://www.rte.ie/](http://www.rte.ie/) or Deutsche Welle, has always been hit or miss for many users. When it comes to streaming video, it seems Linus is still stuck in the bad old days of different tweaks working for different users and what works for you doesn't work for someone else.

I feel happy when I see that the clip is in flash format, because then I know firefox won't seize or I won't be left hanging for 3 minutes wondering if it will start or not.
 
I'm trying to get an overview of the situation, trying to find if there is some light at the end of the tunnel. Playing streaming media is part and parcel of the internet experience these days and at the moment honesty demands that new users be warned they might not be able to watch their favourite news clips.

I's like to know if people generally agree that streaming video is problematic, whether this is due to linux-ignorant web designers, what the story is between mplayer and realplayer - why do the mplayer designers make it realmedia-capable when this should be better handled by realplayer.

Are there issues I am not aware of? Are streaming video formats still in a state of flux, with Linux playing catch-up? Is Flash the way forward?

Is there a guru to point to a brighter future?

---

### Post by nalmeth on 2007-02-17
> **Bloch said:**
> Playing streaming video - in particular for the BBC site [http://news.bbc.co.uk/](http://news.bbc.co.uk/) or RTE news  [http://www.rte.ie/](http://www.rte.ie/) or Deutsche Welle, has always been hit or miss for many users. When it comes to streaming video, it seems Linus is still stuck in the bad old days of different tweaks working for different users and what works for you doesn't work for someone else.

I feel happy when I see that the clip is in flash format, because then I know firefox won't seize or I won't be left hanging for 3 minutes wondering if it will start or not.
 
I'm trying to get an overview of the situation, trying to find if there is some light at the end of the tunnel. Playing streaming media is part and parcel of the internet experience these days and at the moment honesty demands that new users be warned they might not be able to watch their favourite news clips.

I's like to know if people generally agree that streaming video is problematic, whether this is due to linux-ignorant web designers, what the story is between mplayer and realplayer - why do the mplayer designers make it realmedia-capable when this should be better handled by realplayer.

Are there issues I am not aware of? Are streaming video formats still in a state of flux, with Linux playing catch-up? Is Flash the way forward?

Is there a guru to point to a brighter future?
Using mozilla-mplayer and all available codecs, I only run into problems on Active X based websites.

What are you using that causes so much trouble? 

Flash is not the way forward. Open-standards should be the way forward. It's software like flash and the mess of closed-media-formats that are giving you problems with GNU/Linux.

---

### Post by warp99 on 2007-02-17
I have a problem with the mozilla-plugins with Xubuntu PPC so I use a Firefox extension called MediaPlayerConnectivity. It allows me to use any external media player:

[MediaPlayerConnectivity]("https://addons.mozilla.org/firefox/446/")

Plus you can use the plugins in conjunction with the extension in case the plugins fail or you want to change some settings of mplayer on the fly or use a different player for certain video. 

An instance for me is the apple movie trailers. Xine, for me, has better picture and sound quality than mplayer, so I set the extension to use Xine, then the mplayer plugin is not used. I also use it on my Kubuntu 64 install, but just not as much.

You can add custom extensions or change them so you can have one player for .avi, another mplayer for .wmv, another mplayer for .mov, etc. It's just the perfect tool for the shortcoming in the *.nix media plugins world. :D

---

### Post by Bloch on 2007-02-18
I will try some of the solutions the posters propose, but my reason for raising the topic here in the cafe section is to get some general light on the situation. 

I look after the ubuntu installations for two home users, and the one are we all have problems with is video clips. 
For example this thread records how I was able to get video to work, but since then the plugin has failed to work:
[http://www.ubuntuforums.org/showthread.php?t=329522&highlight=bbc](http://www.ubuntuforums.org/showthread.php?t=329522&highlight=bbc)

I do not know if such media sites as BBC and RTE are using web technologies which are linux-unfriendly, or if the problem lies rather with the quality of the open-source plugins.

The realplayer files at the test suite below do not play correctly for me, which leads me to think that the linux realplayer is buggy. 
[http://service.real.com/test/](http://service.real.com/test/)

So is there some article I can read? What direction is there in the future for video streaming compatibility? I do some work for a magazine that will have streaming video in the future - what linux-friendly solutions are there? (both open source and proprietary).

---

### Post by bwallum on 2007-03-08
This worked for me today, now watching BBC news, stay with the flow! [https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9](https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9)

---

