---
title: "run programs on 2nd computers"
date: 2008-01-20
forum: Ubuntu Brainstorm
---

### Post by Xbehave on 2008-01-20
The ability run an individual program on a 2nd ubuntu install
why?
Well this is many for people on EEEbuntu, but i can also see it being useful for a household where there are old computers being used.
e.g A dad has a really powerful new pc and has given his older pc to his son who wants to run something cpu intensive that would take forever on his computer.

Im fairly sure there's no technical reason it cant be done, i run windows programs through wts over the internet so over a lan there should be no/few problems.
What i think would be useful is to have a nice GUI tool to integrate the ability nicely into ubuntu. this could feature
*integration into menus
*using WakeOnLan to turn on the 2nd pc

generally make a feature that is already doable to a selling point for ubuntu.
(even if not in the default install this sort of tool will get picked up in the blogosphere)

---

### Post by smartboyathome on 2008-01-20
This is already possible with a few programs like blender, but I don't think there is an all purpose one. It could be useful for stuff like GIMP, though.

---

### Post by Xbehave on 2008-01-20
With blender doesn't it require you to go to the 2nd computer and start up the server process every time, 
With my idea id hope that you could set it up once and then every time, after that it would just run without touching the  server (although perhaps an allow/deny for local users in a later version would be nice)

---

### Post by smartboyathome on 2008-01-20
The problem I see is that it could set up some security holes. Say someone hacked the computer with that on it, they could launch a forkbomb which would instantly start bogging it down until it froze.

---

### Post by Xbehave on 2008-01-20
While that is true,
* you'd only be able to access the 2nd machine with whatever privileges you were given
* the setup could nice all tasks (probably a good step anyway)
* given that the 2 machines are ultimatly trusted, id consider that attack an aceptable vunerability (in later versions perhaps no network bound aplications could be run to prevent any damage coming from the exploit)

---

### Post by zachtib on 2008-01-22
you can:
```
ssh -X hostname
command
```

will run a program on another computer and display the interface on your local computer. i use it all the time

---

### Post by Xbehave on 2008-01-23
i dont have a 2nd computer to test this on but dont you need to do anything to setup the 2nd computer?

didnt realise it was so easy, i think a gui would still help tho, while i often launch stuff from comand line, ubuntu's target market are gui users

---

### Post by 23meg on 2008-01-23
You need to have the SSH daemon running on the other computer.

---

### Post by smartboyathome on 2008-01-23
it'd probably also be a good idea that the IP for the computer's network be static.

---

