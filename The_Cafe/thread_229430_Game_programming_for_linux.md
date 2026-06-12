---
title: "Game programming for linux"
date: 2006-08-04
forum: The Cafe
---

### Post by Specialsauce on 2006-08-04
is there a book strictly on this subject? A long shot, maybe, but i figure i'd ask... If there is, cans omeone please recommend me a book on amazon that is good on this subject. I know a little bit of C++ but im definateley willing to learn another language. PLease help.

---

### Post by IYY on 2006-08-04
Read up on the QT toolkit. There are many many books:

[http://www.amazon.co.uk/gp/browse.html/202-1389760-1644622?node=14160171](http://www.amazon.co.uk/gp/browse.html/202-1389760-1644622?node=14160171)

With it, you can make games that'll work on Windows, OS X and Linux.

---

### Post by Lord Illidan on 2006-08-04
Try getting an opengl book.

---

### Post by G Morgan on 2006-08-04
C/C++ is by far the best language for gaming and I wouldn't try anything else. I agree with Lord Illidan but I'd widen it and say go for SDL (OpenGL is part of SDL) as the best starting place (start off in 2D, when you've got experience there move up to OpenGL).

[This site has a good tutorial to SDL.]("http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/gfxsdl/index")

---

### Post by mostwanted on 2006-08-04
> **G Morgan said:**
> C/C++ is by far the best language for gaming and I wouldn't try anything else. I agree with Lord Illidan but I'd widen it and say go for SDL (OpenGL is part of SDL) as the best starting place (start off in 2D, when you've got experience there move up to OpenGL).

[This site has a good tutorial to SDL.]("http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/gfxsdl/index")

OpenGL isn't part of SDL. SDL is a 2D graphics and sound library, OpenGL is a separate graphics library (no sound) mainly geared at 3D and provided as a an alternative to Microsoft's Direct3D (part of DirectX). The two are not related projects.

And C/C++ aren't the best languages for gaming, they're just the most widely used ones because modern 3D games typically require the best performance and the complex low level design of those languages provide that. It's quite possible to program games in any language you'd like, Civilization 4 uses compiled Python and Crash Bandicoot uses LISP to give some examples.

---

### Post by G Morgan on 2006-08-04
Performance is everything in gaming, this is why C/C++ rules. People don't use it for the sake of being akward they use it because it is the best tool for the job. It depends what you intend on doing of course, if your only interested in making card games like Solitaire then I suppose you could even use Java and lose 200MB for the VM from the beginning. If you intend to move on to more complex games then you may as well start with practically the only tool capable of doing the job.

As for OpenGL/SDL. They are always considered together because SDL regularly provides the functionality that OpenGL needs to make a full game.

//edit - besides the OP already claimed to be a C programmer. Why would he learn another language just to sacrifice efficiency. He loses on both counts.//

---

### Post by Lord Illidan on 2006-08-04
High performance games are almost always coded in c/c++

But for a cards or turnbased game, where performance is not a must, one can use python or whatever he wants.

---

### Post by Redcard on 2006-08-04
Most games nowadays tend to be conglomerations.. with the major core engines written in C, or C++, and the majority of the game being placed on top of it with a scripting language.  The latest thing in the game industry seems to be less and less C++ in favor of a scripting language like python.

Use the C++ for the core aspects of the engine (3d engine, etc) and then the remainder of the project is coded in Python/XML .  That seems to be the most popular way hi quality commercial games are coded in the last year or two.

---

### Post by G Morgan on 2006-08-04
> **Redcard said:**
> Most games nowadays tend to be conglomerations.. with the major core engines written in C, or C++, and the majority of the game being placed on top of it with a scripting language.  The latest thing in the game industry seems to be less and less C++ in favor of a scripting language like python.

Use the C++ for the core aspects of the engine (3d engine, etc) and then the remainder of the project is coded in Python/XML .  That seems to be the most popular way hi quality commercial games are coded in the last year or two.

That makes a lot of sense. Rapid turnover in pure C/C++ is non-existent but a scripting language like Python would allow it. Also Python can be learned in a week (to a decent extent).

---

### Post by Lord Illidan on 2006-08-04
> **G Morgan said:**
> That makes a lot of sense. Rapid turnover in pure C/C++ is non-existent but a scripting language like Python would allow it. Also Python can be learned in a week (to a decent extent).

I agree there. Python is very very easy to learn.
As for 3D gaming, I also heard that some really high performance games use assembly directly...is it true?

---

### Post by Redcard on 2006-08-04
My suggestion to the original poster would be to give Pygame and Python a run... it might offer you what you can get started with..

---

### Post by forrestcupp on 2006-08-04
> **Lord Illidan said:**
> I agree there. Python is very very easy to learn.
As for 3D gaming, I also heard that some really high performance games use assembly directly...is it true?

Usually mainly just the core or game engine, which is either c/c++ or assembly.  With a good game engine, you really don't lose much using a language like Python for the game logic code.

If you want to program games, look at some of the free game engines, such as Cube, Ogre, or Crystalspace 3d.  If you're good at c/c++, keep using it.  If you're only a beginner c programmer, maybe try Python.  I know that there is already some kind of implementation to use Crystalspace 3d with Python for the game logic.  I will probably be checking into that some time.

---

### Post by forrestcupp on 2006-08-04
> **Redcard said:**
> My suggestion to the original poster would be to give Pygame and Python a run... it might offer you what you can get started with..

I checked out pygame.  It looks pretty good for simple stuff, but it seems very limited.

---

### Post by Lord Illidan on 2006-08-04
> **forrestcupp said:**
> Usually mainly just the core or game engine, which is either c/c++ or assembly.  With a good game engine, you really don't lose much using a language like Python for the game logic code.
Yes, that's what I was referring to.

What about Cg?

---

### Post by Redcard on 2006-08-04
Well, given that PYGame is a wrapper to the most common used functions of SDL, I think it'd be about as limited as SDL is... 

It certainly accomplishes what I want from it, and looking at pygame.org, the "fanbase" seems to be making some pretty solid games with it

---

### Post by G Morgan on 2006-08-04
I think it all depends on what you want and how long you are willing to spend. If your going to spend years doing this then you may as well spend a bit of time (maybe a few weeks) trying a few directions and then ensure your doing things right early on.

Mostly the same concepts will be used everywhere so the knowledge is at least portable in that much.

Anyway the SDL tutorials I pointed to can probably be done in a long weekend and Python can be learned in a week (if you've already learned C++ both in Procedural and OOP terms then any other high level language should be reasonably straight forward).

---

