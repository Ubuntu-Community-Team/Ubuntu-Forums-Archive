---
title: "89 GHZ UltraSPARC CPU released under GPL!"
date: 2007-08-07
forum: The Cafe
---

### Post by amlucent23 on 2007-08-07
Sun has announced the release of a new 89 GHZ UltraSPARC Processor. Not only that but they will be releasing the blueprints as GPL! What impact do you think this will have on x86 processor market share and do you think this will cause more distros (namely ubuntu) to make (official) releases for SPARC architecture?...

[http://hardware.slashdot.org/hardware/07/08/07/2152245.shtml]("http://hardware.slashdot.org/hardware/07/08/07/2152245.shtml")

[URL="http://blogs.sun.com/jonathan/entry/sun_enters_the_commodity_silicon"]http://blogs.sun.com/jonathan/entry/sun_enters_the_commodity_silicon
[/URL]
I am interested to hear your thoughts.

---

### Post by jgrabham on 2007-08-07
> **amlucent23 said:**
> Sun has announced the release of a new 89 GHZ UltraSPARC Processor. Not only that but they will be releasing the blueprints as GPL! What impact do you think this will have on x86 processor market share and do you think this will cause more distros (namely ubuntu) to make (official) releases for SPARC architecture?...

[http://hardware.slashdot.org/hardware/07/08/07/2152245.shtml]("http://hardware.slashdot.org/hardware/07/08/07/2152245.shtml")

[URL="http://blogs.sun.com/jonathan/entry/sun_enters_the_commodity_silicon"]http://blogs.sun.com/jonathan/entry/sun_enters_the_commodity_silicon
[/URL]
I am interested to hear your thoughts.

And there was me thinking "I wish I had a 3GHZ CPU in this PC"  :]

---

### Post by juxtaposed on 2007-08-07
Wow, great job sun :)

---

### Post by amlucent23 on 2007-08-07
I know right. 89 ghz! you know I have a 300 some odd mhz sparc machine in my basement that I got from an old job... runs suse 9 without any issues.. not even very slowly.. wonder how fast an 89ghz sparc would run!

---

### Post by foxholeunder on 2007-08-07
So... I think I need ten of these clustered together - You know... just to ensure I have enough processing power as I am not sure 89.6 Ghz is fast enough to even handle posting in forums...

And I thought my 75mhz Sun Sparcstation5 and 333mhz Sun Ultra10 boxes were speedy despite their tiny size... 

89.6 Ghz is awesome in the true meaning of the word!

GO SUN!

---

### Post by Dual Cortex on 2007-08-07
Why do they have to say it's '89.6GHz'.
Should just name it 89,600+

---

### Post by BarfBag on 2007-08-07
Yeah, baby!  How sexy!  I'm sure they get real warm, real quick.

That was perverted.

---

### Post by foxholeunder on 2007-08-07
I got so excited I forgot to answer the question posed by: amlucent23

Impact? 

If they play their cards right with this one they can surely turn the server world upside down...

Eventually, this will trickle down into the desktop/home computing market. Unless Intel or AMD has something up their sleeves Sun can dominate the market from business to home virtually overnight.

Can you imagine the potential this power could have in a gaming system! X-Box, Nintendo, Playstation, etc... 

If you think about the technology here... This chip is capable of holding so much information on it at one single instant that technically an entire operating system could live within just the cpu and lots of overhead for extra items. 

With a little tweaking by making this a more permanent rom based technology and the days of hard drives are gone for good. SATA drives will collect dust alongside floppy drives in every geeks basement or shed or garage or strewn about the house or all of the above.

Super Computers the size of handhelds... Really this is not some breakthrough technology - It is a revolution for the entire computing industry large and small.

Amazing! Awesome! GO SUN!

---

### Post by Ocxic on 2007-08-08
89.6 GHz.... (drool) ... i think it's time i changed archatechures i think.. drool....

---

### Post by Bigbluecat on 2007-08-08
Hold on a second. The 89Ghz is somewhat misleading. 

The T2 has 8 cores, 64 threads and runs at 1.4GHz. 

The 89.6GHz seems to come from multiplying the 64 threads by the clock speed. 

Of course this will never happen as the system will need to deal with bus contentions and cahce misses etc.

So what you have is a still impressive 8 core risc machine clocked at 1.4 GHz.

---

### Post by PartisanEntity on 2007-08-08
The Register had an article about it yesterday:
[http://www.theregister.co.uk/2007/08/06/niagaraii_out_sun/](http://www.theregister.co.uk/2007/08/06/niagaraii_out_sun/)

---

### Post by ssam on 2007-08-08
you need a to be running a load of threads/processes to get the full power of these chips.

run top in a terminal. look at the figures for load averge in the top line. the numbers are the average load over the last 1, 5 and 15 mins (correct me if those times are wrong).

it basically tells you how many processes are waiting to use the cpu. (seehttp://en.wikipedia.org/wiki/Load_(computing) for more detail)

If you can't get that load above 64, then you can't take full advantage of the T2

Still i would not say no if they offered me one :-)

Also to note. even though you could put this on a FPGA, you would need a giant FPGA, and it would run much slower than the real chip.

---

### Post by RomeReactor on 2007-08-08
Watch [the third video]("http://www.sun.com/featured-articles/2007-0807/feature/index.jsp?intcmp=hp2007aug06_ultrasparct2_curtain")--**Chapter 3: Commodity Business Model**--onwards from minute 5, they mention plans for compatibility with Ubuntu (supposedly they actually have Ubuntu already running on the T2).

---

### Post by mzar on 2007-08-08
I wonder if the cpu can use at desktop. So nice to playing game.

---

### Post by daverich on 2007-08-08
mm yes.

Looking over those schematics I think it should work ok.

Not quite how i would've done it, but each to their own ;)

Kind regards

Dave Rich

---

### Post by Brunellus on 2007-08-08
> **amlucent23 said:**
> Sun has announced the release of a new 89 GHZ UltraSPARC Processor. Not only that but they will be releasing the blueprints as GPL! What impact do you think this will have on x86 processor market share and do you think this will cause more distros (namely ubuntu) to make (official) releases for SPARC architecture?...

[http://hardware.slashdot.org/hardware/07/08/07/2152245.shtml]("http://hardware.slashdot.org/hardware/07/08/07/2152245.shtml")

[URL="http://blogs.sun.com/jonathan/entry/sun_enters_the_commodity_silicon"]http://blogs.sun.com/jonathan/entry/sun_enters_the_commodity_silicon
[/URL]
I am interested to hear your thoughts.
Interesting.

GPL *hardware* is tough to do, since it costs you about 100 million USD to build a chip fab plant, not counting the costs associated with actually RUNNING the fab.

In practice, this opens Sun's architecture to tinkering by electronics hobbyists and other interested parties, but I'd be very surprised if anybody other than Sun started fabricating these chips on a large scale.

---

### Post by mips on 2007-08-08
> **Brunellus said:**
> 
In practice, this opens Sun's architecture to tinkering by electronics hobbyists and other interested parties, but I'd be very surprised if anybody other than Sun started fabricating these chips on a large scale.

Maybe the chinese will catch on. They are already doing a version of the MIPS arch called the Godson.

---

