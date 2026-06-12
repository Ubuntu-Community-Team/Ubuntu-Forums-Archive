---
title: "Which programing language should I learn?"
date: 2011-08-11
forum: The Cafe
---

### Post by ninjaaron on 2011-08-11
Ok, so I'm 26 with a degree in humanities and a second one in the pipes.  I have no ambitions to be a professional programmer or anything like that.  This is the story:

When I was a kid, I always poked around on basic and then I took two years of it in Highschool along with a semester of C++ (forgot all of it).  At the time I wanted to write video games for a living or whatever (like every nerd kid).  Then I sort of got going on a different path, and it's been ten years since I did anything with programming.  This year, I got a Dell duo netvertible for Christmas, and found that stock Ubuntu UI sucked donkey balls for the device.  Some other guys on here were working on tweaks, and somebody suggested a simple script would do nicely for controlling the screen orientation.  Screen rotation was sort of my baby in the group, so I set to work figuring out some rudimentary bash (which is when I learned about [FONT="Courier New"]grep[/FONT], blessed be it's name).  So I eventually I got the rotation under control, but then I had to find a way to make the vitual keyboard resize and move to fit the screen, and then I got unclutter involved to hide the mouse, and then, and then, an then...  So now it's a library of about seventeen scripts, two settings files, one install script, has it's hands in about eight other programs' junk, and has a small manual and setup guide.  Then I started working on some scripts for Arch to automatically detect, connect to, and remeber wifi hotspots. I kinda realized that I really love programming as hobby and would like to continue to work on it for fun.  I have no particular goals except having fun, making my computers do cool stuff, and perhaps contributing bug fixes, patches and whatever to the community.  I eventually want to learn how to do GUI apps, but I have no idea how that works...  and I always had this pipe dream of writing a turn-based RPG too... hmm...

Anyway, just looking for where to go from here.  I'm decent at bash now, though I still have plenty to learn (I've just learned what I needed for my scripts, so there are some functions I haven't even touched.  Just now figuring out about sed).

So, here are some options:

1. Learn some more advanced scripting languages: perl, python, lua, whatever.

2. learn a mainstream programming like Java or C++; c'mon, all the cool kids are doing it.

3. Be a real man and learn C and ASM, or eff that, take it to the next level and just do everything in machine code and binary.

4. MOAR BASH!! (just work on bash until I know it and the standard Linux CLI utils backwards and inside out, then come back and ask again).


P.S.  I remembered that I do have on big ambition: to build a home server that takes acts as a local and remote file server that can stream media to all the multimedia equipment in the house as well as, potentially, remote devices.  Whatever I do should somehow contribute to that goal.

---

### Post by sanderd17 on 2011-08-11
Java is very well documented (which is good if you want to learn the concepts), scripting languages are used for scripts, not a lot for GUI programming. And if you do C(++) you probably best choose a library you like (such as the GTK library or the QT library), where Java has one very big library with a uniform coding style, C(++) has a lot of libraries that all use a different coding style.

You could also learn programming for a portable device (like Android). That's well documented too.

Some problems can also ask for declarative languages as Haskell (functional: everything is a function) or Prolog (logic: everything is a logic statement).

ASM is great to learn the hardware of your computer, but it doesn't learn you anything about programming.

---

### Post by juancarlospaco on 2011-08-11
1) Bash
2) Python
3) Bottle
4) HTML5
6) Profit

---

### Post by MG&amp;TL on 2011-08-11
Lots of people ask this question-I personally like C++, Python and BASH. But others may not. Scripting is fun, I agree.

A few pointers:

For satisfying 'there' results *ad instantanum* take a look at Processing:

