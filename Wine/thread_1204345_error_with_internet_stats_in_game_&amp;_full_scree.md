---
title: "error with internet stats in game &amp; full screen - running under wine"
date: 2009-07-04
forum: Wine
---

### Post by hufferd on 2009-07-04
I am starting to think that the wine app database is BS but thats besides the point and does not need to be posted here... 

I found a  game that I looked at that was in wines app data base & had a platinum rating.....   This game has been anything but platinum....

First of all I had issues getting it to run under wine that has been fixed..... thanks to help in another thread on here.

I am still having issues for having a platinum rating this stuff should not be an issue I would not think.

1. The game will NOT play in an emulated desktop of 800x600 or w/e it is 
even when I have wine config set to emulate 800x600. ***  when the game starts it ALWAYS goes into full screen mode period!!!  Nothing else no matter what I have done.

2. there is a screen where you can see your over all ranking against other players via the Internet well you could see it if it worked...  

everytime I try to refresh stats I get an error in game it says can not connect to server or something like that..

I did take a look at the terminal ouput ... and saw a ref. to http: something and it seems to show an error I wonder if anyone knows how I could fix this?? 
> err:wininet:HTTP_HttpOpenRequestW Unable to escape string!(L"/scoresPT.php?game=0&name=Dr. Dan&score_id=0&score=888&hours_played=43&techpoints_earned=848&babies_made=41&food_gathered=16&people_cured=4&crabs_found=58&peak_population=374&deaths=29&oldest_villager=76&number_events=22&twins_birthed=178&triplets_birthed=1&version=10121&digest=coo006eooecoe6kiec89aw"...) (-2147467261)




The game is Plant Tycoon BTW -- no wise cracks about the the game please LOL the web site is [www.planttycoon.com](www.planttycoon.com) 

And just an FYI all game functions work under a virtual box I have set up including the Internet rankings But performance is bad under virtual box and I really would rather use wine if I can...

---

### Post by ackanao on 2009-07-04
Hi hufferd

I just tested and game runs in emulated Desktop without problems - try something like this:

```
WINEPREFIX=~/Desktop/Tycoon winecfg
```

Replace "/Desktop/Tycoon" with right "path" for your wineprefix.

As for your other problem I'll see what can I do...

---

### Post by NightMKoder on 2009-07-04
Make sure that you're using the latest wine (1.1.25). 
Check if it's your username (Dr.Dan - make one without the period and try).

---

### Post by hufferd on 2009-07-04
Ok guys thanks I will see what I can do and change a couple things :)

---

### Post by hufferd on 2009-07-04
> **NightMKoder said:**
> Make sure that you're using the latest wine (1.1.25). 
Check if it's your username (Dr.Dan - make one without the period and try).

Ah that worked I changed the user name  LOL who would have thought about the "." messing things up

---

### Post by hufferd on 2009-07-04
> **ackanao said:**
> Hi hufferd

I just tested and game runs in emulated Desktop without problems - try something like this:

```
WINEPREFIX=~/Desktop/Tycoon winecfg
```

Replace "/Desktop/Tycoon" with right "path" for your wineprefix.

As for your other problem I'll see what can I do...

And thank you again this worked as well --- so any time you make changes it must be with the prefix for each app I assume?

---

### Post by ackanao on 2009-07-04
Yes - changes you made for one wineprefix have no effect on other wineprefixes you have.

---

