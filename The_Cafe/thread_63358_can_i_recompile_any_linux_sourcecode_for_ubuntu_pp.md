---
title: "can i recompile any linux sourcecode for ubuntu ppc???"
date: 2005-09-07
forum: The Cafe
---

### Post by blumediaprojekt on 2005-09-07
I've found an application that i'd love to have run on my powerbook with ubuntu ppc....

Its called Cinelerra..........  [http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)


They have source code available on their website, along with i386, and x86-64 binaries, which obviously wont work on my G4 powerbook....

So, would it be possible to download the sourcecode for this software, and compile it in ubuntu on my powerbook?? Would it work????

---

### Post by mlomker on 2005-09-07
Hard to say if it would work....it is certainly possible to try.  Compiling from source vary between tedius to impossible, depending upon the application.  Getting the dependencies in place tends to be the challenging thing.

apt-get build-essential

That's the first piece, if you've never compiled anything.  You might want to start out with compiling smaller updated apps that you already use.  I suspect the program that you're looking at will be challenging because it's a half-dozen packages, etc.

---

### Post by poofyhairguy on 2005-09-07
[QUOTE=blumediaprojekt]
So, would it be possible to download the sourcecode for this software, and compile it in ubuntu on my powerbook?? Would it work????[/QUOTE]

It could. Sometimes it takes more than that. You really don't know till you try.

---

