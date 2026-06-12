---
title: "HELP: WARCRAFT III lag on Wine?"
date: 2011-01-04
forum: Wine
---

### Post by Dong9589 on 2011-01-04
Hi guys.
I'm new to Ubuntu [10.04]
and yeah,
i tried to play DOTA on wine, (since everyone told me to)
but it didn't work just as i wanted.

ok so..

screenshot:
to show u i have Warcraft III on my netbook.

screenshot I:
i click on "Frozen Throne" and run it on wine

Screenshot 2: 
so far so good. Actually, it's great!

Screenshot 3: 
it might look ok in the picture, but
it lags
LAGGG
LAGGG I SAYYY

my cursor delays -.-

and i don't like it one bit.

help?!


p.s
i tried watever was on the forum on wine and warcraftIII

i didn't get one bit wat they are telling me to do...

so..

yeah.

thnx.

---

### Post by khelben1979 on 2011-01-22
Have you tried to lower the graphic settings? 

Besides that, it's your hardware which Ubuntu uses which is the result of the performance you get, so it's not much to do other than to check that your system uses the fastest possible graphic drivers. Using the **lspci** command from a terminal tells us what graphic chipset you got to know how that looks like.

---

### Post by noodleman999 on 2011-01-23
I dont know if you can do this with warcraft but it works with world of warcraft... find your warcraft directory. If there is a folder called "WTF" you go in there and find "Config.wtf" Add a new line that says: SET gxApi "opengl". Wine runs better with that

---

