---
title: "real audio latency"
date: 2010-11-08
forum: Ubuntu Studio
---

### Post by bluesscream on 2010-11-08
I often read&talk about audio latencies  w/o information about convincing experiences or comparing test results. Qjackctl/configuration/latency shows something calculated, not measured. So I made up a skinny setting with a short patchcable; you can do it analogously in any jack-compliant full duplex enabled audio software.
Only if you actually have no sensational musical inspirations do this:

Connect your device's MicIn 1 and LineOut 1 physically with a patchcable
disconnect all speakers for the benefit of your ears
synchronize interface's samplerate if there is such a knob
with jack's same samplerate, set jack's  2 or 3 buffers, midrange frames/period.
start Ardour
enable display mi:sec in Ardour
delete track Master
create track Audio 1 mono
goto jack connections
disconnect all 
connect Ardour click/out 1 --> Audio 1/in1
goto Ardour, enable Click 
activate record at Audio 1 
record 10 seconds
disconnect click/out 1 from Audio 1/in1
in Ardour create track Audio 2 mono
connect Audio 1/out 1 --> dev0_LineOut 1+2 left_out
connect dev0_MicIn1 left_in --> Audio 2/in1
playback and adjust volume
record 10 seconds
zoom in and contemplate your system's real latency
tie in apps like rakarrack
use other/customized/-rt kernels
rename Audio n --> your actual setting
compare latencies and xruns
Make your own conclusions about preferable audio settings.

the beat goes on
bluesscream

---

### Post by AutoStatic on 2010-11-09
Try jdelay, this tool is intended to measure the overall latency of your system and soundcard.

Best,

Jeremy

---

### Post by Bi11yy on 2010-11-09
Hey AutoStatic, I've got jdelay, but how do I start with it? I mean running it, keep getting "signal below threshold" in terminal... What do i need to do?

---

