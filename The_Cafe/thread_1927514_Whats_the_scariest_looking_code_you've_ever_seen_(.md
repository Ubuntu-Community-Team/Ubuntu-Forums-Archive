---
title: "Whats the scariest looking code you've ever seen? (Or written)"
date: 2012-02-18
forum: The Cafe
---

### Post by JazzPotato on 2012-02-18
OK guys, 
Code can look pretty scary, but when you write a nice efficient little program and look through it, it's like the most beautiful poetry you've ever read!
 The scariest code i've ever seen is probably a DTD or Assembly.
What about you? :D

---

### Post by Docaltmed on 2012-02-18
Scariest code I ever saw was a foot-long tray of FORTRAN punch cards that I dropped on the floor.

---

### Post by robsoles on 2012-02-18
> **Docaltmed said:**
> Scariest code I ever saw was a foot-long tray of FORTRAN punch cards that I dropped on the floor.That'd be scary and a bit crushing all at once.

I've probably had to make something different about something worse some stage or another but I wrote a mazemaking routine that 'blocked' until it returned a maze, including calculated longest path and mapping throughout to the calculated exit - when I rewrote it to be non-blocking (taking many consequetive calls to complete) it turned into some of the most complicated code I ever wrote in my life.

I looked at it six months later and I had to make quite a few notes and re-read it for ages to pick up the threads and be able to make a simple change to the way it was behaving safely :roll: :lol:

It was in Visual Basic and it was for a specific game I thought of. It ran in the version of Wine that was 'it' when 10.04 was about six months old, you can critique it if you like: [www.robsfreespace.com/software/free-basic-games/mazeracer/](www.robsfreespace.com/software/free-basic-games/mazeracer/) :p

---

### Post by jfreak_ on 2012-02-18
The fork bomb is kind of elegant and scary at the same time...

---

