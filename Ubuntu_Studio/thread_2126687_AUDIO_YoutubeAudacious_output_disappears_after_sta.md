---
title: "AUDIO: Youtube/Audacious output disappears after starting Ardour or Qtractor"
date: 2013-03-17
forum: Ubuntu Studio
---

### Post by #1udancqSHv% on 2013-03-17
Hi all, I'm just trying to get familiar with Ubuntu Studio in the hope of contributing something to the project, but even the basics are giving me a headache at the moment!

Here's the scenario: I find a YouTube video on an audio app I want to learn (Ardour, Qtractor, etc), then start the app, and find that audio on the YouTube video has stopped working. However, if I leave the video playing, and start the app, I get an error message. Here's the error message Qtractor gives me:
 > *"The audio/MIDI engine could not be started. Make sure the JACK audio server (jackd) and/or the ALSA Sequencer kernel module (snd-seq-midi) are up and running and then restart the session."*
Once I get audio working in Ardour or Qtractor, I then can't hear any in video (online or native files) or listen to ogg/mp3s via Audacious.

I've tried searching for a solution but the closest I got was this, and a solution isn't really offered:
[http://ubuntuforums.org/showthread.php?t=2118762](http://ubuntuforums.org/showthread.php?t=2118762)

I also found this thread;
[http://ubuntuforums.org/showthread.php?t=1418391](http://ubuntuforums.org/showthread.php?t=1418391)
...but the solutions offered make me nervous, as there is not mention of the type of specialist audio software used in Ubuntu Studio. I'm worried that reinstalling pulseaudio/libasound2 and/or hacking audio conf files will only end badly for Ardour/Qtractor and the other apps I have installed such as Renoise and energyXT. Audio on Linux seems a bit of a minefield right now, takes me back to the bad old days of pro-audio on Windows (yes, there is such a thing!). I want to get to grips with this and understand how the bits of the jigsaw all fit together. Maybe then there's a slim chance that one day I'll actually be able to contribute something back...

I'm running Ubuntu Studio 12.10 64bit on a Toshiba P850-321 using onboard Realtek ALC280Q-GR audio hardware (I haven't even started trying to get this lot working with my UCA202 yet!!).

Any help and guidance with this _**very**_ gratefully received!! :D

---

### Post by BlinkinCat on 2013-03-17
Hi,

Not sure if the pages on Ubuntu Studio in the NewDocs link in my signature will be of any help.

Cheers - :)

---

### Post by #1udancqSHv% on 2013-03-17
Thanks BlinkinCat! I'm just having a look now (my handicap being that I probably don't know the right terms to search by). Looks like a fantastic resource anyway, though - I've bookmarked and will be working my way through the docs....

---

