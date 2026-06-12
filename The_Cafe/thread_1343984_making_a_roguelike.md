---
title: "making a roguelike"
date: 2009-12-02
forum: The Cafe
---

### Post by karimruan on 2009-12-02
I have been trying for a week now, but can't really get it right. Is there anyone who can tell me what i need to make a SIMPLE roguelike in python, or provide me to a roguelike (open source) whose code I can learn from. I don't want to have to fix the code, i want to just work. I tried libtcod-1.4.1 but i don't know how to install it, I know it has to go into /usr/local/lib/python2.6/dist-packages. Is there another well documented way to write a roguelike? 

If anyone wants to help me with this project so i can learn, that would be great. I have great ideas! Just don't know how to implement them!

---

### Post by MaxIBoy on 2009-12-02
> **karimruan said:**
> I have been trying for a week now, but can't really get it right. Is there anyone who can tell me what i need to make a SIMPLE roguelike in python, or provide me to a roguelike (open source) whose code I can learn from. I don't want to have to fix the code, i want to just work. I tried libtcod-1.4.1 but i don't know how to install it, I know it has to go into /usr/local/lib/python2.6/dist-packages. Is there another well documented way to write a roguelike? 

If anyone wants to help me with this project so i can learn, that would be great. I have great ideas! Just don't know how to implement them!Use [curses]("http://www.amk.ca/python/howto/curses/") for the display.

Your basic playing field can be a 2D array of single-character strings, or just manipulate a raw curses pad. Then another array with your monsters in it. The monsters/items need stats like health and stuff, create a class for a generic "entity" and have child class for each type. Each child class should define a "think" function that runs every frame. 

You can also clip against the displayed area, so items are inactive unless you can see them on the screen. With curses, you get scrolling displays for free with pads.

---

