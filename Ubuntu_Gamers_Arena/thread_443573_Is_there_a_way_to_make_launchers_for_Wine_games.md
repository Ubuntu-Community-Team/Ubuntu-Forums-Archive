---
title: "Is there a way to make launchers for Wine games?"
date: 2007-05-14
forum: Ubuntu Gamers Arena
---

### Post by jmagick07 on 2007-05-14
So I don't have to open "Wine File" each time I want to play a Windows game.  How would I go about making a launcher on the Desktop for the games?  I couldn't figure it out, since it doesn't seem to be the same way you normally create a launcher. :confused:

---

### Post by PhatStreet on 2007-05-14
You can set the command in the manner of "wine /home/user/Games/GridWars2/GridWars.exe" for whatever game you have, pointed to where your game is, obviously. I think you have to use a backslash before a space in a directory/filename though.

---

### Post by dannyboy79 on 2007-05-14
> **PhatStreet said:**
> You can set the command in the manner of "wine /home/user/Games/GridWars2/GridWars.exe" for whatever game you have, pointed to where your game is, obviously. I think you have to use a backslash before a space in a directory/filename though.

correct, I am just commenting since you kind of made a statement and weren't sure about it. the first part of your statement is dean on! you can just create a launcher on your desktop or a menu item within the menu editor under ssytem preferences. when you enter the location of a anything or do anything in linux which has a space, sometimes quotes work around the name, like in a shell, but sometime you can use the backslash, so it would be like this

```
wine /home/username/.wine/drive_c/Program\ Files/Full\ Tilt\ Poker\FullTiltPoker.exe
```

notice that Program Files directory has a space in it and the folder within that which is Full Tilt Poker has spaces as well. then if your programs name has spaces, I think you may then need to use the quotes like this

```
wine /home/username/.wine/drive_c/Program\ Files/Full\ Tilt\ Poker\"Full Tilt Poker.exe"
```

or is it

```
wine "/home/username/.wine/drive_c/Program\ Files/Full\ Tilt\ Poker\Full Tilt Poker.exe"
```

anyway, i think you get it with one of these. he he

---

### Post by jmagick07 on 2007-05-14
Ok I'll try that then reply with my results :)

---

### Post by Lord Illidan on 2007-05-14
> **jmagick07 said:**
> Well I tried

```
wine /home/username/.wine/drive_c/SIERRA/Hoyle\ Board\ Games\ 4\"Hoyle Board Games 4.exe"
```and


Tried removing the double quotes from the name of the game, and treating it as a normal part of the path? Don't forget to remove the backspaces and stuff.

Personally, what I would do is use tab completion in a graphical terminal to give me the full path, then copy and paste it.

---

### Post by jmagick07 on 2007-05-14
I got it to respond when I did this

```
wine "/home/eric/.wine/drive_c/SIERRA\Hoyle Board Games 4\Hoyle Board Games.exe"
```


However, I just get a black screen and can't do anything, I have to restart my computer.

I guess for right now, I'll just stick with using the "Wine File" thing.

---

### Post by Nehvrook on 2007-05-14
> **jmagick07 said:**
> I got it to respond when I did this

```
wine "/home/eric/.wine/drive_c/SIERRA\Hoyle Board Games 4\Hoyle Board Games.exe"
```


However, I just get a black screen and can't do anything, I have to restart my computer.

I guess for right now, I'll just stick with using the "Wine File" thing.


Try changing that to

 ```
 wine /home/eric/.wine/drive_c/SIERRA/Hoyle\ Board\ Games\ 4/Hoyle\ Board\ Games.exe 
```

 and it should run I think. You can also go to the wine folder and manually re-name the files and folders and remove the spaces, then there's none of this backslash malarky

---

### Post by Clay_Banger on 2007-05-14
> **Nehvrook said:**
> You can also go to the wine folder and manually re-name the files and folders and remove the spaces, then there's none of this backslash malarkyAre you sure thats safe? and that it isn't going to break the game cos the path has changed? I think you are better off learning how to deal with the backslashes, then risking breaking the game/app temporarily.

---

### Post by dannyboy79 on 2007-05-14
> **Clay_Banger said:**
> Are you sure thats safe? and that it isn't going to break the game cos the path has changed? I think you are better off learning how to deal with the backslashes, then risking breaking the game/app temporarily.
i did this to full tile poker. it's not like anything is calling for it besides your wine command. the exe is the highest point, within that callls for the programs and other filenames. so it would be bad if you renamed a .dll library that .exe called for but it's ok to rename the .exe. At least it didn't hurt full tilit poker in my example.

also, when you say you get a black screen, do you have an understanding or have read somewhere that this .exe is suppose to work in linux wine? It's not like ALL .exe will work in wine.  chances are that if the command you're trying does do something, like bring up a screen, it's calling upon wine but it just doesn't work OR you need to find out what options if any, wine is using when you try it thru the wine file thing. you can find this out by using the wine file thing, then if your game works, then minimze that and type in 
```
ps aux
```
in a terminal and see what it says about the wine process running, then just use the same options within the launcher you're trying to create. good luck.

---

### Post by Nehvrook on 2007-05-15
> **Clay_Banger said:**
> Are you sure thats safe? and that it isn't going to break the game cos the path has changed? I think you are better off learning how to deal with the backslashes, then risking breaking the game/app temporarily.

Hmm, I don't think so. Of course I'm no expert and it might break some things. But re-naming everything back to how it was before would fix it again so it's worth giving it a go I figured.

EDIT:
Okay I tested it out to make sure. I had starcraft installed to /home/lee/.wine/drive_c/Program Files/Starcraft/StarCraft.exe and I changed it to /home/lee/.wine/drive_c/Program Files/Star craft/Star Craft.exe
Put the two nescessary backslashes in when I ran it in the terminal and it still worked. So just changing the name of directories and .exe's doesn't seem to break it.
I rekon if you changed the names of files the .exe will need you might have problems. But just changing the path to the exe or the exe it's self should be relatively trouble free.
So I stand by my suggestion of removing the spaces to give yourself an easier time :P

---

