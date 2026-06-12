---
title: "Security Question regarding signing files"
date: 2008-02-06
forum: Security Discussions
---

### Post by jonnan on 2008-02-06
My apologies - I'm a relative newbie to Ubuntu, but had an idea go through my mind that seems so relatively obvious that there must be an equally obvious reason it has never been implemented. Quick searches haven't brought anything up on this, so additional apologies if I missed something on this.

Why are important files not signed in the actual filesystem? 

Unlike Windows, linux maintains a 'history' of changes to it's files by simply including the version number in the file, which makes perfect sense when managing dependencies - you don't have to worry about conflicts, you can just maintain the versions you need and leapfrog up as different programs update.

Which brings to mind the question - why not take it a step further, and build signing and verifying the binary file signature directly into the filesystem. Have the filename for something like nautilus be, behind the scenes, nautilus.{asklj90845khgf9834tljkn3423;o8ugfe8907asgkjhgtawer ...},have any program that uses nautilus compiled with that full name, and have the filesystem run a signature program on that file whenever it is accessed by the full name verifying that no changes have been made to the file. 

It seems like having this done behind the scenes in the filesystem would make it very hard for any files to be altered without sending up all sorts of alarms.

Is this
A) yes obvious, in fact so obvious that it is done and I'm just too stupid to be aware of it (I did this years ago when I asked why you didn't prevent dictionary attacks by appending random information to the password before encrypting it. Obviously 'salting' was well understood by anyone that wasn't a layman - <G>. Ah - to be young and dumb and on the Usenet again!)

B) Obvious - well, if you're a frickin' MORON. THIS and THIS and THIS make it a really bad idea.

C) Just not as obvious as it looks to me?

My apologies if the answer is  either A or B, but I'd like to at least know even then.

Thanks - Jonnan

---

### Post by euler_fan on 2008-02-06
> **jonnan said:**
> My apologies - I'm a relative newbie to Ubuntu, but had an idea go through my mind that seems so relatively obvious that there must be an equally obvious reason it has never been implemented. Quick searches haven't brought anything up on this, so additional apologies if I missed something on this.

Why are important files not signed in the actual filesystem? 

Unlike Windows, linux maintains a 'history' of changes to it's files by simply including the version number in the file, which makes perfect sense when managing dependencies - you don't have to worry about conflicts, you can just maintain the versions you need and leapfrog up as different programs update.

Which brings to mind the question - why not take it a step further, and build signing and verifying the binary file signature directly into the filesystem. Have the filename for something like nautilus be, behind the scenes, nautilus.{asklj90845khgf9834tljkn3423;o8ugfe8907asgkjhgtawer ...},have any program that uses nautilus compiled with that full name, and have the filesystem run a signature program on that file whenever it is accessed by the full name verifying that no changes have been made to the file. 

It seems like having this done behind the scenes in the filesystem would make it very hard for any files to be altered without sending up all sorts of alarms.

Is this
A) yes obvious, in fact so obvious that it is done and I'm just too stupid to be aware of it (I did this years ago when I asked why you didn't prevent dictionary attacks by appending random information to the password before encrypting it. Obviously 'salting' was well understood by anyone that wasn't a layman - <G>. Ah - to be young and dumb and on the Usenet again!)

B) Obvious - well, if you're a frickin' MORON. THIS and THIS and THIS make it a really bad idea.

C) Just not as obvious as it looks to me?

My apologies if the answer is  either A or B, but I'd like to at least know even then.

Thanks - Jonnan

The problem with cryptographic signing is very simple and twofold:
1) Whose certificate do you use to sign and how do you know to trust them?
2) Eats processor time like crazy. It is it take forever to hash large files, much less large numbers of files large and small. Throw on cryptographic computations and this is a huge drain on system resources.

If you're looking for a piece of software that will alert you if things change, many pieces of software use hashes to verify files have not changed. These range from things like rkhunter which only check a few key system files to AIDE, AFIC, and OSSEC-HIDS which check much, much more.

---

### Post by jonnan on 2008-02-07
> **euler_fan said:**
> The problem with cryptographic signing is very simple and twofold:
1) Whose certificate do you use to sign and how do you know to trust them?
2) Eats processor time like crazy. It is it take forever to hash large files, much less large numbers of files large and small. Throw on cryptographic computations and this is a huge drain on system resources.

If you're looking for a piece of software that will alert you if things change, many pieces of software use hashes to verify files have not changed. These range from things like rkhunter which only check a few key system files to AIDE, AFIC, and OSSEC-HIDS which check much, much more.

Well, as I understand it, there are one way hash algorithms for signatures that don't require certificates (Which is all you would need for verification purposes I should think - you're just verifying the sanctity if the file), but I'm no expert.

Besides - the important part is B) I'm a frickin' MORON, because I didn't understand the level of overhead involved. S'alright - I don't actually mind - I figured there was an obvious reason, but every once in awhile I come up with an obvious idea no one else has, so I check, just to be sure. 

Thanks for telling me. I wonder how quickly the level of complexity increases on hash algorithms vs file size - I'm sure there's a ratio of file size/processor speed where if the speed of hashing a file crosses that line, it becomes worth the CPU time, but haven't the foggiest where that line would rest. 

