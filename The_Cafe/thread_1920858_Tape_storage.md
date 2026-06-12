---
title: "Tape storage"
date: 2012-02-05
forum: The Cafe
---

### Post by roelforg on 2012-02-05
Ok,
I've been playing with this idea...
If i can use the lpt0 on my pc to generate 2 1/0 signals
and connect this to an old cassette deck.
Could i store data this way?

Reading would involve 2 other ports on lpt0.

The i/o would be controlled by a selfwritten prog.
The trigger would be power on the engine, again via lpt0.

Is this possible?

---

### Post by mips on 2012-02-05
You would have to perform some form of modulation with different carrier frequencies for the 0s & 1s I reckon.

Why you would want to use tape/cassette deck is what boggles the mind though. Last time audio/video tape was used for data storage was in the 80's.

---

### Post by JKyleOKC on 2012-02-05
> **roelforg said:**
> Is this possible?Yes, it's possible. Back in the very early 1980s I was experimenting with an RCA 1802 microprocessor and was working for a mainframe tape drive manufacturer. With access to lots of very good engineering talent, I was able to write a program in the 1802's assembly language to store data to a cassette tape, and read it back accurately. With today's much faster processor chips and peripherals, it should be even easier.

However, "possible" and "practical" are not at all the same thing, and the maximum data transfer rate you could get with a tape cassette recorder would limit you to around 300 bits (not bytes) per second. That would be approximately 30 bytes per second, which means about 1.8K bytes per minute. At that rate, a single 1-megabyte photo file would take well over a day to store -- even if you could find a cassette big enough to hold it!

You can still buy digital audio tape (DAT) backup drives, and cartridges for them that can store gigabytes of data. These are used by some businesses for backup, but it's now cheaper to use external hard disks. In addition, tape cartridges are somewhat notorious for jamming. All in all, it's a technology that's going the way of the buggy whip...

---

### Post by Old_Grey_Wolf on 2012-02-05
^^^
+1

In addition to what JKyleOKC wrote, cassette tapes are made of a polyester type plastic film with a magnetic coating. It deteriorates over time. Those of us that used the tapes for backup or 5 1/2 inch floppy disks in the 1980's are familiar with that problem. After 5 or 10 years they stopped working.

When we used tapes, disk drives cost $100 (76 Euro) per GB, now they are less than $100 (76 Euro) per TB.

---

### Post by alphacrucis2 on 2012-02-05
I remember using cassettes for data storage on my c64 way back when. It was slow and frustrating IIRC. That said [LTO]("http://en.wikipedia.org/wiki/Linear_Tape-Open") tapes are still used today for bulk data archive and backup. They are a bit different to audio cassettes though :). The latest LTO v5 can hold about 1.5tb on a cartridge.

---

### Post by roelforg on 2012-02-05
> **mips said:**
> You would have to perform some form of modulation with different carrier frequencies for the 0s & 1s I reckon.

Why you would want to use tape/cassette deck is what boggles the mind though. Last time audio/video tape was used for data storage was in the 80's.

Because i can!
No reason, i was bored and on the tv was a show about the speed of the exponential increase of storage space (it was a long name, but you get the point) and thought: "I've got myself an old deck... Ahhh why not?"
But as i'm more of a software kinda guy, i was hoping that someone might be able to help me.

According to wikipedia, the range of each audio channel is ~ -2.5v - 2.5v.
Seems doable.

And it's a nice little project,
my plan on getting my old ps2 slim running linux is delayed until my friend comes back from holiday,
i don't have the games for the swap trick or the disk's for the other methods, that leaves my friend's modded ps2 slim to install fmcb on my memcard.

---

### Post by roelforg on 2012-02-05
> **alphacrucis2 said:**
> I remember using cassettes for data storage on my c64 way back when. It was slow and frustrating IIRC. That said [LTO]("http://en.wikipedia.org/wiki/Linear_Tape-Open") tapes are still used today for bulk data archive and backup. They are a bit different to audio cassettes though :). The latest LTO v5 can hold about 1.5tb on a cartridge.

Why an i picturing a lto-tape manufacturer with $ eyes and lot's of cash when reading this?
EDIT: Forgot the big sigar and the big grin.

---

### Post by roelforg on 2012-02-05
> **JKyleOKC said:**
> However, "possible" and "practical" are not at all the same thing, and the maximum data transfer rate you could get with a tape cassette recorder would limit you to around 300 bits (not bytes) per second. That would be approximately 30 bytes per second, which means about 1.8K bytes per minute. At that rate, a single 1-megabyte photo file would take well over a day to store -- even if you could find a cassette big enough to hold it!


Where did i say i wanted to store files bigger then a few kb?
And where did i say i was going to use this for any other kind of storage than the occasional dive in history?

Btw. I'm trying to get a feel for how things used to be, my grand-mother's ibm ps1 and a friends amstrad just made me interrested in the history of computing.

---

### Post by alphacrucis2 on 2012-02-05
> **roelforg said:**
> Why an i picturing a lto-tape manufacturer with $ eyes and lot's of cash when reading this?
EDIT: Forgot the big sigar and the big grin.

That's the case with all hardware manufacturers ;). The tapes do have practical advantages for bulk archive and backup to meet audit requirements. We have several robotic tape libraries at work that use these tapes. It is not at all aimed at the home market.

---

