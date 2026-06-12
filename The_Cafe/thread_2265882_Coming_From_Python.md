---
title: "Coming From Python"
date: 2015-02-18
forum: The Cafe
---

### Post by benrob0329 on 2015-02-18
I want to post this here because it doesn't really fit anywhere else, that is I'm not asking for a solid answer.

I have recently had some trouble with Python3, and was wondering if there was a good language to look to, that has good features for both games and useful (text editor, web browser, etc.) applications. Cross platform is best, and mobile would be a plus. Any Suggestions?

---

### Post by TheFu on 2015-02-18
Just for clarification - when you say "text editor, web browser, etc" ... do you want to create these yourself or just want a language that can?  If you want to create a cross-platform editor, I'd be inclined to push C++ and either GTK+ or Qt libraries. No mobile, but Linux, Windows, OSX.

There are many different kinds of games. Specifics?

A text editor can be written in any language - same for a browser. Clearly, performance will be different based on the OS, language, libraries and your skill.

---

### Post by benrob0329 on 2015-02-18
I have decided on learning Lua, it is suppose to be easy to learn, yet powerful, and it is cross platform (Just look at Minetest). i would be willing to look at another language if it were shown to be better for what I would like to do. For games, 3d mostly was what I was thinking. C and C++ look pretty difficult to learn in comparison to python.

---

### Post by TheFu on 2015-02-18
If you want to do competitive 3D games, you'll use C and C++. Period.  During optimization, you'll write ASM. 
I have a friend in the business of PC game optimizations for when the studios C/C++ code is too slow.

---

