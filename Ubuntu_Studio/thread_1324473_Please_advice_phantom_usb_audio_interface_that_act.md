---
title: "Please advice: phantom usb audio interface that actually works"
date: 2009-11-12
forum: Ubuntu Studio
---

### Post by JC Cheloven on 2009-11-12
Hi, I know there are a lot of posting on the subject. I've spent many hours reading on. 

Also I do know (almost by memory) alsa's matrix page, and also ffado's one BTW. But I have plenty of bad experiences with supposedly suported audio cards. For a few ones:
- Hammerfall hdsp 9632. 350&#8364;. Mine. "Supported" by alsa, but doesn't work in ubuntu due to pulse audio issues. Had to wipe pulseaudio in jaunty, which is very difficult in karmic. 
- M-Audio Mobile pre. 125&#8364;. "Supported" but didn't work for me. It even wasn't listed with aplay -l. Tried many distros, several computers (of course madfuload), works on windoze...
- Tascam fw1804. 550&#8364;. I had this one before landing in linux. It isn't supposed to be supported, and of course it isn't. No hope. Selling it away because I want to support only gnu-linux (I'm doing this to help other people willing to leave windows, actually). 

Well so far the informative part. Please don't ask me to "have a look" elsewhere. My eyes hurt. What I'd be grateful to know is :
** If you (i.e.: you)
** are currently running  (under karmic, jaunty ...)
** any usb audio interface (not firewire or pci; need usb)
** which are found in the stores now adays
** with 24bit/96KHz, XLR, phantom, 2 channels.

