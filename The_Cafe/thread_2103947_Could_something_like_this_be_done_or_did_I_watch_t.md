---
title: "Could something like this be done or did I watch too many movies?"
date: 2013-01-11
forum: The Cafe
---

### Post by Thee on 2013-01-11
Hey

Got an idea yesterday, that maybe some programmer could answer me best. I need thinking out of the box for a second.
Maybe you will laugh, but what the heck, if this is not possible, at least I'll be a little smarter after the discussion or maybe start a good concept for a SF movie :)

Anyway, my idea is about "downloading" (copying a file) and possibility to speed things up only using software, and not upgrading hardware or your internet connection.

So, how this would work...

As I understand, when you download a file, the download manager reads the file byte by byte and copies it to your HDD. Is that correct? If it is, read on...

What if you didn't need to download the actual file? What if the download manager can make an exact local copy of the file you want to download only by getting some information from the Server about the file.

How this would work:
The Client sends the download request for a file to the Server. Then the Server analyses that file and says to the Client: Im not going to send you such a large file psychically, it will take too much time and bandwidth, instead Im gonna send you signals that will perfectly describe how this file looks like, and then you can use this information that I give you and make a local copy of the same file that exists here.

So it's like this: don't send me a psychical file, send me a description of that file, and I will make it psychical here locally.

I have no idea really how that would work, maybe the Server would say "ABC" and the client would know he has to write some information that code "ABC" represents.

So instead of downloading 1 MB of some data, the server would send a code "ABC" (for example) and the client would know what that means, and make an exact copy of that 1 MB of data. So if sending the information "ABC" is quicker then downloading 1 MB of actual data, then you would "download" that 1 MB of data faster with the same internet connection, thus boosting the speed needed to copy something over the internet.

Now this probably is not possible, but I want to know why?

And if there is some kind of workaround to achieve something similar to this. I mean, do we really need to download something? Cant we just clone it locally based on information sent? Or would that get to a point of diminishing returns?

So fiction or plausible?

---

### Post by MG&amp;TL on 2013-01-11
Perfectly plausible, this is what happens (If I understand you correctly) with compression, i.e. downloading a zip file. Problem is, compression isn't that good, so "ABC" wouldn't work too well.

---

### Post by dannyboy79 on 2013-01-11
i don't think this would work for say a movie, if you wanted to download a movie, theres no amount of data the server could provide for the client to "make" that movie locally.

cool idea however

---

### Post by Paqman on 2013-01-11
Yep, you've just described compression.

Say you have a file containing the following data:

AAABB BBCCC CCDEE (15 "bits")

A compression algorithm might shorten that down to:

3A 4B 5C D 2E (9 bits)

The compressed file doesn't contain the original data, it contains "signals that will perfectly describe how this file looks like" as you put it.

Compression is used to speed up connections. It's used on the server side somewhat, and the old Opera Mini browser for phones used to compress all traffic to try and make browsing on a nasty GPRS connection tolerable.

---

### Post by Thee on 2013-01-11
Ok, so I invented ZIP, great :) '89 here I come.

So basically what you guys are saying is, we are already achieving this by using compression, there is no other magical way to do this stuff better then what we are already doing?

---

### Post by koenn on 2013-01-11
> **Thee said:**
> 
So basically what you guys are saying is, we are already achieving this by using compression, there is no other magical way to do this stuff better then what we are already doing?

Well, 2 things
1-
"compression" is a broad generic term. There are many compression algorithms. It's not impssoble to come up with a new one

2- hash/fingerprint functions, maybe ?
Theoretically, each file produces a unique hash. 
So if the server sends you a hash of the file you requested, all you have to do is recreate a file that, given the function, creates the same hash. You then know that the file you created is identical to the one on the server.

Unfortunately, creating the correct file may be difficult.

---

### Post by Thee on 2013-01-11
> **koenn said:**
> Well, 2 things
1-
"compression" is a broad generic term. There are many compression algorithms. It's not impssoble to come up with a new one


Yeah I know that, but its not possible in a way that I described, or it is possible but not practical enough.


> 
2- hash/fingerprint functions, maybe ?
Theoretically, each file produces a unique hash. 
So if the server sends you a hash of the file you requested, all you have to do is recreate a file that, given the function, creates the same hash. You then know that the file you created is identical to the one on the server.

Unfortunately, creating the correct file may be difficult.

Not really sure how that works, but it sounds interesting.
Is there any "proof of concept" on a small scale for those functions used in the matter I described?

