---
title: "Confining execution of scripts while allowing access to standard applications"
date: 2009-04-06
forum: Security
---

### Post by ohboyotero on 2009-04-06
Hey guys,

I'm a TA for a university course on, among other things, basic UNIX use. I'm trying to figure out how best way to programmatically run student homework scripts without risking:

[LIST]
[*]Deletion or modification of any files outside of the current working directory, or creation of new files outside of the wd
[*]Exploitation of known loopholes in *nix design (i.e. "LAWLZ I'Z R00T NOU!")
[/LIST]

I'm not concerned with malicious students trying to actively attack the execution machine, but closing any obvious security vulnerabilities is an added plus.

I'll be running x86 Hardy server.

Is it enough to run their scripts as a special user which only has access to its home directory? I figure that's no good since there could be (and are) any unbounded number of world-readable/writeable files that could still be affected.

Chroot has the problem that anything outside of the chroot jail is not readable, including the binaries that they will need to invoke in their scripts (e.g. find, grep, cat, etc.). I'd have to duplicate enough of the file structure that their scripts would work, right?

Alternatively, I was thinking I could just run everything off of a live CD, but that's a last resort as it would be very tedious.

What do you pros think? Any thoughts would be appreciated. Thanks!

---

