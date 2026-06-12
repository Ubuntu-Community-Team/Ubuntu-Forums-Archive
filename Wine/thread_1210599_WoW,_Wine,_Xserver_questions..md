---
title: "WoW, Wine, Xserver questions."
date: 2009-07-11
forum: Wine
---

### Post by vashthevicious on 2009-07-11
](*,)

Ok, So i have beating my head against the wall trying to figure this crazyness out.

Now here is what i have done.  Ran WoW, In Wine: SUCCESS!!!
Tried to Open a new Xserver session:  Failed?  Or semi-success.
Tired Running a script to run WoW, in its own Xserver: MONDO failed.

Ok... so here are my question.

First, When attempting to run a new Xserver, I do assume that I need to shut down my current run, running all of my lovely little Gnome goodies, is this correct?

2nd, When running a new Xserver session is it required to have another account to run said Xserver, or would it be ideal, and also would it impact preformace if its at all possible to run TWO xservers at the same time.  One for this lovely stuff i see before me, and Another to run WoW.

3rd.  Alt+contrl+F* (* being what ever)  These are in fact other "terminals" that i can use to run xserver is this right?

4th.  HOW the great holyness do I get all this to work correctly, without crashing my Xserver and/or servers.

My objective if at all possible is to get WoW to run in its own Xserver, Regaurdless of having to logout, or shutdown the current one or what ever.

I am just wondering if all this maddness needs to be done at the level below these damned graphic user interfaces.

I am completely new to linux for the most part, I have been all over my x11 xorg.conf file, and I am running the Driver for my graphics card that isnt from ATI, the open source one. 

I am just at end of the robe here trying to get what i want done here, with as little problems, and crazy commands xD as possible 

All and any help would be awesome.   Thank you all for you time.

---

### Post by ackanao on 2009-07-11
Read this page carefully - everything is explained there:

[http://gwos.org/doku.php/wine:winestuff]("http://gwos.org/doku.php/wine:winestuff")

---

### Post by vashthevicious on 2009-07-11
Ok, so i followed the instructions, and also did what it said to run in its own Xserver.

After a little bit.. and a few alt+control+f what ever

I came across this error.

XIO: Error 11, with a few details, that i cant get back too... 


Which from what i am reading is a resource error?

What gives here.

Well what happens when i run the launcher.sh is it just brings up a black screen

So I am kinda lost here

---

### Post by ackanao on 2009-07-11
I think that you have these problems because you're using open source drivers for your graphic card - install ATi drivers and try again

---

### Post by Rody on 2009-07-12
actually i am getting the same issue plain black screen I have tired a few different scripts and nothing has workd yet, in one script i actually had a mouse but nothing to click on! :)

I have gotten a few errors about xorg.conf permissions even using sudo will dig a bit deeper.

rody

---

### Post by Rody on 2009-07-13
ok well I sort of found the problem for some reason the scrip will not change directory. so if you take out the directory part of the script and put the script in your wow folder it might work for you.

rody

---

