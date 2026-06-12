---
title: "using Seq24 with wine midi problem(for live performance) one last hitch"
date: 2009-07-14
forum: Ubuntu Studio
---

### Post by triplesquarednine on 2009-07-14
hello everyone,

i finally managed to join the forums... i am not new to ubuntu, multimedia production,
wine/wineasio. . . but i haven't had too much luck solving a semi-large issue i am having...

i have all the goodies working in "top" form. jack 1.9.2 - almost zero Xruns, very low latency 2.67msecs, my own custom-rt kernel, wineASIO, my best plugins - all working great ;) ! all the best linux audio apps - ardour 3.0, seq24, LV2 etc..

now, this is my problem,

basically, i am looking to use seq24 for live performance, using VST(non-native/wine) funforuntetly, i can't stop using these plugins, as linux has a few years before our native plugins are going to be upto to job, and of a high enough quality for production...

anyway, i cannot use "snd-virmidi", which is a "midi loopback driver" in alsa(it allows inter-application midi) - as it doesn't work with non-native VST's, or with wine at all(i use native instruments - battery+massive+fm8(standalone wine apps). i should add that you can connect them - wine apps see virmidi, there just isn't any data sent when connected...

i can use the midithru and everything works fine, however not all of the plugins i use
allow you to easily specify which channel you are using. as they use "omni" settings.
other than battery3 which i can specify each "cell" - a single drumpad, to use whatever channel 1-16 of the miditru. this is a big pain/hassle to do(when i already have a ton of drumkits/presets). and doesn't solve my problem even if i did change every preset...
i still can't sequence more than one in seq24. as they would be using miditru... :(

so i am looking for an alternative to virmidi which will allow me to be able to sequence more than just one plugin at a time in seq24....

right now, i sequence drums/samples/loops in seq24 from battery3, can manipulate them live(flawless sound/clock-timing) and use my keyboard with massive(a synth), patch it thru sooperlooper(work's like a Kaosillator) and use this all on the fly....

(for more info on what a kaossilator does:
                    [http://www.youtube.com/user/triplesquarednine](http://www.youtube.com/user/triplesquarednine)  )

       just watch a video of mine, or two! :)

however, it would be really nice to be able sequence some of my synth/basslines in seq24. as i can write more complex, structured music(and use it in live mode). taking the pressure away from my keyboard, so i can free up my hands and mind a little bit....

think ableton live/with a multitrack-looping kaossilator(i...
it is already pretty awesome, but to make it really worthwhile, i need to able to
sequence some of these synths....i only have to hands, and i am a singer/mc, so
i need to be able to free myself to sing/rap, and not have to constantly be looping new basslines and leads, as it's a bit too much at once....

any ideas, for a workaround or fix that will allow this???

any help or insight would be greatly appreciated....

i am planning to build a rackmount linux system(based on ubuntu),
with a touch display(gui) for playing live, for both by myself(dj/lyrics) and
with the guys i jam with...so i gotta figure this out!

thanx again, in advance :)

PS:ubuntu is the best, and linux in general!

EDIT: fixed! i re-installed wine and audio related things, also did some updates on my system
and now everything works perfectly....although i don't know what exactly fixed the problem...

---

