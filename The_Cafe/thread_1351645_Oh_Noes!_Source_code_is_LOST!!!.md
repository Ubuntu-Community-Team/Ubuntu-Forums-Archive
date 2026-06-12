---
title: "Oh Noes! Source code is LOST!!!"
date: 2009-12-10
forum: The Cafe
---

### Post by user1397 on 2009-12-10
*EDIT: Source code found in 'more' pristine form than the one originally found through this thread, I've attached it as a zip.

---

### Post by user1397 on 2009-12-11
:(

---

### Post by Bachstelze on 2009-12-11
I eated it.

---

### Post by FuturePilot on 2009-12-11
> **Bachstelze said:**
> I eated it.

How was it? Got any left?

---

### Post by Giant Speck on 2009-12-11
I accidentally the whole thing.

---

### Post by Bölvaður on 2009-12-11
> **Giant Speck said:**
> I accidentally the whole thing.

is that supposed to actually mean anything?

---

### Post by Bachstelze on 2009-12-11
> **Bölvaður said:**
> is that supposed to actually mean anything?

To the enlightened, it does.

---

### Post by alphaniner on 2009-12-11
> **Bölvaður said:**
> is that supposed to actually mean anything?

[lmgtfy]("http://lmgtfy.com/?q=i+accidentally+the+whole+thing+meme")

---

### Post by Giant Speck on 2009-12-11
> **Bölvaður said:**
> is that supposed to actually mean anything?

Yes.  I accidentally the entire source code.

How is that difficult to understand?

---

### Post by user1397 on 2009-12-11
> **Bölvaður said:**
> is that supposed to actually mean anything?you just have to imagine the word 'ate' or another verb in there so that it becomes sortof a pun.

But anyway, getting back to the point here...anyone had any luck searching?

---

### Post by Bölvaður on 2009-12-11
-.- don't tell me you are one of those that was trying to accidentallify wikipedia?

done by deleting the verb coming after "accidentally" from every page in wikipedia.

---

### Post by murderslastcrow on 2009-12-11
:\ Noppz. Would be best to contact the author of the software.

---

### Post by user1397 on 2009-12-11
> **Bölvaður said:**
> -.- don't tell me you are one of those that was trying to accidentallify wikipedia?

done by deleting the verb coming after "accidentally" from every page in wikipedia.
me? definitely not, I only learned about the term about 5 minutes ago via google.

---

### Post by user1397 on 2009-12-11
> **murderslastcrow said:**
> :\ Noppz. Would be best to contact the author of the software.that would be ideal, if I could find his contact info ](*,)

---

### Post by user1397 on 2010-01-12
So would anyone want to try to re-create this game using python and maybe glade/wxpython (I don't know much about python) just as a fun side-project?

2 benefits to this:

One, it is useful for studying python/python-gui programming (and even for converting programs from one language to another).  I know I would be looking at the source code a lot.

Two, a python version would be cleaner and sleeker I presume :)

---

