---
title: "never download again"
date: 2009-02-13
forum: The Cafe
---

### Post by phonicboom on 2009-02-13
idea when computers get faster and bandwidth is too expensive... 

You download a byte size and checksum, your computer then makes files of that size until it hits the checksum, then you have the file without ever downloading it...

---

### Post by marinegundoctor on 2009-02-13
That might take a while, similar to brute-forcing a password. The computer would have to try trillions of combinations until it got the file with a matching checksum.

---

### Post by kernelhaxor on 2009-02-13
There can be two different files with the same checksum value though its really rare ..
Also the method you described is not feasible computationally.

---

### Post by Mr. Picklesworth on 2009-02-13
That's a bit like brute forcing a password, except said password is 1 073 741 824 letters long for every gigabyte of downloading, and to make matters worse we wouldn't be able to rely on a specific alphabet for it to be written in since it isn't all human-written. ...So I guess we really want the number in bits (binary units), which would thus be 8 589 934 592 digits. Not going to happen ;)
Whatever gets saved in ISP bills gets lost in power bills and that ridiculously fast computer.

---

### Post by wmcbrine on 2009-02-13
[quote=kernelhaxor]There can be two different files with the same checksum value though its really rare[/quote]Not rare at all, in fact. A checksum is only for checking; it's not possible to guarantee its uniqueness, unless the checksum itself grows to the same size as the original file. A moment's reflection should show this -- just think of a file (any file) as being a number already, which it essentially is (or, can be interpreted as).

Forget the practical arguments; it's not possible even in theory.

---

### Post by lswb on 2009-02-13
The idea reminds me of something I read in an old sci-fi story. In the distant future, a person wishes to make a record of some written data. He transforms the data into a sequence of numbers, let's say 891345...6.

Then, he takes a piece of some advanced futuristic material and using his super ultra precise and accurate machine tools, cuts it to exactly 0.891345...6 centimeters (or other length unit).

Later, when he wishes to read the data, he simply measures the material with his super ultra precise and accurate measuring device, reads 0.891345...6, then transforms the sequence 891345...6 back into readable characters.

Simple, huh?

---

### Post by init1 on 2009-02-13
> **kernelhaxor said:**
> There can be two different files with the same checksum value though its really rare ..

According to Wikipedia, there are an infinite number of files with the same checksum, although it's extremely unlikely that anyone will ever encounter 2 files like that.

---

### Post by wmcbrine on 2009-02-13
Infinite if you don't constrain the length. If you specify the size, as the OP suggested, the number is merely astronomical. :)

Consider a 400-byte file, with a 32-bit checksum. 400 bytes is 3200 bits, so that's 2^3200 different possible 400-byte files. But you only have 2^32 unique checksums for those 2^3200 files.

You can add more bits to the checksum, but as long as it's fewer bits than in the original file, it doesn't change the nature of the problem. With only a 5-byte file and a 32-bit checksum, for example, you'd still have 256 different files mapped to each checksum. And while you can easily enough generate 256 5-byte files, there's simply no way to tell which of them was the original, just from the checksum and length. That information has been lost.

A checksum is useful because it (sometimes) allows you to tell if a file has been modified, whether accidentally or on purpose -- any given modification is relatively unlikely to produce a matching checksum (although this depends on the checksum algorithm). But as a truly unique identifier, it can't work.

---

### Post by Miguel on 2009-02-13
> **init1 said:**
> According to Wikipedia, there are an infinite number of files with the same checksum, although it's extremely unlikely that anyone will ever encounter 2 files like that.

Not really. MD5 sums are starting to feel little secure, and I think I read on Ars Technica about possible exploits of packages while keeping their md5sum. There's a reason why Debian (and thus Ubuntu) is moving to SHA for package integrity checking, if they haven't already. Mmm... let me check some links...

