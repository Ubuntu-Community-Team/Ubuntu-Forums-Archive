---
title: "Cobol...approaching 50 years old...."
date: 2009-04-11
forum: The Cafe
---

### Post by I-75 on 2009-04-11
Before Linux, before Microsoft and before Unix...there was Cobol. 


"Cobol hits 50 and keeps counting

It is 50 years old this year, but Cobol is still a key player in behind-the-scenes business software"

[http://www.guardian.co.uk/technology/2009/apr/09/cobol-internet-programming](http://www.guardian.co.uk/technology/2009/apr/09/cobol-internet-programming)

---

### Post by samjh on 2009-04-11
Probably the most overlooked programming language ever.  And one that's not dying without a very long, tiring fight. :)

[i]In the beginning, The Programmer said, "Let there be a business programming language".

And there was COBOL.

And The Programmer saw it was overly verbose.[/i]

(Yes, that's of my own making.  Yes, it is a bad joke.)

---

### Post by Icehuck on 2009-04-11
> **samjh said:**
> Probably the most overlooked programming language ever.  And one that's not dying without a very long, tiring fight. :)



Unfortunately, it just won't die.

---

### Post by lisati on 2009-04-11
I learned some COBOL many years ago, and never really liked it too much - too verbose, for one thing. I'd rather have something concise like ```
mvc outputname,itemname
``` than ```
move itemname to outputname
```

---

### Post by measekite on 2009-04-11
> **lisati said:**
> I learned some COBOL many years ago, and never really liked it too much - too verbose, for one thing. I'd rather have something concise like ```
mvc outputname,itemname
``` than ```
move itemname to outputname
```

But in the second example all you need to know is English.

---

### Post by lisati on 2009-04-11
> **measekite said:**
> But in the second example all you need to know is English.

True: but have you ever tried writing a system utility (e.g. to handle "file not found" errors without the OS going berserk) in COBOL? What precious little sanity I've somehow managed to retain over the years would quickly go on vacation.

---

### Post by RiceMonster on 2009-04-11
> **Icehuck said:**
> Unfortunately, it just won't die.

Yep. On first glance you may think "hey that looks easy", but once you actually use it, you'll realize just how tedious it is. Best way to sum it up: you're writing so much to do so little.

---

### Post by Mehall on 2009-04-11
+1

The ultimate High Level Language will be written entirely in native tongue and the compiler will understand what you want.

COBOL was before it's time with that.

EDIT: That was @what measekite said

---

### Post by jflaker on 2009-04-11
COBOL Hello World Program
```

000100 IDENTIFICATION DIVISION.
000200 PROGRAM-ID.     HELLOWORLD.
000300
000400*
000500 ENVIRONMENT DIVISION.
000600 CONFIGURATION SECTION.
000700 SOURCE-COMPUTER. RM-COBOL.
000800 OBJECT-COMPUTER. RM-COBOL.
000900
001000 DATA DIVISION.
001100 FILE SECTION.
001200
100000 PROCEDURE DIVISION.
100100
100200 MAIN-LOGIC SECTION.
100300 BEGIN.
100400     DISPLAY " " LINE 1 POSITION 1 ERASE EOS.
100500     DISPLAY "Hello world!" LINE 15 POSITION 10.
100600     STOP RUN.
100700 MAIN-LOGIC-EXIT.
100800     EXIT.

```

Now here it is in C
```

#include <stdio.h>

main()
{
 printf ("Hello World!\n");
}

```

---

### Post by RiceMonster on 2009-04-11
@jflaker: That's exactly what I'm talking about. Plus, I think the syntax is incredibly ugly and only makes the code harder to look at.

---

### Post by jflaker on 2009-04-12
> **RiceMonster said:**
> @jflaker: That's exactly what I'm talking about. Plus, I think the syntax is incredibly ugly and only makes the code harder to look at.

I know one person who would LOVE to code in COBOL if they had the chance.....I program on the IBM iSeries (aka, AS/400) so it can do COBOL as well as C.  I prefer not to have to learn COBOL, but will if I need to.

---

### Post by samjh on 2009-04-12
> **jflaker said:**
> COBOL Hello World Program
```

000100 IDENTIFICATION DIVISION.
000200 PROGRAM-ID.     HELLOWORLD.
000300
000400*
000500 ENVIRONMENT DIVISION.
000600 CONFIGURATION SECTION.
000700 SOURCE-COMPUTER. RM-COBOL.
000800 OBJECT-COMPUTER. RM-COBOL.
000900
001000 DATA DIVISION.
001100 FILE SECTION.
001200
100000 PROCEDURE DIVISION.
100100
100200 MAIN-LOGIC SECTION.
100300 BEGIN.
100400     DISPLAY " " LINE 1 POSITION 1 ERASE EOS.
100500     DISPLAY "Hello world!" LINE 15 POSITION 10.
100600     STOP RUN.
100700 MAIN-LOGIC-EXIT.
100800     EXIT.

```

Hmm.  Isn't it:
```
000100 IDENTIFICATION DIVISION.
000200 PROGRAM-ID. hello.
000300 PROCEDURE DIVISION.
000400     DISPLAY "Hello World!".
000500     STOP RUN.

```
?

(Using OpenCOBOL.)

---

### Post by MaxIBoy on 2009-04-12
[img]http://www.concretebadger.net/images/blog/editorials/killitwithfire.jpg[/img]

---

### Post by measekite on 2009-04-14
> **RiceMonster said:**
> Yep. On first glance you may think "hey that looks easy", but once you actually use it, you'll realize just how tedious it is. Best way to sum it up: you're writing so much to do so little.

Sounds like that is true with C++ as opposed to other more modern languages.

---

### Post by RiceMonster on 2009-04-14
> **measekite said:**
> Sounds like that is true with C++ as opposed to other more modern languages.

Yeah, I really get what you mean, even though I love C++. COBOL is really not very flexible, though. I can't think of much it's good for other than processing financial reports.

---