I'd be glad if for example, you could tell about one of those:
EMU Tracker pre (138&#8364;), 
Tascam US 122L (112&#8364;), 
Alesis io2 (133&#8364;), 
Edirol UA25 excw (185&#8364;),
Lexicom Omega (149&#8364;) 

Thanks in advance. I'm stuck, and willing to strike some people who rely on me for this.
JC

---

### Post by AutoStatic on 2009-11-13
Hello JC Cheloven, I have an Edirol UA-25 which is (almost) identical to the UA-25 EXCW. I'm running Jaunty with a 2.6.31-9-rt kernel. Latency is < 4 ms. Runs flawlessly. Sounds pretty good, the pre-amps are ok. I'm using it with phantom powered mics too.

---

### Post by JC Cheloven on 2009-11-13
Hi AutoStatic, thank you :-)

I had actually written in my personal notes "low risk choice" next to Edirol UA25 EXCW. I'd go for the plain UA25, as yours, but it's not sold at major internet stores currently. I wonder if the almost identincal appearance to the UA25 EXCW hides some crucial difference. 
[INDENT]So anybody think I'm paranoid? Well, look at the tascam US 122, it is supported by alsa. Then look at the problems with the newer "version" of the device (named US 122L) [here]("http://ubuntuforums.org/showthread.php?t=753804"), [here]("http://ubuntuforums.org/showthread.php?t=1127282"), [here]("http://ubuntuforums.org/showthread.php?t=1280772"), although in post #4 [here]("http://ubuntuforums.org/showthread.php?t=1059492") it seems to work for someone in an earlier date (??). Actually, it seems that there were [significant hardware changes]("http://www.pps.jussieu.fr/~smimram/tascam/") between both vesions [/INDENT]

I'm also considering M-Audio Fast Track. It is reported to work [here]("http://ubuntuforums.org/showthread.php?t=785052"), in post #4. Although the poster seem to be a bit "off the track" (he bumped a thread inactive since may2008 ), he gave me a useful hint.

Any further experiences?

---

### Post by AutoStatic on 2009-11-14
I wouldn't buy the Tascam US 122L, I get the idea that it should work OOTB but apparently it doesn't. And concerning the M-Audio, are you looking at the Fast Track USB or the Fast Track Pro? If you want to get the max out of the Fast Track Pro you have to compile your own kernel: [http://www.joegiampaoli.com/blog/?p=462](http://www.joegiampaoli.com/blog/?p=462)
And there is a forumite who owns a UA-25 EXCW ([Raboofje]("http://ubuntuforums.org/member.php?u=712909")), maybe you could ask him if it works well.

---

### Post by raboofje on 2009-11-16
> **AutoStatic said:**
> there is a forumite who owns a UA-25 EXCW ([Raboofje]("http://ubuntuforums.org/member.php?u=712909")), maybe you could ask him if it works well.

Indeed I'm quite happy with my UA-25ex - works out-of-the-box in both 'standards-compliant' and 'advanced' modes with reasonably recent kernels.

It's a bit picky about which sample formats it accepts, which can be a nuisance if you want to have your applications talk to it directly through ALSA. 

Personally I always use JACK, so this is not a problem for me - if you want to use it without JACK, I'm sure you can do some ALSA configuration to take care of this, too - haven't tried though.

---

### Post by AutoStatic on 2009-11-16
Same here, I only use it with JACK too. And a happy user also. Besides, the UA-25 comes in a bulletproof shell, I did some parties with it (I'm DJ'ing also every now and then) and I can also confirm it's [s]water[/s]beerproof :)

---

### Post by JC Cheloven on 2009-11-16
Hi, thank you very much, this was the kind of report I was looking for. I din't dare to pm anyone :-)

I ordered today the edirol ua25 excw and an m-audio fast track at thomann. It is unclear at the moment whether both or only one will be given away. It depends on how much I like each one myself :-) Of course both will be widely tested by me anyway ;-) 

I also saw a cheap [focusrite saffire]("http://www.thomann.de/es/focusrite_saffire_firewire_audiointerface.htm"), which is "fully supported" in ffado. I'd go for one, as it could be half-a-replacement for my tascam FW1804, but I want the device to work with a no-firewire laptop. According to ffado's devs, this brand is linux friendly. They send specifications and devices for testing to ffado's. 
Just in case anyone is interested ...
Greetings.

---

### Post by AutoStatic on 2009-11-17
Nice!
As for the Focusrite, I also have a Saffire Pro 10 and it works very well with Ubuntu. Got it from Thomann also. Couldn't update the firmware though on the device so had to sent it back. Luckily Thomann fixed it quickly, so thumbs up for them :)

---

### Post by DancemasterGlenn on 2009-12-06
Hi! I figured I'd chime in and say that the Fast Track (not pro, the new one) has worked well for me in the week I've owned it so far, to a point. I cannot tell you how the phantom power works, as I've only used a dynamic mic, but I will say if it does work, it's quite a ncie little machine. That said, I am having a bit of trouble with it. While it does have two inputs (one xlr and one 1/4 inch), Karmic (vanilla) seems to only see the device as one input (see attached). As such, I haven't been able to record both inputs on separate tracks, which I'd ultimately like to be doing. Is there any way I can fix this on my end, or somewhere I could/should post so that a developer of ubuntu/alsa/pulse/jack/whoever should know about this could lend a hand on the drivers for this device?

---

### Post by eveningshift on 2009-12-06
Hi,

I'm using an [Alesis Multimix 4 USB]("http://www.alesis.com/multimix4usb") with 9.10 Karmic, and it seems to work very well.

I've had to install the Ubuntu Studio packages to get it to work, but once that's done, it does the job.

Thanks,
Shifty

---

### Post by JC Cheloven on 2009-12-14
Hi, I'm coming back to post the result of my shoppings (EDIT:"perfect" is perfect, after extensive testing of every feature):

M-Audio Fast Track. 
Works perfect in karmic. It is an uncomplicated 2 channel device with good specs (48KHz, 24bit). 
@dancemaster: it's ok, you have two mono channels or one stereo. If you record to a stereo track, the mic input will go to to the right and the instrument input to the left (well, or vice versa). No interest in doing such thing, though. You'll want to record both channels to 2 mono tracks in your DAW. I use Traverso, btw.

Cakewalk UA-25 EX.
Works perfect in karmic. I recorded at every supported resolution (up to 96KHz), used midi, etc. The price is worth the diference, perhaps I should have purchased two cakewalks. 

Hammerfall HDSP 9632.
It's pci, not usb, but anyway. It works perfect with ALSA, but there is a problem in how Alsa presents the device to pulseaudio. The result is that it won't work in the presence of PulseAudio. I had to completely remove PulseAudio from my ubuntu studio to get it working. Despite its simple appeareance (which contrasts with the high price), it is the better audio device I own at this moment.

I encourage other people to carry on posting here their first-hand experiences with audio devices, specially those that worked. It will help other people a lot.

---

### Post by maghoxfr on 2010-08-12
Hi, I also have the Alesis Multimix 4 USB (it has phantom power) running OOTB. I haven't tested it fully because my budget didn't allow me to get a condenser mic at the time but everythiung else works fine. It's a really cheap interface with the features of a 4 track mixer. It has two mic preamps, Guitar/line IN and phones OUT with dedicated volume control. I'm pretty satisfied with it.

---

### Post by JC Cheloven on 2010-08-29
> **maghoxfr said:**
> Hi, I also have the Alesis Multimix 4 USB (it has phantom power) running OOTB. I haven't tested it fully because my budget didn't allow me to get a condenser mic at the time but everythiung else works fine. It's a really cheap interface with the features of a 4 track mixer. It has two mic preamps, Guitar/line IN and phones OUT with dedicated volume control. I'm pretty satisfied with it.
Thanks for the input. 
It could be interesting to know if it actually can send 4 simultaneous channels to the computer (the worry is whether it's working as usb2.0 or as usb1.0). 
If you wanna test this, you don't need 4 mics/instruments. A couple of stereo sources (as 2 cd walkmans or similar) and cheap cables for connection will do. 
Please let us know when/if you happen to find out ;)

Cheers
JC

---

### Post by maghoxfr on 2010-08-29
No, I don't think it can record multitrack. i think it can only record one stereo track (or two mono). That's a major drawback, but I want it mainly to record myself or the mix from a bigger mixingboard that my friend's band use.

After using a  while I faced a problem that I don't know how to solve, I haven't contacted alesis for it but maybe I will; the problem is that the alesis sends automatically the mix to the headphones, and there isn't a button that unables that, so when I want to play in rakarrack for example, the rough mix is always there (and always louder than the signal comming from the pc) and I hear the clean guitar (with zero latency) over the processed signal (quiet and with very littel latency, but it's not what I want.

That's why I use the alesis as the input and the integrated sound card as the output, but this has disadvantages such as a lower jack performance.

---

### Post by JC Cheloven on 2010-08-30
> **maghoxfr said:**
> No, I don't think it can record multitrack. i think it can only record one stereo track (or two mono). (...)
I [see]("http://www.thomann.de/es/alesis_multimix_4usb.htm"), it has a plain stereo output. It's USB 1.0 then. Well, it's alright for the price! I asked about this because not many usb 2.0 devices work in linux, and it's always interesting to be aware.

> (...) the problem is that the alesis sends automatically the mix to the headphones, and there isn't a button that unables that
mmmm... the usual behaviour of these devices is to send the signal to the headphones if they are plugged; and send the signal to main out otherwise. No particular enable/disable button. Did you try to unplug the headphones?

JC

---

### Post by maghoxfr on 2010-08-30
>  Did you try to unplug the headphones?
No, because it's the only way I can listen right now, but now that you mention that it sends it WHEN the phones are pluigged, I'll make a cable to hook my stereo to it main out and see what goes on.

Thanks

---

