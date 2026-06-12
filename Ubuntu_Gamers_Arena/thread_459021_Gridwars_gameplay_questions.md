---
title: "Gridwars gameplay questions"
date: 2007-05-30
forum: Ubuntu Gamers Arena
---

### Post by tabithaboof on 2007-05-30
I appreciate I am very late on this one but I picked up gridwars (geometry wars clone) a while back and I am really enjoying it but I was wondering what causes the score multiplier to go up? Also any idea what a respectable high score for GW is?

---

### Post by tsukasa80 on 2007-08-29
from world of stuart:

"The black holes contain the key to racking up high scores in GW2. Blasting baddies nets you only a few tens of points, and while staying alive and avoiding using your screen-clearing smart bombs will build up a multiplier (the highest your correspondent has ever seen it get is 7x, and letting off a smart bomb scores zero points and resets the multiplier to 1x), it'll still take you forever to break a million points just by wiping out waves of bad guys. What you CAN do with them, however, is "bank" them by luring them into the black holes, and then blow up the black holes by repeatedly shooting them, which scores a LOT more points. The finer workings of exactly how many more still elude this reporter at the time of writing, but if you really stuff one of those little dark stars with evil beasties before you wipe it out, you can easily notch well over 100,000 points from a single supernova"

grid wars is an awesome game when i feel like some opengl punishment heh.

---

### Post by longandrink on 2008-09-11
I *love* gridwars.  One of the best arcade-style games ever.

Multipliers go up after scoring an exponentially increasing number of points per multiplier level.

On Hard, my high score is 4.35 million.  But I am pretty good, I think.  I can't find too many other high score posts online, but the writer of the article referenced above has a highscore of 1.7mil.  If you top 2 mil, you are quite skillful and that is a very respectable score.

He suggests farming black holes is the key to a high score; I disagree.  Once you get up to x8 multiplier, flying around and shooting **** becomes very profitable.

---

### Post by longandrink on 2008-09-11
PS anyone with a highscore, please post.

---

### Post by kickz101 on 2008-10-14
hey yall!
i also just love the game, and its really sad they closes it down, althouth version 5.4 is near perfection  :D
what doesnt seem good is that the highscores arnt compareable..  
my best is 1.7mil in 21 min with mouse at 800x600 hard in version 5.4....(best settings to my mind ^^)
xD see
5.3 for example was easyer, and playing on bigger screen settings also is.. the 8x multiplyer was taken out in the 5.4 update it sayed in the developers forum i found, but now it seems dead. also the scores that go into the highscore are also the ones you score if you turn the godmode on (with some f2 or f6 key..) and you can change game characteristics with the buttons as well x(
i even got myself geometey wars, but i like gridwars better, especially the mouse control..  i hate to aim and fly around at the same time  :P
Well to my mind, black holes are eating your points away, so you got to shoot them as soon as they appear, and also their dangerous exploding, when the screen is packed... also eliminating the spawn points is better so there arnt that many different enemytypes on the field...  atleast i think so  ^^

there should be someone atleast illigally remaking it, or Mark should release the source  :D

how about a tournament, with the same settings version etc?

MFG
--
K1X

---

### Post by longandrink on 2008-11-14
Good point.  Attainable high scores, and play style, vary over different screen resolutions.  The vast majority of my play was on 20" widescreen LCD at 1440x900.  v5.3.  High score is 6011232 now, by the way ;)

I'm pretty sure, if there was a Gridwars tournament, nothing could keep me from attendance.  I hope it'll be weird, though, lots of dim lighting and shady figures.  Maybe in a jungle, or with tons of fishtanks.

---

### Post by swimb on 2008-11-14
I love GridWars. I played it a ton last winter at 1600x1200 and got a high score of 6159740. Now I have to use 1280x960 and have trouble getting above 3.8 million just to get on the high score list.

I play on medium skill, I should give hard a try sometime.

Anyone else notice how the red bullet powerup only shows up when you dont need it?

---

### Post by kickz101 on 2008-11-15
yeah powerups seem to appear at the end of waves, and so you uselessly shoot them at nothing ... but you dont get red shots after the beginning anyway or , dont know seem to be rare :D
how long do you play on such a big screen? must take ages to die.. ^^

--
kickz

---

### Post by swimb on 2008-11-17
The source is on getdeb, or is that not the full source or something? It needs to be fixed so we dont have to setup the link to see the gamepad all the time :)

Im playing the one from getdeb, it says taumel's build (9.3.2006 on 4.1), where do you get v5.3/v5.4?

My hi score time was 1:11:32.

---

### Post by kickz101 on 2008-11-22
what language is the source coded in? is is possible to add to the programming / change it?

---

### Post by swimb on 2008-11-23
I have no idea about the source, i dont even know if its real source or just a repackaging for linux or something.

5.3 and 5.4 isnt the linux version, are you all not playing the linux version? If not you should give it a try, its not as configurable, at least not in the menus, but its definitely harder, and theres some new grids to play on, you have to hit F3 to cycle through them. Theres an issue with the gamepad but theres instructions to set it up on the forums here.

---

### Post by AdamDunn on 2008-12-02
Actually, the original game code was written in BlitzMax, then someone compiled it for Linux. I once saw the BlitzMax source code a long time ago....

Scoring works thus:
Green squares: 100 points
Yellow pinwheel: 25 points
Blue diamonds: 50 points
Pink square: 100 points
Small pink square: 50 points
Blue circle: 10 points
Small purple triangle: 10 points
Snake: 100 points
Red Clonebot: 100 points
Line end (yellow triangle): 150 points
Black Hole: 150 points + (enemies absorbed * (enemies absorbed + 1) / 3 * 5)
Enemy generator: 1 point per hit, 200 points on kill
4 extra cannons (get 4 cannons rapidly without them decaying): 2000 points
5 faster shots: 2000 points
extra players above 9: 2000 points
extra bombs above 8: 2000 points

Then take the above values, and multiply by the multiplier.

If a black hole has, for example, 20 enemies inside it, then it's worth 150 + 20 * 21 / 3 * 5 = 850 points, so you can see that black holes filled with enemies are by far the most valuable.

---

### Post by Theenils on 2008-12-02
I play 1280x800. Highscore: 1,933,554 *keyboard controls, no 360° of shooting for me. 

I think this is a more balanced and better made game than Geometry Wars. I have put a lot of time (too much) into this game and I would love to mod it. 

I am no programmer, does anyone know where I would start with this? Download BlitzMax or something like that... 

I would love to make minor changes, like putting an accuracy meter at the top that is in real time, then have it affect the multiplier/powerups in some way. I know the accuracy would be very, very low, especially without 360° of shooting range, but it could make things interesting. 

Some bigger ideas would be:
- When 4 shot has been reached with powerups, the next powerup could be with the 2 outside streams becoming 'heat seeking'
- Enemies interact with each other: bounce off snakes/bonded triangles...
- Pac-man shot, goes off the screen on the left, comes out through the right...

Does anyone know where to start altering the Code? Do I need some sort of 'decompiler' because the program is a .exe?

Have people already created mod packs?

Any thoughts would be helpful, Thanks.

---

