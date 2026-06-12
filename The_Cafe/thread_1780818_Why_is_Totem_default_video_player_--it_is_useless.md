---
title: "Why is Totem default video player? --it is useless"
date: 2011-06-12
forum: The Cafe
---

### Post by nrundy on 2011-06-12
Why isn't another multi-media player selected for Ubuntu? There is not a single activity that Totem can successfully accomplish on my computer.

It's useless for playing DVDs. 
It lacks controls for playing video files at native resolution.
It can't play most multimedia streams I encounter online.

It's one of the most useless pieces of software I've ever encountered. there's got to be something better out there. I keep running into problems with it and because it's default it difficult to fix the problems. For example, Chrome can't play a streaming video file (er, I should say Totem can't play a streaming video file online).  Problem: I have no idea how to tell Chrome to use VLC instead of Totem. I know how to do this in Firefox and when I switch to VLC the streaming media play great. If a media player that actually worked was default I wouldn't have to deal with this kind of crap.

---

### Post by mockingbird on 2011-06-12
If there was a way to integrate VLC properly into Firefox (The mozilla-plugin-vlc is broken and has been out of development for a while, and even with Mozplugger, there are no controls), I would vote for it.

Mplayer works really well with Firefox and the Gecko-Mplayer plugin, but MPlayer has some issues with vertical sync and the videos "tear" because of this.  Another issue is that gecko-mplayer it GTK and for those who use KDE and do not wish to install the gnome libraries, it's a bit of a problem.

I agree though, Totem is complete garbage.  I wish VLC would fix the mozilla plugin and then it would be the perfect GUI-independent player.

---

### Post by Tibuda on 2011-06-12
You complain that Gecko-Mplayer uses Gtk+, but VLC uses Qt. There's no such a thing as "GUI-independent".

---

### Post by giddyup306 on 2011-06-12
I've wondered this myself. Mint 11 comes with Totem and VLC (plus all the codecs are already installed).

---

### Post by Phrea on 2011-06-12
Is it just at my computers that Totem works fine?

---