---

### Post by MG&amp;TL on 2013-01-11
> **Thee said:**
> 
Not really sure how that works, but it sounds interesting.
Is there any "proof of concept" on a small scale for those functions used in the matter I described?

"One-way" compression is often a good way to check file integrity, i.e. MD5sums.

You can generate a unique hash from a file like this:

```
md5sum <file>
```...but try recreating that file and it's (hypothetically at least) a one-way process without a lot of time and computing power.

---

### Post by squenson on 2013-01-11
You can have a look at [fractal compression]("http://en.wikipedia.org/wiki/Fractal_compression"). The benefits are very large compression factors, unfortunately, the time to compress a file is extremely long.

---

### Post by koenn on 2013-01-11
> **MG&TL said:**
> ...  without a lot of time and computing power.

yeah, in a worst case scenario you'd have to brute-force it, ie  start from an empty file and create all possible files until one checks out. 


otoh, iirc, rsync uses a sort of "reuse parts of existing files on the destination system to reduce data transfer" approach. It's mostly used to "sync" two copies of supposedly the same file, but I think such algorithm could also be applied between unrelated files.  Like "rsync" (remote) picture A against (local) picture B, to convert picture B into (local) picture A.
The problem then becomes : how to find a suitable file. 

rsync --fuzzy seems to be going in that direction



And in the end it's always a trade off between bandwidth and processing, and their relative costs.

---

### Post by sdowney717 on 2013-01-11
The instructions to create the file would exceed the file size. IMO.

Like a superset above the final product necessarily would be much more complex in nature.

---

### Post by koenn on 2013-01-11
> **sdowney717 said:**
> The instructions to create the file would exceed the file size. IMO.

Like a superset above the final product necessarily would be much more complex in nature.

so wrong.

compare :

a/ a text file containing the lyrics of "99 bottles of beer on the wall" 

b/ a script or program that prints out the lyrics of  "99 bottles of beer on the wall" (or outputs them to a text file)


guess which one will be, more often than not, be the shorter / smaller file ?

---

### Post by sdowney717 on 2013-01-11
> **koenn said:**
> so wrong.

compare :

a/ a text file containing the lyrics of "99 bottles of beer on the wall" 

b/ a script or program that prints out the lyrics of  "99 bottles of beer on the wall" (or outputs them to a text file)


guess which one will be, more often than not, be the shorter / smaller file ?

I think your example idea is producing a file that is simple repetition.

How could you make an infinitely more complex document. You can not. This feels like the idea of a million monkeys hitting a keyboard could produce the entire complete text of a Shakespearean play in the original order. Not in a trillion years.

---

### Post by koenn on 2013-01-11
> **sdowney717 said:**
> I think your example idea is producing a file that is simple repetition.
How could you make an infinitely more complex document. You can not. This feels like the idea of a million monkeys hitting a keyboard could produce the entire complete text of a Shakespearean play in the original order. Not in a trillion years.



The point of **all** compression is to look for repeating patterns, and reproduce them; and often to do so requires less information than the actual file. 
That "Bottles" program example is in fact a special purpose compression, optimized for "text files containing lyrics of '99 bottles of beer'".

There exist files that are sufficiently random that compression doesn't work, and where the overhead produces a slightly larger file than the uncompressed file. That too is a special case. 

The infinity monkey theorem has got nothing to do with any of this, though it has some bearing on the "brute force hash" solution i mentioned in an earlier post. 

Try to keep up.

---

### Post by Paqman on 2013-01-11
> **sdowney717 said:**
> I think your example idea is producing a file that is simple repetition.


Real world data contains lots of repetition. Which is why compression works.

---

### Post by Artemis3 on 2013-01-11
Things like this have been done to a limited extent with certain media types, or generally with compression (with compression your "description" simply takes a lot of space, usually half the actual content).

With "midi" files, for example, you have to have the sound samples, and the files only contain the notes to be played. With sound "tracker" formats, these samples are also bundled with the file.

Vector image formats are also instructions to draw pictures, not the pictures themselves.

---

### Post by TOMBSTONEV2 on 2013-01-11
These are the kind of threads microsoft probably keeps an eye out for. Next time, try to avoid asking a bunch of potential idea thieves for help on your great ideas. :p As for your idea, pretty much compression no matter how you cut it. Just different types as already stated. 

Always good to keep thinking though, you hit a really good idea. Just been done before.

---

