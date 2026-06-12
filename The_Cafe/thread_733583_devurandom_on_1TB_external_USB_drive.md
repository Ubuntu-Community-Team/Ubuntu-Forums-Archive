---
title: "/dev/urandom on 1TB external USB drive"
date: 2008-03-24
forum: The Cafe
---

### Post by blastus on 2008-03-24
I am writing random data to my new 1TB external USB drive from /dev/urandom. I started the dd process yesterday morning and have been monitoring progress with "sudo pkill -USR1 ^dd$" At about 3.2MB per second, it will take about 4 days to fill the drive.

Why is /dev/urandom so extremely slow and CPU intensive (usage is always near 100%)? Is there a faster alternative to /dev/urandom? I wanted to use DBAN (which is several times faster than /dev/urandom) but it does not recognize external USB drives.

---

### Post by hhhhhx on 2008-03-24
wow, i didnet know they made 1TB usb drives

and also, sweet!

---

### Post by Ocxic on 2008-03-24
it takes so long because it not only has to calculate a random piece of data for every bit on your drive, but it is also writing to EVERY single bit on the drive, takes about 4-5 hours to do my 500GB drive with just /dev/zero

---

### Post by happysmileman on 2008-03-24
Possibly because it has to generate 3.2MB of (pseudo-)random data every second, which would be over 800,000 calls to rand() (or whatever makes the numbers) each second.

---

### Post by init1 on 2008-03-24
Would /dev/zero work? Its not random, but it may be faster.

---

### Post by blastus on 2008-03-24
> **xhhux said:**
> wow, i didnet know they made 1TB usb drives

and also, sweet!

I think there are 3TB USB drives now :)

[QUOTE=Ocxic]it takes so long because it not only has to calculate a random piece of data for every bit on your drive, but it is also writing to EVERY single bit on the drive, takes about 4-5 hours to do my 500GB drive with just /dev/zero[/QUOTE]

But the PRNG in DBAN is way faster, like 10 times faster than /dev/urandom on my machine. With DBAN and an internal hard drive, the write speeds are like 30-40MB/s.

[QUOTE=happysmileman]Possibly because it has to generate 3.2MB of (pseudo-)random data every second, which would be over 800,000 calls to rand() (or whatever makes the numbers) each second.[/QUOTE]

I wonder if there is a physical device that can generate secure random numbers? The crypto-chip in new model computers can generate pure random numbers. As hard drive sizes increase, I can see /dev/urandom becoming unfeasible for this sort of thing.

[QUOTE=init1]Would /dev/zero work? Its not random, but it may be faster.[/QUOTE]

Not for my purpose. I want to fill the device with random data before creating a dm-crypt (encrypted) partition on it. No data has ever been written to the device.

---

### Post by happysmileman on 2008-03-24
> **blastus said:**
> I wonder if there is a physical device that can generate secure random numbers? The crypto-chip in new model computers can generate pure random numbers. As hard drive sizes increase, I can see /dev/urandom becoming unfeasible for this sort of thing.

I think I've seen USB devices that generate random numbers, not exactly sure how they work, I think it's to do with static electricity or something, I've also seen software that claims to make pure random numbers using your sound card but I could never get them to work.

---

### Post by blastus on 2008-03-24
> **happysmileman said:**
> I think I've seen USB devices that generate random numbers, not exactly sure how they work, I think it's to do with static electricity or something, I've also seen software that claims to make pure random numbers using your sound card but I could never get them to work.

I don't know how they would work either but I think they'd have to tie into something that isn't exactly predictable like; thermo-temperature, vibration, atmospheric pressure, humidity etc... if I could find one I think I'd be the only person on the block with it :lolflag:

---

### Post by Polygon on 2008-03-24
i bet part of the long delay is that your writing to a usb drive which is much much slower then writing to a hard drive thats connected with SATA or IDE

---

