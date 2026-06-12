---
title: "Year 2038 Problem"
date: 2009-10-20
forum: The Cafe
---

### Post by tom66 on 2009-10-20
I was curious, so I set my time to 30 seconds before the rollover of time_t (19 Jan 2038 03:14:07). 

Everything broke.

Well, not quite everything. But what did break:
[LIST]
[*]MySQLd: both cores 100% usage
[*]gnome-panel: most widgets crashed and panel would not respond to right-click
[*]intermittent freezing, sluggish in general
[*]on rollover, complete freeze for 5 seconds
[*]VT switching very slow, about 5 seconds to switch
[*]conky crashed
[*]chromium crashed
[*]nautilus crashed
[*]networkmanager stopped working (or crashed, can't tell) - lost WiFi connection
[/LIST]

So I guess unless I switch to a 64-bit kernel I'm in trouble if I'm still using 32-bit in 2038...

It's kind of like Y2K, except it actually happened (and probably will happen).

---

### Post by OpenGuard on 2009-10-20
Are you planing to use Ubuntu 9.04 32bit for the next 29 years ?

---

### Post by NoaHall on 2009-10-20
I was just thinking of creating a thread to ask if anyone had done so. Haha, that's almost as bad as when you do rm -rf / . Don't even try to do this command, k?

---

### Post by Tibuda on 2009-10-20
If you switch to 64bit, you'll have to switch to 128bit before Sunday, December 4, 292,277,026,596 AD.

---

### Post by Stavro on 2009-10-20
> **NoaHall said:**
> Haha, that's almost as bad as when you do rm -rf / .

Its nowhere near as bad as doing the instruction you've mentioned, because no data will be lost. I just felt compelled to clarify this should anyone be 'curious' to try that dreadful delete command based on your light heartedness over something so dangerous. The clock can be rectified in the BIOS and is nothing major.

---

### Post by tom66 on 2009-10-20
No, but my mobile phone and embedded systems I and other people use might be using a 32-bit CPU. (For example, ARM CPUs are 32-bit.) Some systems implemented soon may still use a 32-bit CPU and they might be designed so they don't ever go down. Desktops aren't the problem - most will be 64-bit long before the rollover.

---

### Post by NoaHall on 2009-10-20
That's not what I meant. Search on youtube for that command, and you'll see videos of a effect in the thumbnail. I know it causes no data loss, thank you very much.

---

### Post by Stavro on 2009-10-20
The year 2000 'bug' was just a terrible money making scam... lots of small firms of supposed software companies offering solutions that really just looked flash. I had an old Compaq 486 at the time running the first upgrade edition of Windows 95. Upon boot the clock was 1980 something, but setting it to 2000 made it stay there.

---

### Post by Bachstelze on 2009-10-20
> **NoaHall said:**
> I was just thinking of creating a thread to ask if anyone had done so. Haha, that's almost as bad as when you do rm -rf / .

> **Stavro said:**
> Its nowhere near as bad as doing the instruction you've mentioned, because no data will be lost.

I can assure you that typing [font=monospace]rm -rf /[/font] won't make you lose any data either (yes, even with sudo):

```
firas@iori ~ % sudo rm -rf /
rm: cannot remove root directory `/'

```

---

### Post by Stavro on 2009-10-20
> **Bachstelze said:**
> I can assure you that typing [font=monospace]rm -rf /[/font] won't make you lose any data either (yes, even with sudo):

```
firas@iori ~ % sudo rm -rf /
rm: cannot remove root directory `/'

```

Ok. I'm new to Linux, I don't know everything.

---

### Post by imbjr on 2009-10-20
> **Stavro said:**
> The year 2000 'bug' was just a terrible money making scam... lots of small firms of supposed software companies offering solutions that really just looked flash. I had an old Compaq 486 at the time running the first upgrade edition of Windows 95. Upon boot the clock was 1980 something, but setting it to 2000 made it stay there.

Whilst there was indeed a rash of scammers taking a ride on the Y2K wave, the problem was very much a real one.

---

### Post by Stavro on 2009-10-20
> **NoaHall said:**
> That's not what I meant. Search on youtube for that command, and you'll see videos of a effect in the thumbnail. I know it causes no data loss, thank you very much.

Ok Noahall, I was only trying to be helpful. No need to get a little defensive.

---

### Post by OpenGuard on 2009-10-20
> **Bachstelze said:**
> I can assure you that typing [FONT=monospace]rm -rf /[/FONT] won't make you lose any data either (yes, even with sudo):

```
firas@iori ~ % sudo rm -rf /
rm: cannot remove root directory `/'

```

I wouldn't be so sure about this. [COLOR=Gray]/* [/COLOR]and you are screwed.

---

### Post by tom66 on 2009-10-20
I didn't lose any data. It just crashed a few programs, and hammered the CPU (mysqld seemed to be getting confused. I suspect it just kept crashing and restarting itself. All my MySQL databases are fine.) There was no filesystem damage, but it did force me to reboot.

---

### Post by Bachstelze on 2009-10-20
> **OpenGuard said:**
> I wouldn't be so sure about this. [COLOR=Gray]/* [/COLOR]and you are screwed.

It's a different command, then.

---

### Post by OpenGuard on 2009-10-20
> **Bachstelze said:**
> It's a different command, then.

No, the command is:
```
sudo rm -rf <target>
```Static path or pattern - it's still one and the same command.

---

### Post by NoaHall on 2009-10-20
There was a reason I wasn't writing the * there, you know. It's pretty clear as to which command I mean. It's best to leave things out if people that are new are going to see them and try.

---

### Post by steev182 on 2009-10-20
How many people do you know still using a Motorola starTAC or Nokia 3310 or an Atari ST or a 386 pc anymore?

By 2038, this won't be an issue. Also, apparently HaikuOS (32-bit only) doesn't have the 2038 problem.

---

### Post by JillSwift on 2009-10-20
[FONT=Georgia][SIZE=3]It's true. The 32 bit OS is headed for a disaster of biblical proportions.
 What do I mean, "biblical", you ask?
What I mean is Old Testament, dear reader, real wrath of God type stuff.
Fire and brimstone coming down from the skies! Rivers and seas boiling!
Forty years of darkness! Earthquakes, volcanoes...
The dead rising from the grave!
Human sacrifice, dogs and cats living together... ***mass hysteria!***[/SIZE][/FONT]

---

### Post by TheBuzzSaw on 2009-10-20
When does 64-bit end? Has anyone calculated that yet?

---

### Post by tom66 on 2009-10-20
> **steev182 said:**
> How many people do you know still using a Motorola starTAC or Nokia 3310 or an Atari ST or a 386 pc anymore?

By 2038, this won't be an issue. Also, apparently HaikuOS (32-bit only) doesn't have the 2038 problem.

Very few I know about. But I still know that about 98% of mobile phones, PDAs, etc. use ARM processors. ARM is a 32-bit architecture and would have little incentive to upgrade to 64-bit (how many phones do you know with more than 4 GB of RAM?)

---

### Post by sudoer541 on 2009-10-20
> **JillSwift said:**
> [FONT=Georgia][SIZE=3]It's true. The 32 bit OS is headed for a disaster of biblical proportions.
 What do I mean, "biblical", you ask?
What I mean is Old Testament, dear reader, real wrath of God type stuff.
Fire and brimstone coming down from the skies! Rivers and seas boiling!
Forty years of darkness! Earthquakes, volcanoes...
The dead rising from the grave!
Human sacrifice, dogs and cats living together... ***mass hysteria!***[/SIZE][/FONT]


eeeeeeeek!!! OMG!!!!
the end of times!!!  the sky is falling!!!

---

### Post by Tibuda on 2009-10-20
> **TheBuzzSaw said:**
> When does 64-bit end? Has anyone calculated that yet?

According to [wikipedia]("http://en.wikipedia.org/wiki/Year_2038_problem"):
[quote="Wikipedia"]Using a (signed) 64-bit value introduces a new wraparound date in approximately 292 billion years, on Sunday, December 4, 292,277,026,596 AD.[/quote]

---

### Post by steev182 on 2009-10-20
Wouldn't functioning during/after 2038 be enough incentive?

Plus only 15 years ago my computer had a 4GB Hard drive and 32mb ram. My iphone is more powerful than that, we're looking at 30 years from now.

---

### Post by BslBryan on 2009-10-20
How did you get it to set that time?  My machine doesn't allow it.

---

### Post by tom66 on 2009-10-20
You have to set it a few seconds behind the actual time (30 seconds works well for me)

---

