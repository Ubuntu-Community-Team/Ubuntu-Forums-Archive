---
title: "want the 3 new starwars trailers?"
date: 2005-04-19
forum: The Cafe
---

### Post by jdodson on 2005-04-19
lucas released three starwars commercial spots on the internet today.  you can either use the mozilla-mplayer plugin to view them over a webpage, or do some html diving to download the files direct.  here is a hack to download them to your harddrive.  

you have to have the w32codecs installed to view them, check this site here for more information: [http://www.ubuntuguide.org](http://www.ubuntuguide.org) after that i install the totem-xine package.  mplayer or vlc work well too.

to download the new tv trailers copy this into gedit:

```

#! /bin/sh
wget http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/epiii_jediaction1_480_dl.mov
wget http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/epiii_jediaction2_480_dl.mov
wget http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/epiii_unite_480_dl.mov

```

save it as "getStarwars.sh".

to run the script type

```
sh ./getStarwars.sh
```

enjoy!

---

### Post by bored2k on 2005-04-19
As much as I'd love to see them [believe me, I want to], I'm trying to avoid it, mainly because I don't want anything to be spoiled for me [thank God I did the same thing for Attack of the Clones, because the second I saw Yoda draw his lightsaber my mouth hit the floor twice; If i had seen the TV Spot were Yoda draws his Lsaber (trust me, there is one, we have it on DVD) I would have gone berserk].

I'm still going to download them for my brother [my country's #1 SW/Science Fiction fan <-- stupid amount of dollars on S.W.  books/encyclopedias :-\], so thanks for the tip!

---

### Post by jdodson on 2005-04-19
> **bored2k]As much as I'd love to see them [believe me, I want to], I'm trying to avoid it, mainly because I don't want anything to be spoiled for me [thank God I did the same thing for Attack of the Clones, because the second I saw Yoda draw his lightsaber my mouth hit the floor twice said:**
> .

I'm still going to download them for my brother [my country's #1 SW/Science Fiction fan <-- stupid amount of dollars on S.W.  books/encyclopedias :-\], so thanks for the tip!

there are three more trailers on the starwars.com webpage.  i have not totally viewed these fully(saving them for tonight), however from a three second clip i did see, they give away more footage.  so from the 5 combined trailers, i think they might give away too much.  so i do warn people in that regard.  

here are the other trailers:
```

#! /bin/sh
wget http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/aol/auth/switzler084d_dl.mov
wget http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/rednalob_480_r_dl.mov
```

---

### Post by dataw0lf on 2005-04-19
> **bored2k]As much as I'd love to see them [believe me, I want to], I'm trying to avoid it, mainly because I don't want anything to be spoiled for me [thank God I did the same thing for Attack of the Clones, because the second I saw Yoda draw his lightsaber my mouth hit the floor twice said:**
> .

I'm still going to download them for my brother [my country's #1 SW/Science Fiction fan <-- stupid amount of dollars on S.W.  books/encyclopedias :-\], so thanks for the tip!

ah, the only good part about Attack of the Clones.  Please, God, please let the 3rd be better than the first two.  Please.  I beg of you, for the sake of my sanity.

---

### Post by TravisNewman on 2005-04-19
Agreed whole heartedly, dataw0lf.

here's an easier way to get the star wars trailers. Just copy this chunk into a terminal and hit enter:
[code]
wget http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/epiii_jediaction1_480_dl.mov && wget http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/epiii_jediaction2_480_dl.mov && wget http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/epiii_unite_480_dl.mov && wget http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/aol/auth/switzler084d_dl.mov && wget http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/rednalob_480_r_dl.mov
[/quote]

---

### Post by Leif on 2005-04-19
[QUOTE=dataw0lf]ah, the only good part about Attack of the Clones.  Please, God, please let the 3rd be better than the first two.  Please.  I beg of you, for the sake of my sanity.[/QUOTE]

