---
title: "html 5 video free of flash plugin"
date: 2009-12-08
forum: The Cafe
---

### Post by sdowney717 on 2009-12-08
[http://people.opera.com/howcome/2007/video/wikipedia/octopus.html](http://people.opera.com/howcome/2007/video/wikipedia/octopus.html)

got any more sites to try?
I would like to see one with full screen

[http://arstechnica.com/open-source/news/2009/05/google-dailymotion-endorse-html-5-and-standards-based-video.ars](http://arstechnica.com/open-source/news/2009/05/google-dailymotion-endorse-html-5-and-standards-based-video.ars)

i am a little confused about this since they say it wont use flash, but when you try it it does use flash
[http://blog.dailymotion.com/2009/05/27/watch-videowithout-flash/](http://blog.dailymotion.com/2009/05/27/watch-videowithout-flash/)

this site does work, but never for IE?
[http://www.dailymotion.com/openvideodemo](http://www.dailymotion.com/openvideodemo)

---

### Post by forrestcupp on 2009-12-08
Now if we could just have an example with audio and better framerate.

I doubt if it will be any time soon that sites like YouTube or Hulu will switch.  It's cool we can finally do this, though.


Edit:  I didn't see your later examples.  Awesome.

---

### Post by sdowney717 on 2009-12-08
[http://camendesign.com/code/video_for_everybody/test.html](http://camendesign.com/code/video_for_everybody/test.html)

how is this one?

---

### Post by Ric_NYC on 2009-12-08
> **sdowney717 said:**
> [http://camendesign.com/code/video_for_everybody/test.html](http://camendesign.com/code/video_for_everybody/test.html)

how is this one?


Video and audio working perfectly (Google Chrome 4.0.249.22)



There should be an "emergency" to use the hmtl5 instead of the proprietaries Flash and Silverlight. Open standards!

---

### Post by sdowney717 on 2009-12-08
absolutely, i wonder how well it works for others who complain about flash dropping frames, slow, etc...

you could certainly talk it up with people to get it more widely known.

---

### Post by sdowney717 on 2009-12-09
[http://www.double.co.nz/video_test/](http://www.double.co.nz/video_test/)
another site with more html5 videos

---

### Post by gnomeuser on 2009-12-09
> **sdowney717 said:**
> absolutely, i wonder how well it works for others who complain about flash dropping frames, slow, etc...

you could certainly talk it up with people to get it more widely known.

I have yet to make html5's video tag work, on Chromium with ffmpeg-nonfree I just get a few seconds playing then it loops instead of going through the video.

Flash drops frames, doesn't well play in fullscreen, it eats CPU for breakfast and has a tendency towards poor bandwidth utilization making video watching a painful and intolerable experience.

So far unimpressed and predicting doom should this be the path we continue to venture down.

---

### Post by crimesaucer on 2009-12-09
> **sdowney717 said:**
> [http://camendesign.com/code/video_for_everybody/test.html](http://camendesign.com/code/video_for_everybody/test.html)

how is this one?

Video working, but no Audio for my system using ossv4 (firefox3.7a1pre built with oss instead of alsa).


I have perfect audio in flash videos and vlc videos using oss.


I also noticed all of these videos took forever to load while most flash videos load instantly and play perfectly for me (like on vimeo or youtube).

---

### Post by sdowney717 on 2009-12-09
interesting, well i have sound and they all loaded fast.
sound issue must be a configuration problem

---

### Post by koleoptero on 2009-12-09
I'm impressed by the low cpu usage! I can't wait till they make youtube with html5.

---

### Post by crimesaucer on 2009-12-09
> **sdowney717 said:**
> interesting, well i have sound and they all loaded fast.
sound issue must be a configuration problem


Well, some of us don't use the standard alsa driver because they sound like crap.


OssV4 must not be compatible yet with these embedded Firefox videos (and I wonder what else?). It works for flash videos/ads and movies player plugins like vlc and mplayer.

---

### Post by chillicampari on 2009-12-09
crimesaucer, I'm using OSSv4 also and getting audio with the vids okay.

---

### Post by sdowney717 on 2009-12-10
i am using pulse audio, just the defaults came with karmic

---

### Post by gnomeuser on 2009-12-10
> **koleoptero said:**
> I'm impressed by the low cpu usage! I can't wait till they make youtube with html5.

[Like this?](https://chrome.google.com/extensions/detail/kchoimdlcbapmcdnheaahjcdpdjdpfco)

Sorry results are.. less than impressive at least for me, I have reverted back to the horrible, yet working flash based youtube. 

An interesting approach might be to implement a Youtube site in Silverlight, I've always been very impressed with Silverlight and would love to see how it stacks up against the two other options.

---

### Post by Chame_Wizard on 2009-12-10
Only Adobe wants to stop anything having to do with FLOSS video plug-in(HTML5 tags).):P

---

### Post by Bölvaður on 2009-12-10
[http://oggtv.com/]("http://oggtv.com/")

If html5 videos flops. then the internet fails.

---

### Post by Regenweald on 2009-12-10
Win7 + Chrome here, varying between 35 and 18% cpu. Beautiful audio. Using the Big Buck Bunny clip. HTML5 is lovely.

---

### Post by BrokenKingpin on 2009-12-10
This is exciting. This could be the solution to the flash issues in Linux.

---

### Post by crimesaucer on 2009-12-11
> **chillicampari said:**
> crimesaucer, I'm using OSSv4 also and getting audio with the vids okay.

Did you build Firefox with oss instead of alsa?


This is part of the code I used to build firefox with oss:

```

	if [ "$_soundsystem" = "oss" ]; then
		# Use OSS instead of ALSA.
		sed -i 's/sydney_audio_alsa/sydney_audio_oss/' \
		       media/libsydneyaudio/src/Makefile.in || return 1
		# Get rid of ALSA stuff in the config system (requires autoconf run)
		sed -i '/alsa\//d' config/system-headers || return 1
		sed -i '/alsa\//d' js/src/config/system-headers || return 1
		sed -i '/LIB(asound/d' configure.in || return 1
	fi

```


I guess it didn't work too well?

---

### Post by Frak on 2009-12-11
> **Chame_Wizard said:**
> Only Adobe wants to stop anything having to do with FLOSS video plug-in(HTML5 tags).):P
And they'll succeed as long as IE doesn't have HTML5 <video> support.

---

### Post by chillicampari on 2009-12-11
[quote=crimesaucer]Did you build Firefox with oss instead of alsa?[/quote]
Nope, I didn't. What I did was point  apps to use either use OSS or directly to /dev/dsp in configs and most things just worked that way. Can you play .ogv files offline through a media player to see if you have audio?

---

### Post by Linuxforall on 2009-12-11
Works superb in Google Beta x64 for Linux. CPU usage is very low but unfortunately Chrome doesn't allow me to go full screen where it would be the acid test but all in all, excellent plugin with fantastic video quality.

---

### Post by Bölvaður on 2009-12-11
> **Frak said:**
> And they'll succeed as long as IE doesn't have HTML5 <video> support.

dont you remember?
google added a patch for ie so they could actually use html5.

---

### Post by Frak on 2009-12-11
> **Bölvaður said:**
> dont you remember?
google added a patch for ie so they could actually use html5.
It'll take a while for that to propogate, though.

---

### Post by toupeiro on 2009-12-11
I think the coolest thing I learned from this thread is that the common octopus is intelligent enough to unscrew a jar! :shock:

---

### Post by dragos240 on 2009-12-11
> **koleoptero said:**
> I'm impressed by the low cpu usage! I can't wait till they make youtube with html5.

They have. They have an HTML5 version. It does not work.

---

### Post by Frak on 2009-12-11
> **dragos240 said:**
> They have. They have an HTML5 version. It does not work.
It works just fine.

---

### Post by SunnyRabbiera on 2009-12-11
> **Frak said:**
> It works just fine.

On chrome i bet

---

### Post by Frak on 2009-12-11
> **SunnyRabbiera said:**
> On chrome i bet
Chrome and Safari, yeah.

---

### Post by SunnyRabbiera on 2009-12-11
> **Frak said:**
> Chrome and Safari, yeah.

Meh...

Screw it, HTML5 is going to be another broken standard that works for 3 browsers, 3 OS's and nothing much else.

---

### Post by Frak on 2009-12-11
> **SunnyRabbiera said:**
> Meh...

Screw it, HTML5 is going to be another broken standard that works for 3 browsers, 3 OS's and nothing much else.
<------- Said that even before the standard was approved.

---

### Post by crimesaucer on 2009-12-12
> **chillicampari said:**
> Nope, I didn't. What I did was point  apps to use either use OSS or directly to /dev/dsp in configs and most things just worked that way. Can you play .ogv files offline through a media player to see if you have audio?

I don't have any .ogv videos to test, I'm sure it would play just fine in a media player.


I also point my apps like VLC to oss and /dev/dsp with the gui options and I configure MPD to use oss in my /etc/mpd.conf file.

```

audio_output {
	type		"oss"
	name		"My OSS Device"
	device		"/dev/dsp"	# optional
	format		"44100:16:2"	# optional
	mixer_device	"/dev/mixer"	# optional
	mixer_control	"PCM"		# optional
}

```


And I build mplayer-mt-oss configured with the "--enable-ossaudio" switch and when played from the terminal the ao (audio output) is oss and sounds really nice except for .mkv files (.mkv movies sounds much better in VLC so I'm making that my default player now..... and I also like how VLC handles TS_VIDEO files, .img files, iso images, DVD menus, subtitles, and I can use no gui just like mplayer by using the "clvc" command instead) 


Plus I configure gstreamer-properties with custom settings of "oss4sink" and "oss4src" (which really helps a lot), and the flashplugin for Arch has support for ossv4 so no need for and extra library for that. That pretty much covers all of my apps that need sound.


Overall my sound is the BEST it's ever been with Linux, I just think that sed code removed something important from firefox (which is built as a standalone browser not needing the xulrunner package) so those videos had no sound, so I might have to try building a version without it or written differently just to test it out.



EDIT: I just tied every one of those video links using the Google Chrome beta for 64-bit Linux and there was no sound for any of them with my ossV4.

---