### Post by gardnan on 2012-02-18
Perl JAPHs are pretty freaky stuff. 
[http://en.wikipedia.org/wiki/JAPH](http://en.wikipedia.org/wiki/JAPH)

Also, many esoteric programming languages are borderline impossible to program in at all. For example, the language Malbolge is so difficult that to program "Hello, World", they had to search through all possible Malbolge programs.

---

### Post by ikt on 2012-02-18
```
print("I'm standing right behind you")
```

---

### Post by Porcini M. on 2012-02-18
Code with a lot of stuff hardcoded in it (stuff that should be data-driven).

---

### Post by Bachstelze on 2012-02-18
Any piece of C written in Emacs.

---

### Post by SoFl W on 2012-02-18
> **Docaltmed said:**
> Scariest code I ever saw was a foot-long tray of FORTRAN punch cards that I dropped on the floor.
But you numbered the corner of the card in pencil... right?  right?

The scariest code I ever look at is looking at someone else's code, or looking at code I did years ago and don't remember a thing about it.

---

### Post by johnb820 on 2012-02-19
Any code that lacks discernable understanding of basic coding conventions, consistency of said coding conventions, readability or all of the above. It's the stuff that nightmares are made of.

---

### Post by lisati on 2012-02-19
The scariest code I've written was some ASM code which worked perfectly on the machine I had at the time - a '286 machine running MS-DOS.  The machine it was intended for had something similar to a NEC V20 that interpreted some of the 286-specific instructions I'd used a bit differently to what I expected - it would have been safer for me to assume a 8086/8088. 
*facepalm*

---

### Post by LillyDragon on 2012-02-19
Sonic Robo Blast 2's source code, enough said. Scariest looking mess of C++ code I've ever seen; I couldn't begin to figure out where *anything* went to what, disregarding whether or not I had a basic understanding of the DOOM legacy engine at all.

As for what I've written : I really don't think GML counts as a real programming language, (I like to think of it as a complex scripting language built on-top of an already-complete 2D engine with the illusion of absolute "control".) but it's the closest to writing anything I've gotten thus far. (C++ still scares me just a tad; dunno where to start, even though the syntax looks similar to GML.)

Anyway, I'm still refining a level editor (LvlEd, shoot me for the creative name!) for a 2D game I'm working on, and oh jeez, the build script for loading "zones" in the terrain is scary huge and scary confusing. Pretty much, it and the game engine can load portions of the level only when called for, cutting down the stage's initial load-time close to nothing by "streaming" small chunks of a level at a time. It works just fine, but crap it's so flaky and I can't even begin to figure out why! Some "zones" still won't build, or at least do so properly. >_> I think the math holding it all together is just too simple.

---

### Post by donkyhotay on 2012-02-19
I'm not a very good programmer so I'm certain pretty much everything I code is pretty scary to someone that know what they're doing.

---

### Post by MG&amp;TL on 2012-02-19
The standard C library header files, they're covered in macros. Scariest code I've written was probably a really huge switch case, back when I was a **noob**, rather than a noob. Since replaced it with a for loop.

---

### Post by Myrddin Emrys on 2012-02-19
Black Perl: [http://en.wikipedia.org/wiki/Black_Perl](http://en.wikipedia.org/wiki/Black_Perl)

---

### Post by keithpeter on 2012-02-19
> **SoFl W said:**
> The scariest code I ever look at is looking at someone else's code, or looking at code I did years ago and don't remember a thing about it.

Hello All

[http://www.sohcahtoa.org.uk/kepler/tmoon.c](http://www.sohcahtoa.org.uk/kepler/tmoon.c)

The scariest thing is that I *understood* the routines when I wrote this (at least 10 years ago, probably nearer 15).

---

### Post by Bachstelze on 2012-02-19
> **keithpeter said:**
> Hello All

[http://www.sohcahtoa.org.uk/kepler/tmoon.c](http://www.sohcahtoa.org.uk/kepler/tmoon.c)

The scariest thing is that I *understood* the routines when I wrote this (at least 10 years ago, probably nearer 15).

Now that you mention it, I was helping a friend who's a PhD student in Astrophysics with some C last semester, her code was pretty scary too (at least to me, since I have little background in Physics).

*EDIT:* It was also written in Emacs...

---

### Post by CharlesA on 2012-02-19
Does trying to figure out a spot to place some html code in a jungle of html that was mangled by a WYSIWYG editor count? I was trying to help my Aunt with her "simple" website and it was a nasty mess to work with.

That stuff made my eyes bleed, but that might be because I am used to having the source code look neat instead of a huge mess of mixed depreciated elements and stupid stuff like <CENTER> tags instead of using CSS.

It makes me glad that I do my pages the right way.

---

### Post by Bungo Pony on 2012-02-19
Me and a friend of mine used to write programs on our Commdore 64s. He wrote this incredibly sophisticated Blackjack game. It was lots of fun to play... until the program crashed due to a stack overflow. I went in to try and fix the error. The program was full of situations where there was no RETURN for a GOSUB statement, so the stack would just keep piling up until the crash.

BASIC programs use line numbers, and instead of spacing them out by 10s (like everyone else did) he spaced them out by 2s! Inserting code became a horrible nightmare which created even more GOSUB or GOTO statements not to mention scattering pieces of code all over the place, and I eventually gave up on trying to debug the whole nightmare.

---

### Post by pbpersson on 2012-02-19
I was a COBOL programmer between 1986 and 1992.  I was trying to insert a change into a program inside a multi-level nested if-then-else statement that spanned four pages.

That sort of thing gave me a headache.  I was tempted to re-write the whole thing so it made sense but this code ran the factory so I was afraid to touch more than I had to.

---

### Post by TeoBigusGeekus on 2012-02-19
Anything from [this]("http://www.ioccc.org/years.html") page.

---

### Post by pbpersson on 2012-02-19
> **SoFl W said:**
> looking at code I did years ago and don't remember a thing about it.

I always try to put comments in my code so I know years later what I was thinking when I wrote it.....but I find years later that the comments are never clear enough for me to know what in the world I was thinking when I wrote the code.  When I am writing it I think, "This is so self-evident and so clear that anyone can see exactly what is happening here".   Yeah.....right ;)

---

### Post by t1497f35 on 2012-02-19
Perl is the only language that looks the same before and after encryption.

---

### Post by donkyhotay on 2012-02-19
> **Bungo Pony said:**
> Me and a friend of mine used to write programs on our Commdore 64s. He wrote this incredibly sophisticated Blackjack game. It was lots of fun to play... until the program crashed due to a stack overflow. I went in to try and fix the error. The program was full of situations where there was no RETURN for a GOSUB statement, so the stack would just keep piling up until the crash.

BASIC programs use line numbers, and instead of spacing them out by 10s (like everyone else did) he spaced them out by 2s! Inserting code became a horrible nightmare which created even more GOSUB or GOTO statements not to mention scattering pieces of code all over the place, and I eventually gave up on trying to debug the whole nightmare.

I remember coding on my C64 as a kid. Didn't do a whole lot of it but I remember wondering why other programs always had line numbers by 10 rather then by 1 which made more sense to me. It wasn't until I wrote my first program on it and ran into a bug that I realized why.

---

### Post by Porcini M. on 2012-02-19
> **t1497f35 said:**
> Perl is the only language that looks the same before and after encryption.

:lol:

---

### Post by matt_symes on 2012-02-20
> **t1497f35 said:**
> Perl is the only language that looks the same before and after encryption.

Not the scariest looking code i have every seen but i was very impressed by this when i came across it earlier today; an extended regular expression for calculating primes written using Perl !!!

```
perl -wle 'print "Prime" if (1 x shift) !~ /^1?$|^(11+?)\1+$/' <number>
```

(replace <number> with a number to test).

```
matthew@matthew-Aspire-7540:~$ perl -wle 'print "Prime" if (1 x shift) !~ /^1?$|^(11+?)\1+$/' 5
Prime
matthew@matthew-Aspire-7540:~$ perl -wle 'print "Prime" if (1 x shift) !~ /^1?$|^(11+?)\1+$/' 4
matthew@matthew-Aspire-7540:~$ 
```

I would guess to many the regex would look quite scary.

---

### Post by forrestcupp on 2012-02-20
I know this probably doesn't count, but around 1990 during the Cold War, I wrote a program that made it look like I broke into the President's computer. It showed a map of a nuclear missile traveling to Moscow. Right after it blew up, I simulated us getting caught by the FBI. I royally scared the crap out of my cousin. He wanted to try to run away to Canada. :D

And to add to the conversation, that happened to be on a C64. ;)

---

### Post by Old_Grey_Wolf on 2012-02-20
I have seen some old systems where part of the code is written in obsolete programming languages; such as Pascal. What is scary about it is that not very many people know languages like Pascal these days. The companies that use that old code still want someone to keep it working, and I find that scary. :)

---

### Post by forrestcupp on 2012-02-21
> **Old_Gray_Wolf said:**
> I have seen some old systems where part of the code is written in obsolete programming languages; such as Pascal. What is scary about it is that not very many people know languages like Pascal these days. The companies that use that old code still want someone to keep it working, and I find that scary. :)

You have seen modern companies who still use Pascal? Wow.

That brings back some good memories. I started to learn a little Pascal after I got bored with Commodore BASIC and assembly.

---

### Post by Old_Grey_Wolf on 2012-02-21
> **forrestcupp said:**
> You have seen modern companies who still use Pascal? Wow.

Actually, the companies I referred to are maintaining software for city, state, or provincial government bodies that won't or can't afford to replace their outdated systems. I could argue that the government bodies are spending their money in the wrong areas; however, that is futile. They patched the code to work during the Y2K scare, and they are still using it.

There isn't very much of the Pascal code left; however, I know of some that is still in use. Obviously it wouldn't be prudent for me to say where I've seen it.

Wow, scary :twisted:

---