### Post by zombifier25 on 2013-01-11
> **Artemis3 said:**
> Things like this have been done to a limited extent with certain media types, or generally with compression (with compression your "description" simply takes a lot of space, usually half the actual content).

With "midi" files, for example, you have to have the sound samples, and the files only contain the notes to be played. With sound "tracker" formats, these samples are also bundled with the file.

Vector image formats are also instructions to draw pictures, not the pictures themselves.

So I'm not the only person who listen to tracker music. Yay

---

### Post by Thee on 2013-01-11
> **Artemis3 said:**
> 
With "midi" files, for example, you have to have the sound samples, and the files only contain the notes to be played.

Yeah, I know how midi works, and that's a very good example of what I was thinking with this idea. But instead of samples, maybe you have on your hard drive a partial data that looks exactly like the data that you are trying to download, then it borrows a part of that file, that is already there on your HDD, instead of downloading it again. Of course in order for this to work, the software that does this would need to somehow map your HDD's and recognize what he needs and where that is and add it to the file you are downloading.


> These are the kind of threads microsoft probably keeps an eye out for. Next time, try to avoid asking a bunch of potential idea thieves for help on your great ideas :P

Of course, what else would Bill be doing in his free time other then browsing Ubuntu forums :P

---

### Post by 3rdalbum on 2013-01-12
I understand. An obvious example would be file headers. Rather than downloading a jpg header every time, the server would say "right, this is a JPEG" and the client would just substitute a JPEG header. However this would barely save any space as file headers are typically quite small.

A cool example I can think of would be: You have two MP3s on your computer: Super Trooper by ABBA, and Jump by Van Halen. You want to download the mashup of these two songs by MMM. Rather than have to download a whole new MP3, the server can actually instruct your computer about how the mashup was made of those two songs, and your computer simply reconstructs it from your existing MP3s.

It seems a bit limited in application; other people have mentioned vector graphics and such which are basically a very similar idea already in practice. Still it's a very cool concept!

---

### Post by ssam on 2013-01-12
> **koenn said:**
> 
2- hash/fingerprint functions, maybe ?
Theoretically, each file produces a unique hash. 
So if the server sends you a hash of the file you requested, all you have to do is recreate a file that, given the function, creates the same hash. You then know that the file you created is identical to the one on the server.

Unfortunately, creating the correct file may be difficult.

hashes are not unique, it is just that hash collisions are rare (and for a good hash algorithm it is hard to find the collision).

for example suppose you take a 1MB file (8 million bits) and a 25 bit hash. there are 2^8000000 possible 1MB files (in normal notations this is a number with 2.4 million digits, so it wont fit in this post). there 2^256 possible hash values (only 115792089237316195423570985008687907853269984665640564039457584007913129639936). So for each possible has there must be many possible files.

for roughly the same reason a lossless compression algorithm can't guarantee to be able to compress every file.

if you take the
AAABB BBCCC CCDEE (15 "bits") -> 3A 4B 5C D 2E (9 "bits")
example from above, you can see that some inputs (actually most) can't be compressed
ABDED CADEA DCAEC (15 "bits") -> 1A 1B 1D 1E 1D 1C 1A 1D 1E 1A 1D 1C 1A 1E 1C (30 "bits")

compression only works if there is redundancy in the input that can squeezed out.

---

### Post by mips on 2013-01-12
I think you watched to many movies. You can't really create something out of nothing.

---

### Post by koenn on 2013-01-12
> **ssam said:**
> hashes are not unique, it is just that hash collisions are rare (and for a good hash algorithm it is hard to find the collision).

for example suppose you take a 1MB file (8 million bits) and a 25 bit hash. there are 2^8000000 possible 1MB files (in normal notations this is a number with 2.4 million digits, so it wont fit in this post). there 2^256 possible hash values (only 115792089237316195423570985008687907853269984665640564039457584007913129639936). So for each possible has there must be many possible files.

Well, I said "theoretically" - and even so, I don't know enough math to be conclusive. So yes, it's "lossy" in that the file you get is not necessarily identical to the file you requested.

In any case, what you describe, although it's correct, is merely implementation. As you demonstrate, the collision probability will depend on the size of the hash in relation to the key space (how large are the files vs how large are the hashes). With large hashes and relatively small source files, you could get (near) zero collision.

Whether that would at all be practical, I don't know. Is there a reasonable change that sufficiently large hashes would be so big that, overall, you don't gain anything ? Probably, yes. Do I think it's likely you can  save on transfer cost with something like "fuzzy rsync" or similar techniques ?  Again, yes.