[ Ars Technica's MD5 exploit](http://arstechnica.com/security/news/2008/12/theoretical-attacks-yield-practical-attacks-on-ssl-pki.ars)
[Debian packages use SHA](http://en.wikipedia.org/wiki/SHA_hash_functions#cite_note-4). Actually, the apt code in that reference seems to read like "check SHA256, if not go to SHA1, if not check MD5, if not the package is corrupted".

---

### Post by Mr. Picklesworth on 2009-02-14
Naturally, the purpose isn't to make sure you've downloaded Ubuntu as opposed to a mountain goat. It's to check whether you've downloaded Ubuntu + something nasty or just Ubuntu :)

---

### Post by swoll1980 on 2009-02-14
> **wmcbrine said:**
> Not rare at all, in fact. A checksum is only for checking; it's not possible to guarantee its uniqueness, unless the checksum itself grows to the same size as the original file. A moment's reflection should show this -- just think of a file (any file) as being a number already, which it essentially is (or, can be interpreted as).

Forget the practical arguments; it's not possible even in theory.

That's what I was thinking the file is already a # though there are ways to reduce the amount of #s in a file obviously. The only way to make this work would be with some kind of super compression. Isn't that what a compressed file is? A file with less #s?

---

### Post by init1 on 2009-02-14
So basically this would be extremely high compression. Might be possible, but not necessarily the way you described.

---

### Post by swoll1980 on 2009-02-14
> **init1 said:**
> So basically this would be extremely high compression. Might be possible, but not necessarily the way you described.

Quantum computing could go a long way towards reducing file sizes, if I'm understanding the way it works corectly. If it reads three states instead of two wouldn't that make files a lot smaller?

---

### Post by MaxIBoy on 2009-02-14
Not possible. Your standard MD5 checksum is at most a kilobyte. A kilobyte checksum literally isn't capable of holding enough information to represent a decent-sized download.


"BUT MAX!" you say. "What if you made the checksum bigger and bigger until it *could* represent the file, possibly augmenting it with other integrity checks and redundancy checks to make everything nice and small?"

That already exists. It's called "file compression." Typical protocols for "file compression" are "zip," "gzip," "7zip," "bzip," "rar," "z," "shar," "lzma," and a few others.

---

### Post by swoll1980 on 2009-02-14
Is there an echo in here? HELLO...HELLo...HELlo...HEllo hmmmm. I guess there is.

---

### Post by |{urse on 2009-02-14
how on earth does a mere checksum contain the binary needed for a program, picture or whatever without containing the actual binary itself? Cmon ppls that is ridiculous.

---

### Post by howlingmadhowie on 2009-02-14
> **swoll1980 said:**
> That's what I was thinking the file is already a # though there are ways to reduce the amount of #s in a file obviously. The only way to make this work would be with some kind of super compression. Isn't that what a compressed file is? A file with less #s?

compression relies on redundancy in a file. a simple example would be the tree used in zip compression. here you give a number to each byte in the original file and the result is as follows:

input: aaaabbaabbbbaaaaacccaaccbaabaaccabb
lots of a's a some b's and a few c's, total 35 bytes

a=0 <- we choose a short number for a because a is the most common.
b=10 <- b is less common, so the number we choose is longer.
c=11

output 0000101000101010100000011111100111110001000111101010
a stream of 0's and 1's, 52 bits = 7 bytes long.

of course, you also have to save the tree, so you can decipher the stream, and the way we chose the numbers to use for a, b and c is actually the clever bit and worth reading up on on wikipedia.

the important thing to notice is that the input has a lot of redundancy. even some sore of bitmap compression (a4b2a2b4a5c3a2c2ba2ba2c2ab2) would save space here. the best method of compression depends a lot on the structure of the redundancy in the input. if the input has no redundancy (which is actually quite difficult to prove, but an intuitive understanding should be simple enough), then there exists no procedure to reduce its size.

---

### Post by wmcbrine on 2009-02-14
Data compression works by removing redundancy. But there's a hard limit -- once you've squeezed out all the redundancy, that's as small as your data is going to get. Current compression algorithms can get to somewhere around half size, on typical data; more in specific circumstances. It's unlikely that they'll get substantially better in the future, because in typical data, there's just not that much more redundancy to find. Already, the best compression takes orders of magnitude longer than the next-best, for only a few percent further reduction in size.

Ah, howlingmadhowie posted while I was typing. What he said. :)

---

### Post by howlingmadhowie on 2009-02-14
> **swoll1980 said:**
> Quantum computing could go a long way towards reducing file sizes, if I'm understanding the way it works corectly. If it reads three states instead of two wouldn't that make files a lot smaller?

the way i understood it, quantum computing would allow [nondeterministic finite state machines]("http://en.wikipedia.org/wiki/Nondeterministic_finite_state_machine"), but i've never really been interested in it, so i may be wrong.

question, if we introduce the trit as having 3 different states, which we will label 0, 1 and 2, how many trits will be necessary to save an ascii character? how much shorter will files be? :)

if you can't work it out, just ask :)

---

### Post by swoll1980 on 2009-02-14
> **howlingmadhowie said:**
> the way i understood it, quantum computing would allow [nondeterministic finite state machines]("http://en.wikipedia.org/wiki/Nondeterministic_finite_state_machine"), but i've never really been interested in it, so i may be wrong.

question, if we introduce the trit as having 3 different states, which we will label 0, 1 and 2, how many trits will be necessary to save an ascii character? how much shorter will files be? :)

if you can't work it out, just ask :)

I'm no good with math. My brain wants to tell me at least 33% smaller, but common sense tells me that adding a 3rd state would create a huge amount of possibilities, way more than what it would take to reduce a file by 33%

---

### Post by 3rdalbum on 2009-02-14
I can't remember where I found this, but it's hilarious, and with this talk about files being represented by numbers, I thought it very apt.

**Converting pi to binary: Don't do it!**
*by Keith F. Lynch*

Warning: Do not calculate Pi in binary. It is conjectured that this number is normal, meaning that
*it contains all finite bit strings*.

If you compute it, you will be guilty of:

* Copyright infringement (of all books, all short stories, all newspapers, all magazines, all web sites, all music, all movies, and all software, including the complete Windows source code)

