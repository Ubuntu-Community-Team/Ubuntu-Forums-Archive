---
title: "Some fairly newb-like questions about JACK."
date: 2010-02-27
forum: Ubuntu Studio
---

### Post by hxcobd on 2010-02-27
Running Renoise as I've done for a few years now, but I'm making the jump from ALSA to JACK.

So far, I've got it set up fine, running Realtime, playing through my USB interface. All is well, it sounds great, etc.

However, when either the CPU usage or RT usage percentage hits 100%, Renoise freezes, understandably. (I'm assuming it's JACK's RT % that's causing this and not Renoise, as I disabled CPU overload handling.)

Is there a really good way to remedy this? I increased the client timeout as suggested by Renoise, but this doesn't really seem like a "fix" to me.

I'm not OVERLY concerned about having amazing latency, as I don't use MIDI input or anything; I work entirely with output, basically.

It would stand to logic, to me, that the solution is going to have to be trading latency for stability, just like in Windows, right?

---

### Post by hxcobd on 2010-02-27
I tweaked some settings in JACK:

Frames/Period (Buffer): 1024
Timeout (msec): 2000
left Output Latency on 0

I have Realtime and Force 16-bit enabled.

Now, after running one of the Renoise demo songs for a while, the CPU usage obviously goes up as more instruments/samples are being played. When it gets near/hits 100%, JACK displays this:

22:32:22.698 XRUN callback (1).
**** alsa_pcm: xrun of at least 1.523 msecs
**** alsa_pcm: xrun of at least 1.573 msecs
**** alsa_pcm: xrun of at least 1.548 msecs
**** alsa_pcm: xrun of at least 1.537 msecs
**** alsa_pcm: xrun of at least 1.704 msecs
**** alsa_pcm: xrun of at least 1.325 msecs
**** alsa_pcm: xrun of at least 1.574 msecs
**** alsa_pcm: xrun of at least 0.823 msecs
**** alsa_pcm: xrun of at least 0.720 msecs
**** alsa_pcm: xrun of at least 0.653 msecs
**** alsa_pcm: xrun of at least 0.427 msecs
**** alsa_pcm: xrun of at least 1.371 msecs
**** alsa_pcm: xrun of at least 1.405 msecs
**** alsa_pcm: xrun of at least 1.582 msecs
**** alsa_pcm: xrun of at least 1.509 msecs
**** alsa_pcm: xrun of at least 1.746 msecs
**** alsa_pcm: xrun of at least 1.481 msecs
**** alsa_pcm: xrun of at least 1.744 msecs
**** alsa_pcm: xrun of at least 1.802 msecs
**** alsa_pcm: xrun of at least 1.547 msecs
**** alsa_pcm: xrun of at least 1.165 msecs
**** alsa_pcm: xrun of at least 1.554 msecs

And repeats this cycle, more or less, until audio stops playing entirely, and then displays this:

22:32:42.344 XRUN callback (172).
delay of 776.000 usecs exceeds estimated spare time of 638.000; restart ...
delay of 760.000 usecs exceeds estimated spare time of 638.000; restart ...
delay of 790.000 usecs exceeds estimated spare time of 638.000; restart ...

And that message is repeated ad nauseum until either Renoise or JACK crashes. (Appears to be Renoise crashing.)

Thoughts?

---

### Post by hxcobd on 2010-02-27
Oh, I should also note that even if I bypass JACK entirely and simply use ALSA output through Renoise, CPU usage still skyrockets and audio becomes incredibly choppy at the same point in the song that it does with JACK output.

Could this be an issue with using Realtime priority?

---

### Post by AutoStatic on 2010-02-28
Hello hxcobd, did you disable CPU frequency scaling? And what kind of USB device are you using? It probably doesn't need the Force 16-bit option. And what are your other JACK settings?

---

### Post by hxcobd on 2010-02-28
> **AutoStatic said:**
> Hello hxcobd, did you disable CPU frequency scaling? And what kind of USB device are you using? It probably doesn't need the Force 16-bit option. And what are your other JACK settings?

I do not know what CPU frequency scaling is, so I'm guessing I didn't disable it.

