---
title: "striim: Internet Radio Player for GNOME"
date: 2007-05-08
forum: The Cafe
---

### Post by Mystilleef on 2007-05-08
[screenshots]("http://striim.sf.net/screenshots.php")

[Official Website]("http://striim.sf.net/") 

[Download striim]("http://striim.sf.net/download.php")

[Ubuntu GetDeb.net]("http://www.getdeb.net/search.php?keywords=striim")

Hello,

I had tremendous success seeking the Ubuntu community's help testing out [scribes]("http://scribes.sf.net"). Your feedback and suggestions has made it a favorite application on *nix and GNOME.

I'd like to call on the community again to help test [striim]("http://striim.sf.net"). striim is an Internet radio player for GNOME. The project has languished on my computer for months. The RIAA's recent attempt to kill Internet radio motivated me to resurrect the project. You can help [save internet radio]("http://savenetradio.org/").

This is the first public alpha release. The goal of this release is for testing, feedback, suggestion and general discussions. It'll be great if someone can provide a deb to make installing it easier on Ubuntu.

Your feedback is welcome.

Thanks

Installation:

At a shell terminal type the following:

```

./configure
make
sudo make install

```Software Requirements:

```

Yelp 2.12
D-Bus 0.80 (Python bindings)
PyGTK 2.10
GNOME Python 2.12
python-musicbrainz2
gst-python 0.10.3 (Gstreamer 0.10.4 or better)
gstreamer0.10-plugins-base
gstreamer0.10-plugins-ugly

```(The website does not work well on IE. Please use a standards complaint browser like Firefox, Opera for now)

[screenshots]("http://striim.sf.net/screenshots.php")

[Official Website]("http://striim.sf.net/") 

[Download striim]("http://striim.sf.net/download.php")

---

### Post by Technoviking on 2007-05-08
Get the following error when trying to compile.