### Post by forrestcupp on 2011-06-12
Does it work after you install all of the nonfree codecs and DVD packages? VLC has that stuff built in (which is probably why it's not default in Ubuntu). If you're using other media players, you have to install the codecs.

---

### Post by akand074 on 2011-06-12
Totem in Gnome 3 is actually pretty nice. I've also found totem was able to play some video files more successfully than even VLC and SMplayer (very, very, very rare). I never use Totem, but it looks much nicer in Gnome 3 and seems to be quite a bit improved, though I'll still be sticking with VLC primary, SMplayer backup.

---

### Post by giddyup306 on 2011-06-12
> **forrestcupp said:**
> Does it work after you install all of the nonfree codecs and DVD packages? VLC has that stuff built in (which is probably why it's not default in Ubuntu). If you're using other media players, you have to install the codecs.


I have the packages from medibuntu installed.  For some reason Totem absolutely won't play .ogv files.

---

### Post by Phrea on 2011-06-12
> **forrestcupp said:**
> Does it work after you install all of the nonfree codecs and DVD packages? VLC has that stuff built in (which is probably why it's not default in Ubuntu). If you're using other media players, you have to install the codecs.

Well, I do have to say that I never watch DVD's/Bluray, I just play all sorts of other video media, and it never seems to have a problem.

---

### Post by 3Miro on 2011-06-12
If you are having trouble with Totem codecs it is because of gstreamer. Install Ubuntu-restricted-extras and enable the Medibuntu repository. You can also install additional gstreamer codecs (search for them in Synaptic).

I hardly ever find anything that Totem cannot play and it is much faster than VLC or Mplayer (second only to Parole).

Totem is default player for Gnome, hence you can find it in every Gnome distribution.

---

### Post by nrundy on 2011-06-19
> **forrestcupp said:**
> Does it work after you install all of the nonfree codecs and DVD packages? VLC has that stuff built in (which is probably why it's not default in Ubuntu). If you're using other media players, you have to install the codecs.

I;ve got all that nonfree stuff installed. I have all along. So why can't it play stuff VLC can?

---

### Post by Enigmapond on 2011-06-19
> **nrundy said:**
> I;ve got all that nonfree stuff installed. Totem is still useless.

So don't use it. Uninstall it. Make something else default. You have so many other options.

---

### Post by silex89 on 2011-06-19
> **forrestcupp said:**
> Does it work after you install all of the nonfree codecs and DVD packages? VLC has that stuff built in (which is probably why it's not default in Ubuntu). If you're using other media players, you have to install the codecs.

^This :)

If you don't install the codecs and all the backends required to play files It will be useless indeed... I love totem, I installed several codecs for it and some plug ins and extensions and it works like a dream :P


Regards :P

---

### Post by screaminj3sus on 2011-06-19
I dislike totem because it has very, very few options. For example it has no options to enable vaapi/vdpau acceleration.

---

### Post by beew on 2011-06-19
Totem is garbage for playing video files locally, but it has the best quicktime plugin for firefox. It is fast and smooth if you watch something like apple trailers. It is actually better than the quicktime plugin for Windows. For that Totem is a must.Gecko-mplayer has a quicktime plugin but it almost never works, it only works for the latest beta version (1.04, Natty only has 1.02) but the quality is horrible.

Mplayer2 is actually the best vido player, much better than normal mplayer for hd content and beats VLC hands down. Unfortunately there is only one ppa I know that has it. 
[https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")  Otherwise there is a Debian experimental package or you have to compile it yourself. They should make mplayer2 the default mplayer for Linux.

(There is one problem at the moment, namely gnome-mplayer's pausing function is kind of broken for Mplayer2 so things like streaming Divx videos normal mplayer is much smoother, but this will be fixed in the future)

I think VLC is good but also much overrated. It only use one core for video decoding so for hd content it stutters and drops frames like crazy, it also doesn't work well with VDPAU. For the codecs stuffs you can install most of them yourself anyway.  The single core defect will change  soon hopefully now that ffmpeg-mt has been merged into the main trunk.

---

### Post by Mr. Picklesworth on 2011-06-19
> **screaminj3sus said:**
> I dislike totem because it has very, very few options. For example it has no options to enable vaapi/vdpau acceleration.

That's probably because it doesn't make sense as an option. If gstreamer supports hardware acceleration, it'll use hardware acceleration. (Who in their right mind wouldn't want that?). Unfortunately, it isn't supported yet in the first place :)
It's a work in progress and there is a bug report to keep track of it here: [https://bugs.launchpad.net/gstreamer/+bug/531692](https://bugs.launchpad.net/gstreamer/+bug/531692)

Video and audio playback in GNOME is considered a session wide problem. In this way, there is a tool called gstreamer-properties whose options affect everything that uses gstreamer (which is typically everything that does multimedia in a Gnome desktop).

---

### Post by nrundy on 2011-06-19
> **silex89 said:**
> ^This :)

If you don't install the codecs and all the backends required to play files It will be useless indeed... I love totem, I installed several codecs for it and some plug ins and extensions and it works like a dream :P


Regards :P

I've installed every codec I've come across though. I don't know what else I can install. 

I'm not trying to toot VLCs horn. I'm just pointing out that it works when Totem doesn't. It would be preferable to use Totem IMHO because it is the default player that comes with ubuntu. But I always have trouble getting it to work. It's a real headache. and I don't know what else to even try.

What media player do most ubuntu users use as their default?

---

### Post by Lucradia on 2011-06-19
It isn't useless to me. In fact, it's better for me than other players like VLC, exalie, mplayer, etc.

It can play DVDs just fine, even with widescreen, and at full screen.

It can play any windows format fine the same, and Quicktime formats, etc.

It doesn't use a playlist adding feature, which the majority of users seem to want, but I dislike playlists, so it's fine for me.

I can use subtitles perfectly fine with totem as well (libdvdcss2 isn't just for menus.) Sure, I can only use the on-disk subtitles, and not use any of my own, but why should I use third-party subtitles that I have to download, or make myself, when I can use the built-in ones?

In fact, why should I use any other media for playing DVDs than the DVD Drive itself? Why download (illegally might I add) anime movies / shows? (United States is where I live, remember.)

And, the best part of totem, when added with gstreamer codecs (yes, it's gstreamer based), is that when a DVD needs to just auto-play and skip the menu (some DVDs natively do this!) totem will allow the DVD to do it.

Of course, I have to install non-free codecs separate, since totem doesn't have them built-in, but I do it so much, it's so... habitual.

Maybe that's why I don't go to chrome, because I always have to use private mode (as I want everything to clear in chrome when I close it.)

---

### Post by silex89 on 2011-06-19
> **nrundy said:**
> I've installed every codec I've come across though. I don't know what else I can install. 

I'm not trying to toot VLCs horn. I'm just pointing out that it works when Totem doesn't. It would be preferable to use Totem IMHO because it is the default player that comes with ubuntu. But I always have trouble getting it to work. It's a real headache. and I don't know what else to even try.

Oww ooww.... I got your point... :(. So sad that totem doesn't work for you... The good thing is that we have a very broad variety of different media players to test :P


Best luck :P

---

### Post by Thewhistlingwind on 2011-06-19
Works on my box./troll

No, it really does though.

---

### Post by dniMretsaM on 2011-06-19
The reason it's default is that it gives you easy access to YouTube vids. Ok, just kidding, that's not the reason. I think the reason is that VLC comes with the non-free codecs already installed. If Canonical REALLY cares about that, I think they should create a stripped-down version of VLC without them because VLC is much better IMO. It does everything.

---

### Post by Lucradia on 2011-06-19
> **dniMretsaM said:**
> The reason it's default is that it gives you easy access to YouTube vids. Ok, just kidding, that's not the reason. I think the reason is that VLC comes with the non-free codecs already installed. If Canonical REALLY cares about that, I think they should create a stripped-down version of VLC without them because VLC is much better IMO. It does everything.

Without the video editing / screen capture / loading subtitles abilities, tell me what VLC does that totem does not?

---

### Post by dniMretsaM on 2011-06-19
> **Lucradia said:**
> Without the video editing / screen capture / loading subtitles abilities, tell me what VLC does that totem does not?

First things that popped into my head: converting audio/video and extracting audio from video. I can't find those on Totem. If they're there, correct me.

EDIT: And for this guy, it also plays .ogv files.

---

### Post by beew on 2011-06-19
> **dniMretsaM said:**
>  If Canonical REALLY cares about that, I think they should create a stripped-down version of VLC without them because VLC is much better IMO. It does everything.

And the point of that would be? Why would I want a crippled version of VLC while I can easily install the full one from PPAs? 

My experience is that a lot of multi-media stuffs in the Ubuntu repo are either crippled or outdated or just plain don't work (like minitube in all versions of Ubuntu where it is in the repo) To have such garbage in the repo actually harms Ubuntu's reputation. They should instead just link to a few ppas and tell people to install at their own risk (which is zero, but they have to say that because ppas are not supported but frankly I couldn't care less for Canonical support if it can only support craps)

I am not sure what is the big deal about default apps. I use Totem only for streaming quicktime (for other things gecko-mplayer works a lot better)  So when I install Ubuntu basically I go to the Main Menu to uncheck the box for Movie Player and I don't even need to see it.  I then install VLC and Mplayer (and one of its front ends like Umplayer or Smplayer) they do a much better job than Totem.

---

### Post by dniMretsaM on 2011-06-19
Why is a "crippled" version of VLC any different than not having the non-free codecs installed by default? You can just install them (and most people do).

---

### Post by beew on 2011-06-19
> **dniMretsaM said:**
> Why is a "crippled" version of VLC any different than not having the non-free codecs installed by default? You can just install them (and most people do).

Because VLC is statically linked to its own codec libraries and you can't just install codecs from the repo and expect them to work with a castrated version of VLC. You have to essentially fork VLC to make that possible. Why bother?

---

### Post by dniMretsaM on 2011-06-19
Because VLC is the best at what it does?

---

### Post by Lucradia on 2011-06-19
> **dniMretsaM said:**
> Because VLC is the best at what it does?

As for the above transcode ability, I can do that without VLC or any player. I love ffmpeg more than VLC. In fact, I've never successfully transcoded via VLC (nor handbrake.) But FFMPEG always worked.

---

### Post by dniMretsaM on 2011-06-19
> **Lucradia said:**
> As for the above transcode ability, I can do that without VLC or any player. I love ffmpeg more than VLC. In fact, I've never successfully transcoded via VLC (nor handbrake.) But FFMPEG always worked.

That does not negate the fact that it is something VLC does that Totem doesn't. And as far as I know, FFMPEG doesn't convert video to audio. I could be wrong, I never used it too extensively.

---

### Post by Lucradia on 2011-06-19
> **dniMretsaM said:**
> That does not negate the fact that it is something VLC does that Totem doesn't. And as far as I know, FFMPEG doesn't convert video to audio. I could be wrong, I never used it too extensively.

You can convert video with audio to a video with no audio though. Also, totem plays OGVs and OGGs natively in ubuntu.

---

### Post by Zero2Nine on 2011-06-19
I'm not on Gnome now but Totem was an excellent media player in Ubuntu 10.10 for me. It all depends on the codecs I guess.

---

### Post by beew on 2011-06-19
> **dniMretsaM said:**
> Because VLC is the best at what it does?

Which is the built in codecs. Otherwise it is not the best, like I said it uses only one core. There are videos that play fine in mplayer (if you install from ppa you can get multi-threaded versions) but VLC just chokes to death. It also doesn't use VDPAU (you can kind of make it use VDPAU indirectly through VAAPI, but improvement is very marginal)

Mplayer2 is by far the best Linux video player. VLC doesn't even comes close.

---

### Post by NightwishFan on 2011-06-19
Totem is default because it uses gstreamer just like the rest of Ubuntu main. It also is "just a player". It does not baffle with extra features. Vlc is available for those who want the kitchen sink. :)

---

### Post by dniMretsaM on 2011-06-19
> **Lucradia said:**
> You can convert video with audio to a video with no audio though. Also, totem plays OGVs and OGGs natively in ubuntu.

I believe that can be done with VLC. Never done it myself though. And I know it can, I was talking about the OP's problem.

---

### Post by Bandit on 2011-06-19
> **forrestcupp said:**
> Does it work after you install all of the nonfree codecs and DVD packages? VLC has that stuff built in (which is probably why it's not default in Ubuntu). If you're using other media players, you have to install the codecs.
++


OPs response when he realises how silly his complaint was:
[http://www.youtube.com/watch?v=xoMgnJDXd3k&feature=related](http://www.youtube.com/watch?v=xoMgnJDXd3k&feature=related)

---

### Post by Lucradia on 2011-06-19
Chrome also cannot be default in Ubuntu because Chrome has flash built in, which is non-free.

---

### Post by wolfen69 on 2011-06-19
> **Phrea said:**
> Is it just at my computers that Totem works fine?

No, it works well for me also. 
[IMG]http://4.bp.blogspot.com/_mqSq8ThP9Ac/S-hqEJTVTAI/AAAAAAAABBo/kk3Vbvfm64Q/s320/shrug.jpg[/IMG]

---

### Post by koleoptero on 2011-06-19
Why is totem useless btw? It plays video doesn't it? It doesn't have to be able to do your laundry or drive the kids to school too.

---

### Post by wolfen69 on 2011-06-19
> **beew said:**
> but VLC just chokes to death.

Really? As a test of sorts, I played 30 videos at once with vlc, and there was not 1 glitch. Maybe it's your computer, not the software. ;)
> **beew said:**
> 
Mplayer2 is by far the best Linux video player. VLC doesn't even comes close.
I've been using vlc since the very beginning, and never had a single problem. I use it for TV, DVD's, and all around media stuff. Rock solid for me.

[IMG]http://2.bp.blogspot.com/_JhACXIfBklU/Sj7prY_4KJI/AAAAAAAAAJ4/aXxldOkY03k/s400/oh+no+he+didn%27t+words.jpg[/IMG]

---

### Post by beew on 2011-06-19
> **wolfen69 said:**
> Really? As a test of sorts, I played 30 videos at once with vlc, and there was not 1 glitch. 




If you a computer with a powerful single core then VLC works fine,--anything would work fine in that event,-- its shortcoming shows up if you have say dual core where each core is not  that powerful.

> Maybe it's your computer, not the software. :wink:
Of course it is my hardware, that goes without saying. It is a trivial point.

 If I have a super powerful machine then any crappy player would work . The point is that VLC fails because it is choking  up  on one core while mplayer2 handles the playback with ease, on the same modest machine that I have.

As far as hardware goes it is also well known that VLC does work well with VDPAU,-- no or very ineffective hardware decoding if you have a Nvidia card, but mplayer2 (even just mplayer) rocks.

---

### Post by wolfen69 on 2011-06-19
> **beew said:**
> If you a computer with a powerful single core then VLC works fine,--anything would work fine in that event,-- its shortcoming shows up if you have say dual core where each core is not  that powerful.

Of course it is my hardware, that goes without saying. It is a trivial point.

 If I have a super powerful machine then any crappy player would work . The point is that VLC fails because it is choking  up  on one core while mplayer2 handles the playback with ease, on the same modest machine that I have.

As far as hardware goes it is also well known that VLC does work well with VDPAU,-- no or very ineffective hardware decoding if you have a Nvidia card, but mplayer2 (even just mplayer) rocks.

I'm on my iPod touch so I can't edit your quote, but in response to "it's fine if you have a single core", well, I've been using quad cores since they first came out. I can have 15 apps open with vlc playing 18 videos. Never a problem.

---

### Post by beew on 2011-06-20
> **wolfen69 said:**
> I'm on my iPod touch so I can't edit your quote, but in response to "it's fine if you have a single core", well, I've been using quad cores since they first came out. I can have 15 apps open with vlc playing 18 videos. Never a problem.

Of course if you have quad-core and each core is powerful then VLC works fine too. My point is not that you have to have a single core, but that there has to be one powerful enough so that VLC can run on just one since it doesn't do multithreading. I have tried dual core machines where each core was not so powerful on its own, what I observed was that VLC just maxed out on one core and pretty much cloaked  to death whereas mplayer distributed the load pretty evenly.

BTW  I have tested on several machines more or less randomly (except they are all mid range machines rather than something very powerful so you can see the difference) with the same result so it is the hardware, but not due to any odd configuration. VLC is just not as good as many make it out to be. 

Its only strong point is codecs. I have encountered video clips (forget the formats) that I couldn't open in all media players even with all the restricted extra and medibuntu codecs installed but VLC plays right the way (so again it shows that it wouldn't make sense for Ubuntu to put a crippled version of VLC with its codecs stripped as default and expect users to add the codecs, it has more codecs than what is commonly available in Ubuntu)

---

### Post by NightwishFan on 2011-06-20
Vlc seems to play broken media well. With alsa for me it allows me to play 5.1 surround on stereo without some channels having extreme low volume. The point is, good or not, does it really qualify to be the default player? Think of ease of use, space concerns, consistency, etc..

---