### Post by #1udancqSHv% on 2013-03-17
Wow, there's a lot of info in those docs, BlinkingCat! OK, can't spend any more hours on this tonight, need to sleep and get up  for work tomorrow... will have to try to pick this up again as and when I  get chance, hopefully this week. Sigh - ah well... every time I think I might be about to start understanding how audio works on Linux, I just end up realising the ever-increasing enormity of the task. :(

---

### Post by BlinkinCat on 2013-03-17
> **jfj33 said:**
> Wow, there's a lot of info in those docs, BlinkingCat! OK, can't spend any more hours on this tonight, need to sleep and get up  for work tomorrow... will have to try to pick this up again as and when I  get chance, hopefully this week. Sigh - ah well... every time I think I might be about to start understanding how audio works on Linux, I just end up realising the ever-increasing enormity of the task. :(

You don't know how pleased I am that NewDocs has been of benefit to you,

Hope you get it all sorted out.

Cheers - :p

---

### Post by tgalati4 on 2013-03-18
Understand that Ubuntu Studio is for production work and if you are trying to produce a sound track using Ardour and watch a video at the same time--that will be problematic.  It's not that you can't do it, it's just that the Studio setup is not designed for that use case.  It would be better to have a laptop playing the tutorial that you want to watch and have the desktop running Studio with the application that you want to learn.  Because of the real-time nature of sound editing, you can't have two sound apps running at the same time.  (You can, but you may not get sound out of one of them.)

Of course, you will quickly discover this after reading a few pages of [NewDocs]("http://help.ubuntu.com/community/NewDocs").

---

### Post by jejeman on 2013-03-18
Download video and play it in JACK aware video player. (e.g. VLC)

---

### Post by #1udancqSHv% on 2013-03-18
> **BlinkinCat said:**
> You don't know how pleased I am that NewDocs has been of benefit to you,

Hope you get it all sorted out.

Cheers - :p

You're welcome - you've done a great job, praise where praise is due. :)

---

### Post by #1udancqSHv% on 2013-03-18
> **tgalati4 said:**
> Understand that Ubuntu Studio is for production  work and if you are trying to produce a sound track using Ardour and  watch a video at the same time--that will be problematic.  It's not that  you can't do it, it's just that the Studio setup is not designed for  that use case.  It would be better to have a laptop playing the tutorial  that you want to watch and have the desktop running Studio with the  application that you want to learn.  Because of the real-time nature of  sound editing, you can't have two sound apps running at the same time.   (You can, but you may not get sound out of one of them.)

Of course, you will quickly discover this after reading a few pages of [NewDocs]("http://help.ubuntu.com/community/NewDocs").

Hi tgalati, thanks for your response. I do fully understand the purpose of Ubuntu Studio (I installed it because I recognise its advantages and potential), but the simple fact is that watching a video online whilst running pro audio software is something that 'creative humans' can do in both Windows and OSX. I've managed to move the rest of my work and play into Linux 100%, the only area where I can't quite replicate my workflow yet is in audio production - that's why I want to get involved in the Ubuntu Studio project. It's a fantastic distro and I do genuinely love it, but much as it pains me to say so, I don't yet feel that it's a credible alternative to using Windows or Mac for most pro audio tasks. (I don't think it's that far off though, and it's catching up fast!) I'm aware of some who are managing just fine though, of course.

The desktop/laptop combo is one I've considered, but not possible right now as I'm 'confined to quarters' recovering from surgery, so I'm limited to laptop only. Even so, it's a workaround rather than a solution - I'd like to see (and when my skills have improved, hopefully contribute towards) a forward-looking solution that enables pro audio and std audio to get along. There are any number of scenarios where this would be of benefit. I produced library and commissioned audio, and to replicate my Windows workflow I need to be able to quickly learn how to use new and unfamiliar tools on the fly, with online video tutorials aften being an ideal means of doing so. I then close down YouTube and get down to the real work.

To take it to extremes, imagine Ophir Kutiel (Kutiman) attempting to produce the ThruYou series using the tools available in Ubuntu Studio, or any other Linux distro. Possible? Certainly, but the workflow would undoubtably be haphazard and frustrating. Please, please understand that I'm not slating Ubuntu Studio, I'm a huge fan and an advocate, even after a relatively short time using it. However, I do feel I need to point out that being able to replicate a task that other operating systems can handle without much difficulty may be advantageous in Ubuntu Studio/Dream Studio/any other Linux distro as well - to the audio pro as much as the amateur/beginner. Just food for thought...

Maybe I'm also the fool who doesn't accept a situation as it currently is, and wants to strive for a better way ;)  It doesn't exactly make for an easy life, I know!


> **jejeman said:**
> Download video and play it in JACK aware video player. (e.g. VLC)

Nice solution - I hadn't even thought of that. Thanks jejeman!

---

### Post by #1udancqSHv% on 2013-03-20
> **BlinkinCat said:**
> You don't know how pleased I am that NewDocs has been of benefit to you,

Hope you get it all sorted out.

Cheers - :p

UPDATE: I'm really finding this feature very useful, for Ubuntu Studio  and for my vanilla Ubuntu installation too (I have Ubuntu 12.04 installed  alongside multibooting with Win7 as an environment to learn about development/programming languages, bash etc,  and tinker under the Ubuntu hood without risk of stuffing up my Ubuntu  Studio installation). Thanks for this, it makes the wiki a lot easier to  navigate - great work.

---

### Post by BlinkinCat on 2013-03-20
> **jfj33 said:**
> UPDATE: I'm really finding this feature very useful, for Ubuntu Studio  and for my vanilla Ubuntu installation too (I have Ubuntu 12.04 installed  alongside multibooting with Win7 as an environment to learn about development/programming languages, bash etc,  and tinker under the Ubuntu hood without risk of stuffing up my Ubuntu  Studio installation). Thanks for this, it makes the wiki a lot easier to  navigate - great work.

Hi jfj33,

If you are referring to my putting you on to NewDocs, the pleasure is all mine.

Cheers - :)

