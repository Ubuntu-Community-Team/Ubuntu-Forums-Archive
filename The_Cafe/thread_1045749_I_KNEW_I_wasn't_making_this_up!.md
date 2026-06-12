---
title: "I KNEW I wasn't making this up!"
date: 2009-01-20
forum: The Cafe
---

### Post by MaxIBoy on 2009-01-20
> **MaxIBoy said:**
> Ken Thomson himself said that a virus could "reproduce" by injecting its own code into a compiler itself. Compiling a fresh install of the compiler could be made useless. 

After that, it's just a matter of inserting a very small amount of malicious code into anything you compile. It's only a matter of time before you run something with root privileges, and then there goes the neighborhood.


Ever since I posted that, I've been wondering where I learned that (I'd heard it from somewhere, but I couldn't remember where.) Well, I still don't remember, but I have verification for this now. What's more, he actually did it!


Allow me to quote the Jargon File (version 4.3.1) entry for "back door:"
> back door n.
[common] A hole in the security of a system deliberately left in place by designers or maintainers. The motivation for
such holes is not always sinister; some operating systems, for example, come out of the box with privileged accounts
intended for use by field service technicians or the vendor's maintenance programmers. Syn. trap door; may also be
called a `wormhole'. See also iron box, cracker, worm, logic bomb.
Historically, back doors have often lurked in systems longer than anyone expected or planned, and a few have become
widely known. Ken Thompson's 1983 Turing Award lecture to the ACM admitted the existence of a back door in early
Unix versions that may have qualified as the most fiendishly clever security hack of all time. In this scheme, the C
compiler contained code that would recognize when the `login' command was being recompiled and insert some code
recognizing a password chosen by Thompson, giving him entry to the system whether or not an account had been created
for him.
Normally such a back door could be removed by removing it from the source code for the compiler and recompiling the
compiler. But to recompile the compiler, you have to use the compiler -- so Thompson also arranged that the compiler
would recognize when it was compiling a version of itself, and insert into the recompiled compiler the code to insert into
the recompiled `login' the code to allow Thompson entry -- and, of course, the code to recognize itself and do the whole
thing again the next time around! And having done this once, he was then able to recompile the compiler from the
original sources; the hack perpetuated itself invisibly, leaving the back door in place and active but with no trace in the
sources.
The Turing lecture that suggested this truly moby hack was later published as "Reflections on Trusting Trust",
"Communications of the ACM 27", 8 (August 1984), pp. 761-763 (text available at [http://www.acm.org/classics](http://www.acm.org/classics)). Ken
Thompson has since confirmed that this hack was implemented and that the Trojan Horse code did appear in the login
binary of a Unix Support group machine. Ken says the crocked compiler was never distributed. Your editor has heard
two separate reports that suggest that the crocked login did make it out of Bell Labs, notably to BBN, and that it enabled
at least one late-night login across the network by someone using the login name `kt'.



Okay, now I'm scared. Who's with me?

---

### Post by Truefire on 2009-01-20
No one - if the the compiler didn't have the virus in the first place ( as Ubuntu and new 'nixes do NOT) then you have nothing to worry about. It's ancient and a long-dead evil.

---

### Post by MaxIBoy on 2009-01-20
I'm not saying that the exact same virus is still around. I'm just saying that another virus could easily use the same attack vector. No bugs to exploit, and not even permissions will save you. On a source-based distro like Gentoo, this could be seriously evil.

---

### Post by hyperyoda on 2009-01-20
Ken Thompson is an EPIC hacker. He pwns all of us! haha.

---

### Post by zekopeko on 2009-01-20
md5/sha1 sums are your friends.

---

### Post by geoken on 2009-01-20
The problem with this attack is that most of us install/build our systems using compilers that run completely independently of our systems and are located on read only memory.

How would this, or a similar attack affect a typical CD based installer?

---

### Post by MaxIBoy on 2009-01-20
I'm not saying this is likely to happen. I'm just saying that precautions should be taken. For example, you could check to see if a compiler was sanitary by running it in a sandbox. 

Worst case scenario: some unfortunate package maintainer gets cracked by other means and starts infecting other people. Or a cracker could offer to "generously" host a mirror of a "modified" open-source program. Good targets would be programs that are commonly run with root access; installers would be ideal. Here's some pseudocode to show what I mean:
```
/*hee, hee, hee. No one will ever catch me compiling this code into 
(insert application here.)*/

gccCheckSum = md5(/usr/bin/gcc-4.2)

/*Get the version of gcc that is installed locally, using a hash table of
known checksums of different gcc versions. gccVersion will be a string 
describing the version, architecture, etc.*/ 
gccVersion = find_key_in_hash_table(known_gcc_checksums, gccCheckSum) 

/*Find the byte offset to inject the malicious code, based on the current
gcc version.*/
injection_point_offset = find_key_in_hash_table(injectionPoints, gccVersion)

/*Construct an infected version of the gcc binary.*/
dd -if=/usr/bin/gcc-4.2 -of=/tmp/.g bs=1 count=injection_point_offset
echo maliciousCode >> /tmp/.g
dd -if=/usr/bin/gcc-4.2 -of=/tmp/.g bs=1 skip=injection_point_offset conv=notrunc,append

/*Unleash the tainted binary.*/
mv /tmp/.g /usr/bin/gcc-4.2
```
After that, gcc itself is infected.

This crack is still easily defeated using strace.


At this point, I'm theorizing. But remember, to catch a black hat, you need to think like one.

---

### Post by kk0sse54 on 2009-01-20
> **MaxIBoy said:**
> I'm not saying that the exact same virus is still around. I'm just saying that another virus could easily use the same attack vector. No bugs to exploit, and not even permissions will save you. On a source-based distro like Gentoo, this could be seriously evil.

Probably be worse for binary-based distros than source based because if the package maintainer got infected suddenly he's uploading some nice malicious packages to the repo for other people to download while for a gentoo user the infection would only be localized since the binary packages wouldn't be distributed through portage.

---

### Post by MikeTheC on 2009-01-20
Well, speaking for myself, the first place I'd heard of a "back door" was in the movie [War Games](http://en.wikipedia.org/wiki/WarGames).

[Here's the trailer for it.](http://www.youtube.com/watch?v=tAcEzhQ7oqA)

---

### Post by loell on 2009-01-20
diff.

---