[http://processing.org/]("http://processing.org/")

Games will take ages to write, and will most likely be quite unsatisfying. Unless you're really serious, try Game maker ( it runs in wine, and most of it's free (although there's a naff ad on booting the IDE for the 'pro' edition, and an annoying splash screen for the programs, too (although I managed to edit that once)).

Otherwise, stick with python and BASH. That's my opinion, take from it what you will. Oh, and search the forums before posting, people tend to get annoyed if you recycle things. Just a suggestion. :)

---

### Post by 8_Bit on 2011-08-11
Learn Python first. It will open many paths. Panda3D and Blender (both free open source game engines) use Python. Python can also be connected to C++ code, so you can later learn C++ and complement your old Python-fu. :D

---

### Post by unknownPoster on 2011-08-11
> **MG&TL said:**
> 

Games will take ages to write, and will most likely be quite unsatisfying. Unless you're really serious, try Game maker ( it runs in wine, and most of it's free (although there's a naff ad on booting the IDE for the 'pro' edition, and an annoying splash screen for the programs, too (although I managed to edit that once)).

Otherwise, stick with python and BASH. That's my opinion, take from it what you will. Oh, and search the forums before posting, people tend to get annoyed if you recycle things. Just a suggestion. :)

I agree with Game design being very challenging and frustrating. I've taken two courses focused on Game design and it's really not for me.

That being said, PyGame is a very useful and easy to use library for creating games. It would excellent to learn Python with as well, since both are fairly simple. If it's any indication, very simple games can be made in PyGame in about an hour, if you know Python (You're the red box, if you get hit by any other bouncing box you die.)

---

### Post by ninjaaron on 2011-08-11
And one other semi-related question about style.  In my netvertible UI library, I tried to make the code as well documented as possible cause I heard that was good, along with very descriptive variables and all.

I also made it super modular because they told us that was good style in Highschool (or, they said to use subroutines for everything, but that was Basic).  I made it so each script basically does one thing and gets other scripts to do other things.  If several scripts preform the same task, it becomes a subscript of it's own.  Part of the reason for this was to make it as easy to add or change as possible, so if someone wanted to try something else with it, or I had new ideas, they would be easy to add in a modular fashion.  This has worked incredibly well for me so far.  Now, I hear that this kind of thing can be difficult to debug, and I do run into a little bit of that, but I'm not sure a large and involved script would be any easier.  It's like Henry Ford said, "nothing is difficult when broken into small tasks."

Finally, I once read that Linus said that a good programmer never needs more than two levels of indentation, so I never have more than two levels of indentation, not that anything is particularly difficult.  I think this is more of that modularity stuff. Course, if you count all the nested scripts, there are... lots and lots and lots of levels of indentation...

I've tried to be efficient as possible, making the computer do as little as possible on any given pass.  This is pretty arbitrary, given that I have no idea what is actually involved in each command, but I've tried to make fewer commands and smaller chunks of data the general rule.  However, if I ever have to choose between efficiency and modularity, I usually choose modularity.  Normally, they seem to work together, but not always.  It's a very small program, so everything runs pretty much instantly, but it's the principle.  Trying to make good habits 

So, is this good style? Would it be better to have some scripts do several things, or is it better to chop it all into tiny pieces like I'm doing?

---

### Post by papibe on 2011-08-11
Bash will always be very helpful. A few lines of bash can save you hours working on the Desktop (for [example]("http://ubuntuforums.org/showthread.php?t=1536915&highlight=resize")).

Python would be a good step from Bash. Although it is interpreted as Bash, it is a high-level programming language. You can do scripting on the command line, and also create desktop applications (using the Gtk library like in this [example]("http://www.omgubuntu.co.uk/2011/06/gnome-screencasts-taking-tutorials-to-the-next-level/")).

Regards.

---

### Post by juancarlospaco on 2011-08-11
Random Example : [http://arcade.rawrbitrary.com/mario/](http://arcade.rawrbitrary.com/mario/)

---

### Post by ninjaaron on 2011-08-11
> **sanderd17 said:**
> Some problems can also ask for declarative languages as Haskell (functional: everything is a function) or Prolog (logic: everything is a logic statement).  Flanders as in Belgium?  I did my whole undergrad degree in Sint Pieters Leeuw! 

Anyway, I've never heard of those.  I'll have to look into that stuff.

> **juancarlospaco said:**
> 1) Bash
**2) Python**
3) Bottle
4) HTML5
6) Profitwtf is bottle? does this have to do with programming or drinking?

> **MG&TL said:**
> Lots of people ask this question-I personally like C++, **Python** and BASH. But others may not. Scripting is fun, I agree.

...

Games will take ages to write, and will most likely be quite unsatisfying. Unless you're really serious, try Game maker ( it runs in wine, and most of it's free (although there's a naff ad on booting the IDE for the 'pro' edition, and an annoying splash screen for the programs, too (although I managed to edit that once)).
...
Oh, and search the forums before posting, people tend to get annoyed if you recycle things. Just a suggestion. 
Hey, lay off me.  I know people ask this question every second day, but this is different.  I'm not some kid who feels it's his destiny to be a great programmer or an IT professional.  I'm an adult who wants a hobby, and has the small goal of creating the most ***-kicking home server ever.

Anyway, games aren't a big deal to me now really.  It's more of a nostalgic idea than anything.

> **8_Bit said:**
> Learn **Python** first. It will open many paths. Panda3D and Blender (both free open source game engines) use Python. Python can also be connected to C++ code, so you can later learn C++ and complement your old Python-fu. :D

> **unknownPoster said:**
> If it's any indication, very simple games can be made in PyGame in about an hour, if you know **Python** (You're the red box, if you get hit by any other bouncing box you die.)

I already made that game for my final project in Basic II :/

***


Ok, I'm seeing a trend.  I'll keep going with bash, and add some python in there, and maybe later some Java or C++.