---

### Post by jejeman on 2013-03-20
I use this configuration for the firewire card to overcome the problem you addressed
```
pcm.rawjack {
    type jack
    playback_ports {
        0 system:playback_1
        1 system:playback_2
    }
    capture_ports {
        0 system:capture_1
        1 system:capture_2
    }
}

pcm.jack {
    type plug
    slave { pcm "rawjack" }
    hint {
        description "JACK Audio Connection Kit"
    }
}

ctl.mixer0 {
type hw
card 0
}

pcm.!default {
    type plug
    slave { pcm "rawjack" }
}
```You can put the above code to the: ~/.asoundrc
And try it out.
I haven't tested it with ALSA soundcard.
If it doesn't work, try to reboot. If you wan't to disable it - erase or rename the file.
What it does - it creates automaticly ALSA audio ports in running JACK server. So, if you play youtube video it will connect flashplayer to JACK outputs.
One thing I notice is that it doesn't "like" RT or lowlatency. So, I made a separate JACK configuration for playback with no RT and 64ms latency.

---

### Post by tgalati4 on 2013-03-20
jejeman describes what I was talking about.  You can do it, but it requires some configuration.  You only have one sound chip on a laptop.  In a desktop rig, you can have firewire sound devices, motherboard sound, M-Audio PCI soundcards, USB sound cards, and you can get them all to work (well, most of them) at near real time.  A laptop sound chip will just puke when trying to perform realtime sound mixing AND pipe in a youtube soundtrack streaming from the web.  Not to mention that the Southbridge Chip handles both sound and ethernet at the same time.  jejeman struck a compromise, by allowing moderate latency (64ms) on playback.  At 300ms latency, you can't monitor yourself talking into a microphone.  Try it.  [http://www.thedailyactivist.com/science-and-tech-speechjammer/](http://www.thedailyactivist.com/science-and-tech-speechjammer/)

I would like to know how Mac and Windows tools get around these simple facts.

---

### Post by #1udancqSHv% on 2013-03-21
> **jejeman said:**
> 
I haven't tested it with ALSA soundcard.
If it doesn't work, try to reboot. If you wan't to disable it - erase or rename the file.
What it does - it creates automaticly ALSA audio ports in running JACK server. So, if you play youtube video it will connect flashplayer to JACK outputs.
One thing I notice is that it doesn't "like" RT or lowlatency. So, I made a separate JACK configuration for playback with no RT and 64ms latency.
Thanks jejeman, I'll give that a try tonight when I'll hopefully get chance to have another play on Ubuntu Studio. I think for the purposes of following along with a YouTube tutorial, 64ms latency is fine. Thanks for your help!

---

### Post by #1udancqSHv% on 2013-03-21
> **tgalati4 said:**
> jejeman describes what I was talking about.  You can do it, but it requires some configuration.  You only have one sound chip on a laptop.  In a desktop rig, you can have firewire sound devices, motherboard sound, M-Audio PCI soundcards, USB sound cards, and you can get them all to work (well, most of them) at near real time.  A laptop sound chip will just puke when trying to perform realtime sound mixing AND pipe in a youtube soundtrack streaming from the web.  Not to mention that the Southbridge Chip handles both sound and ethernet at the same time.  jejeman struck a compromise, by allowing moderate latency (64ms) on playpack.  At 300ms latency, you can't monitor yourself talking into a microphone.  Try it.  [http://www.thedailyactivist.com/science-and-tech-speechjammer/](http://www.thedailyactivist.com/science-and-tech-speechjammer/)

I would like to know how Mac and Windows tools get around these simple facts.

Ha! That link's brilliant, the video's hilarious - thanks for sharing that! I remember first installing Cubase VST 3.5 all those years ago and being horrified at the latency, about 6-700ms IIRC, until I upgraded my soundcard and tweaked the ASIO drivers. It feels a lot longer ago than fifteen years!

