---
title: "PSA -- We don't all run on x86"
date: 2006-03-23
forum: The Cafe
---

### Post by kadymae on 2006-03-23
Just a gentle reminder to all you kind people who donate your time to help your fellow man get Ubunutu and various bits of software up and running.

**Not everybody has a computer with an intel/AMD processor in it.**

I just came straight from the Beginners thread.  A gentleman is trying to get Firefox 1.5.1 to run on his Powerbook.

The problem is (a) the instructions he's following only mention the x86 file names and (b) there is no PPC Linux version of Firefox 1.5.1 -- at least not at the mozilla firefox site.

AFIAK, this gentleman will not get 1.5.1 on his PowerBook without grabbing the source code and doing a compile.

So please, the next time you hop in to write a how to, or help a fellow "Ubuntist" get something installed, try to remember to list the applicable PPC file names, or if there is no PPC version please make note of that.

(From my total n00b days, I was driven to tears of rage and frustration when , after locating the correct PPC tar.gz file, the only command line instructions I could find [file not avalible through synaptic] didn't work because they were all about how to open and run the x86 file, which was a different kind of zipped file.)

**It's a little thing, but it makes a HUGE difference**

Thanks.:D

---

### Post by dermotti on 2006-03-23
Well you have to remeber people answering the beginner threads may also be beginners themselves.  Not everyone knows about PPC.

---

### Post by John.Michael.Kane on 2006-03-23
kadymae I posted two links in the mac section, and in that post with the user wanting firefox to mac builds of firefox.

---

### Post by K.Mandla on 2006-03-23
Point taken. I have a friend who's keen on putting Ubuntu on an old PowerPC in his basement, just to run the BOINC client 24-7. I should try and help him out more. It would be a valuable learning experience for me.

---

### Post by kadymae on 2006-03-23
> Well you have to remeber people answering the beginner threads may also be beginners themselves. Not everyone knows about PPC.

Well, hopefully, this will educate them. :)

Seriously, it's an easy thing to overlook and I'm not out to crucify anyone who forgets, but if my posting this helps a few more of us remember to include PPC pointers when we help out, my work is done.

---

### Post by kadymae on 2006-03-23
> kadymae I posted two links in the mac section, and in that post with the user wanting firefox to mac builds of firefox.

You rock.

[Now, if only the original instructions the guy followed could be edited with links to the PPC files ... ;)]

---

### Post by ssam on 2006-03-23
i replied to the 2 links in the mac section. i put some packages up at [http://www.tygier.co.uk/linux/firefox.html](http://www.tygier.co.uk/linux/firefox.html)

---

### Post by kadymae on 2006-03-23
ssam:

\m/  

(You rock)

---

### Post by John.Michael.Kane on 2006-03-23
...

---

### Post by Arktis on 2006-03-23
I hope I don't come off as a jerk here...

Time for all the PPC users to think ahead.  Unfortunately, your chosen architecture will fade into obscurity over the next several years.  It's already kind of obscure as it is.  Apples make up the one real mass of PPC desktop computers out there, and their market share in this area isn't exactly that huge to begin with.  Their switch to intel chips comes as a big blow to PPC.  Even though I have always been a consumer of x86 platform hardware, I don't particularly like the reality of this -  I like variety, choices.

Yes, nobody should be ignoring PPC users whether it be developers or people offering support - for the time being.  However, it's time to start letting go.  Either that, or hold to the hope that someone will somehow create a new PPC based PC hardware company out of nowhere and be stunningly successful enough to keep PPC desktop computers alive.  But realisticly, the only OS that their hardware is going to be runnning is unix/linux.  Even OSX is unix based.

Time to move on, or just hope for someone with lots of startup cash and enough savvy to take the risk and keep the Power PC architecture alive.

---

### Post by kadymae on 2006-03-24
> your chosen architecture will fade into obscurity over the next several years.

Don't tell that to Mordorsoft.  After all it is what they chose for the XBox.  ;)

---

### Post by mostwanted on 2006-03-24
[QUOTE=kadymae]Don't tell that to Mordorsoft.  After all it is what they chose for the XBox.  ;)[/QUOTE]

Same with Nintendo and to some degree Sony (Cell is an evolution of PPC).

---

### Post by Virogenesis on 2006-03-24
Arktis, you're incorrect its more likely we'll see  aa growth in ppc being supported as the blade servers will be using cell chips and as we know  linux has fantastic  support for servers.

---

### Post by briancurtin on 2006-03-24
[QUOTE=kadymae]Don't tell that to Mordorsoft.  After all it is what they chose for the XBox.  ;)[/QUOTE]
yeah but that means nothing at all. a gaming system is meant to stay the exact way it is. it doesnt need support. when it breaks, they tell you to buy a new one. when its too old, you have to buy a whole new system. even if its a dying technology, it was not a bad idea at all for microsoft to use it in the xbox.

---

### Post by Arktis on 2006-03-24
[quote=kadymae]Don't tell that to Mordorsoft. After all it is what they chose for the XBox. [/quote]
[quote=mostwanted]Same with Nintendo and to some degree Sony (Cell is an evolution of PPC).[/quote]Perhaps I should have made it clearer that I was talking about *Desktop Computers*.

---

### Post by kadymae on 2006-03-24
> Perhaps I should have made it clearer that I was talking about Desktop Computers.

{weg}And I was making reference to the fact that people will attempt to install Linux on anything with a processor.{/weg} (Although, an article I read about the triple core PPC in the XBox over at Ars Technica made it pretty clear that the processor has such a unique design that anything but software optimised for it will run slowly.)

And, although PPC looks to be on its way out as a Desktop Environment, *it's not dead yet*, and it really would be nice if more people would remember that when writing up instructions.

Technical writing is a component of my job, so I guess I'm predisposed to notice/be nitpicky about this sort of thing.

---

### Post by Jucato on 2006-03-24
I think it's on the part of the OP to state what architecture he's using (x86, PPC, 64-bit, etc) and on the part of the one who will reply to read first if the OP mentioned he was using something other than x86 (or to ask the OP if it wasn't explicitly mentioned). Of course, sometimes we can presume the processor type from the computer type (a Powerbook is presumed to be PPC).

It's like someone telling an OP to use sudo gedit, when the OP says he's running Kubuntu. Or like an OP not stating he's running Kubuntu, so he gets answers that work only in GNOME. :D

---

### Post by Arktis on 2006-03-24
I agree in that if someone is requesting support, it's up to them to state their architecture.  If they don't, it's only natural to assume they are using x86.

Also, we can't support/develop for what we don't have.  We can assume that all that is required is a simple find/replace 386 with ppc (and in many cases this might be true; in such cases what's the big deal?) but that's irresponsible because we don't have the hardware to verify it.  *It's up to people with PPC to help with PPC.*  It's not up to the rest of us with x86 or AMD64.  We really can't do much more than simply acknowledge that the architecture exists.  Honestly, realisticly, I ask you: What else is there for one to do unless he/she actually owns the relevant hardware?

---