dbasinge@tardis:~/projects/striim-0.1-alpha$ make
Making all in data
make[1]: Entering directory `/home/dbasinge/projects/striim-0.1-alpha/data'
make[1]: *** No rule to make target `striim.desktop', needed by `all-am'.  Stop.
make[1]: Leaving directory `/home/dbasinge/projects/striim-0.1-alpha/data'
make: *** [all-recursive] Error 1

---

### Post by Mystilleef on 2007-05-08
> **Mike said:**
> Get the following error when trying to compile.

dbasinge@tardis:~/projects/striim-0.1-alpha$ make
Making all in data
make[1]: Entering directory `/home/dbasinge/projects/striim-0.1-alpha/data'
make[1]: *** No rule to make target `striim.desktop', needed by `all-am'.  Stop.
make[1]: Leaving directory `/home/dbasinge/projects/striim-0.1-alpha/data'
make: *** [all-recursive] Error 1

Thanks Mike. I've made a new release.

[U][download](http://striim.sf.net/download.php)

[/U]

---

### Post by Mystilleef on 2007-05-08
I've updated the dependency requirements. Apparently python-dbus 0.80 is needed and you need to have gst-plugins-gnomevfs and gst-plugins-mad installed to run striim. Also made some build fixes.

Feedback is welcome.

[download]("http://striim.sourceforge.net/download.php")

---

### Post by Orra on 2007-05-08
Hi,

You've got a nice application there. It pretty much /works/, so a lot of my feedback is about how you could achieve slightly more polish.

* Aw wow! I see that you install to my applications menu *and* register a mime type. Nice.

* I'm not quite sure what the "x min" text is for. I first though it's meant to the be length of the currently playing song. Unfortunately, it doesn't seem to work for most of the songs/stations I've been listening to: it usually displays "1min".

* I think a Close (or OK) button on the manage stations dialog would be nice.

* Now, forgive me, but I'm a bit compulsive when it comes to polish. Did you know that you can word wrap the text in the licence dialog that you get to from the about dialog? gtk.AboutDialog.set_wrap_license(True) is what you need. 

* When you click the Play button, it becomes a Pause button, and it is disabled until the radio station finishes loading. But do this: a) click the Play button; b) don't click anything else yet; c) once the Pause button's enabled, click it. The Pause button doesn't respond. I think GTK does this because the button has focus when you disable it. Maybe explicitly giving the button focus after you enable it will fix this.

* When you press the Play button, the status bar says something like "x% loading". What's weird is that it says "100% loading" for such a long time. In fact, still says this after the Pause button's been enabled.

* Being able to resize the main window would be a nice touch.


Thanks for sharing this application.

---

### Post by Mystilleef on 2007-05-09
Hello Orra,

Thanks for the feedback.

> **Orra said:**
> 
* I'm not quite sure what the "x min" text is for. I first though it's meant to the be length of the currently playing song. Unfortunately, it doesn't seem to work for most of the songs/stations I've been listening to: it usually displays "1min".

It's an approximation of how long you've been playing a radio station. It should update itself when the song playing changes. But I see  the flaw in this design. :-) I'll changed its behavior for the next release.

> **Orra said:**
> 
I think a Close (or OK) button on the manage stations dialog would be nice.

Oh, that's a window not a dialog. That is, you can have it open for as long as you wish while still fiddling with striim. You can press Esc to hide it when you're tired of it. :-)

> **Orra said:**
> 
 Now, forgive me, but I'm a bit compulsive when it comes to polish. Did you know that you can word wrap the text in the licence dialog that you get to from the about dialog? gtk.AboutDialog.set_wrap_license(True) is what you need. 


Fantastic, I had no idea. Will change this.

> **Orra said:**
> 
When you click the Play button, it becomes a Pause button, and it is disabled until the radio station finishes loading. But do this: a) click the Play button; b) don't click anything else yet; c) once the Pause button's enabled, click it. The Pause button doesn't respond. I think GTK does this because the button has focus when you disable it. Maybe explicitly giving the button focus after you enable it will fix this.

I didn't understand this well. Do you mean you can't pause a station that is already playing? I can't reproduce this problem.

> **Orra said:**
> 
When you press the Play button, the status bar says something like "x% loading". What's weird is that it says "100% loading" for such a long time. In fact, still says this after the Pause button's been enabled.

I'll try to fix this in the next release.

> **Orra said:**
> 
Being able to resize the main window would be a nice touch.


I've tested this and it leads to very ugly artifacts because of the small number of elements in the window. So  I just let GTK+ dynamically decide how best to size the window and stick with it.

I'm glad the program works for at least one person other than myself. :-) Thanks for the feedback.

Cheers

---

### Post by Mystilleef on 2007-05-09
New Update

[download]("http://striim.sf.net/download.php")

```

- Fix buffering feedback timings 
 - Fix feedback sensitivity in buttons 
 - Wrap license in about dialog properly 
 - build fixes 
 - performance optimizations

```

---

### Post by Orra on 2007-05-09
Hey again. More feedback :-).

Most importantly, you wouldn't believe some of the bad music I've heard testing striim. There should be some kind of check:

```

if artist.find("Shakira") != -1:
    raise BadMusicException

```

No? :)

* The station playing time kind of works now, but I think it could be better. I think it's weird how it starts on "1 min" instead of "0 min". Also, it only updates when the song changes. How about having a timer, and instead updating it every minute?

* This is another nitpick-compulsive-polish thing (I did warn you): when you're at the maximum volume and click the button to increase the volume, it says "increased volume" instead of "Cannot increase volume". Compare to when you try to decrease the volume from 0, where it will say "Cannot decrease volume".

* Actually, I just noticed with the decrease volume button: it doesn't work when the volume is low. Say the decrease volume button decreases the volume by n. When the volume > 0 and the volume < n, the program thinks "Oh, I can't decrease the volume by n", and so fails to decrease the volume, instead of just setting the volume to 0.

* I'll try to explain the button disable error again. Hopefully you can understand me this time :-p. Usually pause works, but not always. Say striim is playing a station. I click the pause button. Then I click the play button. The button is disabled, and then soon enabled. If I now I try to click the pause button, it does not work. But if I focus or click on any other control first, then I can click the pause button again.

Thanks again for striim--good work! :guitar:

---

### Post by Mystilleef on 2007-05-09
> **Orra said:**
> Hey again. More feedback :-).

Most importantly, you wouldn't believe some of the bad music I've heard testing striim. There should be some kind of check:

```