Ah well, yet another beautiful theory killed by cold unforgiving facts - <G>.

Thanks again - Jonnan

On second thought, if the hash algorithm is faster to check than to generate (which is why hash algorithms are usefule as I understand it - I can verify file integrity much faster than it to actually generate the hash, right?) wouldn't  you only need to generate it once for a given combination of architecture and files? Store the hash value in the file name and actually have the filesystem test the hash value when it's called by another program. Or would that still be generating more overhead than I think it would?

---

### Post by euler_fan on 2008-02-07
> **jonnan said:**
> Well, as I understand it, there are one way hash algorithms for signatures that don't require certificates (Which is all you would need for verification purposes I should think - you're just verifying the sanctity if the file), but I'm no expert.

Besides - the important part is B) I'm a frickin' MORON, because I didn't understand the level of overhead involved. S'alright - I don't actually mind - I figured there was an obvious reason, but every once in awhile I come up with an obvious idea no one else has, so I check, just to be sure. 

Thanks for telling me. I wonder how quickly the level of complexity increases on hash algorithms vs file size - I'm sure there's a ratio of file size/processor speed where if the speed of hashing a file crosses that line, it becomes worth the CPU time, but haven't the foggiest where that line would rest. 

Ah well, yet another beautiful theory killed by cold unforgiving facts - <G>.

Thanks again - Jonnan

On second thought, if the hash algorithm is faster to check than to generate (which is why hash algorithms are usefule as I understand it - I can verify file integrity much faster than it to actually generate the hash, right?) wouldn't  you only need to generate it once for a given combination of architecture and files? Store the hash value in the file name and actually have the filesystem test the hash value when it's called by another program. Or would that still be generating more overhead than I think it would?

You're quite correct in saying you can compute hashes and post them without signing them.

To check a hash you have to compute it for the file in question using known good software and compare it to the reference hash. So there's no way to avoid computing them for every file you want to check.

---

### Post by jonnan on 2008-02-08
Okay - stipulated that I'm being dumb and not getting something here. That said - I'm being dumb and not getting something here.

When I download a file that has been signed, I enter the hash into a program, it verifies that hash without actually computing the hash, because the work to verify the hash against the file is orders of magnitude less than the work to compute the hash.

I am not typically running this against a certificate - when I check that hash, it is *not* verifying in the sense that it is, say, verifying a specific source i.e sourceforge - merely that the hash for file x verifies that this is the same file from which that hash was computed, bit for bit.

Which means that these files, for a given architecture, fileversion and trusted hash function, should have identical hashes across, say, all installations of Ubuntu installed on 32 bit processors. For me, it is safe to have the filesystem rename the binary bash to bash.{SHA512(bash compiled for 32bits)} and hide the 512 bits describing the hash unless I specifically toggle them  (something like ls --hash) on or explicitly access them with the full hash name.

This does *not* protect me from executing a compromised copy of bash on my commandline obviously - unless I happen to have that hash memorized, not likely. But it *does* mean that I can compile a program or script to access bash.{SHA512(bash compiled for 32bits)}, and have the operation of accessing it explicitly trigger a daemon that verifies that hash function against the file and aborts the access if the file has been compromised. 

Since all the copies of gimp, 4.1 under Ubuntu are going to have the same binaries, that hash function only needs to be *computed* once per file - it's the same binary on any 32 bit computer. Link everything in the libraries together in this way, and Gimp only accesses the GTK via signed files, the GTK only accesses the filesystem via signed files, et al down the line. The hash daemon itself is not even designed to create hashes (Well, maybe it is, but that would be done only when a binary is compiled I would think), it  just verifies the hash when the file is accessed explicitly by the hash and allows or denies the access based on whether the file passes the integrity check.
[CENTER]----------------------------------------------------[/CENTER]
Somewhere in that description of what I think is a good idea is an assumption, hidden or explicit, that I have wrong. 

The most obvious candidate is that maybe I'm completely wrong that it is computationally much easier to verify a hash than it is to create one - but that's the way I'm reading the information on hash functions is that they are designed exactly for that. 

The second possibility is that I'm understanding that okay, but still vastly underestimating the CPU load required to verify these hashes with every important file access.

Or am I missing something else completely?

Thanks BTW - I've appreciated the responses, sorry if my ignorance is not your bliss. Just think of how much smarter you look with me pulling the average IQ down so much - <G>

Thanks again - Jonnan

---

### Post by euler_fan on 2008-02-08
No, it's a fundamental misunderstanding about hashes.

Let me do this by example:
I have a piece of software, and I compute a hash (say MD5 for concreteness). I post both on the Internet.

You download both and want to know if the software has downloaded correctly. You have the hash I computed (you downloaded that too), but you have no idea (at this point) what the hash of the copy of the software you downloaded to your machine is.

So YOU RECOMPUTE the hash (or colloquially, you hash or find the hash of) the software you downloaded and compare it to the hash I gave you. If they match, then the software you downloaded is the same as the software I hashed and posted.

---

### Post by jonnan on 2008-02-08
Okay dokey then - I fundamentally misunderstand hashes and need to learn more.

Thanks - Jonnan

---

