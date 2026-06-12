---
title: "Making games for Ubuntu: Easy or not?"
date: 2012-06-28
forum: The Cafe
---

### Post by Sarys on 2012-06-28
Hello! I'd like to know few programs/ways of making games for Ubuntu/linux.
So if someone know easy way for making games with Ubuntu please let me know. Thank you

---

### Post by Sarys on 2012-06-28
Nothing? Really? Don't say there's no easy way to make games with/for linux

---

### Post by whatthefunk on 2012-06-28
It would probably involve programing.  Do you program?

---

### Post by Sarys on 2012-06-28
> **whatthefunk said:**
> It would probably involve programing.  Do you program?

Well I know very basics of C++ and Java

---

### Post by whatthefunk on 2012-06-28
Just had a quick look through the repositories.  Theres a program called sandboxgamemaker that might be interesting for you.

---

### Post by BlinkinCat on 2012-06-28
> **whatthefunk said:**
> Just had a quick look through the repositories.  Theres a program called sandboxgamemaker that might be interesting for you.

I always thought you were a helpful guy whatthefunk - :p

---

### Post by MG&amp;TL on 2012-06-28
I've recently been experimenting with pygame and pybox2d. 2D games, it seems are shockingly simple to do with a few libraries.

3D games...you're out of luck. There's a few good libraries, but still not going to be simple to do.

---

### Post by Sarys on 2012-06-28
So what do you recomend?

---

### Post by MG&amp;TL on 2012-06-28
2D games, pygame (for graphics rendering) and pybox2d (for physics).

Of course, you could always make it truly cross-platform and go for html 5...

---

### Post by DangerOnTheRanger on 2012-06-28
For 2D games, I'd go with [PyGame]("http://pygame.org"). It's relatively easy to get up and running, and it's in the Ubuntu repos as well (sudo apt-get install pygame). A second choice for 2D games would be [pyglet]("http://pyglet.org"), which has two advantages over PyGame - namely, it can render faster (pyglet is usually the only choice for Python sh'mup), and it's pure Python (no C/C++), so making an executable is a lot easier. pyglet is installable from the Ubuntu repos via sudo apt-get install pyglet.

