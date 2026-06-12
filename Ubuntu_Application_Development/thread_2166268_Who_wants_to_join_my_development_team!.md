---
title: "Who wants to join my development team!?"
date: 2013-08-08
forum: Ubuntu Application Development
---

### Post by amir2 on 2013-08-08
I will get right too it. The plan is to make a open source app for game development and running. 
1) file type
    A) use a custom file type such as .game
    B) have every thing the game needs within the .game file including save files
    C) when the game is ran, the builder compiles the .game(like java does) runs it, then deletes the compiled program at exit(making it completely cross platform) 
2) the runner
    A) basically like java run time. Hides everything from the user, and gets any platform specific resources. 
3) the reason for not just using java
    A) to make what is basically a new programming languages 
    B) very simplified coding
    C) hands screen re-sizing, getting controller, ect

4) the builder/developer tools/SDK
     A) to start with focus on one type of game(top down or platformer)
     B) split the coding in to 3 main parts; map, entities, and tabs
5) map 
     A) I was thinking data field style maps
     B) let the game maker see changes on the map in real time
     C) when making a tile(or sprite call it what you want), have a list of check boxes with possible features. 
     D) handle any dynamic tiles automatically
     F)  have a tile library in the SKD, with both default tiles and custom/downloaded ones
6) entities(this is the most important feature)
      A) an entity is completely self contained
      B) after being created and placed on a tab, a entity will move, attack, ect on its own. 
      C) entities can be linked(this is a feature I want to make) to data such as controller input or map when created
      D) again there will be a libray 
7) tabs
      A) tabs are the first layer( the order is tab>map>entity)
      B) tabs can be display or background processes like saving 
      C) the active tab has display(active and running are different!)
      D) pausing a tab will pause all the maps in it which will pause all the entities in each map(each tab can have a active map which could be used like rooms)
      F)  what to display is saved in the map such as liking it to a entity's location



Again this is going to open source so all ideas are welcome, and I am looking to make a development team. Also please ask if you have any questions as I don't feel like proof reading this long of a post.

---

### Post by bsamim on 2013-08-11
Wow lot's of numbers and letters and I still don't know what you are trying to accomplish :).  I don't know if you can have a one size fits all architecture for game development.  Speed is of the essence and usually basic computer science patterns are applied as needed divide and couqueor, fast data structures etc.  very specific to the applications needs. I wish you luck though if you have some open source frame work you want to review I would be happy to.

---

### Post by tsunalugi on 2013-08-15
I would personally be interested in coding a custom game template for Linux users. I have some experience coding for game servers like OpenSim & NeverWinterNights. I am perhaps what you would refer to as an intermediate level coder, or scripter. I have done a lot of altering existing game programs & developing quite a lot within 3d environments. Feel free to IM me on this forum about your project & projection plan, etc. :)

Salut!

---

### Post by amir2 on 2013-08-16
Glad to have you. Now that makes two! 

I am willing to bet a lot more people will join in once we get it rolling. I think we should avoid 3D as those take large paid teams years to make. I should warn you(and anyone else that joins) that my code is a little hard to follow as I use little to no OOP(struct's are about it); I will try to play nice. Also all my graphics work as been within the .net network so I am still leaning sdl. 

The project will start on Monday the 26th. 


P.S. It is not that I dislike the layout of OOP; it is that I don't like how much ram it waste.

---

### Post by bsamim on 2013-08-17
so.. what's the project plan?

---

### Post by amir2 on 2013-08-17
First we are going to do the most haves; we will split it up into classes. For example, a class to handle all file reading and writing, a class to handle all our compiling(my best idea is to always compile over the last one), SDL simplified, ect
 
I also plan on going though the gaming forums to see what format people want. The reason I am putting it off is because this is a very bad week for me.

---

### Post by tsunalugi on 2013-08-19
I'm kinda curious what the design spec idea is. I would be interested in doing a number of various projects. A lot of gaming development teams will work (especially open source projects) trying to emulate an established game format. The OpenSim gaming development team is attempting to reproduce what SecondLife offers, with added functionality. As a result, it's really easy to coordinate development projects on that team. If you were looking for suggestions, I would suggest making an open source version of NWN2 (NeverWinter Nights 2), as it supplies great 3d graphics & a single server supports a vast virtual space. The gaming would be d20 style, which I would think would have a great appeal to people whom wanted to build an area with our custom toolset. Just food for thought... The main point of the suggestion is making a platform that could be modified by the user. An area toolset would be vital for developing a platform which gave infinite design potential & could be easily carried into the next generation of computer graphics, whatever that may be.

---

### Post by amir2 on 2013-08-19
That is a good idea; it would be bad if nobody knew what the goal was after we start coding. Although, we have to be careful what game we base it off of. I think NWN2 would not work very good; MMORGP's  require one LONG game to work. I think we should base it off of Fire Emblem(the gba one). This is more along the way of a game engine and not a utility, but still seems like a better idea. 

 But this is a team project, so lets make sure everyone agrees before moving forward.
 

Who votes for Fire Emblem with costume maps, classes, items, and possible multiplier(if you don't know what fire emblem is, it is the granddaddy of all RPG's).
 
Who wants Pokemon with costume maps, Pokemon, moves, items, and possible multiplier(if you don't know what Pokemon is than all hope is lost). 

Who has a different game(2D only!) that they think we should base it off of.

---

### Post by amir2 on 2013-08-21
It looks like I won't have time to do this project after all; I was hoping things would blow over, but instead they got worse...

---