---

### Post by Warpnow on 2013-01-12
This is basically how filetypes work.

---

### Post by lisati on 2013-01-14
> **koenn said:**
> The point of **all** compression is to look for repeating patterns, and reproduce them; and often to do so requires less information than the actual file. 
IMO it's not just repetition but redundancy can be used as well.

Some of the compression algorithms I've briefly looked at go over my head, but one which is a bit easier to grasp is the case of a simple ASCII text file with no fancy formatting, UTF or anything like that. In such a scenario only 7 out of every 8 bits would typically be used, making it unnecessary to transmit the full 8 bits for every byte. Yes, I know, not a particularly massive saving in space and bandwidth in this example, but the idea of an algorithm optimised for a particular kind of data has been used, e.g. jpeg.

---

### Post by Cheesemill on 2013-01-14
A similar process is used by the zsync file transfer program.

I download the 13.04 testing images which are updated every day. By using zsync the latest version is checked against the version already on my machine, and only the pieces of the iso file that are different to the ones I already have are downloaded.

In the example below you can see that zsync realised I already had 91.4% of the file on my machine, so I only had to download 70MB to get the new iso instead of the entire 800MB file.

```
rob@arch:~/ISOs/Linux/Ubuntu/Raring$ zsync http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso.zsync
#################### 100.0% 323.8 kBps DONE     

reading seed file raring-desktop-amd64.iso: ***************************************************************
***********************************************************************************************************
***********************************************************************************************************
***********************************************************************************************************
***********************************************************************************************************
***********************************************************************************************************
***********************************************************************************************************
*************************************************************
Read raring-desktop-amd64.iso. Target 91.4% complete.      
downloading from http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso:
#################### 100.0% 1645.9 kBps DONE     

verifying download...checksum matches OK
used 749846528 local, fetched 70852261
rob@arch:~/ISOs/Linux/Ubuntu/Raring$ 
```

---

### Post by mips on 2013-01-14
I'm beginning to think people are missing what the OP proposes.

He's not talking about compression, most files on the net you download are already heavily compressed.

He seems to be talking about creating a file locally from nothing but something akin to a MD5 Hash sent by the far end.

I'm no mathematician but this is not going to happen with normal algorithms unless we start delving into Quantum teleportation.

---

### Post by ssam on 2013-01-14
> **koenn said:**
> Well, I said "theoretically" - and even so, I don't know enough math to be conclusive. So yes, it's "lossy" in that the file you get is not necessarily identical to the file you requested.

In any case, what you describe, although it's correct, is merely implementation. As you demonstrate, the collision probability will depend on the size of the hash in relation to the key space (how large are the files vs how large are the hashes). With large hashes and relatively small source files, you could get (near) zero collision.

Whether that would at all be practical, I don't know. Is there a reasonable change that sufficiently large hashes would be so big that, overall, you don't gain anything ? Probably, yes. Do I think it's likely you can  save on transfer cost with something like "fuzzy rsync" or similar techniques ?  Again, yes.

for there to be enough possible hashes for all the possible files you would need the hash to be as big as the file.

most real files do have enough redundancy to allow compression. many transfer protocols (http, rsync, ssh) have compression options to enable lossless compression. some mobile web browsers can connect to a proxy server that does lossy compression.

---

### Post by coldraven on 2013-01-14
> So it's like this: don't send me a psychical file, send me a description  of that file, and I will make it psychical here locally.
You have already solved the problem! With your psychic files all you have to do is think of a file and it will immediately appear on your PC.  :)
Wow! I want a psychic computer too!  :lolflag:

---

### Post by Thee on 2013-01-14
I meant to write physical :)

In any case, what I was asking originally is, can something be created out of nothing (or by borrowing parts of bits already on the computer), just by getting information of how that file looks like.

Just like Cheesemill said, something similar to zsync, but unique in its own way. Zsync is the closest to this.

---

### Post by MG&amp;TL on 2013-01-14
> **Thee said:**
> 
Just like Cheesemill said, something similar to zsync, but unique in its own way.

Feel  free to write it/ modify zsync. ;)

---

### Post by mips on 2013-01-14
> **Thee said:**
> 
In any case, what I was asking originally is, can something be created out of nothing...


NO, not unless you are into sorcery or witchcraft.

---

### Post by koenn on 2013-01-14
> **mips said:**
> NO, not unless you are into sorcery or witchcraft.

