---
title: "Ubuntu Controlled Christmas Lights  I/O Board"
date: 2007-10-07
forum: The Cafe
---

### Post by ksudbury on 2007-10-07
Hi, 

A friend of mine covers his house in Christmas lights each year (and i mean covers), motorised / inflatable figures etc... Although being slightly insane it is for a good cause. 

Any way... This year at the donations box we want to have a display screen on a old LCD screen having some thing like Santa clause as the idle screen and possibly a counter which will indicate how much money we have raised so far. I also want to set it up with some sort of I/O board so that when some one puts some money in it displays thank you on the screen and Santa can go "ho ho ho" or some thing like that (you get the idea I hope).  

Has anyone done some thing like this before, obviously not with Christmas lights etc but maybe they can recommend an I/O board for Linux? Also how would you guys play some animations (which are not even created yet, ideas welcome here as well). 

I would like to do this in Ubuntu / Linux if at all possible however is some one know of another solutions please feel free to suggest it. 

Oh yeah in future it would be kool to be able to control the lights from the machine but that's not essential now. 

Many Thanks

Keith

---

### Post by ksudbury on 2007-10-08
Bump :D

---

### Post by frup on 2007-10-08
I may be very wrong here but wouldn't a simple micro controller connect through a serial port be sufficient? obviously you could do it through USB too.

---

### Post by ksudbury on 2007-10-08
Basically, I want a switch then it is pressed it loads a script on the Ubuntu box saying "Thank You". 

I guess I could do the animations in Flash? 



Thanks

---

### Post by frup on 2007-10-08
Now I don't really understand what you are trying to do.

---

### Post by tgalati4 on 2007-10-08
There are a few internet-webpage-controlled Christmas displays.  Do a google search.  Most use X10 control modules and some scripts to drive them.

There are also serial and parallel port and PCI control cards for industrial automation.  These are not trivial to set up.  They require programming and some soldering skills to make breakout cables and possibly relays that are controlled by these devices.  I don't know of any off-the-shelf Christmas, USB light switcher.  That would be idea.

King of cheesy home automation:

X10.com

---