### Post by JKyleOKC on 2012-02-05
> **roelforg said:**
> Btw. I'm trying to get a feel for how things used to be, my grand-mother's ibm ps1 and a friends amstrad just made me interrested in the history of computing.That's a good goal, and I'm more than willing to help you with it. I've forgotten most of the details of the program I wrote, and while I still have it stored on a cassette, I no longer have anything that can read it -- there's really no reason for me to keep those old cassettes and punched paper tapes, but I'm a history buff and hate to dump them...

Check out Wikipedia, looking for "Manchester encoding" and "Kansas City Standard" articles. Googling for those two search terms, individually, might also help. I used the Manchester approach, which switched DC pulses to the recorder's audio input; the KC Standard was an unofficial system developed by early users of the Altair kit, using tone modulation.

You'll also need to study how the early modems work, since they also depended on tone modulation. In fact I suspect that you could connect a dial-up modem to a computer's serial port, wire its phone-line output to a tape recorder, and have a working tape storage system right off the bat. That would give you a sort of baseline to compare your software implementation against. Keep in mind that software and hardware are essentially interchangeable, except for the fact that software takes longer to do the same job...

---

### Post by robsoles on 2012-02-06
> **JKyleOKC said:**
> ... In fact I suspect that you could connect a dial-up modem to a computer's serial port, wire its phone-line output to a tape recorder, and have a working tape storage system right off the bat.

...
I share this suspicion and feel pressed to comment that between better modulation and demodulation techniques these days you might even get 15.2kB/s on the audio cassette :lol:

Pity you couldn't just go straight off the serial port and skip the modem.

It might be a bit "hair brained" but with my knowledge and experience in hardware, and programming it, being as limited as it is I am willing to speculate that a raw RS232 port fed via a cap & some (carefully arranged) resistors to the input of an audio recorder might be successfully read back by a raw RS232 if the output of a matching player (record speed and playback speed not too far off) was trimmed, similar (but pretty much opposite) treatment with cap & resistors, via a [MAX232]("http://www.ti.com/product/max232") into the plain old serial port.

I imagine that if I set out to prove this I would probably end up with a circuit riddled with opamps, DACs, ADCs and comparators but I wouldn't admit my hairbrained theory was no good till I was actually in the middle of writing the code for an MCU I had recently added to the project... :p :lol: :tears:



Modulating using the parallel port won't be a breeze and demodulating might be nightmarish if you are not executing your code high enough priority in the system, my straight to serial idea is hairbrained (I feel confident somebody told me why sometime in the last 25, or so, years :roll:) - so far the winner I see is the hacked modem, although I do admit that going through what it will take to control timing over LPTx: to modulate and demodulate well enough could draw external components down to the connectors and wire (two RCA plugs, a DB25, 3 strands of wire) so maybe (purely as a learning exercise tho, mind you) it is entirely worth pursuing as you initally saw it :)

[COLOR=Blue]EDIT: Ooops, mmmh, you will always have to do something about normal pre-amp audio level (nominally 1V peak to peak) and standard IO levels of 0V and 5V on a parallel port - no three strands of wire for you I'm afraid (although I see hackish workarounds that could work out - between clipping on the input channel to the cassette deck and the cassette deck including an amplifier the inclusion of diode might be all it takes; Depends on how cassette deck input deals with clipping).[/COLOR]

Wow, tape storage - My first audio cassette tape storage was the VZ200 and I was twelve.

---

### Post by JKyleOKC on 2012-02-06
Timing has always been a problem with tape storage, even for the big mainframe drives. The Manchester system that I referred to previously handles the timing as part of the stored information. It's not just the bits of data that have to be passed to the tape drive. Clock information is required in order to know which bit is which.

The advantage of using Manchester coding as opposed to tone modulation is mostly that it's much more compact. The problem of voltage levels can be handled easily with resistor networks; the problem of keeping the software in sync with the tape is much more difficult. When I implemented my approach way back when, the CPU had absolutely no operating system involved. It did absolutely nothing other than dealing with the stream of pulses going to or coming from the tape.

It might be possible to give a program nigh enough real time priority to deal with a stream of data coming through a serial or parallel port -- but it won't be easy. After all, the whole point of a serial port is to handle a stream of input or output pulses and convert that stream to a parallel byte that the computer can process, and even at the comparatively slow bit rates involved with dial-up data, they can drop frames...

I'm not sure that speeds much higher than 300 bytes/sec can be achieved via audio recording. On the phone lines, the higher speeds are possible because of tricky modulation, which might not come through the circuits involved in tape recording. The ultimate limit, of course, would be reached when the duration of a single bit becomes less than that of a single cycle of the audio tone involved.

---

### Post by mips on 2012-02-06
> **JKyleOKC said:**
> On the phone lines, the higher speeds are possible because of tricky modulation, which might not come through the circuits involved in tape recording. The ultimate limit, of course, would be reached when the duration of a single bit becomes less than that of a single cycle of the audio tone involved.

Frequency response range for phones lines (POTS) is 300-3400Hz. Signal equalization I suspect would would determine the maximum bitrate on audio tape though.

---

### Post by Stovey on 2012-02-06
> **alphacrucis2 said:**
> I remember using cassettes for data storage on my c64 way back when. It was slow and frustrating IIRC...

Fo sho.  Load "*",8,1 lol.

It really is an exercise in frustration to fire up the old C-64 and try to load tapes.

---

