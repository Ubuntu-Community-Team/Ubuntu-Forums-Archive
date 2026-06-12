---
title: "wine and opensong"
date: 2006-12-01
forum: Ubuntu Christian Edition
---

### Post by dlehman on 2006-12-01
I have been using open song for about a year on windows xp but I want to migrate everything to ubuntu, I use ubuntu on my desktop and just recently decided to dual boot my laptop with ubuntu so I can promote linux in the church and use all open source.  I finaly got xinerama working and installed opensong for linux and it does not work it is slow and tenable. I looked into lyricue but I don't think it will work to well, it is to mouse oriented for me and you have to double click every tine you want to change songs, I like just to be able to hit the down arrow, especially when standing up.  

So tonight I decided to try the windows version of opensong with wine and what do you know it runs 10 times faster then the linux version and it presents in dual screen as it should, it is sad that the windows version works better on linux then the linux version does.  

but my only problem is I cannnot get any backgrounds for fonts so every thing is with a teal background and small font so I have a few questions

1) Can I install fonts for wine?
2) Is there a way to get the backgronds working?
3) does anyone else have this experance or can you recomenred an application similar to opensong so I can migrate complety to ubuntu?

Thank you

---

### Post by loell on 2006-12-01
if lyricue has the key binding for showing the next slide , would you change your mind and use it instead?

---

### Post by dlehman on 2006-12-01
I would be a step in the right direction.  Here is the situation...

My church is very small I don't have any little tech room where where I can keep every thing setup or a desktop. I bring in my personal laptop every Sunday and connect it to a cable hanging from the ceiling. so when the congregation stands to sing I stand to and I can't see the laptop screen that well I just use the down arrow in opensong and look at the projection screen.  also my pastor is spontaneous so I need to keep up with him add stuff last minute skip a reading etc.  and the last issue I have with lyricue is I just  got my pastor on opensong and he will create sermon notes and show verses to illustrate is points, and copy the file and give it to me Sunday morning on a pen drive. With using sql how can this be done or where is the settings to connect to a central sql server I could not find it. and he uses windows so will lyricue work on his computer.  

So if I can overcome the majority of these obsticals I will switch to whatever program gets the job done.  

Thanks

---

### Post by MJvW on 2006-12-07
> **loell said:**
> if lyricue has the key binding for showing the next slide , would you change your mind and use it instead?
There is already a key binding:
"Page up"  > Previous song
"Page down" > Next song
"Left Arrow" > Previous page
"Right arrow" > Next page 
"b" > blank display

---

### Post by silvagroup on 2006-12-07
For wine you may have to go into ```
winecfg
``` and set up specific libraries (ddl) overrides. Check your windows installed version and see what dll's it's using and with much experimentation you could get this problems resolved (or use lyricue). Also are the microsoft core fonts installed, that could be part of the font problem.

---

### Post by jhmac77 on 2006-12-08
How do I make a new post? 

Thanks and God Bless
Jim

---

### Post by Darrious on 2006-12-08
Do you mean a thread?

If you do then click new thread at the top left of the forums.

---

### Post by jhmac77 on 2006-12-08
> **dlehman said:**
> I have been using open song for about a year on windows xp but I want to migrate everything to ubuntu, I use ubuntu on my desktop and just recently decided to dual boot my laptop with ubuntu so I can promote linux in the church and use all open source.  I finaly got xinerama working and installed opensong for linux and it does not work it is slow and tenable. I looked into lyricue but I don't think it will work to well, it is to mouse oriented for me and you have to double click every tine you want to change songs, I like just to be able to hit the down arrow, especially when standing up.  

So tonight I decided to try the windows version of opensong with wine and what do you know it runs 10 times faster then the linux version and it presents in dual screen as it should, it is sad that the windows version works better on linux then the linux version does.  

but my only problem is I cannnot get any backgrounds for fonts so every thing is with a teal background and small font so I have a few questions

1) Can I install fonts for wine?
2) Is there a way to get the backgronds working?
3) does anyone else have this experance or can you recomenred an application similar to opensong so I can migrate complety to ubuntu?

Thank you


I am a newbie and know very very little about Linux.
How do I use wine on 6.06?  I just installed it and now I don't know how to try putting Quicken and other MS software to use?  Please help!!

Blessings,

Jim  I am sorry but I don't know how to make a new post!  Please email me at [email]jhmac77@bellsouth.net[/email].  Thanks.

---

### Post by silvagroup on 2006-12-09
Go to terminal and ```
winecfg
```
It will then take you the wine configuration window. Not much to do at this point so you can close it.
Next you need to put your software cd or dvd in your drive, when prompted you can open the cd/dvd click on the setup or install .exe and wine will take it from there. If not you may get something like open with, you want to select or enter wine.
Now for the bad news, very few programs actually run well or at all in wine, yet. So you have to do some looking through the appbd on the wine website and do much experimenting with the winecfg settings to get things working. You will need to spend some time on learning about configuring wine also.
If you really must have the windows programs, because there's no windows comparable for the native *nix or they won't run in wine try qemeu, vmware, or my personal favorite win4lin pro.

---

### Post by CptFuzzy on 2007-02-06
> **MJvW said:**
> There is already a key binding:
"Page up"  > Previous song
"Page down" > Next song
"Left Arrow" > Previous page
"Right arrow" > Next page 
"b" > blank display

OpenSong also has key bindings for verses, tags, the chorus, etc... very handy.  A must have for me.

---

### Post by pbhj on 2007-03-06
I just wrote a quick review of [installing opensong on kubuntu]("http://pbhj.alicious.com/opensong-kubuntu-digital-projection"), from the point of view of a windows xp laptop, ie including installing kubuntu first!

Might help someone, feel free to ask me about it .... haven't settled yet, might install openlp?

Have tried lyricue and whilst the install was fine (using adept) I can't run it as I don't know the root pass for mysql, will investigate, can't be too hard.

---