* Trademark infringement

* Possession of child pornography

* Espionage (unauthorized possession of top secret information)

* Possession of DVD-cracking software

* Possession of threats to the President

* Possession of everyone's SSN, everyone's credit card numbers, everyone's PIN numbers, everyone's unlisted phone numbers, and everyone's passwords

* Defaming Islam. Not technically illegal, but you'll have to go into hiding along with Salman Rushdie.

* Defaming Scientology. Which is illegal -- just ask Keith Henson.

Also, your computer will contain all of the nastiest known computer viruses. In fact, all of the nastiest possible computer viruses.

Some of the files on my PC are intensely personal, and I for one don't want you snooping through a copy of them.

You might get away with computing just a few digits, but why risk it? There's no telling how far into Pi you can go without finding the secret documents about the JFK assassination, a photograph of your neighbor's six year old daughter doing the nasty with the family dog, or a complete copy of the not-yet-released Pearl Harbor movie. So just don't do it.

The same warning applies to e, the square root of 2, Euler's constant, Phi, the cosine of any non-zero algebraic number, and the vast majority of all other real numbers.

There's a reason why these numbers are always computed and shown in decimal, after all.

---

### Post by spupy on 2009-02-14
Quick, someone post the checksum of the Ubuntu 25.10 DVD!

---

### Post by Canuckelhead on 2009-02-14
I'm reminded of something form a Jasper Fforde Novel where entire novels are compressed down to a short numerical hash that can be decoded to recreate the entire novel.  Unfortunately MD5 collisions though uncommon are much more likely than say, the complete works of William Shakespeare.  For now, I think I'll go on collecting keyboards and monkeys to get free downloads.  :)

---

### Post by binarypill on 2009-02-14
for some reason, this thread has me thinking about the book neuromancer and how wintermute tells case that his brain is still stuck on the "printed word" information paradigm or something like that...

what i'm thinking is that, once we shift our thinking to something more "3d" than the written word (a, 0, 1, 3.1415), "traditional" computer concerns such as file size, bandwidth and download speed are going to be irrelevant. the answer, therefore is to change the way we "think" about information, shifting it from words, bytes or whatever to something else...3d heiroglyphs perhaps..

a good illustration of such a shift, i think, would be the shift from the magnetic drive to the optical drive. i think there may have been more that could have been done to make the magnetic drive have a higher capacity, better reliablility and smaller size. however, development simply stopped or slowed down once a better medium (optical data storage) emerged...

...or maybe it's just the bbq i ate for lunch...:lolflag:

---

### Post by ithanium on 2009-02-14
good idea, but just not practical :)

---

### Post by Archmage on 2009-02-14
So instead of downloading a file that is 1 MB long, I take 5,000 years, till I have 20 millions file that are each 1 MB long and than I will spend the next 400,000 years to test what file is the real one?

Sounds great if you will live for eternity and don't know how to spend this, but most of us will simply download the file in one minute and save 404,999.999 years.

---

### Post by Canuckelhead on 2009-02-14
Right on Archmage...

My infinite monkeys can type that out in half that time!

---

### Post by JohnSearle on 2009-02-14
> **Canuckelhead said:**
> Right on Archmage...

My infinite monkeys can type that out in half that time!

That's pretty good. All mine have ever done was define all that is Canada.

---

### Post by HavocXphere on 2009-02-14
It kinda works...but the checksum would have to be so long that its pretty close to the original file size just to make collisions unlikely enough.

@howlingmadhowie: Quantum computing is inherently binary: Vertical and Horizontal allignment. No 3rd state possible.

[QUOTE=howlingmadhowie]how many trits will be necessary to save an ascii character? how much shorter will files be?[/QUOTE]
About 5.05 units with 3 possible settings. (~63%...although the % is going to drift with multiple bytes)

---

### Post by howlingmadhowie on 2009-02-15
> **HavocXphere said:**
> It kinda works...but the checksum would have to be so long that its pretty close to the original file size just to make collisions unlikely enough.

@howlingmadhowie: Quantum computing is inherently binary: Vertical and Horizontal allignment. No 3rd state possible.


About 5.05 units with 3 possible settings. (~63%...although the % is going to drift with multiple bytes)

a quick explanation of how the calculation works. 

there are 128 different ascii characters (32 of which non-printing) which are traditionally represented as 7 bits with 1 bit checksum. later this became 7bits and one zero bit. there are various extensions (the iso-8859 extensions for example) which take advantage of this to define 256 different characters. so you either need to store 128 different states or 128 different states plus a checksum or 256 different states. this can be done in 7 bits or in 7 + 1 bits or in 8 bits.

one trit can store 3 different states, 2 can store 9, 3 can store 27, 4 can store 81, 5 can store 243, and 6 can store 729. to store 128 different states, you need 5 trits, to store 128 different states plus a checksum you need 6 trits, to store 256 different states, you need 6 trits.  so there would be a pressure to create new character mappings for exactly 243 different characters.

