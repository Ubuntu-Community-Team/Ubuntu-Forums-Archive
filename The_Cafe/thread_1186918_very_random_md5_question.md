---
title: "very random md5 question"
date: 2009-06-14
forum: The Cafe
---

### Post by renkinjutsu on 2009-06-14
if the md5sum for every file is as 'unique' as they say it is.. i wonder if it's possible to be able to reverse the process and use the md5sum to generate a file!

i was thinking this because md5sums are usually used for large files to check for integrity of the downloaded file.. but a lot of people have slow connections, and if the connection is slow and flaky, that increases the chances of downloading a corrupt file. I was wondering if it's possible to even consider being able to paste a code on a webpage, and have people copy it into their terminals and have the files miraculously generated using the md5sums (or any other checksums) ... that would be so awesome.. would save a lot of bandwidth also!

---

### Post by swoll1980 on 2009-06-14
Oh no! Not this again!

---

### Post by renkinjutsu on 2009-06-14
are you serious?! i thought this was such an original topic.

---

### Post by swoll1980 on 2009-06-14
> **renkinjutsu said:**
> are you serious?! i thought this was such an original topic.

It's not. Trust me.

---

### Post by OutOfReach on 2009-06-14
Yes I've seen this topic at least once here before

---

### Post by renkinjutsu on 2009-06-14
original or not, i still want to *know* if it's actually possible


my unimaginably tiny mind is screaming "YES IT IS!!"
but then again, if it is, people would be doing this already. Am i wrong?

---

### Post by swoll1980 on 2009-06-14
Look at it this way. An md5 sum is not unique. It is just the final hash tally. Lets make this super easy, and use the number 10. Let's say the md5 sum is ten, the computer could generate a file with an md5sum of ten, but it won't be the same file you want. The computer doesn't know how to get to 10. It could do 5+5=10 1+1+1+1+1+1+1+1+1+1=10 2x2+6=10 9-1+2=10 see where I'm going with this, and this is just a 2 digit number. When you scale this to a full md5 sum there are millions, and millions of ways to get one "unique" md5 sum.

---

### Post by kevdog on 2009-06-14
Look up the definition of a hashing algorithm and pay close attention to the one way description.

---

### Post by Junkieman on 2009-06-14
Oh how great this would be! Hahaha! :mrgreen: 

As an interesting exercise, imagine some tells you the file is 1K big, and gives you the hash. You could generate each possible permutation of that 1K and check the hash each time, and when the hashes match, you have recreated the file!

Hmmm this sounds familiar... Oh wait, it's called brute-force password cracking harhar! No seriously, but instead of trying to guess a password of 7 characters, you're talking about a 1K length password.

You will wait for years to generate all those permutations! You can (obiously) use [rainbow tables]("http://www.codinghorror.com/blog/archives/000949.html") to cut down the time, but then you need plenty disk space for the generated table: lowercase alpha-numeric of a 1-7 length string would be [80,6 billion words]("http://www.freerainbowtables.com/faq/"). Yikes! Now add in the full spectrum of characters and BAM, before you know it your swap file will start spewing sparks and smoke.

We don't have the computing power to do this in any real time; maybe in about a thousand years or so, at least when us average users have [quantum PC's]("http://en.wikipedia.org/wiki/Quantum_computer") in our homes ;)

---

### Post by MasterProg on 2009-06-14
Imagine brute forcing a 700 MB Ubuntu image. 700 MB is 734003200 bytes. Each byte can take 256 possible values, so total possible number of different 700 MB files is 256^734003200. Brute force will last like an eternity...

But if it was possible, it would be the best compression technology ever. xD

---

### Post by Tipped OuT on 2009-06-14
> **Junkieman said:**
> 

**We don't have the computing power to do this in any real time**; maybe in about a thousand years or so, at least when us average users have [quantum PC's]("http://en.wikipedia.org/wiki/Quantum_computer") in our homes ;)

We don't, but some one does... some one who owns a super computer that can crack complex codes in a blink of an eye. I wish I had one. =[

---

### Post by MasterProg on 2009-06-14
This task is too complex, at least for now. All the supercomputers put together wouldn't recover an Ubuntu image from its MD5.

---

### Post by Junkieman on 2009-06-14
> **MasterProg said:**
> This task is too complex, at least for now. All the supercomputers put together wouldn't recover an Ubuntu image from its MD5.
By the time we have super computers they'll probably be controlled by [HAL 9000]("http://en.wikipedia.org/wiki/HAL_9000") or somthing similiar ;)

---

### Post by MasterProg on 2009-06-14
We already have supercomputers compared what people had 10 years ago. xD 

Those scientists will always have faster computers than we have and it's perfectly normal.

---

### Post by mister_pink on 2009-06-14
Its not just about how complex a task it would be, its simply not possible. As someone else said there are multiple possible files that can match one hash. This has to be the case - think about it in the normal direction, you're compressing information into a much smaller space so there has to be collisions - theres billions of orders of magitiude more permutations in the possible files than there are in hashes.

The usefulness of the hash lies in the fact that its incredibly difficult to deliberately manufacture a file that has the same hash as another, and could thus be unknowingly be swapped for it. Some algorithms have been shown to have flaws allowing such collisions to be made deliberately, but to be able to make a collision and also specify that it contains your malicious code adds another layer of difficulty.

---

### Post by ssam on 2009-06-14
> **MasterProg said:**
> This task is too complex, at least for now. All the supercomputers put together wouldn't recover an Ubuntu image from its MD5.

md5sum is 128 bits. so there are 2^128 possible md5sums (about 3.4×10^38, a very big number).

an iso file is about 700 MBytes = 5.6 GBits = 5,600,000,000 bits. so there are 2^5,600,000,000 possible 700MB files. so for each MD5sum there are about 2^5,600,000,000 / 2^128 possible files (of that exact size). thats a very big number.

when 2 files have same hash, that's called a collision. if you generate 3.4×10^38 random files you will have some that give you the same md5sum. so if you set a computer trying to recreate a file to match a md5sum, it will (eventually) create such a file, but it probably won't be what you want.

there are weaknesses in the MD5 algorithm that make it a bit easier to create colliding files, so people are begining to move to more advanced checksums like sha256.

---