if artist.find("Shakira") != -1:
    raise BadMusicException

```No? :)


I'll pass on this. :-)

> **Orra said:**
> 
* The station playing time kind of works now, but I think it could be better. I think it's weird how it starts on "1 min" instead of "0 min". Also, it only updates when the song changes. How about having a timer, and instead updating it every minute?


I was thinking to update every 5 mins. The accuracy of the stream duration is not important. I don't see a good reason to poll every minute. And only programmers begin counting from 0. Ordinary users start from 1.

> **Orra said:**
> 
* This is another nitpick-compulsive-polish thing (I did warn you): when you're at the maximum volume and click the button to increase the volume, it says "increased volume" instead of "Cannot increase volume". Compare to when you try to decrease the volume from 0, where it will say "Cannot decrease volume".


Will fix.

> **Orra said:**
> 
* Actually, I just noticed with the decrease volume button: it doesn't work when the volume is low. Say the decrease volume button decreases the volume by n. When the volume > 0 and the volume < n, the program thinks "Oh, I can't decrease the volume by n", and so fails to decrease the volume, instead of just setting the volume to 0.


Seems to be related to above. Will fix too.

> **Orra said:**
> 
* I'll try to explain the button disable error again. Hopefully you can understand me this time :-p. Usually pause works, but not always. Say striim is playing a station. I click the pause button. Then I click the play button. The button is disabled, and then soon enabled. If I now I try to click the pause button, it does not work. But if I focus or click on any other control first, then I can click the pause button again.


Yeap, seems like a GTK+ issue to me. You have to move the cursor away from the button then move it back on the button for the play/pause to work. I haven't figured out a fix for it, yet. Refocusing the button doesn't fix this.

Thanks for the feedback.

Cheers

---

### Post by Mystilleef on 2007-05-12
New Release Version 0.0.4

```

[FONT=Arial][SIZE=2] - Swedish Translation by Daniel Nylander
- Spanking brand new volume system
- AMD64 fixes
- Better bad stream handling.
- Window visibility fix
- Album retrieval fixes
- Performance tweaks[/SIZE][/FONT]

