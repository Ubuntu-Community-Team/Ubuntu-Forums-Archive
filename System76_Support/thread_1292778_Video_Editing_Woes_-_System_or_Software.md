---
title: "Video Editing Woes - System or Software?"
date: 2009-10-16
forum: System76 Support
---

### Post by Grey Melon on 2009-10-16
I'm working with a Bonobo Pro which is great but am having issues when trying to edit video. I work for a non-profit org, that I helped start 20 years ago, and need to take in up to 1 hour HD clips and edit down to 10 -15 minute finished product.

I've tried every program mentioned within this forum with no success. I'm aware that there are problems, after reading many posts, but I can't even begin to work due to poor clip playback from the timeline. Tried both MTS and MP4 convert.

I'm trying to determine if my problems are related to my system or if I have to wait for these apps to further mature. From these forums it looks like people are editing on much slower systems which leads me to belive it's a system problem.

I've narrowed it down to 4 programs:

**Blender** - No probs with editing but can't get a usable output. missing frames, audio not synched and more
**Openshot** - Great app but audio playback is useless for editing and video is choppy at best. This is before I've added any transitions whatsoever.
**Pitivi** - Strangely this app plays the audio flawlessly but video has 3 - 5 second delays. Once again useless not to mention no transitions.
**Kdenlive** - Good looking app but same issues as openshot only it crashes more. I could live with if I could get normal playback

I've tried too many potential fixes to remember so I'd prefer to act as though I'm diagnosing from scratch. Thanks for any help.

---

### Post by betrunkenaffe on 2009-10-16
This might be better posted in another forum, there might be video editing gurus there that can help. Hopefully one has sys76 and can answer the question :)

---

### Post by thomasaaron on 2009-10-16
I don't know a lot about video editing, but I created a demo video for my son's wrestling team, cutting out pieces form several hours of video and putting them all together.

I used Kino. It had some limitations, but then I'm probably pretty lame at video editing anyway. 

Have you tried Kino?

---

### Post by HotShotDJ on 2009-10-16
I've found Cinelerra to be among the best professional quality video editors out there.  The interface isn't pretty and you'll need to spend some time learning how to use it and getting used to it, but the results have always been perfect for me.

[http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php)

I've also used Kino in the past with mixed results.  The main problem was video/audio syncing... audio and video would become more and more out of sync as resulting video was played.  However, that was over a year ago.  The developers may have gotten this problem sorted now.

---

### Post by Grey Melon on 2009-10-16
I should first mention that I'm using 64bit Ubuntu 9.04
[B]
Tried Kino again:[/B]
-major audio sync problems and spontaneous fast forward during playback.
-program crash when attempting any trim.

**Tried Cinelerra again:**
-playback of any video resources, from HD to video phone, is like stepping through one frame at a time with 2 to 3 seconds pause in between.

This is why I posted my problem in this area of the forums. It seems to me that something is problematic on a system level but I need guidance with the right places and procedures to check.

**Viewing Conky during playback with cinelerra shows the following:**
-camera phone video playback: cpu spikes just above 3.0% then drops to around 0.6%. Memory stays around 7.0%
-HD footage playback: cpu spikes just above 23.0% then drops to around 1.0%. Memory stays around 7.0%

---