With those 5 downloads, I think I just *saw* episode 3. Sweet, sweet spoilers. Not that I'm complaining - it's not like we don't know where the movie is going.

---

### Post by geekgod on 2005-04-19
We prefer StarWars Mobile Home

---

### Post by jdodson on 2005-04-19
[QUOTE=panickedthumb]Agreed whole heartedly, dataw0lf.

here's an easier way to get the star wars trailers. Just copy this chunk into a terminal and hit enter:

wget [http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/epiii_jediaction1_480_dl.mov](http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/epiii_jediaction1_480_dl.mov) && wget [http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/epiii_jediaction2_480_dl.mov](http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/epiii_jediaction2_480_dl.mov) && wget [http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/epiii_unite_480_dl.mov](http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/epiii_unite_480_dl.mov) && wget [http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/aol/auth/switzler084d_dl.mov](http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/aol/auth/switzler084d_dl.mov) && wget [http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/rednalob_480_r_dl.mov](http://pdl.stream.aol.com/aol/us/moviefone/movies/2004/lucasfilm/hyperspace/rednalob_480_r_dl.mov)
[/quote]

** SLAPS HEAD ** sometimes i make things WAY more complicated than they should be.  my bad, my bad..... ](*,)

---

### Post by TravisNewman on 2005-04-19
[QUOTE=jdodson]** SLAPS HEAD ** sometimes i make things WAY more complicated than they should be.  my bad, my bad..... ](*,)[/QUOTE]
 ;) s'ok

the shell script is better for learning!

---

### Post by jdodson on 2005-04-19
[QUOTE=panickedthumb];) s'ok

the shell script is better for learning![/QUOTE]

true dat.

---

### Post by TravisNewman on 2005-04-19
though I must say, it doesn't really give anything away-- unless you've been living under a rock for years and haven't seen 4,5, and 6.

---

### Post by TravisNewman on 2005-04-19
Also, what's up with the announcer-- he sounds like he's announcing a kid's movie or something.

---

### Post by bored2k on 2005-04-19
[QUOTE=panickedthumb]Also, what's up with the announcer-- he sounds like he's announcing a kid's movie or something.[/QUOTE]
 Ok that last statement of yours just wiped off any desire I felt towards watching those trailers. After Ep. I & II, I gotta go to the theater with nothing but happy thoughts ("Happy place, my happy place, happy place, my happy place *slaps*, HAPPY" -- Fight Club, 1999).

Please don't tell me the announcer its the same dude that does comedy ones like white chicks and other uber kids films (it was him on Ep. II :(:-o).

BTW, my brother supposedly found the book on the internet .. he hasn't downloaded it yet, but I hope no one ever decides to start giving away any of the story on the internet.

---

### Post by TravisNewman on 2005-04-19
I'm sure it's all over the net. Just don't read it.

---

### Post by bored2k on 2005-04-19
[QUOTE=panickedthumb]I'm sure it's all over the net. Just don't read it.[/QUOTE]
 I just hope no one on any forums I read starts without any alert to spit out anything like often happens on Gamespot's forums. 

I think I'll just cut my communication with the human world the day it gets released 'til I see that movie. I'm still trying to figure out how they will top a) Ep. II Yoda battle and b) "I am your father" >...Fo shizzle?<.

---

### Post by TravisNewman on 2005-04-20
They won't top "I am your father." That's just not possible. They'll top the Yoda battle with... another Yoda battle? Possible.

I'm thrilled. 100% to the brim thrilled. Yes, I did just mix metaphors. Sue me ;)

---

### Post by jdodson on 2005-04-20
[QUOTE=panickedthumb]They won't top "I am your father." That's just not possible. They'll top the Yoda battle with... another Yoda battle? Possible.

I'm thrilled. 100% to the brim thrilled. Yes, I did just mix metaphors. Sue me ;)[/QUOTE]

the new movie seems to look like it will be cool.  i am going into it expecting nothing, perhaps i will be surprised.

---