The USB audio interface is a Behringer UCA200. It works perfectly for everything I've used it for in linux so far, so I'm pretty sure it's well-supported in Ubuntu.

Here's a screenshot of my current settings. With these settings, I'm still getting the Renoise crash after about a minute of playback of the song. (Not to mention 256 buffer seems quite a bit higher than I've seen other users using through RT JACK.)

I do have a Realtime kernel installed and my limits.conf has been properly edited, I believe.

[http://img64.imageshack.us/img64/1227/11448096.jpg]("http://img64.imageshack.us/img64/1227/11448096.jpg")

---

### Post by AutoStatic on 2010-03-01
> **hxcobd said:**
> I do not know what CPU frequency scaling is, so I'm guessing I didn't disable it.The fastest way to find out is to add the CPU frequency scaling applet to your panel (right-click on panel - Add to Panel - CPU Frequency Scaling Monitor). If it says 'CPU frequency scaling not supported' then your CPU doesn't scale. If the applet starts without any warnings your CPU does scale and then it's best to set it to 'Performance'. This will prevent your CPU from scaling up or down.

> **hxcobd said:**
> The USB audio interface is a Behringer UCA200. It works perfectly for everything I've used it for in linux so far, so I'm pretty sure it's well-supported in Ubuntu.If it worked before it should work properly now too.

> **hxcobd said:**
> Here's a screenshot of my current settings. With these settings, I'm still getting the Renoise crash after about a minute of playback of the song. (Not to mention 256 buffer seems quite a bit higher than I've seen other users using through RT JACK.)

I do have a Realtime kernel installed and my limits.conf has been properly edited, I believe.Looks good. But it isn't a duplex device? And why did you set the number of ports? And 256 is a bit high, I can work at 64. And do you also have problems with other applications and JACK? Also because you're mentioning that CPU load is steadily increasing. There are no known Renoise bugs concerning this issue?

---

### Post by rixtr66 on 2010-03-01
i am interested to see where this thread goes as i have a similar
problem w/renoise.my cpu load only goes to 30% but after about 30
seconds of playing a demo song renoise freezes.
this was on 2.5rc2 and 2.1 so im not sure where the problem lies.
i too have tried it on alsa(bad latency)and jack,running an rt kernel.im wondering if it isnt the rt kernel and renoise not getting along,ill test it on the generic kernel and get back to you.hopefully someone will have an answer.
Rick :guitar:

---

### Post by rixtr66 on 2010-03-01
ok i tested renoise 2.1 on the generic kernel of karmic.
my results are that i did not get any freeze ups!BUT
i tested with the song by hunz,soon soon.it played but the latency
was horrible.no matter how high i went with the frames/period.
anyway it didnt freeze,but the cpu went higher on the generic kernel.70%thats pretty high.so my conclusion is that something
is going on w/renoise and the rt kernel.i may be wrong!but it doesnt freeze on the generic kernel.but has atrocious latency????
i dont know enough about this to offer any help,but maybe someone out there has an answer.dont mean to hijack the thread,i just want to be helpfull and get some answers for us!!!
Rick :guitar:

---

### Post by hxcobd on 2010-03-01
Hey Rick, no worries about a possible thread hijacking; I'm open to all ideas and other users' problems as well; I'd like to get this solved and get a better grasp on JACK/RT as well as Renoise!

I ended up making a thread directly on the Renoise forums that you guys might want to have a look at:

[http://www.renoise.com/board/index.php?showtopic=24414]("http://www.renoise.com/board/index.php?showtopic=24414")

The consensus with my particular problem seems to be that my CPU is simply inadequate for some of the Renoise demo songs, as they can be quite CPU-intensive and involve many DSP effects.

I'm somewhat reluctant to accept this reasoning, as to me, a Pentium-M Centrino 1.6ghz seems more than adequate for a tracker-type DAW, but I suppose I could be wrong.

I've made some modifications to JACK and added the CPU frequency widget (and changed it to Performance) as you mentioned, Static. Will post any results.

---

### Post by hxcobd on 2010-03-01
> **AutoStatic said:**
> 

Looks good. But it isn't a duplex device? And why did you set the number of ports? And 256 is a bit high, I can work at 64. And do you also have problems with other applications and JACK? Also because you're mentioning that CPU load is steadily increasing. There are no known Renoise bugs concerning this issue?

Yes, it is a duplex device, but I don't use any input/recording features, so I switched it to solely playback for simplicity's sake.

Yes, 256 is rather high for my tastes as well, but I couldn't get stable playback on any lower setting.

I did not set the maximum port number either; that was at 256 by default.

---

### Post by hxcobd on 2010-03-01
Oh my god, Static, I think you solved my issue!

I kept my JACK settings virtually the same, but turned on the CPU frequency monitor and left it on Performance... And my CPU usage in Renoise isn't going over 50% or so now, even when the demo song hits the REALLY heavy DSP parts!

I am enthralled... Going to do some more testing...

---

### Post by hxcobd on 2010-03-01
Static, I could kiss you right now.

CPU frequency/scaling is absolutely the solution for my problem. With it set on Performance (which leaves it on 100%), I can play every demo song I've tried with no stuttering or freezes. The highest CPU usage I got in Renoise was on the Hunz song, which peaked at about 65%.

When I switched CPU scaling to "Conservative," Renoise crashed within about 10 seconds, ha!

I'm chalking it up to that being the issue.

Static, if you (or anyone else) has any general, non-Renoise-related system tweaks to further enhance my performance, especially in audio programs, I'd love to hear them!

---

### Post by hxcobd on 2010-03-01
Think I've found a configuration that allows for absolutely error-less playback.

in JACK:
- Realtime activated
- 256 frames/sec (slightly slow, but keep in mind, I only need playback, not recording or MIDI at all)
- sample rate: 44100
- periods/buffer: 3
- timeout: 1000 or higher
- output channels: 2

Getting absolutely no stutters or JACK errors at all, during any points in playback through Renoise. With the slightly slower buffer and sample rate, my CPU peak dropped to 55% in the Hunz song mentioned.

I'm just stoked. I'd never be able to get latencies this low in Windows; the lowest I ever got with ASIO was 512, and that was with MAJOR tweaking. I can get it down to 128 in Ubuntu here with no errors, but for the sake of saving some CPU, 256 is a good middle ground.

I should add that this Hunz song uses a grand total of 74 DSP effects units. Yes, I counted. Chances of a Windows machine handling that many sheer effects on my underpowered machine? 0%.

None of the tracks are frozen/bounced, either.

---

### Post by rixtr66 on 2010-03-01
congrats!glad you got it worked out.
unfortunately i dont have freq.scaling :(although i do have 2ghz
processor....but the high cpu wasnt my problem,it was crashing after 30 sec. or so on the rt kernel?hmm...strange..i dont have this problem w/renoise on win7..but this is a weak machine.
acer aspire 5315,2ghz celeron,2gbram,320gbhd.perhaps my jack settings are faulty.ill set jack to your settings and see what happens.maybe my machine isnt cut out for this on linux?
will test some more.
Rick :guitar:

---

### Post by rixtr66 on 2010-03-01
well good news!!like you i have renoise/jack rt working flawlessly!
thanks to your renoise thread i picked up on taktik's response about the timout settings.so i bumped up the timeout to 2000 ms
and set the buffer to 3 and that solved the problem.
so the solution for me was to properly set up jack!
who would have thunk it:p thanx for the thread and the suggestions!
its nice to meet a fellow renoiser on ubuntu ;)
cheers!
Rick :guitar:

---

### Post by AutoStatic on 2010-03-01
> **hxcobd said:**
> Static, I could kiss you right now.Glad I could help!

> **hxcobd said:**
> Static, if you (or anyone else) has any general, non-Renoise-related system tweaks to further enhance my performance, especially in audio programs, I'd love to hear them!
You could tweak your system even further with the help of [rtirq]("http://ubuntuforums.org/showthread.php?t=1328175http://ubuntuforums.org/showthread.php?t=1328175") (it works for USB and onboard devices too, not just Firewire) and the [realTimeConfigQuickScan]("http://realtimeconfigquickscan.googlecode.com/hg/realTimeConfigQuickScan.pl") could give you some pointers. And maybe take a read at [http://wiki.linuxmusicians.com/doku.php?id=system_configuration](http://wiki.linuxmusicians.com/doku.php?id=system_configuration)

Best,

Jeremy

---

### Post by hxcobd on 2010-03-01
Yeah rix, I've read that for some reason, without increasing the timeout, Renoise disconnects from JACK fairly frequently... I couldn't for the life of me figure out why it would do this, but apparently every linux user has to increase the timeout for this reason.

Increasing the timeout doesn't seem to hurt anything, though, so yeah.

Will scope out the links, static, thanks!

---

### Post by hxcobd on 2010-03-01
Static, good tip on scoping out the system tweaks for multimedia production.

That realTimeQuickConfigScan is a wonderful little tool. Some tips on it, though:

The tool itself is a bit outdated now (think it's from early 2009 or so?), so some of the tweaks are unnecessary.

- The TMPFS tweak is arguably not that useful, as Ubuntu now uses EXT4 rather than EXT3, and performs better in general.

- NOATIME is a good tweak, especially for older computers, and really easy to implement.

- The /dev/rtc tweak was (supposedly) a Ubuntu bug and was solved with an update long ago.

The rest are handy, and while they might not even result in noticeable changes on the user's end, they're worth doing.

(Little tip for linux newbs as well: to run a Perl shell script, type

perl ./realTimeQuickConfigScan.pl

from a Terminal line.)

---

### Post by AutoStatic on 2010-03-02
> **hxcobd said:**
> The tool itself is a bit outdated now (think it's from early 2009 or so?)It is still being maintained by a [forumite]("http://ubuntuforums.org/member.php?u=712909").

> **hxcobd said:**
> - The TMPFS tweak is arguably not that useful, as Ubuntu now uses EXT4 rather than EXT3, and performs better in general.It is indeed not useful, also for another reason, jackd uses */dev/shm *afaik nowadays. So this tweak is indeed deprecated.

> **hxcobd said:**
> - NOATIME is a good tweak, especially for older computers, and really easy to implement.It is, I checked with **latencytop** recently and setting atime can cause extra latency.

> **hxcobd said:**
> - The /dev/rtc tweak was (supposedly) a Ubuntu bug and was solved with an update long ago.Yeah, I vaguely recall that, but didn't that have something to do with a symlink to */dev/rtc0*?

---

### Post by hxcobd on 2010-03-03
Static (or others),

Any idea why my sound playback would be randomly cutting out ever since doing the series of audio tweaks?

I've had the same issue with Decibel Audio Player, VLC, and even the Myspace audio player; audio will play as normal for an unspecified amount of time, and then just randomly, it will cut out, as though I hit a "Stop" button or something.

Doesn't seem to be a real cause for it and no error is produced anywhere. If I just hit "Play" on the media player, audio will work fine again.

Super weird. Are any of the aforementioned tweaks known for causing unstable playback outside of JACK?

---

### Post by AutoStatic on 2010-03-04
My guess is that this is a PulseAudio issue. Did you do anything to get a grip on PulseAudio? What happens seems like PulseAudio dies or gets killed and doesn't respawn, maybe because of a *~/.pulse/client.conf* file you've created. But I'm not sure. Maybe you don't use PulseAudio at all.

---

### Post by hxcobd on 2010-03-04
I do use Pulseaudio, but I don't recall specifically tweaking Pulse in any way, shape, or form.

Moreover, I have no .pulse/client.conf config files at all.

Hmmmmm.

---

### Post by AutoStatic on 2010-03-05
And do you have these problems with the generic or the rt kernel? What you could do is try running PulseAudio in a terminal from the CLI and then add the option -vvv to it for extra verbosity. The only problem is that PulseAudio respawns automatically if you kill it so if you don't have a client.conf you could create it, it should contain a single line:
```
autospawn = no
```

As soon as an app chokes on something you should see that reflected in the output of **pulseaudio -vvv**

---

