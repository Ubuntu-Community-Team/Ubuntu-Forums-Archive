---
title: "The Year 2038 Problem"
date: 2005-05-04
forum: The Cafe
---

### Post by bored2k on 2005-05-04
I got today this e-mail with some interesting issues. We have about 30 years to fix this so it's no biggie ^_^

> The Year 2038 Problem
>
>Test it now...
>
>steps...
>
>1. login to yahoo messenger
>2. send instant message to anyone - fine its working...
>3. now, change ur system date to 19-Jan-2038, 03:14:07 AM or above (as
>mentioned in mail)
>4. Confirm weather ur date is changed
>5. again send instant message to anyone...
>
>Your YM crahes....
>
>* * * YES ALL NETWORK BASED APPLICATION WILL NOT WORK NOW * * *
>
>Why.....
>
>What is it?
>
>Starting at GMT 03:14:07, Tuesday, January 19, 2038, It is expected to see
>lots of systems around the world breaking magnificently: satellites falling
>out of orbit, massive power outages (like the 2003 North American
>blackout), hospital life support system failures, phone system
>interruptions, banking errors, etc. One second after this critical second,
>many of these systems will have wildly inaccurate date settings, producing
>all kinds of unpredictable consequences. In short, many of the dire
>predictions for the year 2000 are much more likely to actually occur in the
>year 2038! Consider the year 2000 just a dry run. In case you think we can
>sit on this issue for another 30 years before addressing it, consider that
>reports of temporal echoes of the 2038 problem are already starting to
>appear in future date calculations for mortgages and vital statistics! In
>the first month of the year 2038 C.E. many computers will encounter a
>date-related bug in their operating systems and/or in the applications they
>run. This can result in incorrect and wildly inaccurate dates being
>reported by the operating system and/or applications. The effect of this
>bug is hard to predict, because many applications are not prepared for the
>resulting "skip" in reported time - anywhere from 1901 to a "broken record"
>repeat of the reported time at the second the bug occurs. Also, may make
>some small adjustment to the actual time the bug expresses itself. This bug
>to cause serious problems on many platforms, especially Unix and Unix-like
>platforms, because these systems will "run out of time".
>
>What causes it?
>
>Time_t is a data type used by C and C++ programs to represent dates and
>times internally. (Windows programmers out there might also recognize it as
>the basis for the CTime and CTimeSpan classes in MFC.) time_t is actually
>just an integer, a whole number, that counts the number of seconds since
>January 1, 1970 at 12:00 AM Greenwich Mean Time. A time_t value of 0 would
>be 12:00:00 AM (exactly midnight) 1-Jan-1970, a time_t value of 1 would be
>12:00:01 AM (one second after midnight) 1-Jan-1970, etc..
>
>some example times and their exact time_t representations:
>
>Date & time  time_t representation
>
>1-Jan-1970, 12:00:00 AM GMT 0
>
>1-Jan-1970, 12:01:00 AM GMT 60
>
>1-Jan-1970, 01:00:00 AM GMT 3 600
>
>2-Jan-1970, 12:00:00 AM GMT 86 400
>
>1-Jan-1971, 12:00:00 AM GMT 31 536 000
>
>1-Jan-1972, 12:00:00 AM GMT 63 072 000
>
>1-Jan-2038, 12:00:00 AM GMT 2 145 916 800
>
>19-Jan-2038, 03:14:07 AM GMT 2 147 483 647
>
>By the year 2038, the time_t representation for the current time will be
>over 2 140 000 000. And that's the problem. A modern 32-bit computer stores
>a "signed integer" data type, such as time_t, in 32 bits. The first of
>these bits is used for the positive/negative sign of the integer, while the
>remaining 31 bits are used to store the number itself. The highest number
>these 31 data bits can store works out to exactly 2 147 483 647. A time_t
>value of this exact number, 2 147 483 647, represents January 19, 2038, at
>7 seconds past 3:14 AM Greenwich Mean Time. So, at 3:14:07 AM GMT on that
>fateful day, every time_t used in a 32-bit C or C++ program will reach its
>upper limit.
>
>One second later, on 19-January-2038 at 3:14:08 AM GMT, disaster strikes.
>When a signed integer reaches its maximum value and then gets incremented,
>it wraps around to its lowest possible negative value. This means a 32-bit
>signed integer, such as a time_t, set to its maximum value of 2 147 483 647
>and then incremented by 1, will become -2 147 483 648. Note that "-" sign
>at the beginning of this large number. A time_t value of -2 147 483 648
>would represent December 13, 1901 at 8:45:52 PM GMT.
>
>So, if all goes normally, 19-January-2038 will suddenly become
>13-December-1901 in every time_t across the globe, and every date
>calculation based on this figure will go haywire. And it gets worse. Most
>of the support functions that use the time_t data type cannot handle
>negative time_t values at all. They simply fail and return an error code.
>
>A quick check with the following Perl script may help determine if your
>computers will have problems (this requires Perl to be installed on your
>system, of course):
>
>#!/usr/bin/perl
># Use POSIX (Portable Operating System Interface) use POSIX;
># Set the Time Zone to GMT (Greenwich Mean Time) for
>date calculations.
>$ENV{'TZ'} = "GMT";
># Count up in seconds of Epoch time just before and
>after the critical event.
>for ($clock = 2147483641; $clock < 2147483651;
>$clock++)
>{
>print ctime($clock);
>}
>
>For example, the output of this script on Debian GNU/Linux (kernel 2.4.22)
>(An affected system) will be
>
># ./2038.pl
>Tue Jan 19 03:14:01 2038
>Tue Jan 19 03:14:02 2038
>Tue Jan 19 03:14:03 2038
>Tue Jan 19 03:14:04 2038
>Tue Jan 19 03:14:05 2038
>Tue Jan 19 03:14:06 2038
>Tue Jan 19 03:14:07 2038
>Fri Dec 13 20:45:52 1901
>Fri Dec 13 20:45:52 1901
>Fri Dec 13 20:45:52 1901
>
>Solution
>
>"The best way to predict the future is to engineer it." Consider testing
>your mission-critical code well ahead of time on a non-production test
>platform set just before the critical date. For more general applications,
>just using large types for storing dates will do the trick in most cases.
>For example, in GNU C, 64-bits (a "long " type) is sufficient to keep the
>time from rolling over for literally geological eons This just means any
>executables the operating systems runs will always get the correct time
>reported to them when queried in the correct manner. It doesn't stop the
>executables you may still want to be worried about Well-written programs
>can simply be recompiled with a new version of the library that uses, for
>example, 8-byte values for the storage format. This is possible because the
>library encapsulates the whole time activity with its own time types and
>functions (unlike most mainframe programs, which did not standardize their
>date formats or calculations). So the Year 2038 problem should not be
>nearly as hard to fix as the Y2K problem was.
>
>Admittedly, some don't feel that this impending disaster will strike too
>many people. They reason that, by the time 2038 rolls around, most programs
>will be running on 64-bit or even 128-bit computers. In a 64-bit program, a
>time_t could represent any date and time in the future out to 292 000 000
>000 A.D., which is about 20 times the currently estimated age of the
>universe. The problem with this kind of optimism is the same root problem
>behind most of the Year 2000 concerns that plagued the software industry in
>previous years: Legacy Code. Even if every PC in the year 2038 has a 64-bit
>CPU, there will be a lot of older 32-bit programs running on them.
>
>The greatest danger with the Year 2038 Problem is its invisibility. The
>more-famous Year 2000 is a big, round number; it only takes a few seconds
>of thought, even for a computer-illiterate person, to imagine what might
>happen when 1999 turns into 2000. But January 19, 2038 is not nearly as
>obvious. Software companies will probably not think of trying out a Year
>2038 scenario before doomsday strikes. Of course, there will be some
>warning ahead of time. Scheduling software, billing programs, personal
>reminder calendars, and other such pieces of code that set dates in the
>near future will fail as soon as one of their target dates exceeds
>19-Jan-2038, assuming a time_t is used to store them.
>
>Good luck, and hope no ones flying car breaks down in 2038
>
>Please follow the links for more Info :
>[http://www.howstuffworks.com./question75.htm](http://www.howstuffworks.com./question75.htm)
>[http://www.deepsky.com/~merovech/2038.html](http://www.deepsky.com/~merovech/2038.html)
>[http://www.deepsky.com/~merovech/2038.html](http://www.deepsky.com/~merovech/2038.html)
>[http://www.deepsky.com/%7Emerovech/2038.html](http://www.deepsky.com/%7Emerovech/2038.html)
>[http://pw2.netcom.com/~rogermw/Y2038.html](http://pw2.netcom.com/~rogermw/Y2038.html)
>[http://pw2.netcom.com/~rogermw/Y2038.html](http://pw2.netcom.com/~rogermw/Y2038.html)
>[http://pw2.netcom.com/%7Erogermw/Y2038.html](http://pw2.netcom.com/%7Erogermw/Y2038.html)

---

### Post by jdong on 2005-05-04
The Y2038 problem is too hyped up. See [http://www.dslreports.com/forum/remark,13310528](http://www.dslreports.com/forum/remark,13310528) for a partial discussion.

Bottom line---

By that time, everyone'll be using a 64-bit system, which doesn't suffer from this problem.

If not, time_t will be switched over to an "unsigned long long" 64-bit [High/Low register] format, which gets rid of the problem just as well.

---

### Post by KiwiNZ on 2005-05-04
2038 , heck I wont be able to remember any passwords , or even where I left my PC. :razz::razz:

---

### Post by Gandalf on 2005-05-04
damn :'( my portable won't work in 33 year :lol:

---

### Post by KiwiNZ on 2005-05-04
[QUOTE=Gandalf]damn :'( my portable won't work in 33 year :lol:[/QUOTE]

You'r worried about your portable , my hearing aide will fizzle , my bladder wont be working , my scooter will die , my pace maker will have a meltdown , I will spend each day meeting this stranger in the mirror , and cooking my lunch in the dishwasher , doing my washing in the fridge , and you dont want to know what I will be doing in the closet :razz::razz:

---

### Post by TravisNewman on 2005-05-04
This is about as overblown as Y2k. ;) But if people DON'T start working on it, it'll be a problem. But as dong said, 64 bit systems and all.

---

### Post by jordanau on 2005-05-05
Well I have been waiting for the opportunity to use the Y2K shelter I dug, guess I'll have to wait a few more years.  :smile:

---

### Post by Adrenal on 2005-05-05
Sif we'd still be using c apps in 2038....

---

### Post by paul cooke on 2005-05-05
[QUOTE=panickedthumb]This is about as overblown as Y2k. ;) But if people DON'T start working on it, it'll be a problem. But as dong said, 64 bit systems and all.[/QUOTE]

It will be a problem for those who are contractually obliged to support their ms-windows apps through then. We have a problem with our app... and the customer is expecting it to carry on working then, so to support them (if we're still around then) we'll have to port to a 64 bit version and replace the hardware it runs on.

We supply bespoke turn-key training systems with very long support contracts to various military forces around the world.

We're having enough problems sourcing 386 and 486 processors to support training systems we built back in the 90's. We're even buying up old PC's via ebay and the like.

---

### Post by jerome bettis on 2005-05-05
ms windows??   think how long from now 2038 is ... 35 years!!!  i hope to god windows 95 still isn't around 35 years from now.  that aside, i think this whole thing is specifically a unix problem .. i don't believe windows has the same bug.  and i really don't care because, as stated earlier, it's way too hyped up.

i'll be **55** by then.  hell we probably won't even have computers but something better :-P

---

### Post by Stormy Eyes on 2005-05-05
I'm just a little more concerned with the probable meltdown of social programs in the US as the Baby Boomers retire and die off, especially as I'll probably migrate to one of AMD's 64-bit processors in the next two years or so.

---

### Post by The Producer on 2005-05-05
> >Starting at GMT 03:14:07, Tuesday, January 19, 2038, It is expected to see
>lots of systems around the world breaking magnificently: satellites falling
>out of orbit, massive power outages (like the 2003 North American
>blackout), hospital life support system failures, phone system
>interruptions, banking errors, etc. One second after this critical second,
>many of these systems will have wildly inaccurate date settings, producing
>all kinds of unpredictable consequences. In short, many of the dire
>predictions for the year 2000 are much more likely to actually occur in the
>year 2038!

Wow...it sounds similar to the events in my story....

Like with most other issues, it's a problem, but won't come close to this fantasy apocalyptic mess that somebody thought up. 

As usual, we'll just calmly take care of it, and Jan. 19, 2038 will pass without incident...heck, you'll probably would have forgotten it by then, like I forgot about the Y2K thing months in advance, until someone reminded me about it days after Jan 1st....

---

### Post by paul cooke on 2005-05-05
[QUOTE=jerome bettis]ms windows??   think how long from now 2038 is ... 35 years!!!  i hope to god windows 95 still isn't around 35 years from now.  that aside, i think this whole thing is specifically a unix problem .. i don't believe windows has the same bug.  and i really don't care because, as stated earlier, it's way too hyped up.

i'll be **55** by then.  hell we probably won't even have computers but something better :-P[/QUOTE]

[http://support.microsoft.com/default.aspx?scid=kb;en-us;Q142576](http://support.microsoft.com/default.aspx?scid=kb;en-us;Q142576)

it applies to certain versions of ms-windows as well as all others that are using 32 bit variables for date based on Jan 1st 1970 as the counter start... It also applies to any program that uses that format of date internally, not just the OS.

[http://computer.howstuffworks.com/question75.htm](http://computer.howstuffworks.com/question75.htm)

---

### Post by emperor on 2005-05-05
In 33 years, I'll be 87! That's more of a problem for me than "time_t" being a "long" integer!

---

### Post by XDevHald on 2005-05-05
[QUOTE=jerome bettis]ms windows??   think how long from now 2038 is ... 35 years!!!  i hope to god windows 95 still isn't around 35 years from now.  that aside, i think this whole thing is specifically a unix problem .. i don't believe windows has the same bug.  and i really don't care because, as stated earlier, it's way too hyped up.

i'll be **55** by then.  hell we probably won't even have computers but something better :-P[/QUOTE]
 I don't even want to think about 2038, I'll stick with the present, kinda makes me think to much when trying to think of 2038 and it's nuscents it'll bring ;)

---

### Post by Ubunted on 2005-05-05
By 2038, we will probably have moved out of silicon-based computing altogether fer cryin out loud. 64-bit CPUs will be a thing of the past - think quantum computers, or at the very least 256-bit+ CPUs.

And who knows? We may even get final screenshots of Duke Nukem Forever by then!

---

### Post by TravisNewman on 2005-05-05
Are you crazy? By 2038, they may have released a few PROTOTYPE screenshots of DNF, but no way we'll get the Final screenshots by then. Just won't happen.

(;))

---

### Post by poofyhairguy on 2005-05-05
[QUOTE=jerome bettis]
i'll be **55** by then.  hell we probably won't even have computers but something better :-P[/QUOTE]

Or worse if the media companies and microsoft have their way....

---

### Post by RastaMahata on 2005-05-05
[QUOTE=poofyhairguy]Or worse if the media companies and microsoft have their way....[/QUOTE]
 1984 anyone?
Bill Gat-- I mean, "Big Brother" will watching you.
We will be all having soma and getting one-color-clothes to represent our social status and IQ...

I think I got mixed some books over there...

Something worse if the media companies and microsoft have their way? hrm... I can imagine it now, windows powered eyeglasses... "Oh yeah, I can see everything AND chat through MSN432 AND walk at the same time! Oh, wait, no... no... wait.. what the f*ck?..." *BSOD* "Argh!" *Plaf*

---

### Post by poofyhairguy on 2005-05-05
[QUOTE=RastaMahata]1984 anyone?
[/QUOTE]

Not really. Well, actually yes.

[http://en.wikipedia.org/wiki/Trusted_computing](http://en.wikipedia.org/wiki/Trusted_computing)

---

### Post by jordanau on 2005-05-05
See now if only John Titor had come back from 2038 instead of 2036, we would know. Of course that could be why he needed the IBM 5100...

---

### Post by DJ_Max on 2005-05-06
In the year 2037, will someone please remind me to trade in my cell phone, pda, and iMac, or atleast update my OS(s), which i've had for 30+ years. ;-)

---

### Post by BWF89 on 2005-05-06
This means taht in 2038 we won't be able to run Linux on our aging 32 bit computers :( .

---

### Post by Ubunted on 2005-05-07
Considering Linux still runs on 386/486 processors that were the new hotness 12+ years ago, and that the numbers of moden x86-based processors currently outnumber the amount of 386/486 chips ever produced by an order of magnitude or two, I believe there will ALWAYS be someone supporting Linux for old processors.

Case in point: [DSL](http://www.damnsmalllinux.org/)

---

### Post by binary-boy on 2005-05-07
The majority of the problems with the year 2000 were caused by mainframes. These old beasts probably have the largest collection of legacy code anywhere and so were ripe for these sorts of issues.

Our company, as with most others I assume, subscribed to the mass panic of Y2K and had developers, mainframe and other, working overtime to make sure the world didn't melt but (as many educated people predicted) that never happened and in fact our only problems were caused by someone deciding to fit a new server over the same weekend (another sound management decision).

I may be wrong here, but I believe that if Windows is still about in 2038, Microsoft may have been able to fix it for whatever their latest version will be. Linux  systems continually evolve due to their very nature so this bug will have been ironed out long before 2038.

This is all assuming that global warming hasn't finished us all off before then.....

---