### Post by jpkotta on 2008-03-24
I know some processors (not necessarily desktop ones) use ring oscillators.
[http://en.wikipedia.org/wiki/Ring_oscillator](http://en.wikipedia.org/wiki/Ring_oscillator)

You may want to check out the shred command.

---

### Post by Xzallion on 2008-03-24
> **blastus said:**
> I wonder if there is a physical device that can generate secure random numbers? The crypto-chip in new model computers can generate pure random numbers. As hard drive sizes increase, I can see /dev/urandom becoming unfeasible for this sort of thing.

I don't think theres a way for a computer to get a "true" random number.  Based on the wikipedia article on [Random Number Generators]("http://en.wikipedia.org/wiki/Random_number_generator") this is only hinted at using a physical input such as sound, temperature or time as a seed and hoping its random.  Unfortunately these tend to develop their own bias.

---

### Post by mridkash on 2008-03-24
I'm curious.
Can you please tell how filling up hd with random numbers help in securing the system, and why not just zeroes.

Thanks a lot.

---

### Post by Polygon on 2008-03-24
since he is going to be encrypting his hard drive, he wants to first fill the drive up with random data before he starts writing encrypted data to the disk so its harder if not impossible to tell which is random data and what is encrypted data

what is more secure:

00000000Jk326%$^jnbpj3r2JKL000000000000

or
Hj234r ef2prjrj23r^&*4500KGVBjwn238*/3(234

---

### Post by blastus on 2008-03-24
An attacker won't sample zero'd data because he knows right away that it isn't real data. However, if the drive is filled with random data before the encrypted data was written, and the sample data taken from the drive just happens to be the random data, it can't be decrypted and therefore the attacker will have wasted a bunch of time. By filling the drive with random data, an attacker will not be able to distinguish the random data from the encrypted data. 

This seems to imply that the less encrypted data you have on a drive that was previously filled with random data, the better because it increases the likelihood that sample data taken from the drive is really just random data. Filling a drive with random data won't increase the strength of your pass phrase or encryption algorithm.

---

### Post by cprofitt on 2008-03-24
Yep 0's and 1's are good for removing data, but not so good when encrypting or hiding data.

---

### Post by Washer on 2008-03-24
why not just make a huge truecrypt container? Or lots of them, which is what I do to help me arrange files.

school
linux
firefox
pr0n video
pr0n pix
music
etc

---

### Post by Washer on 2008-03-24
> **blastus said:**
> I wanted to use DBAN (which is several times faster than /dev/urandom) but it does not recognize external USB drives.
what?

---

### Post by init1 on 2008-03-24
Use /dev/dsp and then play some music

---

### Post by krolaw on 2008-04-24
Check out frandom - 50x faster than urandom, although I'm only getting 5x on my TB drive.

---

### Post by grikdog on 2009-03-15
> **blastus said:**
> I am writing random data to my new 1TB external USB drive from /dev/urandom. I started the dd process yesterday morning and have been monitoring progress with "sudo pkill -USR1 ^dd$" At about 3.2MB per second, it will take about 4 days to fill the drive.

Why is /dev/urandom so extremely slow and CPU intensive (usage is always near 100%)? Is there a faster alternative to /dev/urandom? I wanted to use DBAN (which is several times faster than /dev/urandom) but it does not recognize external USB drives.

Dunno why it's slow, but why not just use /dev/urandom to fill a MB or so, then use that file to stamp a copy of the MB image all over the USB drive?  Sure, it's not "random" anymore, but nobody can read the USB drive either (not in your lifetime).

Or, why not just blast the output from Mersenne Twister continuously over the 1T drive?  If you use /dev/urandom to fill the internal table (instead of seeding the MT), the result should be "good enuff."  MT is very fast.  You could also XOR the MT output with an additive congruential generator's output for almost no additional overhead.  The result is functionally equivalent to spinning a coin for each bit independently.  If you have access to Macintosh OS X, use their /dev/urandom to generate your keyfile (destroy after use), because it uses Bruce Schneier's yarrow algorithm, and I'm not sure what Debian cobbled together.  I was trying to find an answer to THAT question when I noticed your question.

And, of course, your photo caught my eye.  Your average male geek is 90 times more likely to puff up, spread tail feathers and provide help to alleged damsels in distress.  Thanks for the fantasy ;-)

---