with binary data this is different. consider a binary file---a long row of 0's or 1's, n long. this can be regarded as representing one out of 2^n possible files. the total number of possible files we will call x.

so 2^n = x.

but m trits can store 3^n possible combinations. 

3^m=x.

so 2^n = 3^m, or

n log(2) = m log(3)
m/n = log(2)/log(3)
  ~ 0.631

so a trinary file in the limit would be just over 63% as long as a binary file.

reading up on quantum computing by wikipedia, it seems to be about storing a number of possible states. 

one of the basic tenets of quantum states is that they take all possible states before they are observed, at which point there is a certain probability of them 'deciding to be in' one of each of the permitted classical states. for example, an electron traveling classically from a to b takes all possible roots. only when we observe it is it 'forced to decide' which root it 'actually' takes.

---

### Post by phonicboom on 2009-02-15
As I posted this idea on a few forums I have had various responses. 

With adaptation there is a possible solution. We do not just send byte length and checksum, we also send clues. 

We send the file type to be produced, the byte length, the checksum, the first and last few characters(?), a 1 or 0 to show if 1 or 0 is more common in the file, and well anything that would help the generating algorithm on the local computer to attempt more suitable guesses. 

Like if I had a 6 sided dice in my hand I do not ask you (the algorithm) to bother with colours, numbers above 6, letters of the alphabet, animals, vegetables or politicians. I give you a much better chance of getting the answer. 

So in the case of a file I say. It is a .png, 4370120bytes, checksum blablabla, starting with a 1 and mainly 1's. 

..obviously I don't really know what I'm talking about ;) but I feel the idea has legs if people add such ideas to the basic premise.



..

---

### Post by namegame on 2009-02-15
> **phonicboom said:**
>  but I feel the idea has legs if people add such ideas to the basic premise.



..

It's really not feasible though. Imagine you had a puzzle with 6 million pieces, but you are blindfolded, you can't see them at all. 

It would be possible to fit the pieces together, however, it would take a long time, and then when you are done, you find out that you pieced it together upside down.

Like someone else in the thread said, I'd rather wait on 2 hour downloads rather than my computer's processor to solve a puzzle with millions of pieces...

---

### Post by howlingmadhowie on 2009-02-15
> **phonicboom said:**
> As I posted this idea on a few forums I have had various responses. 

With adaptation there is a possible solution. We do not just send byte length and checksum, we also send clues. 

We send the file type to be produced, the byte length, the checksum, the first and last few characters(?), a 1 or 0 to show if 1 or 0 is more common in the file, and well anything that would help the generating algorithm on the local computer to attempt more suitable guesses. 

Like if I had a 6 sided dice in my hand I do not ask you (the algorithm) to bother with colours, numbers above 6, letters of the alphabet, animals, vegetables or politicians. I give you a much better chance of getting the answer. 

So in the case of a file I say. It is a .png, 4370120bytes, checksum blablabla, starting with a 1 and mainly 1's. 

..obviously I don't really know what I'm talking about ;) but I feel the idea has legs if people add such ideas to the basic premise.



..

unfortunately by providing clues you are doing the same as lengthening the hashing function you are using. in order to unambiguously define a file of length 10kB with no redundancy, you need 10kB of information. 

the one loophole in the above sentence is the phrase 'with no redundancy'. let's say i am recording a film. one actor is on the screen for much of the film. in some shots, his face may look almost exactly the same, so you could copy these shots. there may be a trivial translation between these shots, so you could just send the information 'like in frame 32843 but 10% darker' or something like that. it might even be worth sending a 3d model of his face, and then telling the software used to play the file to paste this face into the film. if we have 200 different actors, we could record all their different eyes in the software and then define the eyes of the 201st actor as being 'like those of 34 but with a bit or 98 around the edges' or whatever. or if the eyes are really new, we could add them to our database.

and now we're getting pretty close to how light falling onto our retinas gets transformed into a 3d model of the world in our consciousness. for the quality of the 3d model in our head, the amount of information passing along the optic nerve is ridiculously small, just a fraction of a fraction of a percent of the amount needed with the best current compression. of course, we rely on an immensely powerful computer and a vast database to do this.

---

### Post by phonicboom on 2009-02-15
In the OP I do mention that this is for the days of much faster computing and to overcome the potential of being priced out of bandwidth which is already the case in Australia.

---

### Post by 3rdalbum on 2009-02-15
> **binarypill said:**
> 

a good illustration of such a shift, i think, would be the shift from the magnetic drive to the optical drive. i think there may have been more that could have been done to make the magnetic drive have a higher capacity, better reliablility and smaller size. however, development simply stopped or slowed down once a better medium (optical data storage) emerged...

Magnetic drives are still in use. Unless you're typing this on a Linux netbook, I guarantee you are using a magnetic drive (hard disk) right now. And, actually, in a way they do store data in 3D. DVDs and Blu-ray discs store data in 3D as well.

---

### Post by Paqman on 2009-02-15
The only time this would be practical would be if you had astronomical amounts of processing power, but teeny, tiny bandwidth.