I must say, this HTML5 is also interesting, but I have no idea what it's all about.  I used to know 'old' HTML.  It wasn't very exciting.  It is not programming... programs move and do stuff. HTML (the old one) just sits there.

---

### Post by ninjaaron on 2011-08-11
> **papibe said:**
> Bash will always be very helpful. A few lines of bash can save you hours working on the Desktop (for [example]("http://ubuntuforums.org/showthread.php?t=1536915&highlight=resize")). werd. My first bash script was when I needed to change 4000 filenames from upper case to lower case.

The second link is cool too. I'm going to watch those.

> **juancarlospaco said:**
> Random Example : [http://arcade.rawrbitrary.com/mario/](http://arcade.rawrbitrary.com/mario/)

I died.

---

### Post by Bandit on 2011-08-11
A scripting language would be best for starters, it will let you get used to programming without the headaches of compiling every time your wanting to test something. Which scripting language? Well that depends one what platforms you want to really do. If you want it for personal use on your Linux machine BASH is an excellent option. Many say Python is another great one after BASH but I personally haven't programmed in it as BASH normally does what I need to do. Now LUA is one I didnt see mentioned here, but it claims to be the fastest scripting language out that speed wise is comparable to compiled programs made in C or C++. Its what I am attempting to learn now. 
Other then those, C and C++ are the most useful true programming languages and the most widely used, but more complex then the previous scripting languages mentioned. It should be your final destination, but may be to complex to be your first start.

Cheers..

---

### Post by MG&amp;TL on 2011-08-11
> **ninjaaron said:**
> 

Hey, lay off me.  I know people ask this question every second day, but this is different.  I'm not some kid who feels it's his destiny to be a great programmer or an IT professional.  I'm an adult who wants a hobby, and has the small goal of creating the most ***-kicking home server ever.

Anyway, games aren't a big deal to me now really.  It's more of a nostalgic idea than anything.




Sorry, it wasn't my intention to sound aggressive, It's just that I've answered four of these in the last month (a spread, from teenagers to old men), and in the last one, tempers got raised somewhat. just a suggestion, as I said. Sorry. :(

And hey, I'm 'some kid' and I program. Lay off yourself :P

---

### Post by BrokenKingpin on 2011-08-11
C++ or C#.

---

### Post by ninjaaron on 2011-08-11
> **MG&TL said:**
> Sorry, it wasn't my intention to sound aggressive, It's just that I've answered four of these in the last month (a spread, from teenagers to old men), and in the last one, tempers got raised somewhat. just a suggestion, as I said. Sorry. :(

And hey, I'm 'some kid' and I program. Lay off yourself :P

There was meant to be some sort of sarcastic smile in my post or something.

WE ARE NOT FIGHTING.

---

### Post by MG&amp;TL on 2011-08-11
Meh, sorry, stuff happens. <Mightily embarassed> I know, the smilies don't always work. On with the original question, if you want to create a server, you might want to look at Ubuntu server edition (command-line with command-line tools for servers.)

---

### Post by ninjaaron on 2011-08-11
> **Bandit said:**
> Now LUA is one I didnt see mentioned here, but it claims to be the fastest scripting language out that speed wise is comparable to compiled programs made in C or C++. Its what I am attempting to learn now.

If you want to play with LUA, you might want to check out "awesome" window manager. The whole DE is apparently configured with LUA.  It's in the universe repo, and it'll pop up right in GDM.  I installed it for a little while, but when I opened the config file and saw a bunch of scripting language that I didn't recognise, I got the heck out.  I wasn't going to learn a new programming language so I could change my wallpaper.  Shame though, the window management was pretty great... dare I say... awesome?

Course, if you are already trying to learn Lua, it would be perfect.

---

### Post by zkissane on 2011-08-11
What do you want to do?

Do you want to write basic interactive sites?  Try Ruby on Rails or PHP.  Along the way, you'll likely learn some SQL, HTML(5), and Javascript.

Do you want to write enterprise applications (maybe web-enabled, maybe not)?  C# or Java.  Along the way you'll probably pick up some SQL, HTML, Javascript, and XML.

Do you want to write operating systems or drivers?  Do you want to write core OS components (things like GNOME, KDE or Unity)?  C or C++.

Do you want to write mobile apps?  Objective-C + the iOS framework, or (maybe) Java + the Android framework.  I know that with Android, you'll pick up some XML along the way.

Do you want to write hardcore 3D video games?  C, C++, and maybe C# (I think whatever DirectX is nowadays can work with C#).

Do you want to write simple-ish non-Web based applications for the desktop?  C#, Visual Basic, or Python.


I've done C++, Java, Javascript, and Rails, with some SQL and Bash scripting too.  If you're just interested in learning for learning's sake, I'd go with Java.  It's very well documented by the people that make it.  It's reasonably accessible for the beginner (you don't have to jump through a ton of hoops to get a basic program to "just work").  It has a perfectly adequate built-in class library for the beginner, IMO.  I think it has a good balance of verbosity to learn OO concepts without being overwhelming, or being too terse.  I don't know much about Python but from reading its disciples it would be a good language too.

---

### Post by Paqman on 2011-08-11
Ubuntu has some good tools that really smooth out a lot of the road bumps in developing little apps in Python. Check out [Quickly](apt:quickly), it'll take care of all the dull stuff like packaging, distribution and licensing. Just write your code and it'll package it all and push it out to people in a PPA.

---

### Post by ninjaaron on 2011-08-11
> **MG&TL said:**
> On with the original question, if you want to create a server, you might want to look at Ubuntu server edition (command-line with command-line tools for servers.)Server edition isn't going to just light up and do whatever I want.  I have a feeling some coding is going to be involved in setting up the remote file server, not to mention having it stream media to different locations in the house.  I also what mobile devices to be able to act as remotes for the the media systems all over the house.  This will take some programming methinks.

Just what is the "P" in LAMP for anyway?

> **zkissane said:**
> What do you want to do?Have fun. Mostly, make the most badass wired up house ever.

> Do you want to write basic interactive sites?  Try Ruby on Rails or PHP.  Along the way, you'll likely learn some SQL, HTML(5), and Javascript. No, but I'm sure I'll have to use some PHP and SQL for my home server project.  I have a blog that I could theorectically host myself, but I'm perfectly happy with the blogspot hosts it, and it's more wired to the rest of my Google stuff that way.

> Do you want to write enterprise applications (maybe web-enabled, maybe not)?  C# or Java.  Along the way you'll probably pick up some SQL, HTML, Javascript, and XML.NEVER!!

> Do you want to write operating systems or drivers?  Do you want to write core OS components (things like GNOME, KDE or Unity)?  C or C++.First, Unity isn't a core OS component, though it is written in C.  It's a compiz pluggin that happens to be running over Gnome 2.x at the moment.  I wouldn't mind trying to write something like Unity, just a simple interface layer, but I would never be interested in making something as complex as Gnome or KDE.  I just want to play with stuff, not actually make something useful like that.

> Do you want to write mobile apps?  Objective-C + the iOS framework, or (maybe) Java + the Android framework.  I know that with Android, you'll pick up some XML along the way. I like to entertain the idea of doing so.  That sounds like a nice platform for "fun little things" that a hobbyist could really get into.  I already know a little XML.  It's hard to be a tweaker without encountering it quite a bit. Heck... I've edited SVG's in gedit before, when I was really hard-up.

> Do you want to write hardcore 3D video games?  C, C++, and maybe C# (I think whatever DirectX is nowadays can work with C#).No Way! If I ever wrote a game, it would sprites all the way Polygons are overrated.

> Do you want to write simple-ish non-Web based applications for the desktop?  C#, Visual Basic, or Python.probably this, mostly.


> I've done C++, Java, Javascript, and Rails, with some SQL and Bash scripting too.  If you're just interested in learning for learning's sake, I'd go with Java.  It's very well documented by the people that make it.  It's reasonably accessible for the beginner (you don't have to jump through a ton of hoops to get a basic program to "just work").  It has a perfectly adequate built-in class library for the beginner, IMO.  I think it has a good balance of verbosity to learn OO concepts without being overwhelming, or being too terse.  I don't know much about Python but from reading its disciples it would be a good language too.

It's looking like Python will be the next thing for me, with more Bash, of course. Maybe one of the C's or Java if I ever feel that Python is too limited for my needs.  I actually used to know some C++, but I have forgotten all of it.

---

### Post by firefly2442 on 2011-08-11
> **ninjaaron said:**
> 
Just what is the "P" in LAMP for anyway?


Linux Apache MySQL and PHP (LAMP)

---

### Post by juancarlospaco on 2011-08-11
> **firefly2442 said:**
> Linux Apache MySQL and PHP (LAMP)

Linux Apache MySQL and Python (LAMP)

(¬&#8255;¬)

---

### Post by jeffbilling on 2011-08-11
Depending on what you want to do it may be worth looking at 'Squeak'.
It is great fun and you can develop programs quickly.

---

### Post by wojox on 2011-08-11
C/C++, Java, or PERL. 

You can do anything with those three languages. A lot of other languages derived from them. Well PHP, Python ...

Bash is nice but you'll only find that in the unices. :P

---

### Post by wojox on 2011-08-11
> **juancarlospaco said:**
> Linux Apache MySQL and Python (LAMP)

(¬&#8255;¬)

You forgot PERL. :D

---

### Post by ninjaaron on 2011-08-12
> **wojox said:**
> You forgot PERL. :D

Ruby :confused:

---

