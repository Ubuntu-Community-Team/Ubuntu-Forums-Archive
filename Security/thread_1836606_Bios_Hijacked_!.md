---
title: "Bios Hijacked !?"
date: 2011-08-31
forum: Security
---

### Post by Actonix on 2011-08-31
Though still disconcerted by recent events which I might go into down the line, I have started up this new thread in the hopes of rejuvenating interest at seeking resolution of the problems detailed in the original thread of same title as well as provide any genuinely interested parties of the original thread with a link to what I feel is the origin of said problems.

Though a majority did in fact offer much appreciated objective input and advice in the original thread in attempt at seeking resolution,
... any positive contribution was sadly overshadowed by a minority who decided to bypass objective enquiry and/or advice in favour of trying to belittle the problem out of existence by offering what, from their postings, I can only deem to be questionable and unqualified opinions and advice based mainly on supposition and a limited comprehension of specifics - in summary, their conclusions and beliefs were formed and based on unrelated, irrelevant observation and/or by having ignored the information provided or at least misrepresented and misconstrued, all in favour of assumption ...

... with a derailed thread and little by way of input from others with specific knowledge in areas directly related to the problem, I felt I had no choice but to ask that the original thread be closed - though unfortunately the problems as identified still persisted.

It might help if I once again detailed the problems here but I do not know if that really is necessary ?

Anyhow, I sincerely hope this thread can get back on track and though I do not add much by way of progress with the previously detailed problem I envisage that more could come about from collaborative effort as interest is revived, so without much further ado please find a link back to what I feel is more than likely the origins of the problem :-

*it might be a good idea to make copies of those thread as one peruses them not just for historical reasons but also as solution might be found lurking in any one of those threads which could well dissappear at any point in time.

[Full-Disclosure] Bios programming...
[http://lists.grok.org.uk/pipermail/full-disclosure/2005-March/032185.html](http://lists.grok.org.uk/pipermail/full-disclosure/2005-March/032185.html)

My findings indicate that the problem is actually more wide-spread than I initially thought and with the Rootkit sitting where it is, activated before any OS - removal is, I conclude, the only resolution.

I have made efforts in virtually all directions including trying to find out if any commercially available tools capable of identifying the rootkit or it's offshoots exists, to no avail, talk less being able to remove it.

The problem here is that many do not even realise their systems are compromised in the first instance and it appears will have little by way of being to do so unless one can identify a commercially available tool or is able to create one - not to mention that at the level it has been compromised those in control of the rootkit are able to do almost any and everything imaginable limited only by their imagination and understanding of the OS sitting up top.

My finding out about and tracing it to back to source was more intuitively lead than I would have hoped or liked to admit, mainly assisted by an intimate familiarity gained through involvement in I.T. spanning decades. The average user does not have any such benefit, and even if they did have an inkling that their systems have been somewhat compromised, on seeking resolution would have no choice but to go along with the supposition of others who, being ignorant of the facts and full of self-conviction in their abilities to diagnose the existence of such a rootkit, decided that the users problem is either an imagined one with solution existing in an unrelated area or one that has resulted from a bug unwitingly highlighted and/or brought about by the users actions.

I hope enough interest has or at least will be aroused by this or the original thread to encourage any and everyone to contribute positively and objectively to this fresh attempt and that resolution follows not too far behind - unless of course there is some valid justification that I am currently unaware of for not allowing this to happen.

---

### Post by cryptotheslow on 2011-08-31
If I remember correctly, you suspect or indeed know that some undesirable code is lurking in your BIOS.

Surely if it has been coded to protect itself from removal then the only real remedy is going to be to physically remove the BIOS chip from the board and use an EPROM programmer to recode it. Or better yet, replace the chip entirely with a known good one.

---

### Post by Actonix on 2011-08-31
> **cryptotheslow said:**
> If I remember correctly, you suspect or indeed know that some undesirable code is lurking in your BIOS.

Surely if it has been coded to protect itself from removal then the only real remedy is going to be to physically remove the BIOS chip from the board and use an EPROM programmer to recode it. Or better yet, replace the chip entirely with a known good one.


Yes indeed, you remember correctly, I can confirm it remains lurking intermingled with other code.

Thanks, sadly, though I am aware of the remedy you suggest it is not an option available to me, I did in fact post the same advice in the previous thread.

---

### Post by tubezninja on 2011-08-31
> **Actonix said:**
> 
Thanks, sadly, though I am aware of the remedy you suggest it is not an option available to me, I did in fact post the same advice in the previous thread.

I'm not sure exactly how we're supposed to assist you then.  Wiping the EEPROM or full replacement of the BIOS appears to be the only way to effectively eliminate this problem... it's the only way to be sure.

---

### Post by cryptotheslow on 2011-08-31
@tubezninja - I'm glad I'm not the only one who thinks this way - you did pick me up on one thing though... EEPROM rather than EPROM. Which from my understanding means the chip can only be overwritten electronically rather than by dosing it with UV.

Which adds yet more weight to the argument that the OP needs to source a new, preferably blank BIOS chip and program it with his chosen code. I say this on the assumption that surely with a chip that can only be overwritten electronically, if malicious code is loaded onto it, that same code could alter the mechanism for re-writing and thus preserve itself. (?)

Or indeed, if someone had the time, the code could be written to shadow itself to say a video card BIOS in the system, which on seeing the code had been removed from the mobo BIOS, replicate itself back there.

Anyways up, trying to definitively eradicate it with the chip in situ would seem to be a losing battle if the code in question has been crafted to be self-preserving.

All seems somewhat unlikely as it would have to very specific code suited to the machine in question.

^^ The above is all just speculation on my behalf, I'm not an electronics engineer nor am I a coder of any merit. So take from it what you will.

---

### Post by cariboo on 2011-09-01
As most motherboards have none replaceable bios ICs, the only real solution is a new motherboard.

Another thing the op can try is [coreboot]("http://www.coreboot.org/Welcome_to_coreboot"), of course it should only be installed from read-only media, then once the installation completes, use something like a bootable [Dban]("http://www.dban.org/") cdrom to completely wipe the hard drives.

Once everything is completely wiped clean, only install an OS from a trusted source, then if from what I understand from the op's links, never install software from any random website.

---