The amount of processor smash you'd need makes me think that we're talking decades or generations into the future here. Given the transmission delays involved in long-range space communications this could theoretically be a practical solution for sending data at an interstellar range. Since you're effectively communicating only half-duplex anyway the fact that it might take your computer a while to reconstruct the data could be a non-issue. It could be a really efficient form of data compression.

Actually, it's cunning data compression like this that makes SETI so hard. High-tech alien civilisations are likely to be compressing their comms chatter to a high degree, which makes it really hard to distinguish a signal from the background noise. At the moment we probably wouldn't detect a signal that wasn't analogue or deliberately designed to look artificial.

---

### Post by phonicboom on 2009-02-16
You can get a similar checksum from two different files but not for 2 versions of the same file. 

I still think that if I say to supercomputer "make me a file with checksum xyz123 of 123456890bytes then it will more than likely, when finished, have made the same file as I originally took the checksum and byte length from. 

On the slight chance it had not then there would be simple checks and the algorithm could be told "ok try again and don't make that".

..

---

### Post by BuffaloX on 2009-02-16
> **spupy said:**
> Quick, someone post the checksum of the Ubuntu 25.10 DVD!

Haha Microsoft now you die, we've got the secret checksum weapon, and all your software will be obsolete soon, :p

---

### Post by BuffaloX on 2009-02-16
Honestly guys. 

there have already been at least four posts showing this is impossible.
It doesn't matter if you have infinite processing power and could compute this in the fraction of a second, you would still have to deal with the enormous number of possible files that fit the checksum.

Since some here don't understand the math based arguments, imagine the checksum is "Giraffe", how many possible images of a giraffe are there?

A checksum has absolutely nothing to do with compression.

As already shown earlier:
If you have a file of 400 bytes with a 32 bit checksum:
File: 400 bytes = 3200 bits = 2^3200 = 1,976906479e+963
Checksum: 2^32 = 4294967296
Number of 400 byte files matching checksum: 4,602844079e+953

Please please stop saying this is a good idea, or if you include the file length it could work.

---

### Post by wmcbrine on 2009-02-16
> **Paqman said:**
> The only time this would be practical would be if you had astronomical amounts of processing power, but teeny, tiny bandwidth.There is *no* time when this would be practical, because it's mathematically impossible. You *cannot* uniquely specify a file with less information than is in the original.

The best you might hope for are domain-specific and/or lossy schemes, like the one outlined by howlingmadhowie for a film. The results can be spectacular. But for general data compression, you can't just arbitrarily trade off computing time for size. Yes, it would be nice. But no, it won't work. This isn't magic; it's math.

---

### Post by howlingmadhowie on 2009-02-17
> **phonicboom said:**
> You can get a similar checksum from two different files but not for 2 versions of the same file. 

I still think that if I say to supercomputer "make me a file with checksum xyz123 of 123456890bytes then it will more than likely, when finished, have made the same file as I originally took the checksum and byte length from. 

On the slight chance it had not then there would be simple checks and the algorithm could be told "ok try again and don't make that".

..

the total number of files with a 10 bit checksum and length of 100bits is 2^(100-10) = 1237940039285380274899124224 (provided the checksum function generates evenly spaced hashes). in your example, you have a checksum of 64^6 (assuming base64 encoding of the checksum) = 36bits and a file of 1234567890*8 bits, which means there are 2^(1234567890*8 ) different files of which 2^(1234567890*8 - 36) will have the same checksum.

so that you have a feeling for the amount of different files this is, 2^10000 (which multiplied by itself a million times would be smaller than the number of different files 1234567890bytes long with the same 6 character checksum) is

1995063116880758384883742162683585083823496831886192454852008949852
9438830221946631919961684036194597899331129423209124271556491349413
7811175937859320963239578557300467937945267652465512660598955205500
8691819331154250860846061810468550907486608962488809048989483800925
3941633257850621568309473902556912388065225096643874441046759871626
9854532228685381616943157756296407628368807607322285350916414761839
5638145896946389941084096053626782106462142733339403652556564953060
3142680234969400335934316651459297773279665775606172582031407994198
1796073782456837622800373028854872519008344645814546505579296014148
3392161573458813925709537976911927780082695773567444412306201875783
6325502728323789270710373802866393031428133241401624195671690574061
4196543423246388012488561473052074319922596117962501309928602417083
4080760593232016126849228849625584131284406153673895148711425631511
1089745514203313820202931640957596464756010405845841566072044962867
0165150619206310041864222759086709005746064178569519114560550682512
5040600751984226189805923711805444478807290639524254833922198270740
4473162376760846613033778706039803413197133493654622700563169937455
5082417809728109832913144035718775247685098572769379264332215993998
7688666080836883783802764328277517227365757274478411229438973381086
1607423253291974813120197604178281965697475898164531258434135959862
7841301281854062834766490886905210475808826158239619857701224070443
3058307586903931960460340497315658320867210591330090375282341553974
5394397715257455290510212310947321610753474825740775273986348298498
3407569379556466386218745694992790165721037013644331358172143117913
9822298384584733444027096418285100507292774836455057863450110085298
7812389473928699540834346158807043959118985815145779177143619698728
1314594837832020814749821718580113890712282509058268174362205774759
2141765371568772561490458290499246102863008153558330813010198767585
6234343538955409175623400844887526162643568648833519463720377293240
0944562469232543504006780272738377553764067268986362410374914109667
1855705075909810024678988017827192595338128242195402830275940844895
5014676668389697996886241636313376393903373455801407636741877711055
3842257394991101864682196965816514851304942223699477147630691554682
1768287620036277725772378136533161119681128079266948188720129864366
0768551639860534602297871557517947385246369446923087894265948217008
0511203223654962881690357391213683383935917564187338505109702716139
1543959099159815465441733631165693603112224993796999922678173235802
3111862644575299135758175008199839236284615249881088960232244362173
7716180863570154684840586223297928538756234865564405369626220189635
7102881236156751254333830327002909766865056855715750551672751889919
4129711337690149916181315171544007728650573189557450920330185304847
1138183154073240533190384620840364217637039115506397890007428536721
9628090347797453332046836879586858023795221862912008074281955131794
8157624448298518461509704888027274721574688131594750409732115080498
190455803416826949787141316063210686391511681774304792596709376

