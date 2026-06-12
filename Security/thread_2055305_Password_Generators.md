---
title: "Password Generators"
date: 2012-09-09
forum: Security
---

### Post by zioMattia on 2012-09-09
Hi to ALL Folks!!!

I want to explain my idea on passwords generators.

You can make it secure and really random by generating a random number and using it as a seed.

- generate a number
- use it as a seed
- generate the password

you can also make the user choose a seed or implement two button, start and stop, with a timer and measure the time elapsed to make a random, or generate the seed drawing a segment and measuring its length.

Examples of this are here on sourceforce also for linux:

~snip~

~snip~

obiously with Source Code!!!

you can also create more layer of randomless using a random number as seed and after generating another seed and so on!!!

Happy Coding to all happy, funny, kind, people using Ubuntu!!!
zioMattia

---

### Post by d3v1150m471c on 2012-09-09
so where is the actual source code for this program? I looked on sourceforge but all i found was a gigantic 4mb binary. maybe it has embeded images in the code and not some bloated code for a rootkit.

Anyways, you're suggesting initiating a password using characters ranging from [0-9]. i'm not sure why you're suggesting limiting the initial input to 10 characters instead of a minimal fullset of ascii. interesting. i was curious to see if this magic program could somehow compensate for the very restricted input but i couldn't find the source code anywhere. either way, since all your users passwords would be limited to an output of 0,1,2,3,4,5,6,7,8,9 i can imagine a witty script kiddie could breach their security with less time that it takes to code the attack. if the output is not limited to ten integers it's possible to pipe a number generator through the program and use the output to attack the clients using the same weak algorithm, assuming the 4mb of bloat doesn't make the attack far too costly.

---

### Post by Ms. Daisy on 2012-09-10
Bazinga.

---

### Post by movieman on 2012-09-12
Generating a random number and turning it into human-readable form is essentially what most password generators do.

Personally, I use 'dd if=/dev/random bs=16 count=1 | base64' and then take as many characters as seems reasonable for the site in question. Assuming the hash on the server is secure, it should be impossible to break other than by brute force.

Plus it doesn't require trusting anyone other than the kernel developers to get their RNG right.

---

### Post by jwright8 on 2012-09-13
Following quotes taken from both of your links:

> **zioMattia said:**
> 
~snip~


> 
It is Donationware: the money is for College, Books and to pay the computer and compiler.  Thanks. **Mattia** Tristo
> **zioMattia said:**
> 
~snip~

obiously with Source Code!!!

> 
 Enjoy it! **Mattia **Tristo
Your username is zio**Mattia**.  Just want to point out the obvious here.   Both uploads are also through the same username.

And.. really?  The tar.gz is 55.8 kb and the zipped archive is 4.6 MB!? 

Fishy doesn't even begin to describe the whole thing.  

At best, you're shamelessly plugging some poorly developed alpha software that actually doesn't even do what it's supposed to (if you're limited that severely, it can hardly be random).  

At worst, there is something malicious (whether intentional or not) in that 4.6 MB file.

Kind of as an aside... why on earth would you go to a site like this, with people on here that are obviously knowledgeable, and post this to try to sucker someone in (for whatever purpose)?  Shouldn't you go somewhere where people don't think and just click/install?  Maybe I'm dumb here, but I'd have to say "social engineering: you're doing it wrong."

---

### Post by rookcifer on 2012-09-14
> **jwright8 said:**
> Kind of as an aside... why on earth would you go to a site like this, with people on here that are obviously knowledgeable, and post this to try to sucker someone in (for whatever purpose)?  Shouldn't you go somewhere where people don't think and just click/install?  Maybe I'm dumb here, but I'd have to say "social engineering: you're doing it wrong."

I agree.  I downloaded the .zip archive, planning to inspect the source code.  The source code is apparently written in RealBASIC (very unusual) and appears to be binary (couldn't open it with anything but a hex editor).  Very suspicious indeed.  He says it's open source but he doesn't provide a single line of code.


I looked at the Linux binary with a hex editor and found several suspicious function calls.  I would stay away from this.

---

### Post by CharlesA on 2012-09-14
> **rookcifer said:**
> I agree.  I downloaded the .zip archive, planning to inspect the source code.  The source code is apparently written in RealBASIC (very unusual) and appears to be binary (couldn't open it with anything but a hex editor).  Very suspicious indeed.  He says it's open source but he doesn't provide a single line of code.


I looked at the Linux binary with a hex editor and found several suspicious function calls.  I would stay away from this.
With this, this thread is closed.

A 1 bean poster registered in September, no thanks.

---