### Post by Arup on 2009-10-16
The best one I have found is Openshot. To install it follow instructions here [http://www.unixmen.com/linux-tutorials/414-openshot-the-magic-has-arrived](http://www.unixmen.com/linux-tutorials/414-openshot-the-magic-has-arrived)

Also make sure you have the latest video drivers installed.

---

### Post by Grey Melon on 2009-10-16
> **Arup said:**
> The best one I have found is Openshot. To install it follow instructions here [http://www.unixmen.com/linux-tutorials/414-openshot-the-magic-has-arrived](http://www.unixmen.com/linux-tutorials/414-openshot-the-magic-has-arrived)

Also make sure you have the latest video drivers installed.

Hi Arup,

I like Openshot very much and am following it's progress diligently however I have had no success getting usable video/audio playback from it or any app I've tried. The clips usually play fine when using vlc or movie player but even then there are moments where performance degrades.

---

### Post by HotShotDJ on 2009-10-16
> **Grey Melon said:**
> **Tried Cinelerra again:**
-playback of any video resources, from HD to video phone, is like stepping through one frame at a time with 2 to 3 seconds pause in between.Yes.  I remember this problem.  It is due to one of the default settings that has it dropping frames.  It was very easily fixed, but for the life of me, I can't remember what it was.  I'll look into it later today, but I remember being frustrated by it until I checked off the correct tick-box somewhere in the configuration.

---

### Post by Arup on 2009-10-16
> **Grey Melon said:**
> Hi Arup,

I like Openshot very much and am following it's progress diligently however I have had no success getting usable video/audio playback from it or any app I've tried. The clips usually play fine when using vlc or movie player but even then there are moments where performance degrades.

Hmm, thats surprising. I don't really have cutting edge hardware except for the dual quad core. Have basic nvidia 8400GS and ancient Yamaha WaveForce YMF724 sound card but I don't get any skipping with my edited videos. I do have compiz turned off when I do my work.

---

### Post by Grey Melon on 2009-10-16
> **HotShotDJ said:**
> Yes.  I remember this problem.  It is due to one of the default settings that has it dropping frames.  It was very easily fixed, but for the life of me, I can't remember what it was.  I'll look into it later today, but I remember being frustrated by it until I checked off the correct tick-box somewhere in the configuration.

That would be great. I'll look forward to hearing back from you later and in the meantime will poke around as well, very carefully.

---

### Post by Grey Melon on 2009-10-16
> **Arup said:**
> Hmm, thats surprising. I don't really have cutting edge hardware except for the dual quad core. Have basic nvidia 8400GS and ancient Yamaha WaveForce YMF724 sound card but I don't get any skipping with my edited videos. I do have compiz turned off when I do my work.

I agree it is surprising. If it wasn't for these issues I could be getting work done with the current state of Openshot.

When you say "have compiz turned off" do you mean *_visual effects_* set to _*none*_ or something more? I never turn the *_visual effects_* above _*none*_ so unless there's more to it that shouldn't be the culprit.

---

### Post by Grey Melon on 2009-10-16
Well I poked around Cinelerra's settings and nothing has changed. Are there any **System76** folks around that can help troubleshoot a "poor video with audio playback performance" issue. I'm still leaning towards this being something in the system and not the fault of every editing package I've tried.

---

### Post by thomasaaron on 2009-10-16
If this is only in video editing software, there isn't a lot I can do to replicate the problem and help you test.

If it is occuring in different areas...

---

### Post by HotShotDJ on 2009-10-16
> **Grey Melon said:**
> That would be great. I'll look forward to hearing back from you later and in the meantime will poke around as well, very carefully.Ok... I've done some testing.  Here are the settings that work well on my brand new PanP5 (screenshot).

---

### Post by Grey Melon on 2009-10-16
> **thomasaaron said:**
> If this is only in video editing software, there isn't a lot I can do to replicate the problem and help you test.

If it is occuring in different areas...

It's also occurring when playing the .MP4 and .MTS files through both vlc and Movie Player.

The only difference is it happens more intermittently. Sometimes both file types will play flawlessly and then one click later it's single digit frame rates, at best, and acceptable audio. Sometimes it happens the opposite way. Starts with ultra low performance then click and everything is good. Doesn't matter which player I use.

What commands could I use to begin tracking this problem to it's source. As I stated in my first post I've tried multiple ideas from multiple posts and have seen no "tracks". I'm at the point where I'd prefer a more effient and direct approach than poking through the forums. Fundamentaly that's why I chose to start a new thread here.

I appreciate the ideas so far.

---

### Post by Grey Melon on 2009-10-16
> **HotShotDJ said:**
> Ok... I've done some testing.  Here are the settings that work well on my brand new PanP5 (screenshot).

Thanks for the image. That's pretty much where my settings were except my frame rate is resting at a staggering -1.0000 and yes that's a negative sign before the one. I am definitely open to suggestions. In my limited experience these kind of problems usually stem from a "laser like" pinpoint. Something small yet precise and profoundly troublesome.

Too much drama? Yeah maybe.

---

### Post by thomasaaron on 2009-10-17
Grey, does it only do it with the MP4 and MTS files that you've built?
Can you point me to a troublesome file online?

---

### Post by ejolson on 2009-10-18
> **Grey Melon said:**
> I am definitely open to suggestions. In my limited experience these kind of problems usually stem from a "laser like" pinpoint. Something small yet precise and profoundly troublesome.

If your computer is a few years old you should not expect more than 2 to 3 frames per second playback speed for high definition video.  Use standard definition proxy files for smooth playback when editing.  See

[http://cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_21.html#SEC310](http://cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_21.html#SEC310)

Additional information is at

[http://www.renomath.org/ejolson/video/avchd/](http://www.renomath.org/ejolson/video/avchd/)

---

### Post by Grey Melon on 2009-10-19
> **thomasaaron said:**
> Grey, does it only do it with the MP4 and MTS files that you've built?
Can you point me to a troublesome file online?

I've uploaded two different versions of the same footage to my server. You and anyone else here are welcome to download them for testing purposes.

[http://www.greymelon.com/video.html](http://www.greymelon.com/video.html)

I have tried multiple configurations of wrappers, codecs and file type with no change in result. I've also tried cell phone video which behaved the same as HD footage. Yesterday I started out, very briefly, with playback being flawless in Cinelerra then 2 minutes later no dice on any footage in any program. Also, as I've stated earlier, I have chaotic results playing the files with VLC or Movie Player. Sometimes great sometimes bad.

---

### Post by Grey Melon on 2009-10-19
> **ejolson said:**
> If your computer is a few years old you should not expect more than 2 to 3 frames per second playback speed for high definition video.  Use standard definition proxy files for smooth playback when editing.  See

[http://cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_21.html#SEC310](http://cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_21.html#SEC310)

Additional information is at

[http://www.renomath.org/ejolson/video/avchd/](http://www.renomath.org/ejolson/video/avchd/)

My computer is only a few months old but I will give this a try. Thanks for the info.

---

### Post by Grey Melon on 2009-10-21
Has anyone had a chance to test the video clips I posted? I'm still having issues with playback

---

### Post by thomasaaron on 2009-10-21
I just tried, but when I click the link you provided, it goes to...

[http://www.greymelon.com/videos/00037.mp4](http://www.greymelon.com/videos/00037.mp4)

...which just shows a blank white page.

---

### Post by Grey Melon on 2009-10-21
> **thomasaaron said:**
> I just tried, but when I click the link you provided, it goes to...

[http://www.greymelon.com/videos/00037.mp4](http://www.greymelon.com/videos/00037.mp4)

...which just shows a blank white page.

Sorry about that. It's fixed now. The link should take you to a white page with two linked files. Same video but one is .MTS and one is .mp4

Here's the link again

[http://www.greymelon.com/video.html](http://www.greymelon.com/video.html)

---

### Post by bit mad on 2009-10-21
Stuck in Windows Vistaland... I've tried your 1440x1080 29.97 files :

Your **mp4** plays nicely, smoothly in VLC but is sound-only in Media Player Classic.

Your **MTS** plays smoothly in VLC and MPC but with artifacts - odd edges to the child's arm when moving.

---

### Post by thomasaaron on 2009-10-21
They are playing great on my system too.

So... do *any* MP4s and MTS files play back poorly with your computer? Or is it just the ones you've created?

---

### Post by Grey Melon on 2009-10-21
> **thomasaaron said:**
> They are playing great on my system too.

So... do *any* MP4s and MTS files play back poorly with your computer? Or is it just the ones you've created?

Every video file on my system displays the same behavior(MTS, avi, mp4, cell phone).

1. ***Standard System Playback*** - Sometimes flawless playback sometimes poor playback.

2. ***Playback in all Editing Software*** - Mostly abysmal playback(-1 to +1fps) with choppy and no-sync audio. Then there are rare and short lived moments of almost normal performance.

---

### Post by Fire_Chief on 2009-10-21
Could you give us a quick spec list of your system?
CPU type & speed
RAM
Video card
Hard drive size/type/free space

---

### Post by thomasaaron on 2009-10-21
OK. Thanks. That doesn't sound right. Most confusing is the intermittent problem with standard playback.

What version of the nVidia driver are you using?
Are you still running Ubuntu version that came with your system, or have you re-installed, etc..?
What kind of frame-rate to you get if you open a terminal and run...
```
glxgears
```

---

### Post by Grey Melon on 2009-10-21
Here are my system specs:

***OS***: Ubuntu 64bit 9.04
***CPU***: Intel Core2 Quad Q9000 @ 2.00GHz
***Memory***: 4GB
***Video Hardware***: GeForce GTX 280M
***Video Driver***: NVIDIA UNIX x86_64 Kernel Module 190.18.05
***Hard Drive***: 500GB ATA ST9500420AS

Notes:
- I'm still using the OS version "as installed" when the system shipped. No re-install or major updates(other than the typical updates from time to time)
- I was using the 180 version of the restricted video drivers, as recommended, I installed the version I'm using now in hopes of fixing my issues which didn't work.

Also here's a screenshot of the ***glxgears*** command:
[IMG]http://www.greymelon.com/photos/glxgears.png[/IMG]

---

### Post by thomasaaron on 2009-10-22
All of that looks pretty good.

Try playing one of your videos and simultaneously running...
```
top
```
...to see if some other process is being a hog.

---

### Post by Grey Melon on 2009-10-22
> **thomasaaron said:**
> All of that looks pretty good.

Try playing one of your videos and simultaneously running...
```
top
```...to see if some other process is being a hog.

My "top" results were observed using the following combinations:

1. Play .MTS in vlc [vlc]
2. Play .MTS in Movie Player [totem]
3. Play .mp4 in vlc [vlc]
4. Play .mp4 in Movie Player [totem]

Looking at just the numbers there isn't that much variation. It's either vlc or totem at %105 - %125 and xorg at %50 - %80. The video however is horrible in all combinations except for .mp4 using Movie Player. I can hear the audio in all cases but it is way out of sync in all cases except for .mp4 using Movie Player.

It's too bad that I can't get the .mp4 to get up over 1.00fps in an editing app. Then I'd be able to work.

Seriously I had less hassle back in '96 when I built a system with an $800.00 9gb seagate scsi drive and a very young Adobe Premiere. Took a long *** time to render the 60 second bits I was puting together but I could work and get paid. This is rediculous.

---

### Post by thomasaaron on 2009-10-22
I've not seen this before on our machines, but it sure sounds a lot like this bug...
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/347376](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/347376)

Please make sure that your drop-downs on System > Prefs > Sound are set to Autodetect.

Also, please try removing pulseaudio and see if that straightens it out...
```

sudo apt-get remove pulseaudio
```

If it doesn't, you can reinstall it...
```

sudo apt-get install pulseaudio
```

---

### Post by Grey Melon on 2009-10-22
I removed Pulseaudio and rebooted with no change in the issue.
Reinstalled Pulseaudio from repositories and rebooted with no change in problem.
Installed Pulseaudio 0.9.19 and rebooted with no change.

How can I check the installed version of pulseaudio just to be sure the compile and install were clean?


[edit]
nevermind. the install did not go well so I'm going back to 0.9.15

---

### Post by thomasaaron on 2009-10-23
When you initially installed restricted codecs on your system, did you use the instructions on our wiki? See...

[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

If not, you should try uninstalling whatever you installed and going that route.

We're definitely not seeing this across the board. In fact, I know that we have other Bonobos out there on which people are doing blender work, etc...

I'm doubtful that it is a hardware issue, given your output from glxgears.

Attached is a screenshot of my configuration in...

```
gstreamer-properties
```

Is yours the same?

I might need to advise you to do a re-install, or we can bring it to Denver for a re-install. It's *got* to be some sort of software/configuration issue, but I'm just not sure what it is.

---

### Post by Grey Melon on 2009-10-23
> **thomasaaron said:**
> When you initially installed restricted codecs on your system, did you use the instructions on our wiki? See...

[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

If not, you should try uninstalling whatever you installed and going that route.

We're definitely not seeing this across the board. In fact, I know that we have other Bonobos out there on which people are doing blender work, etc...

I'm doubtful that it is a hardware issue, given your output from glxgears.

Attached is a screenshot of my configuration in...

```
gstreamer-properties
```Is yours the same?

I might need to advise you to do a re-install, or we can bring it to Denver for a re-install. It's *got* to be some sort of software/configuration issue, but I'm just not sure what it is.

Yeah, did all that and my configuration looks the same as yours. I agree with your assessment of the problem and was afraid that I was heading in this direction.

So... aside from backing up files and whatnot to my external drive what can I do to make the re-install as painless as possible?

---

### Post by thomasaaron on 2009-10-23
You can download a CD image for Ubuntu here...
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
...I recommend using 9.04 64-bit.

NOTE: 9.10 is only a week away. You *may* want to just hold out until the 29th and install that instead.

Once you've downloaded the CD image, you will need to burn it to a CD. However, it must be burned as an *image* and not as a *data * CD. Otherwise, it will not be bootable. Instructions for this vary based on which operating system you are using to burn the CD. Instructions for various operating systems are here.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Here are instructions for re-imaging your machine...
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)
...including instructions for downloading, installing and running your System76 driver.

---

### Post by Grey Melon on 2009-10-23
I think I'll wait for 9.10 and repost here with the results

Upgrade or Fresh Install? What are your thoughts?

---

### Post by jbelmonte on 2009-10-23
With the existing problem your system is having, the choice is a fresh install without question.

---

### Post by HotShotDJ on 2009-10-24
> **jbelmonte said:**
> with the existing problem your system is having, the choice is a fresh install without question.+1

---

### Post by Grey Melon on 2009-10-24
I agree with you guys that a fresh install is in order. I guess I was holding out for someone to tell me which magic button to push.

I'll report back in about 5 days. Hopefully with some rendered footage.

Thanks everyone.

---

### Post by HotShotDJ on 2009-10-24
> **Grey Melon said:**
> I guess I was holding out for someone to tell me which magic button to push.
You can try to press the attached button, but I don't think it will help much. ;)

---

### Post by Grey Melon on 2009-10-24
> **HotShotDJ said:**
> You can try to press the attached button, but I don't think it will help much. ;)

It didn't fix the video but I think there's a six pack in the fridge where once was a week old pork loin. That's a gooood button.

---

### Post by Grey Melon on 2009-10-29
Okay I'm very upset now. I installed 9.10 today fresh from cd. The only thing I've done is reload my bookmarks into Firefox, reload my emails and contacts into Evolution and install gstreamer plugins so I could attempt to watch the .mp4's and .MTS's on my laptop's hard drive.

Same crap! I've installed nothing and done virtually nothing. This cannot be right I'm not trying to watch raw IMAX footage here. It's 1920 x 1080 footage from a consumer Canon video camera. Give me a break!

Please, I need some immediate guidance here. It was a challenge to get IT to purchase a Linux laptop as it was. I've been stalling the higher ups with the hopes of a fresh install of 9.10 and now I just look like a idiot. I'm going to be forced into a Windows 7 dual boot if I can't fix this fast.

So where should I start looking? Terminal is open and I'm waiting for something to type in...

Thanks in advance.

---

### Post by Fire_Chief on 2009-10-30
I've not had great luck with desktop stuff (especially multimedia) on 64-bit linux. By chance have you tried the 32-bit version of Ubuntu (any release) to see if this occurs there?

---

### Post by thomasaaron on 2009-10-30
How did you install gstreamer plugins?

All that I've done to be able to watch your videos (and pretty much every other multimedia format) is this...

```
sudo apt-get install ubuntu-restricted-extras
```

[This is one long command]
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list  --output-document=/etc/apt/sources.list.d/medibuntu.list
```

[This is one long command]
```
sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

```
sudo apt-get install libdvdcss2 w64codecs
```

If you used *any* other method, please undo it (remove whatever you installed) and do it this way.

---

### Post by Grey Melon on 2009-10-30
> **thomasaaron said:**
> How did you install gstreamer plugins?

All that I've done to be able to watch your videos (and pretty much every other multimedia format) is this...

```
sudo apt-get install ubuntu-restricted-extras
```[This is one long command]
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list  --output-document=/etc/apt/sources.list.d/medibuntu.list
```[This is one long command]
```
sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
``````
sudo apt-get install libdvdcss2 w64codecs
```If you used *any* other method, please undo it (remove whatever you installed) and do it this way.

After removing the gstreamer stuff I installed and doing the above I get the following error when trying to play an .mp4: "GStreamer encountered a general stream error."

When playing an .MTS I get this: "Internal data flow error."

---

### Post by Grey Melon on 2009-10-30
After the fresh 9.10 install I opened one of the .mp4's and Movie Player wanted to search for the proper codecs for the video. I let it and it installed gstreamer bad or ugly one of those things. The video then began playing and was horrible.

---

### Post by thomasaaron on 2009-10-30
I just tried in Karmic (the first time I tried your videos, I was using Jaunty) after following my instructions above, and it worked great.

My best guess is that the codecs that were automatically installed are conflicting with something.

I did find this...
[http://ubuntuforums.org/showthread.php?t=1048993](http://ubuntuforums.org/showthread.php?t=1048993)

How big is your monitor?

---

### Post by Grey Melon on 2009-10-30
> **thomasaaron said:**
> I just tried in Karmic (the first time I tried your videos, I was using Jaunty) after following my instructions above, and it worked great.

My best guess is that the codecs that were automatically installed are conflicting with something.

I did find this...
[http://ubuntuforums.org/showthread.php?t=1048993](http://ubuntuforums.org/showthread.php?t=1048993)

How big is your monitor?

Monitor resolution is 1920 x 1200 and I think the Bonobo is a 17". At least that what it measures on the diag.

I looked at the link above but I'm having this problem regardless of wrapper.

When I removed gstreamer, in synaptic, I left alone anything that was attached to gnome desktop. But I assumed that that stuff gets installed from the beginning. Is there a way to roll back to fresh without putting the disc in again?

---

### Post by thomasaaron on 2009-10-30
Right. Sorry, I was actually wondering if you were using a large external monitor.

Open Synaptic Package Manger and go to File > History. Find the date that you downloaded the gstreamer packages and see if you can figure out what files were downloaded.

---

### Post by Grey Melon on 2009-10-30
[IMG]http://www.greymelon.com/synaptic_history_01.png[/IMG]> **thomasaaron said:**
> Right. Sorry, I was actually wondering if you were using a large external monitor.

Open Synaptic Package Manger and go to File > History. Find the date that you downloaded the gstreamer packages and see if you can figure out what files were downloaded.

No, I got turned off to multiple monitors until I'm sure the problems are fixed. I've attached a screenshot of initial stuff installed. Gstreamer ugly is there but I removed it earlier and followed your instructions. Any ideas?

---

### Post by thomasaaron on 2009-10-30
I would check to see if *any* of those packages are still installed,and remove them if they are. And then re-run my instructions above.

If that doesn't do it, then I'm not sure what the issue is. I know we've got plenty of Bonobos out there. Perhaps it *is* hardware.

If you want us to bring it in to have a look we can.

---

### Post by Grey Melon on 2009-10-30
> **thomasaaron said:**
> I would check to see if *any* of those packages are still installed,and remove them if they are. And then re-run my instructions above.

If that doesn't do it, then I'm not sure what the issue is. I know we've got plenty of Bonobos out there. Perhaps it *is* hardware.

If you want us to bring it in to have a look we can.

Did the above and no video is playing in Movie Player. I'm going to have to retreat for the weekend and think about what to do next.

Definitely bewildering.

---

### Post by Grey Melon on 2009-10-31
Did a fresh install, again, and the very first thing I did was install ***ubuntu-restricted-extras***, ***libdvdcss2*** and ***w64codecs*** per instructions from post #45.

Video plays again but in the same choppy manner and with no audio sync.

Next I'll install NVIDIA accelerated driver (version 185), reboot and consult the [I]I Ching
[/I]

---

### Post by Groucho Marxist on 2009-10-31
> **HotShotDJ said:**
> I've found Cinelerra to be among the best professional quality video editors out there.  The interface isn't pretty and you'll need to spend some time learning how to use it and getting used to it, but the results have always been perfect for me.

[http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php)

I've also used Kino in the past with mixed results.  The main problem was video/audio syncing... audio and video would become more and more out of sync as resulting video was played.  However, that was over a year ago.  The developers may have gotten this problem sorted now.

I'm using a beefed-up Pangolin performance right now ( 3.07 GB dual core; 8 GB RAM) and from my point of view, the problem is inherent in the software. With all due respect to the open-source community, Kino and Cinelerra are currently prosumer [part professional, part consumer] level video editors. In other words, they do not feature the technical options inherent in, say, an Avid non-linear editing system. Then again, for non-industry (i.e. non cinematic or broadcast) uses, they may get the job done, albeit on a different level of quality.

May I ask what the RPM of your hard drive is? I've found in my experience that anything less than 7200 will not write as quickly and may cause lags that corrupt data. I mention this because I edit HD video, which takes up a ridiculous amount of storage space and time to render.

---

### Post by HotShotDJ on 2009-10-31
> **Groucho Marxist said:**
> With all due respect to the open-source community, Kino and Cinelerra are currently prosumer [part professional, part consumer] level video editors.I suspect the rest of your post was addressed to Grey Melon.  But on the above-quoted section, I must respectfully disagree. Kino is by no means anything other than a consumer (home) video editing suite.  It can do the job for most people, but its feature set is limited to what the "average" home user would want/need.  In fact, it is almost the perfect tool for home-movie editing or creating youtube videos.

However, Cinelerra is a nearly feature-complete, professional video editor/renderer.  Of course, it is NOT something that one might use for feature-length, cinematic movies -- but there are other open source tools that places like Dream Works use to get the job done.  However, Cinelerra is just the tool one would use for professional, HD quality, video editing and rendering for things other than cinematic production.  Not all tasks require top-of-the-line software/hardware.  As with most things, software/hardware does not offer binary choices (good/bad, high-quality/garbage, consumer/professional, etc.) but a full range of choices where the best tool is not necessarily the top-of-the-line tool.

From the rest of your above-referenced post, I know that you have a level of experience in video editing that I lack.  I am curious what features are missing in Cinelerra that are needed to be considered "professional" ?  I just wonder if the lousy and unintuitive user interface design of Cinelerra might have been the issue when you tried it.  It is quite possible that it has certain features that you want, but because of the user interface, they are just difficult to find.  On the other hand, it could be that it really is missing important features that I've never cared about. :)

---