For 3D games, I personally use [Panda3D]("http://panda3d.org") - it's probably the most developer-friendly game engine I've seen, and it has the friendliest community of any FOSS project I've ever come across. It's not in the Ubuntu repos, unfortunately, but they do have a package archive ([http://archive.panda3d.org/](http://archive.panda3d.org/)).

Some other useful tools:
[LIST]
[*][Inkscape]("http://inkscape.org") - a powerful vector graphics editor. Install with "sudo apt-get install inkscape"
[*][Blender]("http://blender.org") - an industry-grade 3D modeler. Install with "sudo apt-get install blender"
[*][GIMP]("http://gimp.org") - a free 2D bitmap image editor. Install with "sudo apt-get install gimp" (it may be pre-installed)
[*][ASEPRITE]("http://aseprite.org") - a free sprite editor. Install with "sudo apt-get install aseprite"
[/LIST]

---

### Post by Sarys on 2012-06-29
> **DangerOnTheRanger said:**
> For 2D games, I'd go with [PyGame]("http://pygame.org"). It's relatively easy to get up and running, and it's in the Ubuntu repos as well (sudo apt-get install pygame). A second choice for 2D games would be [pyglet]("http://pyglet.org"), which has two advantages over PyGame - namely, it can render faster (pyglet is usually the only choice for Python sh'mup), and it's pure Python (no C/C++), so making an executable is a lot easier. pyglet is installable from the Ubuntu repos via sudo apt-get install pyglet.

For 3D games, I personally use [Panda3D]("http://panda3d.org") - it's probably the most developer-friendly game engine I've seen, and it has the friendliest community of any FOSS project I've ever come across. It's not in the Ubuntu repos, unfortunately, but they do have a package archive ([http://archive.panda3d.org/](http://archive.panda3d.org/)).

Some other useful tools:
[LIST]
[*][Inkscape]("http://inkscape.org") - a powerful vector graphics editor. Install with "sudo apt-get install inkscape"
[*][Blender]("http://blender.org") - an industry-grade 3D modeler. Install with "sudo apt-get install blender"
[*][GIMP]("http://gimp.org") - a free 2D bitmap image editor. Install with "sudo apt-get install gimp" (it may be pre-installed)
[*][ASEPRITE]("http://aseprite.org") - a free sprite editor. Install with "sudo apt-get install aseprite"
[/LIST]


So first I have to get one of those 3 game making programs and then one program to make graphics?

---

### Post by MG&amp;TL on 2012-06-29
> **Sarys said:**
> So first I have to get one of those 3 game making programs and then one program to make graphics?

They're not game-making programs, they're libraries to make programming easier.

---

### Post by Sarys on 2012-06-29
> **MG&TL said:**
> They're not game-making programs, they're libraries to make programming easier.

Oh. So what do I use to make the games then?

---

### Post by MG&amp;TL on 2012-06-29
> **Sarys said:**
> Oh. So what do I use to make the games then?

Erm. Code? :confused:

Not really sure what you're asking here. Things to do to make a game:

-Use a coding library to do the rendering/physics for you and make your life easier.
-Write the game logic yourself, in code. C++, Java, Python, whatever.
-Do the graphics. Inkscape/Gimp for 2D, Blender for 3d. Although of course there are others.

There are things like Game maker around that will run in wine, but there's no way it's going to come out being anything like you want it (and believe me, I've tried!).

---

### Post by Sarys on 2012-06-29
> **MG&TL said:**
> Erm. Code? :confused:

Not really sure what you're asking here. Things to do to make a game:

-Use a coding library to do the rendering/physics for you and make your life easier.
-Write the game logic yourself, in code. C++, Java, Python, whatever.
-Do the graphics. Inkscape/Gimp for 2D, Blender for 3d. Although of course there are others.

There are things like Game maker around that will run in wine, but there's no way it's going to come out being anything like you want it (and believe me, I've tried!).

Oh ok. I just don't know where to write the code xD

---

### Post by MG&amp;TL on 2012-06-29
> **Sarys said:**
> Oh ok. I just don't know where to write the code xD

Oh. :lol:

Any old source file will do, if you know a programming language, use whatever you normally use for that. I use geany/vim. But that's me.

---

### Post by Sarys on 2012-06-29
> **MG&TL said:**
> Oh. :lol:

Any old source file will do, if you know a programming language, use whatever you normally use for that. I use geany/vim. But that's me.

O...k....

---

### Post by MG&amp;TL on 2012-06-29
> **Sarys said:**
> O...k....

Also, if you want to make games, they're not easy. I'd suggest learning a language to a reasonable degree first. If you already know a bit of C++, that's a good choice.

---

### Post by Sarys on 2012-06-29
> **MG&TL said:**
> Also, if you want to make games, they're not easy. I'd suggest learning a language to a reasonable degree first. If you already know a bit of C++, that's a good choice.

Yeah so I will start with C++. Problem is that my skills are rusty (not used for a while).

---

### Post by Dlambert on 2012-06-29
I recommend the old danger deep source! We need that game to come back! [http://dangerdeep.sourceforge.net/](http://dangerdeep.sourceforge.net/)

---

### Post by Sarys on 2012-06-29
> **Dlambert said:**
> I recommend the old danger deep source! We need that game to come back! [http://dangerdeep.sourceforge.net/](http://dangerdeep.sourceforge.net/)

?

---

### Post by Brinstar on 2012-06-29
Kids these days...

1. Find any open source game that you like, there must be at least one
2. Download the source code
3. Open it up in Gedit or Geany or any programmers editor and look through the game code and look at how it's structured

From there, try to get small things working in any language you like the look of, like a moving image, a textured polygon, etc.

Languages don't matter as much as ideas. Once you have the idea and the drive, see what works, look through different open source 3D engines like Ogred3d, or the 2d ones if that's what you want to do.

---

### Post by Nytram on 2012-06-29
On Linux you're going to need to learn how to program before you can write a game. I agree with others who have suggested Python, it's quite easy to learn. You don't need to become an expert in it in order to make a game, just competent. I wrote a simple 2D platform game using pygame in a few days, but that was after I'd learnt the basics of the Python language.

This is a good tutorial for beginners to Python and programming, it's what I used:

[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_2.6]("http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_2.6")

This wiki has links to several Python tutorials including game making tutorials:

[http://wiki.python.org/moin/BeginnersGuide/NonProgrammers]("http://wiki.python.org/moin/BeginnersGuide/NonProgrammers")

---

### Post by josephmills on 2012-06-29
wait a couple months and Unity3d 4 is coming to Linux 
[http://www.youtube.com/watch?v=Bpi4J11ZE1o](http://www.youtube.com/watch?v=Bpi4J11ZE1o)

---

### Post by madjr on 2012-07-02
hmm,these should help.

remember to create simple (usually 2d) or web games first.

[http://ntt.cc/2011/01/31/66-open-source-javascript-game-engine-for-serious-developers.html](http://ntt.cc/2011/01/31/66-open-source-javascript-game-engine-for-serious-developers.html)

[https://love2d.org/](https://love2d.org/)

[http://www.sandboxgamemaker.com/](http://www.sandboxgamemaker.com/)

[http://game-editor.com/Main_Page](http://game-editor.com/Main_Page)


and pygame was mentioned which is good start too.

---

### Post by Sarys on 2012-07-03
> **Brinstar said:**
> Kids these days...

1. Find any open source game that you like, there must be at least one
2. Download the source code
3. Open it up in Gedit or Geany or any programmers editor and look through the game code and look at how it's structured

From there, try to get small things working in any language you like the look of, like a moving image, a textured polygon, etc.

Languages don't matter as much as ideas. Once you have the idea and the drive, see what works, look through different open source 3D engines like Ogred3d, or the 2d ones if that's what you want to do.

So wait. I should find open source game and do my own changes to that?

---

### Post by madjr on 2012-07-03
> **Sarys said:**
> So wait. I should find open source game and do my own changes to that?

yes you can.

You can even become a contributor, join a dev team or even fork and create your own stuff.

example:

[http://www.phoronix.com/scan.php?page=news_item&px=MTEzMTM](http://www.phoronix.com/scan.php?page=news_item&px=MTEzMTM)

however I would start with something smaller and less complicated, until your skill level increases.

---

### Post by Sarys on 2012-07-04
> **madjr said:**
> yes you can.

You can even become a contributor, join a dev team or even fork and create your own stuff.

example:

[http://www.phoronix.com/scan.php?page=news_item&px=MTEzMTM](http://www.phoronix.com/scan.php?page=news_item&px=MTEzMTM)

however I would start with something smaller and less complicated, until your skill level increases.

I see. I'm just not sure where to start.

---

### Post by fallenshadow on 2012-07-04
Take these recommended ones from above:

2D:

[https://love2d.org/](https://love2d.org/)

[http://game-editor.com/Main_Page](http://game-editor.com/Main_Page)

3D:
[http://www.sandboxgamemaker.com/](http://www.sandboxgamemaker.com/)

First decide if you want 2D or 3D... I would recommend 2D for starters.

So between Love2d and Game Editor:

**Love** 
More like programming so the better you are at programming then the more likely this will suite you. I have no experience with it but the programming doesn't look too hard.

**Game Editor** 
Allows you to do proper programming but it also has a clickable GUI for alot of things. This might suite you better for starting off.

At the end of the day its up to you. Just remember that even making 2D games can be hard.

---

### Post by madjr on 2012-07-04
> **fallenshadow said:**
> 

At the end of the day its up to you. Just remember that even making 2D games can be hard.

not really that hard, but time consuming (but any type of project does anyway).

But once you start and if you like it, then dedicating your time will just feel natural, sometimes even addicting :)

---

### Post by fallenshadow on 2012-07-04
Well yes the programming is pretty easy but what I mean't is that it is hard to keep up the effort in making something.

I started making many different games but I find it hard to keep on developing them. :)

---

### Post by Sarys on 2012-07-05
> **fallenshadow said:**
> Well yes the programming is pretty easy but what I mean't is that it is hard to keep up the effort in making something.

I started making many different games but I find it hard to keep on developing them. :)

Yeah I think I know what you mean. My problem is when I start new project (any project). It goes well in the start but then I just want to start new project and so on.

---

### Post by madjr on 2012-07-05
> **Sarys said:**
> Yeah I think I know what you mean. My problem is when I start new project (any project). It goes well in the start but then I just want to start new project and so on.

Yes, that happens to most of us, and is usually because we want to add too many features at once or work in too many different stuff. Also many times our goal is *perfection* and there's no such thing as perfect, only "good enough".

This is why I like how the **linux/open source** community usually sets fixed dates to release stuff.

They release incrementally. Is a constant evolution (I believe this is called "Agile"). Linux started very very small, now is a huge project.

If you start small (maybe something basic like tic-tac-toe), then you can never fail, abandon or quit.

Also another way I find fun to learn is by checking the tutorials and submissions from the different begineer open source competitions, i.e:

AppShowdown:
[http://www.omgubuntu.co.uk/tag/appshowdown](http://www.omgubuntu.co.uk/tag/appshowdown)

Liberated Pixel Cup:
[http://www.ubuntuvibes.com/2012/04/liberated-pixel-cup-game-making.html](http://www.ubuntuvibes.com/2012/04/liberated-pixel-cup-game-making.html)

---

### Post by Sarys on 2012-07-05
But I'm sure that it will take me years to get skilled enough to make my first game

---

### Post by madjr on 2012-07-05
> **Sarys said:**
> But I'm sure that it will take me years to get skilled enough to make my first game

years ? lol why ?

programming is usually the hardest part and that is not that difficult either.

You learn as you go.

If you're really want it and dont go for something big and complex you can have something playable in weeks or months.

Anyway I thought you mentioned you programmed before ?

---

### Post by Sarys on 2012-07-06
> **madjr said:**
> years ? lol why ?

programming is usually the hardest part and that is not that difficult either.

You learn as you go.

If you're really want it and dont go for something big and complex you can have something playable in weeks or months.

Anyway I thought you mentioned you programmed before ?

Yeah I know how C++ works. Not all though and I know Java but less than C++.
But it will take me years to learn to use C++ well enough to be good enough to make really simple game.

---

### Post by MG&amp;TL on 2012-07-06
> **Sarys said:**
> Yeah I know how C++ works. Not all though and I know Java but less than C++.
But it will take me years to learn to use C++ well enough to be good enough to make really simple game.

Not really. Study hard, play hard, and it shouldn't take years. :)

---

### Post by Sarys on 2012-07-06
> **MG&TL said:**
> Not really. Study hard, play hard, and it shouldn't take years. :)

"play hard". What do you mean?

---

### Post by Elfy on 2012-07-06
*Thread moved to **The Community Cafe**.*

Not a support request

---

### Post by fallenshadow on 2012-07-06
I don't know what he means but trust me making some simple games is not too hard. (saying that from experience)

You will end up asking for help at one stage or another but people on those forums are usually very helpful.

For example Game Editor uses C like programming. It is very easy and you can make a game just using simple variables.

On a collision with pack of bullets you could do:
```

ammo+10;
```

When left click:

```
ammo-1;
```

Those are just simple examples of course. :)

---

### Post by Sarys on 2012-07-06
> **fallenshadow said:**
> I don't know what he means but trust me making some simple games is not too hard. (saying that from experience)

You will end up asking for help at one stage or another but people on those forums are usually very helpful.

For example Game Editor uses C like programming. It is very easy and you can make a game just using simple variables.

On a collision with pack of bullets you could do:
```

ammo+10;
```When left click:

```
ammo-1;
```Those are just simple examples of course. :)

Yeah but I'm still sure I will never learn

---

### Post by Grenage on 2012-07-06
Is it easy to make a game?  Sure, it's not that difficult; look at how many 2d games are being thrashed out for Linux.  Is it easy to make a game people want to play? No.

There are no shortcuts, it's a lot of learning and hard graft.

---

### Post by MG&amp;TL on 2012-07-06
> **Sarys said:**
> "play hard". What do you mean?

Oops. Code is my playground, so by 'play hard' I meant write some fun code. By 'study hard' I mean learn the boring bits of a language. 

It really doesn't take that long, just get started and find out. :)

---

### Post by Sarys on 2012-07-06
> **MG&TL said:**
> Oops. Code is my playground, so by 'play hard' I meant write some fun code. By 'study hard' I mean learn the boring bits of a language. 

It really doesn't take that long, just get started and find out. :)

Riiiiight

---

### Post by Adrian98 on 2012-07-06
My head is spinning around because I have felt making a 3D game with high graphics for Ubuntu is somewhat little bit difficult!

---

### Post by krustenBrot on 2012-07-06
pygame +1

python is pretty simple to learn. Dig a bit aroudn on the net and you will find some examples / tutorials.

---

### Post by madjr on 2012-07-06
> **Sarys said:**
> Yeah but I'm still sure I will never learn

woa hold on right there that's not true. Don't shut yourself down already even before starting.

That sounds like pessimism, maybe you should check this quiz to see if that is getting in the way of your goals:

[http://stress.about.com/od/optimismspirituality/a/optimismquiz.htm](http://stress.about.com/od/optimismspirituality/a/optimismquiz.htm)


then if you think you're suffering from it, this should get you out of that state:

[http://www.psychologytoday.com/basics/pessimism](http://www.psychologytoday.com/basics/pessimism)
[http://psychcentral.com/blog/archives/2011/03/17/pessimism-vs-optimism/](http://psychcentral.com/blog/archives/2011/03/17/pessimism-vs-optimism/)


Anyway, if you feel you're not skilled enough right now, that doesnt mean you can't learn quickly. In this era and with so many free resources available is easier than ever to learn.

for example you can try **Alice**:

[http://www.alice.org/index.php?page=what_is_alice/what_is_alice](http://www.alice.org/index.php?page=what_is_alice/what_is_alice)

to install use 2.0 (2.2 is not needed):
[http://www.alice.org/index.php?page=downloads/download_alice](http://www.alice.org/index.php?page=downloads/download_alice)

This is used in schools and college.

So I wish back in the day we had the resources available now... back then we only had a big black/green text box, almost no help and ugly books. :p

ps. if you find some problems with alice, ask or look in their forums:
[http://www.alice.org/community/showthread.php?t=1538](http://www.alice.org/community/showthread.php?t=1538)

---

### Post by BrokenKingpin on 2012-07-06
If you know C++ look into the SDL library for graphics. If you know java, pick up a game programming book on Java (there are a ton). 

At this point you should probably just focus on increasing your programming skills in general before getting into game development.

---

### Post by Sarys on 2012-07-06
> **BrokenKingpin said:**
> If you know C++ look into the SDL library for graphics. If you know java, pick up a game programming book on Java (there are a ton). 

At this point you should probably just focus on increasing your programming skills in general before getting into game development.

I have know idea what SDL library is.

But anyway witch one I should use C++ or Java?

---

### Post by conradin on 2012-07-06
making simple games is easy. 
even 2-3D scrollers isnt too bad. 
 there is a massive leap from games like that (in abundance on Linux)
to games like halo, soul calibur, or any other typically windows & platformer games. I dont think the programming is the issue, those games could be made for Linux, but companies still haven't realized the Linux market. For an average programmer, working alone, in their spare time, creating such a game is nearly insurmountable. Additionally, for it to be truly opensource, all the content would need to be original, or from GPL, or GNU licenses. There is a serious lack of characters in that pool. Some one could do a game about Jenny Everywhere, since she is a public domain character. 
 What kind of games are we taking about? 
pls no more zombie games, its such a cop out for character development.
There is a book called "Better Game Characters by design" by Katherine isbister, which is pretty good.

---

### Post by madjr on 2012-07-06
> **Sarys said:**
> I have know idea what SDL library is.

But anyway witch one I should use C++ or Java?

if you're going to try Alice then probably use java, else if you're going another route which ever you like is ok, even python.

but is not so much about learning the language (they're all somewhat similar and is usually easy to jump from one to another) but is more about the programming concepts itself to get stuff done.

things like OOP:

[http://searchsoa.techtarget.com/definition/object-oriented-programming](http://searchsoa.techtarget.com/definition/object-oriented-programming)

[http://www.aonaware.com/OOP1.htm](http://www.aonaware.com/OOP1.htm)

And like I mentioned earlier Alice is good way to practice that visually.

[http://blog.alice.org/?p=262](http://blog.alice.org/?p=262)

and there is also **Scratch visual programming** (which I believe is even simpler).

[http://scratch.mit.edu/](http://scratch.mit.edu/)
[http://info.scratch.mit.edu/Scratch_1.4_Download](http://info.scratch.mit.edu/Scratch_1.4_Download)

scratch vs alice:
[http://blog.alice.org/?p=102](http://blog.alice.org/?p=102)

---

### Post by nec207 on 2012-07-06
> **Sarys said:**
> Hello! I'd like to know few programs/ways of making games for Ubuntu/linux.
So if someone know easy way for making games with Ubuntu please let me know. Thank you
 
2D Games like Illusion of Gaia , Final Fantasy ,Zelda take many years to make . And 3D games will take longer .
 
Games like Illusion of Gaia and older Final Fantasy and Zelda will take year or more to make with 30 people or more working on it. And new 3D games like Elder Scrolls V: Skyrim ,Witcher , Oblivion , Witcher 2 and Skyrim will take 3 to 5 years to make with 100 to 200 people working on it.

---

### Post by madjr on 2012-07-06
> **nec207 said:**
> 2D Games like Illusion of Gaia , Final Fantasy ,Zelda take many years to make . And 3D games will take longer .
 
Games like Illusion of Gaia and older Final Fantasy and Zelda will take year or more to make with 30 people or more working on it. And new 3D games like Elder Scrolls V: Skyrim ,Witcher , Oblivion , Witcher 2 and Skyrim will take 3 to 5 years to make with 100 to 200 people working on it.

maybe you haven't seen that the almost none of the indie kickstarters have a team of 30 people (like the big 3d games), but a handful, in fact a lot of open source projects dont even have more than 5 partial time devs...

**Gimp** for example has only 2 to 3 developers.

and countless only have one main developer.

most indies too, like **exploding rabbit** and super retro squad:
[http://www.kickstarter.com/projects/explodingrabbit/super-retro-squad](http://www.kickstarter.com/projects/explodingrabbit/super-retro-squad)
[http://www.explodingrabbit.com/](http://www.explodingrabbit.com/)

:)

---

### Post by nec207 on 2012-07-06
> **madjr said:**
> maybe you haven't seen that the almost none of the indie kickstarters have a team of 30 people, but a handful (like the big 3d games), in fact a lot of open source projects dont even have more than 5 partial time devs...
 
**Gimp** for example has only 2 to 3 developers.
 
and countless only have one main developer.
 
Ya but OP was talking about making 2D games but games like Illusion of Gaia or zelda link to the past there is a lot in game with story and graphics.
 
These games are not easy to make.I say with 30 people may be you can do this in year or two the game like zelda link to the past .
 
 
[IMG]http://farm1.staticflickr.com/54/114033730_706b5ac53d.jpg[/IMG]

---

### Post by madjr on 2012-07-06
> **nec207 said:**
> Ya but OP was talking about making 2D games but games like Illusion of Gaia or zelda link to the past there is a lot in game with story and graphics.
 
These games are not easy to make.I say with 30 people may be you can do this in year or two the game like zelda link to the past .
 


30 people ? you must be high...

**Tomes of Mephistopheles** is 3d and only has 2 devs:
[http://tom.kot-in-action.com/](http://tom.kot-in-action.com/)

and they made steel storm some time ago:
[http://one.steel-storm.com/](http://one.steel-storm.com/)

and most indies only have 1 to 3 devs, and if they are on kickstarter is just for help for the living expenses, else they can't dedicate full time to dev and have to look for a job. But if you're still living at home, you probably don't have that problem and can dedicate more time to your projects than a older person with a family to sustain would.

edit: interviews for steel storm:

[http://www.gamingonlinux.com/index.php?threads/kot-in-action-interview.590/](http://www.gamingonlinux.com/index.php?threads/kot-in-action-interview.590/)
[http://www.joystiq.com/2011/10/16/the-joystiq-indie-pitch-steel-storm/](http://www.joystiq.com/2011/10/16/the-joystiq-indie-pitch-steel-storm/)

---

### Post by nec207 on 2012-07-06
> **madjr said:**
> 30 people ? you must be high...
 
**Tomes of Mephistopheles** is 3d and only has 2 devs:
[http://tom.kot-in-action.com/](http://tom.kot-in-action.com/)
 

 
I will like to see 2 or 3 people make game like **Tomes of Mephistopheles** in one year or 1 or 2 people make game like **zelda link to the past** in 6 month or one year.
 
That I don't see happing .

---

### Post by akku853 on 2012-07-06
Can any one tell me how to add a new post....
m **Confused**):P

---

### Post by madjr on 2012-07-06
> **nec207 said:**
> I will like to see 2 or 3 people make game like **Tomes of Mephistopheles** in one year or 1 or 2 people make game like **zelda link to the past** in 6 month or one year.
 
That I don't see happing .

Well, that's the kind of attitude that gets no where in life.

what wont happen is you ever getting 30 people to do work free for you.


at this stage he doesnt need some type of multi million dollar commercial project, he just needs to learn the basics and get simple stuff done, then he can go from there and maybe even partner with friends.

that is how everyone starts.

and this is how open source in general started. Everything you see here started with just one developer, one idea.


> Can any one tell me how to add a new post....
m Confused

what you want is to **create a new thread**. the button is usually at the top of the desired forum/sub-forum.

---

### Post by Sarys on 2012-07-09
Umm...who was talking about making games like Legend of Zelda??? I know I didn't. I just want to make game that doesn't mean I want to make big and epic game as my first game. I want to make simple and fun games at first and do bigger projects when I'm ready to do them.

EDIT: But first there's been so many programs so tell me the once I need to start making 2d games.

---

### Post by madjr on 2012-07-09
> **Sarys said:**
> Umm...who was talking about making games like Legend of Zelda??? I know I didn't. I just want to make game that doesn't mean I want to make big and epic game as my first game. I want to make simple and fun games at first and do bigger projects when I'm ready to do them.

EDIT: But first there's been so many programs so tell me the once I need to start making 2d games.


see if "**scratch**" is what you want:

[http://vimeo.com/29457909](http://vimeo.com/29457909)

[http://info.scratch.mit.edu/Support/Get_Started](http://info.scratch.mit.edu/Support/Get_Started)

---

### Post by Sarys on 2012-07-09
> **madjr said:**
> see if "**scratch**" is what you want:

I think you know better than I is that good enough

---

### Post by fatality_uk on 2012-07-09
The short answer is no. I get the feeling you are looking for a drag/drop gaming kit that will allow you to put together a game?

A good start to understand basic gaming programming might be [http://html5games.com/](http://html5games.com/)

There are some great innovative games on here and some of the source is easily readable

---

### Post by madjr on 2012-07-09
> **Sarys said:**
> I think you know better than I is that good enough

We can't decide for you, only you know what is your current skill and commitment level to your own projects.

I believe there is more than enough advise in this thread to make a great decision.

anyway what ever you do, don't just get used to most of those limited commercial "drag and drop editor" advertised on the net. Usually they're very limited, they try to lock you in, you may become heavily dependent and in the end you **won't understand** what really happens or how to really create a game (in other words you'll be at square one).

On the other hand **"scratch" and "alice"** are real learning tools used in college, not only allow drag and drop but also really teach you to program/code like a real independent **developer** would.

good luck in your journey ! :D

---

### Post by madjr on 2012-07-09
> **fatality_uk said:**
> The short answer is no. I get the feeling you are looking for a drag/drop gaming kit that will allow you to put together a game?

A good start to understand basic gaming programming might be [http://html5games.com/](http://html5games.com/)

There are some great innovative games on here and some of the source is easily readable

hmtl5 is pretty simple too, but a little more advanced and won't teach him that easily the programming **logic** in games as with scratch.

anyway here is a simple html5 for anyone that wants it.
[http://www.lostdecadegames.com/how-to-make-a-simple-html5-canvas-game/](http://www.lostdecadegames.com/how-to-make-a-simple-html5-canvas-game/)

---

### Post by fatality_uk on 2012-07-09
> **madjr said:**
> hmtl5 is pretty simple too, but a little more advanced and won't teach him that easily the programming **logic** in games as with scratch.

anyway here is a simple html5 for anyone that wants it.
[http://www.lostdecadegames.com/how-to-make-a-simple-html5-canvas-game/](http://www.lostdecadegames.com/how-to-make-a-simple-html5-canvas-game/)

But with Google Chrome, notepad and a few hours learning time, the OP has a complete games dev setup with debugger!

HTML5 games will also introduce anyone to some important 2D gaming concepts (sprites, animation, scoring, story boarding, game position/completion % etc)

---

### Post by JDShu on 2012-07-09
> **Sarys said:**
> But I'm sure that it will take me years to get skilled enough to make my first game

FWIW when I first started to seriously learn to write games, I wrote a tetris clone in a week, and a battle city clone in a month. Aim for something small like tetris first and ask lots of questions. You can use the programming talk forum here, or ask people on irc.

---

### Post by Sarys on 2012-07-10
Ok thanks everyone I guess I just have to test different programs and different ways to find the one that suits my needs best.

---

### Post by Mars11 on 2012-07-10
I'll just put in my 2 cents. You sound just like I did a year or two ago. Here's what I've done:
[LIST]
[*]Look at programs done by other people, then edit them to make them do what you want.
[*]Start writing your own simple programs.
[*]Become skilled and write your own, more complicated programs.
[*]Start experimenting with games.
[/LIST]
Don't think this is an easy road, it takes time and effort on your part.

---

### Post by Sarys on 2012-07-10
> **Mars11 said:**
> I'll just put in my 2 cents. You sound just like I did a year or two ago. Here's what I've done:
[LIST]
[*]Look at programs done by other people, then edit them to make them do what you want.
[*]Start writing your own simple programs.
[*]Become skilled and write your own, more complicated programs.
[*]Start experimenting with games.
[/LIST]
Don't think this is an easy road, it takes time and effort on your part.

Problem is that I don't know what and how to change already done programs. And do my own program? I have no idea what program to do.

---

### Post by Mars11 on 2012-07-10
> **Sarys said:**
> Problem is that I don't know what and how to change already done programs. And do my own program? I have no idea what program to do.
You have to take the source and import it to an IDE (Integrated Developing Environment) like Eclipse and just edit the code then compile and run it. If you don't know how to do that, Google and your ability to read are very helpful. If you don't know how to do something, or how something works, Google it. Chances are somebody else has asked the exact same question.
Edit: And stop thinking so far ahead, just think about now and learning how to edit a program and how they work. While you're doing that write down any ideas that come to you. After you think you're pretty good at changing someone else's work, then start on your own. As I said, this takes time, you can't expect to do this all in one night. :P

---

### Post by madjr on 2012-07-10
> **Mars11 said:**
> You have to take the source and import it to an IDE (Integrated Developing Environment) like Eclipse and just edit the code then compile and run it. If you don't know how to do that, Google and your ability to read are very helpful. If you don't know how to do something, or how something works, Google it. Chances are somebody else has asked the exact same question.
Edit: And stop thinking so far ahead, just think about now and learning how to edit a program and how they work. While you're doing that write down any ideas that come to you. After you think you're pretty good at changing someone else's work, then start on your own. As I said, this takes time, you can't expect to do this all in one night. :P

yes, that's more advance then his skill level right now.

It's called modding (modifying).

But he should focus on the basics first, then when ready he can mod other people's work if he likes.

but he should learn first to create something small totally from scratch, which is the only real way to learn the programming steps and logic.

am teaching my son to program a game and this is what I use:


[http://blogs.kqed.org/mindshift/2011/05/5-tools-to-introduce-programming-to-kids/](http://blogs.kqed.org/mindshift/2011/05/5-tools-to-introduce-programming-to-kids/)

You have to start from **step one, not step 5**. then Once he does that he can do all the other stuff, else he'll just be confused.

---

### Post by Mars11 on 2012-07-10
> **madjr said:**
> yes, that's more advance then his skill level right now.

It's called modding (modifying).

But he should focus on the basics first, then when ready he can mod other people's work if he likes.

but he should learn first to create something small totally from scratch, which is the only real way to learn the programming steps and logic.

am teaching my son to program a game and this is what I use:


[http://blogs.kqed.org/mindshift/2011/05/5-tools-to-introduce-programming-to-kids/](http://blogs.kqed.org/mindshift/2011/05/5-tools-to-introduce-programming-to-kids/)

You have to start from **step one, not step 5**. then Once he does that he can do all the other stuff, else he'll just be confused.
Oh, I see. Well I guess I learned how to code very informally then. That might explain why it was so difficult, actually. :P I'll just leave and let you guys teach him.

---

### Post by fatality_uk on 2012-07-10
You don't have to start by coding a replacement for Quake! If I can make a suggestion. Try coding a simple game of tic-tac-toe. Focus not on the graphics, after all, there two symbols and not much else but think of the gameplay. Try to write a single player and human vs PC version. This will make you think about strategy etc.

---

### Post by madjr on 2012-07-10
> **Mars11 said:**
> Oh, I see. Well I guess I learned how to code very informally then. That might explain why it was so difficult, actually. :P I'll just leave and let you guys teach him.

I also started very informally many years ago, but only after trying to teach my kid was that I discovered all the gaps I had (usually lots of basic stuff).

So like the old saying "*you only really know something if you can teach it to someone else*"

---

### Post by Sarys on 2012-07-11
> **fatality_uk said:**
> You don't have to start by coding a replacement for Quake! If I can make a suggestion. Try coding a simple game of tic-tac-toe. Focus not on the graphics, after all, there two symbols and not much else but think of the gameplay. Try to write a single player and human vs PC version. This will make you think about strategy etc.

Only problem with tic-tac-toe is that I most likely just copy code from internet and never understand what things do. But I've done sine minor modding. I modded Hearts of Iron game data (it was easy since it was text file)

---

### Post by Sarys on 2012-07-19
(sorry for not using edit it didn't give me the option)

Ok so I still need program to make games with (free) I guess I will check srcatch but I fear it's not what I'm looking for.

---