### Post by cammin on 2010-01-12
[http://read.pudn.com/downloads62/sourcecode/java/applet/game/217456/wcss/WorldCupSoccerSlime.java__.htm](http://read.pudn.com/downloads62/sourcecode/java/applet/game/217456/wcss/WorldCupSoccerSlime.java__.htm)

---

### Post by user1397 on 2010-01-13
> **cammin said:**
> [http://read.pudn.com/downloads62/sourcecode/java/applet/game/217456/wcss/WorldCupSoccerSlime.java__.htm](http://read.pudn.com/downloads62/sourcecode/java/applet/game/217456/wcss/WorldCupSoccerSlime.java__.htm)nice!

so now we have the source...awesome, thought it was lost forever, thanks!

I'll upload the source in this thread.

---

### Post by user1397 on 2010-01-16
So I'm just wondering about the .class file, I still have to find that, although can it not be 'harvested' from the .java file? (I don't know much about java...)

To embed the game in an html file, you need the .class file that is all I know.

---

### Post by Yes on 2010-01-16
.class files are created when you compile .java files.

To compile a .java file use javac from the command line.

---

### Post by user1397 on 2010-01-17
> **Yes said:**
> .class files are created when you compile .java files.

To compile a .java file use javac from the command line.Ok so I got the .class file using wget and getting it from one of the websites with the game embedded, so that's no problem, but I did try to compile the .java file that was found in this thread just to see what would happen and this is the 100 error-laden result I got:

```
$ javac WorldCupSoccerSlime.java 
WorldCupSoccerSlime.java:1: class, interface, or enum expected
   1. //<!-- 2-player version of Slime Volleyball -->   
   ^
WorldCupSoccerSlime.java:18: class, interface, or enum expected
  18. import java.awt.*;   
  ^
WorldCupSoccerSlime.java:19: class, interface, or enum expected
  19.    
  ^
WorldCupSoccerSlime.java:20: '{' expected
  20. public class WorldCupSoccerSlime extends Applet   
                                                     ^
WorldCupSoccerSlime.java:23: illegal start of type
  23.     private int nWidth;   
  ^
WorldCupSoccerSlime.java:23: ';' expected
  23.     private int nWidth;   
     ^
WorldCupSoccerSlime.java:24: illegal start of type
  24.     private int nHeight;   
  ^
WorldCupSoccerSlime.java:24: ';' expected
  24.     private int nHeight;   
     ^
WorldCupSoccerSlime.java:25: illegal start of type
  25.     private int p1Score;   
  ^
WorldCupSoccerSlime.java:25: ';' expected
  25.     private int p1Score;   
     ^
WorldCupSoccerSlime.java:26: illegal start of type
  26.     private int p2Score;   
  ^
WorldCupSoccerSlime.java:26: ';' expected
  26.     private int p2Score;   
     ^
WorldCupSoccerSlime.java:27: illegal start of type
  27.     private int p1X;   
  ^
WorldCupSoccerSlime.java:27: ';' expected
  27.     private int p1X;   
     ^
WorldCupSoccerSlime.java:28: illegal start of type
  28.     private int p2X;   
  ^
WorldCupSoccerSlime.java:28: ';' expected
  28.     private int p2X;   
     ^
WorldCupSoccerSlime.java:29: illegal start of type
  29.     private int p1Y;   
  ^
WorldCupSoccerSlime.java:29: ';' expected
  29.     private int p1Y;   
     ^
WorldCupSoccerSlime.java:30: illegal start of type
  30.     private int p2Y;   
  ^
WorldCupSoccerSlime.java:30: ';' expected
  30.     private int p2Y;   
     ^
WorldCupSoccerSlime.java:31: illegal start of type
  31.     private int p1Col;   
  ^
WorldCupSoccerSlime.java:31: ';' expected
  31.     private int p1Col;   
     ^
WorldCupSoccerSlime.java:32: illegal start of type
  32.     private int p2Col;   
  ^
WorldCupSoccerSlime.java:32: ';' expected
  32.     private int p2Col;   
     ^
WorldCupSoccerSlime.java:33: illegal start of type
  33.     private String slimeColText[] = {   
  ^
WorldCupSoccerSlime.java:33: ';' expected
  33.     private String slimeColText[] = {   
     ^
WorldCupSoccerSlime.java:34: '}' expected
  34.         "Argentina", "Belgium", "Australia", "Iceland", "Cameroon", "P.R. of China", "Costa Rica",   
     ^
WorldCupSoccerSlime.java:34: illegal start of type
  34.         "Argentina", "Belgium", "Australia", "Iceland", "Cameroon", "P.R. of China", "Costa Rica",   
                         ^
WorldCupSoccerSlime.java:34: <identifier> expected
  34.         "Argentina", "Belgium", "Australia", "Iceland", "Cameroon", "P.R. of China", "Costa Rica",   
                          ^
WorldCupSoccerSlime.java:34: <identifier> expected
  34.         "Argentina", "Belgium", "Australia", "Iceland", "Cameroon", "P.R. of China", "Costa Rica",   
                                     ^
WorldCupSoccerSlime.java:34: illegal start of type
  34.         "Argentina", "Belgium", "Australia", "Iceland", "Cameroon", "P.R. of China", "Costa Rica",   
                                                 ^
WorldCupSoccerSlime.java:34: <identifier> expected
  34.         "Argentina", "Belgium", "Australia", "Iceland", "Cameroon", "P.R. of China", "Costa Rica",   
                                                  ^
WorldCupSoccerSlime.java:34: <identifier> expected
  34.         "Argentina", "Belgium", "Australia", "Iceland", "Cameroon", "P.R. of China", "Costa Rica",   
                                                             ^
WorldCupSoccerSlime.java:34: illegal start of type
  34.         "Argentina", "Belgium", "Australia", "Iceland", "Cameroon", "P.R. of China", "Costa Rica",   
                                                                        ^
WorldCupSoccerSlime.java:34: <identifier> expected
  34.         "Argentina", "Belgium", "Australia", "Iceland", "Cameroon", "P.R. of China", "Costa Rica",   
                                                                         ^
WorldCupSoccerSlime.java:34: <identifier> expected
  34.         "Argentina", "Belgium", "Australia", "Iceland", "Cameroon", "P.R. of China", "Costa Rica",   
                                                                                          ^
WorldCupSoccerSlime.java:34: illegal start of type
  34.         "Argentina", "Belgium", "Australia", "Iceland", "Cameroon", "P.R. of China", "Costa Rica",   
                                                                                                       ^
WorldCupSoccerSlime.java:34: <identifier> expected
  34.         "Argentina", "Belgium", "Australia", "Iceland", "Cameroon", "P.R. of China", "Costa Rica",   
                                                                                                        ^
WorldCupSoccerSlime.java:35: ';' expected
  35.         "Croatia", "Denmark", "Eucador", "Mexico", "France", "USA",   
     ^
WorldCupSoccerSlime.java:35: illegal start of type
  35.         "Croatia", "Denmark", "Eucador", "Mexico", "France", "USA",   
                       ^
WorldCupSoccerSlime.java:35: <identifier> expected
  35.         "Croatia", "Denmark", "Eucador", "Mexico", "France", "USA",   
                        ^
WorldCupSoccerSlime.java:35: <identifier> expected
  35.         "Croatia", "Denmark", "Eucador", "Mexico", "France", "USA",   
                                   ^
WorldCupSoccerSlime.java:35: illegal start of type
  35.         "Croatia", "Denmark", "Eucador", "Mexico", "France", "USA",   
                                             ^
WorldCupSoccerSlime.java:35: <identifier> expected
  35.         "Croatia", "Denmark", "Eucador", "Mexico", "France", "USA",   
                                              ^
WorldCupSoccerSlime.java:35: <identifier> expected
  35.         "Croatia", "Denmark", "Eucador", "Mexico", "France", "USA",   
                                                        ^
WorldCupSoccerSlime.java:35: illegal start of type
  35.         "Croatia", "Denmark", "Eucador", "Mexico", "France", "USA",   
                                                                 ^
WorldCupSoccerSlime.java:35: <identifier> expected
  35.         "Croatia", "Denmark", "Eucador", "Mexico", "France", "USA",   
                                                                  ^
WorldCupSoccerSlime.java:35: <identifier> expected
  35.         "Croatia", "Denmark", "Eucador", "Mexico", "France", "USA",   
                                                                         ^
WorldCupSoccerSlime.java:36: illegal start of type
  36.         "Italy", "Japan", "Russia", "Paraguay", "Poland",   
              ^
WorldCupSoccerSlime.java:36: <identifier> expected
  36.         "Italy", "Japan", "Russia", "Paraguay", "Poland",   
                     ^
WorldCupSoccerSlime.java:36: ';' expected
  36.         "Italy", "Japan", "Russia", "Paraguay", "Poland",   
                      ^
WorldCupSoccerSlime.java:36: illegal start of type
  36.         "Italy", "Japan", "Russia", "Paraguay", "Poland",   
                              ^
WorldCupSoccerSlime.java:36: <identifier> expected
  36.         "Italy", "Japan", "Russia", "Paraguay", "Poland",   
                               ^
WorldCupSoccerSlime.java:36: <identifier> expected
  36.         "Italy", "Japan", "Russia", "Paraguay", "Poland",   
                                         ^
WorldCupSoccerSlime.java:36: illegal start of type
  36.         "Italy", "Japan", "Russia", "Paraguay", "Poland",   
                                                    ^
WorldCupSoccerSlime.java:36: <identifier> expected
  36.         "Italy", "Japan", "Russia", "Paraguay", "Poland",   
                                                     ^
WorldCupSoccerSlime.java:36: <identifier> expected
  36.         "Italy", "Japan", "Russia", "Paraguay", "Poland",   
                                                               ^
WorldCupSoccerSlime.java:37: illegal start of type
  37.         "Portugal", "Ireland", "Saudi Arabia", "Senegal", "Slovenia",   
              ^
WorldCupSoccerSlime.java:37: <identifier> expected
  37.         "Portugal", "Ireland", "Saudi Arabia", "Senegal", "Slovenia",   
                        ^
WorldCupSoccerSlime.java:37: ';' expected
  37.         "Portugal", "Ireland", "Saudi Arabia", "Senegal", "Slovenia",   
                         ^
WorldCupSoccerSlime.java:37: illegal start of type
  37.         "Portugal", "Ireland", "Saudi Arabia", "Senegal", "Slovenia",   
                                   ^
WorldCupSoccerSlime.java:37: <identifier> expected
  37.         "Portugal", "Ireland", "Saudi Arabia", "Senegal", "Slovenia",   
                                    ^
WorldCupSoccerSlime.java:37: <identifier> expected
  37.         "Portugal", "Ireland", "Saudi Arabia", "Senegal", "Slovenia",   
                                                    ^
WorldCupSoccerSlime.java:37: illegal start of type
  37.         "Portugal", "Ireland", "Saudi Arabia", "Senegal", "Slovenia",   
                                                              ^
WorldCupSoccerSlime.java:37: <identifier> expected
  37.         "Portugal", "Ireland", "Saudi Arabia", "Senegal", "Slovenia",   
                                                               ^
WorldCupSoccerSlime.java:37: <identifier> expected
  37.         "Portugal", "Ireland", "Saudi Arabia", "Senegal", "Slovenia",   
                                                                           ^
WorldCupSoccerSlime.java:38: illegal start of type
  38.         "Spain", "Seth Efrica", "South Corea", "Sveden", "Tunisia", "Turkey",   
              ^
WorldCupSoccerSlime.java:38: <identifier> expected
  38.         "Spain", "Seth Efrica", "South Corea", "Sveden", "Tunisia", "Turkey",   
                     ^
WorldCupSoccerSlime.java:38: ';' expected
  38.         "Spain", "Seth Efrica", "South Corea", "Sveden", "Tunisia", "Turkey",   
                      ^
WorldCupSoccerSlime.java:38: illegal start of type
  38.         "Spain", "Seth Efrica", "South Corea", "Sveden", "Tunisia", "Turkey",   
                                    ^
WorldCupSoccerSlime.java:38: <identifier> expected
  38.         "Spain", "Seth Efrica", "South Corea", "Sveden", "Tunisia", "Turkey",   
                                     ^
WorldCupSoccerSlime.java:38: <identifier> expected
  38.         "Spain", "Seth Efrica", "South Corea", "Sveden", "Tunisia", "Turkey",   
                                                    ^
WorldCupSoccerSlime.java:38: illegal start of type
  38.         "Spain", "Seth Efrica", "South Corea", "Sveden", "Tunisia", "Turkey",   
                                                             ^
WorldCupSoccerSlime.java:38: <identifier> expected
  38.         "Spain", "Seth Efrica", "South Corea", "Sveden", "Tunisia", "Turkey",   
                                                              ^
WorldCupSoccerSlime.java:38: <identifier> expected
  38.         "Spain", "Seth Efrica", "South Corea", "Sveden", "Tunisia", "Turkey",   
                                                                         ^
WorldCupSoccerSlime.java:38: illegal start of type
  38.         "Spain", "Seth Efrica", "South Corea", "Sveden", "Tunisia", "Turkey",   
                                                                                  ^
WorldCupSoccerSlime.java:38: <identifier> expected
  38.         "Spain", "Seth Efrica", "South Corea", "Sveden", "Tunisia", "Turkey",   
                                                                                   ^
WorldCupSoccerSlime.java:39: ';' expected
  39.         "Uruguay", "Brazil", "England", "Germany", "Night Elves"   
     ^
WorldCupSoccerSlime.java:39: illegal start of type
  39.         "Uruguay", "Brazil", "England", "Germany", "Night Elves"   
                       ^
WorldCupSoccerSlime.java:39: <identifier> expected
  39.         "Uruguay", "Brazil", "England", "Germany", "Night Elves"   
                        ^
WorldCupSoccerSlime.java:39: <identifier> expected
  39.         "Uruguay", "Brazil", "England", "Germany", "Night Elves"   
                                  ^
WorldCupSoccerSlime.java:39: illegal start of type
  39.         "Uruguay", "Brazil", "England", "Germany", "Night Elves"   
                                            ^
WorldCupSoccerSlime.java:39: <identifier> expected
  39.         "Uruguay", "Brazil", "England", "Germany", "Night Elves"   
                                             ^
WorldCupSoccerSlime.java:39: <identifier> expected
  39.         "Uruguay", "Brazil", "England", "Germany", "Night Elves"   
                                                        ^
WorldCupSoccerSlime.java:40: illegal start of type
  40.     };   
  ^
WorldCupSoccerSlime.java:40: <identifier> expected
  40.     };   
     ^
WorldCupSoccerSlime.java:41: illegal start of type
  41.     private Color darkRed = new Color(128, 0, 0), darkGreen = new Color(0, 128, 0), darkBlue = new Color(0, 0, 128);   
  ^
WorldCupSoccerSlime.java:41: ';' expected
  41.     private Color darkRed = new Color(128, 0, 0), darkGreen = new Color(0, 128, 0), darkBlue = new Color(0, 0, 128);   
     ^
WorldCupSoccerSlime.java:42: illegal start of type
  42.     private Color[] slimaryCols = {   
  ^
WorldCupSoccerSlime.java:42: ';' expected
  42.     private Color[] slimaryCols = {   
     ^
WorldCupSoccerSlime.java:43: '}' expected
  43.         Color.cyan, Color.red, Color.green, Color.white, darkGreen, Color.white, darkRed,   
     ^
WorldCupSoccerSlime.java:43: illegal start of type
  43.         Color.cyan, Color.red, Color.green, Color.white, darkGreen, Color.white, darkRed,   
                   ^
WorldCupSoccerSlime.java:43: ';' expected
  43.         Color.cyan, Color.red, Color.green, Color.white, darkGreen, Color.white, darkRed,   
                               ^
WorldCupSoccerSlime.java:43: <identifier> expected
  43.         Color.cyan, Color.red, Color.green, Color.white, darkGreen, Color.white, darkRed,   
                                   ^
WorldCupSoccerSlime.java:43: ';' expected
  43.         Color.cyan, Color.red, Color.green, Color.white, darkGreen, Color.white, darkRed,   
                                          ^
WorldCupSoccerSlime.java:43: <identifier> expected
  43.         Color.cyan, Color.red, Color.green, Color.white, darkGreen, Color.white, darkRed,   
                                                ^
WorldCupSoccerSlime.java:43: ';' expected
  43.         Color.cyan, Color.red, Color.green, Color.white, darkGreen, Color.white, darkRed,   
                                                       ^
WorldCupSoccerSlime.java:43: <identifier> expected
  43.         Color.cyan, Color.red, Color.green, Color.white, darkGreen, Color.white, darkRed,   
                                                             ^
WorldCupSoccerSlime.java:43: ';' expected
  43.         Color.cyan, Color.red, Color.green, Color.white, darkGreen, Color.white, darkRed,   
                                                                               ^
WorldCupSoccerSlime.java:43: <identifier> expected
  43.         Color.cyan, Color.red, Color.green, Color.white, darkGreen, Color.white, darkRed,   
                                                                                     ^
100 errors
```

---

### Post by Mornedhel on 2010-01-17
You need to remove the line numbers first.

No idea what those are doing there in the first place. Get an editor that supports rectangular selections and remove the first few columns.

---

### Post by user1397 on 2010-01-17
> **Mornedhel said:**
> You need to remove the line numbers first.

No idea what those are doing there in the first place. Get an editor that supports rectangular selections and remove the first few columns.I removed line numbers using Jedit, and uploaded the source files again with the changes.  I tried compiling it again, and I still got 100 errors.  The output was so long even the terminal couldn't contain it all, so I have here just a snippet:

```
WorldCupSoccerSlime.java:176: case, default, or '}' expected
                gameLength = (1<<i)*60000; worldcup="false;" true;="" return="" false;="" public="" boolean="" handleevent(event="" event)="" switch(event.id)="" 503:="" event.mouse_move="" showstatus(="" slime="" volleyball="" 2-player:="" soccer="" slime,="" by="" quin="" pendragon:="" tartarus.uwa.edu.au="" ~fractoid="" );="" requestfocus();="" 501:="" event.mouse_down="" if(!finplay="" &&="" testbutton(event.x,="" event.y))="" fendgame="false;" finplay="true;" p1x="200;" p1y="0;" p2x="800;" p2y="0;" ballx="500;" bally="200;" balloldx="500;" balloldy="200;" ballvx="0;" ballvy="0;" p1score="0;" p2score="0;" promptmsg="" ;="" paint(getgraphics());="" try="" thread.sleep(100);="" catch="" (exception="" e)="" gamethread="new" thread(this);="" gamethread.start();="" event.key_action:="" 401:="" event.key_press="" (fcanchangecol)="" 83:="" 115:="" while(p1col="=" p1col="p1Col" p1col-1;="" 75:="" 107:="" !="slimaryCols.length-1" +="" 1="" 0;="" while(p2col="=" p1col);="" do="" p2col="p2Col" 0="" ?="" slimarycols.length-1="" p2col-1;="" while="" (p1col="=" p2col);="" drawscores();="" 6="" fsuperslime="!fSuperSlime;" repaint();="" if(fendgame)="" default:="" 68:="" 100:="" d="" p1xv="0;" 87:="" 119:="" w="" if(p1y="=" p1yv="0;" event.left:="" 74:="" 106:="" j="" event.right:="" 76:="" 108:="" l="" p2xv="0;" event.up:="" 73:="" 105:="" i="" if(p2y="=" 0)="" if="" (!worldcup)="" p2yv="0;" b="" togglebuffering();="" 32:="" mousepressed="true;" }="" event.key_action_release:="" 402:="" event.key_release="" switch(event.key)="" {="" s="" fp1sticky="true;" k="" :="" event.down:="" fp2sticky="true;" break;="" 65:="" case="" 97:="" a="" if(p1xv="">< 0)   
                                                                                                                                                                                                                                                                                                                                                                 ^
WorldCupSoccerSlime.java:176: case, default, or '}' expected
                gameLength = (1<<i)*60000; worldcup="false;" true;="" return="" false;="" public="" boolean="" handleevent(event="" event)="" switch(event.id)="" 503:="" event.mouse_move="" showstatus(="" slime="" volleyball="" 2-player:="" soccer="" slime,="" by="" quin="" pendragon:="" tartarus.uwa.edu.au="" ~fractoid="" );="" requestfocus();="" 501:="" event.mouse_down="" if(!finplay="" &&="" testbutton(event.x,="" event.y))="" fendgame="false;" finplay="true;" p1x="200;" p1y="0;" p2x="800;" p2y="0;" ballx="500;" bally="200;" balloldx="500;" balloldy="200;" ballvx="0;" ballvy="0;" p1score="0;" p2score="0;" promptmsg="" ;="" paint(getgraphics());="" try="" thread.sleep(100);="" catch="" (exception="" e)="" gamethread="new" thread(this);="" gamethread.start();="" event.key_action:="" 401:="" event.key_press="" (fcanchangecol)="" 83:="" 115:="" while(p1col="=" p1col="p1Col" p1col-1;="" 75:="" 107:="" !="slimaryCols.length-1" +="" 1="" 0;="" while(p2col="=" p1col);="" do="" p2col="p2Col" 0="" ?="" slimarycols.length-1="" p2col-1;="" while="" (p1col="=" p2col);="" drawscores();="" 6="" fsuperslime="!fSuperSlime;" repaint();="" if(fendgame)="" default:="" 68:="" 100:="" d="" p1xv="0;" 87:="" 119:="" w="" if(p1y="=" p1yv="0;" event.left:="" 74:="" 106:="" j="" event.right:="" 76:="" 108:="" l="" p2xv="0;" event.up:="" 73:="" 105:="" i="" if(p2y="=" 0)="" if="" (!worldcup)="" p2yv="0;" b="" togglebuffering();="" 32:="" mousepressed="true;" }="" event.key_action_release:="" 402:="" event.key_release="" switch(event.key)="" {="" s="" fp1sticky="true;" k="" :="" event.down:="" fp2sticky="true;" break;="" 65:="" case="" 97:="" a="" if(p1xv="">< 0)   
                                                                                                                                                                                                                                                                                                                                                                  ^
```

---

### Post by cammin on 2010-01-18
Wow, that source i linked to is pretty messed up,

There's a few lines missing around line 179 which is causing a bunch of problems.

---

### Post by user1397 on 2010-01-18
> **cammin said:**
> Wow, that source i linked to is pretty messed up,

There's a few lines missing around line 179 which is causing a bunch of problems.yea it is pretty messed up, but it's just about the only living source of this game on the internet as far as I know. (ergo, thanks for finding it)

I made a new [thread]("http://ubuntuforums.org/showthread.php?t=1384090") in programming talk (more appropriate there) to try to clean up the code.

I know next to nothing about java so I don't know how to clean up line 179 (I think it's actually line 176 that returns the error) but I'd sure as hell like some help! :D

