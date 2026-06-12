---
title: "low battery handling?"
date: 2008-10-12
forum: Ubuntu Brainstorm
---

### Post by LordIshamael on 2008-10-12
i was thinking maybe there could be a low battery notification thingy for kubuntu
i dunno, cant remember rather, if its there in gnome, but in kubuntu i NEVER get reminded that my battery is low, i only realise if i check the applet in my panel
oddly enough, once i was running xp in vbox, and it was xp that told me battery critical, sure enough, when i checked the applet, battery was low

this can be a serious problem sometimes with battery low not getting a response. once i left my laptop on downloading at home, and went to school
my maid shut off the extension cord, which meant that my laptop was now running on battery. of course, it died after a couple of hours, and (i know its rare but it does happen) messed up the comp, leading to big headaches for me in fixing it
what REALLY pissed me off was when i booted into my granddads comp to access the net for help, i found that it too had died on battery, but vista had detected critical battery and shut down
vista has such a useful feature, but kubuntu doesnt? :confused:

it would be really cool if the applet in kde4 could be configured to give notification when the battery is low, and if the comp would just save data like in a saved session and then shutdown, then bring back all the data when its turned on w/ sufficient battery or external power

---

### Post by aaronb on 2008-10-12
I think that its a good idea to have a laptop automatically go into hibernate or suspend if the battery is very low.

Maybe it should...
A: Give a on screen warning at 20% battery left
B: Give a on screen warning at 10% battery left and go into Hibernate or Suspend if the user does not click on Cancel after 60 seconds.
C: Be configurable for those laptops that are not great at accurately detecting or/and reporting the amount of battery left. 

I'm not sure how to do this (And have no laptop to test with). It would also be good for desktops on UPS. Maybe the server version of Ubuntu already has this type of thing?

---

### Post by LordIshamael on 2008-10-13
hey i found out about the new power manager for kde4 - powerdevil
at first i was kinda worried because i couldnt run it, but then i found its tab in system settings
and it has configurations for everything
i dont know if the battery warnings work - and have not had an opportunity to try
but it does lock screen and dim screen according to settings given, so maybe thats a good option

edit : i still found no way to get the power applet to do anything other than display the current power level

---

### Post by tom56 on 2008-10-13
> **aaronb said:**
> I think that its a good idea to have a laptop automatically go into hibernate or suspend if the battery is very low.

Maybe it should...
A: Give a on screen warning at 20% battery left
B: Give a on screen warning at 10% battery left and go into Hibernate or Suspend if the user does not click on Cancel after 60 seconds.
C: Be configurable for those laptops that are not great at accurately detecting or/and reporting the amount of battery left. 

I'm not sure how to do this (And have no laptop to test with). It would also be good for desktops on UPS. Maybe the server version of Ubuntu already has this type of thing?

This is already implemented in Ubuntu through GNOME Power Management. Not sure about Kubuntu though...

---