### Post by benrob0329 on 2015-02-18
Lua is free to use for both home and commercial use, [http://www.lua.org/license.html](http://www.lua.org/license.html). I understand that C/C++ are very useful and complete programming languages, however there are some things about them that I do not like. Such as how complicated they are for someone without much programming experience like myself. I don't wish to argue, as that would close this feed.

---

### Post by TheFu on 2015-02-18
gcc and g++ are free for home and commercial use too [https://www.gnu.org/copyleft/gpl.html](https://www.gnu.org/copyleft/gpl.html).
There are many things NOT to like about every language, including C or C++ or Lua or Java or Ruby or Python or Perl or .... 500 other languages.

Certainly there are bindings for lua from some gaming engines, if that is your intent. I assumed you wanted to be unlimited in the games you could create - perhaps that was wrong?

Google for 3d game and lua found some results. [http://love2d.org/](http://love2d.org/) - you've probably seen most of them. I find the example games not very realistic. That's fine, if that's your intent.  [http://polycode.org/features/](http://polycode.org/features/) is another.

Python has 3d game engines too [https://www.panda3d.org/screens.php](https://www.panda3d.org/screens.php)

I had it in my mind that you wanted to create everything, but if using an existing game engine is fine, seems there are many choices.  Never used any of these myself.  [https://en.wikipedia.org/wiki/List_of_game_engines#Free.2Flibre_and_open_source_software](https://en.wikipedia.org/wiki/List_of_game_engines#Free.2Flibre_and_open_source_software) has some more in a table. Take a look at the primary programming language column.  

Licensing
If you want to release a game or group of games commercially, it is important to have a good grasp of the different major software licenses.  For commercial software projects, the BSD, MIT, Artistic, and Apache licenses tend to be more favorable, then the LGPL.  If you are careful, then the GPL or AGPL can be used as well but that might not be as easy as it appears - basically keep all that code separate and don't link to it or your software must also be GPL'd.  That's completely fine and there is a market for it.  Just have your eyes open, as it seems you already do.

---

### Post by benrob0329 on 2015-02-18
The reason I want to switch from python to something else (no pun intended :)) is because I am having trouble using pip3 to add libraries [http://ubuntuforums.org/showthread.php?t=2265670](http://ubuntuforums.org/showthread.php?t=2265670). I will look into C/C++.

---

### Post by benrob0329 on 2015-02-18
Polycode looks pretty good: [http://polycode.org/features/ ]("http://polycode.org/features/")

---

### Post by benrob0329 on 2015-02-18
[http://www.maratis3d.org/](http://www.maratis3d.org/)

---

### Post by benrob0329 on 2015-02-18
maybe Lua isn't the best option, any other object-oriented languages I should look at?

---

### Post by benrob0329 on 2015-02-18
Perl looks promising.

---

### Post by benrob0329 on 2015-02-18
[http://www.perl.com/pub/2004/12/01/3d_engine.html](http://www.perl.com/pub/2004/12/01/3d_engine.html)

---

### Post by TheFu on 2015-02-18
> **benrob0329 said:**
> Perl looks promising.

I'm a perl guy and would never think to write a game in that language.  Perl is a wonderful language for certain type so of people. Perl 5 is mature, but it has lots of warts and modules tacked on to make it more maintainable and modern.  Perl6 is a completely new language and hasn't been released for production use. Perl5 has a bad rap for being a write-once language - meaning even the creator of a program can't fix bugs in his own code.  Crap code can be written in any language. Elegant code can also be written in any language.  

If you want to see lots of different languages [http://rosettacode.org/](http://rosettacode.org/) is a good overview. Pick a problem that you've solved in python and look through the way that other languages solve it.

OTOH, if you already have a problem and want to pick the best language for solving it, I would generally look at how others have solved it previously and follow that as a guide.  For processing text, there are many choices.  For handling matrix math easily, there are different, fewer choices.  For raw performance, there are about 3 choices.  The normal trade-off is development time vs programming runtime speed. Sometimes developer time matters more than runtime performance - just look at java and ruby - both are fantastic languages. I **like** programming in Ruby.

Of course, what do I know? You can prove me wrong easily.  Passion will override many things.

---

### Post by ofnuts on 2015-02-18
> **benrob0329 said:**
> The reason I want to switch from python to something else (no pun intended :)) is because I am having trouble using pip3 to add libraries [http://ubuntuforums.org/showthread.php?t=2265670](http://ubuntuforums.org/showthread.php?t=2265670). I will look into C/C++.

Switching languages for this reason doesn't make sense. Do you really think you won't have equivalent problems sooner or later with another language?

---

### Post by benrob0329 on 2015-02-18
Not the same problem. That one is a continual problem for me, in both Windows and Ubuntu.

---

### Post by benrob0329 on 2015-02-19
I have a question though, why is C/C++ better for writing a game?

---

### Post by TheFu on 2015-02-19
> **benrob0329 said:**
> I have a question though, why is C/C++ better for writing a game?

Lower memory use, higher runtime performance and there isn't any program that cannot be created using C. Drivers are written in C, operating systems are written in C.  C is the closest non-assembly language to the hardware, so it doesn't require many layers and layers and layers like python, perl, Java, Ruby to get the same result.

I take it you are not a CS major?

---

### Post by benrob0329 on 2015-02-19
So, if I were to learn C, I could in theory, write my own OS? Can you do that in C++?

---

### Post by TheFu on 2015-02-19
> **benrob0329 said:**
> So, if I were to learn C, I could in theory, write my own OS? Can you do that in C++?

Yes. If you learn C, you can.
C++ makes more sense on large, complex, projects.  Learning C first before learning C++ is a natural progression.
We've been beating this for awhile: [http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program](http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program) contains my considered thoughts on learning to program. A few others have replied with their agreement/disagreement.  

It also shows my ignorance of beautiful javascript code - having never seen any even now.  My bias against php comes thru too. I just don't see any reason why any programmer would choose to learn a language known to be highly hacked and the core developers have a history of releasing code with known critical security flaws.  That is unacceptable to me. Php is to be avoided for that reason.

---

### Post by benrob0329 on 2015-02-19
Ok, I'm going to learn C! Thanks TheFu!

BTW, You have a lot of coding background! Did you do any coding on a TI-99 4A? I have one, for the sake of having a computer that&#8217;s literally 30 years old :).

---

### Post by benrob0329 on 2015-02-19
BTW, we all have Bias, we just show it in different ways.

---

