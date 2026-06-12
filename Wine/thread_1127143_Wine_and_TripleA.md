---
title: "Wine and TripleA"
date: 2009-04-16
forum: Wine
---

### Post by Blikemmer on 2009-04-16
Hi, TripleA is the computer version of the board game Axis and Allies.

The idea is to run TripleA on ubuntu. I downloaded the "all platforms" zip from softpedia.

After the triplea_1_0_0_3 folder was extracted. I found an exe file. Then I installed wine and ran the triplea.exe with wine. And recieved the following error:

"Launch4j"

"This application requires a java runtime environment 1.5.0" 

I installed java 6 (with runtime 1.6) and when it still didn't work I also tried java 5. But I still have the problem.

I googled and found a lot similar problems with solutions, but none of them work:(

Also, I have to add that I am still new to the whole ubuntu thing. So maybe I made a rookie mistake ( or a few for that matter ) there somewhere.

Thanks

---

### Post by scheuri on 2009-04-16
Hi there

Is there a certain reason why you use the exe-file?

I am asking because that ZIP should containt something line a script called triplea_XXX_unix.sh (or something) which you can start by command line.
However, you need to have a java jre installed (openjdk or sun, does not really matter).

There is no need to use the exe-file to start and play the game, you can run the game with java.

Cheers
scheuri

---

### Post by Blikemmer on 2009-04-16
Thanks!! It worked like a charm :D

---

