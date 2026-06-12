---
title: "Is it safe to use the universe/multiverse/etc?"
date: 2009-06-29
forum: Security
---

### Post by viking_maniac on 2009-06-29
[COLOR=black][FONT=Verdana]I don't know why they're called universe, multiverse, and so on, but I see a lot of programs there. I've already installed MPlayer video player from there and a cryptically named program to be able to control the startup applications better.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I've heard that rootkits are the common threat on Linux/Unix, and that installing an bad application is a great way to get one. Are these programs safe to download and install?[/FONT][/COLOR]

---

### Post by Agent ME on 2009-06-29
Yes, they're safe to use. Everything in the Ubuntu repositories has to get approved by the Ubuntu devs.

I believe the universe and multiverse programs don't strictly fit within the GPL, and/or are given a bit less attention (mainly in being kept up-to-date). Can't really remember what the exact difference was.

---

### Post by decoherence on 2009-06-29
Anything from the official repositories should be fine.

"Universe" refers to software that isn't tested to fit in with the Ubuntu environment. It should still work fine but it might not seem 'ubuntu-y.' Universe software is said to be maintained by the community (rather than by Canonical.)

"Multiverse" contains software that can't be part of Universe or the main repository due to licensing issues.

Frankly, Debian's repository naming makes much more sense. "Main" is... well... main. "Contrib" is contributed work (community maintained) and "Non-free" is non-free work. Not sure why Ubuntu made up these other names. I guess they sounded cooler?

---

### Post by kevdog on 2009-06-29
I hope they are safe because without them life would be bored and I would have one compromised system!!!  Ive been on this board for about 2 years and never seen a complaint about a security breach from these repositories. This doesn't mean its not possible in the future however!

---

### Post by koenn on 2009-06-29
> **Agent ME said:**
>  Everything in the Ubuntu repositories has to get approved by the Ubuntu devs.

I believe the universe and multiverse programs don't strictly fit within the GPL, and/or are given a bit less attention (mainly in being kept up-to-date). Can't really remember what the exact difference was.

Not exactly. The only official repo is main (+ security updates). It's actually a rather small subset of debian main, and ubuntufied. These are the only packages canonical employed ubuntu devs work on. 

Universe is 'all the rest from debian' (+ possibly some other programs) repackaged or recompiled for ubuntu, by "the masters of the universe" (MOTU)- a group of volunteer package maintainers. Multiverse is software that would have gone into universe if it wasn't for license issues - it possibly corresponds to debian's non-free. 

Canonical only claims responsibility for main + updates. For all the rest, you rely on the competence and reliability of the MOTUs.

---