```[download]("http://striim.sf.net/download.php")

[Debs at GetDeb.net]("http://www.getdeb.net/search.php?keywords=striim")

---

### Post by Zdravko on 2007-05-14
Wow! Another impressive application from the Scribes' creator!

---

### Post by mrgnash on 2007-05-15
Great program! Not every station can be added though -- BBC Radio 4, for instance, which uses a Realplayer stream.

---

### Post by Mystilleef on 2007-05-15
> **mrgnash said:**
> Great program! Not every station can be added though -- BBC Radio 4, for instance, which uses a Realplayer stream.

Thanks for the feedback. striim can only play Shoutcast streams.

---

### Post by mrgnash on 2007-05-17
Ok, that makes sense ;) I tried it out with Big Blue Radio though, and it hung indefinitely at 'getting information' :- [http://www.audiocandy.com/radio%20connectors/bigblue.pls](http://www.audiocandy.com/radio%20connectors/bigblue.pls)

---

### Post by Mystilleef on 2007-05-17
> **mrgnash said:**
> Ok, that makes sense ;) I tried it out with Big Blue Radio though, and it hung indefinitely at 'getting information' :- [http://www.audiocandy.com/radio%20connectors/bigblue.pls](http://www.audiocandy.com/radio%20connectors/bigblue.pls)

Works well for me. Are you getting any errors at the terminal?

---

### Post by ebichu on 2007-05-17
Why can't it play m3u playlists?

---

### Post by Mystilleef on 2007-05-17
> **ebichu said:**
> Why can't it play m3u playlists?

striim is an Internet radio player not a music player or mp3 player. It only plays "pls" files. And in the future "asx" files.

---

### Post by ebichu on 2007-05-17
No, you didn't understand. I mean m3u streams. For example [Kohviradio]("http://www.kohviradio.com")
That stream is m3u: [http://sys.estpak.ee:8008/kohvi.m3u](http://sys.estpak.ee:8008/kohvi.m3u)

---

### Post by Mystilleef on 2007-05-17
> **ebichu said:**
> No, you didn't understand. I mean m3u streams. For example [Kohviradio]("http://www.kohviradio.com")
That stream is m3u: [http://sys.estpak.ee:8008/kohvi.m3u](http://sys.estpak.ee:8008/kohvi.m3u)

I wasn't aware of m3u radio streams. Can you file a bug report?

Cheers

---

### Post by mrgnash on 2007-05-17
> **Mystilleef said:**
> Works well for me. Are you getting any errors at the terminal?

I figured it out, for whatever reason, that link only played their jingle -- the one from the Shoutcast page worked fine.

---

### Post by sicofante on 2007-05-18
What other streaming formats can be expected to be supported in the future? Your software is very nice, but none of my favorite radio stations uses Shoutcast.

---

### Post by Mystilleef on 2007-05-19
> **sicofante said:**
> What other streaming formats can be expected to be supported in the future? Your software is very nice, but none of my favorite radio stations uses Shoutcast.

What protocol do they support?

---

### Post by Zdravko on 2007-05-19
Hey, [http://sky.fm/](http://sky.fm/) doesn't work with this application? Why? I tried to load the pls file. But all I get is "Getting information..." :confused:

---

### Post by Mystilleef on 2007-05-19
> **Zdravko said:**
> Hey, [http://sky.fm/](http://sky.fm/) doesn't work with this application? Why? I tried to load the pls file. But all I get is "Getting information..." :confused:

Works fine for me. What striim version are you using? What station are you trying to play?

---

### Post by Zdravko on 2007-05-19
striim 0.0.4
SKY.fm - New Age - soothing sounds of new age and world music!
This is the New age *.pls file.

---

### Post by Mystilleef on 2007-05-19
> **Zdravko said:**
> striim 0.0.4
SKY.fm - New Age - soothing sounds of new age and world music!
This is the New age *.pls file.

This station works fine for me. Are you behind a firewall? Do other stations work for you at all?

---

### Post by Zdravko on 2007-05-19
I am behind a router. XMMS plays everything just fine.
BTW, I also tried World, Chill Out - both produce "Getting information..."
After a few minutes waiting for World.pls a red text appears: "Error! gstreamer encountered a general stream error"

---

### Post by Mystilleef on 2007-05-19
> **Zdravko said:**
> I am behind a router. XMMS plays everything just fine.
BTW, I also tried World, Chill Out - both produce "Getting information..."
After a few minutes waiting for World.pls a red text appears: "Error! gstreamer encountered a general stream error"

Does your router block certain outgoing ports?

---

### Post by Zdravko on 2007-05-19
Nope. Even if it did so, why does XMMS manage to play the pls files?

---

### Post by Mystilleef on 2007-05-19
> **Zdravko said:**
> Nope. Even if it did so, why does XMMS manage to play the pls files?

Perhaps because XMMS and striim use different libraries? Do you have gst-plugin-mad and gst-plugin-gnomevfs installed?

---

### Post by Zdravko on 2007-05-19
No. And there are no such packages. I searched them with Synaptic.

---

### Post by Mystilleef on 2007-05-19
> **Zdravko said:**
> No. And there are no such packages. I searched them with Synaptic.

Does synaptic have gst-plugins-ugly and gst-plugins-base? If so install them. Ubuntu/Debian tend to change the names of packages so you have to be careful with your searches. Also do you get any error messages at the terminal?

---

### Post by morneHeru on 2007-05-19
Thanks Mystilleef, it works perfectly for me. :)

---

### Post by Zdravko on 2007-05-19
> **Mystilleef said:**
> Does synaptic have gst-plugins-ugly and gst-plugins-base? If so install them. Ubuntu/Debian tend to change the names of packages so you have to be careful with your searches. Also do you get any error messages at the terminal?
Nope, no such packages are found. Terminal???

---

### Post by Mystilleef on 2007-05-19
> **Zdravko said:**
> Nope, no such packages are found. Terminal???

As I expected Ubuntu names those packages differently. Their names under Ubuntu are gstreamer0.10-plugins-base and gstreamer0.10-plugins-ugly . Make sure you have those packages installed.

Then launch gnome-terminal. And then type striim. See if any error messages are printed out. Post them here if any.

---

### Post by Zdravko on 2007-05-19
> **Mystilleef said:**
> As I expected Ubuntu names those packages differently. Their names under Ubuntu are gstreamer0.10-plugins-base and gstreamer0.10-plugins-ugly . Make sure you have those packages installed.

Then launch gnome-terminal. And then type striim. See if any error messages are printed out. Post them here if any.
gstreamer0.10-plugins-base was already installed.
gstreamer0.10-plugins-ugly - this one wasn't - so I installed it.
Then I launched striim. It worked! Amazing!
Thanks!

---

### Post by Mr. Picklesworth on 2007-05-29
Icecast (which I believe does .m3u files) would be a good one to support  some day. They have the nicest web site, anyway :)

One bugish thing: Striim's behaviour upon clicking its close button is inconsistent with other programs that use the system monitor. The close button usually just hides the window, but keeps the program alive, visible in the system monitor.


Striim is working great for me so far. Thanks for this great program! It's a nice idea to have a simple Internet radio program like this, and I'm impressed that you've kept it featureful enough to be a strong package contrary to its small size.
I have one problem: My list of internet radio stations is quite short. Would anybody be willing to share their library? (The one you have for those screenshots looks great, Mystilleef).

Also, on that note, a suggestion: It would be nice to see Striim with a big (10, 15?) and varied selection of stations, with genres and easy to read names, by default right when it is installed. This way, people new to Internet radio or just checking out Striim really quickly can get right into it easily. (Resulting, fantastically, in more people using Striim and more people supporting Internet radio!)

---

### Post by Oki on 2007-06-07
How do you make a pls file? Have tried myself, but only getting errors :-/

---

### Post by cdiem on 2007-08-02
How about drag'n'drop support for it? It would be great. 
Btw, I like the program very much by now.

---

### Post by xtknight on 2007-08-06
Striim doesn't work on Gutsy.  I get this error when I run it on Gutsy i386 or amd64:

Xlib: unexpected async reply (sequence 0x46b)!

This happens sometimes instead:

striim: Fatal IO error 104 (Connection reset by peer) on X server :0.0.

This is keeping it from being packaged in Gutsy.

---

### Post by wickwire on 2007-08-07
Great app, thanks for the time and effort! :D

---

### Post by userdce on 2008-05-01
thanx a lot for this software

:guitar:

---

### Post by grounded on 2008-12-05
@all

The [downloadlink]("http://striim.sourceforge.net/download.php") seems to be dead... (error 404)

Where can I download the newest version of Striim?

Thx for help! grounded

---

### Post by dannytatom on 2008-12-05
getdeb doesn't seem to have it, either.

---

### Post by grounded on 2008-12-06
@all

Vegeta from the german Ikhaja-Team posted me [here]("http://forum.ubuntuusers.de/topic/striim-downloadlink-project-tot/") this [link]("http://mozilla2.mirrors.tds.net/pub/linux/frugalware/frugalware-testing/source/gnome-extra/striim/?C=N;O=D").

Greetings grounded

---