now that's already quite a few to sift through to find the right one.

---

### Post by whoop on 2009-02-17
Amusing thread. I wonder why nobody is mentioning parity files ;-)

---

### Post by cmay on 2009-02-17
at the crunch bang linux forums the is an exact same first post. i wonder why it should be posted in more than one forum.

---

### Post by macogw on 2009-02-17
> **Miguel said:**
> Not really. MD5 sums are starting to feel little secure, and I think I read on Ars Technica about possible exploits of packages while keeping their md5sum. There's a reason why Debian (and thus Ubuntu) is moving to SHA for package integrity checking, if they haven't already. Mmm... let me check some links...

[ Ars Technica's MD5 exploit](http://arstechnica.com/security/news/2008/12/theoretical-attacks-yield-practical-attacks-on-ssl-pki.ars)
[Debian packages use SHA](http://en.wikipedia.org/wiki/SHA_hash_functions#cite_note-4). Actually, the apt code in that reference seems to read like "check SHA256, if not go to SHA1, if not check MD5, if not the package is corrupted".
Rainbow tables.  Huge ones exist for MD5 and SHA1, so everyone's running away from MD5 and SHA1 screaming.

Ubuntu uses SHA512.

---

### Post by Miguel on 2009-02-17
> **macogw said:**
> Rainbow tables.  Huge ones exist for MD5 and SHA1, so everyone's running away from MD5 and SHA1 screaming.

Ubuntu uses SHA512.

Thanks for pointing that out!

---

### Post by macogw on 2009-02-17
Hmm...more accurate:

Hardy and earlier use MD5.

Intrepid supports SHA512 and is *supposed* to use it out of the box.  If you use Windows-migration on Intrepid though, it does it **completely wrong** though, and you end up in "only the first 8 characters of the password count" mode, like in old UNIX systems.  Also, SHA512 may not actually happen by default (it might do MD5).  If you change your password using the "passwd" command, then it'll convert you to SHA512.  Use ```
sudo less /etc/shadow
``` to see what it's doing.  If it has $1$ it's doing MD5.  If it's $6$, then it's SHA512.

---

### Post by Miguel on 2009-02-17
> **macogw said:**
> Hmm...more accurate:

Hardy and earlier use MD5.

Intrepid supports SHA512 and is *supposed* to use it out of the box.  If you use Windows-migration on Intrepid though, it does it **completely wrong** though, and you end up in "only the first 8 characters of the password count" mode, like in old UNIX systems.  Also, SHA512 may not actually happen by default (it might do MD5).  If you change your password using the "passwd" command, then it'll convert you to SHA512.  Use ```
sudo less /etc/shadow
``` to see what it's doing.  If it has $1$ it's doing MD5.  If it's $6$, then it's SHA512.

It's good to know. I don't feel all that bad about shadow (yes, I confess), since you need root privileges to be able to read it in the first place. In any case, does that apply for package integrity? I thought Debian moved away from MD5 for package integrity a looong time ago. Like... emm... Sarge or Etch.

---

### Post by Paqman on 2009-02-17
> **wmcbrine said:**
> There is *no* time when this would be practical, because it's mathematically impossible. You *cannot* uniquely specify a file with less information than is in the original.

The best you might hope for are domain-specific and/or lossy schemes, like the one outlined by howlingmadhowie for a film. The results can be spectacular. But for general data compression, you can't just arbitrarily trade off computing time for size. Yes, it would be nice. But no, it won't work. This isn't magic; it's math.

What about if you also included, say, 10% of the file? That should sort the math down to the realm of the computationally sensible, surely? Especially if you had a machine that could understand the semantic contents of the file fragment and could make some guesses about what were sensible candidates for the complete file.

---

### Post by phonicboom on 2009-02-17
> **Paqman said:**
> What about if you also included, say, 10% of the file? That should sort the math down to the realm of the computationally sensible, surely? Especially if you had a machine that could understand the semantic contents of the file fragment and could make some guesses about what were sensible candidates for the complete file.

finally someone with creative input! thanks :)

---

### Post by Miguel on 2009-02-17
I'll totally and utterly change my point of view here and state that thermodynamics is playing against you. 

Trying to generate true 100 Mb from (even) 10 Mb of a checksum is probably as possible as dropping a boat into the sea, and the sea will get cooler so that the boat can use that difference of energy to power its engine.

---

### Post by phonicboom on 2009-02-17
thermodynamics is a myth, check out the "Electric Universe"

---

### Post by Miguel on 2009-02-17
> **phonicboom said:**
> thermodynamics is a myth, check out the "Electric Universe"

All I've seen in google about "Electric Universe" is a music group, so I suppose you are basically pulling my leg about thermodynamics.

---

### Post by wmcbrine on 2009-02-17
> **phonicboom said:**
> thermodynamics is a myth, check out the "Electric Universe"Oh God, not that too.

---

### Post by BuffaloX on 2009-02-17
> **Miguel said:**
> I'll totally and utterly change my point of view here and state that thermodynamics is playing against you. 

Trying to generate true 100 Mb from (even) 10 Mb of a checksum is probably as possible as dropping a boat into the sea, and the sea will get cooler so that the boat can use that difference of energy to power its engine.

I just love how you clever guys talk. :p

So it is possible then? ;)

---

### Post by Arand on 2009-02-17
I propose that we skip the wholly redundant downloading step altogether.

Operation will simply be typing in a request:

```
Write a good science-fiction book for me, please.
```

And the computer will start generating a book which will be deemed complete when conditions are met:

```
correct_spelling=true
correct_grammar=true
is_the_next_I_robot=true
```

Or hang on, even better!
Why not let the computer just generate everything, user input will be superfluous since it may be generated as well.
ZOMG I'm gonna be rich!!! plz no steal idea!1

---

### Post by swoll1980 on 2009-02-17
> **BuffaloX said:**
> I just love how you clever guys talk. :p

So it is possible then? ;)

Look at it this way. I do a math problem (x)=10 I can't give a someone a number 10, and say "ok now you have to make 10 the same way that I did" They will get the same number in the end, but the chances that they get all the stuff in the middle right would be like monkeys typing the constitution by coincidence. There's information missing. With out this information it is imposible to get 10 the same way I did with the exeption of dumb luck. I'm not sure, but it would seem to me that the clues needed for the comp to guess the file would be longer than the file it's self. Think of it  like this, you could ethier download the answer 10 or the 3 pages of clues it would take for you to figure out how a made the ten.

---

### Post by BuffaloX on 2009-02-17
If checksum method saves 50% and we do it recursively.
Any size file can be reduced until they are only one bit in size...

Now all files can be downloadet by just getting 2 bits.
Filelength and Checksum

So here you are:
Ubuntu 25.10 = 0 1

Windows 2025 = 0 1

Yeah I know they seem the same, but our infinite processing power solves that it just take a couple of seconds -- no problemo.

Can we now please stop?

---

### Post by Miguel on 2009-02-17
> **BuffaloX said:**
> I just love how you clever guys talk. :p

So it is possible then? ;)

I'll run the risk of being called an unimaginative retrograde and say that no, it isn't possible.  The original poster, Phonicboom, proposed:

[quote=phonicboom]
You download a byte size and checksum, your computer then makes files of that size until it hits the checksum, then you have the file without ever downloading it.[/quote]

The error in his reasoning is that, once the file size exceeds the checksum size, there are many files of the exact same size with the exact same checksum. Adding additional information (i.e. the first 10% as someone suggested) will help, but it won't be enough until the total information you have is the **same** as the original file. 

You would end up downloading the same amount of information (bytes) and wasting CPU time that could have been spent in something more productive like watching youtube or playing openarena.

Please note that if the original file size is a mere byte longer than the total information you downloaded, you can produce 256 (2^8 ) different files that match all your requirements.

*Example*

We have an up to three bit system, with all the states being the following (associated to numbers for future convenience):
```

  0 = 0
  1 = 1
 10 = 2
 11 = 3
100 = 4
101 = 5
110 = 6
111 = 7

```
Yes, I know it's not very imaginative. Now, we have a one-bit checksum, that is the modulo of the "state" divided by two. In our system this matches the last number in binary form.

If you say *"my file just has one bit, and its checksum is 0"*, then you are providing more information than the real archive (0), but at least you get it. If you say *"my system has two bits, and the last number (or checksum) is 1"*, you provide the same information that you want to recover, and get the correct answer as a prize. But when you get to three bits... Aha! Which file has three bits and "checksum" 0? Both 4 and 6. See why the OP's point fails?

---

### Post by wmcbrine on 2009-02-17
> **Miguel said:**
> Please note that if the original file size is a mere byte longer than the total information you downloaded, you can produce 8 different files that match all your requirements.Not 8 -- 256.

---

### Post by Miguel on 2009-02-17
> **wmcbrine said:**
> Not 8 -- 256.

Silly me! Already corrected and thanks for the tip.

---

### Post by phonicboom on 2009-02-18
Imagine you gave it the first and last megabyte of a 2.5 megabyte file and the checksum for a completed file. Would the computer be able to work out the missing .5? If so then you could ask it to try more next time.

---

### Post by sharon.gmc on 2009-02-18
I don't think to either.

---

### Post by wmcbrine on 2009-02-18
> **phonicboom said:**
> Imagine you gave it the first and last megabyte of a 2.5 megabyte file and the checksum for a completed file. Would the computer be able to work out the missing .5?No. It could only give you BIGNUM versions to choose from. (I am too lazy to work out what BIGNUM is, but trust me, it's big .)

---

### Post by 3rdalbum on 2009-02-18
I know it's mathematically impossible, but I conducted an experiment years ago, where I put little spikes of random data at regular intervals into video files. The video players would still play the files, even with spikes of 20 kilobytes. Obviously video playback software is tolerant to wrong data.

Therefore, if your checksum corresponded to a bunch of video files that were all fairly similar but had some wrong data at frequent intervals, you could still play it fairly well and therefore it wouldn't matter if not all the data was correct.

---

### Post by wmcbrine on 2009-02-18
> **3rdalbum said:**
> Obviously video playback software is tolerant to wrong data.Really not the issue here, nor does it help. The alternate files generated from the checksum would not necessarily (or even likely) be close to the original at all -- think "wrong from top to bottom", not "nearly the same", or "close enough".

---

### Post by Miguel on 2009-02-18
Actually, if the checksum mechanism was any good, the collisions have to be very far away, and the "almost identical video" wouldn't have the same checksum. This is because one of the main requirements of a checksum is that almost identical files have terribly different checksums.

---

### Post by howlingmadhowie on 2009-02-18
> **Paqman said:**
> What about if you also included, say, 10% of the file? That should sort the math down to the realm of the computationally sensible, surely? Especially if you had a machine that could understand the semantic contents of the file fragment and could make some guesses about what were sensible candidates for the complete file.

you're talking about redundancy. i mentioned that above. a good compression algorithm should remove redundancy. there are of course two classes of compression: lossy and lossless. for a film or an image, you can get by with a certain loss. in fact you need it because a film in 800px * 600px image size and 25fps image rate without compression would be (* 1.5 60 60 25 800 600 3) = ca. 200GB in size (assuming no lossless reduction). For a binary software file you can use lossless compression but you should think very carefully about lossy compression.

---

### Post by MaxIBoy on 2009-02-18
Yeah-- the idea is that file corruption happens a few bytes at a time. If your file is corrupted, it'll only be a few bytes off. This will cause the checksum to be WAY different, and the corruption will stick out like a sore thumb.





To do what the original poster suggests, you'd basically have to brute-force guess the file's contents.

We'll start with a small example:
> The amount of time required to break a 128-bit key is also daunting. Each of the 2^128 (340,282,366,920,938,463,463,374,607,431,768,211,456) possibilities must be checked. A device that could check a billion billion keys (10^18) per second would still require about 10^13 years to exhaust the key space. This is a thousand times longer than the [age of the universe]("http://en.wikipedia.org/wiki/Age_of_the_universe"), which is about 13,000,000,000 ([IMG]http://upload.wikimedia.org/math/1/b/4/1b479109f1d92a3207c1042f882b7da9.png[/IMG]) years.Source: [http://en.wikipedia.org/wiki/Brute_force_attack](http://en.wikipedia.org/wiki/Brute_force_attack)

So assuming it only takes **one** instruction to check a combination, the [world's most powerful computer]("http://www.top500.org/system/9707") would take 781250000000000000000 (10^13*(10^18/(12.8*10^9))) **years** to run through all the combinations. Keep in mind that is would actually take five or six instructions per second to check a combination (if you wrote an OS specifically for that purpose that did no other tasks at all,) so the real-world time is **five or six times as long**.

And that's just for a 128-bit key!




Scale it up to the level of recovering entire gigabytes of data, and the laws of physics tell you that you're using many times more than the current electricity usage of the entire planet, **not including any power-using components besides the processor itself**.

---

### Post by ice60 on 2009-02-18
if the output from the hash function is smaller than the input file there will always be hash function collisions. is that right?

---

### Post by MaxIBoy on 2009-02-18
Yes, that is right. There always will be.


If your file is 700 bits and your hash is 699 bits, there will be two possible files.

---

### Post by wmcbrine on 2009-02-18
> **MaxIBoy said:**
> To do what the original poster suggests, you'd basically have to brute-force guess the file's contents.But the deeper problem is that there is no way, with any amount of computing power, to distinguish between the various "correct" answers, even in theory.

---

