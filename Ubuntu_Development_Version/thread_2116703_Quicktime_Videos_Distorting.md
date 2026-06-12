---
title: "Quicktime Videos Distorting"
date: 2013-02-16
forum: Ubuntu Development Version
---

### Post by craig10x on 2013-02-16
I was just wondering if others testing ubuntu 13.04 (with unity) are experiencing this:

Go to the itunes movie trailers website and click on any movie trailer...does the video play normal for you or is it distorted?

When i go to the site, the audio is fine but the video is like i just described...Never had that on any previous version of ubuntu, the quicktime video always played great...I tried re-installing the quicktime plug in, but no go...works exactly the same way..

Thanks in advance for checking...;)

---

### Post by VinDSL on 2013-02-16
> **craig10x said:**
> Go to the itunes movie trailers website and [...]

Thanks in advance for checking...;)
I can't even get on their website.

Browser is complaining about bad certs...

---

### Post by Gyokuro on 2013-02-16
Tested it with this video: [http://trailers.apple.com/trailers/independent/upsidedown/](http://trailers.apple.com/trailers/independent/upsidedown/) and works for me - maybe network related at your site.

---

### Post by tdockery97 on 2013-02-16
Worked for me without distortion.  Gorgeous HD video trailer.





Running Ubuntu 13.04 Daily Build from 2/15/13

---

### Post by cariboo on 2013-02-16
> **Gyokuro said:**
> Tested it with this video: [http://trailers.apple.com/trailers/independent/upsidedown/](http://trailers.apple.com/trailers/independent/upsidedown/) and works for me - maybe network related at your site.

For the most part the above trailer worked for me, but I think Google doesn't like quick-time. I run Chromium, and I get asked if I want to allow quick-time content to be played. I also just checked it on my Android tablet, and I don't even get the chance to tell chrome to allow quick-time content.

---

### Post by Curtis6767 on 2013-02-16
> **craig10x said:**
> I was just wondering if others testing ubuntu 13.04 (with unity) are experiencing this:

Go to the itunes movie trailers website and click on any movie trailer...does the video play normal for you or is it distorted?

When i go to the site, the audio is fine but the video is like i just described...Never had that on any previous version of ubuntu, the quicktime video always played great...I tried re-installing the quicktime plug in, but no go...works exactly the same way..

Thanks in advance for checking...;)

Using the latest version of Firefox, the video is distorted for me. To watch the trailer, I had to install two gstreamer plug ins, but even so still distorted.

I'm using the AMD/ATI Cedar Pro video driver.

I then tried using Netflix Desktop and was prompted to download Quicktime. Didn't do it but I wonder if that might work or.... bork the system.

---

### Post by craig10x on 2013-02-16
Seems like most of you are able to get it properly...for me, i have the problem both when running a live session of 13.04 daily build and on my actual installed 13.04...It is actually the first time i ever experienced it on ubuntu...even my installed 12.10 (which i dual boot with) has the quicktime videos playing fine...

I am using Google Chrome 64 bit...but it happens here also on Firefox as well...

**Update: Oh, now i see some others ARE having a problem with it...so i guess it isn't only me...Since it does it on both live session and installed, i figured something must be "out of whack" in 13.04...

Curtis: the quicktime download on Netflix is more then likely a .exe extension (windows) file i would think...

---

### Post by mc4man on 2013-02-16
You could try playing a trailer directly in totem & see if any better. Using the prior posted link as example - 
```
totem http://trailers.apple.com/movies/independent/upsidedown/upsidedown-tlr1_h720p.mov
```
(totem will leave the trailer ^ (105MB) in ~/.cache, if desired try playing it with another player  after fully cached

(if & when grilo plugins are enabled then the is an apple trailer one that works fairly  well

---

### Post by Curtis6767 on 2013-02-16
> **craig10x said:**
> 
Curtis: the quicktime download on Netflix is more then likely a .exe extension (windows) file i would think...

Yes, certainly an exe file and probably not worth the bother, though it would download inside that Netflix/wine folder, I guess. If Quicktime, or whatever it is, worked in 12.04/12.10 then one has to assume that at some point in the future it will work in 13.04, or famous last words.

---

### Post by Gyokuro on 2013-02-16
> **cariboo907 said:**
> For the most part the above trailer worked for me, but I think Google doesn't like quick-time. I run Chromium, and I get asked if I want to allow quick-time content to be played. I also just checked it on my Android tablet, and I don't even get the chance to tell chrome to allow quick-time content.

Hm, it is working for me - firefox 18.02 +i nstall_flash_player_11_linux.x86_64.tar.gz (adobe download) + bottle of jägermeister :D

---

### Post by VinDSL on 2013-02-16
> **Gyokuro said:**
> Tested it with this video: [http://trailers.apple.com/trailers/independent/upsidedown/](http://trailers.apple.com/trailers/independent/upsidedown/) and works for me - maybe network related at your site.
Thanks, for the link!  It worked.

Earlier today, my Chromium 26 (Canary) browser kept going to a248.e.akamai.net and Canary smelled a rat (security warnings galore).  LoL!

Anyway, "Upside Down" looked great, once I got there...

---

### Post by Budovi on 2013-02-16
> **mc4man said:**
> You could try playing a trailer directly in totem & see if any better. Using the prior posted link as example - 
```
totem http://trailers.apple.com/movies/independent/upsidedown/upsidedown-tlr1_h720p.mov
```

I tried that video in FF and also directly in totem, and I can confirm that colours are messed up into blurred areas considerable amount of time...

But with totem nothing new for me, but in this particular case it is really bad. That is the reason why I use VLC :D (not sure if vlc can handle quicktime videos, almost sure that it can't, but this type of video is rare for me...)

---

### Post by VinDSL on 2013-02-16
> **Budovi said:**
> I tried that video in FF and also directly in totem, and I can confirm that colours are messed up into blurred areas considerable amount of time...
Okay, now I'm seeing it (Upside Down Trailer) ...

When I was watching the trailer in Chromium, it looked okay.  The viewing port was so small, and the movie was so weird, I thought was it supposed to look that way.

When I watched it in Totem (fullscreen) the video was obviously messed up.  I could pause it on the bad spots, fast-forward, and rewind it to the exact same spot(s), blah, blah, blah.

Personally, I think the clip, itself, is bad, e.g. has nothing to do with the player.

GIGO, you know?

---

### Post by mc4man on 2013-02-16
Those apple trailers do seem not as good as previously in either FF with the mozilla-plugin or totem itself, with or without grilo.
(slight occasional breakup, ect.

On the other hand are quite fine on a win7 laptop & in Ubuntu with mplayer or grabbing the trailer & using vlc or mplayer. (the 'grabbed' video has the same display issues when played in totem

To test using same Ex.

```
mplayer -user-agent 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)'  http://trailers.apple.com/movies/independent/upsidedown/upsidedown-fte1_h720p.mov
```

or to grab - 
```
wget --user-agent='QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)'  http://trailers.apple.com/movies/independent/upsidedown/upsidedown-fte1_h720p.mov

```

Edit: - a little cross checking shows that there is an issue with some .mov's & gstreamer1.0. On a 12.10 install with totem 3.6.2 which uses gst-1.0 see the same misbehavior. 
Putting back totem-3.4 which uses gst-0.10 & the .mov's are fine. (as is in totem-mozilla

Having already spent more than enough time/effort with getting .mp4's & .mov's fixed in gst-0.10 am not inclined to pursue again. Maybe they fix in near future, maybe not.

Confirmed for myself by putting up a totem-3.4.3 install on 13.04, works fine with these .mov's in browser, locally from grabbed & in grilo, screen was one area among many where gst1.0 produced some garbage

---

### Post by Gyokuro on 2013-02-17
I can confirm that is not working now on RR but on 12.04 it is working without a problem as 12.04 is using gst-0.10 so it is a problem with gst-1.0. Can somebody make a test whether a mp4 file work as mov is only a container for h264 videos (Apple trailers) as I have no spare disk at the moment for RR testing.

---

### Post by mc4man on 2013-02-17
> **Gyokuro said:**
> I can confirm that is not working now on RR but on 12.04 it is working without a problem as 12.04 is using gst-0.10 so it is a problem with gst-1.0. Can somebody make a test whether a mp4 file work as mov is only a container for h264 videos (Apple trailers) as I have no spare disk at the moment for RR testing.
Would appear here to be limited to quicktime vid's with widely varying degree of affect.

Some are fine, others have slight amounts happening at certain 'spots', some are completely borked from beginning.

Checked from other sites, ex. nasa has quicktime - 
[http://www.nasa.gov/multimedia/hd/HDGalleryCollection_archive_1.html](http://www.nasa.gov/multimedia/hd/HDGalleryCollection_archive_1.html)
They are pretty ok with occasional breakups, ex. of that would be Authur mov, breaks here a bit starting around 24 sec.'s.

An ex. of real bad would be here, happens from the git go  - (trailer1
 [http://trailers.apple.com/trailers/marvel/ironman3/](http://trailers.apple.com/trailers/marvel/ironman3/)

---

### Post by zika on 2013-02-18
> **mc4man said:**
> An ex. of real bad would be here, happens from the git go  - (trailer1[http://trailers.apple.com/trailers/marvel/ironman3/](http://trailers.apple.com/trailers/marvel/ironman3/)This one distorts here (Chromium Canary, FF Nightly) also... badly...

---

### Post by craig10x on 2013-02-18
Yeah, that was my observation...this is the first version of ubuntu i ever installed where quicktime videos didn't play flawlessly...in previous ubuntu's they always played extremely smoothly and always looked great...

Can't imagine what is wrong in 13.04 that causes this...i even tried re-installing the quicktime plug in but it didn't help...

---

### Post by mc4man on 2013-02-19
> **craig10x said:**
> Yeah, that was my observation...this is the first version of ubuntu i ever installed where quicktime videos didn't play flawlessly...in previous ubuntu's they always played extremely smoothly and always looked great...

Can't imagine what is wrong in 13.04 that causes this...i even tried re-installing the quicktime plug in but it didn't help...

It's broken in gstreamer1.0 & it appears to have been for quite some time.
(if you were to go to 12.10, add the gnome3 ppa & upgrade totem, gst-1.0, ect. you'll see the same behavior.
Is not confined to the browser plugin, affects local quicktime files played thru any gstreamer media player.

Best bet is to file an upstream bug with a link or 2 to affected online files & maybe even a cut clip or 2.
(10 sec's or so that demonstate should do

---

### Post by mc4man on 2013-02-20
Didn't think anyone else would so here's a bug on.
As it is there is no issue seen by dev in Debian sid, Fedora?, don't know, don't care.
So whether fixable directly or inadvertently down the road, time will tell..
[https://bugzilla.gnome.org/show_bug.cgi?id=694230](https://bugzilla.gnome.org/show_bug.cgi?id=694230)

---

### Post by craig10x on 2013-02-20
Thanks for filing...well, i was the only one to put a bug report on for the touchpad not locking in setting changes in system settings...so i guess we both did our reports solo ;)

Hope it gets fixed, i like watching my movie previews on there :D

---

### Post by mc4man on 2013-02-21
The problem has been idenified as from multi-thread decoding in the libav plugin.
What & when for a fix is not known yet.

If having a local quicktime to test this now produces good playback, adjusting red to suit
```
gst-launch-1.0 filesrc location=[COLOR="Red"]/home/doug/ironman3-tlr1-m4mb0_h720p.mov[/COLOR] ! qtdemux ! avdec_h264 max-threads=1 ! xvimagesink
```

---

### Post by mc4man on 2013-02-25
This has been fixed upstream for gst-libav-1.0.6 
When it shows up in ubuntu no idea - launchpad bug on issue (unconfirmed
[https://bugs.launchpad.net/ubuntu/+source/gst-libav1.0/+bug/1132459](https://bugs.launchpad.net/ubuntu/+source/gst-libav1.0/+bug/1132459)

---

### Post by craig10x on 2013-02-25
thanks for the update...hope we will get the update soon :)

---

### Post by mc4man on 2013-02-25
> **craig10x said:**
> thanks for the update...hope we will get the update soon :)

Maybe Ubuntu will, there is still some time there & it's a simple bug fix update.
Though it's somewhat unfortunate that they didn't upgrade to libav9 (released on Jan 5), & consider using gstreamer 1.1
That would have allowed multi-thread decoding to be enabled without issue & resolved a bug or 2 & maybe added some other stuff like wmal decoding, ect.

At this point don't know if libav will go to 9, probably not.., multimedia doesn't get much priority it seems.

Some other open bugs - 
totem broken on glib - [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1100937](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1100937)
no ffaudio in audacious - [https://bugs.launchpad.net/ubuntu/+source/audacious-plugins/+bug/1080059](https://bugs.launchpad.net/ubuntu/+source/audacious-plugins/+bug/1080059)
grilo in an MIR quagmire - [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1035701](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1035701)
 [https://bugs.launchpad.net/ubuntu/+source/grilo/+bug/1116098](https://bugs.launchpad.net/ubuntu/+source/grilo/+bug/1116098)
(there are several  others, losing interest..

---

### Post by mc4man on 2013-03-19
Fixed in standard ubuntu install (gst-libav-1.0) with latest  - gst-libav1.0 (1.0.5-1ubuntu1
(users of the ppa gst-libav-1.1 would have not been affected as it uses libav9 included in source
totem/glib issue also fixed, ffaudio in audacious remains open but easily fixed

---

### Post by craig10x on 2013-03-19
Yes, you are right, it is fixed :)
That change didn't come into my morning updates, but after reading your post, i just ran the updater again, and saw that change you mentioned...once installed, went to itunes movie trailers, and they are playing perfect again...

By the way, i had forgotten you had filed a bug report for this and had recently filed one also...i guess they must have finally gotten to it... ;)
I always prefer watching my movie trailers there (rather then yahoo movies trailers) so very glad to see it working again...

Now, if they will just get my reported bug about the touchpad pointer speed setting not locking in when you change it, i will be "good to go" (lol)...
If that gets fixed by final release, on my computer 13.04 will be bug free (was not the case for me on 12.10)...

---

### Post by mc4man on 2013-03-20
> **craig10x said:**
> 
By the way, i had forgotten you had filed a bug report for this and had recently filed one also...i guess they must have finally gotten to it... ;)

well sometimes one needs to get a little proactive to get things fixed..

As far as the bug you filed - whenever possible it's better to file against the source the bug is in.

---

