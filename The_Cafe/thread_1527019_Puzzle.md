---
title: "Puzzle"
date: 2010-07-08
forum: The Cafe
---

### Post by iris-n on 2010-07-08
Fellows,

I propose you a puzzle. Download the attached tarball, untar it, and try to tar it again. You won't. The puzzle is to find out why.

It is due to a bug in file-roller, that I have already reported, so nevermind about that. It was fun for me to debug, and I think you will find find it funny too.

1st hint: 

It is very hard if you do it the wrong way, and very easy if you do it the right way.

2nd hint:

There is no double entendre in the first hint.

3rd hint:

One of the hints is false.

---

### Post by marshmallow1304 on 2010-07-08
11 000a

---

### Post by iris-n on 2010-07-19
wat/

anyway, bump.

---

### Post by marshmallow1304 on 2010-07-19
[COLOR="White"]File 11 has a line feed (000a) in the filename.[/COLOR]


Edit: For the sake of the puzzle, my solution is hidden.  Highlight the post to read it.

---

### Post by murderslastcrow on 2010-07-19
I vote hint 3.

---

### Post by mobilediesel on 2010-07-19
> **iris-n said:**
> Fellows,

I propose you a puzzle. Download the attached tarball, untar it, and try to tar it again. You won't. The puzzle is to find out why.

It is due to a bug in file-roller, that I have already reported, so nevermind about that. It was fun for me to debug, and I think you will find find it funny too.

1st hint: 

It is very hard if you do it the wrong way, and very easy if you do it the right way.

2nd hint:

There is no double entendre in the first hint.

3rd hint:

One of the hints is false.

It's not a bug because a line-feed doesn't belong in a filename.

---

### Post by iris-n on 2010-08-15
> **mobilediesel said:**
> It's not a bug because a line-feed doesn't belong in a filename.

Wrong. UNIX file systems allows all characters except for \0 (and /, but that's trivial). See for example the POSIX standard or the specs of any Linux filesystem, e.g., [ext4]("http://en.wikipedia.org/wiki/Ext4").

How did you do it, marshmallow1304? When I first encountered this bug it took me a while to debug, because I was using the bisection method for root finding, and it does not work in this case: if you separate the folder in two ones, each containing 5 files, both will compress ok.

---

### Post by mobilediesel on 2010-08-15
> **iris-n said:**
> Wrong. UNIX file systems allows all characters except for \0 (and /, but that's trivial). See for example the POSIX standard or the specs of any Linux filesystem, e.g., [ext4]("http://en.wikipedia.org/wiki/Ext4").

I know UNIX file systems allow for a line feed to be in a filename. That doesn't mean a line feed belongs in a filename.

---

### Post by marshmallow1304 on 2010-08-15
I highlighted all the files in nautilus and file 11 had an extra highlighted line.

---

