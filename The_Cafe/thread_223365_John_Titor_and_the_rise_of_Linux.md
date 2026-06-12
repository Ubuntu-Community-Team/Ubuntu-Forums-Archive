---
title: "John Titor and the rise of Linux"
date: 2006-07-26
forum: The Cafe
---

### Post by mister_p_1998 on 2006-07-26
Been running Ubuntu for around five months now, and the snowballing popularity of Ubuntu made me think about the words of "alleged" Time Traveller John Titor. He claimed to come from the future where all computers ran unix and there was a date bug due to appear in 2038 that would shut down all unix computers. He came back to our time to get an obscure ibm portable computer that could fix this bug. Something to think about.

---

### Post by WakkiTabakki on 2006-07-26
Well... The time-bug is a fact, much like the y2k-thing (due to an overflow in the integer return value from a system call getting the POSIX time. Actually unix probably won't shut-down, but it's suddenly gonna think it 1970 again, peace love and understanding, man!)...

How an obscure IBM portable would fix the problem, I can't even guess...
A less obscure solution would be to have the system call return a 64 bit integer value, but that would render that op-system nonbackward-compatible...

We do have about 32 years to figure it, though... :p 

/N

---

### Post by matthew on 2006-07-26
Finding the potential problem looks like the only thing he got right...

[http://en.wikipedia.org/wiki/John_Titor](http://en.wikipedia.org/wiki/John_Titor)

I'm not too worried. We have some time.

---

### Post by jstueve on 2006-07-26
they had YEARS to FIX the Y2K bug, and just LOOK what happened...

...

...

...

Oh well, nevermind then.

---

### Post by WakkiTabakki on 2006-07-26
lol!


Well, actually (just to kill the fun) the y2k-bug was mainly an application related problem. 
The y2k38 (hey! that looks cool) is much more serious, because it affects all POSIX operating systems (through the time_t struct)! 
The whole operating system along with all it's applications are suddely gonna think the vietnam war and Nixon are still raging...

Note, Windows is also a POSIX OP-sys!

/N

---

### Post by mips on 2006-07-26
I actually met John Titor in 2038, nice guy.

---

### Post by slimdog360 on 2006-07-26
> **mips said:**
> I actually met John Titor in 2038, nice guy.

you to huh, I met him a couple of years before that.

---

### Post by halfvolle melk on 2006-07-26
> **mister_p_1998 said:**
> ... there was a date bug due to appear in 2038 that would shut down all unix computers.


> Using a 64-bit value introduces a new wrap around date in about 290 billion years, on Sunday, December 4, 292,277,026,596 15:30:08 UTC. **However, this problem is not widely regarded as a pressing issue**
:mrgreen:

[http://en.wikipedia.org/wiki/Year_2038_problem](http://en.wikipedia.org/wiki/Year_2038_problem)

---

### Post by mips on 2006-07-26
> Using a 64-bit value introduces a new wrap around date in about 290 billion years, on Sunday, December 4, 292,277,026,596 15:30:08 UTC. **However, this problem is not widely regarded as a pressing issue**

I dunno if I'll be able to sleep tonight...

---