---

### Post by user1397 on 2010-11-21
this is the .java file:
```
import java.applet.Applet;
import java.awt.*;

public class WorldCupSoccerSlime extends Applet
    implements Runnable
{
    private int nWidth;
    private int nHeight;
    private int p1Score;
    private int p2Score;
    private int p1X;
    private int p2X;
    private int p1Y;
    private int p2Y;
    private int p1Col;
    private int p2Col;
    private String slimeColText[] = {
        "Argentina", "Belgium", "Australia", "Iceland", "Cameroon", "P.R. of China", "Costa Rica",
        "Croatia", "Denmark", "Eucador", "Mexico", "France", "USA",
        "Italy", "Japan", "Russia", "Paraguay", "Poland",
        "Portugal", "Ireland", "Saudi Arabia", "Senegal", "Slovenia",
        "Spain", "Seth Efrica", "South Corea", "Sveden", "Tunisia", "Turkey",
        "Uruguay", "Brazil", "England", "Germany", "Night Elves"
    };
    private Color darkRed = new Color(128, 0, 0), darkGreen = new Color(0, 128, 0), darkBlue = new Color(0, 0, 128);
    private Color[] slimaryCols = {
        Color.cyan, Color.red, Color.green, Color.white, darkGreen, Color.white, darkRed,
        darkRed, new Color(119, 41, 28), Color.yellow, Color.green, Color.white, Color.white,
        new Color(128, 128, 255), darkBlue, Color.white, Color.red, Color.white,
        new Color(119, 41, 28), Color.green, Color.white, Color.white, Color.white,
        new Color(185, 30, 2), Color.white, Color.red, new Color(252, 239, 82), Color.white, Color.red,
        new Color(16, 180, 180), new Color(241, 245, 71), new Color(230, 230, 230), Color.white, Color.blue,
    };
    private Color[] secondaryCols = {
        Color.white, Color.black, Color.yellow, new Color(128, 128, 255), Color.red, Color.red, darkBlue,
        Color.white, Color.white, darkBlue, Color.green, Color.blue, darkBlue,
        Color.white, Color.white, Color.blue, Color.white, Color.red,
        darkGreen, Color.white, new Color(128, 255, 128), new Color(255, 128, 0), darkGreen,
        darkBlue, new Color(13, 131, 10), Color.white, Color.blue, Color.red, Color.white,
        Color.black, new Color(7, 177, 33), Color.red, Color.black, Color.blue,
    };
    private int p1OldX;
    private int p2OldX;
    private int p1OldY;
    private int p2OldY;
    private int p1XV;
    private int p2XV;
    private int p1YV;
    private int p2YV;
    private int ballX;
    private int ballY;
    private int ballVX;
    private int ballVY;
    private int ballOldX;
    private int ballOldY;
    private Graphics screen;
    private String promptMsg;
    private int replayData[][];
    private int replayPos;
    private int replayStart;
    private boolean mousePressed;
    private boolean fCanChangeCol;
    private boolean fInPlay;
    private int p1Blink;
    private int p2Blink;
    private boolean fP1Sticky;
    private boolean fP2Sticky;
    private boolean fP1Touched;
    private boolean fP2Touched;
    private int p1TouchingGoal;
    private int p2TouchingGoal;
    private Thread gameThread;
    private boolean fEndGame;
    private boolean fPlayOn;
    private int nScoreX;
    private long startTime;
    private long gameTime;
    private int scoringRun;
    private int frenzyCol = 0;
    private int playOnTicks;
    private Image backBuffer;
    private final int SMILE_DIFF = 2;
    private final int DAMPING = 7;
    private final int MAX_TICKS_TOUCHING_GOAL = 60;
    private int JUMPVEL;
    private int SLIMEVEL;
    private int GRAVITY;
    private int gameLength; 

    private boolean worldCup = false;
    private int worldCupRound = 0;
    private boolean fExtraTime;
    private boolean fGoldenGoal;

    private boolean fSuperSlime;

    private boolean doubleBuffered;

    private boolean gamePaused;

    public void initStuff()
    {
        fEndGame = true;
        p1X = 200;
        p1Y = 0;
        p2X = 800;
        p2Y = 0;
        p1XV = 0;
        p1YV = 0;
        p2XV = 0;
        p2YV = 0;
        p1Score = 0;
        p2Score = 0;
        ballOldX = ballX = 500;
        ballOldY = ballY = 200;
        ballVX = 0;
        ballVY = 0;
        replayStart = replayPos = 0;
        fP1Touched = fP2Touched = false;
        playOnTicks = 10;
        fPlayOn = false;
        fExtraTime = false;
        fGoldenGoal = false;
        JUMPVEL = (fSuperSlime) ? 65 : 31;
        SLIMEVEL = (fSuperSlime) ? 16 : 8;
        GRAVITY = (fSuperSlime) ? 8 : 2;

        gamePaused = false;
    }

    private void drawButtons()
    {
        String[] buttons = {"1 minute", "2 minutes", "4 minutes", "8 minutes", "World Cup" };
        FontMetrics fm = screen.getFontMetrics();
        Color darkBlue = new Color(0, 0, 128);
        for (int i=0; i<5; i++)
        {
            screen.setColor(darkBlue);
            screen.fillRect(((2*i+1)*nWidth/10)-nWidth/12,
                nHeight*2/10, nWidth/6, nHeight/10);
            screen.setColor(Color.white);
            screen.drawString(buttons[i],
                ((2*i+1)*nWidth/10)-fm.stringWidth(buttons[i]) / 2,
                nHeight*5/20+fm.getHeight()/2);
        }
        flip();
    }

    private boolean testButton(int x, int y)
    {
        for (int i=0; i<5; i++)
        {
            if ((x > ((2*i+1)*nWidth/10)-nWidth/12)
                && (x < ((2*i+1)*nWidth/10)+nWidth/12)
                && (y > (nHeight*2/10)) && (y < nHeight*3/10))
            {
                if (i == 4) //world cup mode
                {
                gameLength = 120000;
                worldCup = true;
                }
                else
                {
                gameLength = (1<<i)*60000;
                worldCup = false;
                }
                return true;
            }
        }
        return false;
    }

    public boolean handleEvent(Event event)
    {
        switch(event.id)
        {
        default:
            break;

        case 503: // Event.MOUSE_MOVE
            showStatus("Slime Volleyball 2-Player: Soccer Slime, by Quin Pendragon: tartarus.uwa.edu.au/~fractoid");
            requestFocus();
            break;

        case 501: // Event.MOUSE_DOWN
            mousePressed = true;
            if(!fInPlay && testButton(event.x, event.y))
            {
                fEndGame = false;
                fInPlay = true;
                p1X = 200;
                p1Y = 0;
                p2X = 800;
                p2Y = 0;
                p1XV = 0;
                p1YV = 0;
                p2XV = 0;
                p2YV = 0;
                ballX = 500;
                ballY = 200;
                ballOldX = 500;
                ballOldY = 200;
                ballVX = 0;
                ballVY = 0;
                p1Score = 0;
                p2Score = 0;
                promptMsg = "";
                paint(getGraphics());
                try { Thread.sleep(100); } catch (Exception e) { }
                gameThread = new Thread(this);
                gameThread.start();
            }
            break;

        case Event.KEY_ACTION:
        case 401: // Event.KEY_PRESS
            if (fCanChangeCol)
            switch(event.key)
            {
            case 83: // 'S'
            case 115: // 's'
                do
                    p1Col = p1Col != slimaryCols.length-1 ? p1Col + 1 : 0;
                while(p1Col == p2Col);
                drawScores();
                repaint();
                break;

            case 'W':
            case 'w':
                do
                    p1Col = p1Col == 0 ? slimaryCols.length-1 : p1Col-1;
                while (p1Col == p2Col);
                drawScores();
                repaint();
                break;

            case Event.DOWN:
            case 75: // 'K'
            case 107: // 'k'
                    do
                        p2Col = p2Col != slimaryCols.length-1 ? p2Col + 1 : 0;
                    while(p2Col == p1Col);
                    drawScores();
                    repaint();
                    break;

            case 'i':
            case 'I':
            case Event.UP:
                do
                    p2Col = p2Col == 0 ? slimaryCols.length-1 : p2Col-1;
                while (p1Col == p2Col);
                drawScores();
                repaint();
                break;

            case '6':
                fSuperSlime = !fSuperSlime;
                repaint();
            }
            if(fEndGame)
                break;
            switch(event.key)
            {
            default:
                break;

            case Event.PAUSE:
                gamePaused = !gamePaused;
                break;

            case 's':
            case 'S':
                fP1Sticky = true;
                break;

            case 'k':
            case 'K':
            case Event.DOWN:
                if (!worldCup)
                    fP2Sticky = true;
                break;

            case 65: // 'A'
            case 97: // 'a'
                p1XV = -SLIMEVEL;
                break;

            case 68: // 'D'
            case 100: // 'd'
                p1XV = SLIMEVEL;
                break;

            case 87: // 'W'
            case 119: // 'w'
                if(p1Y == 0)
                    p1YV = JUMPVEL;
                break;

            case Event.LEFT:
            case 74: // 'J'
            case 106: // 'j'
                if (!worldCup)
                    p2XV = -SLIMEVEL;
                break;

            case Event.RIGHT:
            case 76: // 'L'
            case 108: // 'l'
                if (!worldCup)
                    p2XV = SLIMEVEL;
                break;

            case Event.UP:
            case 73: // 'I'
            case 105: // 'i'
                if(p2Y == 0)
                    if (!worldCup)
                        p2YV = JUMPVEL;
                break;

            case 'b':
            case 'B':
                toggleBuffering();
                break;

            case 32: // ' '
                mousePressed = true;
                break;
            }
            break;

        case Event.KEY_ACTION_RELEASE:
        case 402: // Event.KEY_RELEASE
            switch(event.key)
            {
            case 's':
            case 'S':
                fP1Sticky = false;
                break;

            case 'k':
            case 'K':
            case Event.DOWN:
                fP2Sticky = false;
                break;

            case 65: // 'A'
            case 97: // 'a'
                if(p1XV < 0)
                    p1XV = 0;
                break;

            case 68: // 'D'
            case 100: // 'd'
                if(p1XV > 0)
                    p1XV = 0;
                break;

            case Event.LEFT:
            case 74: // 'J'
            case 106: // 'j'
                if(p2XV < 0)
                    if (!worldCup)
                        p2XV = 0;
                break;

            case Event.RIGHT:
            case 76: // 'L'
            case 108: // 'l'
                if(p2XV > 0)
                    if (!worldCup)
                        p2XV = 0;
                break;
            }
        }
        return false;
    }

    private int[] pointsX = new int[4], pointsY = new int[4];
    private void DrawSlimers()
    {
        int k1 = nWidth / 10;
        int j2 = nHeight / 10;
        int i3 = nWidth / 50;
        int j3 = nHeight / 25;
        int k3 = (ballX * nWidth) / 1000;
        int l3 = (4 * nHeight) / 5 - (ballY * nHeight) / 1000;
        int i = (p1OldX * nWidth) / 1000 - k1 / 2;
        int l = (7 * nHeight) / 10 - (p1OldY * nHeight) / 1000;
        screen.setColor(Color.blue);
        screen.fillRect(i, l, k1, j2);
        i = (p2OldX * nWidth) / 1000 - k1 / 2;
        l = (7 * nHeight) / 10 - (p2OldY * nHeight) / 1000;
        screen.setColor(Color.blue);
        screen.fillRect(i, l, k1, j2);
        if (!fEndGame) MoveBall();
        i = (p1X * nWidth) / 1000 - k1 / 2;
        l = (7 * nHeight) / 10 - (p1Y * nHeight) / 1000;
        screen.setColor(fSuperSlime ? slimaryCols[frenzyCol = ((frenzyCol + 1) % slimaryCols.length)] : slimaryCols[p1Col]);
        screen.fillArc(i, l, k1, 2 * j2, 0, 180);
        screen.setColor(secondaryCols[p1Col]);
        pointsX[0] = pointsX[2] = i+k1/2; pointsX[1] = i + k1 * 2 / 5; pointsX[3] = i + k1 / 8;
        pointsY[0] = l; pointsY[1] = pointsY[3] = l + j2/2; pointsY[2] = l + j2;
        screen.fillPolygon(pointsX, pointsY, 4);
        int l4 = p1X + 38;
        int i5 = p1Y - 60;
        i = (l4 * nWidth) / 1000;
        l = (7 * nHeight) / 10 - (i5 * nHeight) / 1000;
        int i4 = i - k3;
        int j4 = l - l3;
        int k4 = (int)Math.sqrt(i4 * i4 + j4 * j4);
        boolean flag = Math.random() < 0.01D;
        if(flag)
            p1Blink = 5;
        if(p1Blink == 0)
        {
            screen.setColor(Color.white);
            screen.fillOval(i - i3, l - j3, i3, j3);
            if(k4 > 0 && !flag)
            {
                screen.setColor(Color.black);
                screen.fillOval(i - (4 * i4) / k4 - (3 * i3) / 4, l - (4 * j4) / k4 - (3 * j3) / 4, i3 / 2, j3 / 2);
            }
        } else
        {
            p1Blink--;
        }
        if(p1Score > p2Score + SMILE_DIFF)
        {
            int j = (p1X * nWidth) / 1000;
            int i1 = (7 * nHeight) / 10 - ((p1Y - 40) * nHeight) / 1000;
            int l1 = nWidth / 20;
            int k2 = nHeight / 20;
            int j5 = 0;
            do
            {
                screen.setColor(Color.black);
                screen.drawArc(j, i1 + j5, l1, k2, -30, -150);
            } while(++j5 < 3);
        }
        i = (p2X * nWidth) / 1000 - k1 / 2;
        l = (7 * nHeight) / 10 - (p2Y * nHeight) / 1000;
        screen.setColor(fSuperSlime ? slimaryCols[frenzyCol = ((frenzyCol + 1) % slimaryCols.length)] : slimaryCols[p2Col]);
        screen.fillArc(i, l, k1, 2 * j2, 0, 180);
        screen.setColor(secondaryCols[p2Col]);
        pointsX[0] = pointsX[2] = i+k1/2; pointsX[1] = i+k1*3/5; pointsX[3] = i+k1*7/8;
        pointsY[0] = l; pointsY[1] = pointsY[3] = l+j2/2; pointsY[2] = l+j2;
        screen.fillPolygon(pointsX, pointsY, 4);
        l4 = p2X - 18;
        i5 = p2Y - 60;
        i = (l4 * nWidth) / 1000;
        l = (7 * nHeight) / 10 - (i5 * nHeight) / 1000;
        i4 = i - k3;
        j4 = l - l3;
        k4 = (int)Math.sqrt(i4 * i4 + j4 * j4);
        flag = Math.random() < 0.01D;
        if(flag)
            p2Blink = 5;
        if(p2Blink == 0)
        {
            screen.setColor(flag ? Color.gray : Color.white);
            screen.fillOval(i - i3, l - j3, i3, j3);
            if(k4 > 0 && !flag)
            {
                screen.setColor(Color.black);
                screen.fillOval(i - (4 * i4) / k4 - (3 * i3) / 4, l - (4 * j4) / k4 - (3 * j3) / 4, i3 / 2, j3 / 2);
            }
        } else
        {
            p2Blink--;
        }
        if(p2Score > p1Score + SMILE_DIFF)
        {
            int i2 = nWidth / 20;
            int l2 = nHeight / 20;
            int k = (p2X * nWidth) / 1000 - i2;
            int j1 = (7 * nHeight) / 10 - ((p2Y - 40) * nHeight) / 1000;
            int k5 = 0;
            do
            {
                screen.setColor(Color.black);
                screen.drawArc(k, j1 + k5, i2, l2, -10, -150);
            } while(++k5 < 3);
        }
    }

    public void paint(Graphics g)
    {
        nWidth = size().width;
        nHeight = size().height;
        screen.setColor(Color.blue);
        screen.fillRect(0, 0, nWidth, (4 * nHeight) / 5);
        screen.setColor(Color.gray);
        screen.fillRect(0, (4 * nHeight) / 5, nWidth, nHeight / 5);
        screen.setColor(Color.white);
//      g.fillRect(nWidth / 2 - 2, (7 * nHeight) / 10, 4, nHeight / 10 + 5);
        drawScores();
    if (!fInPlay)
        {
            DrawSlimers();
            drawButtons();
        }
    DrawGoals();
        drawPrompt();
        if(!fInPlay)
        {
            FontMetrics fontmetrics = screen.getFontMetrics();
            screen.setColor(Color.white);
            if (fSuperSlime)
                screen.drawString("Super Soccer Slime!", nWidth / 2 - fontmetrics.stringWidth("Super Soccer Slime!") / 2, nHeight / 2 - fontmetrics.getHeight());
            else
                screen.drawString("Soccer Slime!", nWidth / 2 - fontmetrics.stringWidth("Soccer Slime!") / 2, nHeight / 2 - fontmetrics.getHeight());
            screen.setColor(Color.white);
            fontmetrics = screen.getFontMetrics();
            screen.drawString("Written by Quin Pendragon", nWidth / 2 - fontmetrics.stringWidth("Written by Quin Pendragon") / 2, nHeight / 2 + fontmetrics.getHeight() * 2);
        }
        flip();
    }

    public void destroy()
    {
        gameThread.stop();
        gameThread = null;
    }

    private void ReplayFrame(int i, int j, int k, int l, int i1, boolean flag)
    {
        if(flag)
        {
            ballX = -1000; ballOldX = 500;
            ballY = -1000; ballOldY = 500;
            p1OldX = p1OldY = p2OldX = p2OldY = -10000;
        } else
        {
            int j1 = i != 0 ? i - 1 : 199;
            p1OldX = replayData[j1][0];
            p1OldY = replayData[j1][1];
            p2OldX = replayData[j1][2];
            p2OldY = replayData[j1][3];
            if (i == 0)
            {
                ballOldX = 500;
                ballOldY = 200;
            }
            else
            {
                ballOldX = replayData[j1][4];
                ballOldY = replayData[j1][5];
            }
        }
        p1X = replayData[i][0];
        p1Y = replayData[i][1];
        p2X = replayData[i][2];
        p2Y = replayData[i][3];
        ballX = replayData[i][4];
        ballY = replayData[i][5];
        p1Col = replayData[i][6];
        p2Col = replayData[i][7];
        ballVX = 0;
        ballVY = 1;
        if((i / 10) % 2 > 0)
        {
            screen.setColor(Color.red);
            screen.drawString("Replay...", j, k);
        } else
        {
            screen.setColor(Color.blue);
            screen.fillRect(j, k - i1, l, i1 * 2);
        }
        DrawSlimers();
        DrawGoals();
        try
        {
            Thread.sleep(20L);
            return;
        }
        catch(InterruptedException _ex)
        {
            return;
        }
    }

    private String MakeTime(long l)
    {
        long l1 = (l / 10L) % 100L;
        long l2 = (l / 1000L) % 60L;
        long l3 = (l / 60000L) % 60L;
        String s = "";
        if(l3 < 10L)
            s += "0";
        s += l3;
        s += ":";
        if(l2 < 10L)
            s += "0";
        s += l2;
        s += ":";
        if(l1 < 10L)
            s += "0";
        s += l1;
        return s;
    }

    private void MoveSlimers()
    {
        if (worldCup) //get the AI to move p2
        {
            switch (worldCupRound)
            {
                case 0: controlP2v0(); break;
                case 1: controlP2v1(); break;
                case 2: controlP2v2(); break;
                case 3: controlP2v3(); break;
            }
        }
        p1X += p1XV;
        if(p1X < 50)
            p1X = 50;
        if(p1X > 950)
            p1X = 950;
        if(p1YV != 0)
        {
            p1Y += p1YV -= GRAVITY;
            if(p1Y < 0)
            {
                p1Y = 0;
                p1YV = 0;
            }
        }
        p2X += p2XV;
        if(p2X > 950)
            p2X = 950;
        if(p2X < 50)
            p2X = 50;
        if(p2YV != 0)
        {
            p2Y += p2YV -= GRAVITY;
            if(p2Y < 0)
            {
                p2Y = 0;
                p2YV = 0;
            }
        }
    }

    public WorldCupSoccerSlime()
    {
        p2Col = 1;
        replayData = new int[200][8];
    }

    private void MoveBall()
    {
        int k = (30 * nHeight) / 1000;
        int i = (ballOldX * nWidth) / 1000;
        int j = (4 * nHeight) / 5 - (ballOldY * nHeight) / 1000;
        screen.setColor(Color.blue);
        screen.fillOval(i - k, j - k, k * 2, k * 2);
        ballY += --ballVY;
        ballX += ballVX;
        if(!fEndGame)
        {
            int l1 = (ballX - p1X) * 2;
            int i2 = ballY - p1Y;
            int j2 = l1 * l1 + i2 * i2;
            int k2 = ballVX - p1XV;
            int l2 = ballVY - p1YV;
            if(i2 > 0 && j2 < 15625 && j2 > 25)
            {
                int l = (int)Math.sqrt(j2);
                int j1 = (l1 * k2 + i2 * l2) / l;
                ballX = p1X + (l1 * 63) / l;
                ballY = p1Y + (i2 * 125) / l;
                if(j1 <= 0)
                {
                    if (!fP1Sticky)
                    {
                        ballVY += p1YV - (2 * i2 * j1) / l;
                        ballVX += (p1XV - (2 * l1 * j1) / l) * DAMPING / 10;
                    }
                    else
                    {
                        ballVX = 0;
                        ballVY = 0;
                    }
                    if(ballVX < -15)
                        ballVX = -15;
                    if(ballVX > 15)
                        ballVX = 15;
                    if(ballVY < -22)
                        ballVY = -22;
                    if(ballVY > 22)
                        ballVY = 22;
                }
                fP1Touched = true;
            }
            l1 = (ballX - p2X) * 2;
            i2 = ballY - p2Y;
            j2 = l1 * l1 + i2 * i2;
            k2 = ballVX - p2XV;
            l2 = ballVY - p2YV;
            if(i2 > 0 && j2 < 15625 && j2 > 25)
            {
                int i1 = (int)Math.sqrt(j2);
                int k1 = (l1 * k2 + i2 * l2) / i1;
                ballX = p2X + (l1 * 63) / i1;
                ballY = p2Y + (i2 * 125) / i1;
                if(k1 <= 0)
                {
                    if (!fP2Sticky)
                    {
                        ballVX += (p2XV - (2 * l1 * k1) / i1) * DAMPING / 10;
                        ballVY += p2YV - (2 * i2 * k1) / i1;
                    }
                    else
                    {
                        ballVX = 0;
                        ballVY = 0;
                    }
                    if(ballVX < -15)
                        ballVX = -15;
                    if(ballVX > 15)
                        ballVX = 15;
                    if(ballVY < -22)
                        ballVY = -22;
                    if(ballVY > 22)
                        ballVY = 22;
                }
                fP2Touched = true;
            }
            if(ballX < 15)
            {
                ballX = 15;
                ballVX = -ballVX;
            }
            if(ballX > 985)
            {
                ballX = 985;
                ballVX = -ballVX;
            }
            if ((ballX <= 50) || (ballX >= 950))
            {
                if (((ballY > 200) && (ballOldY < 200))
                    || ((ballY < 200) && (ballOldY >= 200)))
                {
                    ballY = 200;
                    ballVY *= -1;
                }
                if ((ballY > 180) && (ballY < 220))
                {
                    if ((ballX > 40) && (ballX < 50) && (ballVX < 0))
                    {
                        ballX = 50;
                        ballVX *= -1;
                    }
                    if ((ballX < 960) && (ballX > 950) && (ballVX > 0))
                    {
                        ballX = 950;
                        ballVX *= -1;
                    }
                }
            }
        if (ballY < 34)
        {
            ballY = 34;
            ballVY = -ballVY * DAMPING / 10;
                    ballVX = ballVX * DAMPING / 10;
        }
        }
        i = (ballX * nWidth) / 1000;
        j = (4 * nHeight) / 5 - (ballY * nHeight) / 1000;
        screen.setColor(Color.yellow);
        screen.fillOval(i - k, j - k, k * 2, k * 2);
    }

    private void DrawGoals()
    {
        screen.setColor(Color.white);
        screen.fillRect(nWidth / 20, 4 * nHeight / 5 - 200 * nHeight / 1000,
            5, 200 * nHeight / 1000);
        screen.fillRect(nWidth - nWidth / 20 - 5,
            4 * nHeight / 5 - 200 * nHeight / 1000,
            5, 200 * nHeight / 1000);
        screen.fillRect(0, 4*nHeight/5 + 2, nWidth/10, 2);
        screen.fillRect(nWidth*9/10, 4*nHeight/5 + 2, nWidth/10, 2);
    for (int i=0; i<nWidth / 20; i += 5)
        {
            screen.drawLine(i, 4 * nHeight / 5 - 200 * nHeight / 1000,
                i, 4 * nHeight / 5);
            screen.drawLine(nWidth-i, 4 * nHeight / 5 - 200 * nHeight / 1000,
                nWidth-i, 4 * nHeight / 5);
        }
        for (int i=4 * nHeight / 5 - nHeight / 5; i<4 * nHeight / 5; i += 5)
        {
            screen.drawLine(0, i, nWidth/20, i);
            screen.drawLine(nWidth, i, nWidth-nWidth/20, i);
        }
        int p1TickX = (MAX_TICKS_TOUCHING_GOAL - p1TouchingGoal)
            * nWidth / (2 * MAX_TICKS_TOUCHING_GOAL);
        screen.setColor(secondaryCols[p1Col]);
        screen.fillRect(0, nHeight-5, p1TickX, 5);
        screen.setColor(Color.gray);
        screen.fillRect(p1TickX, nHeight-5, nWidth/2-p1TickX, 5);
        int p2TickX = nWidth - (MAX_TICKS_TOUCHING_GOAL - p2TouchingGoal)
            * nWidth / (2 * MAX_TICKS_TOUCHING_GOAL);
        screen.setColor(secondaryCols[p2Col]);
        screen.fillRect(p2TickX, nHeight-5, nWidth, 5);
        screen.setColor(Color.gray);
        screen.fillRect(nWidth/2, nHeight-5, p2TickX-nWidth/2, 5);
    }

    private void DrawStatus()
    {
        Graphics g = screen;
        FontMetrics fontmetrics = screen.getFontMetrics();
        String s=null, time = MakeTime(gameTime);
        int i = nHeight / 20;
        int k=0, kt = fontmetrics.stringWidth(time);
        if (worldCup)
        {
            switch (worldCupRound)
            {
            case 1: s = "Quarter Finals"; break;
            case 2: s = "Semi-Finals"; break;
            case 3: s = "Final"; break;
            default: s = "Qualifying";
            }
            if (fGoldenGoal) s += " [Golden Goal]";
            else if (fExtraTime) s += " [Extra Time]";
            k = fontmetrics.stringWidth(s);
        }
        int mw = (k>kt) ? k : kt;
        g.setColor(Color.blue);
        g.fillRect(nWidth/2 - mw / 2 - 5, 0, mw + 10, i + 22);
        g.setColor(Color.white);
        screen.drawString(time, nWidth/2 - kt / 2, fontmetrics.getAscent() + 20);
        if (s != null) screen.drawString(s, nWidth/2 - k/2, fontmetrics.getAscent()+20-fontmetrics.getHeight());
    }

    public void drawPrompt()
    {
        screen.setColor(Color.gray);
        screen.fillRect(0, (4 * nHeight) / 5 + 6, nWidth, nHeight / 5 - 10);
        drawPrompt(promptMsg, 0);
    }

    public void drawPrompt(String s, int i)
    {
        FontMetrics fontmetrics = screen.getFontMetrics();
        screen.setColor(Color.lightGray);
        screen.drawString(s, (nWidth - fontmetrics.stringWidth(s)) / 2, (nHeight * 4) / 5 + fontmetrics.getHeight() * (i + 1) + 10);
    }

    private void promptBox(String msg1, String msg2)
    {
        FontMetrics fontmetrics = screen.getFontMetrics();
        int len1 = fontmetrics.stringWidth(msg1);
        int len2 = fontmetrics.stringWidth(msg2);
        int maxlen = (len1 > len2) ? len1 : len2;
        screen.setColor(Color.darkGray);
        screen.fillRect(nWidth/2-maxlen/2-20, nHeight*2/5, maxlen+40, nHeight/5);
        screen.setColor(Color.white);
        screen.drawString(msg1, nWidth/2-len1/2, nHeight*9/20);
        screen.drawString(msg2, nWidth/2-len2/2, nHeight*11/20);
            flip();
    }

    private void SaveReplayData()
    {
        replayData[replayPos][0] = p1X;
        replayData[replayPos][1] = p1Y;
        replayData[replayPos][2] = p2X;
        replayData[replayPos][3] = p2Y;
        replayData[replayPos][4] = ballX;
        replayData[replayPos][5] = ballY;
        replayData[replayPos][6] = p1Col;
        replayData[replayPos][7] = p2Col;
        replayPos++;
        if(replayPos >= 200)
            replayPos = 0;
        if(replayStart == replayPos)
            replayStart++;
        if(replayStart >= 200)
            replayStart = 0;
    }

    private void drawScores()
    {
        Graphics g = screen;
        int k = nHeight / 20;
        FontMetrics fm = screen.getFontMetrics();
        int i = fm.stringWidth("Replay...");
        g.setColor(Color.blue);
        g.fillRect(0, 0, nWidth, k + 22);
        g.setColor(Color.white);
        g.drawString(slimeColText[p1Col] + " : " + p1Score, nWidth/20, k);
        String p2ScrStr = p2Score + " : " + slimeColText[p2Col];
        g.drawString(p2ScrStr, nWidth-nWidth/20-fm.stringWidth(p2ScrStr), k);
    }

    public boolean checkScored()
    {
        if ((ballY < 200) && ((ballX < 40) || (ballX > 960)))
        {
            nScoreX = ballX;
            fPlayOn = true;
            playOnTicks = 10;
            return true;
        }
        return false;
    }

    public void run()
    {
        worldCupRound = 0;
        do {
        initStuff();
        replayPos = replayStart = 0;
        scoringRun = 0;
        fP1Touched = fP2Touched = false;
        gameTime = 0;
        startTime = System.currentTimeMillis();
        fEndGame = false;
        fCanChangeCol = false;
        mousePressed = false;
        gameTime = gameLength;
        fInPlay = true;
        fEndGame = false;
        if (worldCup)
        {
            paint(getGraphics());
            do {
                p2Col = (int)(Math.random() * slimaryCols.length / 4)
                    + worldCupRound * slimaryCols.length / 4;
            } while (p1Col == p2Col);
            String vs = slimeColText[p1Col] + " vs. " + slimeColText[p2Col];
            switch (worldCupRound)
            {
            case 0: promptBox("Qualifying Round", vs); gameLength = 30000; break;
            case 1: promptBox("Quarter Finals", vs); gameLength = 120000; break;
            case 2: promptBox("Semi-Finals", vs); gameLength = 120000; break;
            case 3: promptBox("World Cup Final", vs); gameLength = 300000; break;
            }
            try { Thread.sleep(4000); } catch (Exception e) { }
            repaint();
            flip();
        }
        while((gameTime > 0) || (worldCup && (worldCupRound > 0) && (p1Score == p2Score)))
        {
            gameTime = startTime + gameLength - System.currentTimeMillis();
            if (gameTime < 0) gameTime = 0;
            if (worldCup && !fExtraTime && (gameTime <= 0) && (worldCupRound > 0) && (p1Score == p2Score)) //go into extra time
            {
                String score = (p1Score==0) ? " nil" : " "+p1Score;
                promptBox("The score is " + slimeColText[p1Col] + score + ", "
                    + slimeColText[p2Col] + score + ".",
                    "And the game goes into extra time...");
                try { Thread.sleep(4000); } catch (Exception e) { }
                repaint(); flip();
                startTime += 30000; gameTime += 30000;
                fExtraTime = true;
            }
            else if ((gameTime <= 0) && fExtraTime && !fGoldenGoal && (p1Score == p2Score))
            {
                fGoldenGoal = true;
                String score = (p1Score==0) ? " nil" : " "+p1Score;
                promptBox("The score is " + slimeColText[p1Col] + score + ", "
                    + slimeColText[p2Col] + score + ", and the game goes into Golden Goal.",
                    "The next player to score will win the match!");
                try { Thread.sleep(4000); } catch (Exception e) { }
                repaint(); flip();
            }
            SaveReplayData();
            if (gamePaused)
            {
                long pauseTime = System.currentTimeMillis();
                while (gamePaused) try { Thread.sleep(100); } catch (Exception e) { }
                pauseTime = System.currentTimeMillis() - pauseTime;
                startTime += pauseTime; gameTime += pauseTime;
            }
            p1OldX = p1X;
            p1OldY = p1Y;
            p2OldX = p2X;
            p2OldY = p2Y;
            ballOldX = ballX;
            ballOldY = ballY;
            MoveSlimers();
            DrawSlimers();
            DrawGoals();
            DrawStatus();
            flip();
            if (p1X < 150) p1TouchingGoal++; else p1TouchingGoal = 0;
            if (p2X > 850) p2TouchingGoal++; else p2TouchingGoal = 0;
            if (fPlayOn) playOnTicks--;
            else fPlayOn = checkScored();
            if((playOnTicks == 0) ||
                (p1TouchingGoal > MAX_TICKS_TOUCHING_GOAL) ||
                (p2TouchingGoal > MAX_TICKS_TOUCHING_GOAL))
            {
                long l = System.currentTimeMillis();
                if (p1TouchingGoal > MAX_TICKS_TOUCHING_GOAL)
                { p2Score++; promptMsg = slimeColText[p1Col] + " pinged for goal hanging!"; }
                else if (p2TouchingGoal > MAX_TICKS_TOUCHING_GOAL)
                { p1Score++; promptMsg = slimeColText[p2Col] + " pinged for goal hanging!"; }
                else if (nScoreX < 500)
                {   p2Score++; promptMsg = slimeColText[p2Col] + " Scores!"; }
                else
                {   p1Score++; promptMsg = slimeColText[p1Col] + " Scores!"; }
                drawPrompt();
                drawPrompt("Click mouse for replay...", 1);
                flip();
                mousePressed = false;
                if(gameThread != null)
                try { Thread.sleep(2500L); }
                catch(InterruptedException _ex) { }
                if(mousePressed)
                {
                    SaveReplayData();
                    DoReplay();
                }
                promptMsg = "";
                drawPrompt();
                playOnTicks = 10;
                fPlayOn = false;
                startTime += System.currentTimeMillis() - l;
                ballX = 490+(int)(Math.random()*20);
                ballY = 190+(int)(Math.random()*20);
                ballVX = 0;
                ballVY = 0;
                p1X = 200; p1Y = 0; p1YV = 0;
                p2X = 800; p2Y = 0; p2YV = 0;
                replayStart = replayPos = 0;
                repaint();
            }
            if(gameThread != null)
                try
                {
                    if (fPlayOn) Thread.sleep(120L); else Thread.sleep(20);
                }
                catch(InterruptedException _ex) { }
        }
        fEndGame = true;
        if (fPlayOn)
        {
            if (nScoreX < 500)
            {
                p2Score++;
                promptMsg = slimeColText[p2Col] + " scores at the final whistle!";
            }
            else
            {
                p1Score++;
                promptMsg = slimeColText[p1Col] + " scores at the final whistle!";
            }
            drawPrompt();
        }
        else
            drawPrompt("And that's the final whistle!", 0);
        if (worldCup)
        {
            if (p1Score == p2Score)
        {
                drawPrompt("It's a draw at full time, here at Slime Stadium!", 1);
                promptBox("You played well, but a draw is not enough.", "You have been eliminated.");
                worldCup = false;
                flip();
        }
        else if (p1Score >= p2Score)
            {
                switch (worldCupRound)
                {
                case 0: drawPrompt(slimeColText[p1Col] + " qualifies for the world cup!", 1); break;
                case 1: drawPrompt(slimeColText[p1Col] + " proceeds to the semi-finals!", 1); break;
                case 2: drawPrompt(slimeColText[p1Col] + " is through to the final!!!", 1); break;
                case 3: drawPrompt(slimeColText[p1Col] + " wins the WORLD CUP!!!!!", 1); break;
                }
                if (worldCupRound == 3)
                {
                    worldCup = false;
                    promptBox("You win the world cup!!!", "Congratulations!");
                }
                else
                    worldCupRound++;
            }
            else
            {
                switch (worldCupRound)
                {
                case 0:
                case 1: promptBox("You have been eliminated.", "Goodbye."); break;
                case 2: promptBox("You have been knocked out of the semifinals.", "You played well."); break;
                case 3: promptBox("You came second.", "Are you satisfied with that?"); break;
                }
                worldCup = false;
            }
        }
        else
        {
            if (p1Score == p2Score)
                drawPrompt("It's a draw at full time, here at Slime Stadium!", 1);
            else if (p1Score < p2Score)
                drawPrompt(slimeColText[p2Col] + " (" + p2Score + ")    def. "
                    + slimeColText[p1Col] + " (" + p1Score + ")", 1);
            else
                drawPrompt(slimeColText[p1Col] + " (" + p1Score + ")    def. "
                    + slimeColText[p2Col] + " (" + p2Score + ")", 1);
        }
        flip();
        try { Thread.sleep(5000); } catch (InterruptedException e) { }
        initStuff();
        } while (worldCup);
        fCanChangeCol = true;
        fInPlay = false;
        repaint();
    }

    public void init()
    {
        nWidth = size().width;
        nHeight = size().height;
        fInPlay = fEndGame = false;
        fCanChangeCol = true;
        initStuff();
        promptMsg = "Click on an option to play...";
        backBuffer = createImage(nWidth, nHeight);
        screen = backBuffer.getGraphics();
        screen.setFont(new Font(screen.getFont().getName(), 1, 15));
        doubleBuffered = true;
    }

    private void toggleBuffering()
    {
        if (doubleBuffered = !doubleBuffered)
        {
            screen = backBuffer.getGraphics();
            screen.setFont(new Font(screen.getFont().getName(), 1, 15));
        }
        else
        {
            screen = getGraphics();
            screen.setFont(new Font(screen.getFont().getName(), 1, 15));
        }
        repaint();
    }

    private void DoReplay()
    {
        FontMetrics fontmetrics = screen.getFontMetrics();
        int i = fontmetrics.stringWidth("Replay...");
        int j = fontmetrics.getHeight();
        int k = nWidth / 2 - i / 2;
        int l = nHeight / 2 - j;
        promptMsg = "Click the mouse to continue...";
        mousePressed = false;
        int i1 = replayPos-1;
        while(!mousePressed) 
        {
            if(++i1 >= 200)
                i1 = 0;
            if(i1 == replayPos)
            {
                try
                {
                    Thread.sleep(1000L);
                }
                catch(InterruptedException _ex) { }
                i1 = replayStart;
                paint(getGraphics());
            }
            ReplayFrame(i1, k, l, i, j, false);
            flip();
        }
        promptMsg = "";
        paint(getGraphics());
    }

    private void flip()
    {
        if (doubleBuffered)
            getGraphics().drawImage(backBuffer, 0, 0, null);
    }

    //AI helper: returns the X coordinate where the ball will land
    private int getBallBounceX()
    {
        int t = ballVY + (int)Math.sqrt(ballVY*ballVY+2*ballY);
        int ballBounceX = ballX + t * ballVX;
        if (ballBounceX < 0) ballBounceX = -ballBounceX;
        if (ballBounceX > 1000) ballBounceX = 1000-ballBounceX;
        return ballBounceX;
    }

    //AI helper: returns the maximum Y coordinate the ball is expected to reach
    private int getBallMaxY()
    {
        if (ballVY < 0) return ballY;
        return ballY + ballVY * ballVY / 2;
    }

    //AIs start here.

    //controlP2v0 - first crack at an AI.
    private void controlP2v0()
    {
        p2XV = 0;
        //try and make the ball go leftwards
        if ((ballX>p2X+5) && (ballX<960)) fP2Sticky = true;
        if (ballX>p2X-10) p2XV = SLIMEVEL;
        if ((ballX+30>p2X) && (p2YV == 0)) { fP2Sticky = false; p2YV = JUMPVEL; }
        if (ballX+50<p2X) { fP2Sticky = false; p2XV = -SLIMEVEL; }
        if ((ballX > p2X + 50) && (p2YV == 0) && (ballY > 10) && (ballY < 150)) p2YV = JUMPVEL;
        //if we're in our penalty box and we're running out of time, get out of it.
        if ((p2TouchingGoal > 0) &&
            ((MAX_TICKS_TOUCHING_GOAL - p2TouchingGoal) < 3+(p2X-850) / SLIMEVEL)) p2XV = -SLIMEVEL;
    }

    //controlP2v1 - the previous AI with lots of the holes patched.
    private void controlP2v1()
    {
        p2XV = 0;
        int bounceX = getBallBounceX();
        int ballMaxY = getBallMaxY();
        int ballMaxYT = (ballVY < 1) ? 1 : ballVY;
        //if the ball's going to land in our goal square, make sure we're running backwards
        if (bounceX > 900) p2XV = SLIMEVEL;
        //try and make the ball go leftwards
        if (bounceX+20<p2X) { fP2Sticky = false; p2XV = -SLIMEVEL; }
        if (ballX>p2X-10) p2XV = SLIMEVEL;
        if ((ballX+30>p2X) && (p2YV == 0)) { fP2Sticky = false; p2YV = JUMPVEL; }
        if ((bounceX > p2X + 50) && (p2YV == 0)) { p2XV = SLIMEVEL; }
        if ((ballX>p2X) && (ballX<960)) fP2Sticky = true;
        //if the opponent is up in the air, and about the same height as the ball, retreat
        if ((p2YV==0) && (ballX>p1X-120) && (ballX<p1X+120) && (ballY > p1Y)
            && (ballY < p1Y+100) && (p1Y > 0)) p2XV = SLIMEVEL;
        //if the opponent has the ball and we're near his end of the court,
        //and we're not losing, back off and goal hang
        if ((p2Score >= p1Score) && ((bounceX < 200) && (p2X > p1X)) ||
            ((bounceX < p1X+50) && (bounceX > p1X-50) &&
                (ballVY/4 == 0) && (p1X < 400) && (p2X < 848)))
        {
            if (p2X < 900) p2XV = SLIMEVEL;
            if ((ballX > 800) && (bounceX > 950) && (p2YV == 0) && (ballMaxY > 40))
                p2YV = JUMPVEL;
        }
        //stop us jumping in various circumstances
        if (p2YV == JUMPVEL)
        {
            if (ballMaxY < 110) p2YV = 0;
            if (ballX < p2X-400) p2YV = 0;
            if (ballY < 80) p2YV = 0;
            if ((ballX < 900) && (p2X > 900)) p2YV = 0;
            if (p2X < 150) p2YV = 0;
        }
        //if we're in our penalty box and we're running out of time, get out of it.
        if ((p2TouchingGoal > 0) &&
            ((MAX_TICKS_TOUCHING_GOAL - p2TouchingGoal) < 3+(p2X-850) / SLIMEVEL)) p2XV = -SLIMEVEL;
    }

    //controlP2v2 - Yet more hole patching.
    private void controlP2v2()
    {
        int bounceX = getBallBounceX();
        int ballMaxY = getBallMaxY();
        int ballMaxYT = (ballVY < 1) ? 1 : ballVY;
        //by default, park at pos. 800
        if (p2X < 790) p2XV = SLIMEVEL;
        else if (p2X > 830) p2XV = -SLIMEVEL;
        else p2XV = 0;
        //if the ball's going to land in our goal square, make sure we're running backwards
        if (bounceX > 900) p2XV = SLIMEVEL;
        //try and make the ball go leftwards
        if (bounceX+20<p2X) { fP2Sticky = false; p2XV = -SLIMEVEL; }
        if (ballX>p2X-10) p2XV = SLIMEVEL;
        if ((ballX+30>p2X) && (p2YV == 0)) { fP2Sticky = false; p2YV = JUMPVEL; }
        if ((bounceX > p2X + 50) && (p2YV == 0)) { p2XV = SLIMEVEL; }
        if ((ballX>p2X) && (ballX<960)) fP2Sticky = true;
        //if the opponent is up in the air, and about the same height as the ball, retreat
        if ((p2YV==0) && (ballX>p1X-120) && (ballX<p1X+120) && (ballY > p1Y)
            && (ballY < p1Y+100) && (p1Y > 0)) p2XV = SLIMEVEL;
        //if the opponent has the ball and we're near his end of the court,
        //and we're not losing, back off and goal hang
        if ((p2Score >= p1Score) && ((bounceX < 200) && (p2X > p1X)) ||
            ((bounceX < p1X+50) && (bounceX > p1X-50) &&
                (ballVY/4 == 0) && (p1X < 400) && (p2X < 848)))
        {
            if (p2X < 900) p2XV = SLIMEVEL;
            if ((ballX > 800) && (bounceX > 950) && (p2YV == 0) && (ballMaxY > 40))
                p2YV = JUMPVEL;
        }
        //stop us jumping in various circumstances
        if (p2YV == JUMPVEL)
        {
            if (ballMaxY < 110) p2YV = 0;
            if (ballX < p2X-400) p2YV = 0;
            if (ballY < 80) p2YV = 0;
            if ((ballX < 900) && (p2X > 900)) p2YV = 0;
        }
        //if we're up the front of the court and the ball is going to
        //land way behind us, jump whatever happens
        if ((p2YV == 0) && (p2X < 400) && (bounceX > 500) && (ballMaxY > 50)) p2YV = JUMPVEL;
        //if we're in our penalty box and we're running out of time, get out of it.
        if ((p2TouchingGoal > 0) &&
            ((MAX_TICKS_TOUCHING_GOAL - p2TouchingGoal) < 3+(p2X-850) / SLIMEVEL)) p2XV = -SLIMEVEL;
    }

    //controlP2v3 - One or two more holes patched
    private void controlP2v3()
    {
        int SLIMEVEL = this.SLIMEVEL * 4 / 3;
        int bounceX = getBallBounceX();
        int ballMaxY = getBallMaxY();
        int ballMaxYT = (ballVY < 1) ? 1 : ballVY;
        //by default, park at pos. 800
        if (p2X < 790) p2XV = SLIMEVEL;
        else if (p2X > 830) p2XV = -SLIMEVEL;
        else p2XV = 0;
        //if the ball's going to land in our goal square, make sure we're running backwards
        if (bounceX > 900) p2XV = SLIMEVEL;
        //try and make the ball go leftwards
        if (bounceX+20<p2X) { fP2Sticky = false; p2XV = -SLIMEVEL; }
        if (ballX>p2X-10) p2XV = SLIMEVEL;
        if ((ballX+30>p2X) && (p2YV == 0)) { fP2Sticky = false; p2YV = JUMPVEL; }
        if ((bounceX > p2X + 50) && (p2YV == 0)) { p2XV = SLIMEVEL; }
        if ((ballX>p2X) && (ballX<960)) fP2Sticky = true;
        //if the opponent is up in the air, and about the same height as the ball, retreat
        if ((p2YV==0) && (ballX>p1X-120) && (ballX<p1X+120) && (ballY > p1Y)
            && (ballY < p1Y+100) && (p1Y > 0)) p2XV = SLIMEVEL;
        //if the opponent has the ball and we're near his end of the court,
        //and we're not losing, back off and goal hang
        if ((p2Score >= p1Score) && ((bounceX < 200) && (p2X > p1X)) ||
            ((bounceX < p1X+50) && (bounceX > p1X-50) &&
                (ballVY/4 == 0) && (p1X < 400) && (p2X < 848)))
        {
            if (p2X < 900) p2XV = SLIMEVEL;
            if ((ballX > 800) && (bounceX > 950) && (p2YV == 0) && (ballMaxY > 40))
                p2YV = JUMPVEL;
        }
        //stop us jumping in various circumstances
        if (p2YV == JUMPVEL)
        {
            if (ballMaxY < 110) p2YV = 0;
            if (ballX < p2X-400) p2YV = 0;
            if (ballY < 80) p2YV = 0;
            if ((ballX < 900) && (p2X > 900)) p2YV = 0;
            if ((p2XV > 0) && (ballMaxY > 200) && (bounceX > p2X + 300)) p2YV = 0;
        }
        //if we're up the front of the court and the ball is going to
        //land way behind us, jump whatever happens
        if ((p2YV == 0) && (p2X < 400) && (bounceX > p2X+400) && (ballMaxY > 50)) p2YV = JUMPVEL;
        //if we're in our penalty box and we're running out of time, get out of it.
        if ((p2TouchingGoal > 0) &&
            ((MAX_TICKS_TOUCHING_GOAL - p2TouchingGoal) < 3+(p2X-850) / SLIMEVEL)) p2XV = -SLIMEVEL;
    }

    private void p(String s) { System.out.println(s); }
}
```

---

### Post by user1397 on 2010-11-21
yea just wanted to keep the above as a record

---

### Post by Austin25 on 2010-11-21
> **ubuntuman001 said:**
> this is the .java file:
Wouldn't that be good to put in code tags instead of quote tags?

---

### Post by user1397 on 2010-11-21
> **Austin25 said:**
> Wouldn't that be good to put in code tags instead of quote tags?
yup, don't know why i didn't think of that hehe, edited

---

