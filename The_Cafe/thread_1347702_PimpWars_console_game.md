---
title: "PimpWars console game"
date: 2009-12-06
forum: The Cafe
---

### Post by karimruan on 2009-12-06
I am attaching a .py file of a game I am working on. If you would like to work on it with me, download it, make your additions (Not to advanced, I am still a beginner) and add your name to the @authors line (line 5), and upload it back to this forum. I think it would be fun to have a community made game circulating the forums. The goal is to create a dopewars like game, only dealing with pimps.

I think you get the idea. 

the only rule i have is that you document all code well! That way everybody knows what you are getting at with your code. 

Please see the attached .py file.

---

### Post by chris200x9 on 2009-12-06
I like the idea, but disagree with the content. Also I find python confusing, I don't think I'll be able to help.

---

### Post by JDShu on 2009-12-06
> **chris200x9 said:**
> I like the idea, but disagree with the content. Also I find python confusing, I don't think I'll be able to help.

Agreed, I think the game topic is terrible, but I like the idea of a community game.

---

### Post by karimruan on 2009-12-06
SO, you don't mind simulating selling cocaine, heroin, and ludes, but you strongly object to selling women. I actually agree with you in that sense, a little. but, this is a game, and will eventually include all activities that are seen on the streets, if those who work on it and i take that direction. Python is a little confusing at first, but it is pretty much the new basic. 

but, this is not the place to be discussion langs other than the pyhton related to the game. If anyone wants to work on it, and disagrees with the pimping idea, let me know if you have an alternative object besides hoes to sell and buy.

---

### Post by soni1770 on 2009-12-06
if i didn't take 100% of her money....

how would i pay 100% of her bail.:popcorn:

---

### Post by karimruan on 2009-12-06
okay, how about a dopewars -like then. you sell drugs, fight NPC"s, and the like. I don't know how to make a multiplayer game, so, if it goes that direction, someone else will have to write the code.

BUT, we need ideas of how to make it different, better, and such.

The pimp idea is scratched. ANY New ideas?

---

### Post by karimruan on 2009-12-06
Here is the revised code. Changed all hoe variables and globals to dealers. Still need to make it so that once you give the 'work dealers' command, the dealers work in the background.

It would be nice to have it so that they work in specific areas, and if you were able to specify 'work 5 dealers cleveland' to have 5 dealers sell for you in cleveland.

Need more to do though. Anyone and everyone is open to edit this code. 

New working title is streetwars.

Let's get this game going!

EDIT: Getting this error but have no idea what it means:
```

 File "streetwars.py", line 327, in clev_income
    work_dealers()
  File "streetwars.py", line 322, in work_dealers
    income = random.randrange(5, 9)
  File "/usr/lib/python2.6/random.py", line 171, in randrange
    istart = int(start)
RuntimeError: maximum recursion depth exceeded while calling a Python object
mat@mat-laptop:~$

```

here is the code i think has the problem.

[code]

def work_dealers():
	global cash
	income = random.randint(self, 1, 9)
	cash = cash + income
	work_dealers()
[code]

---

### Post by Ylon on 2009-12-06
It's fine to deal with crime subjects. By sure deal a game having crime with subject could be ethically disputable. But using your freedom of creativity is also very important.

I think that if some one keep an eye (and avoid) this:
1. libel real live people 
2. apology of crime (basically, in moral of the story end simply say: the crime (any kind) is right)
3. show inappropriate continents to inappropriate audience (ie: pornography to children)


Anyway, putting a "good willing" warn (ie: racing game burn-out like with msg like "don't drink and drive/use safebelt etc.")when game deal with hard subjects is, also, a good idea.


On your game:

Nowdays is everything made with a GUI, text games are very hardly used...you can have two choice.
Try to emulate a gui with ascii characters (very quick gaming.. very good for "you were hit for xx point"), or a simple text mode, much better suited to show off your skills with long narrative descriptions hiding in the text, puzzles and riddles to solve.








Anyway, what about Blender Game Engine? it also extend in python :D

---

### Post by karimruan on 2009-12-06
i am not yet ready for blender, I basically can only make console stuff right now, mostly using funtions and if...else statements. Which is why i want to collab, so i can learn from others. i would love to be able to make an ascii gui in python, similar to the one in Vi. If anyone could teach me (or point me to the resources) that would be great!

---

### Post by Marvin666 on 2009-12-06
Zork was alright, and it was text based.
-It is pitch black. You are likely to be eaten by a grue.

---

### Post by Shpongle on 2009-12-06
great idea for a community game , i dont know python , but if anyone wants to start a C++ / C or java game i could help a bit. theres lots of good coders on here theres no reason we cant help make a great prog or game and get artwork or characters designed by the community , i propose a brainstorming thread to generate project ideas , then a separate thread for the chosen topic/s . we could make this work  . .  and its one of the best ways we can give back and learn at the same time!!! ,

---

### Post by Ylon on 2009-12-06
> **karimruan said:**
> i am not yet ready for blender, I basically can only make console stuff right now, mostly using funtions and if...else statements.
Belive me, is much easy that you can think, anyway.. if you're curious about blender GE..take 4 min. to watch this video: [http://www.youtube.com/watch?v=SZNstSGcDVA](http://www.youtube.com/watch?v=SZNstSGcDVA) it explain the easiest thing to do in Blender.



> **karimruan said:**
> Which is why i want to collab, so i can learn from others. i would love to be able to make an ascii gui in python, similar to the one in Vi. If anyone could teach me (or point me to the resources) that would be great!

Unlucky, I am not a programmer.. my last experience ends on QBasic lol.

Anyway, remember the main rule: when you stuck somewhere, try to step back to simplify things. Things too complex hardly evolve.

Try to set (first) a basic engine for your game (move, talk, buy), then add the contents (beat the thug, accept a quest...). If you mix engine and contents it will be:
1. more difficult for you to fix things
2. other join to help.

Also add some comment to explain the function (what do you suppose to do with that code's portion) is very important.

---

### Post by Starlight on 2009-12-06
I think a text adventure game would be interesting, so that different people would be able to add something unique to the game's world and storyline, and the game would grow that way into something totally unpredictable :)

---

### Post by karimruan on 2009-12-06
> **Starlight said:**
> I think a text adventure game would be interesting, so that different people would be able to add something unique to the game's world and storyline, and the game would grow that way into something totally unpredictable :)

Exactly! THAT is what I want! Only, I would like to do it in python because that is all I Know, I know a little sdl basic, and am learning kbasic, but other than that, nothing. Java seems to complicated for me at this time. I still need to master python before I try c/c++ or java!

If anyone agrees with starlight and I, and can code (even a little bit), please download streetwars.py and add your own personal touch to it. do whatever, just don't completely rewrite it, add to it. Also, add your name to the @authors section.

read the source and you may see something you could do better, or something you may want to add. Do it. Let's get this going! No need to plan, as long as it ends in a working text adventure, go ahead! Just make sure the code you write is complete, and if you don't complete it, use comments to document where you are going with your addition!

---

