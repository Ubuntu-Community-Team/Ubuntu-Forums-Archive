---
title: "Problems with wine under 20.04"
date: 2020-04-14
forum: Ubuntu Development Version
---

### Post by kc1di on 2020-04-14
I've been trying out 20.04 beta, fully upgraded each day.  everything seems to work quite well except wine.  I have one old windows program that there is no replacement for but that I use every day. I know I could install windows in Virtualbox but would prefer to avoid it if possible.  It's always worked well in Ubuntu up through 19.10, but with 20.04 wine crashes with a box saying quit or wait - Which I can't get the mouse to choose.  If I wait two or three minutes the program will eventually launch.  after that if I close the session, and try to restart it I get the prompt that says wine is already running and have to kill it with killall before I can restart it.  then it's back to two or three minutes or longer.  hope this will be fixed in final.  If anyone has any Ideas I'll try it. 
thanks
P.S. I've already tried Playonlinux same result there.

---

### Post by Claus7 on 2020-04-14
Hello,

I suppose that you initiate the program by clicking on the executable file after installation. Have you checked what it mentions if executed from terminal? 

Also, are you facing the same issue using 32 or 64 bit wine prefixes? Just some initial ideas that you might have already checked...

Regards!

---

### Post by kc1di on 2020-04-14
> **Claus7 said:**
> Hello,

I suppose that you initiate the program by clicking on the executable file after installation. Have you checked what it mentions if executed from terminal? 

Also, are you facing the same issue using 32 or 64 bit wine prefixes? Just some initial ideas that you might have already checked...

Regards!

I'm using 32 bit libs. i'll give the terminal a try tomorrow and get back to you.
Thanks

---

### Post by kc1di on 2020-04-15
Same problem when lauched form terminal.  No error messages given :(

---

### Post by Claus7 on 2020-04-15
Hello,

having problems myself with playonlinux and 32bit applications, I gave a go to phoenicis playonlinux alpha2 version: [https://www.playonlinux.com/en/comments-1368.html](https://www.playonlinux.com/en/comments-1368.html). It seems that it is working ok, yet I do not know if it is on the right direction, since, focal is still in beta state and things might change when it goes to stable. I guess that I would wait a week more to see what I would get.

Another idea would be to try and install it in a 64 version of wine/playonlinux, preferably to 5.1 version at that time. I think that you might get a descent performance, so if you have the time you could try that as well. 

Regards!

---

### Post by kc1di on 2020-04-16
thanks Claus7 
yes, going to wait here also, but just put this out so if anyone had found a solution I could try that. 
Waiting not so patiently :)

---

### Post by kc1di on 2020-07-12
well nothing really changed with final.  Still takes a long time to launch a program, but once launched runs fine.  Guess that's just the way it is. :(

---

### Post by Claus7 on 2020-07-13
Hello,

haven't seen or taken any notice of any wine updates lately. Since point release is on its way in about one month from now, where bug fixes are expected, I would wait a little longer. Also, it seems that now the application in question does not crush, yet it takes longer. I suppose that the new graphics drivers that are under way would play a difference as well. 

Regards!

---

### Post by slickymaster on 2020-07-13
Thread closed

---