Anyway, to be honest, I can't tell you how they (specifically Windows) gets round this, but that's sort of the point - I don't need to know, it just works. I can appreciate and love that one of the many benefits of Linux is that you can get under the hood and hack to your heart's content, but for the purposes of pro audio on Linux, that's not just an option, it's a requirement. From a pro-musician's perspective, you just need to be able to boot up and be productive from the outset, and Linux isn't quite there yet. If Linux is ever going to be taken seriously as a pro audio platform (more than just by the outliers and hobbyists), it needs to be easy to just start up a DAW and get working, with out having to connect up lots of individual modules. I realise that's 'the Linux way', but if you try to persuade most studio engineers that to do that for each recording session, they'll laugh you out of the building. If I'm wrong on that, please feel free to set me straight, but that's certainly my perception.


Back to the specific subject of the post, though. Just to clarify, what I'm trying to achieve here is not realtime sound mixing and watching YouTube at the same time - in Windows if I need to record an acoustic instrument on my laptop, I'd connect my UCA202, use ASIO drivers, set the latency to 256 buffers or lower (which gives me 10ms latency in Ableton Live), and hit record. But if I'm following a YouTube tutorial, I can still get 20ms latency playing a VSTi synth with my USB MIDI keyboard using the onboard audio and stock drivers.

Now believe me, I can't really express how much I hate the idea of giving MS and Windows any credit whatsoever (!!), but I haven't yet found a way to replicate this performance using Linux. I would be over the moon to know that I could wipe my Windows 7 partition altogether, but audio production is currently the only thing stopping me doing so.

However, that's part of what's motivating me to get involved and contribute to the Ubuntu Studio project and the wider Linux/GNU/FOSS community, mainly just by donating so far, but hopefully soon by making myself useful on projects too! The more of us there are helping out, the greater the chance that pro audio capability and ease of use on Linux will not only catch up with Mac and Windows, but surpass them, sooner rather than later. I'd really like to see that happen.

---

### Post by tgalati4 on 2013-03-21
How would you do this in Windows?

```
sudo apt-get install sox

play "|rec -d delay 0.300"

play "|rec -d pitch -200" 
```

The first command delays your speech by 300 ms.  The second lowers your pitch by 2 semitones.  Works best with headphones.  You may have to fiddle with the built-in microphone gain.

I agree with your comments.  Linux is not widely used in professional music production and it is not easy to set up and use.

---

### Post by #1udancqSHv% on 2013-03-21
Hehe, thanks for that, fun to play with :D

> **tgalati4 said:**
> I agree with your comments.  Linux is not widely used in professional  music production and it is not easy to set up and use.
I have high hopes for the future though...

---

### Post by CraigPid on 2013-03-21
I think this is much simpler than everyone is making this.I think the original issue was that when you were starting Ardour you were not getting youtube playback.When Jack starts it takes over your soundcard so Pulseaudio can't access it.In Ubuntu studio, when you start Qjackctrl,you will see Pulseaudio sink in your inputs side & they should be connected up to your outputs.So when you lose your youtube playback or whatever app, click your volume control icon and click sound settings and look for your app.I think youtube in firefox would say plugin container.Then click the dropdown for the output of that app & select pulseaudio jacksink.Sorry if this isn't that clear as I'm not at my home computer right now.
There's even a possibly easier way to deal with this on this page
[https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro)
You could set pulseaudio jack sink as a fallback device in your sound settings.When your app can't make the connection to pulseaudio it will fall back to jack sink.
By the way...in my version of Audacious in Ubuntu Studio you can go into the prefs and set jack as your output rather thatn pulseaudio.Anyway there is no issue here except maybe a couple clicks here and there to set things up properly.
Craig

---

### Post by jejeman on 2013-03-22
I have overlooked that he was asking about Audacious. Yes, Audacious is JACK aware application. He can switch the audio output settings to JACK, but then he will complain how he need to switch it back to ALSA when not using JACK. ;)

Pulseaudio JACK sink never worked for me.

---

### Post by CraigPid on 2013-03-22
I think the trick is that you have to set the output of that app to jacksink in the sound settings.Even though the connections are made in the jack connections window, the application is still outputting to pulseaudio in the sound settings until you switch it.Normally I keep DBus disabled in Jack so that PAsink doesn't appear.I find it annoying & distracting to have all those extra connections when you're trying to route the audio for the programs that you're using.That said though, once I realized how to work it, I've never had a problem getting YouTube to play through JackSink if I wanted to use it.
  Craig

---