### Post by AutoStatic on 2010-11-09
[http://lists.linuxaudio.org/pipermail/linux-audio-user/2009-April/059437.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2009-April/059437.html)

---

### Post by Bi11yy on 2010-11-09
Kinda confused, The numbers I'm getting back, are they in frames or ms? I'm getting back 709.000, which if ms, would be ridiculous, and I'm not sure how to convert from frames to ms.

---

### Post by Pablo_F on 2010-11-09
Hi Bi11yy, 

Those are frames. 

Latency (ms) = (frames / sample rate (frames/s)) * 1000

If you get jack_delay from [http://www.kokkinizita.net/linuxaudio/](http://www.kokkinizita.net/linuxaudio/) and compile it, the output is shown in frames and miliseconds so you don't have to make the calculation. Note that in this case, the executable file is called jack_delay instead of jdelay.

Cheers! Pablo

---

### Post by bluesscream on 2010-11-09
Tx for the answers and hints. I'm visual orientated, so I have more pleasure with waveforms in ardour tracks then with bare figures in a terminal ;)

.jackdrc shows '/usr/bin/jackd -T -P75 -p1024 -t2000 -dfirewire -r48000 -p64 -n3'
this gives here 6.4 ms delay measured in Ardour and 10.433 in jack_delay.

Why are there different results when measuring in Ardour against measuring in j(ack_)delay?

Do j(ack_)delay's signals stress the hardware more then Ardour's simple metronome clicks?

Could it be that these results are not to be interpreted as absolute physical values but useful for comparison under defined conditions?
Best regards
bluesscream

---

### Post by Pablo_F on 2010-11-10
Hi, 

Afaik, jack_delay measures accurately the round trip latency of the jack-audio card system including AD and DA conversions. You make the virtual connections and the physical connection as shown in the attachment (the thick red line represents the cable between the first input and the first output)

You don't explain how you are measuring what delay in ardour. But, anything that you do inside your computer is not affected by DA or AD conversion. 

Cheers! Pablo

---

### Post by AutoStatic on 2010-11-10
I thought jack_delay and jdelay were the same?
Oh well, whatever, nevermind ;)

---

### Post by Pablo_F on 2010-11-10
jdelay from ubuntu shows latency in frames, only. If you compile the source from Fons' site, the binary is called jack_delay and the latency is shown in frames and miliseconds, but yes it must be the same program. Go figure.

Cheers! Pablo

---

### Post by bluesscream on 2010-11-10
> **Pablo_F said:**
> Hi, 
You don't explain how you are measuring what delay in ardour. But, anything that you do inside your computer is not affected by DA or AD conversion. 

I connected ardour's audio_1 to dev_lineout1 in jackd, then with a real cable  devices physical lineout_1 to physical linein_1. Back again in jackd linein_1 to ardour's audio_2. 
As far I understand there must have been a DA-processing when signal  from ardour's audio_1 is caught at devices output and an AD-processing will be done when this  analogue signal physically relooped into devices line_in is recorded with ardour.

This way we should be able to measure latencies with every reasonably conveniant audio recording/editing software.

Best regards
bluesscream

---

### Post by Pablo_F on 2010-11-12
Hi, 

OK, I think ardour is trying to compensate latency but this is a bit of a hit and miss because it seems to depend on many factors:

1. the jackd version you are using (jackd1 or jackd2)
2. the driver, alsa or firewire. 
3. the ardour version
4. Possibly, some ardour track configuration
5. The audio card itself and the firewire controller

I suggest you measure latency in ardour in frames. You can select the option "Secondary Clock delta to edit point" and put the secondary clock to samples (right click).

I don't have a firewire card to check but you can try to improve latency compensation in ardour with the -I and -O options in jackd (Input latency and output latency in qjackctl). You put latency values in frames. At 48000 KHz, 1 frame takes 0,0208333 ms and 1 ms is 48 frames. . You can try different values in Input and Output latency and see if this makes a difference. 

As for point 1., jackd2 behaves differently to jackd1 with regards to latency. By default, jackd2 runs in aynchronous mode. I am not sure what this means but it adds a period latency. The -S option in the command field (server path) is for synchronous mode. You might notice a slight improvement (64 frames) in jack_delay. If you are running jackd1, forget about this.

There are some interesting notes on latency in firewire devices here: [http://subversion.ffado.org/wiki/SomeNotesOnLatency](http://subversion.ffado.org/wiki/SomeNotesOnLatency)

Cheers! Pablo

---

### Post by bluesscream on 2010-11-14
Hi Pablo, tx for your reply and the link.


>  you can try to improve latency compensation in ardour with the -I and -O options in jackd (Input latency and output latency in qjackctl).
In Qjackctl 0.3.6 Build: Jun 30 2010 when I set driver firewire the buttons for in- and output devices and their corresponding latencies are grayed out. I failed compiling the actual svn where this is told to be fixed.
 > By default, jackd2 runs in aynchronous mode. I am not sure what this means but it adds a period latency. The -S option in the command field (server path) is for synchronous mode. You might notice a slight improvement (64 frames) in jack_delay. 
I see no improvement when I start qjackctl with server-path entry jackd -S. Just for interest, where can I find information about default asynchronous jack2 setting and the option -S for 'synchronous'?    man jack announces  -S for 'Short', 16 bit instead of 32bit.
I see, there is a lot more I'll have to read and learn to get deeper into this matter.

In my amateurish experiments in customized ubuntustudio 10.04 amd64 with ardour2.8.11 and jack_delay I find only slight differences in latencies/delays - max. difference is 14 samples ~ 0,3 ms in jack_delay - when always using identical settings and hardware on different kernels  (2.6.31.x-2.6.36.x, generic, preempt, if available  lowlatency, realtime, -ck patched).
Hardware assemblies tested: Notebook with intel dualcore 2g, onboard via firewirechip, edirol fa101.
Desktop amd athlon64 x2 4200, pci firewire card with via chip, edirol fa101 and the same machine with pci hoontech dsp 24 (ice1712).
Best regards 
bluesscream

---

### Post by Pablo_F on 2010-11-14
> In Qjackctl 0.3.6 Build: Jun 30 2010 when I set driver firewire the buttons for in- and output devices and their corresponding latencies are grayed out. I failed compiling the actual svn where this is told to be fixed.

Oh, I don't know of any qjackctl deb package for lucid where this is issue is solved. You always have the terminal. Replicating the command you were using in a previous post:

jackd -T -P75 -p1024 -t2000 -dfirewire -r48000 -p64 -n3

you would have to add at the end (this is just an example)

-I500 (for 500 frames of input latency)

and/or

-O500 (for 500 frames of output latency)

Afaik, if you are running lucid, jack is jack1 (0.118 I think) and -S means what you say. But in jack2, -S means synchronous mode. As you have jack1, you don't have to worry about this. 

[http://trac.jackaudio.org/](http://trac.jackaudio.org/)

Most of the stuff there goes beyond my knowledge.

 Note that, in general, upstream devs don't read distro specific forums but read and reply to user's mailing list, such as linux audio users or ffado users. They know about their software better than any of us, distro specific forum helpers. If you want to get deeper into this, join the mailing lists. wiki page at limuxmusicians.org is another distro-neutral good resource.

> I find only slight differences in latencies/delays 

Well, if you tell jack to use a given sample rate and p and n values, it is expected that you get the same latency with different kernels. A "bad" kernel or other bad configurations will give you more xruns, or even prevent jackd from starting with very low latency, whereas a well configured linux will allow jackd to run with low latency without xruns. You set the latency in the jack command but jack can't do anything with hardware latency.

Good night, Pablo

---

### Post by trulan on 2010-11-15
The only thing I've found that actually affects my hardware latency (not the software latency set in JACK, rather the difference between the round-trip latency measured with jdelay and the JACK latency, in other words the actual latency of my interface) is the sampling rate.  A sampling rate of 96000 gives a much lower hardware latency than does a sampling rate of 44100.  (presonus firepod)

---

### Post by bluesscream on 2010-11-15
@trulan: tx, I'll try this. But some of my preferred applications like hydrogen drumsets only are available in 44100 and I've not the patience to recompile them.
@ pablo: > Afaik, if you are running lucid, jack is jack1 (0.118 I think)
As I said, I customized my ubuntustudio and of course I use jackd 1.9.6 ;)

I learned: To compare audio performance of different kernels and/or system configurations I'll have to adjust sampling rates, buffers, periods --> latencies in defined steps and applicate stress under standardized conditions to find the threshold for the appearance of xruns.
Any suggestions for a practical test-design?
My priorities are 
1. live performance with midi controlled samplers, synthesizers and effects
2. sound design
3. clean multitrackrecording
4. playback recording
cu bluesscream
[http://www.mediafire.com/?ynmcfoximoy](http://www.mediafire.com/?ynmcfoximoy)

---

