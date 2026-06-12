---
title: "Firefox 3.5 video support worse than flash"
date: 2009-06-30
forum: The Cafe
---

### Post by lovinglinux on 2009-06-30
If you was expecting an alternative for flash video with the release of Firefox 3.5, then you might be disappointed.

I tested the same page with Firefox 3.0.11 using flash and Firefox 3.5b4pre using the new video feature. Believe me or not, but it uses a LOT more CPU than flash.

Open [this video](http://www.mozilla.com/en-US/firefox/video/) on both browsers to see the difference. Maybe the final version will be better, maybe my system is the culprit, but I'm definitely disappointed.

Do you get the same results?

---

### Post by TheLions on 2009-06-30
actually i get better results on html5 video. 
Maybe because i compiled it for my amd64 cpu with all possible optimizations.

---

### Post by lovinglinux on 2009-06-30
> **TheLions said:**
> actually i get better results on html5 video. 
Maybe because i compiled it for my amd64 cpu with all possible optimizations.

Do you have a tutorial for compiling with those optimizations? I have i386 btw.

---

### Post by TheLions on 2009-06-30
> **lovinglinux said:**
> Do you have a tutorial for compiling with those optimizations? I have i386 btw.

get this:
```
sudo apt-get build-dep firefox
sudo apt-get install mercurial libasound2-dev libcurl4-openssl-dev libnotify-dev
```
create '.mozconfig' in your home directory containig something like this
[HTML]    . $topsrcdir/browser/config/mozconfig
export MOZILLA_OFFICIAL=1
export BUILD_OFFICIAL=1
mk_add_options MOZILLA_OFFICIAL=1
mk_add_options BUILD_OFFICIAL=1
ac_add_options --enable-official-branding
    export CHOST="i686-pc-linux-gnu"
    export CFLAGS="-O3 -march=athlon64 -pipe -fomit-frame-pointer -msse -mmmx -m3dnow -mfpmath=sse"
    export CXXFLAGS="-O3 -march=athlon64 -pipe -fomit-frame-pointer -msse -mmmx -m3dnow -mfpmath=sse"
    export CPPFLAGS="-O3 -march=athlon64 -pipe -fomit-frame-pointer -msse -mmmx -m3dnow -mfpmath=sse"

ac_add_options --enable-application=browser
ac_add_options --enable-optimize 
ac_add_options --enable-default-toolkit=cairo-gtk2
ac_add_options --enable-xft
ac_add_options --enable-extensions=default
ac_add_options --enable-strip
ac_add_options --enable-install-strip
ac_add_options --enable-pango
ac_add_options --enable-svg
ac_add_options --enable-canvas
ac_add_options --disable-tests
ac_add_options --disable-accessibility
ac_add_options --disable-jsd
ac_add_options --disable-mochitest
ac_add_options --disable-debug
ac_add_options --disable-installer
ac_add_options --disable-crashreporter
ac_add_options --disable-parental-controls
ac_add_options --with-pthreads

ac_add_options --enable-optimize="-O3 -march=athlon64 -freorder-blocks -fno-reorder-functions -gstabs+ -msse -mmmx -m3dnow -mfpmath=sse -funroll-loops  -fschedule-insns2 -fexpensive-optimizations"[/HTML]
More info about creating '.mozconfig' here: [https://developer.mozilla.org/en/Configuring_Build_Options](https://developer.mozilla.org/en/Configuring_Build_Options)

download the source ([http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5rc3/source/firefox-3.5rc3-source.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5rc3/source/firefox-3.5rc3-source.tar.bz2)) , untar it and in terminal type :```
make -f client.mk build
sudo make install

```

complete guide here: [https://developer.mozilla.org/en/Build_Documentation](https://developer.mozilla.org/en/Build_Documentation)

---

### Post by Bios Element on 2009-06-30
> **lovinglinux said:**
> If you was expecting an alternative for flash video with the release of Firefox 3.5, then you might be disappointed.

I tested the same page with Firefox 3.0.11 using flash and Firefox 3.5b4pre using the new video feature. Believe me or not, but it uses a LOT more CPU than flash.

Open [this video](http://www.mozilla.com/en-US/firefox/comingsoon/) on both browsers to see the difference. Maybe the final version will be better, maybe my system is the culprit, but I'm definitely disappointed.

Do you get the same results?

Nope, my entire system was sleeping under 10% CPU Usage for the entire video. FTR I've got an Intel duel core 2.4Ghz so it's a pretty standard system. Granted I've got an Nvidia 8600GT which helps out.

---

### Post by mikewhatever on 2009-06-30
> **lovinglinux said:**
> If you was expecting an alternative for flash video with the release of Firefox 3.5, then you might be disappointed.

I tested the same page with Firefox 3.0.11 using flash and Firefox 3.5b4pre using the new video feature. Believe me or not, but it uses a LOT more CPU than flash.

Open [this video](http://www.mozilla.com/en-US/firefox/comingsoon/) on both browsers to see the difference. Maybe the final version will be better, maybe my system is the culprit, but I'm definitely disappointed.

Do you get the same results?

I think you missed the point entirely. No one has ever said 3.5 will use less CPU for video, the point is, it requires no plugins to play it. Just read the note to the right of the video window or watch the video again.
It's soft of like getting frustrated that your dog doesn't make tee in the morning.

---

### Post by froggyswamp on 2009-06-30
> **lovinglinux said:**
> If you was expecting an alternative for flash video with the release of Firefox 3.5, then you might be disappointed.

I tested the same page with Firefox 3.0.11 using flash and Firefox 3.5b4pre using the new video feature. Believe me or not, but it uses a LOT more CPU than flash.

Open [this video]("http://www.mozilla.com/en-US/firefox/comingsoon/") on both browsers to see the difference. Maybe the final version will be better, maybe my system is the culprit, but I'm definitely disappointed.

Do you get the same results?
For the Linux port it is true especially with crappy Intel  & ATI drivers, but on windows the CPU usage was very low.

---

### Post by Closed_Port on 2009-06-30
> **froggyswamp said:**
> For the Linux port it is true especially with crappy Intel  & ATI drivers, but on windows the CPU usage was very low.

Hm, works fine for me here on my netbook running linux with a crappy intel gpu.

---

### Post by jomiolto on 2009-06-30
> **lovinglinux said:**
> If you was expecting an alternative for flash video with the release of Firefox 3.5, then you might be disappointed.

Nah, I'm already amazed :)

The HTML5 <video> tag makes it really easy (possibly too easy ;) ) to add video to websites and there's no need for pesky plugins. Flash in particular is awful (never tried Silverlight...)

> **lovinglinux said:**
> I tested the same page with Firefox 3.0.11 using flash and Firefox 3.5b4pre using the new video feature. Believe me or not, but it uses a LOT more CPU than flash.

Open [this video](http://www.mozilla.com/en-US/firefox/comingsoon/) on both browsers to see the difference. Maybe the final version will be better, maybe my system is the culprit, but I'm definitely disappointed.

Do you get the same results?

For me the CPU usage is about the same, with perhaps Flash using a little bit less CPU. Despite that Flash feels more sluggish and if I open several tabs with Flash content, my CPU usage jumps to 100% and the whole browser becomes slo-o-ow (even if I'm only playing one of the Flash videos). With <video> I can open several tabs with videos and the CPU usage doesn't get noticeably higher.

All in all, I hope <video> catches on soon.

---

### Post by Pogeymanz on 2009-06-30
Wow. This is great. It still uses a good amount of CPU, but less than Flash does.

I hope this inspires a movement away from Flash and Silverlight. Of course, for those sites that want to "protect" their content, Flash and Silverlight will stay.

I'm all for open formats and I'm very excited about this.

---

### Post by lovinglinux on 2009-06-30
> **TheLions said:**
> get this:

Thank you very much for the tutorial.


> **Bios Element said:**
> Nope, my entire system was sleeping under 10% CPU Usage for the entire video. FTR I've got an Intel duel core 2.4Ghz so it's a pretty standard system. Granted I've got an Nvidia 8600GT which helps out.

I have a single core P4 3.06 GHz HT and nVidia 7300 GT gfx card.

> **mikewhatever said:**
> I think you missed the point entirely. No one has ever said 3.5 will use less CPU for video, the point is, it requires no plugins to play it. Just read the note to the right of the video window or watch the video again.

No I didn't. I totally agree that playing videos without plugins is a big advancement, but that is exactly the point here. I still need a plugin, because the built-in video support gives me a worse experience.

> **mikewhatever said:**
> It's soft of like getting frustrated that your dog doesn't make tee in the morning.

Sorry, but that analogy is nonsense. What you are saying is like if I were expecting to play World of Warcraft with it. I just want to play videos and have a better experience than when using flash. That is the point here right, playing videos without plugins? Well, I still need the plugin to have a "decent" experience.


> **froggyswamp said:**
> For the Linux port it is true especially with crappy Intel  & ATI drivers, but on windows the CPU usage was very low.

Well, I don't use Windows and have nVidia card.


> **jomiolto said:**
> Nah, I'm already amazed :)

The HTML5 <video> tag makes it really easy (possibly too easy ;) ) to add video to websites and there's no need for pesky plugins. Flash in particular is awful (never tried Silverlight...)

For me the CPU usage is about the same, with perhaps Flash using a little bit less CPU. Despite that Flash feels more sluggish and if I open several tabs with Flash content, my CPU usage jumps to 100% and the whole browser becomes slo-o-ow (even if I'm only playing one of the Flash videos). With <video> I can open several tabs with videos and the CPU usage doesn't get noticeably higher.

All in all, I hope <video> catches on soon.

Just for comparison, if I use a [greasemonkey](https://addons.mozilla.org/en-US/firefox/addon/748) script to [replace youtube flash player with gecko-mediaplayer](http://userscripts.org/scripts/show/41722), it plays youtube videos pretty fine. No hiccups and CPU usage is very low. So who is the culprit? Is not my hardware. I understand that flash cannot deliver the same experience because is closed source and we depend on Adobe to get plugins (I know about swfdec and gnash), but the video support on Firefox should deliver a better experience than flash, after all it is all about open source.

---

### Post by geoken on 2009-06-30
> **lovinglinux said:**
> I understand that flash cannot deliver the same experience because is closed source and we depend on Adobe to get plugins (I know about swfdec and gnash), but the video support on Firefox should deliver a better experience than flash, after all it is all about open source.

Aren't you willing to re-think your suppositions about why flash is slow seeing as how firefox in the same situation also runs slow?

---

### Post by lovinglinux on 2009-06-30
> **geoken said:**
> Aren't you willing to re-think your suppositions about why flash is slow seeing as how firefox in the same situation also runs slow?

Yes. I'm starting to think it's Firefox fault :)

Seriously, as I said, Firefox plays videos pretty fine and with very low CPU usage if I replace the flash player with a gecko-mediaplayer by using a greasemonkey script. So who is the culprit?

---

### Post by khelben1979 on 2009-06-30
I have never seen Firefox 3.5 in action, but once they release a stable version of it, I will test it.

---

### Post by hyperdude111 on 2009-06-30
> **khelben1979 said:**
> I have never seen Firefox 3.5 in action, but once they release a stable version of it, I will test it.

They have release the final, stable  version today. 

[http://lifehacker.com/5304572/firefox-35-officially-available-for-download](http://lifehacker.com/5304572/firefox-35-officially-available-for-download)

---

### Post by geoken on 2009-06-30
> **lovinglinux said:**
> Yes. I'm starting to think it's Firefox fault :)

Seriously, as I said, Firefox plays videos pretty fine and with very low CPU usage if I replace the flash player with a gecko-mediaplayer by using a greasemonkey script. So who is the culprit?

I'd guess (like Adobe says) RGB based video is slower than regular YUV and decoding in software at a higher level (ie in a plugin or browser) slows it down even more.

---

### Post by RazVayne on 2009-06-30
> **khelben1979 said:**
> I have never seen Firefox 3.5 in action, but once they release a stable version of it, I will test it.

What do you mean?Isnt it out already?

[www.getfirefox.com](www.getfirefox.com)

Hmm,someone beat me 2 it...

---

### Post by lovinglinux on 2009-07-01
> **TheLions said:**
> actually i get better results on html5 video. 
Maybe because i compiled it for my amd64 cpu with all possible optimizations.

> **TheLions said:**
> get this:
```
sudo apt-get build-dep firefox
sudo apt-get install mercurial libasound2-dev libcurl4-openssl-dev libnotify-dev
```
create '.mozconfig' in your home directory containig something like this
[HTML]    . $topsrcdir/browser/config/mozconfig
export MOZILLA_OFFICIAL=1
export BUILD_OFFICIAL=1
mk_add_options MOZILLA_OFFICIAL=1
mk_add_options BUILD_OFFICIAL=1
ac_add_options --enable-official-branding
    export CHOST="i686-pc-linux-gnu"
    export CFLAGS="-O3 -march=athlon64 -pipe -fomit-frame-pointer -msse -mmmx -m3dnow -mfpmath=sse"
    export CXXFLAGS="-O3 -march=athlon64 -pipe -fomit-frame-pointer -msse -mmmx -m3dnow -mfpmath=sse"
    export CPPFLAGS="-O3 -march=athlon64 -pipe -fomit-frame-pointer -msse -mmmx -m3dnow -mfpmath=sse"

ac_add_options --enable-application=browser
ac_add_options --enable-optimize 
ac_add_options --enable-default-toolkit=cairo-gtk2
ac_add_options --enable-xft
ac_add_options --enable-extensions=default
ac_add_options --enable-strip
ac_add_options --enable-install-strip
ac_add_options --enable-pango
ac_add_options --enable-svg
ac_add_options --enable-canvas
ac_add_options --disable-tests
ac_add_options --disable-accessibility
ac_add_options --disable-jsd
ac_add_options --disable-mochitest
ac_add_options --disable-debug
ac_add_options --disable-installer
ac_add_options --disable-crashreporter
ac_add_options --disable-parental-controls
ac_add_options --with-pthreads

ac_add_options --enable-optimize="-O3 -march=athlon64 -freorder-blocks -fno-reorder-functions -gstabs+ -msse -mmmx -m3dnow -mfpmath=sse -funroll-loops  -fschedule-insns2 -fexpensive-optimizations"[/HTML]
More info about creating '.mozconfig' here: [https://developer.mozilla.org/en/Configuring_Build_Options](https://developer.mozilla.org/en/Configuring_Build_Options)

download the source ([http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5rc3/source/firefox-3.5rc3-source.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5rc3/source/firefox-3.5rc3-source.tar.bz2)) , untar it and in terminal type :```
make -f client.mk build
sudo make install

```

complete guide here: [https://developer.mozilla.org/en/Build_Documentation](https://developer.mozilla.org/en/Build_Documentation)


OMG, the difference is freaking amazing. It took some time to learn about all the options, but I have compiled it today and now Firefox benchmarks are 30% higher. It beats Opera 10 :)

The html5 video is still CPU intensive, but it is way much better now. 

Thank you so much. 

Here is my *.mozconfig* for Pentium4 3.06GHz HT Prescott:

```
    . $topsrcdir/browser/config/mozconfig
export MOZILLA_OFFICIAL=1
export BUILD_OFFICIAL=1
mk_add_options MOZILLA_OFFICIAL=1
mk_add_options BUILD_OFFICIAL=1
ac_add_options --enable-official-branding
    export CHOST="i686-pc-linux-gnu"
    export CFLAGS="-O3 -march=prescott -pipe -fomit-frame-pointer"
    export CXXFLAGS="-O3 -march=prescott -pipe -fomit-frame-pointer"
    export CPPFLAGS="-O3 -march=prescott -pipe -fomit-frame-pointer"

ac_add_options --enable-application=browser
ac_add_options --enable-optimize 
ac_add_options --enable-default-toolkit=cairo-gtk2
ac_add_options --enable-xft
ac_add_options --enable-extensions=default
ac_add_options --enable-strip
ac_add_options --enable-install-strip
ac_add_options --enable-pango
ac_add_options --enable-svg
ac_add_options --enable-canvas
ac_add_options --disable-tests
ac_add_options --disable-accessibility
ac_add_options --disable-mochitest
ac_add_options --disable-debug
ac_add_options --disable-installer
ac_add_options --disable-crashreporter
ac_add_options --disable-parental-controls
ac_add_options --with-pthreads
```

From now on I will always compile Firefox myself.

---

### Post by mikewhatever on 2009-07-01
> **lovinglinux said:**
> 

Sorry, but that analogy is nonsense. What you are saying is like if I were expecting to play World of Warcraft with it. I just want to play videos and have a better experience than when using flash. That is the point here right, playing videos without plugins? Well, I still need the plugin to have a "decent" experience.



You are entitled to your opinion as much as I am to mine. That said, I think the nonsense here is this: Firefox 3.5 video support worse than flash. Let's think reasonably. Did Mozilla ever promised less then flash CPU usage? Did they ever mention that the experience is more pleasant then that of using flash? No, they didn't, so why make such a fuss out of nothing? Don't you understand that CPU usage has nothing whatsoever to do with the new Open Video and Audio feature?

---

### Post by Sealbhach on 2009-07-01
Is anyone able to play these videos?

[http://www.youtube.com/html5](http://www.youtube.com/html5)

I've got 3.5 but I don't know if it can play HTML5 video, just want to test it but none of those videos play, I just get black squares.


.

---

### Post by daverich on 2009-07-01
> **Sealbhach said:**
> Is anyone able to play these videos?

[http://www.youtube.com/html5](http://www.youtube.com/html5)

I've got 3.5 but I don't know if it can play HTML5 video, just want to test it but none of those videos play, I just get black squares.


.

yup not working here either.

Kind regards

Dave Rich

---

### Post by LookTJ on 2009-07-01
> **Sealbhach said:**
> Is anyone able to play these videos?

[http://www.youtube.com/html5](http://www.youtube.com/html5)

I've got 3.5 but I don't know if it can play HTML5 video, just want to test it but none of those videos play, I just get black squares.


.
The site doesn't look like it's complete.

---

### Post by Sealbhach on 2009-07-01
Oh, OK thanks.

.

---

### Post by jomiolto on 2009-07-01
> **Sealbhach said:**
> Is anyone able to play these videos?

[http://www.youtube.com/html5](http://www.youtube.com/html5)

I've got 3.5 but I don't know if it can play HTML5 video, just want to test it but none of those videos play, I just get black squares.


.

As far as I understand, those are not actual videos, but rather a showcase for Google plugin that makes 3D-accelerated graphics possible in a web browser. I'm quite sure I saw the actual results somewhere (possibly in a YouTube video?).

Ah, here's more: [http://code.google.com/apis/o3d/](http://code.google.com/apis/o3d/)

HTH :)

---

### Post by lovinglinux on 2009-07-01
> **Sealbhach said:**
> I've got 3.5 but I don't know if it can play HTML5 video, just want to test it but none of those videos play, I just get black squares.

Visit [http://www.mozilla.com/en-US/firefox/upgrade.html](http://www.mozilla.com/en-US/firefox/upgrade.html) and click the "Take a Tour of Firefox 3.5....Watch Video" link on the lower left. It should play with a different interface if your browser has the ability to play html5 video.


> **mikewhatever said:**
> You are entitled to your opinion as much as I am to mine. That said, I think the nonsense here is this: Firefox 3.5 video support worse than flash. Let's think reasonably. Did Mozilla ever promised less then flash CPU usage? Did they ever mention that the experience is more pleasant then that of using flash? No, they didn't, so why make such a fuss out of nothing? Don't you understand that CPU usage has nothing whatsoever to do with the new Open Video and Audio feature?

We both said what we think and we still disagree, so continuing this discussion will not be productive. If you don't like the thread title you are entitled to report it to a moderator and ask for a title change. I wouldn't mind if you do that.

---

### Post by SunnyRabbiera on 2009-07-01
Well the vid works fine here.

---

### Post by lovinglinux on 2009-07-01
> **SunnyRabbiera said:**
> Well the vid works fine here.

Is working fine here too, after compiling Firefox with optimizations. Still uses more CPU than flash, but doesn't need a plugin. So I'm not so disappointed anymore :)

---

### Post by YeOK on 2009-07-01
> **jomiolto said:**
> As far as I understand, those are not actual videos, but rather a showcase for Google plugin that makes 3D-accelerated graphics possible in a web browser. I'm quite sure I saw the actual results somewhere (possibly in a YouTube video?).

Ah, here's more: [http://code.google.com/apis/o3d/](http://code.google.com/apis/o3d/)

HTH :)

The reason YouTube's HTML5 demo fails is because google used a different codec, They use h.246 while Firefox 3.5 supports the open source codec Theora. 

HTML5 is great, but until we get a standard codec, its going to be messy.

Expect flash video for a while longer yet.

---

### Post by HavocXphere on 2009-07-01
> **lovinglinux said:**
> I tested the same page with Firefox 3.0.11 using flash and Firefox 3.5b4pre using the new video feature. Believe me or not, but it uses a LOT more CPU than flash.
You're right in that theora does in principle use more cpu cycles. However, the comparison your doing is ummmm flawed.

Pages can redirect users to different video formats depending on the means used to access them. In the page in question:
```
<video width="640" height="360" controls="controls" autoplay="true">
    <source **src="http://videos.mozilla.org/firefox/3.5/overview/overview.ogv"** type="video/ogg" />
    <source src="http://videos.mozilla.org/firefox/3.5/overview/overview.mp4" type="video/mp4" />
    <object width="640" height="385" type="application/**x-shockwave-flash" data="http://www.youtube.com/v/k5Zbc-Rg6e8"**>
        <param name="movie" value="http://www.youtube.com/v/k5Zbc-Rg6e8" />

        <!--[if gt IE 6]>
        <object width="640" height="375" classid="clsid:02BF25D5-8C17-4B23-BC80-D3488ABDDC6B">
            <param name="src" value="http://videos.mozilla.org/firefox/3.5/overview/overview.ogv" />
            <param name="autoplay" value="true" /><!
        [endif]-->
        <!--[if gt IE 6]><!-->
        <object width="640" height="375" type="video/quicktime" data="http://videos.mozilla.org/firefox/3.5/overview/overview.mp4"

```
As you can see **you are comparing two different videos**. Hell, they are not even on the same site (mozilla vs youtube). Bitrate, filesize and quality is pretty much guaranteed to be different, so yes CPU cycle will also differ.

Don't believe me? Check carefully again. The one has a youtube logo at the bottom (flash configuration on FF3.0.11) the other does not (35b4 html5).

And finally, h264 (which youtube uses) can be GFX card accelerated. So I'd expect the flash variation to use less CPU cycles since it is *probably* being off-loaded to the gfx card. Theora is not gfx accelerated.

btw the link in the Opening post redirects to FF frontpage since FF3.5 launched. Original page is in the google cache:
```
http://www.google.co.za/url?sa=t&source=web&ct=clnk&cd=1&url=http%3A%2F%2F209.85.229.132%2Fsearch%3Fq%3Dcache%3A3EXH0uLeD6gJ%3Awww.mozilla.com%2Ffirefox%2Fcomingsoon%2F%2Bhttp%3A%2F%2Fwww.mozilla.com%2Fen-US%2Ffirefox%2Fcomingsoon%2F%26cd%3D1%26hl%3Den%26ct%3Dclnk%26gl%3Dza%26client%3Dfirefox-a&ei=xdRLSqrfBNihjAfb4pnQAQ&usg=AFQjCNGYL3KwMK9gRtZl3i7mMvKIPe05lg&sig2=tvxTRC5Z65mc6-haif8fyQ

```

---

### Post by lovinglinux on 2009-07-01
> **HavocXphere said:**
> You're right in that theora does in principle use more cpu cycles. However, the comparison your doing is ummmm flawed.

Pages can redirect users to different video formats depending on the means used to access them. In the page in question:
```
<video width="640" height="360" controls="controls" autoplay="true">
    <source **src="http://videos.mozilla.org/firefox/3.5/overview/overview.ogv"** type="video/ogg" />
    <source src="http://videos.mozilla.org/firefox/3.5/overview/overview.mp4" type="video/mp4" />
    <object width="640" height="385" type="application/**x-shockwave-flash" data="http://www.youtube.com/v/k5Zbc-Rg6e8"**>
        <param name="movie" value="http://www.youtube.com/v/k5Zbc-Rg6e8" />

        <!--[if gt IE 6]>
        <object width="640" height="375" classid="clsid:02BF25D5-8C17-4B23-BC80-D3488ABDDC6B">
            <param name="src" value="http://videos.mozilla.org/firefox/3.5/overview/overview.ogv" />
            <param name="autoplay" value="true" /><!
        [endif]-->
        <!--[if gt IE 6]><!-->
        <object width="640" height="375" type="video/quicktime" data="http://videos.mozilla.org/firefox/3.5/overview/overview.mp4"

```
As you can see **you are comparing two different videos**. Hell, they are not even on the same site (mozilla vs youtube). Bitrate, filesize and quality is pretty much guaranteed to be different, so yes CPU cycle will also differ.

Don't believe me? Check carefully again. The one has a youtube logo at the bottom (flash configuration on FF3.0.11) the other does not (35b4 html5).

And finally, h264 (which youtube uses) can be GFX card accelerated. So I'd expect the flash variation to use less CPU cycles since it is *probably* being off-loaded to the gfx card. Theora is not gfx accelerated.

Thanks for this excellent explanation. I guess you might be able to explain why the theora video uses 66% of my CPU (sum of [color=#CC0000]firefox[/color]+xorg cpu usage), while the same video/codec uses 14% of my CPU (sum of [color=#33CC00]mplayer[/color]+xorg cpu usage), when downloaded and played with gnome-mplayer?

Also why the same video using h264 codec uses 45% of my CPU (sum of [color=#CC0000]firefox[/color]+xorg cpu usage), while the same video/codec uses 9% of my CPU (sum of [color=#33CC00]mplayer[/color]+xorg cpu usage), when downloaded and played with gnome-mplayer?

Most of the extra CPU usage while viewing theora in Firefox goes to xorg cycles. I believe this in line with your explanation, but it doesn't invalidate the fact that both video technologies are much more CPU intensive when viewing through Firefox than viewing with gnome-mplayer. In this scenario, the extra load of theora codec makes the html5 video worse than flash in terms of CPU usage and user experience.

Don't get me wrong. I admire the initiative of Firefox to enable html5 video already and I do understand the benefits. Who would want flash when you can play videos natively, using open source codecs? But for someone who loves Firefox (yes I do, I can't live without it for years, even when I was a Windows user), Ubuntu and videos, this is disappointing, specially because I thought it could improve my video experience.

---

### Post by doorknob60 on 2009-07-01
All videos I've tried with the <video> tags my CPU usage doesn't go above 20%, usually less. That's with a few other random things running that could be contributing too. The same can't be said about Flash. Flash doesn't usually take up too much CPU, it still takes more than the <video> tags. See my specs in Siggy.

---

### Post by khelben1979 on 2009-07-02
> **hyperdude111 said:**
> They have release the final, stable  version today. 

[http://lifehacker.com/5304572/firefox-35-officially-available-for-download](http://lifehacker.com/5304572/firefox-35-officially-available-for-download)

Not for the ppc linux platform, from what I can see.

---

### Post by lovinglinux on 2009-07-15
Just a heads up...

I don't know if some recent Ubuntu updates did the trick or if this is the result of compiling Firefox with PGO, but the same video embedded with html5 is using 10-20% less CPU than flash now. When I compiled just using processor optimization it improved a lot, but now it's better than flash. Great news.

---

### Post by Viva on 2009-07-15
Easily better than flash on my computer.

---

### Post by lovinglinux on 2009-07-15
I'm experiencing something weird. Watch [this video](http://www.mozilla.com/en-US/firefox/video/?video=fastest-sport-stacker) till the end and don't stop it or close the tab. Leave it there and check after a few seconds if your CPU usage starts to increase, a lot, until you close the tab.

Additionally, watch the same video from [http://www.mozilla.com/en-US/firefox/fastest/](http://www.mozilla.com/en-US/firefox/fastest/)

The page above includes a javascript overlay player. I guess that is the culprit of high CPU usage, not the video itself. Do you also experience huge differences in CPU usage between both videos?


Note: Comments about the video content [here](http://ubuntuforums.org/showthread.php?t=1214387).

---