any sufficiently advanced technology ...

---

### Post by koenn on 2013-01-14
> **lisati said:**
> IMO it's not just repetition but redundancy can be used as well.


mm yeah. I emphasised the repetition a bit because someone said I was cheating with the 99 bottles of beer example earlier on - which, as it happens, was a real life example of bandwith saving from the 90s: [http://www.99-bottles-of-beer.net/info.html](http://www.99-bottles-of-beer.net/info.html)


obviously, repetition is redundant.

In your 7 bit ascii example, I could(*)  also argue that it's a repetition  : for every character : send 7 bits , skip 1



(*)if I were in a pedantic mood, which today, I'm not.

---

### Post by koenn on 2013-01-14
> **ssam said:**
> for there to be enough possible hashes for all the possible files you would need the hash to be as big as the file.


hm ... 
more accurately (I think) : given an algorithm that produces hashes of a fixed length,  for the probability of collisions to be near 0, there will be many cases where the hash is equal or larger in length than the source file and the net result will be 0 - you win some, you loose some. 

But, regardless, it's an extreme long shot - randomly rebuilding a file in the hope it matches ... . 
de rsync / zsync option is more realistic.

---

### Post by Thee on 2013-01-14
> **mips said:**
> NO, not unless you are into sorcery or witchcraft.

Let me quote something out of Simpsons :)

*"I predict that within 100 years computers will be twice as powerful, 10,000 times larger, and so expensive that only the five richest kings in Europe will own them."*

What I'm trying to say is, don't be so close-minded :) maybe it's not possible now, but everything we have today was once not possible or impossible.

---

### Post by mlentink on 2013-01-14
> **Thee said:**
> What I'm trying to say is, don't be so close-minded :) maybe it's not possible now, but everything we have today was once not possible or impossible.

You will never be able to keep on dividing a number until it's zero....

What you have to realize is that there's already quite a bit of theoretical work done (in some cases many years ago) on how to transfer information in the smallest and most efficient way. The only way your proposal would work (reconstruction of a dataset, by transfering a code that describes it) would be with lossless compression. And that has its inherent limits. Please also keep in mind that a computer file *is already a code* describing something else.

Google for Claude Shannon...

---

### Post by mips on 2013-01-15
> **Thee said:**
> 
What I'm trying to say is, don't be so close-minded :) maybe it's not possible now, but everything we have today was once not possible or impossible.

What I'm saying is right here right now the answer is NO. 
I'm not making any claims wrt stuff happening 20yrs down the line, that would also amount to witchcraft/sorcery on my part.

---

### Post by sffvba[e0rt on 2013-01-15
In 2035 the Singularity will happen and everyone will know everything at the same time.  Problem solved.


404

---

### Post by ssam on 2013-01-15
> **koenn said:**
> hm ... 
more accurately (I think) : given an algorithm that produces hashes of a fixed length,  for the probability of collisions to be near 0, there will be many cases where the hash is equal or larger in length than the source file and the net result will be 0 - you win some, you loose some. 

But, regardless, it's an extreme long shot - randomly rebuilding a file in the hope it matches ... . 
de rsync / zsync option is more realistic.

a hash is like using someones initials. I write down my 2 letter initials, and you use those initials to check if the next person you meet is me. the chance of a random person matching my initials is less than 1%, which might be a good enough check in some cases. but it is quite clear that if you write a program that randomly generates names, and checks those against my initials, it is unlikely to guess my name.

(initials are poor hashing algorithm because given a name i can easily modify it into a different name that has the same initials. with a good name->2 letters algorithm i would have to blindly modify the name and check in the hash was still the same, and it would take 26^2 guess to find one. but the maths on number of possible hashes and number of possible inputs is the same)

compression is like noticing that 'son' is a more common pattern in names that 'sn' to replacing each 'son' with 'sn' and each 'sn' with 'son'. now lots of names get shorter, but a few get longer.

---

### Post by bakelitedoorbell on 2013-01-15
I think it depends on what type of file is being transferred.  For example, if you are downloading an application, the source code would probably have a smaller file size compared to the compiled binary file.

So your downloading tool requests the application, the source code file is sent quickly, and then your computer's software center could possibly compile it for your computer.  That kinda meets your definition.

---

### Post by Cheesemill on 2013-01-15
From my experience the source code is always *much* larger than the compiled application.

For example source for the Linux kernel currently runs to around 470MB, whereas Ubuntu kernel packages are around 30MB.

---

